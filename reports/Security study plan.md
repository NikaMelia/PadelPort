# Web security to OSCP: a 13 to 15 month study plan

Written 30 Sep 2026, revised the same day for a self-taught developer who builds and deploys web apps but has never had the fundamentals checked, studying about 15 hours a week alongside paid work. Costs in USD. Dates assume a start on 6 Oct 2026; shift everything if you start later.

## Ground rules

- **Only ever test what you are authorised to test.** Training platforms, your own machines, and clients who signed a scope. Nothing else, ever. Unauthorised access is a criminal offence in Georgia.
- **Rhythm:** three weekday evenings of 2 hours plus one weekend block of 6 to 8 hours. Protect the weekend block; it is where labs actually get finished.
- **Notes from day one.** Keep a personal wiki (Obsidian or similar) with one page per technique: what it is, how to find it, how to exploit it, how to fix it, and the exact commands. This becomes your exam cheat sheet and, later, your report templates.
- **Three decision gates.** Week 8, week 13 and week 21 (after the four-week shift noted in Phase A). If you are not enjoying it at a gate, stop. The plan is designed so stopping early costs almost nothing.

## Phase A: gap check and gap fill (weeks 1 to 8 as graded, cost 0 to 35)

The self-test was taken on 30 Sep 2026 and showed gaps in 8 or 9 of the 12 rows (Linux, networking, TLS, Windows, CSRF and SameSite, sessions, SQL injection, deployment unanswered, plus three rows not attempted). So this phase runs the full eight weeks. The day-by-day version is in `reports/Gap fill plan.md`; the table below is kept as the checklist to retest against in week 8.

### Week 1: the self-test

Do each task without looking anything up. Be honest; nobody is watching. A row is a pass only if you can do the whole thing.

| Area | Task | If failed, fill with |
|---|---|---|
| HTTP | Write out, from memory, a raw HTTP request and response including method, path, Host, Cookie, Content-Type and status line. Explain the difference between GET, POST, PUT, PATCH, DELETE and what idempotent means | MDN "HTTP overview" and "HTTP headers"; then read 20 raw requests in Burp for a site you own |
| Web security model | Explain same-origin policy, what CORS actually changes, and why a cookie with SameSite=Lax blocks some CSRF but not all | MDN "Same-origin policy", "CORS", "SameSite cookies"; PortSwigger CORS and CSRF learning material (not labs yet) |
| Auth | Explain how a session cookie login differs from a JWT, where each is stored, how each is invalidated, and what happens if a JWT signature is not checked | Auth0 "JWT handbook" chapters 1 to 4; OWASP Session Management cheat sheet |
| TLS | Explain what a certificate proves, what a certificate authority is, and why a self-signed cert warns but still encrypts | Cloudflare Learning Center "What is SSL/TLS" series, about 2 hours |
| Networking | Explain what an IP address, subnet mask, port, TCP handshake and DNS lookup are. Read this Nmap line and say what the box is: `22/tcp open ssh, 80/tcp open http, 3306/tcp open mysql` | TryHackMe "Network Fundamentals" and "Nmap" rooms; Professor Messer Network+ sections on TCP/IP and ports |
| Linux | In a terminal: find every file under /var modified in the last day, show which process is listening on port 8080, change a file so only its owner can read it, read the last 50 lines of a log while it grows, and explain what sudo does and what the SUID bit is | OverTheWire Bandit levels 0 to 20; TryHackMe "Linux Fundamentals" 1 to 3 |
| Deployment | Draw how your last app was deployed: reverse proxy, app process, database, environment variables, firewall or security group, and where secrets live | Redo it on a fresh VPS with Nginx in front; DigitalOcean's Nginx and firewall tutorials |
| SQL | Without an ORM, write a query with a JOIN and a GROUP BY, then explain exactly why string-concatenated queries are injectable and what a parameterised query does differently | SQLBolt (free, 2 hours); OWASP SQL Injection Prevention cheat sheet |
| Windows | Explain what a domain, a domain controller, Active Directory, a local admin and a service account are | TryHackMe "Windows Fundamentals" 1 to 3 and "Active Directory Basics" room |
| Scripting | In 30 minutes, write a Python script that logs into a site you own, fetches a page and extracts one value | Automate the Boring Stuff chapters 1 to 12, then the requests library docs |
| Reading code you did not write | Open an unfamiliar open-source web app on GitHub and find, in under an hour, where authentication happens and where user input reaches the database | Do this three times on three different frameworks |
| Security vocabulary | Explain, in one sentence each: vulnerability, exploit, CVE, attack surface, privilege escalation, lateral movement, what a pentest report contains | TryHackMe "Cyber Security 101" path, first third; read two public pentest reports |

