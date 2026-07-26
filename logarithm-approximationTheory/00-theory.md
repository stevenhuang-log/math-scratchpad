# An Approximation for $\log_2(x)$
 
**Author:** Steven Huang <br>
**Date:** 2026-07-25 <br>
**Status:** Observation — verified numerically, proven for the general case <br>
**Tags:** `logarithms` `approximation` `error-analysis` 
 
---
 
## 1. The Observation
 
While building a table of $\log_2(x)$ by hand, I noticed something about the values between 1 and 2:

$$\log_2(1.b) \approx 0.b$$ 

**This means the decimal digit of the input becomes the decimal digit of the output.**

|$x$|$\log_2(x)$ (actual)|$0.b$ (my rule)|error|
|---|---|---|---|
|1.0|0.00000|0.0|0.00000|
|1.1|0.13750|0.1|0.03750|
|1.2|0.26303|0.2|0.06303|
| 1.3 | 0.37851 | 0.3 | 0.07851 |
| 1.4 | 0.48543 | 0.4 | 0.08543 |
| 1.5 | 0.58496 | 0.5 | 0.08496 |
| 1.6 | 0.67807 | 0.6 | 0.07807 |
| 1.7 | 0.76553 | 0.7 | 0.06553 |
| 1.8 | 0.84800 | 0.8 | 0.04800 |
| 1.9 | 0.92600 | 0.9 | 0.02600 |
| 2.0 | 1.00000 | 1.0 | 0.00000 |

- **First: Since the error is always positive, my approximation is always lower than the actual value.**
- **Second: The error rises and falls. It then peaks at $x = 1.4$.**


---

## 2. A Way to Play Around with the Idea
 
I wanted to approximate other values. Suppose we have
 
$$\log_2(k.b)$$
 
We can factor $k$ out, so it now looks like 

$$\log_2(k.b) = \log_2(k \cdot (1 + \frac{0.b}{k})) = \log_2(k) + \log_2(1 + \frac{0.b}{k})$$

 Since we know that $\frac{0.b}{k}$ equals a decimal. My rule from part one applies to the second term:
 
 $$\log_2(1 + \frac{0.b}{k}) \approx \frac{0.b}{k}$$
 
In conclusion:
 
$$\log_2(k.b) \approx \log_2(k) + \frac{0.b}{k}$$

### Checking

|$x$|my rule|actual|error|
|:---:|:---:|:---:|:---:|
|2.5|$1 + \frac{0.5}{2} == 1.25000$|1.32193|0.07193|
|3.2|$1.58496 + \frac{0.2}{3} = 1.65163$|1.67807|0.02644|
|7.5|$2.80735 + \frac{0.5}{7} = 2.87878$|2.90689|0.02811|

The errors are still positive, the same as section one.

### Notes
 
- **First: we can transfer the value to other bases by using the change of base formula $\log_2(a.b) = \frac{\log(a.b)}{\log(2)}$.**
- **Second: The key step is factoring $k$ out first. This turns the leftover decimal part into $\frac{0.b}{k}$ instead of $0.b$. Dividing by $k$ is what my earlier attempt was missing.**
- **Third: Notice that we still cannot approximate $\log_2(a.b)$ without a calculator, because the formula needs $\log_2(k)$ as an input. How about approximating $\log_2(k)$?**

> **Unresolved:** I have not yet measured how the error behaves when k grows larger and approaches infinity, so checking if the approximation works for every value might need another graph of $\log_2(k.5)$.
 
---
 
## 3. Next Steps
 
I will try to approximate $\log_2(k)$ next time by analyzing data.











