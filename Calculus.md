---
pure:
---
Calculus studies limits(how things act as a variable converges to a specific value), derivatives(The instantaneous rate of change of a function at a specific point along a specific direction), and integrals(a way of calculating the accumulated area underneath the curve at a specific point) 

# Derivatives 
Derivatives are the instantaneous rate of change of a function. Examples of which include taking a position graph and then creating a plot of its velocity, or taking the plot of the velocity graph and getting the graph of the acceleration. 
Another way that you can define the derivative is the slope of that it is a function which returns the value of the tangent line at a specific point 
![[Pasted image 20260801131917.png|226]]
## Limit Definition
The way we define a derivative is using limits. Limits are how something acts as a particular value converges to a specific number. Here is the limit definition, all other rules come from the limit definition and 
$$
f'(x) = \lim_{h \to 0} \frac{f(x + h) - f(x)}{h}

$$
## Differential Operators 
A differential operator is formally defined as a linear transformation within the domain of functions. 
$\frac{d}{dx}$ is the function which takes in some function and returns its derivative
$\frac{dy}{dx}$ is the image of a specific function when passed into $\frac{d}{dx}$ 

## Base Derivatives 
### Power Rule(Positive Integer Powers)
The power rule states that 
$$
\frac{d}{dx}x^n=nx^{n-1}
$$
which is incredibly useful when taking the derivative of polynomials. In order to prove this you need to use the limit definition(because we have no other rules) because of this we have
$\frac{d}{dx}[x^n]=\lim_{h \to 0}\frac{(x+h)^n-x^n}{h}$ which we can use the binomial theorem to expand out to be $\frac{(x+h)^n-x^n}{h}=\frac{x^n+nx^{n-1}h+\binom{n}{2}x^{n-2}h^2+...+h^n-x^n}{h}$  which makes our limit simplify to $\lim_{h \to 0}\frac{nx^{n-1}+\binom{n}{2}x^{n-2}h+...+h^{n-1}}{h}$ which as we take the limit we see all the terms with $h$ in it become $0$. Leaving us only $nx^{n-1}$ 
### $\sin(x)$
We can take the derivative of $\sin(x)$ using the limit definition 
$$f'(x) = \lim_{h \to 0} \frac{\sin(x+h) - \sin(x)}{h}$$
then the angle sum property 
$$f'(x) = \lim_{h \to 0} \frac{\sin(x)\cos(h) + \cos(x)\sin(h) - \sin(x)}{h}$$
then we factor getting $$f'(x) = \lim_{h \to 0} \left[ \sin(x) \cdot \frac{\cos(h) - 1}{h} + \cos(x) \cdot \frac{\sin(h)}{h} \right]$$
which then taking the limit of $\frac{\cos(h) - 1}{h}$ and  $\frac{\sin(h)}{h}$ we get get $0$ and $1$ respectively which then gives us $\cos(x)$. We can actually do something incredibly similar to find the $\cos(x)$ leading to this circle ![[Pasted image 20260801165553.png|221]] 



### Exponentials
To find the derivative of all exponentials we first need to start with finding $\frac{d}{dx}e^x$ using the limit we see 
$$\frac{d}{dx}\left[e^x\right] = \lim_{h \to 0} \frac{e^{x+h} - e^x}{h}$$
which we can factor out $e^x$ because it does not depend on $h$
$$= e^x \cdot \left( \lim_{h \to 0} \frac{e^h - 1}{h} \right)$$
which $e$ is defined to have a derivative of $1$ at $x=0$ thus we have proven that $\frac{d}{dx}e^x=e^x$ 

Now to find the derivative of general exponentials we see that 
$$a^x = \left(e^{\ln(a)}\right)^x = e^{x \ln(a)}$$Thus
$$\frac{d}{dx} \left[ a^x \right] = \frac{d}{dx} \left[ e^{x \ln(a)} \right]$$
Then using the chain rule we get 
$$\frac{d}{dx} \left[ e^{x \ln(a)} \right]= e^{x \ln(a)} \cdot \frac{d}{dx}\left[ x \ln(a) \right]$$
which works out to be $e^{x\ln(a)}\ln(a)=a^x\ln(a)$  


