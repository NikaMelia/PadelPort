# Web security to OSCP: a 12-month study plan

Written 30 Sep 2026 for a working developer in Georgia studying about 15 hours a week alongside freelance work. Costs in USD. Dates assume a start on 6 Oct 2026; shift everything if you start later.

## Ground rules

- **Only ever test what you are authorised to test.** Training platforms, your own machines, and clients who signed a scope. Nothing else, ever. Unauthorised access is a criminal offence in Georgia.
- **Rhythm:** three weekday evenings of 2 hours plus one weekend block of 6 to 8 hours. Protect the weekend block; it is where labs actually get finished.
- **Notes from day one.** Keep a personal wiki (Obsidian or similar) with one page per technique: what it is, how to find it, how to exploit it, how to fix it, and the exact commands. This becomes your exam cheat sheet and, later, your report templates.
- **Two decision gates.** Week 4 and week 12. If you are not enjoying it at a gate, stop. The plan is designed so stopping early costs almost nothing.

## Phase 0: setup (week 0, one weekend, cost 0)

- Install a Kali Linux virtual machine (VirtualBox or VMware) with snapshots.
- Install Burp Suite Community and configure the browser proxy.
- Create accounts: PortSwigger Web Security Academy, TryHackMe, Hack The Box.
- Set up your notes wiki with a template page.
- Read OWASP Top 10 (2021) once, just to learn the vocabulary.

## Phase 1: the free month (weeks 1 to 4, cost 0)

Goal: finish the core Web Security Academy topics and decide whether you like this.

| Week | Topics (Academy learning paths and labs) |
|---|---|
| 1 | SQL injection, cross-site scripting (all apprentice and practitioner labs) |
| 2 | Authentication, path traversal, OS command injection, business logic |
| 3 | Access control, CSRF, information disclosure, file upload |
| 4 | SSRF, XXE, clickjacking, CORS, race conditions |

Weekly output: every lab solved is a note page. By week 4 you should have 60 to 80 labs done.

**Gate 1 (end of week 4).** Ask yourself one question: did you do labs on a night you did not have to? If yes, continue. If you had to force every session, stop here and put the hours into freelance development instead.

## Phase 2: Burp Suite Certified Practitioner (weeks 5 to 12, cost about 600)

Buy Burp Suite Professional (499 per year) at the start of week 5. You need it for the exam and for any real client work.

| Week | Focus |
|---|---|
| 5 | Advanced topics: insecure deserialization, server-side template injection, JWT attacks |
| 6 | OAuth, prototype pollution, web cache poisoning, HTTP request smuggling |
| 7 | HTTP host header attacks, GraphQL, NoSQL injection, API testing |
| 8 | Finish every remaining practitioner lab; start the expert labs on your weak topics |
| 9 | Mystery labs: 10 a week with no topic hint, timed at 30 minutes each |
| 10 | PortSwigger practice exam, twice, under exam conditions (4 hours) |
| 11 | Review failures; redo the labs behind every miss; write one full report for a practice app |
| 12 | Sit the BSCP exam (99). It is two apps, three vulnerabilities each, four hours |

Selling starts here, in parallel:
- Week 6: publish two short technical posts in English on things you learned that apply to Georgian systems, such as testing rs.ge integrations or Keepz payment flows for common web flaws.
- Week 8: offer a "security review" add-on to every freelance development client you have. Price it low the first two times.
- Week 12: with the certificate, approach five small fintechs or crypto firms and five software agencies in Tbilisi with a fixed-price web application test.

**Gate 2 (week 12).** Passed BSCP and had at least one conversation about paid work? Continue to OSCP. Failed BSCP? Retake in week 14, it is only 99. No interest in paid work at all? Stay a developer who does security reviews and skip OSCP.

## Phase 3: infrastructure foundations (weeks 13 to 16, cost about 60)

OSCP is mostly networks, Linux, Windows and Active Directory, which web work does not teach.

| Week | Focus |
|---|---|
| 13 | TryHackMe "Jr Penetration Tester" path: networking, Nmap, enumeration, Linux fundamentals |
| 14 | Linux privilege escalation (TryHackMe room plus GTFOBins), Windows fundamentals |
| 15 | Windows privilege escalation, basic Active Directory concepts, Metasploit basics |
| 16 | Hack The Box: 6 to 8 easy retired boxes from the TJ Null OSCP list, write a note per box |

## Phase 4: PEN-200 (weeks 17 to 40, cost 1,499 to 1,749)

Buy the PEN-200 Course and Cert bundle (90 days of lab) at week 17, or Learn One (2,749) if you want a full year and two attempts. Learn One is the safer buy given the pass rate.

| Weeks | Focus |
|---|---|
| 17 to 22 | Read every PEN-200 module and complete every exercise. Do not skip the boring ones; the exam bonus points come from exercises |
| 23 to 28 | Course challenge labs: Medtech, Relia, Skylark. Finish all three. This is where Active Directory clicks |
| 29 to 34 | Proving Grounds Practice (19 per month): 40 to 60 boxes from the TJ Null and Lain Kusanagi lists, at least 20 Windows, at least 10 Active Directory related |
| 35 to 38 | OSCP A, B and C challenge sets, each under exam conditions with a full report written afterwards |
| 39 to 40 | Timing drills: three boxes in six hours, then a full 24-hour mock on a weekend |

Targets by week 40: 100 or more boxes rooted in total, a report template you have used at least four times, and a personal cheat sheet you can navigate without searching.

## Phase 5: exam (weeks 41 to 48, cost 0 to 249)

- Week 41: book the exam three to four weeks out.
- Weeks 42 to 44: light revision, redo your five weakest boxes, sleep properly.
- Week 45: sit the exam. Sleep at least 4 hours during the 24 hours. Screenshot everything as you go.
- Week 46: write and submit the report within 24 hours.
- Weeks 47 to 48: if you failed, book the retake (249) for six to eight weeks later and spend the gap on the machine types that beat you.

## Costs and timeline

| When | Item | Cost |
|---|---|---|
| Week 5 | Burp Suite Professional | 499 |
| Week 12 | BSCP exam | 99 |
| Weeks 13 to 16 | TryHackMe premium, 2 months | about 30 |
| Weeks 17 to 40 | PEN-200 bundle or Learn One | 1,499 to 2,749 |
| Weeks 29 to 40 | Proving Grounds Practice, 3 months | about 60 |
| Week 47 | Retake, if needed | 249 |
| Total | | about 2,200 to 3,700 |

Money can start coming in from week 8 (security reviews) and week 12 (web tests), which is before the largest cost.

## Milestones

- Week 4: 60 to 80 Academy labs, decision made.
- Week 12: BSCP passed, first paid or trial security review done.
- Week 16: 8 boxes rooted, comfortable in a Linux shell and Nmap.
- Week 28: all three PEN-200 challenge labs complete.
- Week 40: 100 boxes, mock exam done.
- Week 45 to 48: OSCP.
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
