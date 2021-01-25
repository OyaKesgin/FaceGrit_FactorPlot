# FaceGrit_FactorPlot
It s one of seaborn most powerful features is ability to combine multiple smaller plots into larger visualisations they can help identify trends and data with many variables. The concept of small multiples is useful for analysing data with many variables. You can quickly identify and analyse trends and data by comparing multiple plots by side by side in the same scale and axis. One very important requirement for seaborn creates this plots. the data must be in "tidy" format. This means each row of data is a single observation and columns contain the variables. Once the data in this format seaborn can perform a lot of heavy lifting needed to create this small graphs. Facegrid allows user to control how data is distributed across columns,rows and hue.
Once a Facegrid is created, the plot type must be mapped to the grid. Facegrid provides a lots of flexibility but you must use two processes.. Defining facegrit and plotting. Facegrid requires multiple steps..Factor plot is a short cut creating faster grids.
ref: DataCamp
# Create FacetGrid with Degree_Type and specify the order of the rows using row_order
g2 = sns.FacetGrid(df, 
             row="Degree_Type",
             row_order=['Graduate', 'Bachelors', 'Associates', 'Certificate'])

# Map a pointplot of SAT_AVG_ALL onto the grid
g2.map(sns.pointplot, 'SAT_AVG_ALL')

# Show the plot
plt.show()
plt.clf()

# Create a factor plot that contains boxplots of Tuition values
sns.factorplot(data=df,
         x='Tuition',
         kind='box',
         row='Degree_Type')

plt.show()
plt.clf()

# Create a facetted pointplot of Average SAT_AVG_ALL scores facetted by Degree Type 
sns.factorplot(data=df,
        x='SAT_AVG_ALL',
        kind='point',
        row='Degree_Type',
        row_order=['Graduate', 'Bachelors', 'Associates', 'Certificate'])

plt.show()
plt.clf()

# Create a FacetGrid varying by column and columns ordered with the degree_order variable
g = sns.FacetGrid(df, col="Degree_Type", col_order=degree_ord)

# Map a scatter plot of Undergrad Population compared to PCTPELL
g.map(plt.scatter, 'UG', 'PCTPELL')

plt.show()
plt.clf()

# Create an lmplot that has a column for Ownership, a row for Degree_Type and hue based on the WOMENONLY column
sns.lmplot(data=df,
        x='SAT_AVG_ALL',
        y='Tuition',
        col="Ownership",
        row='Degree_Type',
        row_order=['Graduate', 'Bachelors'],
        hue='WOMENONLY',
        col_order=inst_ord)

plt.show()
plt.clf()
