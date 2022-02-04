# Sales Rep

=IFERROR(VLOOKUP(Respicaire!$G3,Lookups!$A:$B,2,FALSE),"")



"=============="
"Rep Commission"
"=============="
"Current Logic:  Indexing the table on 'Commission Rates' for rate per company percentage"
=INDEX(Table1[#All],MATCH("Respicaire",Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(Respicaire!A3,Table1[#Headers],0))*$J3


"=================="
"Company Commission"
"=================="
=IFERROR((INDEX(Table1[#All],MATCH("Respicaire",Table1[[#All],[Commission Rates per Manufacturers]],0),MATCH(Table1[[#Headers],[Company Percentage]],Table1[#Headers],0))*$K3)-$B3,"")

"=================="
"Out of State (OOS)"
"=================="
=IFERROR(IF(AND(E3<>"TX",E3<>0,NOT(ISBLANK(E3))),"Y","N"),"")


"====="
"State"
"====="
=N3


"============"
"Account Name"
"============"
=R4

"===="
"City"
"===="
=O3

"========="
"Date Paid"
"========="
=DATE(YEAR(P3),MONTH(P3),1)

"==========="
"Invoice No."
"==========="
=S3

"========"
"Net Amt."
"========"
=U3