### Logarithmic Differentiation
This is use to take derivatives of functions such as $x^x$ or $\sin(x)^x$. We can apply any bijective monotonic function to an equation and it remains true. Thus in the situation $y=x^x$ we can change that into $\ln(y)=x\ln(x)$ which we then implicitly differentiate giving us $\frac{d}{dx}\ln(y)=\frac{d}{dx}x\ln(x)$ which can then be solved for $\frac{1}{y}\frac{dx}{dy}=\ln(x)+1$ which we then multiply by $y$ isolating it and getting $\frac{dx}{dy}=y(\ln(x)+1)$ but we can substitute back in $y=x^x$ giving us a final derivative of $\frac{dx}{dy}=x^x(\ln(x)+1)$ 
### Logarithms



## Combination Rules
### $\frac{d}{dx}$ is a linear operator 
To prove this we use the limit definition 
$$
\frac{d}{dx}\big[a \cdot f(x) + b \cdot g(x)\big] = \lim_{\Delta x \to 0} \frac{\big[a \cdot f(x + \Delta x) + b \cdot g(x + \Delta x)\big] - \big[a \cdot f(x) + b \cdot g(x)\big]}{\Delta x}
$$
which we can regroup into $$= \lim_{\Delta x \to 0} \frac{\big(a \cdot f(x + \Delta x) - a \cdot f(x)\big) + \big(b \cdot g(x + \Delta x) - b \cdot g(x)\big)}{\Delta x}$$
factor out the $a$ and $b$
$$= \lim_{\Delta x \to 0} \frac{a\big(f(x + \Delta x) - f(x)\big) + b\big(g(x + \Delta x) - g(x)\big)}{\Delta x}$$
split into two parts 
$$= \lim_{\Delta x \to 0} \left( a \cdot \frac{f(x + \Delta x) - f(x)}{\Delta x} + b \cdot \frac{g(x + \Delta x) - g(x)}{\Delta x} \right)$$
which then becomes $af^{\prime}(x)+bg^{\prime}(x)$ 


### Product Rule
This property if for finding $\frac{d}{dx}u(x)v(x)$ again for this we use the limit definition
$$\frac{d}{dx}[u(x)v(x)] = \lim_{h \to 0} \frac{u(x+h)v(x+h) - u(x)v(x)}{h}$$
then we add and subtract $u(x+h)v(x)$ which gives us 
$$\lim_{h \to 0} \frac{u(x+h)v(x+h) \mathbf{- u(x+h)v(x) + u(x+h)v(x)} - u(x)v(x)}{h}$$
which we factor getting
$$ \lim_{h \to 0} \left[ \frac{u(x+h)v(x+h) - u(x+h)v(x)}{h} + \frac{u(x+h)v(x) - u(x)v(x)}{h} \right]$$
$$ \lim_{h \to 0} \left[ u(x+h) \cdot \frac{v(x+h) - v(x)}{h} + v(x) \cdot \frac{u(x+h) - u(x)}{h} \right]$$
and then we apply limit laws
$$\left( \lim_{h \to 0} u(x+h) \right) \cdot \left( \lim_{h \to 0} \frac{v(x+h) - v(x)}{h} \right) + \left( \lim_{h \to 0} v(x) \right) \cdot \left( \lim_{h \to 0} \frac{u(x+h) - u(x)}{h} \right)$$
which gives us $$ u(x)v'(x) + v(x)u'(x)$$













### Chain Rule
Given a function $f(g(x))$ we can take the derivative of using the chain rule. It seems hard to prove so I am just going to state it $\frac{d}{dx}f(g(x))=f^\prime(g(x))g^{\prime}(x)$ 

### Quotient Rule
This is another rule that you can use for differentiation functions that are in the form $\frac{f(x)}{g(x)}$ and is easily remembered using the mnemonic "low d high minus high d low all over low squared". It can easily be derived using the chain rule by representing it as $h(x)=f(x)g^{-1}(x)$ then using the product rule we get
$$
\frac{d}{dx}[f(x)g^{-1}(x)]=(\frac{d}{dx}f(x))g^{-1}(x)+f(x)(\frac{d}{dx}g^{-1}(x))
$$
Now we are gonna just solve parts of this we know that $(\frac{d}{dx}f(x))=f^{\prime}(x)$ and that $\frac{d}{dx}g^{-1}(x)=-1g^{-2}(x)g^{\prime}(x)$. Thus we get $$\frac{dy}{dx} = \frac{f'(x)}{g(x)} - \frac{f(x)g'(x)}{[g(x)]^2}$$
which we then find a common denominator by multiplying the first fraction by $\frac{g(x)}{g(x)}$ which makes everything simplify to $$\frac{d}{dx}\left[ \frac{f(x)}{g(x)} \right] = \frac{f'(x)g(x) - f(x)g'(x)}{[g(x)]^2}$$





