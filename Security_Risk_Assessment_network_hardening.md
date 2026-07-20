Security Risk Assessment Report

Organization: Social media company
Role: Security analyst

Overview

The organization recently experienced a major data breach that exposed customer personal information such as names and addresses. After inspecting the network, I found four major vulnerabilities that need to be addressed so the company can prevent another breach in the future. The four vulnerabilities are that employees share passwords, the database admin password is still set to the default, the firewalls have no rules in place to filter traffic coming in and out of the network, and multifactor authentication is not used. This report explains the network hardening tools and methods that should be used to reduce these risks and why they are effective.

Part 1: Recommended network hardening tools and methods

The most effective response to this situation is a combination of firewall traffic filtering, multifactor authentication, and stronger password and access practices.

The first and most urgent hardening task is to configure firewall rules and port filtering. Right now the firewalls pass all traffic because no rules are defined, which means malicious traffic can move in and out of the network freely. The firewall should be set up with rules that allow only the traffic the organization actually needs, and port filtering should block ports and services that are not in use. This directly reduces the number of ways an attacker can reach the network and is a control that should be reviewed on a regular schedule so the rules stay current.

The second hardening task is to turn on multifactor authentication for accounts that access the network and the database. Multifactor authentication requires a second piece of proof of identity in addition to a password, such as a code from a phone or a hardware token. Even if an attacker steals or guesses a password, they still cannot log in without the second factor, so this control adds a strong layer of protection on top of the login process.

The third hardening task is to fix the password and access problems. The default admin password on the database must be changed to a strong, unique password right away, because default passwords are widely known and are one of the first things an attacker will try. Employees should also stop sharing passwords and instead use their own individual accounts, so that access can be tracked to a specific person and a single shared secret does not expose multiple accounts at once. Supporting practices such as requiring strong passwords and monitoring login attempts help keep these accounts protected over time.

Part 2: Why the selected tools and methods are effective

The recommended techniques are effective because each one closes off a specific way that an attacker could reach the customer data.

Firewall rules and port filtering are effective because they control exactly what traffic is allowed to enter and leave the network instead of letting everything through. By allowing only known, needed traffic and closing unused ports, the organization removes many of the paths an attacker would use to get in or to move data out. Firewall rules are not a one time task. They need to be reviewed and updated on a regular basis, for example monthly or whenever the network changes, so that the rules keep matching what the network actually needs.

Multifactor authentication is effective because it protects accounts even when a password is compromised. Since the login now requires a second factor that the attacker does not have, a stolen or guessed password is no longer enough to break in. This is especially important here because employees were sharing passwords and the database used a default password. Multifactor authentication is set up once per account and then used every time a user logs in, so it provides continuous protection at the point of login.

Changing the default database password and ending password sharing are effective because they remove the easiest openings an attacker has. A default password is public knowledge and can be guessed almost instantly, so replacing it with a strong, unique password immediately raises the difficulty of getting in. Giving each employee an individual account makes it possible to see who did what and limits the damage if one account is exposed. Passwords should be changed on a regular schedule and reviewed whenever an employee leaves or changes roles.

Using these tools and methods together gives the organization layered protection. If one control is bypassed, the others still stand in the way, which lowers the chance of another data breach and helps keep customer information secure.
