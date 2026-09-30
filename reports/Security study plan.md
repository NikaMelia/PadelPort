# Web security to OSCP: a 15-month study plan

Written 30 Sep 2026, revised the same day for someone who has written code but has little grounding in how the web, networks and operating systems work, studying about 15 hours a week. Costs in USD. Dates assume a start on 6 Oct 2026; shift everything if you start later.

## Ground rules

- **Only ever test what you are authorised to test.** Training platforms, your own machines, and clients who signed a scope. Nothing else, ever. Unauthorised access is a criminal offence in Georgia.
- **Rhythm:** three weekday evenings of 2 hours plus one weekend block of 6 to 8 hours. Protect the weekend block; it is where labs actually get finished.
- **Notes from day one.** Keep a personal wiki (Obsidian or similar) with one page per technique: what it is, how to find it, how to exploit it, how to fix it, and the exact commands. This becomes your exam cheat sheet and, later, your report templates.
- **Three decision gates.** Week 8, week 13 and week 21. If you are not enjoying it at a gate, stop. The plan is designed so stopping early costs almost nothing.

## Phase A: foundations (weeks 1 to 8, cost 0 to 30)

Skip this only if you can already answer, without looking anything up: what happens between typing a URL and a page appearing; what a cookie and a session are; what a port is; how to list files, find text and change permissions in a Linux terminal; how a web app talks to its database. If any of those is fuzzy, do this phase. It is the difference between the later labs making sense and not.

| Week | Topic | Resource (free unless noted) | What you can do at the end |
|---|---|---|---|
| 1 | How the internet works: IP, DNS, HTTP, HTTPS, ports, clients and servers | TryHackMe "Pre Security" path, first half | Explain a request from browser to server and back |
| 2 | How a web app works: HTML, forms, cookies, sessions, login, APIs, databases | TryHackMe "Pre Security" second half; build a tiny login page with a database yourself | Draw the parts of a web app and where data lives |
| 3 | Linux command line | OverTheWire "Bandit" levels 0 to 20; TryHackMe "Linux Fundamentals" 1 to 3 | Navigate, search, read logs, manage permissions from a terminal |
| 4 | Networking in practice | Professor Messer Network+ videos, selected; TryHackMe "Network Fundamentals" | Read an Nmap scan and know what the open ports mean |
| 5 | Windows and operating system basics | TryHackMe "Windows Fundamentals" 1 to 3 | Users, permissions, services, registry at a basic level |
| 6 | Python for automation | Automate the Boring Stuff, chapters 1 to 12 | Write a 30-line script that makes HTTP requests and parses the reply |
| 7 | What cybersecurity is: attackers, defenders, the kill chain, common attacks, what a pentest report looks like | TryHackMe "Cyber Security 101" path; read two real public pentest reports (search "public pentest reports GitHub") | Explain to a friend what a penetration test is and is not |
| 8 | First hands-on: guided attack rooms | TryHackMe "Cyber Security 101" remainder, plus 3 guided easy rooms | Follow a walkthrough and understand every step |

TryHackMe premium (about 15 a month) speeds this phase up but is optional. Keep the same notes wiki from the start.

**Gate A (end of week 8).** Did you finish Bandit and the two TryHackMe paths, and did you find at least some of it interesting? If yes, continue. If it felt like homework you resented, stop here and put the time into building software instead. Either way you now understand how the systems you code for actually work, which makes you a better developer regardless.

## Phase 0: setup (week 9, one weekend, cost 0)

- Install a Kali Linux virtual machine (VirtualBox or VMware) with snapshots.
- Install Burp Suite Community and configure the browser proxy.
- Create accounts: PortSwigger Web Security Academy, TryHackMe, Hack The Box.
- Set up your notes wiki with a template page.
- Re-read OWASP Top 10 (2021); after Phase A it should now make sense.

## Phase 1: the free month (weeks 10 to 13, cost 0)

Goal: finish the core Web Security Academy topics and decide whether you like this.

| Week | Topics (Academy learning paths and labs) |
|---|---|
| 10 | SQL injection, cross-site scripting (all apprentice and practitioner labs) |
| 11 | Authentication, path traversal, OS command injection, business logic |
| 12 | Access control, CSRF, information disclosure, file upload |
| 13 | SSRF, XXE, clickjacking, CORS, race conditions |

Weekly output: every lab solved is a note page. By week 13 you should have 60 to 80 labs done.

**Gate 1 (end of week 13).** Ask yourself one question: did you do labs on a night you did not have to? If yes, continue. If you had to force every session, stop here and put the hours into freelance development instead.

## Phase 2: Burp Suite Certified Practitioner (weeks 14 to 21, cost about 600)

Buy Burp Suite Professional (499 per year) at the start of week 14. You need it for the exam and for any real client work.

