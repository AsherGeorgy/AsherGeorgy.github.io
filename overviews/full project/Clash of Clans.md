# Clash of Clans Hero Equipment Upgrade Planner

## Overview

This project started as a fun side project during my time playing Clash of Clans, and it has evolved into a comprehensive tool for players to plan their Hero Equipment upgrades effectively. It’s designed to help players optimize their upgrade paths based on various in-game parameters, such as Townhall Level, Trophy League, blacksmith balance, and Clan War frequency. Upon receiving postivie feedback from the reddit community ([link to post](https://www.reddit.com/r/ClashOfClans/comments/1atwpa1/plan_your_hero_equipment_upgrades_using_this/)) I decided to record it here on my Github. 

The tool is an Google Sheets-based calculator that uses formulas and lookup tables to dynamically update based on user input. By providing a clear visualization of the required resources and time needed for upgrades, players can better strategize their gameplay and resource allocation.

[Link to Google Sheets Document](https://docs.google.com/spreadsheets/d/1DzUwIBW1AuYfyH7iTgxRb2dmPH8VyY5uu85CffDie-I/edit#gid=895341860)

## Objectives and Skills

**Objectives:** To create an interactive tool that assists Clash of Clans players in planning their Hero Equipment upgrades.

**Skills Demonstrated:**
- Advanced functions and formula usage (e.g., IF, INDEX, MATCH, IFERROR)
- Data validation and conditional formatting
- Dynamic data visualization and user interface design

## Features

- **Intuitive Interface**: The planner features a user-friendly interface that allows easy input of details such as Townhall Level, Trophy League, and ore balances.
- **Dynamic Planning**: The tool dynamically calculates the resources needed and the time required to upgrade specific equipment based on user-defined parameters.
- **Clan War Frequency**: It takes into account the frequency of Clan Wars to include the collection of Starry Ores in the upgrade plan.

## Problem Statement and Background

Clash of Clans players often face challenges in planning upgrades due to the complexity of the game’s resource management and varying upgrade costs. The need to balance resource collection, time, and strategic gameplay decisions makes it difficult for players to optimize their progress. This project addresses these challenges by providing a structured, user-friendly tool to visualize and plan upgrades more effectively.

## Approach and Methodology

1. **Data Input**:
   - Players input their Townhall Level, Trophy League, blacksmith balance, and Clan War frequency.
   - Formulas are used to fetch corresponding images or values based on the input. For example:
     - `=if(isblank(My_League),"", INDEX(League_Icons,MATCH(My_League,League_List,0)))`
     - `=if(isblank(My_Townhall),"", INDEX(Townhall_Icons,MATCH(My_Townhall,Townhall_Levels,0)))`
     - `=INDEX(Equipment_Icons,MATCH(E11,Equipment_List,0))`

2. **Dynamic Calculation**:
   - The tool uses formulas to dynamically calculate the resources required and the time needed to collect these resources based on user inputs.
   
3. **Visual Feedback**:
   - The tool provides visual cues and error messages to guide the user in inputting valid data and understanding the output.

4. **Customization**:
   - The planner allows for personalized upgrade paths and considers the player's specific in-game situation, enhancing decision-making and strategic planning.
   
## Results and Insights
By using the Clash of Clans Hero Equipment Upgrade Planner, players can:
  - Efficiently plan their upgrade paths based on realistic timelines and resource availability.
  - Make informed decisions on where to allocate resources for maximum gameplay efficiency.
  - Understand the impact of different game factors, such as Clan War frequency and league placement, on their upgrade strategy.

## Screenshots

### Dashboard
![Dashboard](https://github.com/ashergeo/My-Portfolio/blob/main/assets/Fun%20projects/Dashboard.png)

### Data and Lookup
![Data and Lookup](https://github.com/ashergeo/My-Portfolio/blob/main/assets/Fun%20projects/Data%20and%20Lookup.png)

### Example Usage
A **Townhall 15 at Champion III** that wars once a week and has a blacksmith balance of [15529 Shiny Ores, 680 Glowy Ores, and 32 Starry Ores] will need 272 days to upgrade Frozen Arrow from level 17 to 27. The Dashboard will look like this:

![Example](https://github.com/ashergeo/My-Portfolio/blob/main/assets/Fun%20projects/Example%20Usage.png)

## Replication Instructions

1. **Open the Google Sheets Document**:
   - [Link to Google Sheets Document](https://docs.google.com/spreadsheets/d/1DzUwIBW1AuYfyH7iTgxRb2dmPH8VyY5uu85CffDie-I/edit#gid=895341860)

2. **Save File to Google Drive**:
   - Go to File > 'Make a copy' to save the document to Google Drive.

3. **Read Instructions**:
   - Review the 'Instructions' tab within the sheet to get the most out of the tool.

4. **Input Your Details**:
   - Enter your Townhall Level, Trophy League, current ore balances, and Clan War frequency.

5. **View Upgrade Timeline**:
   - The tool will calculate the number of days required to collect the necessary ores to upgrade your equipment to the desired levels.

6. **Plan Upgrades Long Term**:
   - Use the 'My Upgrade Plan' section to jot down and organize your long-term upgrade plans.




