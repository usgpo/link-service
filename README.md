# link-service
The link service is used to create links to content and metadata on FDsys.

The service is currently available for the for the collections below. The collection code is listed in parenthesis after each collection name. The available queries and parameters are listed below each collection.

##Code of Federal Regulations (CFR)

###Query: 
title number, part number, section number, year OR most recent

####Parameters:
collection: Required - Value is cfr. 

titlenum: Required - This is the title number. Sample value is 3. 

partnum: Required - This is the part number. Sample value is 100. 

sectionnum: Optional - This is the section number. Sample value is 1. If section number is not provided the entire part will be returned. 

year: Optional - This is the four digit numerical year OR mostrecent. If year is not provided the most recent version of the CFR section or part is returned. Default is most recent. Sample value is 2011. 

link-type: Optional - This is the format of the returned document. Default is pdf. Other values are xml, mods, premis, contentdetail. 

####Examples:
http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&year=2011

http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&year=mostrecent

http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1

http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&link-type=premis

http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&link-type=mods

http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100 

##Compilation of Presidential Documents (CPD)

###Query: 

document type, document number

####Parameters:

collection: Required - Value is cpd. 

doctype: Required - Values are executiveorder, proclamation, determination. 

docnum: Required - This is the numerical document number. Sample value is 13514. 

link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail. 

####Examples:

http://api.fdsys.gov/link?collection=cpd&doctype=proclamation&docnum=8685 

http://api.fdsys.gov/link?collection=cpd&doctype=executiveorder&docnum=13514&link-type=html 

http://api.fdsys.gov/link?collection=cpd&docnum=94-35&doctype=determination 

###Query: 

dcpd type OR dcpd number

####Parameters:

collection: Required - Value is cpd. 

year: Required - This is the four digit numerical year. The first Daily Compilation of Presidential Documents (dcpd) document was published on 1/20/2009. Sample value is 2010. 

dcpnumber: Optional - This is the five digit numerical identifier on a dcpd document. It does not include the four digit year. Document are numbered sequentially within each year. Leading zeros can be supplied but are not required. Sample value is 00123. Either dcpdnumber or dcpdtype is required. If a document contains both a dcpdnumber and a dcpdtype, we recommend providing dcpdtype instead of dcpdnumber. If both are provided, precedence is given to dcpdnumber. 

dcpdtype: Optional - This is the type of dcpd document. Values are digest, nominations, checklist, actsapproved. Either dcpdnumber or dcpdtype is required. If a document contains both a dcpdnumber and a dcpdtype, we recommend providing dcpdtype instead of dcpdnumber. If both are provided, precedence is given to dcpdnumber. 
link-type: Optional - This is the format of the returned document. Default is pdf. Other values are html, mods, premis, contentdetail. 


####Examples:

http://api.fdsys.gov/link?collection=cpd&dcpdnumber=00123&year=2010&link-type=contentdetail 

http://api.fdsys.gov/link?collection=cpd&dcpdtype=nominations&year=2011 
