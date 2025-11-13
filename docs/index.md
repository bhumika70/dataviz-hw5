# Homework 5 - Data Visualization

## Plot 1: UFO Sightings by U.S. State

<iframe src="{{ 'ufo_plot1_state_counts.html' | relative_url }}" width="900" height="450"></iframe>

### Description, encodings, color choices, transformations

The first plot shows the total number of UFO sightings recorded in each U.S. state. I chose a **bar chart** because it clearly compares discrete regions. 

The x-axis encodes the **state abbreviation** as an ordinal and categorical variable, and the y-axis encodes the **count of sightings** as a quantitative measure using count(). 

I coloured each bar categorically by state so that individual bars are easier to distinguish even when there are many states along the axis.

On the data side, I performed several transformations in the Python notebook. Because the CSV file did not include column headers, I manually assigned names such as `date_time`, `city`, `state`, and `shape` when reading the file. I then converted the `date_time` field to a proper datetime type with `pd.to_datetime`, dropped rows where the date could not be parsed and also filtered the dataset to include only rows where `country == "us"`. I did these cleaning steps to make sure that the state-level counts are based on valid U.S. sightings.


---

## Plot 2: UFO Sightings Over Time by Shape (Interactive)

<iframe src="{{ 'ufo_plot2_shape_time_interactive.html' | relative_url }}" width="900" height="500"></iframe>

### Description, encodings, color choices, transformations

The second plot shows how UFO sightings have changed over time and it is grouped by the reported **shape** of the object. I used a **line chart** to emphasize trends over time. 

The x-axis encodes the **year** (which I derived from the sighting date) as an ordinal variable, and the y-axis encodes the **count of sightings** as a quantitative measure. 

Color encodes the UFO shape which helps the viewer to compare how different reported shapes increase or decrease over the years.

For data transformations, I reused the cleaned `date_time` column and created a new `year` field by extracting the year component. I then restricted the analysis to years between 1950 and 2020 to avoid early years and to focus on the modern reporting time. To keep the chart readable, I filtered the data to only the **top 10 most frequently reported shapes** and created a subset `df_shapes` that includes those particular shapes only. These transformations helped me in reducing noise and made the multi-line time series much easier to interpret.


---

## Interactivity

For the second plot, I added a **dropdown selection** that lets the viewer choose a specific UFO shape. The dropdown is implemented using an Altair `selection_single` bound to a list of the top shapes. When a shape is selected, its line remains fully opaque while the other lines fade to low opacity. This interactivity makes the visualization more interesting and clearer because the user can focus on one shape at a time and is able to see its trend without being overwhelmed by all shapes layered together. It also encourages exploration by letting the user quickly switch between shapes and compare how their patterns vary over time.


---

## Links

- **The Data**  
  [ufo-scrubbed-geocoded-time-standardized-00.csv](https://github.com/UIUC-iSchool-DataViz/is445_data/raw/main/ufo-scrubbed-geocoded-time-standardized-00.csv)

- **The Analysis Notebook**  
  [ufo_altair_hw.ipynb on GitHub](https://github.com/bhumika70/bhumika70.github.io/blob/main/ufo_altair_hw.ipynb)


