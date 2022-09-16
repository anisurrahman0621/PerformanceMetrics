# PerformanceMetrics
## About

Actasys Inc. creates devices that clean sensors in adverse weather conditions. Designs are tested by simulating different weather conditions in the Sensor Cleaning Station at Actasys headquarters and using image processing to track cleaning effectiveness. Initially, product performance was mostly being judged based off the shape of the graphs. Based off of my experience doing research for internal combustion engines, I was able to leverage some techniques I had learned to come up with objective, quantitative metrics to evaluate designs. In addition to measuring cleaning effectiveness, energy and water consumption was also taken into consideration.  
  
## How to Run  
  
1. Download the jupyter notebook file and place in a directory
2. Navigate to the AnalaysisFolders tab and download each of the folders named "... trial"
3. Move the folders to the same directory as the jupyter notebook file
4. Each Excel file should only be one level away from the jupyter notebook files (i.e. "Output Edge.xlsx" file should appear right after opening "1st Trial" directory)
5. Run the jupyter notebook file
6. An Excel file with all the relevant parameters will be created in the same directory as the jupyter notebook file. Each case will have its own sheet. 

## Methodology  
    
The videos that record the tests are started before the actuator turns on. In order to fairly grade each test, a common start point had to be determined. Naturally,
the point in time where the actuator turns on was taken as the start point. This start point was determined by numerically differentiating the cleaning effectiveness with respect to time and looking for time where the maximum change over time occurs.  
  
Another issue was that the test samples would all reach a slightly different steady-state value which wasn't necessarily indicative of effectiveness. As a consequence, a cutoff value is selected ahead of time to cut off the evaluation period, standardizing the time interval. This is similar to how burn duration is calculated in the combustion engine industry-- the time it takes between 10% of the fuel and 90% of the fuel being burned.  
  
Once all the raw metrics are determined, each metric is normalized using min-max normalization. Min-max normalization takes a dataset and maps all the values between 0 and 1, allowing the datasets to be graded on the same scale. Using this, a final score is calculated using a weight matrix. The weight matrix allows different parameters to be given higher importance based off the situation. For example, if rain fall is heavy and a vehicle is at high speeds, cleaning speed is of the utmost importance while energy consumption can be sacraficed.  
  
## Results  
  
This methodology allowed for higher flexibility and objectivity in product testing. Algorithms are being developed to determine different operating modes based off weather and vehicle data. As the customer base grows, different parameters can be easily added to the evaluation methodology. 
