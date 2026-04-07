---
name: HW5
tools: [Python, HTML, vega-lite]
image: assets/pngs/Licenses.png
description: This is a HW5 project that uses vega-lite for interactive viz!
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

# Visualizing Illinois Professional Licenses (Fall 2022)

This project analyzes the `licenses_fall2022.csv` dataset, using Python and Altair, we explore patterns in license types, statuses, and issuance trends over time.

## Plot 1: Top 10 License Types by Status

<vegachart schema-url="{{ site.baseurl }}/assets/json/licenses_by_type.json" style="width: 100%"></vegachart>

This bar chart illustrates the distribution of the top 10 most common professional license types in the dataset, categorized by their current license status (e.g., Active, Not Renewed, Revoked). The x-axis encodes the number of licenses as a quantitative variable, while the y-axis encodes license types as nominal variables, sorted in descending order by total count.

The chart uses the `tableau10` color scheme to color-code license statuses. This scheme provides clear contrast between categories, making it easy to distinguish between different statuses at a glance.

For data transformation, I grouped the original dataset by “License Type” and “License Status” and calculated the corresponding counts. I then filtered the data to retain only the top 10 license types sorted by total count, ensuring the chart remains clear and easy to read while focusing on the most significant categories.

The chart’s interactivity is implemented using `selection_point` bound to the legend. When a license status label in the legend is clicked, only the corresponding bar in the chart is highlighted, while the bars for other statuses are dimmed.

## Plot 2: License Issuance Over Time by Type

<vegachart schema-url="{{ site.baseurl }}/assets/json/licenses_over_time.json" style="width: 100%"></vegachart>

This line chart illustrates the annual changes in the number of licenses issued for the top five most common license types between 1990 and 2022. The x-axis is coded to represent the year (temporal data), and the y-axis is coded to represent the number of licenses issued (quantitative data).

The colors in the line chart use the `category10`color scheme to encode the license types (nominal variables), with different shades used to distinguish each line.

During data transformation, I parsed the `Original Issue Date` column into a date-time format, extracted the year, and then filtered records from 1990 to 2022 to focus on the modern period with valid data. The data were further filtered to include the top 5 license types by total count in the dataset and then grouped by year and type to generate aggregate counts.

Simple interactivity in the chart: Each line is marked with points to indicate annual data points, and a tooltip displays the exact values when hovered over.

## Data Resources

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/licenses_fall2022.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/bochenz3-sys/bochenz3-sys.github.io/blob/main/python_notebooks/Workbook.ipynb" text="The Analysis" %}
</div>
