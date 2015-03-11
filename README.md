# link-service
The link service is used to create links to content and metadata on FDsys.

The service is currently available for the for the collections below. The collection code is listed in parenthesis after each collection name, and the available queries are listed below each collection.

##Code of Federal Regulations (CFR)

###Query: 
title number, part number, section number, year OR most recent

###Parameters:
collection: Required - Value is cfr. 
titlenum: Required - This is the title number. Sample value is 3. 
partnum: Required - This is the part number. Sample value is 100. 
sectionnum: Optional - This is the section number. Sample value is 1. If section number is not provided the entire part will be returned. 
year: Optional - This is the four digit numerical year OR mostrecent. If year is not provided the most recent version of the CFR section or part is returned. Default is most recent. Sample value is 2011. 
link-type: Optional - This is the format of the returned document. Default is pdf. Other values are xml, mods, premis, contentdetail. 

###Examples:
http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&year=2011
http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&year=mostrecent
http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1
http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&link-type=premis
http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100&sectionnum=1&link-type=mods
http://api.fdsys.gov/link?collection=cfr&titlenum=3&partnum=100 
