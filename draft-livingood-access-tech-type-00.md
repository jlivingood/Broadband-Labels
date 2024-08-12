<?xml version="1.0" encoding="US-ASCII"?>
	<!-- 
	     draft-rfcxml-general-template-annotated-00
	  
	     This template includes examples of most of the features of RFCXML with comments explaining 
	     how to customise them, and examples of how to achieve specific formatting.
	     
	     Documentation is at https://authors.ietf.org/en/templates-and-schemas
	-->
	<?xml-model href="rfc7991bis.rnc"?>  <!-- Required for schema validation and schema-aware editing -->
	<!-- <?xml-stylesheet type="text/xsl" href="rfc2629.xslt" ?> --> 
	<!-- This third-party XSLT can be enabled for direct transformations in XML processors, including most browsers -->
	
	<!DOCTYPE rfc [
	  <!ENTITY nbsp    "&#160;">
	  <!ENTITY zwsp   "&#8203;">
	  <!ENTITY nbhy   "&#8209;">
	  <!ENTITY wj     "&#8288;">
					]>
	
	<!-- Extra statement used by XSLT processors to control the output style. -->
	<?xml-stylesheet type='text/xsl' href='rfc2629.xslt' ?>
	<!-- Processing Instructions- PIs (for a complete list and description,
	     see file http://xml.resource.org/authoring/README.html.
	     You may find that some sphisticated editors are not able to edit PIs when palced here.
	     An alternative position is just inside the rfc elelment as noted below. -->
	<!-- Some of the more generally applicable PIs that most I-Ds might want to use -->
	<!-- Try to enforce the ID-nits conventions and DTD validity -->
	<?rfc strict="yes" ?>
	<!-- Items used when reviewing the document -->
	<!-- Controls display of <cref> elements -->
	<?rfc comments="yes" ?>
	<!-- When no, put comments at end in comments section,
	     otherwise, put inline -->
	<?rfc inline="yes" ?>
	<!-- When yes, insert editing marks: editing marks consist of a 
	     string such as <29> printed in the blank line at the 
	     beginning of each paragraph of text. -->
	<?rfc editing="no" ?>
	<!-- Create Table of Contents (ToC) and set some options for it.  
	     Note the ToC may be omitted for very short documents,but idnits insists on a ToC 
	     if the document has more than 15 pages. -->
	<?rfc toc="yes"?>
	<?rfc tocompact="yes"?>
	<!-- If "yes" eliminates blank lines before main section entries. -->
	<?rfc tocdepth="3"?>
	<!-- Sets the number of levels of sections/subsections... in ToC.
	   Can be overridden by 'toc="include"/"exclude"' on the section
	   element-->
	<!-- Choose the options for the references. 
	     Some like symbolic tags in the references (and citations) and others prefer 
	     numbers. The RFC Editor always uses symbolic tags.
	     The tags used are the anchor attributes of the references. -->
	<?rfc symrefs="yes"?>
	<?rfc sortrefs="yes" ?>
	<!-- If "yes", causes the references to be sorted in order of tags.
				 This doesn't have any effect unless symrefs is "yes"
	          also. --> 
	<!-- These two save paper: Just setting compact to "yes" makes savings by not starting each 
	     main section on a new page but does not omit the blank lines between list items. 
	     If subcompact is also "yes" the blank lines between list items are also omitted. -->
	<?rfc compact="yes" ?>
	<?rfc subcompact="no" ?>
	<!-- end of list of popular I-D processing instructions -->
	
	<!-- Information about the document.
	     category values: std, bcp, info, exp, and historic
	     For Internet-Drafts, specify attribute "ipr".
	         original ipr values are: full3978, noModification3978, noDerivatives3978), 
	         2008 IETF Trust versions: trust200811, noModificationTrust200811, noDerivativeTrust200811
	         2009/Current: trust200902, noModificationTrust200902, noDerivativesTrust200902, pre5378Trust200902
	     Also for Internet-Drafts, you must specify a value for attributes "docName" which is 
	        typically the file name under which it is filed but need not be.
	     If relevant, "iprExtract" may be specified to denote the anchor attribute value of a
	        section that can be extracted for separate publication, it is only useful when the value
	        of "ipr" does not give the Trust full rights.
	     "updates" and "obsoletes" attributes can also be specified here, their arguments are
	        comma-separated lists of RFC numbers (just the numbers) -->
	<rfc
	  xmlns:xi="http://www.w3.org/2001/XInclude"
	  category="info"
	  docName="draft-livingood-access-tech-type-00"
	  ipr="trust200902"
	  obsoletes=""
	  updates=""
	  submissionType="independent"
	  xml:lang="en"
	  version="3">
	
	
	  <!-- ***** FRONT MATTER ***** -->
	
	  <front>
	
	    <title abbrev="ISP Access Network Technology Type Registry">ISP Access Network Technology Type Registry</title>
	    <seriesInfo name="Internet-Draft" value="draft-livingood-access-tech-type-00"/>
	
	    <!-- add 'role="editor"' below for the editors if appropriate -->
	    <author fullname="Jason Livingood" initials="J" surname="Livingood">
		   <organization>
	           Comcast
	       </organization>
	      <address>
	        <postal>
	          <city>Philadelphia</city> <region>PA</region>
	          <country>USA</country>
	        </postal>
	        <email>jason_livingood@comcast.com</email>
	      </address>
	    </author>
	
	    <date month="September" day="8" year="2024"/>
	
	    <!-- Meta-data Declarations -->
	    <!-- WG name at the upper left corner of the doc,
	         IETF fine for individual submissions.  You can also
	         omit this element in which case it defaults to "Network Working Group" -
	         a hangover from the ancient history of the IETF! -->
	    <workgroup>Independent Stream</workgroup>
	
		<!-- You can add <keyword/> elements here.  They will be incorporated into HTML output
	         files in a meta tag but they have no effect on text or nroff output. -->
		<!-- <keyword>Text</keyword> (as many of those elements as needed -->
	
		
	    <abstract>
	      <t>xxxx</t>
	    </abstract>
	
		<!-- Note here if needed
		   <note title=""><t> .... </t></note> -->
		
	  </front>
	
	  <middle>
	    <section title="Introduction">
			    
		<t>xxx</t>
		
		<t>For additional background on latency and why latency matters so much to the Internet, please read <xref target="BITAG"/></t>
		  
	    <!--  <t>The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
	      "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this
	      document are to be interpreted as described in
		  <xref target="RFC2119">RFC 2119</xref>.</t> -->
	
	    </section>
	    
	    <section title="XXX">
		    
		    
		    
		    <t>xxx</t>
					

		</section>
		
		
	 
	    <section title="Acknowledgements">
			<t>Thanks to xxx for their review and feedback on this document.</t>
		</section>
	
	    <section title="IANA Considerations">
		  <t>RFC Editor: Please remove this section before
			 publication.</t>
	      <t>This memo includes no requests to or actions for IANA.</t>
	    </section>
	
	    <section title="Security Considerations">
		  <t>RFC Editor: Please remove this section before
			 publication.</t>
	      <t>This memo includes no security considerations.</t>
	    </section>
	    
	    <section title="Privacy Considerations">
		  <t>RFC Editor: Please remove this section before
			 publication.</t>
	      <t>This memo includes no privacy considerations.</t>
	    </section>
	    
	    <section title="Revision History">
		  <t>RFC Editor: Please remove this section before
			 publication.</t>
	      <t>v00: First draft</t>
	    </section>
	    
	    <section title="Open Issues">
		  <t>RFC Editor: Please remove this section before
			 publication.</t>
	      <t>- Open issues are being tracked in a GitHub repository for this document 
		      at https://github.com/jlivingood/Broadband-Labels/issues</t>
	    </section>
	    
	    
	  </middle>
	
	  <!--  *****BACK MATTER ***** -->
	
	  <back>
	    <!-- References split to informative and normative -->
	
	   <references title="Informative References">
			<xi:include href="https://www.rfc-editor.org/refs/bibxml/reference.RFC.8325.xml"/>
			<xi:include href="https://www.rfc-editor.org/refs/bibxml/reference.RFC.9330.xml"/>
			<xi:include href="https://www.rfc-editor.org/refs/bibxml/reference.RFC.9331.xml"/>
			<xi:include href="https://www.rfc-editor.org/refs/bibxml/reference.RFC.9332.xml"/>
		   <xi:include href="https://bib.ietf.org/public/rfc/bibxml3/reference.I-D.ietf-tsvwg-l4sops.xml"/>
		   <xi:include href="https://bib.ietf.org/public/rfc/bibxml3/reference.I-D.ietf-tsvwg-nqb.xml"/>
		   <xi:include href="https://bib.ietf.org/public/rfc/bibxml3/reference.I-D.ietf-tsvwg-dscp-considerations.xml"/>
		   <xi:include href="https://bib.ietf.org/public/rfc/bibxml3/reference.I-D.briscoe-docsis-q-protection.xml"/>
		   
		   <reference anchor="BITAG" target="https://bitag.org/documents/BITAG_latency_explained.pdf">
			   <front>
	            <title>Latency Explained</title>
	            <author>
	              <organization>Broadband Internet Technical Advisory Group</organization>
	            </author>
	            <date year="2022" month="January" day="10"/>
			   </front>
		   </reference>
		   
		   <reference anchor="Lotus" target="https://www.eff.org/wp/packet-forgery-isps-report-comcast-affair">
			   <front>
	            <title>Packet Forgery By ISPs: A Report on the Comcast Affair</title>
	            <author fullname="Peter Eckersley" initials="P" surname="Eckerseley">
	              <organization>Electronic Frontier Foundation</organization>
	            </author>
                <author fullname="Fred von Lohmann" initials="F" surname="von Lohmann">
	              <organization>Electronic Frontier Foundation</organization>
	            </author>
                <author fullname="Seth Schoen" initials="S" surname="Schoen">
	              <organization>Electronic Frontier Foundation</organization>
	            </author>
	            <date year="2007" month="November" day="28"/>
			   </front>
		   </reference>
		   
		   <reference anchor="IETF-114-Slides" target="https://datatracker.ietf.org/meeting/114/materials/slides-114-tsvwg-update-on-l4s-work-in-ietf-114-hackathon-00.pdf">
			   <front>
	            <title>First L4S Interop Event @ IETF Hackathon</title>
	            <author fullname="Greg White" initials="G" surname="White">
	              <organization>CableLabs</organization>
	            </author>
	            <date year="2022" month="July" day="25"/>
			   </front>
			   
			</reference>
			
			<reference anchor="LLD" target="https://cablela.bs/low-latency-docsis-technology-overview-february-2019">
				<front>
					<title>Low Latency DOCSIS: Technology Overview</title>
					<author fullname="Greg White" initials="G" surname="White">
						<organization>CableLabs</organization>
						</author>
					<author fullname="Karthik Sundaresan" initials="K" surname="Sundaresan">
						<organization>CableLabs</organization>
						</author>
							<author fullname="Bob Briscoe" initials="B" surname="Briscoe">
					</author>
					<date year="2019" month="February"/>
				</front>
				
				</reference>

				<reference anchor="Ericsson" target="https://www.ericsson.com/49bc82/assets/local/reports-papers/white-papers/26052021-enabling-time-critical-applications-over-5g-with-rate-adaptation-whitepaper.pdf">
							<front>
							<title>Enabling time-critical applications over 5G with rate adaptation</title>
					<author fullname="Per Willars" initials="P" surname="Willars"><organization>Ericsson</organization></author>
					<author fullname="Emma Wittenmark" initials="E" surname="Wittenmark"><organization>Ericsson</organization></author>
					<author fullname="Henrik Ronkainen" initials="H" surname="Ronkainen"><organization>Business Area Networks</organization></author>
					<author fullname="Ingemar Johansson" initials="I" surname="Johansson"><organization>Ericsson</organization></author>
					<author fullname="Johan Strand" initials="J" surname="Strand"><organization>Business Area Networks</organization></author>
					<author fullname="Petr Ledl" initials="D" surname="Ledl"><organization>Deutsche Telekom</organization></author>
					<author fullname="Dominik Schnieders" initials="D" surname="Schnieders"><organization>Deutsche Telekom</organization></author>
	
	
							<date year="2021" month="May"/>
						</front>
							
						</reference>

			<reference anchor="CTI" target="https://www.itu.int/rec/T-REC-G.Sup71-202104-I">
							<front>
							<title>Optical line termination capabilities for supporting cooperative dynamic bandwidth assignment</title>
							<author><organization>International Telecommunications Union - Telecommunication Standardization Sector (ITU-T)</organization></author>
			
			        <date year="2021" month="April"/>
		           </front>
			           <seriesInfo name="Series G: Transmission Systems and Media, Digital Systems and Networks" value="Supplement 71" />
						</reference>

			<reference anchor="IEEE" target="https://ieeexplore.ieee.org/document/9363693">
							<front>
							<title>Part 11: Wireless LAN Medium Access Control (MAC) and Physical Layer (PHY) Specifications</title>
							<author><organization>IEEE Computer Society (IEEE)</organization></author>
			        <date year="2021" month="February" day="26"/>
		           </front>
				   		<seriesInfo name="DOI" value="10.1109/IEEESTD.2021.9363693"/>
			           <seriesInfo name="IEEE Standard for Information Technology--Telecommunications and Information Exchange between Systems - Local and Metropolitan Area Networks--Specific Requirements" value="802.11-2020" />
						</reference>

			<reference anchor="Microsoft" target="https://learn.microsoft.com/en-us/gaming/gdk/_content/gc/networking/overviews/qos-packet-tagging">
			   <front>
	            <title>Quality of service (QoS) packet tagging on Xbox consoles</title>
	            <author>
	              <organization>Microsoft</organization>
	            </author>
	            <date year="2022" month="August" day="19"/>
			   </front>
			   
			</reference>
			
		   
	   </references>
	
	  </back>
	</rfc>
