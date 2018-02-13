# link-service
The Link Service is used to create links to content and metadata on FDsys.

The service is currently available for the collections below. The collection code is listed in parenthesis after each collection name. The available queries and parameters are listed below each collection.

# govinfo link service

GPO has released its link service for govinfo. It has all of the same functionality as the FDsys link service, but with a few additional link types and an easier to use set of documentation.

For more information, see the interactive documentation available at https://www.govinfo.gov/link-docs/ . This link service has been built and documented using the [Open API Spec](https://github.com/OAI/OpenAPI-Specification) and [Swagger UI](https://github.com/swagger-api/swagger-ui)

The parameters below are also available for the govinfo link service. High-level changes are:
- `link-type` value of 'contentdetail' is now 'details'
- the addition of the 'related' and 'context' values for `link-type`. These additional link types will provide access to the equivalent tabs on a govinfo details page, where available. 

## Code of Federal Regulations (CFR)

### Query: 
title number, part number, section number, year OR most recent

#### Parameters:

* collection: Required - Value is cfr. 

* titlenum: Required - This is the title number. Sample value is 3. 

* partnum: Required - This is the part number. Sample value is 100. 

* sectionnum: Optional - This is the section number. Sample value is 1. If section number is not provided the entire part will be returned. 

* year: Optional - This is the four digit numerical year OR mostrecent. If year is not provided the most recent version of the CFR section or part is returned. Default is most recent. Sample value is 2011. 

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are xml, mods, premis, contentdetail. 

#### Examples:

* https://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&year=2011

* https://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&year=mostrecent

* https://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1

* https://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&link-type=premis

* https://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&link-type=mods

* https://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100 

## Compilation of Presidential Documents (CPD)

### Query: 

document type, document number

#### Parameters:

* collection: Required - Value is cpd. 

* doctype: Required - Values are executiveorder, proclamation, determination. 

* docnum: Required - This is the numerical document number. Sample value is 13514. 

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail. 

#### Examples:

* https://api.fdsys.gov/link?collection=cpd&doctype=proclamation&docnum=8685 

* https://api.fdsys.gov/link?collection=cpd&doctype=executiveorder&docnum=13514&link-type=html 

* https://api.fdsys.gov/link?collection=cpd&docnum=94-35&doctype=determination 

### Query: 

dcpd type OR dcpd number

#### Parameters:

* collection: Required - Value is cpd. 

* year: Required - This is the four digit numerical year. The first Daily Compilation of Presidential Documents (dcpd) document was published on 1/20/2009. Sample value is 2010. 

* dcpnumber: Optional - This is the five digit numerical identifier on a dcpd document. It does not include the four digit year. Document are numbered sequentially within each year. Leading zeros can be supplied but are not required. Sample value is 00123. Either dcpdnumber or dcpdtype is required. If a document contains both a dcpdnumber and a dcpdtype, we recommend providing dcpdtype instead of dcpdnumber. If both are provided, precedence is given to dcpdnumber. 

* dcpdtype: Optional - This is the type of dcpd document. Values are digest, nominations, checklist, actsapproved. Either dcpdnumber or dcpdtype is required. If a document contains both a dcpdnumber and a dcpdtype, we recommend providing dcpdtype instead of dcpdnumber. If both are provided, precedence is given to dcpdnumber. 

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail. 


#### Examples:

* https://api.fdsys.gov/link?collection=cpd&dcpdnumber=00123&year=2010&link-type=contentdetail 

* https://api.fdsys.gov/link?collection=cpd&dcpdtype=nominations&year=2011 

## Congressional Bills (BILLS)

### Query: 

bill number, bill type, congress, bill version OR most recent

#### Parameters:

* collection: Required - Value is bills.

* billtype: Required - Values are hr, s, hjres, sjres, hconres, sconres, hres, sres.

