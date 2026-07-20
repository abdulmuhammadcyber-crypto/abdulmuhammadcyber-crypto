# Cybersecurity Incident Report — yummyrecipesforme.com

**Analyst role:** Cybersecurity analyst (website hosting provider)
**Affected asset:** yummyrecipesforme.com (recipe/cookbook e-commerce website)
**Report type:** Web server compromise — brute force attack leading to source-code tampering and malware redirect

---

## Section 1: Identify the network protocol involved in the incident

The network protocols identified in the tcpdump packet capture were the **Domain Name System (DNS)** protocol and the **Hypertext Transfer Protocol (HTTP)**, both carried over **TCP/IP**.

Mapped to the four-layer TCP/IP model:

- **Application layer:** DNS and HTTP — DNS resolved the domain name `yummyrecipesforme.com` (and later `greatrecipesforme.com`) to an IP address, and HTTP was used to request the web pages.
- **Transport layer:** TCP — provided the reliable, connection-oriented delivery (three-way handshake) that the HTTP requests rode on.
- **Internet layer:** IP — routed the packets between the client and the web server using the resolved IP addresses.
- **Network Access layer:** the physical/data-link transmission of the frames on the wire.

The protocol most central to the observed behavior is **DNS**, because the capture shows a *second* DNS request for a different domain (`greatrecipesforme.com`) — evidence of the malicious redirect.

---

## Section 2: Document the incident

**Where it occurred:** The incident affected the web server hosting yummyrecipesforme.com and, downstream, the personal computers of customers who visited the site and ran the downloaded file.

**How it was discovered:** Several hours after the attack, multiple customers emailed the yummyrecipesforme.com helpdesk. They reported that the website prompted them to download a file to access "free recipes," and that after running the file the website address changed and their computers began running more slowly. The website owner then attempted to log in to the admin panel, could not, and contacted the website hosting provider. A team of cybersecurity analysts, including this analyst, was assigned to investigate.

**How it happened (root cause):** The web server was compromised through a **brute force attack**. A former employee repeatedly entered several known default passwords against the administrative account until the correct one was guessed. The password was easy to guess because the admin account was still set to its **default password**, and there were **no controls in place to limit or block repeated failed login attempts**.

**What the attacker did:** After obtaining valid administrator credentials, the attacker accessed the admin panel and modified the website's source code. They inserted a **JavaScript function** that prompted every visitor to download and run an executable file (disguised as a browser update). The attacker then **changed the administrator password**, locking out the legitimate owner.

**Observed behavior in the sandbox investigation:** To safely reproduce the issue, analysts built a sandbox environment and ran the network protocol analyzer **tcpdump** while browsing to `yummyrecipesforme.com`. The tcpdump log recorded the following sequence:

1. The browser sent a **DNS request** for the IP address of `yummyrecipesforme.com`.
2. The **DNS server replied** with the correct IP address.
3. The browser sent an **HTTP request** to that IP address for the yummyrecipesforme.com page.
4. On page load, the browser was prompted to download an executable file; the download of the malware was initiated.
5. After the file ran, the browser sent a **DNS request** for `greatrecipesforme.com`.
6. The **DNS server responded** with the IP address for `greatrecipesforme.com`.
7. The browser sent an **HTTP request** to the IP address for `greatrecipesforme.com`, the fake site containing the malware.

**Impact:** Customers who ran the file were redirected from the legitimate site (`yummyrecipesforme.com`) to a fraudulent site (`greatrecipesforme.com`) hosting malware, and reported degraded performance on their personal computers. The legitimate owner lost access to the administrative account.

**Sources of information and evidence:**
- The tcpdump traffic log captured during the sandbox investigation (packet capture of the DNS and HTTP exchanges above).
- Customer helpdesk emails reporting the malicious download and redirect.
- Source-code review by a senior analyst, which confirmed the injected JavaScript that prompted the download.
- Analysis of the downloaded executable, which contained a script redirecting browsers from yummyrecipesforme.com to greatrecipesforme.com.
- The cybersecurity team's finding that the server was reached via a brute force attack against a default administrator password.

---

## Section 3: Recommended remediation for brute force attacks

**Recommendation: Limit the number of login attempts (account lockout / rate limiting).**

The organization should configure the admin login to lock the account, or introduce an increasing time delay, after a small number of consecutive failed attempts (for example, five). A brute force attack depends on being able to submit a large volume of password guesses quickly. Capping the number of allowed attempts directly removes that ability — the attacker is stopped or slowed to the point that guessing even a weak or default password becomes impractical, and the repeated failures also generate alerts that make the attack visible to defenders.

This control should be paired with supporting measures for defense in depth: requiring strong, non-default passwords, enforcing two-factor authentication (2FA) on the administrative account, and monitoring login attempts for abnormal patterns. Together these ensure that even if one control is bypassed, others remain in place to protect the admin panel.
