# Pandas

Pandas deals with two different types of data structures - DataFrames and Series.  
1. **Create a DataFrame** - `pd.DataFrame({'Bob': ['I liked it.', 'It was awful.'], 'Sue': ['Pretty good.', 'Bland.']}, index=['Product A', 'Product B'])`   
2. **Create a Series** - `pd.Series([30, 35, 40], index=['2015 Sales', '2016 Sales', '2017 Sales'], name='Product A')`  
3. **Read CSV File** - `df = pd.read_csv("<path>", index_col = k)`. Pandas gives a default index, if we want to use a row in df as the index col, we specify that row index there.    
4. **Get the dimensions of df** - `df.shape`
5. **Get first k rows** - `df.head(k)` if no parameter was present, gives first 5 rows.  
6. We can access a df column by `df.row` or `df["row"]`
7. There are two ways to index in pandas, they are `loc` (location based selection) and `iloc` (index based selection).   
**iloc** - `df.iloc[:3, 0]`. iloc works row first, column second way. The indices are also inclusive. The parameters can be indices, slices, list of indices.  
**loc** - `reviews.loc[:, [<col_lst>]]`. loc is basically location based selection, we give out index names (can be 0-1 or any specified index) and column names accordingly.  
8. We can use conditional operators for loc like `reviews.loc[(reviews.country.isin(['Italy', 'France'])) & (reviews.points >= 90)]`. We can use it along with conditional operators, `isin()` fucntion is used for checking. we have other functions like `notnull()` etc. 
9. **Get info on dataset** - `df.describe()`
10. **Functions** - `df.column.mean()` `sum()` `unique()` `value_counts()` (get frequency of each unique value in the col), etc
11. **Map** - `df.col.map(lambda p: p - 1)`
12. **Apply** - `df.apply(<fn_name>, axis='columns')` - if we put axis as columns, the function is applied to each row, and the result returned by function is the updated row. For axis as index, the column is passed.
13. **Group By** - `df.groupby(['<col_list>']).col.agg_fn()` We need to have only agg functions like min, max, sum, we can also use apply() for getting query values. we have seperate agg functions like `groupby().col.agg([len, min, max])` this gives us the count, min and max values of that col. If we use multiple indices in groupby, we can reset the index by `df.reset_index()`
14. **Sorting** - We can sort values by `df.sort_values(by=['<col_name>'], ascending = True|False)`. We can sort through index by `df.sort_index()`
15. **Type** - `df.col.dtype`, `df.dtypes` - gives the datatypes of all columns
16. **Type Casting** - `df.col.astype('<new_type>')`
17. In pandas, if we have any missing data, it is filled with `NaN` which stands for not a number. This is by default a float64 value. We verify NaN by `isnull()` method. `df[pd.isnull(df.col)]`. This gives all the rows with null value of the given col. We can fill these NaNs with `fillna()` function - `df.col.fillna("value")`.
18. **Replace values** - `df.col.replace('oldval', 'newval')`
19. **Renaming** - We can rename both columns and indices with the rename function. Rename column - `df.rename(columns={'old_name': 'new_name'})`. Rename index - `df.rename(index={0: 'new_name', 1: 'new_name'})`. Both rows and columns have their own index name. we can rename that index by - `df.rename_axis("<new_name>", axis='rows').rename_axis("<new_name>", axis='columns')`
20. **Combining** - We can combine dfs with three methods - `concat()`, `join()` and `merge()`. We can achieve with join what we want to achieve with merge.
**Concat** - This will combine dfs based on the col names, and mush same col values together - `pd.concat([df1, df2])`.  
**Join** - This will join both the dfs based on the same index. 
```
left = canadian_youtube.set_index(['title', 'trending_date'])
right = british_youtube.set_index(['title', 'trending_date'])

left.join(right, lsuffix='_CAN', rsuffix='_UK')
```