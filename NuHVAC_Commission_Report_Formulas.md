# Sales Rep

=IFERROR(VLOOKUP(Respicaire!$G3,Lookups!$A:$B,2,FALSE),"")


# Rep Commission

## Final Formula with OOS replacement option with Error Check

=IFERROR(INDEX(Table1[#All],MATCH("Respicaire",Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(IF(INDEX($A:$J,ROW(),MATCH("OOS",$1:$1,0))="Y","Out of State of TX",Respicaire!A3),Table1[#Headers],0))*$J3,"")

<details><summary>More Details</summary>
<p>

### we'll need to do the above rep calculation, however, will need to pull the 'Out of State of TX' header match if OOS = Y 
=INDEX(Table1[#All],MATCH("Respicaire",Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(Respicaire!A4,Table1[#Headers],0))*$J4

### Get OOS Value
=INDEX($A:$J,ROW(),MATCH("OOS",$1:$1,0))

### Replace Rep with OOS Text if OOS = Y
=IF(INDEX($A:$J,ROW(),MATCH("OOS",$1:$1,0))="Y","Out of State of TX",Respicaire!A4)

### Final Formula with OOS replacement option
=INDEX(Table1[#All],MATCH("Respicaire",Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(IF(INDEX($A:$J,ROW(),MATCH("OOS",$1:$1,0))="Y","Out of State of TX",Respicaire!A4),Table1[#Headers],0))*$J4

</p>
</details>


# Company Commission

=IFERROR((INDEX(Table1[#All],MATCH("Respicaire",Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(Table1[[#Headers],[Company Percentage]],Table1[#Headers],0))*$K3)-$B3,"")

# Out of State (OOS)

=IFERROR(IF(AND(E3<>"TX",E3<>0,NOT(ISBLANK(E3))),"Y","N"),"")

# State

=N3

# Account Name

=R4

#City

=O3

# Date Paid

=DATE(YEAR(P3),MONTH(P3),1)

# Invoice No.

=S3

# Net Amt.

=U3
