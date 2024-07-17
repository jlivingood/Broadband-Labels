\newpage

Title: Draft Specification for Machine-Readable Broadband Internet Access Service Labels

**Executive Summary**

In the United States, the Federal Communications Commission (FCC) requires Internet Service Providers (ISPs) that serve consumers to publish a file containing information in the broadband labels in a machine-readable broadband format. This file is intended to more easily facilitate data collection by the FCC, as well as data aggregation by third parties so that anyone can build consumer-facing tools to help compare among service offerings. While every ISP could use their own unique format, it is more efficient for them and any users of these files if they used a common format. 

This document provides background on broadband labels and examines some of the options and issues associated with creating a machine-readable broadband labels file. It concludes by recommending a common format that uses a Comma Separated Value (CSV) file type and specifies a document schema to define each field that is required or optional in the file. The document also includes an example file in addition to the schema. This should be sufficiently flexible for any ISP to use and will save labor for ISPs and any users of these files. 

\pagebreak

# Introduction
In the United States, the Federal Communications Commission (FCC) [^FCC-website] has some 
regulatory authority over Internet Service Providers (ISPs). In FCC parlance, they define ISPs that 
serve consumers as providing a Broadband Internet Access Service (BIAS). Pursuant to federal legislation 
and a recent Order[^FCC-label-order], the FCC required BIAS providers (ISPs hereafter) to publish labels 
describing each BIAS offering to prospective customers or current customers at points of sale. For large 
ISPs, these rules went into effect April 10, 2024, and by October 10, 2024, for smaller providers. This requires 
that providers display clear and accurate information about the BIAS offering and disclose details like pricing, 
data allowances, and speeds, with links to network management practices and privacy policies. Looking ahead, the 
FCC will require so-called "machine-readable" broadband labels to be published for large ISPs on October 10, 2024. 
These machine-readable labels are intended to more easily facilitate third-party data aggregation so that 
anyone can build consumer-facing tools to compare among service offerings. 

[^FCC-website]: See https://www.fcc.gov.

[^FCC-label-order]: Empowering Broadband Consumers Through Transparency, CG Docket No. 22-2, Report and Order and Further Notice of Proposed Rulemaking, November 14, 2022. https://docs.fcc.gov/public/attachments/FCC-22-86A1.pdf

Machine-readable broadband access labels can be challenging due to the complex and varied nature of broadband networks and differences in the way different ISPs have implemented the FCC’s broadband labels rules. Broadband access can be provided through a variety of technologies such as fiber optics, DSL, cable, satellite, and wireless, each with its own set of specifications, configurations, pricing, taxes, frameworks, data allowances, and fees. Creating a standardized format that accurately represents each relevant aspect of the BIAS offerings of so many different ISPs can be difficult, as there may be intricacies that need to be taken into account. Furthermore, interoperability between different systems and platforms can be a challenge when it comes to machine-readable broadband labels. Different vendors and organizations may use different formats, protocols, and standards for encoding and interpreting these labels. Ensuring compatibility and seamless integration between various systems and platforms requires careful coordination and standardization efforts within the industry.

This paper explores the topic of machine-readable labels and why it is useful and more efficient for ISPs to voluntarily use a common format for such information. It explores some of the options, and makes recommendations about 
machine-readable labels and concludes with a sample template in the appendix.

# Background on FCC Broadband Label Rules 
## Background Information  

The FCC's labels Order [@FCCOrder] requires ISPs to publish a label for each BIAS offering that includes 
several specific service attributes, such as "typical speed". Large ISPs started publishing these on April 10, 2024. [^ISPPubs]. The Order further requires machine-readable labels by October 10, 2024, for large ISPs. But that Order left a great deal of flexibility for ISPs to determine how to meet that requirement and thus did not set any detailed requirements. The FCC, in May 2024, did attempt to clarify this somewhat with format suggestions, but these suggestions do not address how to capture some information that ISPs include in their labels, so they ultimately are insufficient. [@FCCFormat]

[^ISPPubs]: Examples include: https://support.google.com/fiber/answer/14119068#zippy=%2Cnutrition-labels%2Cgig; https://frontier.com/consumerlabels; https://www.risebroadband.com/residential/#broadband-label-modal-661715f754259; https://www.fidiumfiber.com/broadband-labels; https://fiber.google.com/broadband-labels/; https://ptera.com/nutrition-labels/; https://www.claropr.com/personas/servicios/servicios-moviles/internet-movil/#!; https://www.brctv.com/standard-pricing?area=58; https://www.midco.com/labels; https://www.sonic.com/broadband-facts; https://www.gci.com/showlabel?planId=F00015715612M256K10GBRBB


Specifically, the Order [@FCCOrder] laid out in paragraph 68, the following requirements. These requirements are further enumerated later in the document.
> Machine-Readable Format. We require providers to make the information included in
 the label available to the public in machine-readable format. By “machine-readable,” we mean
providing “data in a format that can be easily processed by a computer without human intervention while
ensuring no semantic meaning is lost.” Providers should make each label’s information available by
providing the information separately in a spreadsheet file format such as .csv. These files should be made
available on a provider’s website via a dedicated URL that contains all of a provider’s given labels. We
require providers to publicize the URL with the label data in the transparency disclosures required under
47 CFR § 8.1(a). These machine-readable files must provide the same categories of information as those
presented in each label, including the unique identifier described below. 

There are many potential uses for a standard format for machine-readable labels and the FCC suggested 
it can make the job easier and more efficient for ISPs. As the FCC noted [@FCCOrder]:
> ...machine readability will enable third
parties to more easily collect and aggregate data for the purpose of creating comparison-shopping tools
for consumers. These tools may include browser add-ons or websites that compare plans offered by
different providers. Making the information machine-readable also helps ensure that the data third
parties use is both accurate and up to date. Because providers often “adjust . . . [their] business
offerings,” we believe it may be simpler for them to “re-enter the new information and re-upload [their]
labels” in a machine-readable format.

To help provide ISPs with some direction, the FCC in May 2024, provided some additional voluntary guidance. [@FCCFormat][^FCCGuidance] But the sample FCC file had internal inconsistencies, made incorrect assumptions about pricing types, and had other issues that meant it alone was insufficient for providers to use in order to generate machine-readable labels. 
This document takes that guidance into consideration but also builds on it to provide a more complete and useful specification. 

[^FCCGuidance]: See https://www.fcc.gov/broadbandlabels#:~:text=Machine%2Dreadable%20format-,Data%20Specification,-%5BPDF%5D, https://www.fcc.gov/broadbandlabels#:~:text=Data%20Dictionary,CSV%20download, https://www.fcc.gov/sites/default/files/broadband_label_template.csv, https://www.fcc.gov/sites/default/files/broadband_label_template_with-example-data.csv

## Relevant Comments in the FCC Proceeding

In the Order adopting label rules, the FCC included footnotes referring to several comments pertaining 
to machine-readable labels. These are summarized below, as they are relevant to BITAG's discussion 
of the topic.

1. One organization recommended using a *consistent structured data format* and also suggested CSV and XML file types. [^AARP] 

