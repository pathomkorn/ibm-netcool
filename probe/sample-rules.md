#IBM Tivoli Netcool Probe Sample Rules
## Extract information from text to variables using `scanformat` function
```
[ $intname1, $intid1, $devfqdn2, $intname2, $intid2 ] = scanformat( $clogHistMsgText, "Native VLAN mismatch discovered on %s (%d), with %s %s (%d)" )
```
* Adapt with pulling hostname from FQDN
```
[ $devname ] = scanformat( regreplace( $devfqdn, "\.", " " ), "%s" )
```
