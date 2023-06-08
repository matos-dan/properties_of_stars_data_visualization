# Exploring Stellar Data with Data Visualization
This repository contains code snippets to analyze and visualize stellar data using R and the tidyverse and dslabs packages. To get started, make sure you have installed the required packages by running the following commands:

### 1- Install and load the necessary packages:

```
install.packages("tidyverse")
install.packages("dslabs")
library(tidyverse)
library(dslabs) 
```
###  2- Load the dataset and explore its contents:

```
data(stars)
dF_stars <- stars
show(dF_stars)
glimpse(dF_stars)
```
###  3- Plot a density plot of magnitude:
```
ggplot(data = stars, aes(x = magnitude)) +
  geom_density(fill = "lightblue", color = "black") +
  labs(x = "Magnitude", y = "Density", title = "Density Plot of Magnitude")
```
Graph:
Density Plot of Magnitude

![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/bc273f23-14f9-4629-827f-bc375e24d1fd)

###  4- Plot a histogram of temperature:
```
ggplot(data = stars, aes(x = temp)) +
  geom_histogram(binwidth = 0.1, fill = "lightblue", color = "black") +
  labs(x = "Temperature", y = "Count", title = "Distribution of Temperature") +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 16, face = "bold"),
    axis.title = element_text(size = 12),
    axis.text = element_text(size = 10),
    panel.grid.major = element_blank(),
    panel.grid.minor = element_blank(),
    panel.background = element_blank()
  )
```
Graph:
Distribution of Temperature

![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/3bb88618-9785-4e40-9dca-3c270391fd14)


###  5-  Plot a scatter plot of temperature vs. magnitude:
```
ggplot(data = stars, aes(x = temp, y = magnitude)) +
  geom_point(color = "blue", alpha = 0.5) +
  labs(x = "Temperature", y = "Magnitude", title = "Scatter Plot of Temperature vs. Magnitude")
```
Graph:
Scatter Plot of Temperature vs. Magnitude

![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/6c058e7a-2f74-49f9-bca8-c44e4bdfb22a)

###  6- Plot a scatter plot of temperature vs. magnitude with a reversed y-axis and logarithmic transformation on the x-axis:

Graph:
Scatter Plot of Temperature vs. Magnitude with Reversed Y-axis

![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/96345455-3408-4c65-a47e-304a08507786)

### 7- Plot a scatter plot of temperature vs. magnitude with a reversed y-axis, logarithmic transformation on the x-axis, and color-coded star types using a custom color palette:
```
star_colors <- c("#000000", "#AAAAAA", "#0022BB", "#22BB00", "#CCCCCC", "#CC00CC", "#CCCC00", "#00CC00", ...)
ggplot(data = stars, aes(x = log10(temp), y = magnitude, color = star)) +
  geom_point(alpha = 0.5) +
  labs(x = "log10(Temperature)", y = "Magnitude", title = "Scatter Plot of Temperature vs. Magnitude") +
  scale_y_reverse() +
  scale_x_reverse() +
  scale_color_manual(values = star_colors) +
  theme(legend.position = "none")
```
Graph:
Scatter Plot of Temperature vs. Magnitude with Color-Coded Star Types

![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/7b629750-39f1-4ffc-aba9-edd68c3a13c9)

### 8- Scatter Plot of Temperature vs. Star with Color Gradient
```
ggplot(stars, aes(x = temp, y = star, color = temp)) +
  geom_point(shape = 20, size = 4.5) +
  scale_color_gradient(low = "blue", high = "red") +
  labs(title = "Temperature Heatmap", x = "Temperature", y = "Star") +
  scale_y_discrete(expand = expansion(mult = c(0, -0.1))) +
  theme_minimal() +
  theme(
    axis.text.x = element_text(angle = 45, hjust = 1, vjust = 1),
    legend.position = "right",
    panel.spacing = unit(1, "lines")
  )
```
Graph:
Scatter Plot of Temperature vs. Star with Color Gradient

![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/06f74c53-bb6c-4e28-b694-bc7af16a7f8c)




### 9- Box Plot of Temperature with Outlier Labels
```
ggplot(stars, aes(y = temp)) +
  geom_boxplot(fill = "lightblue", color = "black") +
  labs(title = "Box Plot of Temperature", y = "Temperature") +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 16, face = "bold"),
    axis.title = element_text(size = 12),
    axis.text = element_text(size = 10),
    panel.grid.major = element_blank(),
    panel.grid.minor = element_blank(),
    panel.background = element_blank()
  ) +
  geom_text(data = subset(stars, temp > 26000), aes(x = 0, label = star), vjust = -1, hjust = -2, size = 3)
```
Graph:
Box Plot of Temperature with Outlier Labels

![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/053d02a2-435a-4983-9e12-51286cc52eee)

### 10- Box Plot of Temperature by Star Type
```
ggplot(stars, aes(x = type, y = temp)) +
  geom_boxplot(fill = "lightblue", color = "black") +
  labs(title = "Box Plot of Temperature", y = "Temperature") +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 16, face = "bold"),
    axis.title = element_text(size = 12),
    axis.text = element_text(size = 10),
    panel.grid.major = element_blank(),
    panel.grid.minor = element_blank(),
    panel.background = element_blank()
  )
```
Graph:
Box Plot of Temperature by Star Type

![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/067c4bd4-de55-45aa-a78a-62f5f415b278)

### 11 - Box Plot of Magnitude 
```
Graph
Box Plot of Magnitude 

ggplot(stars, aes(y = magnitude)) +
  geom_boxplot(fill = "red", color = "black") +
  labs(title = "Box Plot of Magnitude", y = "Magnitude") +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 16, face = "bold"),
    axis.title = element_text(size = 12),
    axis.text = element_text(size = 10),
    panel.grid.major = element_blank(),
    panel.grid.minor = element_blank(),
    panel.background = element_blank()
  )
```
![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/26d23aee-6203-410f-98b1-d99ac7621937)


### 12- Box Plot of Magnitude by Star Type
```
ggplot(stars, aes(x = type, y = magnitude)) +
  geom_boxplot(fill = "red", color = "black") +
  labs(title = "Box Plot of Magnitude", y = "Magnitude") +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 16, face = "bold"),
    axis.title = element_text(size = 12),
    axis.text = element_text(size = 10),
    panel.grid.major = element_blank(),
    panel.grid.minor = element_blank(),
    panel.background = element_blank()
  )

```
Graph
Box Plot of Magnitude by Star Type

![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/3eab7682-204a-44cb-96fe-a6055a00317a)


### 13- Density Plot of Magnitude and Temperature

```
ggplot(data = stars) +
  geom_density(aes(x = magnitude), fill = "lightblue", color = "black") +
  geom_smooth(aes(x = temp, y = magnitude), method = "loess", formula = y ~ x, fill = "lightgreen", color = "black", linetype = "dashed") +
  labs(x = "Temperature", y = "Magnitude Density", title = "Density Plot of Magnitude and Temperature") +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 16, face = "bold"),
    axis.title = element_text(size = 12),
    axis.text = element_text(size = 10),
    panel.grid.major = element_blank(),
    panel.grid.minor = element_blank(),
    panel.background = element_blank()
  )
```
Graph
Density Plot of Magnitude and Temperature

![image](https://github.com/matos-dan/properties_of_stars_data_visualization/assets/83671856/54715e89-5801-445e-8c32-01a0fba3beac)


###### Make sure to replace the placeholder path/to/ with the actual paths where you want to save the graphs. Once you have created the post on GitHub, you can embed the graphs by providing the respective image paths in the appropriate locations within the post.