2. Two organizations observed that machine readability would simplify the task of third parties to "compare service plans and their cost[s]". [^OTICR]

3. Two organizations suggested that machine-readable labels would "help ensure transparency of . . . measurement" by enabling third parties to collect such data. [^ILSRCF]

4. Several organizations observed that machine-readable labels would "facilitate the Commission’s collection of broadband pricing data". [^ILSRBJCR]

5. The FCC reiterated that "access to accurate, simple-to-understand information about Internet
access services helps consumers make informed choices and is central to a well-functioning marketplace" and
"enabl[es] consumers to comparison shop when choosing broadband services and providers that best meet their
needs and match their budgets". [^FN169]

6. New America's Open Technology Institute also filed an ex parte that urged the FCC to push for commonality. [^OTIexparte] This ex parte highlighted the downsides of having an inconsistent format across providers, problems in finding and downloading label files, and the need for a predictable file location address. 

[^AARP]: See AARP Reply at 9-11 in the [@FCCOrder].

[^OTICR]: See OTI Comments at 11; see also Consumer Reports Comments at 6.

[^ILSRCF]: See ILSR Comments at 7; see also Cloudflare Comments at 11.

[^ILSRBJCR]: See to ILSR Comments at 7; Boston Joint Commenters Reply at 8-9; see also Consumer Reports Comments at 6.

[^FN169]: See FN 169 of [@FCCOrder].

