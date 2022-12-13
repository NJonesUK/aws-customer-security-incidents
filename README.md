# Background

Security is an exercise in managing risk. Reviewing the common root causes of security incidents is an effective way to guide prioritized remediation efforts.

This repository seeks to index all publicly disclosed AWS customer security incidents with a known root cause. It will exclude incidents involving exposed data stores (e.g S3 bucket leaks, exposed managed or hosted databases).
Those incidents are already well understood, and examples can be found cataloged in places like [nagwww's s3-leaks repo](https://github.com/nagwww/s3-leaks), [upguard's reports](https://www.upguard.com/breaches), [hackmeggedon's annual rollup reports (2022)](https://www.hackmageddon.com/2022/02/21/leaky-buckets-in-2022/) and [Corey Quinn's LWIAWS](https://www.lastweekinaws.com) S3 Bucket Negligence Award.

It also excludes incidents impacting individuals, such as the periodic reports of cryptomining due to compromised credentials. [1](https://vertis.io/2013/12/16/unauthorised-litecoin-mining/) [2](https://readwrite.com/amazon-web-services-hack-bitcoin-miners-github/) [3](http://www.nvenky.in/2014/03/bitcoin-mining-closed-my-aws-account.html)

### A Note on Blameless Postmortems

This repository is in no way intended as a criticism of the listed companies. In the spirit of blameless postmortems [<sup>1</sup>](#1), our goal is to learn from incidents without an atmosphere of blame.

# Catalog of AWS Customer Security Incidents

A repository of breaches of AWS customers

| Name  | Date | Root Cause | Escalation Vector(s) | Impact | Link to details|
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| Uber | 2014, May  | Github Gist (data analysis script) with AWS credentials | N/A | 50,000 records, including names and driver’s licenses from S3 hosted database prunes | [Exclusive: In lawsuit over hacking, Uber probes IP address assigned to Lyft exec - sources ](https://www.reuters.com/article/uk-uber-tech-lyft-hacking-exclusive/exclusive-in-lawsuit-over-hacking-uber-probes-ip-address-assigned-to-lyft-exec-sources-idUKKCN0S20D020151008), [A blameless post-mortem of USA v. Joseph Sullivan](https://magoo.medium.com/a-blameless-post-mortem-of-usa-v-joseph-sullivan-a137162f7fc9) |
| Code Spaces  | 2014, June  | AWS Console Credentials (Phishing?) | Attacker created additional accounts/access keys | Wiped S3 buckets, EC2 instances, AMIs, EBS snapshots | [Hacker puts code spaces out of business](https://threatpost.com/hacker-puts-hosting-service-code-spaces-out-of-business/106761/)  |
| BrowserStack  | 2014, November  | Shellshock on exposed, outdated prototype machine | Access keys on server, used to create IAM user, create EC2, and mount backup | Steal user data and email users | [BrowserStack analysis](http://archive.today/rsmmS)  |
| DNC Hack by the GRU  | 2016, June  | Unknown, test clusters breached | EC2 Snapshots copied to attacker AWS accounts | Tableau and Vertica Queries | [DEMOCRATIC NATIONAL COMMITTEE v. THE RUSSIAN FEDERATION](https://www.politico.com/f/?id=00000168-6161-de11-af7d-ef7327ea0000)  |
| DataDog  | 2016, July  | CI/CD AWS access key and SSH private key leaked | Attacker attempted to pivot with customer credentials | 3 EC2 instances and subset of S3 buckets | [2016-07-08 Security Notice](https://web.archive.org/web/20201128071102/https://www.datadoghq.com/blog/2016-07-08-security-notice/)  |
| Uber | 2016, October  | ~13 Hacked Uber credentials purchased for forum gave access to private Github Repo with AWS credentials | N/A | Names and driver’s license numbers of 600k drivers, PII of 57 million users in unencrypted manual backup| [Uber concealed cyberattack ...](https://web.archive.org/web/20210824171652/https://www.bloomberg.com/news/articles/2017-11-21/uber-concealed-cyberattack-that-exposed-57-million-people-s-data), [A blameless post-mortem of USA v. Joseph Sullivan](https://magoo.medium.com/a-blameless-post-mortem-of-usa-v-joseph-sullivan-a137162f7fc9) |
| Lynda.com | 2016, December  | Private Github Repo with AWS credentials | N/A | User data for 9.5m users, attempted extortion | [2 Plead Guilty in 2016 Uber and Lynda.com Hacks](http://archive.today/oU2ZL) |
| OneLogin | 2017, May  | AWS keys | Created EC2 instances | Accessed database tables (with encrypted data) | [May 31, 2017 Security Incident](https://web.archive.org/web/20210620180614/https://www.onelogin.com/blog/may-31-2017-security-incident) |
| Politifact | 2017, October  | "Misconfigured cloud computing server" | N/A | Coinhive cryptojacking | [Hackers have turned Politifact’s website into a trap for your PC](https://web.archive.org/web/20200806102838/https://www.washingtonpost.com/news/the-switch/wp/2017/10/13/hackers-have-turned-politifacts-website-into-a-trap-for-your-pc/) |
| DXC Technologies | 2017, November  | Private AWS key exposed via Github | 244 EC2 instance started | Cryptomining | [DXC spills AWS private keys on public GitHub](https://web.archive.org/web/20210228215919/https://www.theregister.com/2017/11/14/dxc_github_aws_keys_leaked/) |
| Drizly  | 2018  | AWS Credentials committed to public github repo | N/A | Cryptojacking | [FEDERAL TRADE COMMISSION - Drizly Complaint](https://archive.ph/BbOvv) |
| LA Times  | 2018, February  | S3 global write access | N/A | Cryptojacking | [Coinhive cryptojacking added to homicide.latimes.com](https://web.archive.org/web/20210413201832/https://www.tripwire.com/state-of-security/security-data-protection/la-times-website-cryptojacking-attack/) |
| Tesla | 2018, February  | Globally exposed Kubernetes console, Pod with AWS credentials | N/A | Cryptojacking | [Hack Brief: Hackers Enlisted Tesla's Public Cloud to Mine Cryptocurrency](https://www.wired.com/story/cryptojacking-tesla-amazon-cloud/) |
| Chegg | 2018, April | Former contractor abuses broadly shared root credential | Unknown | 40 million users' data (from S3 bucket) | [FTC Complaint](https://www.ftc.gov/system/files/ftc_gov/pdf/2023151-Chegg-Complaint.pdf) |
| imToken | 2018, June  | Email account compromise | Reset AWS account password | Minimal customer device data | [ Disclosure of Security Incidents on imToken ](https://archive.ph/bRjXi) |
| Voova  | 2019, March  | Stolen credentials by former employee  | N/A | Deleted 23 servers |  [Sacked IT guy annihilates 23 of his ex-employer’s AWS servers](https://nakedsecurity.sophos.com/2019/03/22/sacked-it-guy-annihilates-23-of-his-ex-employers-aws-servers/)  |
| Capital One  | 2019, April  | "Misconfigured WAF" that allowed for a SSRF attack  | Over-privileged EC2 Role | 100 million credit applications |  [A Technical Analysis of the Capital One Cloud Misconfiguration Breach](https://www.fugue.co/blog/a-technical-analysis-of-the-capital-one-cloud-misconfiguration-breach)  |
| JW Player | 2019, September  | Weave Scope (publicly exposed), RCE by design | N/A | Cryptojacking | [How A Cryptocurrency Miner Made Its Way onto Our Internal Kubernetes Clusters](https://web.archive.org/web/20210828044334/https://medium.com/jw-player-engineering/how-a-cryptocurrency-miner-made-its-way-onto-our-internal-kubernetes-clusters-9b09c4704205) |
| Malindo Air | 2019, September  | Former employee insider threat | N/A | 35 million PII records | [ Malindo Air: Data Breach Was Inside Job](https://www.infosecurity-magazine.com/news/malindo-air-data-breach-was-inside/) |
| Imperva | 2019, October  | “Internal compute instance” globally accessible, “Contained” AWS API key | N/A | RDS snapshot stolen | [Imperva Security Update](https://web.archive.org/web/20210620143023/https://www.imperva.com/blog/ceoblog/) |
| Cameo | 2020, February  | Credentials in mobile app package | N/A | Access to backend infrastructure, including user data | [Celeb Shout-Out App Cameo Exposes Private Videos and User Data](https://www.vice.com/en/article/akwj5z/cameo-app-exposed-private-videos-user-data-passwords) |
| Open Exchange Rates | 2020, March | Third-party compromise exposing access key | N/A | User database | [Exchange rate service’s customer details hacked via AWS](https://nakedsecurity.sophos.com/2020/03/20/exchange-rate-services-customer-details-hacked-via-aws/) |
| Live Auctioneers | 2020, July | Compromised third party software granting access to cloud environment | N/A | User database, including MD5 hashed credentials | [Washington State OAG -  Live Auctioneers](https://www.atg.wa.gov/live-auctioneers/) |
| Twilio | 2020, July  |S3 global write access | N/A | Magecart[<sup>2</sup>](#2) | [Incident Report: TaskRouter JS SDK Security Incident](https://web.archive.org/web/20210813010417/https://www.twilio.com/blog/incident-report-taskrouter-js-sdk-july-2020) |
| Natures Basket responsible disclosure | 2020, July  | Hard-coded root keys in source code exposed via public S3 bucket | N/A | N/A | [GotRoot! AWS root Account Takeover](https://web.archive.org/web/20200825004529/https://medium.com/@gchib/naturesbasket-aws-root-account-takeover-e4aa5c5e95e1) |
| Drizly  | 2020, July  | Inactive Github account compromised via reused password, granting AWS credential access in source code | N/A | RDS Instance with 2.5 users data exfiltrated | [FTC Takes Action Against Drizly and its CEO James Cory Rellas for Security Failures that Exposed Data of 2.5 Million Consumers](https://archive.ph/p21Vk) |
| Cryptomining AMI | 2020, August  | Windows 2008 Server Community AMI | N/A | Monero miner | [Cryptominer Found Embedded in AWS Community AMI](https://web.archive.org/web/20210625192906/https://www.darkreading.com/cloud/cryptominer-found-embedded-in-aws-community-ami/d/d-id/1338713/) |
| Animal Jam | 2020, November | Slack compromise exposes AWS credentials | N/A | User database | [Kids' gaming website Animal Jam breached](https://web.archive.org/web/20210122070047/https://www.theregister.com/2020/11/12/animal_jam_breached/) |
| Cisco | 2020,  December  | Former employee with AWS access 5 months post-resignation | N/A | Deleted \~450 EC2 instances | [Former Cisco engineer sentenced to prison](https://web.archive.org/web/20210304053727/https://www.zdnet.com/article/former-cisco-engineer-sentenced-to-prison-for-deleting-16k-webex-accounts/) |
| Juspay | 2021, January | Compromised old, unrecycled Amazon Web Services (AWS) access key | N/A | Masked card data, email IDs and phone numbers | [Data from August Breach of Amazon Partner Juspay Dumped Online](https://web.archive.org/web/20210127001214/https://threatpost.com/data-from-august-breach-of-amazon-partner-juspay-dumped-online/162740/) |
| 20/20 Eye Care Network and Hearing Care Network | 2021, January | Compromised credential | N/A | S3 buckets accessed then deleted | [20/20 Eye Care Network and Hearing Care Network notify 3,253,822 health plan members of breach that deleted contents of AWS buckets](https://www.databreaches.net/20-20-eye-care-network-and-hearing-care-network-notify-3253822-health-plan-members-of-breach-that-deleted-contents-of-aws-buckets/) |
| Sendtech | 2021, February | (Current or former employee) Compromised credentials | Created additional admin account | Accessed customer data in S3 | [PERSONAL DATA PROTECTION COMMISSION Case No. DP-2102-B7884](https://web.archive.org/web/20220923025502/https://www.pdpc.gov.sg/-/media/Files/PDPC/PDF-Files/Commissions-Decisions/Decision---Sendtech-Pte-Ltd---220721.ashx?la=en) |
| LogicGate | 2021, April | Compromised credentials | N/A | Backup files in S3 stolen | [Risk startup LogicGate confirms data breach](https://web.archive.org/web/20210519233848/https://techcrunch.com/2021/04/13/logicgate-risk-cloud-data-breach/) |
| Ubiquiti | 2021, April | Compromised credentials from IT employee Lastpass (alleged former employee insider threat) | N/A | root administrator access to all AWS accounts, extortion | [Ubiquiti All But Confirms Breach Response Iniquity](https://web.archive.org/web/20210731152054/https://krebsonsecurity.com/2021/04/ubiquiti-all-but-confirms-breach-response-iniquity/) |
| Uran Company | 2021, July | Compromised Drupal with API keys | N/A | Cryptomining | [Clear and Uncommon Story About Overcoming Issues With AWS](https://topdigital.agency/clear-and-uncommon-story-about-overcoming-issues-with-aws/) |
| redoorz.com | 2021, September | Access Key leaked via APK | N/A | Customer database stolen | [PERSONAL DATA PROTECTION COMMISSION Case No. DP-2009-B7057](https://web.archive.org/web/20211130202805/https://www.pdpc.gov.sg/-/media/Files/PDPC/PDF-Files/Commissions-Decisions/Decision---Commeasure-Pte-Ltd---15092021.pdf?la=en) |
| HPE Aruba | 2021, October | Unknown exposure of Access Key | N/A | Potential access to network telemetry and contact trace data | [Aruba Central Security Incident](https://www.arubanetworks.com/support-services/security-bulletins/central-incident-faq/) |
| Kaspersky | 2021, November | Compromised SES token from third party | N/A | Phishing attacks | [Kaspersky's stolen Amazon SES token used in Office 365 phishing](https://www.bleepingcomputer.com/news/security/kasperskys-stolen-amazon-ses-token-used-in-office-365-phishing/) |
| Onus | 2021, December | Log4Shell vulnerability in Cyclos server | AmazonS3FullAccess creds (and DB creds) in Cyclos config | 2 million ONUS users’ information including EKYC data, personal information, and password hash was leaked.  | [The attack on ONUS – A real-life case of the Log4Shell vulnerability](https://cystack.net/research/the-attack-on-onus-a-real-life-case-of-the-log4shell-vulnerability) |
| Flexbooker | 2021, December | Unknown | Unknown | 3.7M first and last names, email addresses, phone numbers, "encrypted" passwords | [Booking management platform FlexBooker leaks 3.7 million user records](https://therecord.media/booking-management-platform-flexbooker-leaks-3-7-million-user-records/) |
| npm | 2022, April | Third party OAuth token compromise granting private repository access, containing AWS keys | Unknown | 100k users data (from 2015) | [npm security update: Attack campaign using stolen OAuth tokens](https://github.blog/2022-05-26-npm-security-update-oauth-tokens/) |
| Uber | 2022, September | Contractor account compromise leading to AWS credential discovery on a shared drive | Unknown | N/A | [Uber - Security update](https://www.uber.com/newsroom/security-update/) |

## Vendor-reported AWS Customer Security Incident Case Studies

| Report | Date | Root Cause | Escalation Vector(s) | Impact | Link to details|
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| TeamTNT Worm| 2020, April | Misconfigured Docker & k8s platforms | Steals AWS credentials from \~/.aws/* | Cryptojacking for Monero | [Team TNT – The First Crypto-Mining Worm to Steal AWS Credentials](https://web.archive.org/web/20210607223609/https://www.cadosecurity.com/post/team-tnt-the-first-crypto-mining-worm-to-steal-aws-credentials/), [TeamTNT with new campaign aka “Chimaera”](https://cybersecurity.att.com/blogs/labs-research/teamtnt-with-new-campaign-aka-chimaera) |
| Expel case study 1 | 2020, April  | 8 IAM access keys compromised | Backdoored security groups | Command line access to EC2 instances | [Finding evil in AWS: A key pair to remember](https://web.archive.org/web/20210226132628/https://expel.io/blog/finding-evil-in-aws/) |
| Expel case study 2 | 2020, July  | Root IAM user access keycompromised | SSH keys generated for EC2 instances  | Cryptojacking | [Behind the scenes in the Expel SOC: Alert-to-fix in AWS](https://web.archive.org/web/20210128055101/https://expel.io/blog/behind-the-scenes-expel-soc-alert-aws/) |
| Mandiant: Insider Threat Scenario | 2020, September | Fired employee uses credentials | Access CI/CD server, create a new user, steal credentials | Deleted production databases | [Cloud Breaches: Case Studies, Best Practices, and Pitfalls](https://web.archive.org/web/20201103091354/https://www.youtube.com/watch?v=rtEjI_5TPdw&feature=youtu.be/) |
| Expel case study 3 | 2022, April | Credentials in publicly available code repository | AttachUserPolicy used for privesc | Cryptomining (prevented) | [Incident report: From CLI to console, chasing an attacker in AWS](https://expel.com/blog/incident-report-from-cli-to-console-chasing-an-attacker-in-aws/) |
| Palo Alto Unit 42 | 2022, December | Code execution in Lambda context | Exfiltrate credentials from envvars | SES abuse for phishing | [Compromised Cloud Compute Credentials: Case Studies From the Wild](https://unit42.paloaltonetworks.com/compromised-cloud-compute-credentials/) |
| Permiso case study 1 | 2022, June | Gitlab vulnerability (CVE-2021-22205) | Credentials on the system found, used to create a backupuser | Cryptomining | [Anatomy of an Attack: Exposed keys to Crypto Mining](https://web.archive.org/web/20220629061640/https://permiso.io/blog/s/anatomy-of-attack-exposed-keys-to-crypto-mining/) |

## Catalog of AWS Threat Actors

| Name | Vectors | Reports |
| ------------- | ------------- | ------------- |
| 8220 Gang | Exploit outdated and misconfigured software | [JupiterOne - 8220 Gang Cloud Botnet Targets Misconfigured Cloud Workloads](https://www.sentinelone.com/blog/8220-gang-cloud-botnet-targets-misconfigured-cloud-workloads/) |
| AndroxGh0st / Xcatze  | Exposed Laravel .env configs, use compromise for SES spam or malicious email  | [Lacework Labs - AndroxGh0st: the python malware exploiting your AWS keys](https://www.lacework.com/blog/androxghost-the-python-malware-exploiting-your-aws-keys/) |
| Cloud Snooper | Rootkit | [Sophos - Cloud Snooper Attack Bypasses AWS Security Measures](https://www.sophos.com/en-us/medialibrary/PDFs/technical-papers/sophoslabs-cloud-snooper-report.pdf) |
| Cosmic Wolf | Credential compromise | [CrowdStrike - 2022 Global Threat Report](https://irp.cdn-website.com/5d9b1ea1/files/uploaded/Report2022GTR.pdf) |
| Demonia | Lambda Malware | [Cado Discovers Denonia: The First Malware Specifically Targeting Lambda](https://www.cadosecurity.com/cado-discovers-denonia-the-first-malware-specifically-targeting-lambda/) |
| Kinsing | Malware| [CyberArk - Kinsing: The Malware with Two Faces](https://www.cyberark.com/resources/threat-research-blog/kinsing-the-malware-with-two-faces) |
| LAPSUS$ / DEV-0537 | phone-based social engineering; SIM-swapping to facilitate account takeover; accessing personal email accounts of employees at target organizations; paying employees, suppliers, or business partners of target organizations for access to credentials and multifactor authentication (MFA) approval | [Microsoft - DEV-0537 criminal actor targeting organizations for data exfiltration and destruction](https://www.microsoft.com/en-us/security/blog/2022/03/22/dev-0537-criminal-actor-targeting-organizations-for-data-exfiltration-and-destruction/) |
| Rocke | Targeting known CVEs | [Cisco Talos -  Rocke: The Champion of Monero Miners ](https://blog.talosintelligence.com/2018/08/rocke-champion-of-monero-miners.html) |
| TeamTNT | Exploit misconfigured docker and k8s | [MITRE ATT&CK -  TeamTNT](https://attack.mitre.org/groups/G0139/) |
| UNC2903 | SSRF (targeting known CVEs) | [Mandiant - Old Services, New Tricks: Cloud Metadata Abuse by UNC2903](https://www.mandiant.com/resources/blog/cloud-metadata-abuse-unc2903) |
| Watchdog | Exploit misconfigured docker and k8s | [TeamTNT Returns – or Does It?](https://www.trendmicro.com/en_us/research/22/j/teamtnt-returns-or-does-it.html) |

## "State of the Cloud" Report Incident Takeaways

| Report | Takeaways | 
| ------------- | ------------- | 
| Palo Alto Unit 42: [Cloud Threat Report H2 2020](https://falksangdata.no/wp-content/uploads/2021/04/unit-42-cloud-threat-report-2h-2020.pdf) | Unit 42 research shows that cryptojacking affects at least 23% of organizations globally that maintain cloud infrastructure |
| Expel: [Q1 2022 Threat Report](https://expel.com/wp-content/uploads/2022/05/Expel-QTR-051822.pdf) | Misconfigurations and exposed long-term credentials in Amazon Web Services (AWS) and Google Cloud Platform (GCP) accounted for 3% of incidents<br />These incidents break down into two categories:<br />1. Admins accidentally setting AWS S3 Buckets to Public<br />2. Threat actors gaining access to exposed long-lived credentials in AWS and GCP, which resulted in unauthorized access |
| Fugue: [The State of Cloud Security 2021](https://f.hubspotusercontent20.net/hubfs/4846674/Resources%20Content/State_of_Cloud_Security_2021.pdf) | N/A |
| IDC for Ermetic: [State of Cloud Security 2021](https://www.vpngids.nl/wp-content/uploads/ermetic-idc-survey-report-state-of-cloud-security-2021.pdf) | Most organizations (63%) confirmed that their sensitive data has been exposed in the cloud |
| Snyk: [State of Cloud Native Application Security 2021](https://go.snyk.io/rs/677-THP-415/images/State%20of%20CNAS.pdf) | Over 56% experienced a misconfiguration or known unpatched vulnerability incident involving their cloud native applications |
| GCP: [November 2021 Cloud Threat Intelligence report](https://services.google.com/fh/files/misc/gcat-threathorizons-full-nov2021.pdf) | Of 50 recently compromised GCP instances, 86% of the compromised Google Cloud instances were used to perform cryptocurrency mining |
| AWS: [2022 re:Inforce session on ransomware](https://www.firemon.com/what-you-need-to-know-about-ransomware-in-aws) h/t [Rich Mogull](https://twitter.com/rmogull)  | ransomware is a common problem for AWS customers, stemming from two common exploit vectors:<br />A traditional ransomware attack against instances in AWS. The attacker compromises an instance (often via phishing a user/admin, not always direct compromise), then installs their malware to encrypt the data and spread to other reachable instances. This is really no different than ransomware in a data center since it doesn’t involve anything cloud-specific.<br />The attacker copies data out of an S3 bucket and then deletes the original data. This is the most commonly seen cloud native ransomware on AWS.| 
| CrowdStrike: [2022 Global Threat Report](https://go.crowdstrike.com/rs/281-OBQ-266/images/Report2022GTR.pdf) | Cloud-related threats are particularly likely to become more prevalent and to evolve, given that targeted intrusion adversaries are expected to continue prioritizing targets that provide direct access to large consolidated stores of high-value data |
| CrowdStrike: [Protectors of the Cloud eBook](https://go.crowdstrike.com/rs/281-OBQ-266/images/eBookProtectorsoftheCloudEng.pdf) | CrowdStrike continues to see adversary activity in three particular areas concerning the cloud:<br />Neglected cloud infrastructure that is slated for retirement yet still contains sensitive data<br />A lack of outbound restrictions and workload protection to exfiltrate your data<br />Adversaries leveraging common cloud services to obfuscate malicious activity |
| Datadog: [State of AWS Security 2022](https://www.datadoghq.com/state-of-aws-security/) | N/A |
| ENISA [Threat Landscape 2022](https://www.enisa.europa.eu/topics/cyber-threats/threats-and-trends) | Cybercriminals target cloud services mostly in the following ways. \n * Exploiting cloud vulnerabilities: virtualisation infrastructure has been increasingly targeted (e.g. VMWare vSphere and ESXi platforms) by cybercriminals and especially by ransomware groups.<br />• Using cloud services for hosting their infrastructure: cybercriminals take advantage of the highly scalable and reliable cloud infrastructure and use legitimate cloud services to bypass security controls by blending into normal network traffic.<br />• Targeting cloud credentials: cybercriminals use social engineering attacks to harvest credentials for cloud services (e.g. Microsoft Office 365, Okta, etc.).<br />• Exploiting misconfigured image containers cybercriminals increasingly target poorly configured Docker containers and Kubernetes clusters.<br />• Targeting cloud instances for cryptomining (e.g. TeamTNT group): security researchers have identified a cloud-focused toolset from the TeamTNT group.<br />• Targeting cloud infrastructure (e.g. Azure AD), cloud application programming interfaces (APIs), and cloud-hosted backups by ransomware groups to infiltrate cloud environments and increase impact. |
| Fidelis: [2022 AWS Cloud Security Report](https://connect.fidelissecurity.com/rs/884-ZRZ-648/images/2022-AWS-Cloud-Security-Report.pdf) | For the 31% of organizations that experienced a security incident in the cloud, misconfiguration was the leading cause (28%), followed by inappropriately shared data (17%) and account compromise (15%). Exploited vulnerabilities account for 13% of incidents |
| GCP: [July 2022 Cloud Threat Intelligence report](https://services.google.com/fh/files/blogs/gcat_threathorizons_full_july2022.pdf) | the most common attack vectors used across cloud providers was brute force of cloud services that are exposed to the internet and have a weak or default password ... close behind brute force attacks was the exploitation of vulnerable software | 
| IBM: [Cost of a Data Breach 2022](https://ermetic.com/blog/cloud/ibm-cost-of-a-data-breach-2022-highlights-for-cloud-security-professionals/)| 45% of Breaches Were Cloud-Based. Stolen or compromised credentials were the number one attack vector in the past two years. Following credentials, the next most common initial attack vectors were:<br />Second place: Phishing - 16% of breaches, $4.91M average costs<br />Third place: Cloud misconfigurations - 15% of breaches, $4.14M average costs<br />Fourth place: Third-party software vulnerability - 13% of breaches, $4.55M average costs|<br /> |
| (ISC)2: [2022 Cloud Security Report](https://www.isc2.org/-/media/5E48A83950264AB1B265B1F073F5C9FB.ashx) | We asked cybersecurity professionals about the cloud security threats that most concern them. Misconfiguration of cloud security remains the biggest cloud security risk according to 62% of cybersecurity professionals in our survey. This is followed by insecure interfaces/APIs (54%), exfiltration of sensitive data (51%) and unauthorized access (50%). |
| Orca: [2022 State of Public Cloud Security](https://orca.security/wp-content/uploads/2022/09/Orca-Securitys-2022-State-of-Public-Cloud-Security-Report.pdf) | N/A |
| Palo Alto Unit 42: [Incident Response Threat Report 2022](https://www.paloaltonetworks.com/unit42/2022-incident-response-report) |  Nearly 65% of known cloud security incidents were due to misconfigurations. The main culprit? IAM configuration. |
| riskrecon: [Cloud Risk Surface Report](https://cdn2.hubspot.net/hubfs/2477095/Cloud%20Risk%20Surface%20Report%202019/RR_Cloud-Report_Web_final%20(1).pdf) | N/A |
| Snyk: [State of cloud security 2022](https://resources.snyk.io/state-of-cloud-security) | 80% of organizations experienced a serious cloud security incident during the last year - 33% breach, 26% leak, 27% intrusion, 23% cryptomining |
| Wiz: [2022 cloud security threats report](https://www.datocms-assets.com/75231/1659965344-6223652ebbad288bbdfa046e_2022-cloud-security-threats.pdf) | Effectively, unintentionally exposed databases are one of the most common sources of data breaches |


## Disclosure (responsible, coordinated, public)

| Date | Vulnerability | Reference |
| ------------- | ------------- | ------------- |
| 2021, Feb | Credentials leaked in repository | [Access to Glassdoor's Infra (AWS) and BitBucket account through leaked repo](https://hackerone.com/reports/801531) | 
| 2021, Apr | Ssubdomain takeover, deleted EC2 instance  | [Subdomain takeover of www2.growasyouplan.com](https://hackerone.com/reports/1179193) |
| 2021, Oct | AWS Creds hardcoded in MSI | [Hardcoded AWS credentials in ███████.msi](https://hackerone.com/reports/1368690) |
| 2021, Nov | Potential subdomain takeover, dangling CNAME  | [Possible Domain Takeover on AWS Instance](https://hackerone.com/reports/1390782) |
| 2021, Nov | Subdomain takeover, deleted S3 bucket  | [Subdomain takeover of images.crossinstall.com](https://hackerone.com/reports/1406335) |
| 2021, Dec | Account takeover via Cognito user email change | [Flickr Account Takeover using AWS Cognito API](https://hackerone.com/reports/1342088) |
| 2022, Oct | Subdomain takeover, deleted S3 bucket | [Subdomain takeover at http://test.www.midigator.com](https://hackerone.com/reports/1718371) |
| 2022, Nov | AWS Creds in string constant in public python package | [Infosys leaked FullAdminAccess AWS keys on PyPi for over a year](https://tomforb.es/infosys-leaked-fulladminaccess-aws-keys-on-pypi-for-over-a-year/) |
| 2022, Jan | NoSQL-Injection discloses discloses S3 File Upload URLs | [NoSQL-Injection discloses S3 File Upload URLs](https://hackerone.com/reports/1458020) |

### Catalog of AWS Exploits via SSRF

[Server-side request forgery](https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/) is a class of attack that is not cloud or AWS specific. However, the existence of cloud metadata services, such as [IMDS](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) in AWS, have historically allowed for a substantial straightforward impact when SSRF is achieved on a cloud hosted application. For that reason, we include this list of SSRF attacks against AWS environments.

* [Bypassing SSRF Protection to Exfiltrate AWS Metadata from LarkSuite](https://sirleeroyjenkins.medium.com/bypassing-ssrf-protection-to-exfiltrate-aws-metadata-from-larksuite-bf99a3599462)
* [ESEA Server-Side Request Forgery and Querying AWS Meta Data](https://buer.haus/2016/04/18/esea-server-side-request-forgery-and-querying-aws-meta-data/)
* [A pair of Plotly bugs: Stored XSS and AWS Metadata SSRF](https://web.archive.org/web/20170527104436/https://ysx.me.uk/a-pair-of-plotly-bugs-stored-xss-and-aws-metadata-ssrf/)
* [Dropbox - Full Response SSRF via Google Drive](https://github.com/httpvoid/writeups/blob/main/Hacking-Google-Drive-Integrations.md#dropboxs-full-read-ssrf)
* [Mandiant - Old Services, New Tricks: Cloud Metadata Abuse by UNC2903](https://www.mandiant.com/resources/blog/cloud-metadata-abuse-unc2903)
* [SSRF leads to access AWS metadata.](https://infosecwriteups.com/ssrf-leads-to-access-aws-metadata-21952c220aeb)
* [Escalating SSRF to RCE](https://sanderwind.medium.com/escalating-ssrf-to-rce-7c0147371c40)
* [SSRF Leads To AWS Metadata Exposure](https://systemweakness.com/ssrf-leads-to-aws-metadata-exposure-8b4c3424755b)
* [How I discovered an SSRF leading to AWS Metadata Leakage](https://techkranti.com/ssrf-aws-metadata-leakage/)
* [Exploitation of an SSRF vulnerability against EC2 IMDSv2](https://www.yassineaboukir.com/blog/exploitation-of-an-SSRF-vulnerability-against-EC2-IMDSv2/)
* [Mozilla - AWS SSRF to Pull AWS Metadata and Keys](https://bugzilla.mozilla.org/show_bug.cgi?id=1550366)
* [Full read SSRF in www.evernote.com that can leak aws metadata and local file inclusion](https://hackerone.com/reports/1189367) |
* [SSRF allows reading AWS EC2 metadata using "readapi" variable in Streamlabs Cloudbot](https://hackerone.com/reports/1108418)
* [Server Side Request Forgery (SSRF) at app.hellosign.com leads to AWS private keys disclosure](https://hackerone.com/reports/923132)
* [SSRF via Office file thumbnails](https://hackerone.com/reports/671935)

For more about this attack, please see [Hacking the Cloud - Steal EC2 Metadata Credentials via SSRF](https://hackingthe.cloud/aws/exploitation/ec2-metadata-ssrf/)


## Talks

The initial data was collected for a talk at BSidesCT 2020: _Learning from AWS (Customer) Security Incidents_  [slides here](https://speakerdeck.com/ramimac/learning-from-aws-customer-security-incidents)
A follow up talk was given at OWASP DevSlop in May 2022. [video](https://www.youtube.com/watch?v=JBUgAXvcObU), [slides](https://speakerdeck.com/ramimac/learning-from-aws-customer-security-incidents-2022)

<a class="anchor" id="1"></a> [Postmortem Culture: Learning from Failure](https://sre.google/sre-book/postmortem-culture/)

<a class="anchor" id="2"></a> _Note_: There have been numerous identified incidents of Magecart exploiting S3 Global Write - in [one review targeting "well over 17,000 domains"](https://web.archive.org/web/20210620145033/https://www.riskiq.com/blog/labs/magecart-amazon-s3-buckets/)