### Weeks 2 to 4: fill only what you failed

Take the rows you failed, in the order they appear, and work through the resources in the right-hand column. Budget about a week per two rows. Keep the same notes wiki from day one: one page per topic, in your own words.

**Gate A (end of week 8).** Every row passes from memory on a retest. Do not start security labs on shaky HTTP, Linux or auth knowledge, because every later lab assumes them. All later phase weeks shift by four: Phase 0 is week 9, Phase 1 weeks 10 to 13, Phase 2 weeks 14 to 21, Phase 3 weeks 22 to 25, Phase 4 weeks 26 to 49, the exam around weeks 54 to 57.

## Phase 0: setup (week 5, one weekend, cost 0)

- Install a Kali Linux virtual machine (VirtualBox or VMware) with snapshots.
- Install Burp Suite Community and configure the browser proxy.
- Create accounts: PortSwigger Web Security Academy, TryHackMe, Hack The Box.
- Set up your notes wiki with a template page.
- Read OWASP Top 10 (2021) once, to learn the vocabulary.

## Phase 1: the free month (weeks 6 to 9, cost 0)

Goal: finish the core Web Security Academy topics and decide whether you like this.

| Week | Topics (Academy learning paths and labs) |
|---|---|
| 6 | SQL injection, cross-site scripting (all apprentice and practitioner labs) |
| 7 | Authentication, path traversal, OS command injection, business logic |
| 8 | Access control, CSRF, information disclosure, file upload |
| 9 | SSRF, XXE, clickjacking, CORS, race conditions |

Weekly output: every lab solved is a note page. By week 9 you should have 60 to 80 labs done.

**Gate 1 (end of week 9).** Ask yourself one question: did you do labs on a night you did not have to? If yes, continue. If you had to force every session, stop here and put the hours into paid development work instead.

## Phase 2: Burp Suite Certified Practitioner (weeks 10 to 17, cost about 600)

Buy Burp Suite Professional (499 per year) at the start of week 10. You need it for the exam and for any real client work.

| Week | Focus |
|---|---|
| 10 | Advanced topics: insecure deserialization, server-side template injection, JWT attacks |
| 11 | OAuth, prototype pollution, web cache poisoning, HTTP request smuggling |
| 12 | HTTP host header attacks, GraphQL, NoSQL injection, API testing |
| 13 | Finish every remaining practitioner lab; start the expert labs on your weak topics |
| 14 | Mystery labs: 10 a week with no topic hint, timed at 30 minutes each |
| 15 | PortSwigger practice exam, twice, under exam conditions (4 hours) |
| 16 | Review failures; redo the labs behind every miss; write one full report for a practice app |
| 17 | Sit the BSCP exam (99). It is two apps, three vulnerabilities each, four hours |

Selling starts here, in parallel:
- Week 11: publish two short technical posts in English on things you learned that apply to Georgian systems, such as testing rs.ge integrations or Keepz payment flows for common web flaws.
- Week 13: offer a "security review" add-on to every development client you have. Price it low the first two times.
- Week 17: with the certificate, approach five small fintechs or crypto firms and five software agencies in Tbilisi with a fixed-price web application test.

**Gate 2 (week 17).** Passed BSCP and had at least one conversation about paid work? Continue to OSCP. Failed BSCP? Retake in week 19, it is only 99. No interest in paid work at all? Stay a developer who does security reviews and skip OSCP.

