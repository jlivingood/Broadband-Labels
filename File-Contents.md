See also the File Name Format guide at https:\\github.com\jlivingood\Broadband-Labels\blob\main\File-Name-Format.md

## Contents of the file MUST be comma-separated

## Header of the file (first several fields) MUST mirror the file name, for consistency
### File names should be standardized according to this format:
HEADER, \
[Date when published, YYYY-MM-DD, fixed length] \
[Regulator Version, 3 digits, fixed length],  \
[Autonomous System Number, 10 digits, fixed length],  \
[Country Code, 4 digits, fixed length],  \
[Version number in two digits, starting from 00, fixed length],  \
[Unique ID of Tier, in 10 digits, fixed length],  \
[Advertised downstream speed in Mbps, variable length numeric field],  \
[Advertised upstream speed in Mbps, variable length numeric field],  \
[Access technology type ID, 4 digits, fixed length], \
[Termination Type, 2 digits, fixed legth], \
[Customer type ID, 4 digits, fixed length] \
LABEL-DETAILS, \
[Provider Name, up to 64 characters, variable length] ex: Xfinity Internet \
[Service Name, up to 64 characters, variable length] ex: Internet Extreme \
[Timeframe of Pricing, two digits, fixed length - see table below] ex: Post-Paid, Monthly \
[Monthly Price Is\Is Not an introductory rate, 1 number - either 0 for IS or 1 for IS NOT] ex: 0 \
[Conditional - IF price above = 0] [Introductory Period, in days, up to 3650 days, 4 numbers, fixed length] ex: 0090 \
[Conditional - IF price above = 0] [Monthly rate, 4 numbers, fixed length] ex: 0090 \


END-FILE \

## Timeframe of Pricing Table
00 - Pre-Paid, Hourly \
01 - Pre-Paid, Daily \
02 - Pre-Paid, Weekly \
03 - Pre-Paid, Monthly \
04 - Pre-Paid, Annual \
05 - Pre-Paid, Consumption-Based \
06-09 - Reserved for future pre-paid use \
10 - Post-Paid, Hourly \
11 - Post-Paid, Daily \
12 - Post-Paid, Weekly \
13 - Post-Paid, Monthly \
14 - Post-Paid, Annual \
15-19 - Reserved for future pre-paid use \
.. \ 
20-99 - Reserved for future use \ 

### Use Case:
A label published on March 19, 2024. It describes a Comcast tier in the US with a speed of 800\200 using DOCSIS and delivered to an residential consumer's user's home. 

## File Name Example: 
2024-03-19-0000007922-840-00-0000000002-800-200-001-001-0000.csv






[ISSUE: Should we leverage some type of certificate PKI system top validate the file?]
