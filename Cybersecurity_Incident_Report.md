Cybersecurity Incident Report

Section 1: Identify the type of attack that may have caused this network interruption

One potential explanation for the website's connection timeout error message is: A denial of service attack known as a SYN flood. The web server is being hit with far more connection requests than it can handle, which is why it stops responding and visitors get a connection timeout error.

The logs show that: A very large number of TCP SYN requests are arriving from a single unfamiliar IP address in a short window of time. The volume is much higher than normal traffic, and the handshakes are never completed, so the server is left holding many unfinished connections.

This event could be: A SYN flood, which is a form of denial of service (DoS) attack. Because the requests come from one source address, it points to a single source DoS rather than a distributed denial of service, although the attacker can spoof other addresses to keep the attack going after an IP block.

Section 2: Explain how the attack is causing the website to malfunction

When website visitors try to establish a connection with the web server, a three way handshake occurs using the TCP protocol. The three steps of the handshake are:
1. The client sends a SYN packet to the server to ask to open a connection.
2. The server replies with a SYN ACK packet to acknowledge the request and set aside resources for the new connection.
3. The client sends back a final ACK packet, and the connection is established so data can be exchanged.

Explain what happens when a malicious actor sends a large number of SYN packets all at once: The attacker sends a flood of SYN packets but never returns the final ACK to complete any of them. For every SYN it receives, the server replies with a SYN ACK and then reserves memory and a slot in its connection table while it waits for an ACK that never arrives. These are called half open connections. As thousands of them pile up, the server's connection resources are used up.

Explain what the logs indicate and how that affects the server: The logs show a heavy stream of SYN requests from one unfamiliar IP with no completed handshakes, which is the signature of a SYN flood. Once the connection table fills with half open connections, the server has no room left to accept new sessions. Legitimate visitors and employees can no longer reach the site and receive a connection timeout error, so the website is effectively taken offline until the traffic is filtered and the server recovers.

Ways to help prevent this attack in the future: Turn on SYN cookies so the server does not reserve resources for a connection until the handshake is finished. Use firewall and rate limiting rules to cap how many SYN requests a single source can send. Place the site behind a DDoS mitigation service or content delivery network that can absorb and filter large traffic spikes. Set shorter timeouts for half open connections so they clear faster, and keep monitoring in place to alert on abnormal SYN volume.
