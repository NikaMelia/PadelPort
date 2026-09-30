# Gap fill plan: eight weeks, day by day

Written 30 Sep 2026 from the self-test answers. Assumes five sessions a week: four weekday evenings of about 2 hours and one weekend block of 5 to 6 hours. Every resource is free unless marked. Keep a notes wiki from day 1: one page per topic, in your own words, with the exact commands.

Order is deliberate. Linux first, because every tool and every lab after this runs from a Linux terminal. Then the raw web layer, then the browser's security model, then the network under it, then the rest.

## Week 1: Linux, part 1

- **Day 1.** Install VirtualBox and a Kali Linux VM (kali.org, "virtual machines" download). Take a snapshot. Open a terminal. Learn: `pwd`, `ls -la`, `cd`, `cat`, `less`, `head`, `tail -f`, `mkdir`, `cp`, `mv`, `rm`. Make a notes page "Linux basics".
- **Day 2.** OverTheWire Bandit levels 0 to 8 (overthewire.org/wargames/bandit). You will need `ssh`, `find`, `file`, `sort`, `uniq`, `grep`. Write down every command that solved a level.
- **Day 3.** Bandit levels 9 to 15. Introduces `strings`, `base64`, `tr`, `openssl s_client`, `nc`. Also learn `man` and `--help`.
- **Day 4.** Users and permissions: read TryHackMe "Linux Fundamentals Part 2" (free). Then in Kali: `whoami`, `id`, `sudo`, `chmod`, `chown`, `ls -l` output explained, what `rwx` means for owner, group, other. Create a file only its owner can read.
- **Weekend (5 hours).** Bandit levels 16 to 24. TryHackMe "Linux Fundamentals Part 3": processes, `ps`, `top`, `kill`, cron, logs in `/var/log`. Exercise from the self-test: find every file under `/var` modified in the last day (`find /var -mtime -1`), show what is listening on a port (`ss -tlnp`), tail a growing log.

## Week 2: Linux, part 2, and the raw HTTP wire

- **Day 1.** Bandit 25 to 33 (finish it). Learn `ssh` keys, `scp`, environment variables, `export`, `$PATH`, `which`.
- **Day 2.** What SUID is: read the GTFOBins homepage and one example (gtfobins.github.io). In Kali run `find / -perm -4000 2>/dev/null` and read what comes back. Notes page "Permissions, sudo, SUID". Linux row done.
- **Day 3.** Raw HTTP. Read MDN "An overview of HTTP" and "HTTP messages". Then in Kali: `nc example.com 80`, type `GET / HTTP/1.1`, `Host: example.com`, blank line, and read the raw response. Do it with `curl -v` too. Write out a request and response from memory at the end.
- **Day 4.** Methods and status codes: MDN "HTTP request methods" and "HTTP response status codes". Define idempotent in your own words with an example. Install Burp Suite Community, set up the browser proxy, and watch 20 real requests to a site you own or to the PortSwigger Academy site. Note the Cookie, Set-Cookie, Content-Type and Authorization headers you see.
- **Weekend.** HTTP headers deep dive: MDN "HTTP headers" page, read the sections on Cookie, Set-Cookie, Cache-Control, Content-Type, Location, Origin, Referer. Then TryHackMe "Web Application Basics" and "How Websites Work" rooms. HTTP row done: redo the self-test task from memory.

## Week 3: browser security model and authentication

- **Day 1.** Same-origin policy: MDN "Same-origin policy". Write down what an origin is (scheme, host, port) and what the browser blocks by default.
- **Day 2.** CORS: MDN "Cross-Origin Resource Sharing". Key point to internalise: CORS lets a server relax same-origin so another origin may *read* the response; the request itself often goes out anyway. Then PortSwigger's CORS learning page (portswigger.net/web-security/cors), reading only, no labs.
- **Day 3.** CSRF: PortSwigger's CSRF learning page. Understand why a form on evil.com can submit to bank.com with the victim's cookie attached. Then MDN and PortSwigger on SameSite cookies: Strict, Lax, None, and why Lax still allows top-level GET navigations.
- **Day 4.** Sessions versus tokens: OWASP "Session Management Cheat Sheet", then Auth0's JWT introduction (jwt.io/introduction). Fill the gaps in your JWT answer: where a session ID lives (server store plus cookie) versus a JWT (client, usually cookie or local storage), how each is revoked, what "alg: none" and unchecked signatures mean.
- **Weekend.** Build it: a small app in your usual stack with a cookie-session login and a JWT login side by side. Watch both in Burp. Make a page on another origin that submits a form to it and see the cookie go along. Then set SameSite=Lax and watch it stop. Web security model and Auth rows done.

## Week 4: networking