* billversion: Optional - If bill version is not provided, the most recent version of a bill is returned. Values are
as, cps, fph, lth, ppv, rds, rhv, rhuc, ash, eah, fps, lts, pap, rev, rih, sc, eas, hdh, nat, pwah, reah, ris, ath, eh, hds, oph, rah, res, rsv, ats, eph, ihv, ops, ras, renr, rth, cdh, enr, iph, pav, rch, rfh, rts, cds, esv, ips, pch, rcs, rfs, s_p, cph, fah, isv, pcs, rdh, rft, sas, mostrecent.

* billnum: Required - This is the numerical bill number. Sample value is 1027.

* congress: Required - This is the numerical Congress number. Sample value is 112.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are xml, html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=bills&billtype=hr&billversion=ih&billnum=1&congress=112

* https://api.fdsys.gov/link?collection=bills&billtype=hconres&billnum=17&congress=112&link-type=xml 

## Congressional Calendars (CCAL)

### Query: 

chamber, section, publish date OR most recent

#### Parameters:

* collection: Required - Value is ccal.

* chamber: Required - This is the chamber of Congress. Values are house, senate.

* section: Required - This is the name of the calendar section. Recommend encoding special characters and spaces (%20). Common sample values include Unanimous Consent Agreements, Cover and Special Orders, Subjects on the Table, Union Calendar, Bills in Conference, Special Legislative Days.

* publishdate: Optional - If date is not provided, the most recent version of the calendar is returned. Values are date formated as yyyy-mm-dd or mostrecent. Default is most recent.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=ccal&chamber=senate&section=Subjects%20on%20the%20Table

* http://api.fdsys.gov/link?collection=ccal&chamber=senate&section=Subjects%20on%20the%20Table&publishdate=2011-12-01 

## Congressional Committee Prints (CPRT)

### Query: 

congress, chamber, senate print number

#### Parameters:

* collection: Required - Value is cprt.

* congress: Required - This is the numerical Congress number. Sample value is 112.

* chamber: Required - This is the chamber of Congress. Value is senate.

* printnum: Required - This is the numerical Senate print number. Senate prints are numbered consecutively across committees within a Congress. Sample value is 4.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Example:

* https://api.fdsys.gov/link?collection=cprt&congress=112&chamber=senate&printnum=4

### Query: 

congress, chamber, house print number, committee

#### Parameters:

* collection: Required - Value is cprt.

* congress: Required - This is the numerical Congress number. Sample value is 109.

* chamber: Required - This is the chamber of Congress. Value is house.

* printnum: Required - This is the numerical House committee print number. House prints are not numbered consecutively across committees within a Congress. For example, 109-2 could exist for both the Ways and Means Committee and the Rules and Administration Committee within the 109th Congress. Sample value is 2.

* committee: Required - This is the name of the House committee. Recommend encoding special characters and spaces (%20). Sample value is Ways and Means.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Example:

* https://api.fdsys.gov/link?collection=cprt&congress=109&chamber=house&printnum=2&committee=Ways+and+Means

### Query: 

congress, jacket number

#### Parameters:

* collection: Required - Value is cprt.

* congress: Required - This is the numerical Congress number. Sample value is 112.

* jacketid: This is the GPO jacket number. The jacket number is typically listed on the first page in the lower left corner. Jacket number is unique within a Congress. Sample value is 74-558.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=cprt&congress=112&jacketid=74-558

## Congressional Documents (CDOC)

### Query: 

congress, document type, document number

#### Parameters:

* collection: Required - Value is cdoc.

* doctype: Required - This is the congressional document type. Congressional documents can either be house documents, senate documents, or treaty documents. Values are hdoc, sdoc, tdoc.

* docnum: Required - This is the numerical document number. Congressional documents are numbered consecutively within a Congress for each document type. Sample value is 15. Note: congressional documents that have been processed through the GPO collection are currently not available through the Link Service.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=cdoc&congress=112&docnum=5&doctype=hdoc

### Query: 

congress, jacket number

