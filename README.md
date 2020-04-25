# OptiX-PathTracer-Direct-Lighting
Extra Implementation Results for [UCSD CSE 168 Rendering](http://cseweb.ucsd.edu/~viscomp/classes/cse168/sp20/168.html) assignments.

## Reduced Variance
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


Basic Stratified Sampling  | Stratified + Center       | Stratified + Analytic
:-------------------------:|:-------------------------:|:-------------------------:
![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/rv/direct3x3_ori.png)  |  ![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/rv/direct3x3_center.png) |  ![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/rv/direct3x3_analytic.png)
Bias 0 / Variance 3.8      |  Bias -0.2 / Variance 0.3 |  Bias 0 / Variance 0

- Note: The area light is not occlued by any objects, and therefore there is no noise in **Stratified + Analytic**.

Basic Stratified Sampling  | Stratified + Center       | Stratified + Analytic
:-------------------------:|:-------------------------:|:-------------------------:
![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/rv/sphere_ori.png)  |  ![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/rv/sphere_center.png) |  ![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/rv/sphere_analytic.png)
Bias 0 / Variance 2.8      |  Bias 0 / Variance 1.4 |  Bias 0.1 / Variance 1.4

## Point Lights
- Physically-based correct implementation
- Put point light at the location where the center of area is located

Only Area Light            |  Only Point Light
:-------------------------:|:-------------------------:
![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/point/cornell_ori.png)  |  ![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/point/cornell_point.png)

## Directional Lights
- Physically-based correct implementation
- Put directional light as the same directions where the area lights originally orient

Only Area Light            |  Only Directional Light   | 1 Area + 2 Directional    | 2 Area + 1 Directional
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/rv/sphere_center.png)  |  ![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/directional/sphere_directional.png) |  ![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/directional/sphere_directional_area.png) |  ![](https://github.com/yuyingyeh/OptiX-PathTracer/blob/master/directional/sphere_directional_area2.png)

