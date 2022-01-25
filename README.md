# Algorythms in Python

## Normal Distribution and simulation of AR(1) process

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
pdf_g = stats.norm.pdf(lnspc, m, s) # get theoretical values  
plt.plot(lnspc, pdf_g) # plot it

#QQ Plot
sm.qqplot(x,line='45')
```
![Alt-текст](https://github.com/anastasiia-belova/Algorythms-in-Python/blob/main/qq%20plot.png)

```python
# Plotting with seaborn library
import seaborn as sns; 
sns.kdeplot(x)
sns.kdeplot(x, shade=True, color="r")
sns.distplot(x)
sns.lineplot(data = x)

# Different Normal Distributions
xgrid = np.arange(-10, 10, 0.001)
x1 = stats.norm.pdf(xgrid, 2, 1)
x2 = stats.norm.pdf(xgrid, 0, 1)
x3 = stats.norm.pdf(xgrid, 0, 3)

plt.plot(xgrid,x1,label='N(2,1)',lw = 4)
plt.plot(xgrid,x2,label='N(0,1)',lw = 4)
plt.plot(xgrid,x3,label='N(0,3)',lw = 4)
plt.legend(fontsize = 20)
```
![Alt-текст](https://github.com/anastasiia-belova/Algorythms-in-Python/blob/main/Normal%20distributions.png)

```python
# Student t distribution with df = 5
xgrid = np.arange(-5, 5, 0.001)
df = 5
# Theoretical denisties
plt.plot(xgrid,stats.t.pdf(xgrid,df),label='t5',lw = 4)
plt.plot(xgrid,stats.norm.pdf(xgrid, 0, 1),label='N(0,1)',lw = 4)
plt.legend(fontsize = 20)

#Simulate
xn = np.random.normal(0,1,n)
xt = np.random.standard_t(df,n)
# Descriptive Statistics
stats.describe(xn)
stats.describe(np.sqrt((df-2)/df)*xt)
```
![Alt-текст](https://github.com/anastasiia-belova/Algorythms-in-Python/blob/main/student%20t%20distr.png)

```python
# Simulate an AR(1) process
# AR(1): y_t = phi*y_(t-1) + epsilon_t

burnin = 500; T = 1000+burnin; phi = 0.8
y= np.zeros((T,1)); e = np.random.normal(0,1,T)

for t in range(1,T):
    y[t] = phi*y[t-1] + e[t]

x = y[burnin:]

from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
# Plot things
fig, (ax, ax2,ax3) = plt.subplots(nrows=3) # create two subplots, one in each row
plot_acf(x,lags = 30,ax=ax)
plot_pacf(x,lags = 30,ax = ax2)
plt.plot(x)
plt.show()
```
![Alt-текст](https://github.com/anastasiia-belova/Algorythms-in-Python/blob/main/AR(1).png)