[^OTIexparte]: See (https://www.fcc.gov/ecfs/document/10514623225297/

# Enumerated FCC Requirements
The FCC Order included a number of requirements for machine-readable broadband label files. 
For ease of reviewing this document, those requirements are summarized here.

1. Provide data in a format that can be easily processed by a computer without human intervention while
ensuring no semantic meaning is lost.

2. Make each label’s information available by providing the information separately in a spreadsheet file format such as .csv.

3. Files must be made available on a provider’s website via a dedicated URL that contains all of a provider’s given labels.

4. Publicize the URL with the label data in the transparency disclosures required under 47 CFR § 8.1(a).

5. Files must provide the same categories of information as those presented in each label, including the Unique Plan Identifier (UPI) included on each label. The UPI begins with F or M to denote fixed or mobile plan followed by the broadband provider’s FCC Registration Number (FRN) and ending with a provider-chosen string of precisely 15 alphanumeric characters uniquely identifying the specific plan within the broadband provider’s offerings. [^FRNs] The UPI shall not include special characters such as, &, *, and %. The UPI must also be sufficiently distinctive so that third parties and the FCC can identify the specific plan identified by the unique identifier. Finally, the UPI must be unique and must never be reused, even if a given plan is no longer offered.
    
6. The file must include the monthly price exclusive of discounts, taxes, or fees. Introductory discounts, one-time or recurring fees and other contract requirements, such as early termination fees, must be included.
    
7. Links may be provided for discount information, data allowance policy, network management policy, privacy policy, and customer support. For customer support, a phone number may also be provided.

[^FRNs]: See list of FRNs at https://apps.fcc.gov/cores/simpleSearch.do?csfrToken=

# Usefulness of a Common Format

Open standards for broadband labels create many significant benefits,
including
including empowering consumers to choose the best Internet service option for
their needs, and enabling government officials to make more informed decisions
and interventions. 

Broadband labels provide consumers with easily accessible and understandable
information about available broadband services. 
Machine-readable labels enable software to collect, aggregate, and
compare labels easily as a result of a standardized file format, which can
enable researchers, academics, and civic society to quickly compare different
offerings based on factors such as speed, reliability, and pricing, ultimately
leading to more transparent and competitive markets. [^ACM] The ability to
perform such comparisons helps
consumers choose the best broadband option for their needs and ensures that
ISPs are held accountable for delivering the services they advertise.
Such a standardized format offers many benefits, as we outline in more detail
below.


## Increased Transparency, Market Efficiency, and Consumer Empowerment
Broadband labels provide clear, standard information about Internet service
offerings, allowing consumers to easily compare plans and make informed
decisions. Clear standards make it more difficult for ISPs to obscure
important details from customers. Apples-to-apples comparisons of broadband
services foster competition among providers, encouraging better performance
and lower prices. Easily accessible information reduces consumer search costs
and enables an efficient broadband marketplace. Mandatory disclosure also
makes it more difficult for providers to mislead customers about their
offerings relative to competitors.

Common formats for broadband labels can assist consumers with comparing
various aspects of Internet service provider plans. When metrics are
standardized across providers, consumers can easily compare different plans
based on factors such as speed, reliability, and pricing. This can help
consumers make more informed decisions about the broadband services they
purchase, potentially leading to more competitive markets and better service
offerings.

Consumer advocates can use machine-readable labels to analyze and compare
broadband plans across different providers, which can help them identify
trends in the broadband market. 

## Broadband Measurement Tools, Analysis, and Research

Machine-readable data allows third parties to develop comparison tools, search
engines, and other resources for consumers. Additionally, researchers and
analysts can better analyze and visualize broadband metrics across providers
and geographic areas, helping to identify issues and opportunities. Aggregated
data also enables evidence-based policymaking to address broadband needs and
market failures.

Developers of tools that measure broadband performance can use
machine-readable labels to design common measurement tools and pipelines
for collecting data on broadband plans from different providers. Such
standardization can also help developers of these tools develop common
metrics for measuring performance, as well as how those measurements can be
represented. 

Machine-readable broadband labels that are easy to find can offer
significant benefits for researchers, such as streamlining and enhancing the
scope and depth of broadband affordability studies. According to the FCC
Order, "broadband affordability research that is reliant on manual review of
existing provider advertising can be a time-consuming and laborious process
that many organizations are unable to undertake." Standard labels can
automate and expedite this data collection process, allowing researchers to
aggregate and analyze large-scale datasets efficiently, and identify trends in
the broadband market. 

According to the Institute for Local Self-Reliance, this facilitation of
research efforts presents "an excellent opportunity to allow researchers to
aggregate data at a large scale and analyze this data." A consistent and
comprehensive dataset across ISPs could enable researchers to conduct detailed
analyses of differences among providers, regions, and service offerings. Such
analyses can yield valuable insights for industry comparisons and help
correlate broadband services with general Internet trends and activities.

Furthermore, the ability to evaluate longitudinal changes to these labels can
help researchers and others spot trends in how broadband service offerings
evolve over time, enabling studies that analyze trends and draw correlations
with changing market conditions. These longitudinal insights are beneficial
not only for the academic community but also for industry stakeholders,
policymakers, consumers, and advocacy groups. By offering a clearer picture of
the marketplace, standard machine-readable broadband labels can drive
informed decision-making and foster a more competitive and transparent
broadband market.

## Streamlined Regulatory Compliance

Clear standards create bright-line rules for enforcing labeling commitments
that providers must follow, helping ameliorate regulatory risk. Customers can
more easily verify whether providers deliver the speeds and service levels
listed on the label. Comparative analyses between labels and typical
performance both insulate ISPs from incorrect claims of under-servicing and
provide an empirical basis for FCC investigations or penalties when
under-servicing occurs.

Standard machine-readable broadband labels can help regulatory agencies
streamline the process of monitoring compliance with current and future
regulations. As highlighted in the Order, "requiring ISPs to post
machine-readable label information will allow the Commission to more easily
collect data about broadband markets. Information collected via
machine-readable labels may also make monitoring for compliance with
Commission rules and enforcement more efficient as well." This enhanced
monitoring capability may lead to greater transparency, accountability, and
competition within the broadband market. 

## Promoting Accessibility and Inclusion

Standard machine-readable broadband labels not only benefit researchers
and regulatory bodies but also prioritize accessibility and inclusion. Labels
that present information clearly, in a machine-readable format, can also
facilitate assistive technologies such as text-to-speech (TTS) and machine
translation, thus making broadband information more accessible to a wider
range of consumers, potentially empowering underserved communities. Accessible and
comprehensible broadband data can help ensure that more consumers have access
to important information about available broadband service offerings.

# Unified Discovery & Validation of Broadband Labels

Given the utility of a common machine-readable file format, it seems that it would also be useful if there was a common way to find a provider's machine-readable labels. Websites, for example, already use well-known Uniform Resource Indicators (URIs, alternatively called a URL in the context of the web). The Internet Engineering Task Force (IETF) 
has specified a way to obtain well-known URIs in RFC 8615 [^RFC8615], which explains how these URIs are formatted 
and how to register them with the Internet Assigned Numbers Authority (IANA). A list of registered well-known 
URIs is available. [^IANA] 

[^RFC8615]: See https://datatracker.ietf.org/doc/html/rfc8615.

[^IANA]: See https://www.iana.org/assignments/well-known-uris/well-known-uris.xhtml.

An advantage of using a well-known URI for machine-readable broadband labels files is that implementation 
is up to each provider, and no one must centrally administer a registry of broadband label files. In general, 
that may be more sustainable over the long term than having some organization coordinate or track all 
providers updates.

## Well-Known URI

Following the release of this report, or in parallel with this report, a unique well-known URI can be registered with IANA. In this case, if the name 'broadband-labels' was registered, the corresponding well-known URI for 'https://www.example.com/' would be 'https://www.example.com/.well-known/broadband-labels'.

Another advantage of a well-known URI is that Transport Layer Security (TLS) [^TLS]  can be used to validate the file and securely transfer the file. In the example of 'https://www.example.com/', the URI is secured with TLS and there is a certificate associated with that website that the web browser (or other web client) will use to ensure that it is connecting to a trusted destination, and then the browser encrypts transport of the file itself. 

[^TLS]: See https://www.internetsociety.org/deploy360/tls/basics/ and https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/.

## Other Discovery Mechanisms

Another alternative to a well-known URI would be a centralized registry of ISP names with associated URIs for their respective machine-readable broadband label files. As noted above, the disadvantage to that approach is that some organization must serve as the central coordinator and tracker of any provider updates. If the provider's URI changes, 
a new provider enters the market, or if an existing provider is aquired or ceases operating, then the registry 
needs to be updated on a timely basis. For these and other reasons, it seems preferable to leave it to each provider to use a well-known URI (or not) rather than have a centralized registry. In essence, delegate responsibility to each provider to maintain a well-known URI rather than expect an organization to centrally coordinate changes.

# Extensibility and Backward Compatibility

It is reasonable to expect that this CSV schema will be updated in the future. It is thus important to ensure good extensibility for adding fields in the future, as well as maintaining backward compatibility with earlier versions. 
That means that for any future additions, new fields MUST be appended to the end of the schema, so that current fields 
are maintained in the order that they previously appeared. 

# Test Methodologies

Many of the fields of the broadband label, as well as this machine-readable file format, cite specific measurements. 
That includes fields such as upstream and downstream bandwidth, idle latency, and so on. The technical definition 
of these metrics and any associated test methodologies are not based on a specific standard and are out of scope of 
this document. 

# Privacy and Security Issues

In this section we develop best practices informed by a stakeholder analysis and
threat model to determine relevant parties and potential threats to consider.
[^RFC3552] contains some examples of potential security considerations that may
be relevant to Broadband Labels and the administrators deploying them.

This is meant only to address securing the machine-readable labels themselves and any 
inherent privacy and security issues that may apply. 

## Stakeholders

### Broadband Providers
Broadband providers are interested in being confident that their implementation
of broadband labels is in compliance with government requirements and that
making broadband labels available via the Internet incurs negligible additional
risk for their own security.

### Broadband Customers
Broadband customers are interested in being able to confirm that a label is
authentic and that it applies to them. They wish to be able to confidently use
labels to compare the price and level of service available from different
broadband providers.

### Governments / Regulatory Bodies

Governmental and regulatory bodies are interested in being able to confirm that
broadband providers are in compliance with broadband label requirements as well
as other requirements that can be tested via the broadband label's representations. 
Government agencies also intend to use broadband labels as a way of collecting 
data about the marketplace.

### Researchers / Public Interest Organizations

Public interest organizations are interested in being able to confirm that a
label is authentic and that it applies to a population of interest, and are
interested in being able to confidently enumerate the entire list of broadband
labels for a specific provider or a specific population of interest. Researchers
and public interest organizations are also interested in being able to confirm
that information provided in broadband labels are true, i.e., customer experiences
of performance and price are in line with the information provided in the label.

## Threat model

Broadband label providers should be prepared to defend against: attackers who
wish to take the label service offline; attackers who wish to impersonate the
provider or otherwise provide false information as if they were a given
provider; attackers who wish to gain access to private information through the
mechanism that is used to make the machine-readable labels available.

## Best practices for Privacy and Security

Providers should be aware of the need to encrypt the transport of label files,
so that they cannot be modified 'over the wire' in transport. By using TLS to do
so, they also use a chain of trust so that end users can validate the site on
which the provider's labels are stored. Labels should cover a reasonable number
of users, rather than one label for each user, so that it is not possible to
identify an end user based on the label.

Providers should maintain a well-documented and well-publicized mapping between
their common business names and the canonical location for their label. If
labels are hosted on the same domain name as the provider uses to communicate
with the public, a valid TLS connection to that domain name should be sufficient
for the first party receiving the label to verify its authenticity.
If labels are stored in a centralized repository or otherwise verified by third
parties (i.e., an entity which did not download the label itself and thus is
unable to confirm the validity of the TLS connection), the text of the label
file itself should include a digital signature using a key which is available
directly from the provider via a trusted channel (e.g., a well-known URI). If
these keys must be rotated, historical keys and their validity dates should be
maintained for a reasonable amount of time.

Providers should clearly separate the apparatus that provides these labels to
the public from the internal apparatus that generates the labels using internal
and/or proprietary data. This will provide both for stronger confidentiality
guarantees, e.g., if the server hosting the labels is compromised, internal data
related to generating those labels is not directly accessible. This separation
will also provide for stronger availability guarantees, because static files can
be aggressively cached and cheaply served even in the presence of DDoS attacks.

# Geographic Specificity

## Tax and Pass Through Fee Issues
A major concern expressed by providers during development of this paper is about how geographically precise the data in the machine-readable file should be. This is mainly due to the fact that government taxes and pass through fees vary from one city, county, or tax jurisdiction to another. For example, one provider suggested that since they offer roughly 450 products nationally, that they will need 450 machine-readable label files, each with roughly 33,000 applicable tax/fee jurisdiction rows. Investigating further, they noted that a city alone cannot be used, because some cities span multiple counties. While geographic tax/fee area identifiers exist in certain billing systems, these are proprietary to the vendors of those systems.

After we kicked off this paper, the FCC published additional guidance [@FCCFormat] that alleviated one of these issues, indicating clearly that providers can simply indicate whether the taxes are included or will vary. 

This left the issue of the variability of pass through fees. The group debated this extensively and considered options ranging from just saying "varies" to including a separate row for each potential pass through fee. But the latter option would result in tens of thousands of rows with little difference between rows other than one field. The group eventually settled on the option of a maximum value for this field (which could also be zero), which is all-encompassing and dramatically simplifies the file. 

## Address-Level Issues
A related issue is that product availability is address-specific. For example, one side of a street may be upgraded to a new technology like FTTP that offers symmetric multi-gigabit speed, while the other side of the street only supports older copper or HFC technology that has different speeds. This means for that city and even that block of a street that there can be a multitude of products available. Ultimately however, the machine-readable file is not intended to answer the question of exactly what is available at a consumer's specific address (according to the USPS there are over 166 millions addresses in the US [^USPS-FACTS]; it is not a replacement for the website-based individual labels shown to consumers or for broadband availability data that providers file with the FCC [^FCC-FORM477]. 

[^FCC-FORM477]: See https://www.fcc.gov/general/form-477-filings-internet-access-services.

[^USPS-FACTS]: See https://facts.usps.com/size-and-scope/

# Observations and Recommendations

## Observations
1. The US FCC has required that ISPs publish machine-readable labels, starting on October 10, 2024.
2. It is objectively better for providers to use a common format, as this makes it much easier and more efficient to consume, comprehend, and compare data. Such commonality can benefit providers, government, consumers, researchers, and others.
3. The sample file released by the FCC, while helpful, is insufficient to meet providers' needs.
4. A Comma Separated Value (CSV) file is one of the most common and easily consumed file types for this type of data.
5. A common way to discover these files across providers is important and will also make the consumption of the files much more efficient.
6. People and organizations consuming these files need secure mechanisms for validating the source and download of the files. They should also be assured that these files do not contain any data that would pose privacy challenges.
7. There are a multitude of tax and fee jurisdictions. While individually-provided labels on a website can be based on a specific street address, this presents complications for a machine-readable file intended to cover a provider's entire service area. Because these taxes and fees vary based on the service type, access network type, state, county, city, and so on, attempting to include each in the file would result in tens of thousands of rows for larger providers. This would not provide any meaningful comparison between different services to make the complexity of that undertaking worthwhile.
8. The machine-readable broadband label file is not a replacement for service availability tools or providers' current 
label websites that provide address-specific labels. 
9. Some providers may wish to include additional data, so the schema should include optional fields.
10. Some providers publish bandwidth as a range and others as one number, so the schema should accommodate either 
approach.

## Recommendations

All recommendations in this section will follow the use of case sensitivity 
described in RFC 8174:

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL
      NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED",
      "MAY", and "OPTIONAL" in this document are to be interpreted as
      described in BCP 14 [^RFC2119] [^RFC8174] when, and only when, they
      appear in all capitals, as shown here

[^RFC2119]: https://www.rfc-editor.org/rfc/rfc2119.html
[^RFC8174]: https://www.rfc-editor.org/rfc/rfc8174.html

1. The FCC SHOULD allow providers to use "fees will vary by tax jurisdiction" in the machine-readable labels file, since 
not doing so will result in an extraordinary number of rows in the file.
2. Providers MUST publish the file in CSV format and use the recommended CSV schema provided in this document.
3. Providers MUST publish their machine-readable labels using a well-known URI: 'https://www.example.com/.well-known/broadband-labels'.
4. Providers SHOULD use TLS in order to provide validation trust & transport security for obtaining labels via the well-known URI.
5. The CSV schema SHOULD include optional fields in order to make it more extensible, allowing providers to include supplemental information at their discretion without the need for a new CSV schema. 
6. Future versions of the CSV schema SHOULD be backward compatible.

\pagebreak

# Definition of Format

This section follows the use of case sensitivity 
described in RFC 8174:

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL
      NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED",
      "MAY", and "OPTIONAL" in this document are to be interpreted as
      described in BCP 14 [^RFC2119] [^RFC8174] when, and only when, they
      appear in all capitals, as shown here

## File Type

There are a variety of potential file types that could be used, such as CSV, XML, JSON, and others. Of all of the options, it appears that a Comma Separated Value (CSV) [^RFC4180] file is the most uniformly understood and easiest to use. For one, most relevant individuals know how to use a CSV file or have access to software that will automatically figure out how to open a CSV file. One downside may be that while a CSV file is universally known - it's difficult to extend a CSV file, since calculations are often built on fixed column - not by looking up the column header name or description. That can be mitigated to some extent by building in as many optional fields as we can conceive of in the first version, and by creating an accompanying data dictionary file that explains and defines each field, but is certainly a downside to using a CSV. 

[^RFC4180]: See https://www.rfc-editor.org/info/rfc4180.

On the other hand, JavaScript Object Notation (JSON) is also well-known in the research and technical communities and can be human-readable rather than just values separated by commas. There is also software that can convert a JSON file to a CSV file [^CSV-to-JSON], and it is easily extensible. 

[^CSV-to-JSON]: See https://www.csvjson.com/csv2json.

Based on the widespread use of CSV files, it seems this is the primary file that should be made available. ISPs can of course optionally consider generating a JSON file or other file types. 

## File Format
The CSV file uses the "text/csv" media (MIME) type [^RFC6838], which is defined in the IANA registry of MIME types [^IANACSV]. 

The character encoding of the CSV file MUST be UTF-8. 

When served over HTTP, the most common use case, the media type used in the Content-Type header MUST have 
the parameter of "charset=utf-8".

[^RFC6838]: https://www.rfc-editor.org/rfc/rfc6838.html
[^IANACSV]: https://www.iana.org/assignments/media-types/text/csv

### Format Guidelines Conform to RFC 4180
The format of the published CSV MUST adhere to RFC 4180 [^RFC4180]. 

That RFC defines several key formatting requirements, 
especially in Section 2, which requires close reading my operators. This covers a variety of requirements, such as 
that the format MUST use CRLF for line breaks (a.k.a. "Carriage Return, Line Feed" - CRLF), that you MAY 
use spaces within a field value, MAY use commas within a field value, and MAY use line returns within a field value. 
Please read RFC 4180 carefully to ensure format compliance.

This RFC 4180 format can be imported into recent versions 
of Microsoft Excel and LibreOffice, as well as other software clients.

[^RFC4180]: https://www.rfc-editor.org/rfc/rfc4180.html

The schema also follows the proposed standard guidelines in the U.K. National Archives CSV Schema 
Language version 1.2 [^githubCSV]. 

[^githubCSV]: https://digital-preservation.github.io/csv-schema/csv-schema-1.2.html.

### File Header Required
The CSV file MUST contain a header row. In addition, when served over HTTP (the most common case), the 
media-type used in the Content-Type HTTP header MUST have the parameter of "header=present".

While a file header is not strictly required for CSV files as defined in RFC 4180, it is required here 
because it provides a firm definition of field names without having to consult a separate file for this information.

The file header will appear on the first line of the file and will include each field name, separated by commas and 
ending with a line break (i.e., field_name,field_name,field_name CRLF). 

### Schema Version 1
This is the first version of the schema, version 1. Subsequent versions will increase one integer at a time,
from 1 to 2, and so on. The schema version MUST be listed in the media type of the file.

For example, "text/csv;header=present;charset=utf-8;schema-version=bblabel-1", with the "bblabel-1" part representing the first version of the broadband label schema. The second, when/if defined, would be "bblabel-2", then "bblabel-3" for the third, and so on.

Note: This document attempts to define a number of both required and optional fields. This is being done in a way to 
try to think to future needs and a variety of uses, because adding fields means adding columns to the definition of 
the CSV schema, and thus the definition of a new schema version.

### One Row is One Broadband Label
Each row represents a distinct broadband label and is delimited in the CSV file with a line break. 

## Format of File Name

Underscore characters and spaces MUST NOT be used in the file name.

The file name MUST follow this standard format in the order below. 

1. Date when published, in the ISO 8601 format [^ISO8601], with hyphens. Thus the format is YYYY-MM-DD, so 
2025-01-15 for example to represent January 15, 2025.

[^ISO8601]: See https://www.iso.org/iso-8601-date-and-time-format.html.

2. Regulator Unique Provide Identifier. This will vary by jurisdiction. In the United States for example, 
it will be the FCC Registration Number (FRN) [^FCCFRN]. 

3. Country Code, using the International Organization for Standardization 
(ISO) ISO 3166-3 format. This the "Alpha-3" code – a three-letter code that represents a country name, which is usually more closely related to the country name than the two-letter code. For example, the United States of America is USA and Canada is CAN. [^CC]

[^CC]: See https://www.iso.org/iso-3166-country-codes.html.

4. The provider MAY optionally include additional information in the field name (see the use of "ABCD" below). 
For example, the file might include "mobile" or "5g-fwa" in the name. 

Examples (non-exclusive): 2025-01-15-0003768165-USA.csv, 2025-01-15-0005937974-USA-ABCD.csv, 2025-01-15-0005937974-USA-mobile.csv

## File Contents
The file MUST contain the required fields. There are several optional fields which MAY also be included by 
providers. All these fields are all detailed below. If additional fields are defined in the future, the schema 
will need to be updated.

If any field does not apply, whether required or optional, then it MUST be left empty (null). 

All examples are non-exclusive.

### Required Fields
 
1. Date Published

Date when published, in the ISO 8601 format [^ISO8601], with hyphens. Thus the format is YYYY-MM-DD, so 
2025-01-15 for example to represent January 15, 2025.

Name: date_published

Type/Format: date

Examples: 2025-01-15, 2025-11-02, 2025-06-06


2. Regulator Name

Initially this will only be the FCC, but as it is possible that other regulators may wish to use this format, a 
regulator field is included.
This field MUST be in the file and MAY be used. If this field is empty, users of the file SHOULD assume the regulator is the FCC.

Name: regulator_name

Type/Format: string

Examples: FCC, OFCOM, ECOI, MIC
  
3. Regulator Version Number
   
If requirements ever change, as we expect they will, having a required version field will be very useful. Given that labels must be maintained historically, it will be useful to know that a particular historical or current label is compatible with a specific regulatory requirement version. This field will begin from 01 for the first version, with the next being 02, all the way up to 99. 
This field MUST be in the file and MAY be populated. If this field is not used or is not applicable it SHOULD be left empty.

If and when a regulator changes the requirements for these labels, a new version of the schema will also need to 
be published.

Field: regulator_version_number

Type/Format: numeric, range(01, 99)

Examples: 01, 02, 55, 77

4. Access Network Connection Type
A provider may need to update a specific label due to error, new data, or other reason. In this case a version number should be incremented, with the default first version being 1. 

This field MUST be in the file and MUST be populated. 

Field: connection_type

Type/Format: string 

Examples: fixed, mobile, satellite

5. FCC Registration Number (FRN). This is a 10-digit unique identifying number that is assigned to organizations doing business with the Commission. An organization can be issued a FRN through the FCC's Commission Registration System (CORES) or by filing FCC Form 160 [^FCCFRN]. The FRN is a required part of the label identification number (but if providers outside of the US use this schema, this field can be left empty). 
This field MUST be in the file and MUST be populated by providers in the US. For providers outside of the US, it MAY be left empty.

Name: fcc_registration_number

Type/Format: numeric, range(0000000000, 9999999999)

Examples: 0005937974, 0003768165, 0005937974

[^FCCFRN]: See https://www.fcc.gov/licensing-databases/commission-registration-system-fcc and https://www.fcc.gov/sites/default/files/form160.pdf.

6. Unique Plan Identifier (UPI). This is a combination of plan type (F or M), plus the FRN from above (up to 10 
numbers), plus an additional unique string of up to 15 characters.

The unique alphanumeric string part at the end of the UPI MUST only contain capital letters (A-Z) and numbers (0-9). 
It MUST NOT include any special characters or other delimiters such as hyphens. This part of the string is 
chosen by the provider.
This field MUST be in the file and MUST be populated by providers in the US. For providers outside of the US, it MAY be left empty.

Name: unique_plan_identifier

Type/Format: string, limited to a maximum of 26 characters, no special characters, no delimiters, all 
letters capitalized.

Examples: F0005937974TIER1, F0005937974ABCD12341234, F0005937974ABCDEFGHIJ12345

7. Network Technology Type. This defines the access network technology used for a given BIAS offering. This is a 
numeric field using FCC-defined technology codes, limited to no more than 3 digits length. (In the future, it may be better to register these codes with IANA and to maintain them globally, rather than on a regulator-specific basis.)

* If a Fixed plan type, refer to the FCC's Fixed Technology Codes [^FCCFTC]. For example, hybrid-fiber coaxial (HFC) is "40" and fiber to the premises (FTTP) is "50".

* If a Mobile plan type, refer to the FCC's Mobile Technology Codes [^FCCMTC]. For example, 3G is "300" and 5G is "500".
This field MUST be in the file and MUST be populated.

Name: network_technology_type

Type/Format: numeric, range (0, 999)

Examples: 40, 50, 500

[^FCCFTC]: See https://help.bdc.fcc.gov/hc/en-us/articles/5290793888795-Fixed-Technology-Codes.

[^FCCMTC]: See https://help.bdc.fcc.gov/hc/en-us/articles/6673022944155-Mobile-Technology-Codes.

8. Provider Name. Name of the BIAS provider delivering a specific service.
   
This field MUST be in the file and MUST be populated.
Name: provider_name

Type/Format: string, limited to 100 characters

Examples: Xfinity Internet, Comcast Business Class, T-Mobile, Google Fiber

9. Service Plan Name. Name of the provider's specific tier of service offered for sale. If a provider has only 
one service offering, it is possible this field will be empty.
This field MUST be in the file and MAY be populated.
Name: service_plan_name

Type/Format: string, limited to 100 characters

Examples: Extreme 500, Fiber 2G, Turbo 5G Plus

10. Download Bandwidth Units. The applicable bits per second of bandwidth.
This field MUST be in the file and MUST be populated.


Name: bandwidth_download_units

Type/Format: string, length(4)

Examples: kbps, Mbps, Gbps, Tbps, Pbps


11. Download Bandwidth, Marketed, Low. What the customer is being or has been sold. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If it is an absolute number, then it should generally be one to three digits, because after 999 then a new bandwidth unit is used. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MUST be populated.

Name: bandwidth_download_marketed_low

Type/Format: numeric, length(1-3)

Examples: 2, 75, 500

12. Download Bandwidth, Marketed, High. What the customer is being or has been sold. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If it is an absolute number, then it should generally be one to three digits, because after 999 then a new bandwidth unit is used. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MUST be populated.

Name: bandwidth_download_marketed_high

Type/Format: numeric, length(1-3)

Examples: 2, 75, 500


13. Download Bandwidth, Typical, Low. What the customer typically can expect to receive. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If it is an absolute number, then it should generally be one to three digits, because after 999 then a new bandwidth unit is used. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MUST be populated.

Name: bandwidth_download_typical_low

Type/Format: numeric, length(1-3)

Examples: 2, 75, 500

14. Download Bandwidth, Typical, High. What the customer typically can expect to receive. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If it is an absolute number, then it should generally be one to three digits, because after 999 then a new bandwidth unit is used. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MUST be populated.

Name: bandwidth_download_typical_high

Type/Format: numeric, length(1-3)

Examples: 2, 75, 500

15. Upload Bandwidth Units. The applicable bits per second of bandwidth.
This field MUST be in the file and MUST be populated.

Name: bandwidth_upload_units

Type/Format: string, length(4)

Examples: kbps, Mbps, Gbps, Tbps, Pbps

16. Upload Bandwidth, Marketed, Low. What the customer is being or has been sold. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If it is an absolute number, then it should generally be one to three digits, because after 999 then a new bandwidth unit is used. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MUST be populated.
Name: bandwidth_upload_marketed_low

Type/Format: numeric, length(1-3)

Examples: 2, 75, 500

17. Upload Bandwidth, Marketed, High. What the customer is being or has been sold. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If it is an absolute number, then it should generally be one to three digits, because after 999 then a new bandwidth unit is used. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MUST be populated.

Name: bandwidth_upload_marketed_high

Type/Format: numeric, length(1-3)

Examples: 2, 75, 500


18. Upload Bandwidth, Typical, Low. What the customer typically can expect to receive. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If it is an absolute number, then it should generally be one to three digits, because after 999 then a new bandwidth unit is used. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MUST be populated.

Name: bandwidth_upload_typical_low

Type/Format: numeric, length(1-3)

Examples: 2, 75, 500

19. Upload Bandwidth, Typical, High. What the customer typically can expect to receive. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If it is an absolute number, then it should generally be one to three digits, because after 999 then a new bandwidth unit is used. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MUST be populated.

Name: bandwidth_upload_typical_high

Type/Format: numeric, length(1-3)

Examples: 2, 75, 500

20. Latency, Idle, Low. This is a number, in milliseconds, of the typical idle latency a user will experience. 
Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MUST be populated.

Name: latency_idle_low

Type/Format: numeric, length(*,10)

Examples: 2, 75, 500

21. Latency, Idle, High. This is a number, in milliseconds, of the typical idle latency a user will experience. 
Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MUST be populated.

Name: latency_idle_high

Type/Format: numeric, length(*,10)

Examples: 2, 75, 500

22. Currency. Since it is possible that this machine-readable label specification may be used outside of the US, and 
for the avoidance of ambiguity, a currency code MAY be used. If it is empty, users of the file MUST assume that the 
currency is US Dollars.

This is limited to three characters in length and uses the International Organization for Standardization (ISO) 
ISO 4217:2015 format. This format specifies the structure for a three-letter alphabetic code and an equivalent three-digit numeric code for the representation of currencies. 

If this field is used, it MUST use the alphabetic codes in ISO 4217:2015, which are human-readable, as opposed to the numeric code. [^CurrencyCode]

[^CurrencyCode]: See https://www.iso.org/iso-4217-currency-codes.html.
This field MUST be in the file and MAY be populated. 

Name: currency

Type/Format: string, max length 3 characters

Examples: USD, GBP, EUR

23. Price Type. This describes whether a price is for pre-paid service, post-paid, per-line, and so on. In cases where the pricing is a combination of factors, the provider may choose to use the primary pricing type here and a qualifier in the next subsequent Price Type Details field, or may just choose Other here and define all details in Price Type Details.
It is highly recommended that the string value for this field be limited to the following options:
* Pre-Paid
* Post-Paid
* Volume-Based (example: per GB, per TB)
* Per-Line
* Per-Device (example: tablet, phone)
* Per-Location (example: per home, per office location)
* Per-Organization
* Per-Person
* Per-Time (example: per day, per month)
* Other 
This field MUST be in the file and MUST be populated. The subsequent price_type field SHOULD in some cases be used in conjuction with this field. For example, if the value of this field was Volume-Based, then price_type might be Per TB.

Name: price_type

Type/Format: string

Examples: Pre-Paid, Post-Paid, Per-Line


24. Price Details. This is a string intended to address instances where pricing is a combination or attributes, or 
something else we have not envisioned (given the dynamism of pricing mechanisms). In many cases this field may 
be empty. While this field MUST be used when price_type = 99 from above, it MAY also be used for other 
pricing types at the discretion of the provider.
This field MUST be in the file and MAY be populated.

Name: price_details

Type/Format: string

Examples: Requires activation of one new device., Price covers first 1 GB of data transferred. Data transfer billed at $1 per GB thereafter., For new customers only.

  
25. Recurring Price. This is how much a customer is charged on a recurring basis, if applicable, such as 
per month or per week, as defined above in price_type. This price MAY include two decimal places and is numeric.

7 digits plus two decimal places, fixed length (ex: price is $125/month, so value is 0000125)
This field MUST be in the file and MUST be populated.
Name: price_recurring

Type/Format: numeric, range(0000000.01-9999999.99)

Example: 29, 29.99, 399.00


26. Introductory Fee. If this is populated, it indicates that there is an introductory rate. If introductory 
price does not apply, then this field MUST be empty. 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.
Name: fee_introductory
Format/Type: Numeric 
Examples: 9, 9.99, 12.99

27. Introductory Fee Details. This is used to list the details of any introductory fee that may apply to a given BIAS offering. 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.
Name: fee_introductory_description
Format/Type: string
Examples: Only available to new customers., Fee for first three months., Fee for first three devices. 


28. Contract Required. Defines whether the price requires a contract and is either Yes or No.

This field MUST be in the file and MUST be populated. 

Name: contract_required

Type/Format: string, length(2,3)

Examples: Yes, No

29. Contract Details. If a contract is required, the field provides more information about the particulars. If 
there is no contract required, it is expected that this field will be empty.
This field MUST be in the file and MAY be used. If it does not apply, it SHOULD be left empty.
Name: contract_details

Type/Format: string

Examples: Contract is 1 year., Valid for first 3 months., Contract must be digitally signed within 7 days of installation.

30. Contract Terms Uniform Resource Indicator (URI). If a contract is required, then a URI MUST be provided in 
this field. If there is no contract required, it is expected that this field will be empty.
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.

Name: contract_terms_uri

Type/Format: identifier, uri

Examples: https://example.com/contract-terms/internet/, https://example.com/internet-contract/, 
https://example.com/legal/terms/contracts.html

31. One-Time Fee Amount. This is used to list the details of any one-time fees that may apply to a given BIAS offering. This price MAY include two decimal places and is numeric. 7 digits plus two decimal places, fixed length (ex: price is $125/month, so value is 0000125)
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.
Name: fee_one_time_amount
Type/Format: numeric, range(0000000.01-9999999.99)

Example: 29, 29.99, 399.00

32. One-Time Fee Details. This is used to list the details of any one-time fees that may apply to a given BIAS offering. 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.
Name: fee_one_time_details

Format/Type: string

Examples: Professional installation fee of $100 required., Shipping fee of $20 for sending equipment., $10 device 
provisioning fee.

33. Recurring Fees. If this is populated, it indicates that there are recurring fees, such as for the rental of a device.
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.
Name: fee_recurring
Type/Format: string
Examples: 9, 9.99, 12.99; 1.99


34. Recurring Fee Details. This is used to list the details of any recurring fees that may apply to a given BIAS offering. 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.
Name: fee_recurring_description
Format/Type: string
Examples: Monthly device rental., Cloud storage fee., Streaming video package; Sports package. 

35. Pass Through Fees (Maximum). If this is populated, it indicates that there are recurring pass through fees, such as a fee required by a particular city or county. This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.
Name: fee_pass_through_recurring
Type/Format: string
Examples: 9, 9.99, 12.99

36. Early Termination Fee. Defines whether there is a fee charged for early termination. If there is NOT a fee, then the value in this field should be zero (0). This fee MAY include two decimal places and is numeric. 
This field MUST be in the file and MUST be populated. If it does not apply, it MUST contain the value 0.
Name: fee_early_termination
 
Type/Format: string

Examples: 9.99, 100, Varies

37. Early Termination Fee Details. This is used to list the details of any early termination fees that may apply to a given BIAS offering. 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.
Name: fee_early_termination_description
Format/Type: string
Examples: $100 charged if service is terminated before the end of one year., $25, $10 for every month remaining in contract term.

38. Government Taxes. The field indicates whether any government taxes and fees are included in the price of a given BIAS offering. This may include those taxes and fees charged by franchise authorities, cities, states, the federal government, or other governmental or government-related entities.
This field MUST be in the file and MUST be populated. It is recommended that the value be one of these: Included, Varies, Not Applicable.
Name: government_taxes
Format/Type: string
Examples: Included, Varies, Not Applicable


39. Data Usage Policy Applies. Defines whether a given BIAS offering has a data usage policy and is either Yes or No.
This field MUST be in the file and MUST be populated. 

Name: policy_data_usage

Type/Format: string, length(2,3)

Examples: Yes, No

40. Data Usage Fee. Defines whether there is a fee charged for extra data usage. If there is NOT a fee, then the value in this field should empty. This fee MAY include two decimal places and is numeric. 
This field MUST be in the file and MUST be populated. If it does not apply, it MAY be left empty.
Name: fee_data_usage
 
Type/Format: string

Examples: 1, 10, Varies

41. Data Usage Fee Details. This is used to list the details of any data usage fees that may apply to a given BIAS offering. 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.
Name: fee_data_usage_description
Format/Type: string
Examples: $1 per GB after the first 1 TB., No fee but bitrates are reduced to 100 Mbps after 10 GB of usage., $2 per GB during peak times and $1 per GB during off-peak times.


42. Data Usage Policy Uniform Resource Indicator (URI). This is the URI for a data usage policy that 
may apply to a specific BIAS offering. 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.

Name: uri_data_usage

Type/Format: identifier, uri

Examples: https://example.com/data-usage/internet/, https://example.com/datausagepolicies, 
https://example.com/data-usage.html

43. Restrictions Apply, 1 number - either 0 for YES or 1 for NO] ex: 0
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.

