
To look at TEF along my estuary, I defined sections spaced roughly 20 km apart as follows and calculated the exchange flow at each location.
<img width="500" alt="image" src="https://github.com/user-attachments/assets/5d8cf4f9-a199-47c9-b8f1-360bd22bcae5" />   
Fig. 1: Sections for TEF analysis

This is similar to Figure 5 of MacCready et al. 2014. Note $Q_{out}$ is negative, so $-Q_{out}$ is plotted for better comparison. The TEF values have been averaged over a spring-neap tidal cycle.
<img width="1200" alt="image" src="https://github.com/user-attachments/assets/a184f2a3-45a4-4bac-a5c3-f8733f16e51d" />
Fig. 2: TEF values along estuary averaged over spring-neap tidal cycle, river discharge = 1000 m^3/s   

The volume of the exchange flow decreases away from the mouth, as expected as the estuary cross section narrows. The most interesting dynamics occur at the mouth and within the closest 20 km. At the mouth, outflow dominates. The larger magnitude of $Q_{out}$ corresponding to a larger magnitude of $S_{in}$ at the mouth suggests there is an export of freshwater while the inflowing water is saltier than the outflowing water. Moving away from the mouth, there is a net inflow as $Q_{out}$ shrinks faster than $Q_{in}$. This suggests the surface outflow is weaker than the inflow at depth here.

I repeated the TEF calculations with a model run in which I decreased the river discharge from 1000 m^3/s to 100 m^3/s. 
<img width="1200" alt="image" src="https://github.com/user-attachments/assets/18d32c1a-b95f-4da4-8d14-36d41abfc9db" />    
Fig. 3: TEF values along estuary averaged over spring-neap tidal cycle, river discharge = 100 m^3/s   

Here we see the same structure with a peak positive net inflow just landward of the mouth. At the mouth we expect mixing to be the strongest, moving this peak due to saltwater intrusion further inland. The difference between $S_{in}$ and $S_{out}$ is smaller in this case where less freshwater enters the estuary.


## Eulerian vs. Isohaline salt flux decomposition
In the classic Eulerian view, salt flux through the section is computed as (tidally averaged)
$F = \left\langle \int us dA \right\rangle$, where $u$ is the along-channel velocity. The salt flux is then decomposed into $u = u_0 + u_1 + u_2$: river, exchange, and tidal terms. The mean velocity (sectionally and tidally averaged) is computed as $u_0 = \frac{\left\langle \int u dA \right\rangle}{A_0}$ where $A_0$ is the tidally averaged area. This mean term is related to the river flow, it is the net flow that exists after averaging out tides. The classical exchange flow is then described by subtracting out the mean from the tidally averaged transport divided by the tidally averaged area yielding $u_1 = \frac{\left\langle u dA \right\rangle}{dA_0} - u_0$. Then the remaining $u_2 = u - u_0 - u_1$ accounts for the tidal transport.

The isohaline salt flux decomposition looks at transport as a function of salinity rather than spatial position. **Transport is sorted into salinity classes/bins, then tidally averaged, and then summed with positive values creating Q_in and negative values becoming Q_out.** TEF requires a discretization into salinity space, where transport data are binned into salinity classes. If the number of discrete salinity classes is chosen too high TEF profiles can become too noisy. In the code, `process_sections.py` creates 1000 salinity bins. It then sorts each cell's transport into salinity bins, so we are left with q(time, sbins). To better understand what happens next, I took a closer look at q versus salinity class. 

Tidal averaging is done in `bulk_calc.py` using a 72 hour godin filter.  I applied the same filter (centered on 12:00) and plotted the histogram style plot for a day during spring tide when there was strong vertical mixing and a day during neap tide where the flow seperated into two layers:
<img width="2106" alt="image" src="https://github.com/user-attachments/assets/bfb408ea-74d3-41f0-ae32-d1ab52333fa3" />

Salinity space identifies inflow/outflow layers as multiple extrema in q(sbins), which is done in the code `tef_fun_lorenz.py`. 


