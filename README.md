## Background

Security is an exercise in managing risk. Reviewing the common root causes of security incidents is an effective way to guide prioritized remediation efforts. 

This repository seeks to index all publicly disclosed AWS customer security incidents with a known root cause. It will exclude incidents involving exposed data stores (e.g S3 bucket leaks, exposed managed or hosted databases). Those incidents are already well understood, and examples can be found cataloged in places like https://github.com/nagwww/s3-leaks, https://www.upguard.com/breaches and Corey Quinn's [LWIAWS](https://www.lastweekinaws.com) S3 Bucket Negligence Award.


The intial data was collected for a talk at BSidesCT 2020: _Learning from AWS (Customer) Security Incidents_
You can find the slides [here](https://speakerdeck.com/ramimac/learning-from-aws-customer-security-incidents)

### A Note on Blameless Postmortems

This repository is in no way intended as a criticism of the listed companies. In the spirit of blameless postmortems [<sup>1</sup>](#1), our goal is to learn from incidents without an atmosphere of blame. 

## Statistics

## Catalog of AWS Customer Security Incidents

A repository of breaches of AWS customers

| Name  | Date | Root Cause | Escalation Vector(s) | Impact | Link to details
| ------------- | ------------- | ------------- | ------------- |
| Capital One  | 2019, April  | "Misconfigured WAF" that allowed for a SSRF attack  | Over-privileged EC2 Role |  [A Technical Analysis of the Capital One Cloud Misconfiguration Breach](https://www.fugue.co/blog/a-technical-analysis-of-the-capital-one-cloud-misconfiguration-breach)  |
| Code Spaces  | 2014, June  | AWS Console Credentials (Phishing?) | Attacker created additional accounts/access keys | Wiped S3 buckets, EC2 instances, AMIs, EBS snapshots | [Hacker puts code spaces out of business](https://threatpost.com/hacker-puts-hosting-service-code-spaces-out-of-business/106761/)  |
| DNC Hack by the GRU  | 2016, June  | Unknown, test clusters breached | EC2 Snapshots copied to attacker AWS accounts | Tableau and Vertica Queries | [DEMOCRATIC NATIONAL COMMITTEE v. THE RUSSIAN FEDERATION](https://threatpost.com/hacker-puts-hosting-service-code-spaces-out-of-business/106761/)  |
| DataDog  | 2016, July  | CI/CD AWS access key and SSH private key leaked | Attacker attempted to pivot with 
customer credentials | 3 EC2 instances and subset of S3 buckets | [2016-07-08 Security Notice](https://web.archive.org/web/20201128071102/https://www.datadoghq.com/blog/2016-07-08-security-notice/)  |
| Uber | 2016, October  | Private Github Repo with AWS credentials | N/A | Names and driver’s license numbers of 600k drivers, PII of 57 million users| [Uber concealed cyberattack ...](https://web.archive.org/web/20210824171652/https://www.bloomberg.com/news/articles/2017-11-21/uber-concealed-cyberattack-that-exposed-57-million-people-s-data) |
| OneLogin | 2017, May  | AWS keys | Created EC2 instances | Accessed database tables (with encrypted data) | [May 31, 2017 Security Incident](https://web.archive.org/web/20210620180614/https://www.onelogin.com/blog/may-31-2017-security-incident) |
| Politifact | 2017, October  | "Misconfigured cloud computing server" | N/A | Coinhive cryptojacking | [Hackers have turned Politifact’s website into a trap for your PC](https://web.archive.org/web/20200806102838/https://www.washingtonpost.com/news/the-switch/wp/2017/10/13/hackers-have-turned-politifacts-website-into-a-trap-for-your-pc/) |
| DXC Technologies | 2017, November  | Private AWS key exposed via Github | 244 EC2 instance started | Cryptomining | [DXC spills AWS private keys on public GitHub](https://web.archive.org/web/20210228215919/https://www.theregister.com/2017/11/14/dxc_github_aws_keys_leaked/) |
| LA Times  | 2018, February  | S3 global write access | N/A | Coinhive cryptojacking added to homicide.latimes.com](https://web.archive.org/web/20210413201832/https://www.tripwire.com/state-of-security/security-data-protection/la-times-website-cryptojacking-attack/) |
| Tesla | 2018, February  | Globally exposed Kubernetes console, Pod with AWS credentials | N/A | Cryptojacking | [Imperva Security Update](https://web.archive.org/web/20210620143023/https://www.imperva.com/blog/ceoblog//) |
| Imperva | 2019, October  | “Internal compute instance” globally accessible, “Contained” AWS API key | N/A | RDS snapshot stolen | [Hacker puts code spaces out of business](https://www.bloomberg.com/news/articles/2017-11-21/uber-concealed-cyberattack-that-exposed-57-million-people-s-data) |
| Cisco | 2020,  December  | Former employee with AWS access 5 months post-resignation | N/A | Deleted \~450 EC2 instances | [Former Cisco engineer sentenced to prison](https://web.archive.org/web/20210304053727/https://www.zdnet.com/article/former-cisco-engineer-sentenced-to-prison-for-deleting-16k-webex-accounts/) |
| JW Player | 2019, September  | Weave Scope (publicly exposed), RCE by design | N/A | Cryptojacking | [ Malindo Air: Data Breach Was Inside Job](https://web.archive.org/web/20210828044334/https://medium.com/jw-player-engineering/how-a-cryptocurrency-miner-made-its-way-onto-our-internal-kubernetes-clusters-9b09c4704205) |
| Twilio | 2020, July  |S3 global write access | N/A | Magecart[<sup>2</sup>](#2) | [Incident Report: TaskRouter JS SDK Security Incident](https://web.archive.org/web/20210813010417/https://www.twilio.com/blog/incident-report-taskrouter-js-sdk-july-2020) |
| Expel case study 1 | 2020, July  | Root IAM user access keycompromised | SSH keys generated for EC2 instances  | Cryptojacking | [Behind the scenes in the Expel SOC: Alert-to-fix in AWS](https://web.archive.org/web/20210128055101/https://expel.io/blog/behind-the-scenes-expel-soc-alert-aws/) |
| Expel case study 2 | 2020, April  | 8 IAM access keys compromised | Backdoored security groups | Command line access to EC2 instances | [Finding evil in AWS: A key pair to remember](https://web.archive.org/web/20210226132628/https://expel.io/blog/finding-evil-in-aws/) |
| TeamTNT Worm| 2020, April  | Misconfigured Docker & k8s platforms | Steals AWS credentials from \~/.aws/* | Cryptojacking for Monero | [Team TNT – The First Crypto-Mining Worm to Steal AWS Credentials](https://web.archive.org/web/20210607223609/https://www.cadosecurity.com/post/team-tnt-the-first-crypto-mining-worm-to-steal-aws-credentials/) |
| Cryptomining AMI | 2020, August  | Windows 2008 Server Community AMI | N/A | Monero miner | [Cryptominer Found Embedded in AWS Community AMI](https://web.archive.org/web/20210625192906/https://www.darkreading.com/cloud/cryptominer-found-embedded-in-aws-community-ami/d/d-id/1338713/) |
| Mandiant: Insider Threat Scenario | 2020, September | Fired employee uses credentials | Access CI/CD server, create a new user, steal credentials | Deleted production databases | [Cloud Breaches: Case Studies, Best Practices, and Pitfalls](https://web.archive.org/web/20201103091354/https://www.youtube.com/watch?v=rtEjI_5TPdw&feature=youtu.be/) |
| LogicGate | 2021, April | Compromised credentials | N/A | Backup files in S3 stolen | [Risk startup LogicGate confirms data breach](https://web.archive.org/web/20210519233848/https://techcrunch.com/2021/04/13/logicgate-risk-cloud-data-breach/) |
| Ubiquiti | 2021, April | Compromised credentials from IT employee Lastpass (alleged former employee insider threat) | N/A | root administrator access to all AWS accounts, extortion | [Ubiquiti All But Confirms Breach Response Iniquity](https://web.archive.org/web/20210731152054/https://krebsonsecurity.com/2021/04/ubiquiti-all-but-confirms-breach-response-iniquity/) |
| Juspay | 2021, January | Compromised old, unrecycled Amazon Web Services (AWS) access key | N/A | Masked card data, email IDs and phone numbers | [Data from August Breach of Amazon Partner Juspay Dumped Online](https://web.archive.org/web/20210127001214/https://threatpost.com/data-from-august-breach-of-amazon-partner-juspay-dumped-online/162740/) |
| Animal Jam | 2020, November | Slack comprise exposes AWS credentials | N/A | User database | [Kids' gaming website Animal Jam breached](https://web.archive.org/web/20210122070047/https://www.theregister.com/2020/11/12/animal_jam_breached/) |


## TKTK https://www.databreaches.net/20-20-eye-care-network-and-hearing-care-network-notify-3253822-health-plan-members-of-breach-that-deleted-contents-of-aws-buckets/


<a class="anchor" id="1"></a> [Postmortem Culture: Learning from Failure](https://sre.google/sre-book/postmortem-culture/)
<a class="anchor" id="2"></a> _Note_: There have been numerous identified incidents of Magecart exploiting S3 Global Write - in [one review targeting "well over 17,000 domains"](https://web.archive.org/web/20210620145033/https://www.riskiq.com/blog/labs/magecart-amazon-s3-buckets/)