#### Parameters:

* collection: Required - Value is cdoc.

* congress: Required - This is the numberical Congress number. Sample value is 112.

* jacketid: This is the GPO jacket number. The jacket number is typically listed on the first page in the lower left corner. Jacket number is unique within a Congress. Sample value is 66-208.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=cdoc&congress=112&jacketid=66-208 

## Congressional Hearings (CHRG)

### Query: 

congress, chamber, senate hearing number

#### Parameters:

* collection: Required - Value is chrg.

* congress: Required - This is the numerical Congress number. Sample value is 122.

* chamber: Required - This is the chamber of Congress. Value is senate.

* hearingnumber: Required - This is the numerical Senate hearing number. Senate hearings are numbered consecutively across committees within a Congress. Sample value is 122.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Example:

* https://api.fdsys.gov/link?collection=chrg&chamber=senate&congress=112&hearingnumber=122

### Query: 

congress, chamber, committee, house serial number

#### Parameters:

* collection: Required - Value is chrg.

* chamber: Required - This is the chamber of Congress. Value is house.

* committee: Required - This is the name of the House committee. Recommend encoding special characters and spaces (%20). Sample value is energy.

* serialnumber: Required - This is the numerical house committee serial number. House hearings are not numbered consecutively across committees within a Congress. For example, 109-138 could exist for both the Energy Committee and the Rules and Administration Committee within the 109th Congress. Sample value is 138.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Example:

* https://api.fdsys.gov/link?collection=chrg&chamber=house&congress=109&serialnumber=138&committee=energy

### Query: 

congress, jacket number

#### Parameters:

* collection: Required - Value is chrg.

* congress: Required - This is the numerical Congress number. Sample value is 105.

* jacketid: This is the GPO jacket number. The jacket number is typically listed on the first page in the lower left corner. Jacket number is unique within a Congress. Sample value is 48-707.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Example:

* https://api.fdsys.gov/link?collection=chrg&congress=105&jacketid=48-707&link-type=html 

## Congressional Record - Daily (CREC)

### Query: 

volume, page prefix, page number

#### Parameters:

* collection: Required - Value is crec.

* volume: Required - This is the numerical volume number. Sample value is 158.

* pageprefix: Required - This is the page prefix that corresponds to the Congressional Record section. Sections are Daily Digest, House, Senate, and Extensions of Remarks. Values are d, h, s, e.

* page: Required - This is the numerical page number. Congressional record pages are numbered consecutively in a section within a volume. Note: when multiple granules are contained on a page, content and metadata for the last granule on the page will be returned. Recommend selecting PDF link-type to return content for all granules on a page. Sample value is 234.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=crec&pageprefix=s&page=234&volume=158

### Query: 

section, publish date OR most recent

#### Parameters:

* collection: Required - Value is crec.

* section: Required - This is the Congressional Record section. Values are dailydigest, senate, house, extensions.

* publishdate: Optional - If date is not provided, the most recent version of the Congressional Record section is returned. Values are date formated as yyyy-mm-dd or mostrecent. Default is most recent.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are mods, premis, contentdetail. Note: mods, premis, and contentdetail are returned at the package level because they are not available for section level granules.

#### Examples:

* https://api.fdsys.gov/link?collection=crec&section=dailydigest

* https://api.fdsys.gov/link?collection=crec&section=dailydigest&publishdate=2011-11-22

### Query: 

document type, publish date OR most recent

#### Parameters:

* collection: Required - Value is crec.

* type: Optional - This is the type of Congressional Record document within each section. Please see tables below for values.

* publishdate: Optional - If date is not provided, the most recent version of the Congressional Record document is returned. Values are date formated as yyyy-mm-dd or mostrecent. Default is most recent.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=crec&type=hclerk

#### Type Values 

The information below lists the allowable values for the type field. Values are not case sensitive. Note: some values may produce multiple results. For example, both the House section and Senate section could contain a tributeto granule on the same day. In this case, the desired document may not be returned. 

