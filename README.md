# Atomic-Physics-Senior-Thesis

  This is my senior thesis for my Bachelor of Science in Physics at the University of North Texas. The theoretical/computational atomic physics thesis was six credit hours over the course of two semesters. Elastic, momentum, and differential cross sections, which relate to the probability of a collision event occurring, of various atomic systems involving electrons, positrons, positronium, helium, and hydrogen were analyzed and compared. Data needed for the calculations were aggregated from several sources and then compared through graphing. All results were obtained via Python using data science libraries such as SciPy, NumPy, pandas, and Matplotlib.
  
 Please see the references.md file for sources.

## Intro

  Helium was chosen as the focused target because of its compromise between theoretical and experimental ease. Of particular interest for comparison is the behavior of positronium-helium scattering. Even though the composition of positronium is a bound state of an electron and the positron, it has been shown experimentally that the elastic cross section of positronium-helium is very similar to electron-helium compared to the disparity between positronium-helium and positron-helium. What is also examined here is the potential similarity of these systems’ differential cross sections. The range of energies examined are constrained such that only the elastic channel is open; there is no possibility of excitation. All phase shifts used throughout were obtained from the literature or private communication, none were calculated.
  

## Theory

The total cross section,  $\sigma$,  is a measure of the likelihood of a scattering event and is expressed as an effective area. Incident particles go through an infinitesimal area $d\sigma$ and are then scattered though an infinitesimal solid angle $d\Omega$.  The differential cross section is the ratio between them and is given by:
$$\frac{d\sigma}{d\Omega} = {|f(k, \theta, \phi)|}^{2}\$$

$f(k, \theta, \phi)$ is the scattering amplitude. It can be shown that: $${|f(k, \theta)|}^{2} = \frac{1}{k^2} \sum_{l=0}^{\infty}\sum_{l^{'}=0}^{\infty}(2l+1)(2l^{'}+1)exp(i[\delta_l(k) - \delta_{l^{'}}(k)])sin(\delta_l)sin(\delta_{l^{'}})P_{l}(cos(\theta))P_{l^{'}}(cos(\theta))\$$

The phase shift $\delta_l(k)$ determines the interaction of each partial wave and is real. The differential cross section is a real measured quantity. It can be shown: $${|f(k, \theta)|}^{2} = \frac{1}{k^2} \sum_{l=0}^{\infty}\sum_{l^{'}=0}^{\infty}(2l+1)(2l^{'}+1)cos(\delta_l(k) - \delta_{l^{'}}(k) )sin(\delta_l)sin(\delta_{l^{'}})P_{l}(cos(\theta))P_{l^{'}}(cos(\theta))\$$ 

Calculating the imaginary component of the differential cross section readily shows that it is indeed 0, within numerical error. 

Integration of the differential cross section over all angles yields the total cross section.

$$\sigma_{tot}(k) = \int \frac{d\sigma}{d\Omega}d\Omega  = \int_{0}^{2\pi} d\phi \int_{0}^{\pi}d\theta sin\theta {|f(k, \theta, \phi)|}^{2}$$

Substitution of the scattering amplitude yields the total cross section.

$$\sigma_{tot}(k) = 2\pi\int_{0}^{\pi} \frac{d\sigma}{d\Omega}(k, \theta)sin(\theta)d\theta = \frac{4\pi}{k^2} \sum_{l=0}^{\infty}(2l + 1)sin^{2}\delta_l(k)$$
 This is the total cross section as represented by a sum of partial waves. Since the energies here only allow elastic scattering, $\sigma_{tot} = \sigma_{el}$. 
 
 The momentum transfer cross section is:

$$\sigma_{M}(k) = \int \frac{d\sigma}{d\Omega} (1 - cos\theta) d\Omega  = \int_{0}^{2\pi} d\phi \int_{0}^{\pi}d\theta (1 - cos\theta) sin\theta {|f(k, \theta, \phi)|}^{2}$$

The momentum transfer cross section can also be represented by a sum of partial waves.

$$\sigma_{M}(k)  =  \frac{4\pi}{k^2} \sum_{l=0}^{\infty}(l + 1)sin^{2}( \delta_{l+1}(k) - \delta_l(k))$$