- **Day 1.** TryHackMe "What is Networking?" and "Intro to LAN" (free). IP addresses, MAC, subnet mask, gateway, DHCP, in your own words.
- **Day 2.** TryHackMe "OSI Model" and "Packets and Frames". TCP three-way handshake, TCP versus UDP, what a port is, common ports (22, 25, 53, 80, 443, 445, 3306, 3389, 5432, 8080).
- **Day 3.** DNS: TryHackMe "DNS in Detail". Then run `dig`, `nslookup`, `host` in Kali on a few domains and read the answer sections.
- **Day 4.** Nmap: TryHackMe "Nmap" room. Scan your own VM or a TryHackMe target only. Learn `-sV`, `-sC`, `-p-`, `-oN`. Read the self-test Nmap line and say what the box is: a Linux web server with SSH and a MySQL database exposed.
- **Weekend.** Professor Messer Network+ videos (free on YouTube), only the sections on TCP/IP, ports and protocols, DNS, and firewalls, about 3 hours. Wireshark: TryHackMe "Wireshark: The Basics", capture your own HTTP request and find the GET line in the packet. Networking row done.

## Week 5: TLS, deployment and SQL injection

- **Day 1.** TLS: Cloudflare Learning Center, "What is SSL?", "What is TLS?", "What is an SSL certificate?", "What is a certificate authority?", about 90 minutes. Then `openssl s_client -connect example.com:443` and read the certificate chain.
- **Day 2.** Why a self-signed certificate warns but still encrypts; what a man-in-the-middle is; why Burp needs you to install its CA certificate to intercept HTTPS. Install Burp's CA in your browser and intercept an HTTPS site you own. TLS row done.
- **Day 3.** Deployment, on paper: draw your last real deployment with every box named: DNS, reverse proxy, app process, database, environment variables, secrets, firewall. Then read DigitalOcean's "Nginx reverse proxy" and "UFW essentials" tutorials.
- **Day 4.** Deployment, for real: on a cheap VPS or a second local VM, deploy a small app behind Nginx with HTTPS from Let's Encrypt and a firewall that allows only 22, 80 and 443. Then port-scan it from Kali and confirm only those are open. Deployment row done.
- **Weekend.** SQL injection: SQLBolt lessons 1 to 12 (sqlbolt.com) for the JOIN and GROUP BY refresh, then PortSwigger's SQL injection learning page, reading only, then OWASP "SQL Injection Prevention Cheat Sheet". Write, in your own stack, one concatenated query and one parameterised query, and explain exactly what differs when the input is `' OR 1=1--`. SQL row done.

## Week 6: Windows and Active Directory, at a basic level

- **Day 1.** TryHackMe "Windows Fundamentals 1": desktop, file system, users, permissions, UAC.
- **Day 2.** TryHackMe "Windows Fundamentals 2": system configuration, task manager, services, registry.
- **Day 3.** TryHackMe "Windows Fundamentals 3": updates, Defender, firewall, BitLocker, volume shadow copies.
- **Day 4.** TryHackMe "Active Directory Basics": domain, domain controller, users, groups, computers, group policy, Kerberos at a high level, service accounts.
- **Weekend.** Write a one-page explanation of a domain, a domain controller, Active Directory, a local admin and a service account, as if for a colleague. Then TryHackMe "Windows Command Line" and "Windows PowerShell" rooms. Windows row done.

## Week 7: scripting, reading code, vocabulary

- **Day 1.** Python check: in 30 minutes, write a script with the `requests` library that logs into your own test app, keeps the session or token, fetches a protected page and extracts one value. If you finish, the scripting row is done. If not, Automate the Boring Stuff chapters 1 to 12 over the next three evenings.
- **Day 2.** Reading unfamiliar code, attempt 1: pick an open-source web app on GitHub in a framework you do not use (for example a Django or Laravel project). In under an hour, find where login is checked and where user input reaches a database query. Note how long it took.
- **Day 3.** Reading unfamiliar code, attempt 2, a different framework. Attempt 3 at the weekend. Reading code row done.
- **Day 4.** Vocabulary: TryHackMe "Cyber Security 101" path, the first modules (security principles, careers, the attack lifecycle). Write one sentence each for: vulnerability, exploit, CVE, attack surface, privilege escalation, lateral movement.
- **Weekend.** Read two real public penetration test reports (search "public pentest reports GitHub", the juliocesarfort collection). Note the structure: scope, methodology, findings with severity, evidence, remediation. Draft your own report template from them. Vocabulary row done.

## Week 8: consolidate and retest

- **Day 1 to Day 4.** Redo the whole self-test from memory, one row per half hour. For any row that is still shaky, spend the rest of that evening on the resource for that row.
- **Weekend.** TryHackMe "Cyber Security 101" remaining offensive modules, plus three guided easy rooms (for example "Pickle Rick", "Basic Pentesting", "Simple CTF"). Follow the walkthroughs and make sure you understand every single step. This is your first taste of the real thing.

**Gate A.** All twelve rows pass from memory. Then start Phase 0 of the main plan, the PortSwigger Academy month, which is where you find out whether you like this.

## Costs for these eight weeks

- TryHackMe premium, about USD 15 a month, optional but it removes queueing and unlocks some rooms: about USD 30.
- A VPS for the deployment week, about USD 5 for one month, or use a second local VM for free.
- Everything else is free.
