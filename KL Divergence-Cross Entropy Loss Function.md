---
tags:
  - Applied
---
KL divergence is a way to measure the distance between probability distributions. This could be useful when detecting data drift or added to a cost function within machine learning to make the latent space model a specific distribution(Variational Auto-Encoders).

The cross entropy loss function is used in classification models which minimizes the KL divergence between the models distribution and the real world distribution


Image we have two probability distributions $P$ and $Q$, we an calculate the cross entropy which tells us the average number of bits required by for $Q$ if we approximated it using $P$. This is known as the cross entropy and is denoted $H(P,Q)$. The KL divergence is simply $H(P,Q)-H(P)$.  

![[Screenshot 2025-11-27 at 10.03.47 PM.png]]

In a real world setting you would just treat categorical variables as events with the probability seen in the data.


When you use the cost function cross entropy it ends up doing a monte-carlo approximation of the KL divergence between the true distribution and the actual distribution  