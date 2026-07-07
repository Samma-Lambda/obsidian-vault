
## Preferences as relations
The preferences are encoded as encoded as posets meaning every single element either either $a\succ b$, $b \succ a$ meaning $a$ either outranks $b$, $a \sim b$ meaning $a$ is tied with $b$, or $a|b$ meaning they are incomparable.  

## Median Procedures
$A$ is a set of alternatives(things we are voting on), and $U$ is a set all possible posets on the elements of $A$.
There are $m$ voters and their $m$ relations which we are going to denoted as $\Pi=(R_1,...,R_m)$ which is called the profile
We define a distance metric on this space which is $d:U\times U\rightarrow \mathbb{R}$.
We define the remoteness between a relation $R$ and a profile $\Pi$ to be $\rho(R,\Pi)=\Sigma_{k=1}^{m}d(R,R_k)$. 
We let $O$ be a set of relations which are outputs, and $J$ be a set of relations which are inputs. 
For a profile $\Pi\in J^m$  the $O$ median is an element $M\in O$ such that $\rho (M,\Pi)=\min_{R\in O}\rho (R,\Pi)$  

Here is an example of this where we restrict $O$ and $J$ to linear posets and use bubble sort distance(number of swaps needed to be the same)
![[Screenshot 2026-06-15 at 11.38.03 PM.png|378]]


## Symmetric Difference 
The symmetric difference is a metric between relations is the minimal number of pairs you would need to remove or change to make two relations the same. This is low key a confusing definition so if you think of two posets as ordered pairs then its
![[Screenshot 2026-06-15 at 11.49.51 PM.png|377]]

Here we show posets that are all distance 1 from each other. Note that the very top is $\{(a,c),(c,b),(a,c)\}$ because the relation is transitive
![[Screenshot 2026-06-15 at 11.54.36 PM.png|417]]