##### Daily Digest Type Values

Type Value | User Readable Value

DDALLOTHER | All Other

DDSCHAMBER | Senate Chamber Action

DDSCMEETINGS | Senate Committee Meetings

DDHCHAMBER | House Chamber Action

DDHCMEETINGS | House Committee Meetings

DDNEWPUBLAWS | New Public Laws

DDAHEAD | Congressional Program Ahead

DDCOMMITTEEMEETINGS | Committee Meetings Upcoming

DDRESUMEONGOING | Resume of Congressional Activity - Ongoing

DDRESUMEFINAL | Resume of Congressional Activity - Final

DDENDMATTER | End Matter

##### House, Senate, and Extensions of Remarks Type Values

Type Value | User Readable Value

ALLOTHER | All Other Legislative Business

PRAYER | Prayer

PLEDGE | Pledge of Allegiance

ADJOURNMENT | Adjournment

EXECUTIVECOMM | Executive and other Communications

JOINTMEETINGS | Joint Meetings of the House and Senate

ENROLLEDSIGNED | Enrolled Legislation Signed

ENROLLEDPRESENTED | Enrolled Legislation Presented

MSGPRESIDENT | Messages From the President

TECHNICALCORRECTIONS | Making Technical Corrections

PERSONALEXPLAIN | Personal Explanation

RECOGNIZING | Recognitions

HONORING | Honoring

COMMEMORATING | Commemorations

CELEBRATING | Celebrations

COMMENDING | Commending

PASSINGOF | On the passing of

TRIBUTETO | Tribute

CONGRATULATIONS | Congratulations

RETIREMENT | Retirement Of

DESIGNATING | Designating

INMEMORYOF | In Memory Of

##### House Type Values

Type Value | User Readable Value

HDESIGNATION | Designation of The Speaker Pro Tempore

HJOURNAL | The Journal

HMESSAGE | Message From the Senate

HCLERK | Communication From The Clerk of the House

HANNOUNCEMENT | Announcement by the Speaker

HMORNINGDEBATE | Morning Hour Debates

HREPORTON | Report On

HCONFREPORTON | Conference Report On

HSENATEBILLREFERRED | Senate Bill Referred

HLEGPROGRAM | Legislative Program

HTIMELIMIT | Time Limitation Of Referred Bill

HEXPENDITURE | Expenditure Reports Concerning Official Foreign Travel

HCORRECTIONS | Honoring

COMMEMORATING | Commemorations

CELEBRATING | Celebrations

COMMENDING | Commending

PASSINGOF | On the passing of

TRIBUTETO | Tribute

CONGRATULATIONS | Congratulations

RETIREMENT | Retirement Of

DESIGNATING | Designating

INMEMORYOF | In Memory Of

HPETITIONS | Petitions

HAMENDMENTS | Amendments

HEARMARKS | Congressional Earmarks, Limited Tax Benefits, Or Limited Tariff Benefits

##### Senate Type Values

Type Value | User Readable Value

SENATEALLOTHER | All Other Legislative Business

SAPPOINTMENT | Appointment of The Acting President Pro Tempore

SORDER | Order of Procedure

SSCHEDULE | Schedule

SSSCHEDULE | Senate Schedule

SMEASUREDCAL | Measures Placed on the Calendar

SMBUSINESS | Morning Business

SCONBUSINESS | Conclusion of Morning Business

SRECESS | Recess

SADDITIONAL | Additional Statements

SMSGHOUSE | Message From the House

SCOMMREPORT | Reports of Committees

SEXECREPORT | Executive Reports of Committees

SPETANDMEM | Petitions and Memorials

SREFERRED | Measures Referred

SREADFIRST | Measures Read the First Time

SDISCHARGED | Measures Discharged

SDICHARGEREF | Discharge and Referral

SMSGEXEC | Executive Messages Referred

