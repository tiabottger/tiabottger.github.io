## Defining sigma layer structure
The sigma coordinate system transitions the vertical grid from the surface ($\sigma$ = 0) to the seabed ($\sigma$ = -1). Because every layer occupies the same fraction of the water column, the grid follows bottom topography. The total water column depth is $D = H + \zeta$ where $H$ is the bottom depth and $\zeta$ is the height of the free surface. The $\sigma$-coordinate transformation is defined as:  
$\sigma = \frac{z - \zeta}{H + \zeta} = \frac{z - \zeta}{D} $

According to Khangaonkar et al. 2018: "The vertical configuration of the model uses 10 sigma-stretched layers distributed using a power law function with an exponent P-Sigma of 1.5, which provides more layer density near the surface." The FVCOM manual describes the power law function as:  
$\sigma(k) = (\frac{k-1}{k_b-1})^{P_{\sigma}}$  
where $k_b$ is the number of sigma levels while $k$ is the layer index (1, ... , $k_b$). For 10 layers and $P_{\sigma} = 1.5$ this would produce the following layers:  
| Layer | Upper σ | Lower σ | Thickness ∣Δσ∣ |
|:-----:|-----------------:|-----------------:|------------------------------:|
| 1 | 0.0000 | -0.0316 | 0.0316 |
| 2 | -0.0316 | -0.0894 | 0.0578 |
| 3 | -0.0894 | -0.1643 | 0.0749 |
| 4 | -0.1643 | -0.2530 | 0.0887 |
| 5 | -0.2530 | -0.3536 | 0.1006 |
| 6 | -0.3536 | -0.4648 | 0.1112 |
| 7 | -0.4648 | -0.5857 | 0.1209 |
| 8 | -0.5857 | -0.7155 | 0.1299 |
| 9 | -0.7155 | -0.8538 | 0.1383 |
| 10 | -0.8538 | -1.0000 | 0.1462 |

So the **bottom layer represents 14.6% of the water column**. This is the percentage we will use to compare to LiveOcean and SalishSeaCast "bottom" values. 
## Going into the code
ROMS has depth information stored in two forms, 'z_rho': the depth of the cell centers where values for DO and other variables are stored, and 'z_w': the depth of cell interfaces, so 'np.diff(z_w)' gives the thickness of each cell. The arrays are ordered bottom to surface.
