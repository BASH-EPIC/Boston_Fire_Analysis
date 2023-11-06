 Fire Incident Data Analysis and Forecasting Report
Data Link : https://data.boston.gov/dataset/fire-incident-reporting
## Overview:
The objective of this analysis is to gain insights into fire incident patterns, identify significant factors that could influence the number of incidents, and forecast future incidents to aid in proactive measures and resource planning for emergency services.

## Dataset Description:

The dataset encompasses fire incident records with various attributes, including the date and time of the alarm, the type of incident, property use, and estimated losses. Specific attention has been given to incidents categorized under the '100 Series' for fire incidents and the '500 Series' for service calls.

### Key Variables:

- `incident_number`: A unique identifier for each incident.
- `alarm_date`: The date when the incident was reported.
- `alarm_time`: The time of day when the incident was reported, converted to seconds from midnight for analysis.
- `incident_type`: A numerical code representing the type of incident, which has been converted to numeric data for modeling.
- `incident_description`: A text description of the incident type.
- `estimated_property_loss`: An estimation of the property damage caused by the incident.
- `zip`: The postal code where the incident occurred.
- `property_use`: A code signifying the type of property involved in the incident.
- `property_description`: Descriptive text of the property use.

## Data Cleansing
<img width="1130" alt="Screenshot 2023-11-05 at 10 18 58 PM" src="https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/f52a9a06-3dd2-4075-b3e8-ae5e48dfa758">

The dataset was cleansed to ensure quality and consistency:

- Irrelevant columns such as `street_suffix`, `street_type`, `address_2`, `xstreet_prefix`, `xstreet_name`, `xstreet_suffix`, and `xstreet_type` were dropped due to missing data or irrelevance to the analysis.
- Rows with missing values in the `property_use` column were removed to maintain the integrity of the target variable for predictive modeling.
- The `alarm_time` was transformed from a string to a numeric feature, representing the number of seconds past midnight, to be usable in regression analysis.
- Missing values for `estimated_property_loss` and `estimated_content_loss` were imputed with zero, assuming no loss was equivalent to missing data.

## Analysis and Insights

Descriptive analysis was conducted to understand the distribution and frequency of incidents.
- Geographical distribution mapping of Series 100 (fire incidents) and Series 500 (service calls) for the year 2022.
This included:
<img width="677" alt="Screenshot 2023-11-05 at 10 19 47 PM" src="https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/db76371b-d5ed-42a0-a4dc-1283dba09abd">

<img width="808" alt="Screenshot 2023-11-06 at 10 16 23 AM" src="https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/f52b819b-a17c-4670-a9c7-85d3666e6507">


Output Explanation:
The output of the code consists of two maps:

Geographical Distribution of Series 100 Fire Incidents in 2022:

This map shows the locations of Series 100 incidents, which typically include more severe fire-related incidents.
The size of the markers on the map is proportional to the number of incidents in that location, providing a visual representation of incident frequency.
Areas with larger markers indicate a higher number of fire incidents, which could be areas of interest for resource allocation and preventive measures.
Geographical Distribution of Series 500 Fire Incidents in 2022:

Similarly, this map visualizes the Series 500 incidents, which are service calls that may not necessarily be fires but are related to fire department services.
Again, the marker size indicates the number of incidents, allowing emergency services to analyze patterns in service calls and plan accordingly.
In summary, these visualizations are powerful tools for the fire department to understand spatial patterns in incidents, identify hotspots, and allocate resources more effectively. They also provide a visual means to communicate these patterns to stakeholders and the public.
  
- A bar chart depicting the top 10 incident types from 2018 to 2023, which highlighted the most common fire and service call scenarios.
![image](https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/009f056b-6df3-45a6-bf59-fd6184e8d095)
This horizontal bar chart displays the "Top 10 Incidents from 2018 to 2023" based on the incident description and their respective counts. Each bar represents the frequency of a particular type of fire department incident reported over this period.

From the chart, we can discern the following:

