
# Worksheet Global

## <a name="get-tab"></a>Get Tab/Worksheet Name

Retrieve the Tab/Worksheet Name and Insert into $B$2 for use within formulas.

```ruby
=MID(CELL("filename",A1),FIND("]",CELL("filename",A1))+1,255)
```



# Sales Rep

```ruby
=IF(ISBLANK($M3),"",VLOOKUP($G3,Lookups!$A:$B,2,FALSE))
```


# Rep Commission

## Final Formula with OOS replacement option with Error Check
Dependency: [Get Tab/Worksheet Name](#get-tab)

```ruby
=IF(ISBLANK($M3),"",IFERROR((INDEX(Table1[#All],MATCH($B$2,Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(IF(INDEX($A:$J,ROW(),MATCH("OOS",$1:$1,0))="Y","Out of State of TX",INDIRECT($B$2&"!$A5")),Table1[#Headers],0))*$J3),""))
```

<details><summary>More Details</summary>
<p>

### We will need to pull the 'Out of State of TX' header match if OOS = Y 
Dependency: [Get Tab/Worksheet Name](#get-tab)
```ruby
=INDEX(Table1[#All],MATCH($B$2,Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(INDIRECT($B$2&"!$A5"),Table1[#Headers],0))*$J5
```

### Get OOS Value
```ruby
=INDEX($A:$J,ROW(),MATCH("OOS",$3:$3,0))
```

### Replace Rep with OOS Text if OOS = Y
Dependency: [Get Tab/Worksheet Name](#get-tab)
```ruby
=IF(INDEX($A:$J,ROW(),MATCH("OOS",$3:$3,0))="Y","Out of State of TX",INDIRECT($B$2&"!$A5"))
```

### Final Formula with OOS replacement option
Dependency: [Get Tab/Worksheet Name](#get-tab)
```ruby
INDEX(Table1[#All],MATCH($B$2,Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(IF(INDEX($A:$J,ROW(),MATCH("OOS",$3:$3,0))="Y","Out of State of TX",INDIRECT($B$2&"!$A5")),Table1[#Headers],0))*$J5```
```
</p>
</details>


# Company Commission
Dependency: [Get Tab/Worksheet Name](#get-tab)
```ruby
=IF(ISBLANK($M3),"",INDEX(Table1[#All],MATCH($B$2,Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(INDIRECT($B$2&"!$A5"),Table1[#Headers],0))*$J3)
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