SINTROBILLS | Introduction of Bills and Joint Resolutions

SSUBMISSION | Submission of Concurrent and Senate Resolutions

SCOSPONSORS | Additional Cosponsors

SSTATEMENTS | Statements on Introduced Bills and Joint Resolutions

SSUBMITTED | Submitted Resolutions

SRESOLUTION | Senate Resolution

SAMENDMENTSSUB | Amendments Submitted and Proposed

SAMENDMENTTEXT | Text of Amendments

SNOTICE | Notice of Hearings

SAUTHORITY | Authority for Committees to Meet

SPRIVILEGES | Privileges of the Floor

SPROGRAM | Program

SCALENDAR | The Calendar

SCONSENTAGREE | Unanimous Consent Agreement

SCONSENTREQUEST | Unanimous Consent Request

SORDERFOR | Order For

SEXECSESSION | Executive Session

SEXECCAL | Executive Calendar

SLEGISLATIVE | Legislative Session

SNOMINATIONS | Nominations

SWITHDRAWAL | Withdrawals

SCONFIRMATIONS | Confirmation

SCLOTURE | Cloture Motion

##### Extensions of Remarks Type Values

Type Value | User Readable Value

ESENATECOMMITTEE | Senate Committee Meetings

EINTRODUCTIONOF | Introducing Legislation

## Congressional Reports (CRPT)

### Query: 

congress, report type, report number

#### Parameters:

* collection: Required - Value is crpt.

* congress: Required - This is the numerical Congress number. Sample value is 112.

* reportnum: Required - This is the numerical report number. Congressional reports are numbered consecutively within a Congress for each report type. Sample value is 154.

* doctype: Required - This is the congressional report type. Congressional reports can either be house reports, senate reports, or senate executive reports. Values are hrpt, srpt, erpt.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=crpt&congress=112&reportnum=154&doctype=srpt

### Query: 

associated bill, congress

#### Parameters:

* collection: Required - Value is crpt.

* congress: Required - This is the numerical Congress number. Sample value is 112.

* associatedbillnum: Required - Congressional reports often accompany a specific bill. Note: some associated bill numbers may produce multiple results. This will occur when two different reports are issued to accompany a single bill within a single Congress. In this case, the desired report may not be returned. Sample value is h.r.2297.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=crpt&associatedbillnum=h.r.2297&congress=112

## Federal Register (FR)

### Query: 

volume, page number

#### Parameters:

* collection: Required - Value is fr.

* volume: Required - This is the numerical volume number. Sample value is 76.

* page: Required - This is the numerical page number. Federal Register pages are numbered consecutively within a volume. Note: when multiple granules are contained on a page, content and metadata for the last granule on the page will be returned. Recommend selecting PDF link-type to return content for all granules on a page. Sample value is 575.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=fr&volume=76&page=575

### Query: 

Federal Register document number

#### Parameters:

* collection: Required - Value is fr.

* frdocnum: Required - The is the FR doc number that is listed at the end of each Federal Register document. Sample value is 2010-32535.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=fr&frdocnum=2010-32535

## Public and Private Laws (PLAW)

### Query: 

congress, law type, law number

#### Parameters:

* collection: Required - Value is plaw.

* congress: Required - This is the numerical Congress number. Sample value is 111.

* lawtype: Required - This is the law type. Laws can either be public laws or private laws. Values are public, private.

* lawnum: Required - This is the numerical law number. Laws are numbered consecutively within each law type within a Congress. Sample value is 78.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Example:

* https://api.fdsys.gov/link?collection=plaw&congress=111&lawtype=public&lawnum=78


### Query: 

associated bill number, congress

#### Parameters:

* collection: Required - Value is plaw.

* congress: Required - This is the numerical Congress number. Sample value is 111.

* associatedbillnum: Required - Public and private laws are associated with a primary bill number. The primary bill number is listed at the beginning of the law. Sample value is S. 3397.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Example:

