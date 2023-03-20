[comment]: # "Auto-generated SOAR connector documentation"
# Cisco Umbrella Investigate

Publisher: Splunk  
Connector Version: 1\.2\.0  
Product Vendor: Cisco  
Product Name: Cisco Umbrella Investigate  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 5\.5\.0  

This app implements investigative actions by querying the Cisco Umbrella Investigate cloud service


# Splunk> SOAR

Welcome to the open-source repository for Splunk> SOAR’s Cisco Umbrella Investigate App.

Please have a look at our [Contributing
Guide](https://github.com/Splunk-SOAR-Apps/.github/blob/main/.github/CONTRIBUTING.md) if you are
interested in contributing, raising issues, or learning more about open-source Splunk SOAR apps.

## Legal and License

This Splunk SOAR App is licensed under the Apache 2.0 license. Please see our [Contributing
Guide](https://github.com/Splunk-SOAR-Apps/.github/blob/main/.github/CONTRIBUTING.md#legal-notice)
for further details.

## Port Information

The app uses HTTP/ HTTPS protocol for communicating with the Cisco Umbrella Investigate server.
Below are the default ports used by Splunk SOAR.

| SERVICE NAME | TRANSPORT PROTOCOL | PORT |
|--------------|--------------------|------|
| **http**     | tcp                | 80   |
| **https**    | tcp                | 443  |

## Note:

-   Kindly refer [official
    documentation](https://developer.cisco.com/docs/cloud-security/#!introduction) for API rate
    limits


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Cisco Umbrella Investigate asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**access\_token** |  required  | password | Cisco Umbrella Investigate API Access Token

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity  
[domain reputation](#action-domain-reputation) - Query Cisco Umbrella Investigate for domain info  
[ip reputation](#action-ip-reputation) - Query Cisco Umbrella Investigate for IP info  
[whois domain](#action-whois-domain) - Run a whois query on Cisco Umbrella Investigate for the given domain  

## action: 'test connectivity'
Validate the asset configuration for connectivity

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'domain reputation'
Query Cisco Umbrella Investigate for domain info

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**domain** |  required  | Domain to query | string |  `domain` 

#### Action Output
DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action\_result\.status | string |  |   success  failed 
action\_result\.parameter\.domain | string |  `domain`  |   testdomain\.com 
action\_result\.data\.\*\.category | string |  |   Search Engines  Malware 
action\_result\.data\.\*\.category\_info\.content\_categories | string |  |   Search Engines 
action\_result\.data\.\*\.category\_info\.security\_categories | string |  |   Malware 
action\_result\.data\.\*\.category\_info\.status | numeric |  |   1  -1 
action\_result\.data\.\*\.indicators\.\*\.indicator | string |  |   Geo Popularity Score  Keyword Score  Lexical 
action\_result\.data\.\*\.indicators\.\*\.indicator\_id | string |  |   Geo Popularity Score 
action\_result\.data\.\*\.indicators\.\*\.normalized\_score | numeric |  |   2  60  100 
action\_result\.data\.\*\.indicators\.\*\.score | numeric |  |   -3.610878170000002  0.09264255482489717  0.606 
action\_result\.data\.\*\.relative\_links\.\* | numeric |  |   4289 
action\_result\.data\.\*\.risk\_score | numeric |  |   6 
action\_result\.data\.\*\.security\_info\.asn\_score | numeric |  |   -0.03286849936319416  0 
action\_result\.data\.\*\.security\_info\.attack | string |  |  
action\_result\.data\.\*\.security\_info\.dga\_score | numeric |  |   0  -15.55033332819711 
action\_result\.data\.\*\.security\_info\.entropy | numeric |  |   1.91829583405449  2.75 
action\_result\.data\.\*\.security\_info\.fastflux | boolean |  |   False  True 
action\_result\.data\.\*\.security\_info\.found | boolean |  |   False  True 
action\_result\.data\.\*\.security\_info\.geodiversity | string |  |  
action\_result\.data\.\*\.security\_info\.geodiversity\.\* | numeric |  |   0.0001  0.1429 
action\_result\.data\.\*\.security\_info\.geodiversity\_normalized | string |  |  
action\_result\.data\.\*\.security\_info\.geodiversity\_normalized\.\* | numeric |  |   0.0003299100640734098  0.009745995689748824 
action\_result\.data\.\*\.security\_info\.geoscore | numeric |  |   0  0.002894054671255598 
action\_result\.data\.\*\.security\_info\.handlings\.normal | numeric |  |  
action\_result\.data\.\*\.security\_info\.ks\_test | numeric |  |   0  0.2846253137451792 
action\_result\.data\.\*\.security\_info\.pagerank | numeric |  |   60.32995  0 
action\_result\.data\.\*\.security\_info\.perplexity | numeric |  |   0.1878675610437336  1.122248102917671 
action\_result\.data\.\*\.security\_info\.popularity | numeric |  |   100  0 
action\_result\.data\.\*\.security\_info\.prefix\_score | numeric |  |   -0.1054320152441063  0 
action\_result\.data\.\*\.security\_info\.rip\_score | numeric |  |   -3.051340626556875  0 
action\_result\.data\.\*\.security\_info\.securerank2 | numeric |  |   100  -0.004050008137296145 
action\_result\.data\.\*\.security\_info\.threat\_type | string |  |  
action\_result\.data\.\*\.security\_info\.tld\_geodiversity | string |  |  
action\_result\.data\.\*\.security\_info\.tld\_geodiversity\.\* | numeric |  |   0.01008192795884705 
action\_result\.data\.\*\.status\_desc | string |  |   SAFE  MALICIOUS 
action\_result\.data\.\*\.tag\_info\.\*\.attacks | string |  |   Rig 
action\_result\.data\.\*\.tag\_info\.\*\.categories | string |  |   Malware 
action\_result\.data\.\*\.tag\_info\.\*\.category | string |  |  
action\_result\.data\.\*\.tag\_info\.\*\.period\.begin | string |  |  
action\_result\.data\.\*\.tag\_info\.\*\.period\.end | string |  |  
action\_result\.data\.\*\.tag\_info\.\*\.threatTypes | string |  |   Exploit Kit 
action\_result\.data\.\*\.tag\_info\.\*\.timestamp | numeric |  |   1428593707849  1496547887014 
action\_result\.summary\.domain\_status | string |  `domain`  |   SAFE  MALICIOUS 
action\_result\.summary\.risk\_score | numeric |  |   0  6 
action\_result\.summary\.total\_co\_occurances | numeric |  |   0 
action\_result\.summary\.total\_relative\_links | numeric |  |   100  0 
action\_result\.summary\.total\_tag\_info | numeric |  |   1  2 
action\_result\.message | string |  |   Total co occurances\: 0, Domain status\: SAFE, Total tag info\: 1, Total relative links\: 100  Total co occurances\: 0
Domain status\: MALICIOUS
Total tag info\: 2
Total relative links\: 0 
summary\.total\_objects | numeric |  |   1 
summary\.total\_objects\_successful | numeric |  |   1   

## action: 'ip reputation'
Query Cisco Umbrella Investigate for IP info

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip** |  required  | IP to query | string |  `ip` 

#### Action Output
DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action\_result\.status | string |  |   success  failed 
action\_result\.parameter\.ip | string |  `ip`  |   22\.22\.22\.22 
action\_result\.data\.\*\.id | string |  |   84626522 
action\_result\.data\.\*\.name | string |  `domain`  |   test\_domain\.net 
action\_result\.summary\.ip\_status | string |  |   MALICIOUS 
action\_result\.summary\.total\_blocked\_domains | numeric |  `domain`  |   37 
action\_result\.message | string |  |   Total blocked domains\: 37, Ip status\: MALICIOUS 
summary\.total\_objects | numeric |  |   1 
summary\.total\_objects\_successful | numeric |  |   1   

## action: 'whois domain'
Run a whois query on Cisco Umbrella Investigate for the given domain

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**domain** |  required  | Domain to query | string |  `domain`  `url` 

#### Action Output
DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action\_result\.status | string |  |   success  failed 
action\_result\.parameter\.domain | string |  `domain`  `url`  |   test\_domain\.com 
action\_result\.data\.\*\.addresses | string |  |   1600 amphitheatre parkway, 
action\_result\.data\.\*\.administrativeContactCity | string |  |   Mountain View 
action\_result\.data\.\*\.administrativeContactCountry | string |  |   UNITED STATES 
action\_result\.data\.\*\.administrativeContactEmail | string |  `email`  |   dns\-admin\@test\_domain\.com 
action\_result\.data\.\*\.administrativeContactFax | string |  |  
action\_result\.data\.\*\.administrativeContactFaxExt | string |  |  
action\_result\.data\.\*\.administrativeContactName | string |  |   Domain Administrator 
action\_result\.data\.\*\.administrativeContactOrganization | string |  |   Test LLC 
action\_result\.data\.\*\.administrativeContactPostalCode | string |  |   94043 
action\_result\.data\.\*\.administrativeContactState | string |  |   CA 
action\_result\.data\.\*\.administrativeContactStreet | string |  |   1600 amphitheatre parkway, 
action\_result\.data\.\*\.administrativeContactTelephone | string |  |   16502530000 
action\_result\.data\.\*\.administrativeContactTelephoneExt | string |  |  
action\_result\.data\.\*\.auditUpdatedDate | string |  |   2018\-05\-17 12\:38\:07\.000 UTC 
action\_result\.data\.\*\.billingContactCity | string |  |  
action\_result\.data\.\*\.billingContactCountry | string |  |  
action\_result\.data\.\*\.billingContactEmail | string |  |  
action\_result\.data\.\*\.billingContactFax | string |  |  
action\_result\.data\.\*\.billingContactFaxExt | string |  |  
action\_result\.data\.\*\.billingContactName | string |  |  
action\_result\.data\.\*\.billingContactOrganization | string |  |  
action\_result\.data\.\*\.billingContactPostalCode | string |  |  
action\_result\.data\.\*\.billingContactState | string |  |  
action\_result\.data\.\*\.billingContactStreet | string |  |  
action\_result\.data\.\*\.billingContactTelephone | string |  |  
action\_result\.data\.\*\.billingContactTelephoneExt | string |  |  
action\_result\.data\.\*\.created | string |  |   1997\-09\-15 
action\_result\.data\.\*\.domainName | string |  `domain`  |   test\_domain\.com 
action\_result\.data\.\*\.emails | string |  `email`  |   dns\-admin\@test\_domain\.com 
action\_result\.data\.\*\.expires | string |  |   2020\-09\-14 
action\_result\.data\.\*\.hasRawText | boolean |  |   False  True 
action\_result\.data\.\*\.nameServers | string |  |   ns4\.test\_domain\.com 
action\_result\.data\.\*\.recordExpired | boolean |  |   True  False 
action\_result\.data\.\*\.registrantCity | string |  |   Mountain View 
action\_result\.data\.\*\.registrantCountry | string |  |   UNITED STATES 
action\_result\.data\.\*\.registrantEmail | string |  `email`  |   dns\-admin\@test\_domain\.com 
action\_result\.data\.\*\.registrantFax | string |  |   16502530001 
action\_result\.data\.\*\.registrantFaxExt | string |  |  
action\_result\.data\.\*\.registrantName | string |  |   Domain Administrator 
action\_result\.data\.\*\.registrantOrganization | string |  |   Test LLC 
action\_result\.data\.\*\.registrantPostalCode | string |  |   94043 
action\_result\.data\.\*\.registrantState | string |  |   CA 
action\_result\.data\.\*\.registrantStreet | string |  |   1600 amphitheatre parkway, 
action\_result\.data\.\*\.registrantTelephone | string |  |   16502530000 
action\_result\.data\.\*\.registrantTelephoneExt | string |  |  
action\_result\.data\.\*\.registrarIANAID | string |  |   292 
action\_result\.data\.\*\.registrarName | string |  |   MarkMonitor, Inc\. 
action\_result\.data\.\*\.status | string |  |   clientDeleteProhibited clientTransferProhibited clientUpdateProhibited serverDeleteProhibited serverTransferProhibited serverUpdateProhibited 
action\_result\.data\.\*\.technicalContactCity | string |  |   Mountain View 
action\_result\.data\.\*\.technicalContactCountry | string |  |   UNITED STATES 
action\_result\.data\.\*\.technicalContactEmail | string |  `email`  |   dns\-admin\@test\_domain\.com 
action\_result\.data\.\*\.technicalContactFax | string |  |   16502530001 
action\_result\.data\.\*\.technicalContactFaxExt | string |  |  
action\_result\.data\.\*\.technicalContactName | string |  |   Domain Administrator 
action\_result\.data\.\*\.technicalContactOrganization | string |  |   Test LLC 
action\_result\.data\.\*\.technicalContactPostalCode | string |  |   94043 
action\_result\.data\.\*\.technicalContactState | string |  |   CA 
action\_result\.data\.\*\.technicalContactStreet | string |  |   1600 amphitheatre parkway, 
action\_result\.data\.\*\.technicalContactTelephone | string |  |   16502530000 
action\_result\.data\.\*\.technicalContactTelephoneExt | string |  |  
action\_result\.data\.\*\.timeOfLatestRealtimeCheck | numeric |  |   1526564647993 
action\_result\.data\.\*\.timestamp | string |  |  
action\_result\.data\.\*\.updated | string |  |   2018\-02\-21 
action\_result\.data\.\*\.whoisServers | string |  |   whois\.markmonitor\.com 
action\_result\.data\.\*\.zoneContactCity | string |  |  
action\_result\.data\.\*\.zoneContactCountry | string |  |  
action\_result\.data\.\*\.zoneContactEmail | string |  |  
action\_result\.data\.\*\.zoneContactFax | string |  |  
action\_result\.data\.\*\.zoneContactFaxExt | string |  |  
action\_result\.data\.\*\.zoneContactName | string |  |  
action\_result\.data\.\*\.zoneContactOrganization | string |  |  
action\_result\.data\.\*\.zoneContactPostalCode | string |  |  
action\_result\.data\.\*\.zoneContactState | string |  |  
action\_result\.data\.\*\.zoneContactStreet | string |  |  
action\_result\.data\.\*\.zoneContactTelephone | string |  |  
action\_result\.data\.\*\.zoneContactTelephoneExt | string |  |  
action\_result\.summary\.city | string |  |   Mountain View 
action\_result\.summary\.country | string |  |   UNITED STATES 
action\_result\.summary\.organization | string |  |   Google LLC 
action\_result\.message | string |  |   Organization\: Test LLC, Country\: UNITED STATES, City\: Mountain View 
summary\.total\_objects | numeric |  |   1 
summary\.total\_objects\_successful | numeric |  |   1 