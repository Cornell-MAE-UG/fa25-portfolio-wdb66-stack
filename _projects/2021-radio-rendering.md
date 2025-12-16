---
layout: project
title: MAE 4272 Wind Turbine Blade
description: Fluid Mechanism Design
technologies: [Autodesk Inventor, MATLAB]
image: /assets/images/Blade.png
---

![Shaded rendering of earlier version]({{ "/assets/images/Weibull.png" | relative_url }}){: .inline-image-l style="width: 200px"}

For MAE 4272 Fluids and Heat Transfer Lab, we were tasked with designing a wind turbine blade to operate in our large wind tunnel. The wind velocity in the wind tunnel were provided to us using a Weibull Distribution which indicated that the most frequent windspeed was 4.76 m/s. There were additional geometric constraints to our design such as a max blade length of 6 inches and integrating to a standard hub geometry. Our blade was designed to output the maximum power at a windspeed 5.36 m/s and 2866 RPM.

Knowing our operating parameters and geometry constraints, the only thing left was to choose the airfoil profile to base our blade geometry off of. We decided to stick with the NACA airfoil family as they are common in wind turbines. We chose the NACA 4412 for its high CL/CD which should help improve output torque and efficiency. This leaves us with an optimal AOA of 8.5 degrees which was calculated using data on AirfoilTools.com with Re = 50,000.

![Shaded rendering of earlier version]({{ "/assets/images/Airfoil-Selection.png" | relative_url }}){: .inline-image-r style="width: 200px"}

To design our blade's taper and twist, we wrote a MATLAB script that uses Blade Element Momentum (BEM) to optimize these variables along the length of the blade. BEM analyzes small sections of the blade along its length and calculates its ideal chord among other variables. An important input parameter for BEM is the tip speed ratio which is how fast the blade tips move compare to the incoming wind speed. We chose a tip speed ratio of 7 which is commonly used in wind turbine designs like ours. Our model splits the blade up into 24 elements and takes 190 iterations to converge to a final geometry. This code helped us maximize the power output of each element in the context of the entire blade. This script predicted a power output of 3.1 W for our blade geometry.

![Photo of old radio]({{ "/assets/images/MATLAB_Blade.png" | relative_url }}){: .inline-image-r}

We had an additional MATLAB script to analyze the blade for structural failure. This code modeled the blade as a simplified beam in bending with a distributed load according to the load on each element. This output a very high safety factor of ~71 for our blade.

We tested our turbine in a large wind tunnel. The turbine assembly was mounted to a torque brake and RPM sensor which allowed us to collect output torque and RPM. The two variables we swept during our testing was wind tunnel RPM (wind speed) and torque brake voltage (torque applied to turbine at rotor). We started at a low wind tunnel RPM and zero torque brake voltage (no torque) and slowly increased torque brake until stall. Turbine RPM, wind speed, and torque data were collected at each torque increase interval. Using this data, we can easily calculate turbine power generation.

![Photo of old radio]({{ "/assets/images/Power-Curve.png" | relative_url }}){: .inline-image-l}

My primary contribution to the design was modeling the blades in CAD. While this was my main focus, I also contributed to overall performance targets and analysis.