## Phase 3: infrastructure deepening (weeks 18 to 21, cost about 30)

OSCP is mostly networks, Linux, Windows and Active Directory, which web work does not teach.

| Week | Focus |
|---|---|
| 18 | TryHackMe "Jr Penetration Tester" path: enumeration, Nmap in depth, service exploitation |
| 19 | Linux privilege escalation (TryHackMe room plus GTFOBins), Windows internals refresher |
| 20 | Windows privilege escalation, Active Directory attacks at a basic level, Metasploit basics |
| 21 | Hack The Box: 6 to 8 easy retired boxes from the TJ Null OSCP list, write a note per box |

## Phase 4: PEN-200 (weeks 22 to 45, cost 1,499 to 2,749)

Buy the PEN-200 Course and Cert bundle (90 days of lab) at week 22, or Learn One (2,749) if you want a full year and two attempts. Learn One is the safer buy given the pass rate.

| Weeks | Focus |
|---|---|
| 22 to 27 | Read every PEN-200 module and complete every exercise. Do not skip the boring ones; the exam bonus points come from exercises |
| 28 to 33 | Course challenge labs: Medtech, Relia, Skylark. Finish all three. This is where Active Directory clicks |
| 34 to 39 | Proving Grounds Practice (19 per month): 40 to 60 boxes from the TJ Null and Lain Kusanagi lists, at least 20 Windows, at least 10 Active Directory related |
| 40 to 43 | OSCP A, B and C challenge sets, each under exam conditions with a full report written afterwards |
| 44 to 45 | Timing drills: three boxes in six hours, then a full 24-hour mock on a weekend |

Targets by week 45: 100 or more boxes rooted in total, a report template you have used at least four times, and a personal cheat sheet you can navigate without searching.

## Phase 5: exam (weeks 46 to 53, cost 0 to 249)

- Week 46: book the exam three to four weeks out.
- Weeks 47 to 49: light revision, redo your five weakest boxes, sleep properly.
- Week 50: sit the exam. Sleep at least 4 hours during the 24 hours. Screenshot everything as you go.
- Week 51: write and submit the report within 24 hours.
- Weeks 52 to 53: if you failed, book the retake (249) for six to eight weeks later and spend the gap on the machine types that beat you.

## Costs and timeline

| When | Item | Cost |
|---|---|---|
| Weeks 1 to 4 | TryHackMe premium, optional | 0 to 15 |
| Week 10 | Burp Suite Professional | 499 |
| Week 17 | BSCP exam | 99 |
| Weeks 18 to 21 | TryHackMe premium, 2 months | about 30 |
| Weeks 22 to 45 | PEN-200 bundle or Learn One | 1,499 to 2,749 |
| Weeks 34 to 45 | Proving Grounds Practice, 3 months | about 60 |
| Week 52 | Retake, if needed | 249 |
| Total | | about 2,200 to 3,700 |

Money can start coming in from week 13 (security reviews) and week 17 (web tests), which is before the largest cost.

## Milestones

- Week 4: every self-test row passes.
- Week 9: 60 to 80 Academy labs, decision made.
- Week 17: BSCP passed, first paid or trial security review done.
- Week 21: 8 boxes rooted, comfortable with Nmap and privilege escalation basics.
- Week 33: all three PEN-200 challenge labs complete.
- Week 45: 100 boxes, mock exam done.
- Weeks 50 to 53: OSCP.
- After: register an LLC when a client requires it, and look at the Digital Governance Agency register once you have two or three tests behind you.

## Resources

- PortSwigger Web Security Academy (free): portswigger.net/web-security
- TryHackMe: tryhackme.com
- Hack The Box: hackthebox.com
- OverTheWire Bandit: overthewire.org/wargames/bandit
- TJ Null OSCP-like box list: search "TJ Null OSCP list" for the current spreadsheet
- OffSec PEN-200: offsec.com/courses/pen-200
- Proving Grounds Practice: offsec.com/labs
- GTFOBins and LOLBAS for privilege escalation lookups
- OWASP Web Security Testing Guide for report structure