* https://api.fdsys.gov/link?collection=plaw&associatedbillnum=s.3397&congress=111

### Query: 

Statutes at Large citation

#### Parameters:

* collection: Required - Value is plaw.

* statutecitation: Required - A Statutes at Large citation is listed at the top of each page of a law. Use a + (plus sign) in place of spaces in the citation. Sample value is 124+stat+2859.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Example:

* https://api.fdsys.gov/link?collection=plaw&statutecitation=124+stat+2859 

## Statutes at Large (STATUTE)

### Query: 

congress, law type, law number

#### Parameters:

* collection: Required - Value is statute.

* congress: Required - This is the numerical Congress number. Sample value is 108.

* lawtype: Required - This is the law type. Laws can either be public laws or private laws. Values are public, private.

* lawnum: Required - This is the numerical law number. Laws are numbered consecutively within each law type within a Congress. Sample value is 841.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Example:

* https://api.fdsys.gov/link?collection=statute&congress=108&lawtype=public&lawnum=481

### Query: 

volume, page number

#### Parameters:

* collection: Required - Value is statute.

* volume: Required - This is the numerical volume number. Sample value is 118.

* page: Required - This is the numerical page number. Statutes at Large pages are numbered consecutively within a volume. Note: when multiple granules are contained on a page, content and metadata for the last granule on the page will be returned. Recommend selecting PDF link-type to return content for all granules on a page. Sample value is 3910.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Example:

* https://api.fdsys.gov/link?collection=statute&volume=118&page=3910

## United States Code (USCODE)

### Query: 

title number, type, section, year OR most recent

#### Parameters:

* collection: Required - Value is uscode.

* title: Required - This is the title number. Sample value is 5.

* section: Required - This is the section number. Sample value is 104.

* type: Optional - This is the U.S. Code section type. Values are usc, uscappendix. Default value is usc.
year Optional - This is the four digit numerical year OR mostrecent. If year is not provided the most recent version of the U.S. Code section is returned. Default is most recent. Sample value is 2010.

* link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail.

#### Examples:

* https://api.fdsys.gov/link?collection=uscode&title=50&year=2011&section=797&type=usc

* https://api.fdsys.gov/link?collection=uscode&title=50&year=2011&section=797

* https://api.fdsys.gov/link?collection=uscode&title=50&year=mostrecent&section=797

* https://api.fdsys.gov/link?collection=uscode&title=50&section=797&link-type=html

* https://api.fdsys.gov/link?collection=uscode&title=50&year=2011&section=2403-1&type=uscappendix

* https://api.fdsys.gov/link?collection=uscode&title=50&year=2011&section=2403-1a&type=uscappendix

* https://api.fdsys.gov/link?collection=uscode&title=50&year=2011&section=2410c&type=uscappendix

## Common Errors:

### Multiple Results Found

This error occurs when more than one document matches parameters for a given request. Additional parameters must be specified in order to return a single document.

### No Results Found

This error occurs if a match document was not found for the given parameters. Please check the API documentation to make sure values provided are correct.

### Validation Failed

This error occurs when request parameters fail validation. Possible causes include the following:

* No queries found for COLLECTION CODE. This error occurs if the value for collection is incorrect or has not been enabled yet. Please check the documentation for available collections and collection codes.

* Request parameter XXXX is not found but is required. This error occurs if a required parameter is missing in the URL. Please check the documentation for required parameters for each collection.

* The value provided for XXXX is invalid. One of the following [XXXX, YYYY] is expected. This error occurs if a value provided for a parameter is not among the listed choices. Please check the documentation for parameter values.

### Content File Not Found

This error can occur for an invalid or unavailable link-type value. Allowable values are pdf, html, mods, premis and contentdetail. This error can also occur if a requested link-type is not available for a specific document.

### System Error

Please contact contactcenter@gpo.gov to report any system errors encountered while using the Link Service. 

Cheers!