The longest bar, indicating the highest count, is for "Public service" incidents. This suggests that the most common incidents the fire department responded to were public service calls.
The second most frequent type of incident is related to "Alarm system activation, no fire - unintentional," implying that a significant number of calls were due to false alarms or malfunctioning alarm systems.
"Central station, malicious false alarm" and "Local alarm system, malicious false alarm" both suggest incidents of false alarms where the activation was intentional, hinting at potential misuse or abuse of alarm systems.
Incidents like "Good intent call, Other" and "Assist invalid" demonstrate the variety of situations the fire department assists with, beyond just fires.
"Smoke detector activation, no fire - unintentional" is another common false alarm-related incident, indicating that smoke detectors are frequently triggered without the presence of a fire.
"Cooking fire, confined to container" shows that cooking-related incidents are also a significant portion of the fire department's call-outs, though it seems these incidents were contained and did not lead to larger fires.
"Water or steam leak" incidents are also notable but less frequent than alarm-related incidents.

![image](https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/39675cb7-4caf-4a40-8ada-f94106b2b641)
This line graph is titled "Annual Fire Incidents" and shows the number of fire incidents recorded each year from 2014 to 2022.

Observations from the graph:

Starting in 2014, there was a steady increase in the number of incidents until 2016.
After 2016, there was a decline in incidents until 2018, suggesting an improvement in fire prevention or reporting methods during this period.
From 2018 to 2020, incidents increased again, reaching a peak in 2020, indicating a potential rise in fire occurrences or changes in reporting.
There was a sharp decline in reported incidents in 2021. This could be due to various factors, such as effective fire prevention measures, changes in incident reporting, or external factors such as reduced activities or occupancy in buildings due to events like the COVID-19 pandemic.
In 2022, the graph shows a significant increase, surpassing the previous peak in 2020. This suggests a substantial rise in fire incidents, which could be alarming and might require investigation into the causes and preventive measures.

![image](https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/01b4df77-4bdb-4d2d-b203-9c5ce63d376a)
Monthly Fire Incidents in 2022" , It tracks the number of fire incidents reported each month over a nearly ten-year span, starting from 2014 and going into the first few months of 2023. The graph exhibits seasonal trends with peaks and troughs suggesting a possible correlation between the time of year and the number of fire incidents. There are notable spikes in some months, which could correspond to events or conditions that lead to more fires, such as holidays, dry weather, etc. The increase in incidents from late 2021 into 2022 could indicate a need for further investigation to understand the causes behind this trend.


![image](https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/84e381e8-1471-42ba-804c-96472a145461)
Top 30 Incident Types by Frequency". It ranks the 30 most common types of fire incidents based on how often they occurred within a given data set. The bar lengths represent the frequency of each incident type, with '553.0' being the most frequent and '400.0' the least frequent within the top 30. This chart can be used by fire departments and public safety organizations to identify the most common risks and allocate resources or create public safety campaigns accordingly.


![image](https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/a347f78c-8e72-4d1a-977f-45929cff0065)
This image displays a scatter plot titled "Property Loss by Incident Type". Each dot represents an incident type plotted against the estimated property loss incurred. The horizontal axis (Incident Type) is numerical, which suggests these are coded categories of incidents. The vertical axis (Estimated Property Loss) is scaled logarithmically, given the "1e7" notation, which indicates the values range exponentially.

The plot shows that most incident types are clustered at the lower end of property loss, close to zero. However, there are a few outliers that have resulted in significantly higher property losses, denoted by the dots that are further up on the vertical axis.

![image](https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/1ab86708-4285-447e-9124-220c0e531384)
<img width="852" alt="Screenshot 2023-11-05 at 10 28 35 PM" src="https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/21aa7253-3e4a-4858-bf36-50383ffbd375">
We'll I concat these data and craeted feature, as it's shown at upperside.
The image shows a bar chart representing the "Number of Incidents by Time of Day." There are four categories of the time of day: Morning, Afternoon, Evening, and Night. The vertical axis indicates the number of incidents, while the horizontal axis categorizes the time of day.

