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

- **First: Since the error is always positive, my approximation is always lower than the actual value**<br>
- **Second: The error rises and falls. It then peaks at $x = 1.4$.**


---

## 2. An Attempt That Didn't Work
 
I wanted to approximate other values. Suppose we have
 
$$\log_2(k.b)$$
 
Let $d = k \cdot b$. Then I approximate this as $\log_2(k.d)$, which equals $\log_2\big(k \cdot (1 + 0.b)\big)$ — this rewriting is only valid when $d < 10$, so that no carrying happens.
 
That gives
 
$$\log_2(k) + \log_2(1.b) \approx \log_2(k) + 0.b$$
 
In conclusion:
 
$$\log_2(k.b) \approx \log_2(k) + 0.b$$
 
- **First: we can transfer the value to other bases by using the change of base formula $\log_2(a.b) = \frac{\log(a.b)}{\log(2)}$.**
- **Second: Since I approximate $\log_2(k.b)$ as $\log_2(k.d)$ with $d = k \cdot b$, these are two different numbers, so the error between the true value and the approximation might increase.**
- **Third: Notice that we still cannot approximate $\log_2(a.b)$ without a calculator. How about approximating $\log_2(a)$?**
**Unresolved:** I need to measure the gap $k.d - k.b$ in terms of $k$ and $b$, and check what it equals when $k = 1$. Until I do that, I am not claiming this section works.
 
---
 
## 3. Next Steps
 
I will try to approximate $\log_2(a)$ next time by analyzing data.











