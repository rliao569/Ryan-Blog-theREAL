---
toc: True
comments: True
layout: post
title: Student Lesson Python Libraries
description: To teach the class how to use public Python libraries around the internet
type: hacks
courses: {'csp': {'week': 10}}
---

### What is a Library?
Essentially a list of pre-written code that you can use to streamline and clean up your program.

Libraries can help simplify complex programs

APIS are specifications for how the procedures in a library behave, and how they can be used 

Documentations for an API/library is necessary in understanding the behaviors provided by the API/library and how to use them

Libraries that we will go over: Requests, Pillow, Pandas, Numpy, Scikit-Learn, TensorFlow, matplotlib.


### Required Installations
Please run the following commands in your vscode terminal in order to continue the lesson
- pip install numpy
- pip install matplotlib
- pip install scikit-learn
- pip install pillow
- pip install pandas
- pip install tensorflow
- pip install requests

### Images using requests and pillow libraries
'Requests' is focused on handling HTTP requests and web data while 'Pillow' is designed for data manipulation and analysis
It's common to see them used together in data-related assignments where data is fetched by HTTP requests using Requests and then processed and analyzed with Pandas.

Here's an example:


```python
import requests
from PIL import Image
from io import BytesIO

# Step 1: Download an image using Requests
image_url = "https://example.com/path/to/your/image.jpg"  # Replace with the actual URL of the image you want to download
response = requests.get(image_url)

if response.status_code == 200:
    # Step 2: Process the downloaded image using Pillow
    image_data = BytesIO(response.content)  # Create an in-memory binary stream from the response content
    img = Image.open(image_data)  # Open the image using Pillow

    # Perform image processing tasks here, like resizing or applying filters
    img = img.resize((x, y))  # Resize the image and replace x,y with desired amounts

    # Step 3: Save the processed image using Pillow
    img.save("processed_image.jpg")  # Save the processed image to a file

    print("Image downloaded, processed, and saved.")
else:
    print(f"Failed to download image. Status code: {response.status_code}")

```

In this code, we use the Requests library to download an image from a URL and then if the download is successful the HTTP status code 200 will pop up, and from there we create an in-memory binary stream (BytesIO) from the response content. We then use the Pillow library to open the image, make any necessary changes, and save the processed image to a file.

Here's a step by step tutorial on how we wrote this code: 
1)We started by importing the necessary libraries, which were Requests, Pillow, and io.

2)Download the Image

3)Use the Requests library to send an HTTP GET request to the URL to download the image.
Check the response status code to make sure the download goes through(status code 200).

4)If the download is successful, create an in-memory binary stream (BytesIO) from the response content.
Process the Image:

5)Utilize the Pillow library to open the image from the binary stream.
Change photo to desired preference(ie: size)
Save the Processed Image:

6)Save the processed image to a file using Pillow. Choose a filename and file format for the saved image.




### Hack 1

Write a Python code that accomplishes the following tasks:

Downloads an image from a specified URL using the Requests library.
Processes the downloaded image (like resizing) using the Pillow library.
Save the processed image to a file.



```python
#Code here
import requests
from PIL import Image
from io import BytesIO

# Step 1: Download an image using Requests
image_url = "https://m.media-amazon.com/images/I/61Sz-RayqyL._AC_UF1000,1000_QL80_.jpg"  # Replace with the actual URL of the image you want to download
response = requests.get(image_url)

if response.status_code == 200:
    # Step 2: Process the downloaded image using Pillow
    image_data = BytesIO(response.content)  # Create an in-memory binary stream from the response content
    img = Image.open(image_data)  # Open the image using Pillow

    # Perform image processing tasks here, like resizing or applying filters
    img = img.resize((1080, 1080))  # Resize the image and replace x,y with desired amounts

    # Step 3: Save the processed image using Pillow
    img.save("processed_image.jpg")  # Save the processed image to a file

    print("Image downloaded, processed, and saved.")
else:
    print(f"Failed to download image. Status code: {response.status_code}")
```

