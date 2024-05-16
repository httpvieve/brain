
# Definite Integrals $$\int_{a}^{b}f(x)dx$$
<p align = "center"> where a = start, b = end </p>
### GEOMETRIC INTERPRETATION: 
-> To find an area under a curve (cumulative sum)

![[Pasted image 20240516055500.png]]
> 
> 1. Divide into rectangles
> 2. Add up areas
> 3. Take the limit as rectangles get thin
> 

### Example 1: $f(x) = x^{2}  ; a = 0$

$$\sum \text{ Areas of } \space \square \space  =  \frac{b}{n}\space\cdot \left(\frac{b}{n}\right)^{2} + \frac{b}{n} \cdot \left(\frac{2b}{n}\right)^{2} + \ldots + \frac{b}{n} \cdot \left(\frac{nb}{n}\right)^{2} 
$$
$$= \left(\frac{b}{h}\right)^{3} \left( 1 + 2^{2} + 3^{2} + \ldots + n^{2}\right)$$

-----
### [[Theorem 2.1]] $$\forall_{x \ \in \ I} \ \exists_{C} \ | \  f'(x) = g'(x) \ \rightarrow \ f(x) = g(x) + C $$
-----
### [[Theorem 2.2]] 
F(x) + C = [[general antiderivative]], where C = arbitrary constant
$$  F'(x) = f(x)  \rightarrow \forall \int_{} f(x)dx = F(x) + C  $$

-----
### [[Theorem 2.3]] $$ \int dx = x + C$$

-----
### [[Theorem 2.4]] $$\int a \ \cdot f(x)  \ dx = a \int f(x) \ dx$$

-----
### [[Theorem 2.5]] $$\int [f(x) \ + \ g(x)] \ dx = \int f(x) \ dx + \int g(x) \ dx$$
-----
### [[Theorem 2.6]] $$\forall_{f} \forall_{c}: \int [c_{1}f_{1}(x) + c_{2}f_{2}(x) + \ldots + c_{n}f_{n}(x)] \ dx = c_{1}\int f_{1}(x) \ dx + c_{2}\int f_{2}(x) \ dx + \ldots + c_{n}\int f_{n}(x) \ dx  $$
-----
### [[Theorem 2.7]] $$ \int x^{n} dx = \frac{x^{n + 1}}{n + 1} + C \ \ \ ; \ \ \ n \neq -1$$
-----

#### ==EXAMPLE 1== : Find the most general antiderivative of the function $$g(t) = \frac{1}{\sqrt{t}}$$

### [[Indefinite Integrals]]
### [[Trigonometric Integrals]]

![[Pasted image 20240516222904.png]]



```PYTHON
  
bacteria_count = int(input("Enter initial count of bacteria: "))

hours = int(input("Enter the number of hours: "))

gen_time = int((hours * 60) / 20) 
  
print ("The number of bacteria per hour will be:")

replications = 2**gen_time 

for n in range(1, bacteria_count + 1):

        total = n * replications
        # case n = 1: printes = bacteria_count * replications per gen time
        print ("Hour " + str (n) + " = " + str(total))  
        
```

2(60) = 180 mins
$$
\frac{\text{1 gen time}}{\text{20 mins}} = \frac{???}{180 mins}
$$
for i in range (10)


a * b = ab
a ** b = $a^b$
![[Pasted image 20240516224648.png]]


$$
N_{t}= N_{0} \ \cdot 2^{n}
$$
2 hours -> 120 minutes 120/20 = 6 
1 2^1 = 2 2^2 = 4
2^N