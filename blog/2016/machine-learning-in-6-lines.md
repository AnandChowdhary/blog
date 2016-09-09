# Machine Learning in 6 Lines

At Oswald Foundation, we’re currently building a user interface for the blind, a smartphone UI that works entirely on vibrational and speech feedback. While reengineering the Phone app, the app you use to make calls, we decided to incorporate some machine learning.

If you call your Doctor in the morning every day and your parents in the evening on weekends, the app should be able to analyse that pattern and pre-populate the list of contacts relevant to the current time and location. This means that we can make a huge button for “Call Doctor” if it’s the right time and the user launches the app, and then add other options below it.

I’ve only very recently started experimenting with Machine Learning, but Python has made is super simple. First, set up an [scikit-learn](http://scikit-learn.org/stable/) environment (I used [Anaconda](https://www.continuum.io/downloads)) and import the decision tree.

```py
from sklearn import tree
```

And that’s line 1. Compile this python script, and, if there are no errors, we have our environment set up. Now let’s get some data. In the following, we’re using two one-dimensional arrays for features and labels. At 10:00 am, I called “Mom”, and, at 12:00 pm, I called “Doctor” and so on.

```py
features = [[10.00], [10.30], [12.10], [12.55], [14.00], [15.00], [18.00], [18.07], [20.00], [21.00]]
labels = ['Mom', 'Mom', 'Doctor', 'Doctor', 'Friend', 'Friend', 'Girlfriend', 'Girlfriend', 'Mom', 'Mom']
```

We’ve reached ’til line 3. This list can be populated using the history of your phone app, where labels correspond to features, and we use this information to predict who you might want to call. Let’s set up a classifier, in this case the Decision Tree Classifier, and start predicting after fitting the data.

```py
clf = tree.DecisionTreeClassifier()
clf = clf.fit(features, labels)
clf.predict([[15.30]])
```

And that’s it. When you execute this script, you’ll get the following output:

```py
['Friend']
```

Which is precisely what we were aiming for. Even though we hadn’t explicitly told the computer who we might want to call at 3:00 pm, it recognized the calling pattern to generate this answer. That’s machine learning in six lines.

This is what a simple application of this could look like. We’ve converted the current time to decimal, and we’ll print who you might want to call right now.

```py
from datetime import datetime
from sklearn import tree
features = [[10.00], [10.30], [12.10], [12.55], [14.00], [15.00], [18.00], [18.07], [20.00], [21.00]]
labels = ['Mom', 'Mom', 'Doctor', 'Doctor', 'Friend', 'Friend', 'Girlfriend', 'Girlfriend', 'Mom', 'Mom']
clf = tree.DecisionTreeClassifier()
clf = clf.fit(features, labels)
time = float("{:%H:%M}".format(datetime.now()).replace(":", "."))
print clf.predict([[time]])
```

Of course, this is just a simple demo of how it will work. We’ll incorporate other factors like the current location (latitude/longitude) and time of the month/year as features to detect precisely who you might want to call right now.

If you’re interested in learning more about Machine Learning, Google Developers has a [great playlist](https://www.youtube.com/playlist?list=PLT6elRN3Aer7ncFlaCz8Zz-4B5cnsrOMt) to get you started, and Prof. Andrew Ng’s Machine Learning [course on Coursera](https://www.coursera.org/learn/machine-learning) will help you understand the underlying concepts.
