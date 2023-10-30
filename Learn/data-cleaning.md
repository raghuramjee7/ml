# Data Cleaning

## Filling

1. **Get null counts of all columns** - `df.isnull().sum()`
2. **Imputation** - Setting the missing values in data using statistical techniques
3. **Drop Missing Values** - `df.dropna(axis = 1|0)` 0 - hori, 1 - vertical
4. **Fill null values** - `df.fillna("value")`
5. We can also fill them with the next non null value with - `df.fillna(method='bfill', axis=0)`

## Scaling and Normalisation

**Scaling** - We transform the data in such a way that all the data goes into a single scale (eg: 0-100, 0-1, etc)  
**Normalisation** - We change the data such a way that it fits a normal distribution. Here, after normalization the shape and distribution of data has changed.  

## Date Parsing
Pandas has a default `datetime64` type to denote datetypes.
1. `df[<col>] = pd.to_datetime(df[<col>], format="%m/%d/%y")`  
1/17/07 has the format "%m/%d/%y"  
17-1-2007 has the format "%d-%m-%Y"  
2. If we have rows with both formats of data, we can use inbuilt date inference with pandas - `pd.to_datetime(df['<col>'], infer_datetime_format=True)`. We dont always do this because a new type of incorrect date format might be there and also it is slow.  
3. We can get parts of the date from datetime64 by `df[col].dt.day|month|year`

## Character Encodings
We need to have proper encoding and decoding to read the files properly. 
1. `before.encode("utf-8", errors="replace")` encode a string
2. `after.decode("utf-8")` decode a string
3. `with open("<path>", 'rb') as rawdata: result = charset_normalizer.detect(rawdata.read(10000))` -  to check encoding confidence
4. `pd.read_csv("<path>", encoding='Windows-1252')` to decode the data propery
5. UTF-8 is the standard encoding in python. All data is encoded with that.

## Inconsistent Data


