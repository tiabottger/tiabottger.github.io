
Look at salinity class bins created.

Where is mixing the strongest? Create a plot versus distance from mouth.

I defined sections as follows:
<img width="800" alt="create_sections2" src="https://github.com/user-attachments/assets/93067377-a859-40e9-9eb0-9ca4a92a6bdc" />

## Eulerian vs. Isohaline salt flux decomposition
In the classic Eulerian view, salt flux through the section is computed as (tidally averaged)
$F = \left\langle \int us dA \right\rangle$, where $u$ is the along-channel velocity. The salt flux is then decomposed into $u = u_0 + u_1 + u_2$: river, exchange, and tidal terms. The mean velocity (sectionally and tidally averaged) is computed as $u_0 = \frac{\left\langle \int u dA \right\rangle}{A_0}$ where $A_0$ is the tidally averaged area. This mean term is related to the river flow, it is the net flow that exists after averaging out tides. The classical exchange flow is then described by subtracting out the mean from the tidally averaged transport divided by the tidally averaged area yielding $u_1 = \frac{\left\langle u dA \right\rangle}{dA_0} - u_0$. Then the remaining $u_2 = u - u_0 - u_1$ accounts for the tidal transport.

The isohaline salt flux decomposition looks at transport as a function of salinity rather than spatial position. **Transport is sorted into salinity classes/bins, then tidally averaged, and then summed with positive values creating Q_in and negative values becoming Q_out.** TEF requires a discretization into salinity space, where transport data are binned into salinity classes. If the number of discrete salinity classes is chosen too high TEF profiles can become too noisy. In the code, `process_sections.py` creates 1000 salinity bins. It then sorts each cell's transport into salinity bins, so we are left with q(time, sbins). To better understand what happens next, I took a closer look at q versus salinity class. 

Tidal averaging is done in `bulk_calc.py` using a 72 hour godin filter.  I applied the same filter (centered on 12:00) and plotted the histogram style plot for a day during spring tide when there was strong vertical mixing and a day during neap tide where the flow seperated into two layers:
<img width="2106" alt="image" src="https://github.com/user-attachments/assets/bfb408ea-74d3-41f0-ae32-d1ab52333fa3" />

Salinity space identifies inflow/outflow layers as multiple extrema in q(sbins), which is done in the code `tef_fun_lorenz.py`. 


