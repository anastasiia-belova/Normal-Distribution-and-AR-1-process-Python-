# Algorythms in Python

```
# Simulate Standard Normal Distribution
mu, sigma = 0, 1 # mean and standard deviation
n = 5000 # length 
x = np.random.normal(mu, sigma, n)
# Plot data
plt.plot(x)
```
![Alt-текст](https://github.com/anastasiia-belova/Algorythms-in-Python/blob/main/Simulated%20data.png)

```
# Histogram
plt.hist(x, bins = 30, color='#00CDCD',normed = True)

```
![Alt-текст](https://github.com/anastasiia-belova/Algorythms-in-Python/blob/main/Histogram.png)
