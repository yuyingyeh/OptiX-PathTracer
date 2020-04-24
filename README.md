# OptiX-PathTracer
Extra Implementation Results for [UCSD CSE 168 Rendering](http://cseweb.ucsd.edu/~viscomp/classes/cse168/sp20/168.html)

## Homework 2 - Direct Lighting
### Reduced Variance
- Slightly increase bias but reduce variance by leaving the visibility term as the only term causing noise. Two options:
  * Use center of stratum as sampled points for BRDF and Geometric term.
    ```
    reducevariance center
    ```
  * Use analytic direct lighting formula to evaluate unshadowed irradiance for each stratum. (Test on diffuse surface.)
    ```
    reducevariance analytic
    ```
- Note: Not evaluating visibility at the center of stratum to reduce the noise is due to banding effect to which human visual system is sensitive.


Original                   |  Center                   | Analytic
:-------------------------:|:-------------------------:|:-------------------------:
![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/rv/direct3x3_ori.png)  |  ![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/rv/direct3x3_center.png) |  ![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/rv/direct3x3_analytic.png)
Bias 0 / Variance 3.8      |  Bias -0.2 / Variance 0.3 |  Bias 0 / Variance 0

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
