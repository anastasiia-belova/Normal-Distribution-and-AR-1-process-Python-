# Algorythms in Python

```python
# Simulate Standard Normal Distribution
mu, sigma = 0, 1 # mean and standard deviation
n = 5000 # length 
x = np.random.normal(mu, sigma, n)
# Plot data
plt.plot(x)
```
![Alt-текст](https://github.com/anastasiia-belova/Algorythms-in-Python/blob/main/Simulated%20data.png)

```python
# Histogram
plt.hist(x, bins = 30, color='#00CDCD')

```
![Alt-текст](https://github.com/anastasiia-belova/Algorythms-in-Python/blob/main/Histogram.png)


```python
# fitting the normal distribution 
m, s = stats.norm.fit(x) # get mean and standard deviation  
pdf_g = stats.norm.pdf(lnspc, m, s) # now get theoretical values in our interval  
plt.plot(lnspc, pdf_g) # plot it
#plt.show() 

#QQ Plot
sm.qqplot(x,line='45')
```

![Alt-текст](https://github.com/anastasiia-belova/Algorythms-in-Python/blob/main/qq%20plot.png)