Name: restrictions_apply
Type/Format: string
Examples: Site survey required, Qualified for a low-income offering, Mobile service only available to existing customers of wireline service

44. Network Management Policy Uniform Resource Indicator (URI). This is the URI for a network management policy that 
may apply to a specific BIAS offering. 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.

Name: uri_policy_network_management

Type/Format: identifier, uri

Examples: https://example.com/network-management/internet/, https://example.com/networkpolicies, 
https://example.com/network-management.html

45. Privacy Policy Uniform Resource Indicator (URI). This is the URI for a privacy policy that 
may apply to a specific BIAS offering. 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.

Name: uri_policy_privacy

Type/Format: identifier, uri

Examples: https://example.com/privacy/internet/, https://example.com/privacy-policies/, 
https://example.com/privacypolicy.html

46. Customer Support Information Uniform Resource Indicator (URI). This is the URI containing information 
about how to obtain customer support for a specific BIAS offering. 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.

Name: uri_customer_support

Type/Format: identifier, uri

Examples: https://example.com/support/internet/, https://example.com/support, 
https://example.com/support.html

47. Customer Support Phone Number. This is the telephone number a customer can use to contact customer 
support. The field MUST use the International Telecommunications Union (ITU), Telecommunication Standardization Sector (ITU-T) E.164-format telephone number. [^ITUE164] It MUST contain only numbers; no parenthesis marks, hyphens, periods, or other delimiting marks are permissible. For example, while a North American number may be represented variously 
as +1-800-555-1212, 1-800-555-1212, 800-555-1212, (800) 555-1212, 800.555.1212, or other format, this field MUST NOT 
contain non-numeric characters. If no customer support phone number is provided, this field MAY be left empty.
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.

