---
date: 2026-02-09
---

# AgentScript

A few weeks ago, I was staring at a system prompt that was 127,000 tokens long. One hundred and twenty-seven thousand tokens - just the system prompt. Most of it was, you guessed it, tool schemas: JSON definitions for every possible thing the agent could do, most of which it would never touch in any given run.

My solution? I propose AgentScript: a code-first execution language where the LLM can only interact with the outside world by writing programs. No tool schemas, no function calling, no MCP, no multi-modal response gymnastics. The model writes code, a sandboxed runtime executes it, and the return value is the response. As simple as that.

## The problem with tool calling

Here's how tool calling works today: you define a bunch of tools as JSON schemas, stuff them into the system prompt, and hope the model picks the right one. Each tool needs a name, a description, parameter definitions, and examples. A single tool can easily consume hundreds of tokens. A production-grade system might have tens, sometimes hundrends, of tools.

And the tools the model never uses still consume tokens - they're sitting in the context window like furniture in a storage unit you're paying rent on but never visiting (I would know something about that). As systems grow, you get this compounding problem: context inflation drives up latency and reduces alignment, both in turn drive up costs, and costs scale non-linearly because you're paying for all those schema tokens on every single inference call.

Since many agent tasks require iteration, filtering, branching, retries, and aggregation, when you encode these behaviors through repeated LLM calls or chained tool invocations, you're effectively using natural language as a programming language. You're asking the model to be both the thinker and the doer, when decades of CS have taught us that these should be separate concerns.

In the last few months, I've seen this become an exciting idea space: Program-of-thought prompting, code interpreter systems, Anthropic's work on code execution with MCP - they all point to the same conclusion: models are better planners than executors, and deterministic computation belongs outside the model.

AgentScript takes that insight to its logical conclusion.

## The core idea

AgentScript enforces a code-only contract between a language model and its execution environment. In this world, the LLM is not an API client, not it is a conversational participant; it's a program author that can only emit AgentScript code. So there is only one execution entry point, and all interaction with the world happens through code.

This collapses tool calling, function responses, and structured outputs into a single universal abstraction: program execution.

The execution model is deliberately boring:

1. The LLM emits AgentScript code
2. The runtime executes it in a sandboxed Bun environment
3. The program can edit files, execute (constrained) shell commands, append or read logs, do arbitrary computation, etc.
4. Execution terminates via `return(value)` or `throw`
5. Only explicit return values re-enter model-visible space

Intermediate data never enters the model's context unless the program explicitly reads the persisted logs from the file system. This is my main insight: pull-based data access instead of push-based context stuffing.

The API surface can be intentionally tiny, for example:

```ts
// Control flow
return(value: any): never
console.log(message: string): void // Flushed to fs
throw new Error(message: string): never

// Filesystem
readFile(path: string): string
writeFile(path: string, content: string): void
listDir(path?: string, recursive?: boolean): string[]
exists(path: string): boolean

// Shell (possibly restricted/allowlisted)
bash(command: string): { stdout: string; stderr: string; code: number }

// Web standard library on top of Bun
Promise, Date, JSON, crypto, etc.
```

The model already knows JavaScript. The API is small enough to learn once and never forget.

And the safety model is simple: constraints are enforced by the runtime, not the model. The model can write whatever code it wants. The sandbox decides what actually executes, like only mounting the working directory, allowlisted commands, or network access.

## What's next

To start with, a backwards-compatible model would be to force a tool call from LLM responses and only give it a single tool: `execute_agentscript`, and stop the loop based on the execution of the code.

There are also a few extensions I'm thinking about:

- Capability negotiation using something like calling `fetch()` or `import * from fs` that makes the program explicitly request elevated permissions
- Deterministic replay via seeding or persisting state, so you can replay and debug agent runs
- Multi-agent orchestration as code; imagine instead of agents talking to each other in natural language, one agent's program spawns and coordinates other agent program

When systems become too complex to reason about in prose, you re-found them on code. This has happened repeatedly in computing history, and it's happening again now to agents.

_Written on a flight from Amsterdam to New Delhi_
