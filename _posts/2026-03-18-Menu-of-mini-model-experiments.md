
## Menu of mini model experiments

I want to use this blog post to track ideas for LiveOcean learning.

My goal is to become familiar with the LiveOcean infrastructure beyond the user level to understand the model under the hood. What is included in my goal for user level learning is the grid set-up, initial conditions, and boundary conditions. To access the model under the hood there are perhaps two tracks:

**An interesting physical system on the existing ae0 grid**. The advantage of using the ae0 grid is that I do not need to remake forcing files and boundary conditions. Instead I can interrogate parameters such as:
- How mixing is represented: changing the turbulence
- Changing the drag coefficient for linear vs quadratic drag
- Creating assymetric flow. Penn cove is off of strong tidal currents through Saratoga Passage which enter more at the North. What do the currents on the shelf of the idealized grid look like? Can we impose strong Coriolis forcing as a way of doing this?

**A simplified subbasin on which to test biogeochemical 1D NPZD modeling**. 1D vertical dimension where I play around with changing parameters in Fennel/Banas. 

As I become more comfortable with the model, it is very valuable to be having model-observation data comparison, and even model-model-observation comparison happening in tandem with the SalishSeaCast and Salish Sea models. I can continuously ask questions of what becomes simplified or is left out. We are in a unique position to be collecting more biogeochemical data in Penn Cove including sediment cores from Western Washington's group with the goal of model validation. My hunch is that how they model the biogeochemistry and where this interacts with physical parameters is one of the biggest differences between them. When rerunning the analysis of hypoxic inlets using the updated version of LiveOcean that includes sediment burial, Aurora found that only 2 rather than 6 inlets went hypoxic. I think the sediment burial in LiveOcean is done using a mask to remove/bury, whereas Salish Sea model includes a fancy *sediment diagenesis module* which allows direct coupled interaction between the water column and sediments through the processes of organic sediment settling, burial, and remineralization. 

--------------------------------

### Interesting Physics
#### Estuarine circulation
*Motivating questions:* How do boundary conditions/initial conditions change the magnitude of exchange flow? This magnitude might be a point of sensitivity when comparing to SalishSeaCast and Ecology's Salish Sea Model, as this controls nutrients that are coming in from the ocean at depth (far and away the largest source of nutrient loading in Puget Sound). Explore tidally variable stratification over spring-neap tidal cycle-- are tides strong enough to weaken establishment of two layer flow?

*Next steps:*
- Identify what drives more exchange flow: try initial conditions half fresh half salty 

*Plots to explore:*
- Subtidally averaged velocity profiles to compare with CEWA570?

#### Atmospheric forcing (Upwelling Case) 
*Motivating questions:* Explore how introduction of wind can set up pressure gradient by creating a sea surface height tilt. How long wind stress at surface needs to be sustained to extend down to lake bottom opposing stratificiation which dampens eddy viscosity. This is like what happens in spring when nutrients are mixed up fueling blooms in the surface. Or what can happen to cause fishkills in Hood Canal when low DO water is mixed.

*Next steps:*
- Closed system? Flat shelf grid like [Aurora's blogpost](https://ajleeson.github.io/research_blog/2022/07/18/flat-shelf-upwelling-part-1.html)?

--------------------------------------------------------

### Layering in biogeochemistry
- Can we change parameters like residence time and make-up of incoming source water in subbasin?
- Do we see phytoplankton blooms (Chl in surface) in response to just nutrient concentrations coming in from the ocean/initial conditions? What if we add a point source?
- Does low bottom DO develop over time and with what kind of timelag? How much sustained stratification to set this up? 

-----------------------------------------

## Intermodel comparison learning points
Where models are different from eachother:
- implementation of biogeochemistry?
- role of boundary conditions?
- magnitude of estuarine circulation/ physical modeling differences?


