## Summarizing model skill
I've been looking at a lot of plots and I wanted to take a step-back and synthesize some of the regional by basin differences in model error I have been seeing to answer the questions of: where is there the greatest model error? Are there regions with consistently higher error across all state variables, or does this vary variable to variable? Are there variables with consistently higher error?

To make this more digestible I made heatmap plots of model skill looking at several metrics. The first row shows results for the entire Puget Sound, with rows below being seperated into subbasins using the same subbasin masks from Aurora.

I normalized RMSE by the standard deviation so that variables with different ranges in variability could be compared to eachother. I used the standard deviation of the observations across all basins, so that each basin was normalized by the same reference value. 

<img width="3333" alt="heatmap_nrmse_2014" src="https://github.com/user-attachments/assets/1823b4ae-b522-4e68-9ad9-8a726fd7391f" />

The Nash-Sutcliffe model efficiency (NSE) is calculated as 1 minus the ratio of the error variance of the modeled data to the variance of the observed data. It has values from $-\infty$ to 1, where 1.0 is a perfect match between model predictions and the actual data, a value of 0 indicates the model's predictions are only as good as predicting the average of the data, and less than 0 meaning the observed average is a better predictor than the model.
<img width="3333" alt="heatmap_nse_2014" src="https://github.com/user-attachments/assets/b23c452d-a078-4bbf-86e7-8d040205a781" />

Willmott's index of agreement has values from 1.0 to 0, where 1 is perfect agreement and 0 is no agreement, indicating that the model performs no better than guessing the average value of all observations.
<img width="3333" alt="heatmap_willmott_d_2014" src="https://github.com/user-attachments/assets/67316b93-b0a2-4771-8adf-dfd03d1a5d53" />

NSE penalizes large errors heavily because it uses the variance which squares the differences, while Willmott's index uses absolute differences making it more robust to outliers.
### Takeaways
- Models have the least error for temperature (CT) as expected. Dissolved Oxygen is also well predicted.
- SalishSeaCast and LiveOcan have the greatest error in predicting ammonia (NH4). SalishSeaCast especially has high error for NH4. This is unsurprising, Tall is currently working on a version which remineralizes NH4 faster to improve predictions, and Susan mentioned that there previosuly wasn't model validation done for NH4. NH4 is a transient species and is commonly not represented well in models.
- Model performance is more or less spatially consistent. Looking at NRMSE, Main basin seems to have the least error for both models, although there isn't a stand-out region with the least error. Looking at NSE and Willmott's Index of Agreement, South Sound seems to have the most error for both models. I wonder if this is because South Sound is a shallower region. Because it is shallower, more of the water column is directly influenced by the seabed biogeochemistry. The models must accurrately represent processes like sediment oxygen demand and nutrient remineralization. Salinity also has greater error in South Sound which perhaps points to difficulty resolving physical circulation and freshwater exchange-- there are narrow channels which may only be a few grid cells wide making these processes more difficult to capture accurately.

