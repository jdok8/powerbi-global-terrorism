# Global Terrorism Analysis with Power BI: Exploring Terrorist Incidents from 1970 to 2017

![Terrorist Attacks Report](/assets/img/terrorism_teaser.gif)

## Table of Contents

- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [Data Source](#data-source)
- [Usage](#usage)
- [DAX Formulas Used in Measures](#dax-formulas-used-in-measures)
- [Contributing](#contributing)
- [License](#license)
- [Authors](#authors)

## Introduction

This Power BI project aims to analyze worldwide terrorist attacks using data from the Global Terrorism Database (GTD) spanning from 1970 to 2017 (except 1993). With over 180,000 incidents recorded, the database provides a comprehensive view of terrorist activities globally. Leveraging the capabilities of Power BI, the project utilizes interactive visualizations to explore various aspects of terrorist attacks, including geographical distribution, attack types, targets, perpetrators, and casualties.

Through interactive exploration and data visualization, this project seeks to provide comprehensive insights into the multifaceted nature of terrorism worldwide. By enabling users to delve into historical trends, geographical hotspots, and tactical patterns, the project aims to facilitate informed decision-making and strategic planning for stakeholders involved in counterterrorism efforts.

## Project Structure

The report consists of several pages, each focusing on different aspects of the analysis:

- **Overview:** Provides an overview of terrorist attacks worldwide, showcasing charts highlighting the top 30 countries by the number of attacks, attack types by number of attacks and casualties, trends over the years, and primary targets.

- **Regional Analysis:** Allows users to explore different regions across the globe, including Sub-Saharan Africa, Central Asia, etc. It also lists the top 10 most active terrorist organizations in the selected region and visualizes the number of attacks by weapon type and a heat map of attacks.

- **Country-specific Analysis:** Enables users to select a specific country and delve into detailed analysis, including the share of attacks by target and weapon type, geographical distribution of attacks, casualties by city, and duration of attacks.

- **Attack Analysis:** Provides in-depth analysis and insights into terrorist attacks across different time periods. Users can dynamically adjust the analysis to focus on specific timeframes ranging from 1970 to 2017. It includes metrics such as the average number of killed and wounded per attack, the number of attacks and casualties by country, trends over the years, and the share of attacks among nationalities

## Data Source

The project utilizes data from the Global Terrorism Database (GTD), an open-source database maintained by researchers at the National Consortium for the Study of Terrorism and Responses to Terrorism (START), headquartered at the University of Maryland. The database contains information on over 180,000 terrorist attacks worldwide, spanning from 1970 to 2017 (except 1993), with over 100 variables on location, tactics, perpetrators, targets, and outcomes.

### Source

National Consortium for the Study of Terrorism and Responses to Terrorism (START), University of Maryland. (2018). The Global Terrorism Database (GTD) [Data file]. Retrieved from https://www.start.umd.edu/gtd

Copyright University of Maryland 2018.

## Usage

**1. Clone the Repository**

**2. Open the Power BI Project**

Open the `.pbix` file using Power BI Desktop.

You can download the dataset [here](https://drive.google.com/file/d/1-0qeBGL89B6axPmCkNSYhuLYwZp-WuWt/view?usp=sharing).

**3. Explore Reports**

Navigate through the different pages to explore the interactive visualizations.Use slicers, filters, and dropdowns to customize the analysis based on your preferences.

## DAX Formulas Used in Measures

**1. Expenses**

The count of suicide terrorist attacks:

    nsuicide = 
    COUNTAX(
        FILTER(
            terrorism_fact,
            terrorism_fact[suicide] = TRUE()
        ),
        terrorism_fact[eventid]
    )

The average number of individuals killed per terrorist attack event:

    killed_per_event = 
    DIVIDE(
        SUM('terrorism_fact'[nkill]),
        COUNTA('terrorism_fact'[eventid])
    )

The total number of casualties (killed and wounded) across all terrorist attacks in the dataset:

    casualties = SUMX(terrorism_fact, terrorism_fact[nkill] + terrorism_fact[nwound])

The average number of individuals wounded per terrorist attack:

    wounded_per_event = 
    DIVIDE(
        SUM('terrorism_fact'[nwound]),
        COUNTA('terrorism_fact'[eventid])
    )

## Contributing

Contributions to this project are welcome! Feel free to fork the repository, make improvements, and submit pull requests.

## License

This project is licensed under the [MIT License](LICENSE).

**Dataset source:**

National Consortium for the Study of Terrorism and Responses to Terrorism (START), University of Maryland. (2018). The Global Terrorism Database (GTD) [Data file]. Retrieved from https://www.start.umd.edu/gtd

Copyright University of Maryland 2018.

## Authors

- [Jan Dokoupil](https://github.com/jdok8)
