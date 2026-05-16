#domain 
# What is SAR(Synthetic Aperture Radar)


### Notes: SAR image formation toolbox for MATLAB
We have a function representing the location of the phase center(the location the radar is being emitted from) denoted
$$
r_{-a}(\tau)=[x_a(\tau),y_{a}(\tau),z_a(\tau)]^{T}
$$
Also the distance from the coordinate $(0,0)$ is denoted as $d_a(\tau_n)$ 
$d_{a_0}(\tau_n)$ is the distance from a specific object to the phase center

The phase center emits pulses at transmission times $\{\tau_n|n=1,2,..n\}$ with each pulse and there are frequency samples received from each pulse $\{f_k|k=1,2,..,K\}$

The receiver receives output from target location 
$$
S(f_k,\tau_n)=A(f_k,\tau_n)\exp(\frac{-j4\pi f_k \Delta R(\tau_n)}{c})
$$
Where $A(f_k,\tau_n)$ determines the out of energy reflected back from an object. Note that some objects reflect different frequencies differently and the shape of the object is important.

$j$ is $\sqrt{-1}$ meaning this whole thing is a complex number 

$\Delta R(\tau_n)=d_{a_0}(\tau_n)-d_{a}(\tau_n)$ is the differential range which is distance from the plane wave to the object 

$4\pi$ is because of the spread out from the distance 