Name: customer_support_phone

Type: numeric, length(*,15)
 
Examples: 18005551212, 18885551212, 12675551212

[^ITUE164]: See https://www.itu.int/rec/T-REC-E.164/.


### Additional Fields for Optional Use

48. Country Code: Since it is possible that this machine-readable label file specification may be useful 
outside of the US, an optional country code is included. This MUST be limited to three characters in fixed 
length. It MUST use the International Organization for Standardization (ISO) ISO 3166-3 format. 
This the "Alpha-3" code – a three-letter code that represents a country name, which is usually more closely 
related to the country name than the two-letter code. For example, the United States of America is USA and Canada is CAN. [^CC]

This field MUST be in the file and MAY be populated. 

Name: country_code

Format/Type: string, length(3)

Examples: USA, CAN, JPN

[^CC]: See https://www.iso.org/iso-3166-country-codes.html.

49. Autonomous System Number (ASN). It may be useful to include a provider's ASN in the file. One example 
of this may be that a researcher is collecting network measurements using source IP address, which can be 
used to identify the ASN, or ASN is part of the collected data (such as related to the Border Gateway Protocol, 
BGP, for routing security to see if a Route Object Authorization, ROA, was issued), making it easy for a 
researcher to find labels based on the ASN or to combine label files with their data. 

