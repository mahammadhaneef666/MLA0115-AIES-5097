from sklearn.tree import DecisionTreeClassifier from sklearn.datasets import load\_iris from sklearn.model\_selection import train\_test\_split from sklearn.metrics import accuracy\_score

**Load the Iris dataset**

iris = load\_iris()

**Split the dataset into training and testing sets**

X\_train, X\_test, y\_train, y\_test = train\_test\_split(iris.data, iris.target, test\_size=0.2, random\_state=42)

**Create the Decision Tree Classifier** clf = DecisionTreeClassifier()

**Fit the model on the training data** clf.fit(X\_train, y\_train)

**Predict on the test data**

y\_pred = clf.predict(X\_test)

**Calculate accuracy**

accuracy = accuracy\_score(y\_test, y\_pred) print(f"Accuracy: {accuracy \* 100:.2f}%")
**output**





![image](https://github.com/user-attachments/assets/e0fea8c7-7fbb-48aa-8c5a-00f4039f998a)

