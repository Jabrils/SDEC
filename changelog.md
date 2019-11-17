# SDEC Changelog

## v0.1.2
|#|Detail
|---|---
|1|.conf now saves all of the elements on the first line
|2|SDEC.CreateSeqDomainDictionary function is a bit more flexible now. Model_name is now optional, & you can now define useUnknownChar is you don't want to use the the unknown char 
|3|removed a bunch of unused vars
|4|made a very clear distinction between the SDEC library, & what functions I wrote using the library to best fit the example dataset!


## v0.1.1
|#|Detail
|---|---
|1|Added a null character to every sequence counter, to be used for when met with unrecognizable characters
|2|Added the tanh squashing function for sequence counters