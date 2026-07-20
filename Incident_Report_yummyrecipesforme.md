Cybersecurity Incident Report

Website affected: yummyrecipesforme.com
Role: Cybersecurity analyst working for the website hosting provider

Section 1: Identify the network protocol involved in the incident

The network protocols identified in the tcpdump packet capture were DNS and HTTP, and both of these ran on top of TCP and IP.

Looking at the four layers of the TCP/IP model, the protocols show up like this. At the application layer, DNS resolved the domain name yummyrecipesforme.com into an IP address, and later it resolved a second domain name, greatrecipesforme.com. Also at the application layer, HTTP was used to request the actual web pages. At the transport layer, TCP carried the HTTP traffic and handled the connection using the three way handshake. At the internet layer, IP routed the packets between the visitor and the web server using the resolved addresses. At the network access layer, the frames were physically transmitted across the network.

The protocol that stands out the most in this incident is DNS, because the capture shows a second DNS request for a completely different domain name, greatrecipesforme.com, which is the evidence of the malicious redirect.

Section 2: Document the incident

The incident affected the web server that hosts yummyrecipesforme.com, and it also affected the personal computers of the customers who visited the site and ran the file they were told to download.

The problem was first discovered a few hours after the attack, when several customers emailed the yummyrecipesforme.com helpdesk. They reported that the website had prompted them to download a file to get free recipes, and that after they ran the file the website address changed and their computers started running more slowly. The website owner then tried to log in to the admin panel, could not get in, and contacted the website hosting provider. A group of cybersecurity analysts, including me, was assigned to investigate.

The root cause was a brute force attack against the web server. A former employee repeatedly entered several known default passwords for the administrative account until the correct one was guessed. The password was easy to guess because the admin account was still set to its default password, and there were no controls in place to limit or block repeated failed login attempts.

Once the attacker had valid administrator credentials, they logged into the admin panel and changed the website source code. They added a JavaScript function that prompted every visitor to download and run an executable file that was disguised as a browser update. After adding the code, the attacker changed the administrator password, which locked out the real owner.

To investigate safely, the team built a sandbox environment and ran the network protocol analyzer tcpdump while browsing to yummyrecipesforme.com. The tcpdump log recorded the following sequence of events:

1. The browser sent a DNS request for the IP address of yummyrecipesforme.com.
2. The DNS server replied with the correct IP address.
3. The browser sent an HTTP request to that IP address for the yummyrecipesforme.com page.
4. When the page loaded, the browser was prompted to download an executable file, and the download of the malware started.
5. After the file ran, the browser sent a DNS request for greatrecipesforme.com.
6. The DNS server responded with the IP address for greatrecipesforme.com.
7. The browser sent an HTTP request to the IP address for greatrecipesforme.com, which is the fake website that contained the malware.

The impact was that customers who ran the file were redirected from the real site, yummyrecipesforme.com, to a fake site, greatrecipesforme.com, that hosted malware, and they reported that their computers slowed down afterward. The legitimate owner also lost access to the administrative account.

The information and evidence in this report came from several sources. The tcpdump traffic log captured during the sandbox investigation showed the DNS and HTTP exchanges listed above. The customer helpdesk emails reported the malicious download and the redirect. A senior analyst reviewed the website source code and confirmed the injected JavaScript that prompted the download. Analysis of the downloaded executable found a script that redirected browsers from yummyrecipesforme.com to greatrecipesforme.com. The cybersecurity team also confirmed that the server had been reached through a brute force attack against a default administrator password.

Section 3: Recommended remediation for brute force attacks

My recommendation is to limit the number of login attempts on the administrative account.

The organization should set the admin login to lock the account, or add an increasing time delay, after a small number of failed attempts in a row, for example five. A brute force attack works by submitting a very large number of password guesses quickly, so putting a cap on the number of allowed attempts takes away the attacker's ability to keep guessing. This would have stopped the attacker from cycling through default passwords until one worked, and the repeated failures would also create alerts that make the attack visible to the security team.

This control works best when it is combined with other measures, such as requiring strong passwords that are not defaults, turning on two factor authentication for the administrator account, and monitoring login attempts for unusual patterns. Using several of these measures together means that even if one is bypassed, the others still help protect the admin panel.
