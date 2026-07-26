# USB Baiting Exercise: The Parking Lot Drive

## Project description

I am part of the security team at Rhetorical Hospital. One morning I found a USB stick
with the hospital's logo on the ground in the parking lot, with no one around who might
have dropped it. Instead of plugging it into a normal machine, I examined it inside
virtualization software on an isolated workstation, which is one of the only safe ways
to inspect an unknown drive because the virtual machine is not connected to other files
or networks. The contents appeared to belong to Jorge Bailey, the hospital's human
resource manager. I did not open any of the files, which is best practice.

## Contents

The drive holds a mix of personal and work files belonging to Jorge Bailey, the HR
manager. On the personal side there are folders of family and pet photos. On the work
side there is a new hire letter and an employee shift schedule. Together these files
carry personally identifiable information about Jorge, new employees, and other staff
at the hospital.

## Attacker mindset

An attacker could use these details to build a convincing phishing or social
engineering attack. Knowing Jorge is in HR, along with new hire information and staff
schedules, would let them impersonate him or target new employees who do not yet know
the hospital's people and processes. The whole event may have been staged as bait,
hoping a curious finder would plug the drive in and open a backdoor into the network.

## Risk analysis

A baited USB can carry malware such as ransomware, spyware, worms, or a keylogger, and
if another employee had plugged this into a live machine it could have infected the
hospital network and exposed patient data. Technical controls help most: disable
autorun, block or restrict USB ports through device control, and require endpoint
protection that scans removable media. Operationally, staff should be trained never to
plug in found drives and to hand them to security, while managerial policy should
separate personal and business drives and require any unknown media to be examined in
isolation. Layering these controls reduces both the chance and the impact of a USB
baiting attack.

## Summary

A logo-branded USB left in the parking lot is a classic baiting setup that preys on
curiosity. Even though this drive held no malicious code, the personal and work files
on it gave an attacker plenty to build targeted phishing or impersonation attacks, and
a real bait drive could have delivered malware straight into the hospital network.
Inspecting it in an isolated virtual machine, never opening the files, and backing that
up with USB port control, endpoint scanning, training, and a clear removable-media
policy is how a security team keeps a found drive from turning into a breach.