### Math Operations With Python Libraries
Numpy(Numerical Python) is used for numerical and scientific computing. It provides tools for handling large sets of numbers, such as data tables and arrays. Numpy makes it easier and more efficient to do mathematical tasks. 

The Matplotlib library lets you create a visual representation of your data (graphs, charts, and etc.)

### Example Sine Graph
Uses numpy and matplotlib libaries


```python
import numpy as np
import matplotlib.pyplot as plt

# Generate sample data with NumPy
x = np.linspace(0, 2 * np.pi, 100) 
# Create an array of values from 0 to 2*pi
# 100 is included to have 100 points distributed between 0 and 2π to make graph smoother
y = np.sin(x)
# Compute the sine of each value

# Create a simple line plot using Matplotlib
plt.plot(x, y, label='Sine Function', color='blue', linestyle='-')  # Create the plot
plt.title('Sine Function')  # Set the title
plt.xlabel('x')  # Label for the x-axis
plt.ylabel('sin(x)')  # Label for the y-axis
plt.grid(True)  # Display a grid
plt.legend()  # Show the legend
plt.show()  # Display the plot

```

### Hack 2
Using the data from the numpy library, create a visual graph using different matplotlib functions.


```python
import numpy as np
import matplotlib.pyplot as plt

# Generate data for two lines
x = np.linspace(0, 10, 50)  # Create an array of values from 0 to 10
y1 = 2 * x + 1  # Set of data poits

# Create and display a plot using Matplotlib

# your code here
plt.plot(x, y1, label='Sine Function', color='blue', linestyle='-')  # Create the plot
plt.title('Function')  # Set the title
plt.xlabel('amount of anime girl pulled')  # Label for the x-axis
plt.ylabel('AMOUNT OF MEN PULLED')  # Label for the y-axis
plt.grid(True)  # Display a grid
plt.legend()  # Show the legend
plt.show()  # Display the plot

```

Tensor Flow is used in deep learning and neural networks, while scikit-learn is used for typical machine learning tasks. When used together, they can tackle machine learning projects. In the code below, Tensor Flow is used for model creation and training. Scikit-learn is used for data-processing and model evaluation.

## Pip install tensorflow scikit-learn


```python
import numpy as np
import tensorflow as tf
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from sklearn.preprocessing import StandardScaler
from tensorflow import keras
from tensorflow.keras import layers
# Generate synthetic data
np.random.seed(0)
X = np.random.rand(100, 1)  # Feature
y = 2 * X + 1 + 0.1 * np.random.randn(100, 1)  # Target variable with noise
# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
# Standardize the features
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
# Create a simple linear regression model using TensorFlow and Keras
model = keras.Sequential([
    layers.Input(shape=(1,)),
    layers.Dense(1)
])
# Compile the model
model.compile(optimizer='adam', loss='mean_squared_error')
# Train the model
model.fit(X_train, y_train, epochs=100, batch_size=32, verbose=2)
# Make predictions on the test set
y_pred = model.predict(X_test)
# Calculate the Mean Squared Error on the test set
mse = mean_squared_error(y_test, y_pred)
print(f"Mean Squared Error: {mse:.4f}")
```

A decrease in loss and time metrics (ms/epoch and ms/step) shows the efficiency increases as the training epochs increases

## Hack
fill in the missing code to match the custom data set


