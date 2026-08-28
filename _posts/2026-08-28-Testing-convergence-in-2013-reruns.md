## Testing convergence in 2013 reruns
I reran 2013 on itself one more time to more confidently see that the model was converging indicating that it is mostly spun-up. During our meeting at 
UBC Susan also suggested a more quantifiable way of testing for convergence, where we could say something like we stopped rerunning the model once we reached a certain percentage. 

First, here are the stacked timeseries plots created as before, now with 4 iterations of 2013. 
<img width="5221" src="https://github.com/user-attachments/assets/410569d5-f8e0-4186-8fa0-2329e55580f0" />

The 4th rerun sits almost on top of the previous run. 

To quantify convergence, I thought about the difference between successive runs. Because a straight difference between runs would vary in time, I took the root mean square difference. I could then define a percent convergence relative to the initial root mean square difference between runs. This method would enable me to say something like: "Spin-up was considered achieved when the successive-run difference decreased to ≤5% of the initial repeated-year difference, corresponding to 95% convergence."

Despite looking quite close in the stacked timeseries plots, the fourth repeat run did not reach 95% convergence as I have defined it here:
<img width="1000"  src="https://github.com/user-attachments/assets/513c4023-1792-46cc-9bac-515d18e5aeaf" />

This raises the question of whether it is worth it to run one more 2013 repeat (for a total of 5)? Does this method for testing for convergence make sense?
