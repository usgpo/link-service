# link-service

The Link Service is used to create links to content and metadata on GovInfo. This allows for both predictable link creation as well as the ability to point to the latest version of a given resource - like the latest version of a Congressional Bill or latest edition of a CFR section.

For more information, see the interactive documentation available at https://www.govinfo.gov/link-docs/ . This link service has been built and documented using the [Open API Spec](https://github.com/OAI/OpenAPI-Specification) and [Swagger UI](https://github.com/swagger-api/swagger-ui)

## Code of Federal Regulations (CFR)

### CFR Title and Part Query

Returns a specific CFR Title and part, including the ability to specify a particular section

#### Parameters

- **collection:** Required - Value is cfr.

- **titlenum:** Required - title number. Sample value is 3.

- **partnum:** Required - part number. Sample value is 100.

- **sectionnum:** Optional - section number. Sample value is 1. If section number is not provided the entire part will be returned.

- **year:** Optional - four digit year OR mostrecent. If year is not provided the most recent version of the CFR section or part is returned. Default is most recent. Sample value is 2011.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are xml, mods, premis, details, context, and related.

#### Examples

- https://www.govinfo.gov/link/cfr/3/100?sectionnum=1&year=2018

- https://www.govinfo.gov/link/cfr/3/100?sectionnum=1&year=mostrecent

- https://www.govinfo.gov/link/cfr/3/100?sectionnum=1

- https://www.govinfo.gov/link/cfr/3/100?sectionnum=1&link-type=premis

- https://www.govinfo.gov/link/cfr/3/100?sectionnum=1&link-type=mods

- https://www.govinfo.gov/link/cfr/3/100

## Compilation of Presidential Documents (CPD)

### DCPD Type or Number Query

Return a specific DCPD document by Supplementary Materials Type or DCPD number

#### Parameters

- **collection:** Required - Value is cpd.

- **year:** Required - four digit year. The first Daily Compilation of Presidential Documents (dcpd) document was published on 1/20/2009. Sample value is 2010.

- **dcpnumber:** Optional - five digit identifier on a dcpd document. It does not include the four digit year. Document are numbered sequentially within each year. Leading zeros can be supplied but are not required. Sample value is 00123. Either dcpdnumber or dcpdtype is required. If a document contains both a dcpdnumber and a dcpdtype, we recommend providing dcpdtype instead of dcpdnumber. If both are provided, precedence is given to dcpdnumber.

- **dcpdtype:** Optional - type of dcpd document. Values are digest, nominations, checklist, actsapproved. Either dcpdnumber or dcpdtype is required. If a document contains both a dcpdnumber and a dcpdtype, we recommend providing dcpdtype instead of dcpdnumber. If both are provided, precedence is given to dcpdnumber.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details, related.

#### Examples

- https://www.govinfo.gov/link/cpd/2018?dcpdnumber=00849&link-type=details

- https://www.govinfo.gov/link/cpd/2022?dcpdtype=nominations
  
### DCPD doctype or number Query

Return DCPD documents by a specific presidential document type and number.

#### Parameters

- **collection:** Required - Value is cpd.

- **doctype:** Required - Values are executiveorder, proclamation, determination.

- **docnum:** Required - document number. Sample value is 13514.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Examples

- https://www.govinfo.gov/link/cpd/proclamation/9297

- https://www.govinfo.gov/link/cpd/executiveorder/14104?link-type=html

- https://www.govinfo.gov/link/cpd/determination/94-35?link-type=details

## Congressional Bills (BILLS)

### BILLS Query

bill number, bill type, congress, bill version OR most recent

#### Parameters

- **collection:** Required - Value is bills.

- **billtype:** Required - Values are hr, s, hjres, sjres, hconres, sconres, hres, sres.

- **billversion:** Optional - If bill version is not provided, the most recent version of a bill is returned. Values are
as, cps, fph, lth, ppv, rds, rhv, rhuc, ash, eah, fps, lts, pap, rev, rih, sc, eas, hdh, nat, pwah, reah, ris, ath, eh, hds, oph, rah, res, rsv, ats, eph, ihv, ops, ras, renr, rth, cdh, enr, iph, pav, rch, rfh, rts, cds, esv, ips, pch, rcs, rfs, s_p, cph, fah, isv, pcs, rdh, rft, sas, mostrecent.

- **billnum:** Required - bill number. Sample value is 1027.

