# Matplotlib Cheat Sheet

## Importing Matplotlib

```python
import matplotlib.pyplot as plt
```

## Basic Plotting

### Line Plot

```python
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]
plt.plot(x, y, label='Line')
plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.title('Line Plot')
plt.legend()
plt.show()
```

### Scatter Plot

```python
plt.scatter(x, y, label='Points', color='red', marker='o')
plt.legend()
plt.show()
```

## Customization

### Colors and Markers

```python
plt.plot(x, y, color='blue', linestyle='--', marker='o', markersize=8, label='Customized Line')
```

### Labels and Title

```python
plt.xlabel('X-axis', fontsize=12)
plt.ylabel('Y-axis', fontsize=12)
plt.title('Customized Plot', fontsize=14)
```

### Legends and Annotations

```python
plt.legend(loc='upper left')
plt.annotate('Important Point', xy=(3, 6), xytext=(4, 8), arrowprops=dict(facecolor='black', shrink=0.05))
```

## Subplots

### Creating Subplots

```python
plt.subplot(2, 2, 1)  # 2 rows, 2 columns, current plot is the 1st
plt.plot(x, y)

plt.subplot(2, 2, 2)  # current plot is the 2nd
plt.scatter(x, y)

plt.subplot(2, 1, 2)  # 2 rows, 1 column, current plot is the 2nd
plt.bar(x, y)
```

## Types of Plots

### Bar Plot

```python
categories = ['A', 'B', 'C', 'D']
values = [15, 24, 12, 30]
plt.bar(categories, values)
```

### Histogram

```python
data = [3, 5, 7, 7, 8, 8, 8, 9, 9, 9, 9, 10, 10, 11]
plt.hist(data, bins=5, edgecolor='black')
```

### Pie Chart

```python
labels = ['Apples', 'Bananas', 'Cherries', 'Dates']
sizes = [30, 25, 20, 15]
plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=140)
```

### Box Plot

```python
data = [randint(1, 100, 50), randint(1, 100, 50)]
plt.boxplot(data, labels=['Group A', 'Group B'])
```

## Saving and Displaying

### Saving to File

```python
plt.savefig('plot.png', dpi=300, bbox_inches='tight')
```

### Displaying Plot

```python
plt.show()
```

## Advanced Features

### 3D Plot

```python
from mpl_toolkits.mplot3d import Axes3D

fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
```

### Colormaps

```python
import numpy as np
x = np.linspace(0, 10, 100)
y = np.sin(x)
plt.scatter(x, y, c=y, cmap='viridis')
plt.colorbar()
```

### Annotations

```python
plt.annotate('Maximum', xy=(4, 1), xytext=(4, 1.5), arrowprops=dict(facecolor='black', shrink=0.05))
```

### Grid and Style

```python
plt.grid(True)
plt.style.use('seaborn')
```

---
**Note:** This cheat sheet is a reference guide and might not cover all scenarios. Always refer to the official documentation and consult with experienced developers for complex projects.

Feel free to create a pull request and customize and format this cheat sheet according to your preferences.