A complicating factor can be that some ISPs have several ASNs, though often these aggregate up into one primary ASN. In other cases, small ISPs may not have their own ASN and thus may be using the ASN of their upstream provider. For these reasons, this field is considered optional. 

ASN as maintained by the Internet Assigned Numbers Authority (IANA). [^ASN]  In North America, these are issued by the American Registry for Internet Numbers (ARIN). [^ARINASN] For US ISPs, the ARIN ASN list shall be used. [^ARINlist] Until 2007, ASN were defined as 16-bit integers, which allowed for a maximum of 65,536 assignments. But the IANA is now assigning 32-bit ASNs up to 4,294,967,295. As a result this field will be numeric and limited to 10 digits in length. 
This field MUST be in the file and MAY be populated. 

Name: asn

Format/Type: string, length(0,4294967295)

Examples: 7922, 14593, 701

[^ASN]: See https://www.iana.org/assignments/as-numbers/as-numbers.xhtml.

[^ARINASN]: See https://www.arin.net/resources/guide/asn/.

[^ARINlist]: See https://ftp.arin.net/info/asn.txt.

50. Additional Terms Uniform Resource Indicator (URI). This is the URI for any additional terms and/or 
policies that may apply to a specific BIAS offering. If nothing applies, this field should be left empty. If 
multiple policies apply, then URIs MUST be separated by a semi-colon.