- **congress:** Required - Congress number. Sample value is 112.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are xml, html, mods, premis, details.

#### Examples

- https://www.govinfo.gov/link/bills/hr&billversion=ih&billnum=1&congress=112

- https://www.govinfo.gov/link/bills/118/s/2950?link-type=xml

## Congressional Calendars (CCAL)

### CCAL section Query

chamber, section, publish date OR most recent

#### Parameters

- **collection:** Required - Value is ccal.

- **chamber:** Required - chamber of Congress. Values are house, senate.

- **section:** Required - name of the calendar section. Recommend encoding special characters and spaces (%20). Common sample values include Unanimous Consent Agreements, Cover and Special Orders, Subjects on the Table, Union Calendar, Bills in Conference, Special Legislative Days.

- **publishdate:** Optional - If date is not provided, the most recent version of the calendar is returned. Values are date formated as yyyy-mm-dd or mostrecent. Default is most recent.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details, context.

#### Examples

- https://www.govinfo.gov/link/ccal/senate/Subjects%20on%20the%20Table

- https://www.govinfo.gov/link/ccal/senate/Subjects%20on%20the%20Table?publishdate=2011-12-01

### CCAL Latest Full Calendar Query

Returns the latest full House or Senate Calendar

#### Parameters

- **collection:** Required - Value is ccal.

- **chamber:** Required - chamber of Congress. Values are house, senate.

- **publishdate:** Optional - If date is not provided, the most recent version of the calendar is returned. Values are date formated as yyyy-mm-dd or mostrecent. Default is most recent.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details, context, zip.

#### Examples

- https://www.govinfo.gov/link/ccal/latest/senate/

- https://www.govinfo.gov/link/ccal/latest/house?publishdate=2023-10-20

## Congressional Committee Prints (CPRT)

### CPRT by Jacket Number Query

Returns a specific committee print by Congress and GPO jacket number

#### Parameters

- **collection:** Required - Value is cprt.

- **congress:** Required - Congress number. Sample value is 112.

- **jacketid:** - GPO jacket number. The jacket number is typically listed on the first page in the lower left corner. Jacket number is unique within a Congress. Sample value is 74-558.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Examples

- https://www.govinfo.gov/link/cprt/112/74-558

### CPRT by Senate Print Number Query

Returns a specific Senate committee print by Congress and unique Senate Print number

#### Parameters

- **collection:** Required - Value is cprt.

- **congress:** Required - Congress number. Sample value is 112.

- **chamber:** Required - chamber of Congress. Value is senate.

- **printnum:** Required - Senate print number. Senate prints are numbered consecutively across committees within a Congress. Sample value is 4.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Example

- https://www.govinfo.gov/link/cprt/112/senate/4

### CPRT by House Committee and Serial Number Query

Returns a specific committee print by Congress, House Committee, and serial number

#### Parameters

- **collection:** Required - Value is cprt.

- **congress:** Required - Congress number. Sample value is 109.

- **chamber:** Required - chamber of Congress. Value is house.

- **printnum:** Required - House committee print number. House prints are not numbered consecutively across committees within a Congress. For example, 109-2 could exist for both the Ways and Means Committee and the Rules and Administration Committee within the 109th Congress. Sample value is 2.

- **committee:** Required - name of the House committee. Recommend encoding special characters and spaces (%20). Sample value is Ways and Means.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Example

- https://www.govinfo.gov/link/cprt/118/house/11/Ways%20and%20Means

## Congressional Documents (CDOC)

### CDOC by Jacket Number Query

Return a specific Congressional Document by Congress and GPO Jacket number.

#### Parameters

- **collection:** Required - Value is cdoc.

- **congress:** Required - Congress number. Sample value is 112.

- **jacketid:** - GPO jacket number. The jacket number is typically listed on the first page in the lower left corner. Jacket number is unique within a Congress. Sample value is 66-208.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Examples

- https://www.govinfo.gov/link/cdoc/112/66-208

### CDOC by Document Type and Number Query

congress, document type, document number

#### Parameters

- **collection:** Required - Value is cdoc.

- **doctype:** Required - congressional document type. Congressional documents can either be house documents, senate documents, or treaty documents. Values are hdoc, sdoc, tdoc.

- **docnum:** Required - document number. Congressional documents are numbered consecutively within a Congress for each document type. Sample value is 15. Note:** congressional documents that have been processed through the GPO collection are currently not available through the Link Service.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Examples