| Week | Focus |
|---|---|
| 14 | Advanced topics: insecure deserialization, server-side template injection, JWT attacks |
| 15 | OAuth, prototype pollution, web cache poisoning, HTTP request smuggling |
| 16 | HTTP host header attacks, GraphQL, NoSQL injection, API testing |
| 17 | Finish every remaining practitioner lab; start the expert labs on your weak topics |
| 18 | Mystery labs: 10 a week with no topic hint, timed at 30 minutes each |
| 19 | PortSwigger practice exam, twice, under exam conditions (4 hours) |
| 20 | Review failures; redo the labs behind every miss; write one full report for a practice app |
| 21 | Sit the BSCP exam (99). It is two apps, three vulnerabilities each, four hours |

Selling starts here, in parallel:
- Week 15: publish two short technical posts in English on things you learned that apply to Georgian systems, such as testing rs.ge integrations or Keepz payment flows for common web flaws.
- Week 17: offer a "security review" add-on to every freelance development client you have. Price it low the first two times.
- Week 21: with the certificate, approach five small fintechs or crypto firms and five software agencies in Tbilisi with a fixed-price web application test.

**Gate 2 (week 21).** Passed BSCP and had at least one conversation about paid work? Continue to OSCP. Failed BSCP? Retake in week 23, it is only 99. No interest in paid work at all? Stay a developer who does security reviews and skip OSCP.

## Phase 3: infrastructure deepening (weeks 22 to 25, cost about 60)

OSCP is mostly networks, Linux, Windows and Active Directory, which web work does not teach.

| Week | Focus |
|---|---|
| 22 | TryHackMe "Jr Penetration Tester" path: networking, Nmap, enumeration, Linux fundamentals |
| 23 | Linux privilege escalation (TryHackMe room plus GTFOBins), Windows fundamentals |
| 24 | Windows privilege escalation, basic Active Directory concepts, Metasploit basics |
| 25 | Hack The Box: 6 to 8 easy retired boxes from the TJ Null OSCP list, write a note per box |

## Phase 4: PEN-200 (weeks 26 to 49, cost 1,499 to 1,749)

Buy the PEN-200 Course and Cert bundle (90 days of lab) at week 26, or Learn One (2,749) if you want a full year and two attempts. Learn One is the safer buy given the pass rate.

| Weeks | Focus |
|---|---|
| 26 to 31 | Read every PEN-200 module and complete every exercise. Do not skip the boring ones; the exam bonus points come from exercises |
| 32 to 37 | Course challenge labs: Medtech, Relia, Skylark. Finish all three. This is where Active Directory clicks |
| 38 to 43 | Proving Grounds Practice (19 per month): 40 to 60 boxes from the TJ Null and Lain Kusanagi lists, at least 20 Windows, at least 10 Active Directory related |
| 44 to 47 | OSCP A, B and C challenge sets, each under exam conditions with a full report written afterwards |
| 48 to 49 | Timing drills: three boxes in six hours, then a full 24-hour mock on a weekend |

Targets by week 49: 100 or more boxes rooted in total, a report template you have used at least four times, and a personal cheat sheet you can navigate without searching.

## Phase 5: exam (weeks 50 to 57, cost 0 to 249)

- Week 50: book the exam three to four weeks out.
- Weeks 51 to 53: light revision, redo your five weakest boxes, sleep properly.
- Week 54: sit the exam. Sleep at least 4 hours during the 24 hours. Screenshot everything as you go.
- Week 55: write and submit the report within 24 hours.
- Weeks 56 to 57: if you failed, book the retake (249) for six to eight weeks later and spend the gap on the machine types that beat you.

## Costs and timeline

| When | Item | Cost |
|---|---|---|
| Weeks 1 to 8 | TryHackMe premium, optional | 0 to 30 |
| Week 14 | Burp Suite Professional | 499 |
| Week 21 | BSCP exam | 99 |
| Weeks 22 to 25 | TryHackMe premium, 2 months | about 30 |
| Weeks 26 to 49 | PEN-200 bundle or Learn One | 1,499 to 2,749 |
| Weeks 38 to 49 | Proving Grounds Practice, 3 months | about 60 |
| Week 56 | Retake, if needed | 249 |
| Total | | about 2,200 to 3,700 |

Money can start coming in from week 17 (security reviews) and week 21 (web tests), which is before the largest cost.

## Milestones

- Week 8: foundations done, Bandit finished, decision made.
- Week 13: 60 to 80 Academy labs, second decision made.
- Week 21: BSCP passed, first paid or trial security review done.
- Week 25: 8 boxes rooted, comfortable in a Linux shell and Nmap.
- Week 37: all three PEN-200 challenge labs complete.
- Week 49: 100 boxes, mock exam done.
- Week 54 to 57: OSCP.
- After: register an LLC when a client requires it, and look at the Digital Governance Agency register once you have two or three tests behind you.

## Resources

- PortSwigger Web Security Academy (free): portswigger.net/web-security
- TryHackMe: tryhackme.com
- Hack The Box: hackthebox.com
- TJ Null OSCP-like box list: search "TJ Null OSCP list" for the current spreadsheet
- OffSec PEN-200: offsec.com/courses/pen-200
- Proving Grounds Practice: offsec.com/labs
- GTFOBins and LOLBAS for privilege escalation lookups
- OWASP Web Security Testing Guide for report structure
