
# Worksheet Global

## <a name="get-tab"></a>Get Tab/Worksheet Name

Retrieve the Tab/Worksheet Name and Insert into $B$1 for use within formulas.

```
=MID(CELL("filename",A1),FIND("]",CELL("filename",A1))+1,255)
```


# Sales Rep

```
=IF(ISBLANK($M5),"",VLOOKUP(INDIRECT(B6&"!$G5"),Lookups!$A:$B,2,FALSE))
```


# Rep Commission

## Final Formula with OOS replacement option with Error Check
Dependency: [Get Tab/Worksheet Name](#get-tab)

```
=IF(ISBLANK($M5),"",IFERROR((INDEX(Table1[#All],MATCH($B$1,Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(IF(INDEX($A:$J,ROW(),MATCH("OOS",$3:$3,0))="Y","Out of State of TX",INDIRECT($B$1&"!$A5")),Table1[#Headers],0))*$J5),""))
```

<details><summary>More Details</summary>
<p>

### We will need to pull the 'Out of State of TX' header match if OOS = Y 
Dependency: [Get Tab/Worksheet Name](#get-tab)
```
=INDEX(Table1[#All],MATCH($B$1,Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(INDIRECT($B$1&"!$A5"),Table1[#Headers],0))*$J5
```

### Get OOS Value
```
=INDEX($A:$J,ROW(),MATCH("OOS",$3:$3,0))
```

### Replace Rep with OOS Text if OOS = Y
Dependency: [Get Tab/Worksheet Name](#get-tab)
```
=IF(INDEX($A:$J,ROW(),MATCH("OOS",$3:$3,0))="Y","Out of State of TX",INDIRECT($B$1&"!$A5"))
```

### Final Formula with OOS replacement option
Dependency: [Get Tab/Worksheet Name](#get-tab)
```
INDEX(Table1[#All],MATCH($B$1,Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(IF(INDEX($A:$J,ROW(),MATCH("OOS",$3:$3,0))="Y","Out of State of TX",INDIRECT($B$1&"!$A5")),Table1[#Headers],0))*$J5```
```
</p>
</details>


# Company Commission
Dependency: [Get Tab/Worksheet Name](#get-tab)
```
=IF(ISBLANK($M5),"",INDEX(Table1[#All],MATCH($B$1,Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(INDIRECT($B$1&"!$A5"),Table1[#Headers],0))*$J5)
```


# Out of State (OOS)

```
=IF(ISBLANK($M5),"",IF(AND(E5<>"TX",E5<>0,NOT(ISBLANK(E5))),"Y","N"))
```

# State

```
=IF(ISBLANK($M5),"",INDEX($M:$AE,ROW(),MATCH(E$3,$M$3:$AE$3,0)))
```

# Account Name

```
=IF(ISBLANK($M5),"",INDEX($M:$AE,ROW(),MATCH(F$3,$M$3:$AE$3,0)))
```

#City

```
=IF(ISBLANK($M5),"",INDEX($M:$AE,ROW(),MATCH(G$3,$M$3:$AE$3,0)))
```

# Date Paid

```
=IF(ISBLANK($M5),"",(DATE(YEAR(INDEX($M:$AE,ROW(),MATCH(H$3,$M$3:$AE$3,0))),MONTH(INDEX($M:$AE,ROW(),MATCH(H$3,$M$3:$AE$3,0))),1)))
```


# Invoice No.

```
=IF(ISBLANK($M5),"",INDEX($M:$AE,ROW(),MATCH(I$3,$M$3:$AE$3,0)))
```

# Net Amt.

```
=IF(ISBLANK($M5),"",INDEX($M:$AE,ROW(),MATCH(I$3,$M$3:$AE$3,0)))
```
