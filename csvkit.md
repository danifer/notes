Convert .xlsx to .csv
    in2csv origin.xlsx > destination.csv

Return a range of columns from .csv
    csvcut -c 1-10 source.csv > destination.csv

Delete empty rows from .csv
    csvcut -x source.csv > destination.csv

Get data and statistics about a .csv file (such as finding empty columns)
    csvstat source.csv
