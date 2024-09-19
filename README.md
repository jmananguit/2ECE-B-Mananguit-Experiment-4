# 2ECE-B-Mananguit-Experiment-4
## ECE BOARD EXAM PROBLEM

### Filename: Instru = ["Name", "GEAS", "Electronics >70"]
### Track is constant as Instrumentation, and Hometown as Luzon

#### Import pandas library to be able to use phyton data analysis
``` python
import pandas as pd
```
#### Call the dataframe csv file named 'read.csv' and assign it to variable 'board'
``` python
board = pd.read_csv('board2.csv')
```

#### Subset every variable named 'Luzon' under the column 'Hometown',
``` python
board['Hometown']=='Luzon'
```
#### Subset every variable named 'Instrumentation' under column 'Track'
``` python
board['Track']=='Instrumentation'
```
#### Subset all values under 'Electronics' greater than 70
``` python
board['Electronics'] > 70
```
#### Use .loc() to subset all conditions and use & to create a condition where every condition must be true
``` python
data = board.loc[(board['Hometown']=='Luzon')&(board['Track']=='Instrumentation')&(board['Electronics'] > 70)]
```
#### Subset all the needed columns
``` python
Instru = data[['Name','GEAS','Electronics']]
Instru
```
>Output

![image](https://github.com/user-attachments/assets/5d7ce23e-7529-4dd9-bb83-7c9a6241114c)

## b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]
#### Where hometown is constant as Mindanao and gender Female
#### Subset every variable named 'Mindanao' under column 'Hometown'. 
``` python
board['Hometown']=='Mindanao'
```
#### Subset every variable named 'Female' under column 'Gender'.
``` python
board['Gender']=='Female'
```
#### Use .loc() to subset all conditions and use & to create a condition where every condition must be true
``` python
data2 = board.loc[(board['Hometown']=='Mindanao')&(board['Gender']=='Female')].copy() #use .copy() in order to create a duplicate dataframe
```
#### Get the mean from all subjects and assign a new column to the data frame called 'Average'
```
data2['Average'] = data2[['Math', 'Electronics', 'Communication','GEAS']].mean(axis=1)
#axis=1 indicates the column 
```
#### Subset all value of 'Average' greater than or equal to 55
``` python
Mindy = data2.loc[data2['Average']>=55]
```
#### Subset all the needed columns
```
Mindy[['Name', 'Track', 'Electronics', 'Average']]
```
> Output

![image](https://github.com/user-attachments/assets/0c9ecf1f-5bee-4e2a-a934-06c54274450d)

# 2. Create a visualization that shows how the different features contributes to average grade
#### In order to use plots and graphs, import the following;
``` python
import matplotlib.pyplot as plt
import seaborn as sns
```
## Box Plot
#### Get the mean from all subjects and assign a new column to the data frame called 'Average'
``` python
board['Average'] = board[['Math', 'Electronics', 'Communication','GEAS']].mean(axis=1).copy()
# .copy() creates a duplicate dataframe in which the .meaan() is performed
```
# Set up the figure for visualization
``` python
plt.figure(figsize=(20, 10))
```
## Plot 1: Average Grade by Track
#### Creates the first subplot in a 1-row, 3-column grid of subplots which is positioned at the first column
``` python
plt.subplot(1, 3, 1)
``` 
#### Create a boxplot of relation of Average to 'Track'
``` python
sns.boxplot(x='Track', y='Average', data=board, hue='Track', palette='Set2',legend=False)
```
#### Create the title of the boxplot
``` python
plt.title('Average Grade by Track')
```
#### Rotate the texts of types of tracks in order to fit within the figure size
``` python
plt.xticks(rotation=45)
```
## Plot 2: Average Grade by Gender
#### Creates the first subplot in a 1-row, 3-column grid of subplots which is positioned at the second column
``` python
plt.subplot(1, 3, 2)
```
#### Create a boxplot of relation of Average to 'Gender'
``` python
sns.boxplot(x='Gender', y='Average', data=board, hue='Gender',palette='Set1',legend=False)
```
#### Create the title of the boxplot
``` python
plt.title('Average Grade by Gender')
```
## Plot 3: Average Grade by Hometown
#### Creates the first subplot in a 1-row, 3-column grid of subplots which is positioned at the third column
``` python
plt.subplot(1, 3, 3)
```
#### Create a boxplot of relation of Average to 'Hometown'
``` python
sns.boxplot(x='Hometown', y='Average', data=board,hue='Hometown', palette='Set3',legend=False)
```
#### Create the title of the boxplot
``` python
plt.title('Average Grade by Hometown')
```
#### Adjust the spacings between the subplots
``` python
plt.tight_layout()
```
#### Prints the plots
``` python
plt.show()
```
>Output

![image](https://github.com/user-attachments/assets/47a712cf-9ebd-49cf-8e24-18353e55c8b8)

# Bar Graph
#### Set up the figure for visualization
``` python
plt.figure(figsize=(20, 10))
```
## Plot 1: Average Grade by Track
``` python
plt.subplot(1, 3, 1)
```
#### Create a bar plot of the average grade by 'Track'
``` python
sns.barplot(x='Track', y='Average', data=board, hue='Track', palette='Set2', errorbar=None)
```
#### Create the title of the bar graph
``` python
plt.title('Average Grade by Track')
```
#### Rotate the texts of types of tracks in order to fit within the figure size
``` python
plt.xticks(rotation=45)
```
## Plot 2: Average Grade by Gender
``` python
plt.subplot(1, 3, 2)
```
#### Create a bar plot of the average grade by 'Gender'
``` python
sns.barplot(x='Gender', y='Average', data=board, hue='Gender', palette='Set1', errorbar=None)
```
####Create the title of the bar graph
``` python
plt.title('Average Grade by Gender')
```
## Plot 3: Average Grade by Hometown
``` python
plt.subplot(1, 3, 3)
```
# Create a bar plot of the average grade by 'Hometown'
``` python
sns.barplot(x='Hometown', y='Average', data=board, hue='Hometown', palette='Set3', errorbar=None)
```
#Create the title of the bar graph
``` python
plt.title('Average Grade by Hometown')
```
#### Adjust the spacings between the subplots
``` python
plt.tight_layout()
```
#### Show the plots
``` python
plt.show()
```
>Output

![image](https://github.com/user-attachments/assets/d409db6c-ef9c-438c-860a-d05586620d12)

#### Does chosen track in college, gender, or hometown contributes to a higher average score?
#### In the case of track, by looking at the boxplot, it can be seen that the communcations track got the highest median, microelectronics got the second highest, and instrumentation got the lowest median of the three but the median of the tracks does not differ from each other much. By looking at the highest values of the three tracks, it can be seen that microelectronics got the highest score, followed by communications and instrumentation. 
#### By looking at the bar graph it can be seen that the chosen track does not contribute greatly to a higher average score as the averages of each track does not differ by much.
#### In the case of gender, by looking at the boxplot, it can be seen that the male students got a median score compared to the females but the females got a higher peak score. And by looking at the bar graph, it can be seen that the average score was found to be higher at males compared to females. Although once again, the differences between the two means does not differ by much.
#### Lastly, in the case of the hometowns, it can be seen in the both box plot and bar graph that Luzon had the highest average followed by Mindanao, then Visayas.
#### In conclusion, the chosen track in colleg, gender, or hometown does contributes to a higher average score albeit not by much. 