- https://www.govinfo.gov/link/cdoc/112/hdoc/5

## Congressional Hearings (CHRG)

### CHRG by Jacket Number Query

Return a specific Congressional Hearing by Congress and GPO jacket number.

#### Parameters

- **collection:** Required - Value is chrg.

- **congress:** Required - Congress number. Sample value is 105.

- **jacketid:** - GPO jacket number. The jacket number is typically listed on the first page in the lower left corner. Jacket number is unique within a Congress. Sample value is 48-707.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Example

- https://www.govinfo.gov/link/chrg/105/48-707?link-type=html
- https://www.govinfo.gov/link/chrg/118/53-022


### CHRG - Senate Hearing Number Query

congress, chamber, senate hearing number

#### Parameters

- **collection:** Required - Value is chrg.

- **congress:** Required - Congress number. Sample value is 122.

- **chamber:** Required - chamber of Congress. Value is senate.

- **hearingnumber:** Required - Senate hearing number. Senate hearings are numbered consecutively across committees within a Congress. Sample value is 122.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Example

- https://www.govinfo.gov/link/chrg/112/senate/122

### CHRG - House Serial Number Query

Return a specific House Hearing by Congress, committee and serial number

#### Parameters

- **collection:** Required - Value is chrg.

- **chamber:** Required - chamber of Congress. Value is house.

- **committee:** Required - name of the House committee. Recommend encoding special characters and spaces (%20). Sample value is energy.

- **serialnumber:** Required - house committee serial number. House hearings are not numbered consecutively across committees within a Congress. For example, 109-138 could exist for both the Energy Committee and the Rules and Administration Committee within the 109th Congress. Sample value is 138.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Example

- https://www.govinfo.gov/link/chrg/109/house/energy/138
- https://www.govinfo.gov/link/chrg/118/house/judiciary/31

## Congressional Record - Daily (CREC)

### CREC Page Number Query

Return a specific Congressional Record document by volume, page prefix, and page number.

#### Parameters

- **collection:** Required - Value is crec.

- **volume:** Required - volume number. Sample value is 158.

- **pageprefix:** Required - page prefix that corresponds to the Congressional Record section. Sections are Daily Digest, House, Senate, and Extensions of Remarks. Values are d, h, s, e.

- **page:** Required - page number. Congressional record pages are numbered consecutively in a section within a volume. **Note:** when multiple granules are contained on a page, content and metadata for the last granule on the page will be returned. Recommend selecting PDF link-type to return content for all granules on a page. Sample value is 234.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Examples

- https://www.govinfo.gov/link/crec/158/s/234
- https://www.govinfo.gov/link/crec/169/h/2716?link-type=html

### CREC document type Query

Return the latest Congressional Record Document by type. More information below. Note that in instances where there are multiple documents of a type for a given date, the desired document may not be returned. In this case, it would be preferable to use the page reference query above.

#### Parameters

- **collection:** Required - Value is crec.

- **type:** Optional - type of Congressional Record document within each section. Please see tables below for values.

- **publishdate:** Optional - If date is not provided, the most recent version of the Congressional Record document is returned. Values are date formated as yyyy-mm-dd or mostrecent. Default is most recent.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Examples

- https://www.govinfo.gov/link/crec/type/hclerk
- https://www.govinfo.gov/link/crec/type/hclerk

#### Type Values

The information below lists the allowable values for the type field. Values are not case sensitive. Note: some values may produce multiple results. For example, both the House section and Senate section could contain a tributeto granule on the same day. In this case, the desired document may not be returned.

##### Daily Digest Type Values

