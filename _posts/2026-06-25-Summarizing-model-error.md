## Summarizing regional differences in model error
I've been looking at a lot of plots and I wanted to take a step-back and synthesize some of the regional by basin differences in model error I have been seeing to answer the questions of: where is there the greatest model error? Are there regions with consistently higher error across all state variables, or does this vary variable to variable?

In the plot below, I normalized RMSE by the standard deviation so that variables with different ranges in variability could be compared to eachother. I used the standard deviation of the observations across all basins, so that each basin was normalized by the same reference value. 

<img width="910" alt="image" src="https://github.com/user-attachments/assets/357bd2b5-035d-4975-8bc5-c3ab22aff489" />


- Models have the least error for temperature (CT) as expected
- SalishSeaCast has the greatest error predicting ammonia (NH4). This is unsurprising, Tall is currently working on a version which remineralizes NH4 faster to improve predictions.

