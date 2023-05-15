# powerbi-snippets
The data has a date column which have multiple dates in the Date column in data view, now, generate 3 columns from this column in table visualization and dynamically create a column header so that the 3 columns last 3 days sequentially. Power Bi.



Snipet 1

Last Day = 
VAR RankTable = ADDCOLUMNS('Table', "Rank", RANKX(ALL('Table'[Date]), 'Table'[Date], , DESC))
VAR LastDay = CALCULATE(MAX('Table'[Date]), FILTER(RankTable, [Rank] = 1))
RETURN
FORMAT(LastDay, "mmm dd")



Snippet 2



Second Last Day = 
VAR RankTable = ADDCOLUMNS('Table', "Rank", RANKX(ALL('Table'[Date]), 'Table'[Date], , DESC))
VAR SecondLastDay = CALCULATE(MAX('Table'[Date]), FILTER(RankTable, [Rank] = 2))
RETURN
FORMAT(SecondLastDay, "mmm dd")



Snippet 3


Third Last Day = 
VAR RankTable = ADDCOLUMNS('Table', "Rank", RANKX(ALL('Table'[Date]), 'Table'[Date], , DESC))
VAR SecondLastDay = CALCULATE(MAX('Table'[Date]), FILTER(RankTable, [Rank] = 3))
RETURN
FORMAT(SecondLastDay, "mmm dd")