### Implicit Differentiation
A lot of time there are equations where instead of just getting an $x$ coordinate and then getting the derivative you need to input both and $x$ and $y$ coordinate. An example of this would be 
$$
x^2+y^2=1
$$
Note that $\frac{d}{dx}y^2=2y\frac{dy}{dx}$ 
Thus we take $\frac{d}{dx}(x^2+y^2)=\frac{d}{dx}1$ which is equivalent to $\frac{d}{dx}x^2+\frac{d}{dx}y^2=0$ which is the same as $2x+2y\frac{dy}{dx}=0$ which then we solve for $\frac{dy}{dx}=\frac{-x}{y}$ and now we can plug in points.

This works because you are always doing it when you take the derivative for example $\frac{d}{dx}(y=x^2+1)=(\frac{dx}{dy}=2x)$ but if you rearrange the equation to $\frac{d}{dx}(y-x^2=1)=(\frac{dx}{dy}-2x\frac{dx}{dx}=1\frac{d}{dx})=(\frac{dx}{dy}-2x=0)=(2x=y)$ I this is kinda weird I am thinking of these as curves in space      


# Trigonometry
This is actually just the study of triangles but it is incredibly useful within calculus to define oscillating motion. 
## Soh Cah Toa 
This is a basic for remembering how to calculate the lengths and angles of different sides of a triangle. Here are the definitions 
- $\sin(\theta)= \frac{\text{Opposite}}{\text{Hypotenous}}$  
- $\cos(\theta)= \frac{\text{Adjecent}}{\text{Hypotenous}}$
- $\tan(\theta)= \frac{\text{Opposite}}{\text{Adjecent}}$ 
And you can use the inverses of all of these functions to be able to recover the angle based of the side lengths. 
There are also the following functions
- $\sec(\theta)=\frac{1}{\cos(\theta)}$
- $\csc(\theta)=\frac{1}{\sin(\theta)}$
- $\cot(\theta)=\frac{1}{\tan(\theta)}$
Note that these systems of equations are not independent meaning we can get identities like $\tan(\theta)=\frac{\sin(\theta)}{\cos(\theta)}$  
## Soh Cah Toa to circles
As we can see below you can use $\sin$ and $\cos$ to be able to calculate the $y$ and $x$ coordinates on the circle directly. This can lead us to being able to derive tons of trigonometric identities such as $\sin^2(\theta)+\cos^2(\theta)=1^2$ from the pythagorean theorem 
![[Pasted image 20260801134720.png|380]]
## Angle Sum 
This proof relies on Euler's identity which states that $e^{i\theta}=\cos(\theta)+i\sin(\theta)$. Then we can see that
$$
e^{i(A+B)}=\cos(A+B)+i\sin(A+B)
$$
and that 
$$
e^{iA}e^{iB}=(\cos(A)+i\sin(A))(\cos(B)+i\sin(B))
$$
which when we distribute we get that it equals to 
$\cos(A)\cos(B) + i\cos(A)\sin(B) + i\sin(A)\cos(B) + i^2\sin(A)\sin(B)$ which simplifies to $[\cos(A)\cos(B)-\sin(A)\sin(B)]+i[\sin(A)\cos(B)+\cos(A)\sin(B)]$. In order to for two complex numbers to be equal both their real and imaginary components must be equal. Thus we have proven the following identities
$$
\cos(A+B) = \cos(A)\cos(B) - \sin(A)\sin(B)
$$
$$
\sin(A+B) = \sin(A)\cos(B) + \cos(A)\sin(B)
$$
## Parity 
We can easily see that $\cos$ is an even function(meaning $\cos(\theta)=\cos(-\theta)$) and that $\sin$ is an odd function meaning that $-\sin(\theta)=\sin(-\theta)$. 
We can see this by considering the coordinate $P=(\cos(\theta),\sin(\theta))$ and $P^{\prime}=(\cos(-\theta),\sin(-\theta))$. This is a reflection across the $x$ axis meaning that the $x$ coordinate stays the same(thus $\cos(\theta)=\cos(-\theta)$) and the $y$ coordinate becomes the negative version(thus $\sin(\theta)=-\sin(-\theta)$) 

## Periodicity
From just looking at the circle we can see that $\sin(\frac{\pi}{2}+\theta)=\cos(\theta)$, $\cos(\frac{\pi}{2}+\theta)=\sin(\theta)$, $\sin(\theta+2\pi)=\sin(\theta)$ and $\cos(\theta+2\pi)=\cos(\theta)$ 