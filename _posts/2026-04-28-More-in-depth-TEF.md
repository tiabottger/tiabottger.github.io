Transport is sorted into salinity classes, then tidally averaged, and then summed with positive values creating Q_in and negative values becoming Q_out.
Look at salinity class bins created.

Where is mixing the strongest? Create a plot versus distance from mouth.

I defined sections as follows:
<img width="800" alt="create_sections2" src="https://github.com/user-attachments/assets/93067377-a859-40e9-9eb0-9ca4a92a6bdc" />

## Eulerian vs. Isohaline salt flux decomposition
In the classic Eulerian view, salt flux through the section is computed as (tidally averaged)
$F = \left\langle \int us dA \right\rangle$, where $u$ is the along-channel velocity. The salt flux is then decomposed into $u = u_0 + u_1 + u_2$: river, exchange, and tidal terms. The mean velocity (sectionally and tidally averaged) is computed as $u_0 = \frac{\left\langle \int u dA \right\rangle}{A_0}$ where $A_0$ is the tidally averaged area. This mean term is related to the river flow, it is the net flow that exists after averaging out tides. The classical exchange flow is then described by subtracting out the mean, leaving the sectionally varying tidally averaged term $u_1 = \frac{\left\langle u dA \right\rangle}{dA_0} - u_0$, where tidal oscillations are filtered out.

Salinity space identifies inflow/outflow layers as multiple extrema in Q(S). TEF requires a discretization into salinity space, where transport data are binned into salinity classes. If the number of discrete salinity classes is chosen too high TEF profiles can become too noisy. In the code, `process_sections.py` creates 
