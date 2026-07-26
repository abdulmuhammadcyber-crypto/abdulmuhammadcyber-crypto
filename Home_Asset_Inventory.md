# Home Asset Inventory and Classification

## Project description

For this activity I ran a small business out of my home and needed to build an
inventory of the devices connected to my home network. The point of the exercise
is that most valuable information moves across a network, and every device on that
network is a possible way in for an attacker. Writing down what is connected, who
owns it, where it sits, and how sensitive it is helps me see which assets need the
most protection. I started from a template that already listed a network router, a
desktop, and a guest smartphone, then added three more devices of my own and filled
in the details for each.

## Scenario

The home office has a desktop computer, a printer, a router, a webcam, speakers,
headphones, and an external hard drive. Because I am running a business from home,
I need to know which of these devices hold sensitive information so I can give them
extra protection. To keep the inventory useful I recorded how often each device is
on the network, who is responsible for it, where it lives in relation to the router,
a note or two about the risk it carries, and a sensitivity level.

## The three devices I added

The router, desktop, and guest smartphone were already in the template for
reference, so I chose three devices that were not on the list yet:

- Personal laptop
- External hard drive
- Webcam

## Asset inventory

| Asset | Network access | Owner | Location | Notes | Sensitivity |
|---|---|---|---|---|---|
| Network router | Always connected | Me | Home office, central | Uses one frequency for smart home devices and another for everything else, so guest and personal traffic stay separated. Access is limited to specific users. | Confidential |
| Desktop | Occasional | Me | Home office | Holds business records and personal photos that only I should see. Connects over an ethernet cable, so it is not exposed over Wi-Fi. | Restricted |
| Guest smartphone | Occasional | Guest | Anywhere in the home | Connects to the guest network only and holds no business information. The owner changes often since it belongs to whoever is visiting. | Internal-only |
| Personal laptop | Frequent | Me | Home office and moves around the house | Stores client files, invoices, and saved logins for business accounts. It leaves the house sometimes and joins other networks, which widens the risk. I keep it patched and use full disk encryption. | Restricted |
| External hard drive | Occasional | Me | Locked drawer in the home office | Keeps the backup copies of business records and financial documents. It only connects when I run a backup, so it is offline most of the time, but losing it would mean losing the last safe copy of that data. | Restricted |
| Webcam | Always connected | Me | Home office, on top of the monitor | Streams live video and audio over Wi-Fi. Cameras like this often ship with weak default passwords, so I changed the login and keep the firmware current. If it were taken over it could watch the office. | Confidential |

## How I evaluated the access

Before classifying anything I looked at how each device reaches the network and how
careful the owner is with it. The desktop and the external hard drive are the
easiest to reason about because they are wired or offline most of the time, which
keeps their exposure low even though the data on them is sensitive. The webcam and
the personal laptop are the opposite. They are on Wi-Fi and, in the laptop's case,
they leave the house, so they touch more networks and carry more risk. The guest
smartphone matters least because it is walled off on the guest network and never
sees business data.

## How I classified the sensitivity

I sorted each device using the four levels from the course and asked what would
happen to the business if that device were compromised. If information would be
disclosed or stolen, if an attacker could quietly change what is stored on it, or
if the business would struggle when that data was destroyed, the device earned a
higher level.

- Restricted is the highest level and I gave it to the desktop, the personal laptop,
  and the external hard drive. These hold the client files, financial records, and
  backups that the business could not easily replace. Losing or exposing any of them
  would hurt the most.
- Confidential covers the router and the webcam. Access to both is limited to
  specific people, and either one being taken over would give an attacker a foothold
  or a view into the office, but they do not store the core business records
  themselves.
- Internal-only fits the guest smartphone. It stays on the guest network and holds
  nothing that belongs to the business, so its exposure is contained.

## Summary

I built an inventory of six devices on my home network and recorded the network
access, owner, location, a short risk note, and a sensitivity level for each one.
The desktop, personal laptop, and external hard drive came out as Restricted because
they hold the information the business depends on. The router and webcam are
Confidential since they control or watch the environment but do not store the core
data. The guest smartphone is Internal-only because it is isolated on the guest
network. Going through this exercise showed me that the most sensitive data is not
always on the device that looks the most active, and that keeping a simple, current
inventory is the first real step toward protecting the confidentiality, integrity,
and availability of everything on the network.
