---
tags:
  - "#Applied"
---
A Fourier transformation is a change of basis from the time domain to the frequency domain. Formally the Fourier transformation is defined as 
$$
F(\omega)=\int_{-\infty}^{\infty} f(t)e^{i\omega t}dt
$$
Which can be rewritten as 
$$
F(\omega)=\int_{-\infty}^{\infty}f(t)(\text{cos}(\omega t)-i\text{sin}(\omega t))dt
$$
Our function $F(w)$ takes in a frequency $\omega$ and returns a complex value. Then from this complex value we can find the phase and amplitude of the $\text{sin}(\omega t)$ wave. This allows us to decompose our function into a linear combination of $\text{sin}(\omega t)$ for different $\omega$ values. 

# Applications
- **Denoising Signals:** By taking a signal and only preserving the top highest strength signals you can remove background noise
- **Detecting Periodicities:** By looking through the periodogram and seeing if there are dominant signals you can find trends. An example might be looking at the brightness of a star and find out how many planets orbit around it. 
![[Pasted image 20251125191312.png]]