```python
import numpy as np
import tensorflow as tf
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from sklearn.preprocessing import StandardScaler
from tensorflow import keras
from tensorflow.keras import layers
# Generate a custom dataset (replace this with your data loading code)
# Synthetic data: House prices based on number of bedrooms and square footage
np.random.seed(0)
num_samples = 100
bedrooms = np.random.randint(1, 5, num_samples)
square_footage = np.random.randint(1000, 2500, num_samples)
house_prices = 100000 + 50000 * bedrooms + 100 * square_footage + 10000 * np.random.randn(num_samples)
# Combine features (bedrooms and square footage) into one array
X = np.column_stack((bedrooms, square_footage))
y = house_prices.reshape(-1, 1)
# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
# Standardize the features
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
# Create a regression model using TensorFlow and Keras
model = keras.Sequential([
    layers.Input(shape=(1,)),
    layers.Dense(1)
])
    # Input shape adjusted to the number of features
     # Output layer for regression

# Compile the model for regression
model.compile(optimizer='adam', loss='mean_squared_error')
  # Using MSE as the loss function
# Train the model
model.fit(X_train, y_train, epochs=100, batch_size=32, verbose=2)
# Make predictions on the test set
y_pred = model.predict(X_test)
# Calculate the Mean Squared Error on the test set
mse = mean_squared_error(y_test, y_pred)
print(f"Mean Squared Error: {mse:.4f}")
```

## HOMEWORK 1

Create a GPA calculator using Pandas and Matplot libraries and make:
1) A dataframe
2) A specified dictionary
3) and a print function that outputs the final GPA

Extra points can be earned with creativity.


```python
import pandas as pd
import matplotlib.pyplot as plt

# Define a dictionary with grade values
grade_dict = {'A': 4.0, 'B': 3.0, 'C': 2.0, 'D': 1.0, 'F': 0.0}

data = {'Subject': ['AP Calc', 'APCSP', 'AP PHYSICS', 'CHINESE 7', 'USH 1'],
        'Grade': ['A', 'A', 'A', 'A', 'A'],
        'Teacher': ['Nydam', 'Mortenson', 'Liao', 'Lin', 'Ayres']}

# Function to calculate GPA
def calculate_gpa(data):
    FinalGPA = 0
    for index, row in data.iterrows():
        class_name = row['Subject']
        letter_grade = str(row['Grade'])
        GPA = grade_dict.get(letter_grade, 0)  # Use get() to handle missing grades
        FinalGPA += GPA
    avgGPA = FinalGPA / len(data)
    print(f"Average GPA is {avgGPA}")
    return avgGPA

df = pd.DataFrame(data)

# Calculate GPA
gpa = calculate_gpa(df)

# Display the DataFrame
print(df)

# Plotting the GPA for each class
fig, ax = plt.subplots()
bar_width = 0.4

class_names = df['Subject']
gpa_values = [grade_dict.get(grade, 0) for grade in df['Grade']]

bars = ax.bar(class_names, gpa_values, color='blue')

# Add labels and title
ax.set_ylabel('GPA')
ax.set_xlabel('Classes')
ax.set_title('GPA for Each Class')

# Add data values on top of the bars
for bar, gpa_value in zip(bars, gpa_values):
    height = bar.get_height()
    ax.annotate('{}'.format(gpa_value),
                xy=(bar.get_x() + bar.get_width() / 2, height),
                xytext=(0, 3),  # 3 points vertical offset
                textcoords="offset points",
                ha='center', va='bottom')

plt.show()

```

    Average GPA is 4.0
          Subject Grade    Teacher
    0     AP Calc     A      Nydam
    1       APCSP     A  Mortenson
    2  AP PHYSICS     A       Liao
    3   CHINESE 7     A        Lin
    4       USH 1     A      Ayres



    
![png](output_20_1.png)
    


## HOMEWORK 2

Import and use the "random" library to generate 50 different points from the range 0-100, then display the randomized data using a scatter plot.

Extra points can be earned with creativity.


```python
import random
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(0, 100, 50)

setofvalues = []
count = 0
while count < 50:
    count += 1
    setofvalues.append(random.randint(0, 100))
y2 = setofvalues

plt.scatter(x, y2, color='green', s=18, alpha=0.5)
plt.title('Data')
plt.xlabel('')
plt.ylabel('')
plt.grid(True)
plt.show()
```


    
![png](output_22_0.png)
    