From the chart, we can observe the following:

The highest number of incidents occur in the Afternoon, followed closely by the Morning.
The Evening has a lower number of incidents compared to Morning and Afternoon.
The Night has the least number of incidents.
This chart could be valuable for emergency services and city planners to allocate resources appropriately, as it indicates that incidents are more likely to happen during the daytime, with a peak in the Afternoon. It could suggest that increased activity during these times, such as traffic, business operations, and human interactions, could contribute to a higher likelihood of incidents. Knowing this, one could argue for a greater allocation of resources during these peak times to manage and respond to incidents more effectively.

## Predictive Modeling

A linear regression model was developed to predict `estimated_property_loss` based on various features, including `incident_type` and `alarm_time`. The model's performance was evaluated using mean squared error and R² metrics, which indicated the model's accuracy and explained variance.

Furthermore, a time series model using Facebook's Prophet was employed to forecast the number of incidents for the year 2024. The model took into account historical data and projected future trends while accounting for seasonal variations.

![image](https://github.com/BASH-EPIC/Boston_Fire_Analysis/assets/81670865/2c6686cf-140e-4823-9234-cbe3b6db8933)
This graph represents a time series forecast for the year 2023, displaying the expected trend and range of fire incident counts based on historical data from 2014 onwards. The solid line in the middle indicates the model's prediction (yhat), while the shaded area represents the prediction uncertainty, showing the upper and lower bounds of the forecast (yhat_upper and yhat_lower).

The time series model, possibly using a tool like Prophet or another forecasting algorithm, has been trained on historical data from 2014 to the last known data point, and it uses patterns in the data to project into the future. The black dots represent actual past incidents, and the forecast extends beyond these known points to predict future incidents.

We make such forecasts to:

1. Prepare and allocate resources efficiently: By understanding potential future incident counts, emergency services can ensure they have adequate staffing and equipment on hand.
2. Identify trends and patterns: Forecasting can reveal seasonal trends or long-term changes in incident rates, which can inform prevention strategies.
3. Plan for growth and development: City planners and public safety officials can use forecasts to understand how urban development might affect incident rates and prepare accordingly.

To prevent fires or reduce the number of incidents, a multi-faceted approach could be employed:

1. Public Education: Programs to educate the public on fire safety and prevention measures can reduce accidental fires.
2. Building Codes: Strengthening fire safety standards in building codes and ensuring compliance can mitigate fire risks.
3. Fire Inspections: Regular inspections of properties, especially in high-risk areas, can identify and rectify potential fire hazards.
4. Resource Allocation: Using forecast data to optimize the placement and readiness of fire stations and equipment.
5. Technological Solutions: Implementing smart home systems and IoT devices that can detect and alert residents to fire hazards.

The model's output serves as a strategic tool for planning and risk management, aiming to enhance community safety and preparedness against fire-related incidents.


## Conclusion and Recommendations

The data analysis provided valuable insights into the patterns and nature of fire incidents and service calls. Predictive modeling allows for the estimation of future incidents, which can inform resource allocation and emergency response planning.

For the fire department operations, the following recommendations are made:

- **Resource Allocation**: Increase readiness during peak times identified in the analysis.
- **Preventive Measures**: Focus on areas with higher incident rates and types of incidents that are most common.
- **Public Awareness Campaigns**: Target campaigns based on the common incident types to raise awareness and reduce occurrences.


Rerferenecs:

https://www.nfpa.org/-/media/Files/News-and-Research/Fire-statistics-and-reports/Emergency-responders/osNFIRSIncidentType.ashx?la=en

https://data.boston.gov/dataset/fire-incident-reporting

https://media.licdn.com/dms/document/media/D561FAQEgD2O3YbepWA/feedshare-document-pdf-analyzed/0/1698744569805?e=1700092800&v=beta&t=8Q68cJPHIlZgwIIesWBgQl7TKT3NLAr7Sn6HtHEwxas

https://www.mass.gov/doc/2013-suffolk-county/download