This field MUST be in the file and MAY be populated. 

Name: uri_policy_additional_terms
 
Type/Format: identifier, uri

Examples: https://www.example.com/terms-of-service/, https://www.example.com/terms/;https://www.example.com/abuse/, https://www.example.com/anti-abuse/

51. Language. This field can optionally specify the language used in the machine-readable file. The default language shall be English. This field will use the ISO 639-3 format [^ISO639], which is a three letter format 
This field MUST be in the file and MAY be populated. If it does not apply, it SHOULD be left empty.
[^ISO639]: https://www.iso.org/iso-639-language-code
Name: language
Type/Format: string, length(3)
Examples: JPN, DEU, ITA

52. Latency, Working, Low. This is a number, in milliseconds. It latency under normal working conditions, otherwise known as latency under load. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MAY be populated.

Name: latency_working_low

Type/Format: numeric, length(*,10)

Examples: 2, 75, 500

53. Latency, Working, High. This is a number, in milliseconds. It latency under normal working conditions, otherwise known as latency under load. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MAY be populated.

Name: latency_working_high

Type/Format: numeric, length(*,10)

Examples: 2, 75, 500

54. Jitter, Low. This is a number, in milliseconds. It is the variability of working latency. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MAY be populated.

Name: jitter_low

Type/Format: numeric, length(*,10)

