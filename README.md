# MLB Statcast Hitter Report

## Overview

This project is an interactive MLB hitter analysis tool built using Statcast data. The goal of the project is to create a single report that can be used to evaluate how a hitter is being attacked, how often he is swinging at different pitches, and how those pitches are translating into run value.

The report was built as a way to combine several areas of hitter analysis into one place rather than relying on individual tables or manually reviewing different Statcast metrics.

The current version focuses on pitch usage, swing and take tendencies, pitch location, run value, count context, and the interaction between pitch type and location.

The report is designed to eventually serve as a foundation for more advanced hitter decision analysis.

## What the Report Includes

### Pitch Usage and Swing or Take Tendencies

The pitch usage chart shows the percentage of all pitches a hitter sees by pitch type. Each pitch is divided between swings and takes so that the report shows both how frequently the pitch is thrown and how the hitter responds to it.

### Run Value by Count

The report breaks down pitch level run value across several count groups including hitter's counts, even counts, pitcher's counts, and two strike counts.

Run value is calculated using Statcast's change in run expectancy.

### Run Value by Pitch Location

The location section uses the Statcast zone numbering system to show how run value changes throughout the strike zone.

The zone is displayed from the catcher's perspective. For a right handed hitter, zones 1, 4, and 7 represent the inside portion of the plate.

### Swing Rate by Pitch Location

The swing rate section shows how frequently the hitter swings in each location. This provides additional context to the run value results by showing how the hitter is responding to pitches in different areas of the zone.

### Pitch Type and Location

The final table combines pitch type and location to show how individual pitches have performed in different areas of the zone.

The table includes pitch count, usage percentage, swing percentage, and run value per 100 pitches.

## Run Value

The primary run value metric used in this project is delta_run_exp, which represents the change in run expectancy resulting from a pitch.

Positive values represent an increase in run expectancy for the hitter while negative values represent a decrease.

Run value is useful for understanding the outcome of a pitch, but it should not be interpreted as a direct measure of decision quality. A negative run value on a take does not necessarily mean the hitter made a poor decision, and a positive run value on a swing does not necessarily mean the swing itself was a good decision.

The longer term goal of the project is to build a more complete decision quality framework that considers the characteristics and context of the pitch before evaluating the hitter's decision.

## Data

The project uses MLB Statcast data accessed through pybaseball.

The notebook currently analyzes the 2026 season and uses pitch level information including pitch type, pitch location, count, batter handedness, swing or take classification, and run expectancy.

## How to Use

### 1. Install the Required Packages

pip install -r requirements.txt

### 2. Open the Notebook

Open MLB_Statcast_Hitter_Report.ipynb using Jupyter Notebook or JupyterLab.

### 3. Load Statcast Data

The notebook pulls Statcast data for the selected time period using pybaseball.

The current analysis uses the 2026 season.

### 4. Select a Hitter

The report contains an interactive hitter input.

Enter a player's first and last name and select whether to analyze all pitches or an individual pitch type.

For example:

Hitter: Juan Soto

Pitch: All Pitches

Click Generate Report to create the report.

### 5. Review the Report

The generated report provides an overview of the selected hitter's pitch usage, swing tendencies, run value, pitch location, count performance, and pitch type and location results.

## Example

Below is an example of the report generated for Juan Soto.

![Juan Soto Statcast Hitter Report](examples/Juan_Soto_Report.png)

Additional examples are available in the examples folder.

## Future Development

There are several areas I would like to continue developing.

The first is adding additional game context such as runners on base, score differential, leverage, and inning.

Another area is improving the pitch location visualization using the actual plate_x and plate_z coordinates rather than relying exclusively on Statcast zone numbers.

The longer term goal is to move beyond simply measuring the result of a pitch and develop a decision quality model that evaluates whether a hitter's swing or take was appropriate given the pitch characteristics and game context.

This could eventually incorporate pitch type, location, velocity, movement, count, batter handedness, expected swing probability, and other contextual variables.