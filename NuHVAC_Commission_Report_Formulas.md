
# Worksheet Global

## <a name="get-tab"></a>Get Tab/Worksheet Name

Retrieve the Tab/Worksheet Name and Insert into $B$2 for use within formulas.

```ruby
=MID(CELL("filename",A1),FIND("]",CELL("filename",A1))+1,255)
```



# Sales Rep

```ruby
=IF(ISBLANK($M3),"",IF($D3="Y",VLOOKUP($E3,Lookups!$J:$K,2,FALSE),VLOOKUP($G3,Lookups!$A:$B,2,FALSE)))
```
* Check if Account Name is blank or not. (Used to determine if entry exists in data source columns to avoid N/A or Error)
* If OOS, then lookup State in Lookups.
* If NOT OOS, then lookup City in Lookups.


# Rep Commission

## Final Formula with OOS replacement option with Error Check
Dependency: [Get Tab/Worksheet Name](#get-tab)

```ruby
=IF(ISBLANK($M3),"",IFERROR((INDEX(Table1[#All],MATCH($B$2,Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(IF(INDEX($A:$J,ROW(),MATCH("OOS",$1:$1,0))="Y","Out of State of TX",$A3),Table1[#Headers],0))*$J3),""))
```
* Check if Account Name is blank or not. (Used to determine if entry exists in data source columns to avoid N/A or Error)
* If OOS, then lookup % in Commission Rates' OOS Column.
* If NOT OOS, then lookup % in Commission Rates' appropriate Sales Rep Column.


# Company Commission
Dependency: [Get Tab/Worksheet Name](#get-tab)
```ruby
=IF(ISBLANK($M3),"",INDEX(Table1[#All],MATCH($B$2,Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(C$1,Table1[#Headers],0))*$J3-$B3)
```


# Out of State (OOS)

```ruby
=IF(ISBLANK($M3),"",IF(AND(E3<>"TX",E3<>0,NOT(ISBLANK(E3))),"Y","N"))
```

# State
:information_source:	Generic/Pastable field lookup; pastable to any column.
This will find the current column's header in the source data lookup column header.

```ruby
=IF(ISBLANK($M3),"",INDEX($M:$AE,ROW(),MATCH(E$1,$M$1:$AE$1,0)))
```

# Account Name
:information_source:	Generic/Pastable field lookup; pastable to any column.
This will find the current column's header in the source data lookup column header.

```ruby
=IF(ISBLANK($M3),"",INDEX($M:$AE,ROW(),MATCH(F$1,$M$1:$AE$1,0)))
```

# City
:information_source:	Generic/Pastable field lookup; pastable to any column.
This will find the current column's header in the source data lookup column header.

```ruby
=IF(ISBLANK($M3),"",INDEX($M:$AE,ROW(),MATCH(G$1,$M$1:$AE$1,0)))
```

# Date Paid

```ruby
=IF(ISBLANK($M3),"",(DATE(YEAR(INDEX($M:$AE,ROW(),MATCH(H$1,$M$1:$AE$1,0))),MONTH(INDEX($M:$AE,ROW(),MATCH(H$1,$M$1:$AE$1,0))),1)))
```


# Invoice No.
:information_source:	Generic/Pastable field lookup; pastable to any column.
This will find the current column's header in the source data lookup column header.

```ruby
=IF(ISBLANK($M3),"",INDEX($M:$AE,ROW(),MATCH(I$1,$M$1:$AE$1,0)))
```

# Net Amt.
:information_source:	Generic/Pastable field lookup; pastable to any column.
This will find the current column's header in the source data lookup column header.

```ruby
=IF(ISBLANK($M3),"",INDEX($M:$AE,ROW(),MATCH(J$1,$M$1:$AE$1,0)))
```


# Conditional Formatting

## Out of State (OOS)


## Anything that is a formula
