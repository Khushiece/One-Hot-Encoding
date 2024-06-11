<h1>Car Price Prediction Project</h1>
    <p>Predict car selling prices based on model, age, and mileage using linear regression and one-hot encoding.</p>
<h2>Dataset Description</h2>
    <p>Dataset: <code>carprices.csv</code></p>
    <ul>
        <li><strong>Car Model:</strong> Model of the car</li>
        <li><strong>Mileage:</strong> Distance traveled (miles)</li>
        <li><strong>Age(yrs):</strong> Car's age (years)</li>
        <li><strong>Sell Price($):</strong> Selling price ($)</li>
    </ul>
<h2>Project Steps</h2>
    <ol>
        <li>Load and inspect the dataset.</li>
        <li>Explore the data with visualizations.</li>
        <li>Prepare data by creating dummy variables.</li>
        <li>Define features and target variables.</li>
        <li>Train the linear regression model.</li>
        <li>Make predictions.</li>
        <li>Evaluate model performance.</li>
    </ol>
<h2>Step-by-Step Instructions</h2>
<h3>Step 1: Load and Inspect the Dataset</h3>
    <pre class="snippet">
import pandas as pd
df = pd.read_csv('carprices.csv')
df.head()
    </pre>
<h3>Step 2: Explore the Data</h3>
    <pre class="snippet">
import matplotlib.pyplot as plt
plt.scatter(df['Mileage'], df['Sell Price($)'])
plt.scatter(df['Age(yrs)'], df['Sell Price($)'])
plt.show()
    </pre>
<h3>Step 3: Prepare the Data</h3>
    <pre class="snippet">
dummies = pd.get_dummies(df['Car Model'], drop_first=True)
final_df = pd.concat([df, dummies], axis='columns').drop(['Car Model'], axis='columns')
final_df.head()
    </pre>
<h3>Step 4: Define the Features and Target</h3>
    <pre class="snippet">
X = final_df.drop('Sell Price($)', axis='columns')
y = final_df['Sell Price($)']
    </pre>
<h3>Step 5: Train the Linear Regression Model</h3>
    <pre class="snippet">
from sklearn.linear_model import LinearRegression
model = LinearRegression().fit(X, y)
model.coef_, model.intercept_
    </pre>
<h3>Step 6: Make Predictions</h3>
    <pre class="snippet">
mercedez_price = model.predict([[45000, 4, 0, 1]])[0]
bmw_price = model.predict([[86000, 7, 1, 0]])[0]
mercedez_price, bmw_price
    </pre>
<h3>Step 7: Evaluate the Model</h3>
    <pre class="snippet">
score = model.score(X, y)
score
    </pre>
<h2>Conclusion</h2>
    <p>This project predicts car prices using linear regression and one-hot encoding.</p>
</body>
