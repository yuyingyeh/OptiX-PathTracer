# OptiX-PathTracer
Extra Implementation Results for [UCSD CSE 168 Rendering](http://cseweb.ucsd.edu/~viscomp/classes/cse168/sp20/168.html)

## Homework 2 - Direct Lighting
### Reduced Variance
- Slightly increase bias but reduce variance by leaving the visibility term as the only term causing noise. Two options:
  * Use center of stratum as sampled points for BRDF and Geometric term.
    ```
    reducevariance center
    ```
  * Use analytic direct lighting formula to evaluate unshadowed irradiance for each stratum.
    ```
    reducevariance analytic
    ```
- Note: Not evaluating visibility at the center of stratum to reduce the noise is due to banding effect to which human visual system is sensitive.

Before                     |  After
:-------------------------:|:-------------------------:
![](https://...Dark.png)  |  ![](https://...Ocean.png)

### Point Lights
- 

Before                     |  After
:-------------------------:|:-------------------------:
![](https://...Dark.png)  |  ![](https://...Ocean.png)

### Directional Lights
- 

Before                     |  After
:-------------------------:|:-------------------------:
![](https://...Dark.png)  |  ![](https://...Ocean.png)
