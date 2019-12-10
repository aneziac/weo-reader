# weo-reader


Download latest WEO data file from IMF web site as `weo.csv`, example:

```
curl -o weo.csv https://www.imf.org/external/pubs/ft/weo/2019/02/weodata/WEOOct2019all.xls
```

Caveat: `.xls` from the web site is really a CSV file.

Use `WEO` class from `weo.py` to view and extract data. `WEO` is a wrapper around a by-country pandas dataframe that ensures proper import and easier access to data.

Things to try in a REPL, by line:

```
from weo import WEO
w = WEO('weo.csv') 
w.vars()
w.units()    
w.units('Gross domestic product, current prices')
w.get('General government gross debt', 'Percent of GDP')
w.gdp_usd(2024).head(20).sort_values().plot.barh(title="GDP by country, USD bln (2024)")
```