|Type Value | User Readable Value|
|-----------|----------|
|[DDALLOTHER](https://www.govinfo.gov/link/crec/type/DDALLOTHER)| All Other|
|[DDSCHAMBER](https://www.govinfo.gov/link/crec/type/DDSCHAMBER)| Senate Chamber Action|
|[DDSCMEETINGS](https://www.govinfo.gov/link/crec/type/DDSCMEETINGS)| Senate Committee Meetings|
|[DDHCHAMBER](https://www.govinfo.gov/link/crec/type/DDHCHAMBER)| House Chamber Action|
|[DDHCMEETINGS](https://www.govinfo.gov/link/crec/type/DDHCMEETINGS)| House Committee Meetings|
|[DDNEWPUBLAWS](https://www.govinfo.gov/link/crec/type/DDNEWPUBLAWS)| New Public Laws|
|[DDAHEAD](https://www.govinfo.gov/link/crec/type/DDAHEAD)| Congressional Program Ahead|
|[DDCOMMITTEEMEETINGS](https://www.govinfo.gov/link/crec/type/DDCOMMITTEEMEETINGS)| Committee Meetings Upcoming|
|[DDRESUMEONGOING](https://www.govinfo.gov/link/crec/type/DDRESUMEONGOING)| Resume of Congressional Activity - Ongoing|
|[DDRESUMEFINAL](https://www.govinfo.gov/link/crec/type/DDRESUMEFINAL)| Resume of Congressional Activity - Final|
|[DDENDMATTER](https://www.govinfo.gov/link/crec/type/DDENDMATTER)| End Matter|

##### House, Senate, and Extensions of Remarks Type Values

|Type Value | User Readable Value|
|-----------|--------------------|
|[ALLOTHER](https://www.govinfo.gov/link/crec/type/ALLOTHER)| All Other Legislative Business|
|[PRAYER](https://www.govinfo.gov/link/crec/type/PRAYER)| Prayer|
|[PLEDGE](https://www.govinfo.gov/link/crec/type/PLEDGE)| Pledge of Allegiance|
|[ADJOURNMENT](https://www.govinfo.gov/link/crec/type/ADJOURNMENT)| Adjournment|
|[EXECUTIVECOMM](https://www.govinfo.gov/link/crec/type/EXECUTIVECOMM)| Executive and other Communications|
|[JOINTMEETINGS](https://www.govinfo.gov/link/crec/type/JOINTMEETINGS)| Joint Meetings of the House and Senate|
|[ENROLLEDSIGNED](https://www.govinfo.gov/link/crec/type/ENROLLEDSIGNED)| Enrolled Legislation Signed|
|[ENROLLEDPRESENTED](https://www.govinfo.gov/link/crec/type/ENROLLEDPRESENTED)| Enrolled Legislation Presented|
|[MSGPRESIDENT](https://www.govinfo.gov/link/crec/type/MSGPRESIDENT)| Messages From the President|
|[TECHNICALCORRECTIONS](https://www.govinfo.gov/link/crec/type/TECHNICALCORRECTIONS)| Making Technical Corrections|
|[PERSONALEXPLAIN](https://www.govinfo.gov/link/crec/type/PERSONALEXPLAIN)| Personal Explanation|
|[RECOGNIZING](https://www.govinfo.gov/link/crec/type/RECOGNIZING)| Recognitions|
|[HONORING](https://www.govinfo.gov/link/crec/type/HONORING)| Honoring|
|[COMMEMORATING](https://www.govinfo.gov/link/crec/type/COMMEMORATING)| Commemorations|
|[CELEBRATING](https://www.govinfo.gov/link/crec/type/CELEBRATING)| Celebrations|
|[COMMENDING](https://www.govinfo.gov/link/crec/type/COMMENDING)| Commending|
|[PASSINGOF](https://www.govinfo.gov/link/crec/type/PASSINGOF)| On the passing of|
|[TRIBUTETO](https://www.govinfo.gov/link/crec/type/TRIBUTETO)| Tribute|
|[CONGRATULATIONS](https://www.govinfo.gov/link/crec/type/CONGRATULATIONS)| Congratulations|
|[RETIREMENT](https://www.govinfo.gov/link/crec/type/RETIREMENT)| Retirement Of|
|[DESIGNATING](https://www.govinfo.gov/link/crec/type/DESIGNATING)| Designating|
|[INMEMORYOF](https://www.govinfo.gov/link/crec/type/INMEMORYOF)| In Memory Of|


##### House Type Values

Type Value | User Readable Value
|-----------|---------------------|
|[HDESIGNATION](https://www.govinfo.gov/link/crec/type/HDESIGNATION)| Designation of The Speaker Pro Tempore|
|[HJOURNAL](https://www.govinfo.gov/link/crec/type/HJOURNAL)| The Journal|
|[HMESSAGE](https://www.govinfo.gov/link/crec/type/HMESSAGE)| Message From the Senate|
|[HCLERK](https://www.govinfo.gov/link/crec/type/HCLERK)| Communication From The Clerk of the House|
|[HANNOUNCEMENT](https://www.govinfo.gov/link/crec/type/HANNOUNCEMENT)| Announcement by the Speaker|
|[HMORNINGDEBATE](https://www.govinfo.gov/link/crec/type/HMORNINGDEBATE)| Morning Hour Debates|
|[HREPORTON](https://www.govinfo.gov/link/crec/type/HREPORTON)| Report On|
|[HCONFREPORTON](https://www.govinfo.gov/link/crec/type/HCONFREPORTON)| Conference Report On|
|[HSENATEBILLREFERRED](https://www.govinfo.gov/link/crec/type/HSENATEBILLREFERRED)| Senate Bill Referred|
|[HLEGPROGRAM](https://www.govinfo.gov/link/crec/type/HLEGPROGRAM)| Legislative Program|
|[HTIMELIMIT](https://www.govinfo.gov/link/crec/type/HTIMELIMIT)| Time Limitation Of Referred Bill|
|[HEXPENDITURE](https://www.govinfo.gov/link/crec/type/HEXPENDITURE)| Expenditure Reports Concerning Official Foreign Travel|
|[HCORRECTIONS](https://www.govinfo.gov/link/crec/type/HCORRECTIONS)| Honoring|
|[COMMEMORATING](https://www.govinfo.gov/link/crec/type/COMMEMORATING)| Commemorations|
|[CELEBRATING](https://www.govinfo.gov/link/crec/type/CELEBRATING)| Celebrations|
|[COMMENDING](https://www.govinfo.gov/link/crec/type/COMMENDING)| Commending|
|[PASSINGOF](https://www.govinfo.gov/link/crec/type/PASSINGOF)| On the passing of|
|[TRIBUTETO](https://www.govinfo.gov/link/crec/type/TRIBUTETO)| Tribute|
|[CONGRATULATIONS](https://www.govinfo.gov/link/crec/type/CONGRATULATIONS)| Congratulations|
|[RETIREMENT](https://www.govinfo.gov/link/crec/type/RETIREMENT)| Retirement Of|
|[DESIGNATING](https://www.govinfo.gov/link/crec/type/DESIGNATING)| Designating|
|[INMEMORYOF](https://www.govinfo.gov/link/crec/type/INMEMORYOF)| In Memory Of|
|[HPETITIONS](https://www.govinfo.gov/link/crec/type/HPETITIONS)| Petitions|
|[HAMENDMENTS](https://www.govinfo.gov/link/crec/type/HAMENDMENTS)| Amendments|
|[HEARMARKS](https://www.govinfo.gov/link/crec/type/HEARMARKS)| Congressional Earmarks, Limited Tax Benefits, Or Limited Tariff Benefits|

##### Senate Type Values

|Type Value | User Readable Value|
|-----------|---------------------|
|[SENATEALLOTHER](https://www.govinfo.gov/link/crec/type/SENATEALLOTHER)| All Other Legislative Business|
|[SAPPOINTMENT](https://www.govinfo.gov/link/crec/type/SAPPOINTMENT)| Appointment of The Acting President Pro Tempore|
|[SORDER](https://www.govinfo.gov/link/crec/type/SORDER)| Order of Procedure|
|[SSCHEDULE](https://www.govinfo.gov/link/crec/type/SSCHEDULE)| Schedule|
|[SSSCHEDULE](https://www.govinfo.gov/link/crec/type/SSSCHEDULE)| Senate Schedule|
|[SMEASUREDCAL](https://www.govinfo.gov/link/crec/type/SMEASUREDCAL)| Measures Placed on the Calendar|
|[SMBUSINESS](https://www.govinfo.gov/link/crec/type/SMBUSINESS)| Morning Business|
|[SCONBUSINESS](https://www.govinfo.gov/link/crec/type/SCONBUSINESS)| Conclusion of Morning Business|
|[SRECESS](https://www.govinfo.gov/link/crec/type/SRECESS)| Recess|
|[SADDITIONAL](https://www.govinfo.gov/link/crec/type/SADDITIONAL)| Additional Statements|
|[SMSGHOUSE](https://www.govinfo.gov/link/crec/type/SMSGHOUSE)| Message From the House|
|[SCOMMREPORT](https://www.govinfo.gov/link/crec/type/SCOMMREPORT)| Reports of Committees|
|[SEXECREPORT](https://www.govinfo.gov/link/crec/type/SEXECREPORT)| Executive Reports of Committees|
|[SPETANDMEM](https://www.govinfo.gov/link/crec/type/SPETANDMEM)| Petitions and Memorials|
|[SREFERRED](https://www.govinfo.gov/link/crec/type/SREFERRED)| Measures Referred|
|[SREADFIRST](https://www.govinfo.gov/link/crec/type/SREADFIRST)| Measures Read the First Time|
|[SDISCHARGED](https://www.govinfo.gov/link/crec/type/SDISCHARGED)| Measures Discharged|
|[SDICHARGEREF](https://www.govinfo.gov/link/crec/type/SDICHARGEREF)| Discharge and Referral|
|[SMSGEXEC](https://www.govinfo.gov/link/crec/type/SMSGEXEC)| Executive Messages Referred|
|[SINTROBILLS](https://www.govinfo.gov/link/crec/type/SINTROBILLS)| Introduction of Bills and Joint Resolutions|
|[SSUBMISSION](https://www.govinfo.gov/link/crec/type/SSUBMISSION)| Submission of Concurrent and Senate Resolutions|
|[SCOSPONSORS](https://www.govinfo.gov/link/crec/type/SCOSPONSORS)| Additional Cosponsors|
|[SSTATEMENTS](https://www.govinfo.gov/link/crec/type/SSTATEMENTS)| Statements on Introduced Bills and Joint Resolutions|
|[SSUBMITTED](https://www.govinfo.gov/link/crec/type/SSUBMITTED)| Submitted Resolutions|
|[SRESOLUTION](https://www.govinfo.gov/link/crec/type/SRESOLUTION)| Senate Resolution|
|[SAMENDMENTSSUB](https://www.govinfo.gov/link/crec/type/SAMENDMENTSSUB)| Amendments Submitted and Proposed|
|[SAMENDMENTTEXT](https://www.govinfo.gov/link/crec/type/SAMENDMENTTEXT)| Text of Amendments|
|[SNOTICE](https://www.govinfo.gov/link/crec/type/SNOTICE)| Notice of Hearings|
|[SAUTHORITY](https://www.govinfo.gov/link/crec/type/SAUTHORITY)| Authority for Committees to Meet|
|[SPRIVILEGES](https://www.govinfo.gov/link/crec/type/SPRIVILEGES)| Privileges of the Floor|
|[SPROGRAM](https://www.govinfo.gov/link/crec/type/SPROGRAM)| Program|
|[SCALENDAR](https://www.govinfo.gov/link/crec/type/SCALENDAR)| The Calendar|
|[SCONSENTAGREE](https://www.govinfo.gov/link/crec/type/SCONSENTAGREE)| Unanimous Consent Agreement|
|[SCONSENTREQUEST](https://www.govinfo.gov/link/crec/type/SCONSENTREQUEST)| Unanimous Consent Request|
|[SORDERFOR](https://www.govinfo.gov/link/crec/type/SORDERFOR)| Order For|
|[SEXECSESSION](https://www.govinfo.gov/link/crec/type/SEXECSESSION)| Executive Session|
|[SEXECCAL](https://www.govinfo.gov/link/crec/type/SEXECCAL)| Executive Calendar|
|[SLEGISLATIVE](https://www.govinfo.gov/link/crec/type/SLEGISLATIVE)| Legislative Session|
|[SNOMINATIONS](https://www.govinfo.gov/link/crec/type/SNOMINATIONS)| Nominations|
|[SWITHDRAWAL](https://www.govinfo.gov/link/crec/type/SWITHDRAWAL)| Withdrawals|
|[SCONFIRMATIONS](https://www.govinfo.gov/link/crec/type/SCONFIRMATIONS)| Confirmation|
|[SCLOTURE](https://www.govinfo.gov/link/crec/type/SCLOTURE)| Cloture Motion|

##### Extensions of Remarks Type Values

|Type Value | User Readable Value|
|-----------|--------------------|
|[ESENATECOMMITTEE](https://www.govinfo.gov/link/crec/type/ESENATECOMMITTEE)| Senate Committee Meetings|
|[EINTRODUCTIONOF](https://www.govinfo.gov/link/crec/type/EINTRODUCTIONOF)| Introducing Legislation|


### CREC Section Query

Return a specific Congressional Record section

#### Parameters

- **collection:** Required - Value is crec.

- **section:** Required - Congressional Record section. Values are dailydigest, senate, house, extensions.

- **publishdate:** Optional - If date is not provided, the most recent version of the Congressional Record section is returned. Values are date formated as yyyy-mm-dd or mostrecent. Default is most recent.

- **link-type: Optional - format of the returned document. Default is pdf. Other values are mods, premis, details. Note:** mods, premis, and details are returned at the package level because they are not available for section level granules.

#### Examples

- https://www.govinfo.gov/link/crec/section/dailydigest
- https://www.govinfo.gov/link/crec/section/dailydigest?publishdate=2011-11-22
- https://www.govinfo.gov/link/crec/section/dailydigest?publishdate=2023-09-30

### Senate Amendments Query

Return the text of a specific Senate Amendment within the Congressional Record

#### Parameters

- **collection:** Required - Value is crec.

- **congress:** Required - Congress number. Sample value is 117.

- **amendmentNumber:** Required - Senate amendment number. Sample value is 5010.

- **link-type:** Optional - format of the returned document. Default is html. Other values are mods, premis, details, context, related.

#### Examples

- https://www.govinfo.gov/link/crec/samendment/117/5010

## Congressional Reports (CRPT)

### Report Type and Number Query

congress, report type, report number

#### Parameters

- **collection:** Required - Value is crpt.

- **congress:** Required - Congress number. Sample value is 112.

- **reportnum:** Required - report number. Congressional reports are numbered consecutively within a Congress for each report type. Sample value is 154.

- **doctype:** Required - congressional report type. Congressional reports can either be house reports, senate reports, or senate executive reports. Values are hrpt, srpt, erpt.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details, context, related.

#### Examples

- https://www.govinfo.gov/link/crpt/112/srpt/154/
- https://www.govinfo.gov/link/crpt/117/hrpt/663?link-type=details

### Associated Bill Query

Returns a specific Congressional report based on an associated Congressional bill

#### Parameters

- **collection:** Required - Value is crpt.

- **congress:** Required - Congress number. Sample value is 112.

- **associatedbillnum: Required - Congressional reports often accompany a specific bill. Note:** some associated bill numbers may produce multiple results. This will occur when two different reports are issued to accompany a single bill within a single Congress. In this case, the desired report may not be returned. Sample value is h.r.2297.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details, context, related.

#### Examples

- https://www.govinfo.gov/link/crpt/112/h.r.2297
- https://www.govinfo.gov/link/crpt/118/s.311

## Federal Register (FR)

### FR Volume and Page Number Query

Return a specific portion of the Federal Register by Volume and page citation

#### Parameters

- **collection:** Required - Value is fr.

- **volume:** Required - volume number. Sample value is 76.

- **page: Required - page number. Federal Register pages are numbered consecutively within a volume. Note:** when multiple granules are contained on a page, content and metadata for the last granule on the page will be returned. Recommend selecting PDF link-type to return content for all granules on a page. Sample value is 575.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details, context, related.

#### Examples

- https://www.govinfo.gov/link/fr/76/575
- https://www.govinfo.gov/link/fr/87/8949?link-type=related

### Federal Register document number Query

Returns specific FR content by FR document number

#### Parameters

- **publishdate:** Optional If date is not provided, the most recent version of the Federal Register is returned. Values are date formated as yyyy-mm-dd or mostrecent. Default is most recent.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are toc, mods, premis, details, context, zip.

#### Examples

- https://www.govinfo.gov/link/fr/2010-32535
- https://www.govinfo.gov/link/fr/2022-03394
### Latest Federal Register Query

Returns the latest edition of the Federal Register

#### Parameters

- **collection:** Required - Value is fr.

- **frdocnum:** Required - The is the FR doc number that is listed at the end of each Federal Register document. Sample value is 2010-32535.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Examples

- https://www.govinfo.gov/link/fr/latest
- https://www.govinfo.gov/link/fr/latest?link-type=toc 


## Public and Private Laws (PLAW)

### Congress, Law Type and Number Query

Returns a public or private law based on Congress, law type, and number

#### Parameters

- **collection:** Required - Value is plaw.

- **congress:** Required - Congress number. Sample value is 111.

- **lawtype:** Required - law type. Laws can either be public laws or private laws. Values are public, private.

- **lawnum:** Required - law number. Laws are numbered consecutively within each law type within a Congress. Sample value is 78.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details, related.

#### Example

- https://www.govinfo.gov/link/plaw/111/public/78
- https://www.govinfo.gov/link/plaw/115/private/1?link-type=details 

### Associated Bill Query

Return a public or private law (if it exists) based on associated bill numbers

#### Parameters

- **collection:** Required - Value is plaw.

- **congress:** Required - Congress number. Sample value is 111.

- **associatedbillnum:** Required - Public and private laws are associated with a primary bill number. The primary bill number is listed at the beginning of the law. Sample value is S. 3397.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Example

- https://www.govinfo.gov/link/plaw/111/s.3397
- https://www.govinfo.gov/link/plaw/111/h.r.2544


### Statutes at Large citation Query

Returns public or private law based on Statutes at Large citation

#### Parameters

- **collection:** Required - Value is plaw.

- **statutecitation:** Required - A Statutes at Large citation is listed at the top of each page of a law. Use a + (plus sign) in place of spaces in the citation. Sample value is 124+stat+2859.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Example

- https://www.govinfo.gov/link/plaw/124+stat+2859
- https://www.govinfo.gov/link/plaw/131+stat+2278?link-type=details

## Statutes at Large (STATUTE)

### Statute by Congress and Law Query

Returns a public or private law in the U.S. Statutes at Large based on Congress, law type, and number

#### Parameters

- **collection:** Required - Value is statute.

- **congress:** Required - Congress number. Sample value is 108.

- **lawtype:** Required - law type. Laws can either be public laws or private laws. Values are public, private.

- **lawnum:** Required - law number. Laws are numbered consecutively within each law type within a Congress. Sample value is 841.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Example

- https://www.govinfo.gov/link/statute/108/public/481
- https://www.govinfo.gov/link/statute/115/public/114

### Statute Citation Query

Returns a Statutes at Large document based on Statute Citation

#### Parameters

- **collection:** Required - Value is statute.

- **volume:** Required - volume number. Sample value is 118.

- **page: Required - page number. Statutes at Large pages are numbered consecutively within a volume. Note:** when multiple granules are contained on a page, content and metadata for the last granule on the page will be returned. Recommend selecting PDF link-type to return content for all granules on a page. Sample value is 3910.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details, context.

#### Example

- https://www.govinfo.gov/link/statute/118/3910
- https://www.govinfo.gov/link/statute/131/2278

## United States Code (USCODE)

### Query

title number, type, section, year OR most recent

#### Parameters

- **collection:** Required - Value is uscode.

- **title:** Required - title number. Sample value is 5.

- **section:** Required - section number. Sample value is 104.

- **type:** Optional - U.S. Code section type. Values are usc, uscappendix. Default value is usc.
year Optional - four digit year OR mostrecent. If year is not provided the most recent version of the U.S. Code section is returned. Default is most recent. Sample value is 2010.

- **link-type:** Optional - format of the returned document. Default is pdf. Other values are html, mods, premis, details.

#### Examples

- https://www.govinfo.gov/link/uscode/50/797?year=2011&type=usc
- https://www.govinfo.gov/link/uscode/50/797
- https://www.govinfo.gov/link/uscode/54/101121?year=mostrecent&link-type=details
- https://www.govinfo.gov/link/uscode/50/2403-1?type=uscappendix
- https://www.govinfo.gov/link/uscode/28/32?type=uscappendix

## Common Errors

### Multiple Results Found

This error occurs when more than one document matches parameters for a given request. Additional parameters must be specified in order to return a single document.

### No Results Found

This error occurs if a match document was not found for the given parameters. Please check the API documentation to make sure values provided are correct.

### Validation Failed

This error occurs when request parameters fail validation. Possible causes include the following:

- No queries found for COLLECTION CODE. This error occurs if the value for collection is incorrect or has not been enabled yet. Please check the documentation for available collections and collection codes.

- Request parameter XXXX is not found but is required. This error occurs if a required parameter is missing in the URL. Please check the documentation for required parameters for each collection.

- The value provided for XXXX is invalid. One of the following [XXXX, YYYY] is expected. This error occurs if a value provided for a parameter is not among the listed choices. Please check the documentation for parameter values.

### Content File Not Found

This error can occur for an invalid or unavailable link-type value. Allowable values are pdf, html, mods, premis and details. This error can also occur if a requested link-type is not available for a specific document.

### System Error

Please report any errors encountered while using the Link Service on https://ask.gpo.gov/s/contactsupport using the `govinfo.gov question` category. Please include the link you tried generating and what issue you are seeing.
