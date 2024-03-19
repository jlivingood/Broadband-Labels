# File names should be standardized according to this format:

[Date when published, YYYY-MM-DD, fixed length] - [Regulator Version, 3 digits, fixed length] - [Autonomous System Number, 10 digits, fixed length] - [Country Code, 4 digits, fixed length] - 
[Version number in two digits, starting from 00, fixed length] - [Unique ID of Tier, in 10 digits, fixed length] - 
[Advertised downstream speed in Mbps, variable length numeric field] - [Advertised upstream speed in Mbps, variable length numeric field] - [Access technology type ID, 4 digits, fixed length] - [Termination Type, 2 digits, fixed legth] - [Customer type ID, 4 digits fixed length] in a 
Comma Separated Value (CSV) file.

## Regulator Version
4 digit fixed length, specifies the version of label regulatory requirements that will presumably change over time \
00 - Initial version /
01 - First update - 2nd version /
.. /
99

## Autonomous System Number (ASN)
Use the fixed 10-digit ASN from regional internet registries to uniquely identify each ISP. \
See IANA ASN registry at https://www.iana.org/assignments/as-numbers/as-numbers.xhtml \
Example: AS7922 for Comcast in North America is issued by ARIN and can be found at https://whois.arin.net/rest/asn/AS7922 \
For further reading: https://www.arin.net/resources/guide/asn/

## Country Code (CC)
Four digit country code identifier \
Uses ISO 3166-1 numeric codes \
For references see the full list at https://www.iso.org/obp/ui/#search

## Version numbers: 
Start at 00 but increment to 01, 02, 03, and so on if corrections must be made. 

## Unique ID of Tiers: 
Fixed 10 digit length. Relative to each ISP; so two ISPs may have the same unique ID but within each ISP that ID must be unique. \
[ISSUE: Alternatively, have a national registry of tiers with each unique ID being nationally unqiue]

## Advertised speeds: 
Variable length numeric field, in Mbps without commas between thousands. So 800 Mbps is 800, and 1.2 Gbps is 1200. \
If the speed is UNDER 1 Mbps, then just mark this field as 1 to represent 1 or fewer Mbps. 

## Access Technology Type Table
0000 - DSL \
0001 - HFC DOCSIS \ 
0002 - Wi-Fi \
0003 - Unlicensed Wireless \
0004 - 4G Wireless \
0005 - 5G Wireless \
0006 - 6G Wireless \
0007 - 7G Wireless \
0008 - 8G Wireless \
0009 - 9G Wireless \
0010 - 10G Wireless \
0011 - Geostationary Satellite \
0012 - Low Earth Orbit Satellite \
0013 - Very Low Earth Orbit Satellite \
0014 - Balloon \
0015 - Airborne Drone or Airplane \
0016 - Point-to-Point Laser \
0017 - LoRaWAN  \
0018 - Dedicated (Direct) FTTP \
0019 - RFoG (RF Over Glass) FTTP \
0020 - GPON FTTP \
0021 - 10G-PON / XGS-PON FTTP \
0022 - 25G-PON FTTP \
0023 - 50G-PON FTTP \
0024 - 100G-PON FTTP \
0025 - EPON FTTP \
0026 - 25G-EPON FTTP \
0027 - 50G-EPON FTTP \
0028 - 100G-EPON FTTP \
.... \
9999 - TBD 

## Termination Type Table
00 - Fixed \
01 - Mobile \
.. \
99 - TBD 

## Customer Type Table
0000 - Consumer fixed location \
0001 - Consumer mobile location (i.e., boat, plane, recreational vehicle) \
0002 - Commercial fixed location \
0003 - Commercial mobile location (i.e., boat, plane, truck, rail) \
0004 - Consumer mobile user/device  \
0005 - Commercial mobile user/device \
0006 - Consumer robot \
0007 - Commercial robot \
.... \
9999 - TBD 

### Use Case:
A label published on March 19, 2024. It describes a Comcast tier in the US with a speed of 800/200 using DOCSIS and delivered to an residential consumer's user's home. 

## File Name Example: 
2024-03-19-0000007922-840-00-0000000002-800-200-001-001-0000.csv


