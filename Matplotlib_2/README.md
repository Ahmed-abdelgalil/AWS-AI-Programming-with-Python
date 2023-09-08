# Matplotlib 2

### Bivariate plots
1. **Scatter plots** : quantitative **VS** quantitative variables.
2. **Violin plots** :  qualitative **VS** quantitative variables.
3. **Clustered bar charts** : qualitative **VS** qualitative variables.

### Overplotting
- occurs when there is a high amount of overlap in points on a scatter plot, making it difficult to see the actual relationship between the plotted variables. This can happen when there are a large number of points or when the numeric variables are discrete-valued.

  **To solve** the problem of overplotting, there are several techniques you can use:
  1. *Sampling*: Instead of plotting all the data points, you can randomly select a subset of points to plot. This reduces the number of points and helps to reveal the underlying patterns. However, keep in mind that this approach may introduce some sampling bias.
  
  2. *Transparency*: By setting the transparency of the points, you can make the overlapping regions darker, while the less dense areas become lighter. This allows you to visually perceive the density of the data points and identify the areas of high concentration.
  
  3. *Jitter*: Jittering adds a small amount of random noise to the position of each point. This spreads out the points with the same values over a small area, making it easier to see the distribution and identify trends, especially when one or both variables are discrete.