Examples: 2, 75, 500


55. Jitter, High. This is a number, in milliseconds. It is the variability of working latency. Depending on the type of service offered, this MAY be an absolute number or MAY be a range. If there is only one number, then the value for the respective "low" and "high" fields MUST be the same. When a range is appropriate, then the "low" and "high" numbers will differ. This field MUST be in the file and MAY be populated.

Name: jitter_high

Type/Format: numeric, length(*,10)

Examples: 2, 75, 500

56. Uptime. Also known as availability, and expressed as a percentage, with a maximum of 100% that would represent 
no outage time in a typical monthly period. This is a measure of up or down status of connectivity, and is 
not intended to represent degraded service periods. 
This field MUST be in the file and MAY be populated.
Name: uptime

Type/Format: numeric, range (0.0001,1.0000)

Examples: 0.9921, 1, 0.9899

\pagebreak

# Appendix: CSV Schema for Machine-Readable Broadband Labels
For more information please see this reference page. [^githubCSV2]

version 1.2
@totalColumns 56
name: BroadbandLabels
field1: range(0, 120)
field2: is("m") or is("f") or is("t") or is("n")

date_published: ???
regulator_name: string
regulator_version_number: range(01, 99)
connection_type: string
fcc_registration_number: range(0000000000, 9999999999)
unique_plan_identifier: string, length(\*,26)
network_technology_type: range (0, 999)
provider_name: string, length(\*,100)
service_plan_name: length(\*,100)
bandwidth_download_units: string, length(4)
bandwidth_download_marketed_low: numeric, length(1-3)
bandwidth_download_marketed_high: numeric, length(1-3)
bandwidth_download_typical_low: numeric, length(1-3)
bandwidth_download_typical_high: numeric, length(1-3)
bandwidth_upload_units: string, length(4)
bandwidth_upload_marketed_low: numeric, length(1-3)
bandwidth_upload_marketed_high: numeric, length(1-3)
bandwidth_upload_typical_low: numeric, length(1-3)
bandwidth_upload_typical_high: numeric, length(1-3)
latency_idle_low: numeric, length(\*,10)
latency_idle_high: numeric, length(\*,10)
currency: string, length(3)
price_type: string
price_details: string
price_recurring: numeric, range(0000000.01-9999999.99)
fee_introductory: numeric
fee_introductory_description: string
contract_required: string, length(2,3), is("Yes") or is("No")
contract_details: string
contract_terms_uri: identifier, uri
fee_one_time_amount: numeric, range(0000000.01-9999999.99)
fee_one_time_details: string
fee_recurring: string
fee_recurring_description: string
fee_pass_through_recurring: numeric
fee_early_termination: string
fee_early_termination_description: string
government_taxes: string
policy_data_usage: string, length(2,3), is("Yes") or is("No")
fee_data_usage: string 
fee_data_usage_description: string
uri_data_usage: identifier, uri
restrictions_apply: string
uri_policy_network_management: identifier, uri
uri_policy_privacy: identifier, uri
uri_customer_support: identifier, uri
customer_support_phone: numeric, length(\*,15)
country_code: string, length(3)
asn: string, length(0,4294967295)
uri_policy_additional_terms: identifier, uri
language: string, length(3)
latency_working_low: numeric, length(\*,10)
latency_working_high: numeric, length(\*,10)
jitter_low: numeric, length(\*,10)
jitter_high: numeric, length(\*,10)
uptime: numeric, range (0.0001,1.0000)

[^githubCSV2]: See https://digital-preservation.github.io/csv-schema/csv-schema-1.2.html.

\pagebreak

# Appendix: Sample Machine-Readable Broadband Label File
It should be possible to validate your file at https://digital-preservation.github.io/csv-validator/. 
*HOLD UNTIL LATER*
