# Weather Data CSV Analysis

This project involves analyzing weather data stored in a CSV file using Python and the pandas library.

## Overview

The weather data CSV file (`weather_data.csv`) contains daily weather information such as temperature and conditions. This README provides an overview of how to access and analyze this data using various methods in Python.

## Methods to Access and Analyze Data

### 1. Using Basic File Methods

```python
with open("weather_data.csv") as data_file:
    data = data_file.readlines()
    print(data)
```

This method reads the entire CSV file as lines of text.

### 2. Using csv Library

```python
import csv

with open("weather_data.csv") as data_file:
    data = csv.reader(data_file)
    temperatures = []
    for row in data:
        if row[1] != "temp":
            temperatures.append(int(row[1]))
    print(temperatures)
```

This method uses the csv library to read and process the CSV file, extracting temperatures from the second column.

### 3. Using pandas Library

```python
import pandas as pd

data = pd.read_csv("weather_data.csv")
print(type(data))
print(data["temp"].mean())
print(data["temp"].max())
```

This method utilizes pandas to read the CSV file into a DataFrame, providing powerful data analysis capabilities such as calculating mean and maximum temperatures.

## Data Analysis Example

### Example: Central Park Squirrel Census Data

```python
import pandas as pd

# Load squirrel data from CSV
data = pd.read_csv("2018_Central_Park_Squirrel_Census_-_Squirrel_Data.csv")

# Count squirrels by primary fur color
grey_squirrels_count = len(data[data["Primary Fur Color"] == "Gray"])
red_squirrels_count = len(data[data["Primary Fur Color"] == "Cinnamon"])
black_squirrels_count = len(data[data["Primary Fur Color"] == "Black"])

print(f"Gray squirrels count: {grey_squirrels_count}")
print(f"Red squirrels count: {red_squirrels_count}")
print(f"Black squirrels count: {black_squirrels_count}")

# Create a summary CSV with counts
data_dict = {
    "Fur Color": ["Gray", "Cinnamon", "Black"],
    "Count": [grey_squirrels_count, red_squirrels_count, black_squirrels_count]
}

df_summary = pd.DataFrame(data_dict)
df_summary.to_csv("squirrel_count_summary.csv", index=False)
```

This example shows how to analyze squirrel census data from Central Park, counting squirrels by primary fur color and creating a summary CSV file.

## Requirements

- Python 3.x
- pandas library (`pip install pandas`)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```
