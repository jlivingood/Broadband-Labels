See also the File Name Format guide at https:\\github.com\jlivingood\Broadband-Labels\blob\main\File-Name-Format.md

## Contents of the file MUST be comma-separated

## Header of the file (first several fields) MUST mirror the file name, for consistency
### File names should be standardized according to this format:

HEADER, 


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
[Customer type ID, 4 digits, fixed length] 


LABEL-DETAILS, 


[Provider Name, up to 64 characters, variable length] ex: Xfinity Internet \
[Service Name, up to 64 characters, variable length] ex: Internet Extreme \
[Timeframe of Pricing, two digits, fixed length - see table below] ex: Post-Paid, Monthly \
[Monthly Price Is\Is Not an introductory rate, 1 number - either 0 for IS or 1 for IS NOT] ex: 0 \
[Conditional - IF price above = 0] [Introductory Period, in days, up to 3650 days, 4 numbers, fixed length] ex: 0090 \
[Conditional - IF price above = 0] [Monthly rate, 4 numbers, fixed length] ex: 0090 
[Monthly Price Does\Does Not Require a Contract, 1 number - either 0 for DOES or 1 for DOES NOT] ex: 0 \
[Conditional - IF contract above = 0] [Duration of contract, in days, up to 3650 days, 4 numbers, fixed length] ex: 0090 \
[Contract Terms and Conditions, 1 number - either 0 for Terms Apply or 1 for No Terms Apply] ex: 0 \
[Conditional - IF terms apply above = 0] [URL for terms, 256 characters] ex: https://example.com/contract-terms/internet \
[Monthly Price] [Dollars, 7 digits, fixed length] ex: price is $125/month, so value is 0000125 \
[Monthly Price Does\Does Not Include One-Time Fees 1 number - either 0 for DOES or 1 for DOES NOT] ex: 1 \
[Conditional - IF one-time fees above = 1] [Fee amount in Dollars, 7 numbers, fixed length] 
    ex: one-time fee is $1,575, so value is 0001575 \
[Early Termination Fees Apply, 1 number - either 0 for DOES or 1 for DOES NOT] ex: 0 \
[Conditional - IF early termination fees above = 0] [Fee amount in Dollars, 7 numbers, fixed length] 
    ex: early termination fee is $99, so value is 0000099 \
[Govermment Taxes Apply, 1 number - either 0 for DOES or 1 for DOES NOT] ex: 0 \
[Conditional - government taxes apply above = 0] [Fee amount in Dollars, 7 numbers, fixed length] 
    ex: taxes are $24, so value is 0000024 \
[Discounts Available, 1 number - either 0 for YES or 1 for NO] ex: 0 \
[Conditional - IF discounts available above = 0] [URL for terms, 256 characters] ex: https://example.com/promotions/internet \
[Participates In Subsidy Program, 1 number - either 0 for YES or 1 for NO] ex: 0 \
[Conditional - IF subsidy program above = 0] [fixed length, 6 numbers, see table below] ex: ACP, so value = 000001 \
[Label downstream speed in Mbps, variable length numeric field],  ex: 800 Mbps = 800 \
[Label upstream speed in Mbps, variable length numeric field], ex: 200 Mbps = 200 \
[Label idle latency, in ms, variable length numeric field], ex: 15 ms = 15 \
[Label working latency, in ms, variable length numeric field], ex: 50 ms = 50 \
[Label uptime, in percent with 2 digits after the decimal, variable length numeric field], ex: 99.87% = 0.9987 \
[Network Management Policy, 1 number - either 0 for Yes or 1 for No] ex: 0 \
[Conditional - IF policy above = 0] [URL for policy, 256 characters] ex: https://example.com/network-management/internet \
[Privacy Policy, 1 number - either 0 for Yes or 1 for No] ex: 0 \
[Conditional - IF policy above = 0] [URL for policy, 256 characters] ex: https://example.com/privacy/internet \
[Support Information] [URL for support, 256 characters] ex: https://example.com/support/internet \
END-LABEL-DETAILS \
START-UNIQUE-ID \
The intent here is generate a unique one-time ID that represents the label file presented, when it was presented, and to whom it was prevented. This may subsequently be recorded in regulatory compliance systems and in customer records. 

Ex: \
File shown is named 2024-03-19-0000007922-840-00-0000000002-800-200-001-001-0000.csv \
Was shown 2023-03-19 at 14:23 UTC \
Customer account number is ABCD12345XZY \
So -- generate Unique ID = 2024-03-19-0000007922-840-00-0000000002-800-200-001-001-0000-2023-03-19-1423-ABCD12345XZY 

END-UNIQUE-ID 


END-FILE 


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
.. 
20-99 - Reserved for future use 

## Subsidy Program
000000 - None \
000001 - Affordable Connectivity Program \
000002 - 999999 - Reserved for future use 

### Use Case:
A label published on March 19, 2024. It describes a Comcast tier in the US with a speed of 800\200 using DOCSIS and delivered to an residential consumer's user's home. 

## File Name Example: 
2024-03-19-0000007922-840-00-0000000002-800-200-001-001-0000.csv 


[ISSUE: Should we leverage some type of certificate PKI system top validate the file?]
