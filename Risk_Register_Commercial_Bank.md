# Risk Register and Risk Assessment for a Commercial Bank

## Project description

I joined the cybersecurity team at a commercial bank while the team was running a
risk assessment of the bank's operating environment. My supervisor asked me to work
through the risk register, which is the central record of the risks facing the
bank's assets, systems, and data. For five risks to the bank's funds I estimated how
likely each one is to happen, how severe the impact would be, and then calculated a
priority score so the team could decide where to focus first. Risk is worked out with
a simple formula, Likelihood times Impact equals Risk, and both likelihood and
severity are scored on a scale of 1 to 3.

## Operating environment

The bank sits in a coastal area with low crime rates. Its data is handled by a lot of
people and systems, with 100 on-premise employees and 20 remote employees, and it
serves 2,000 individual accounts and 200 commercial accounts. The bank is marketed by
a professional sports team and ten local businesses, so its reputation is visible in
the community. Strict financial regulations apply, including the requirement to hold
enough cash each day to meet Federal Reserve rules. The coastal location also brings
weather risk, since hurricanes can disrupt supply and power every few years.

## Risk factors (Notes)

The bank's funds are exposed on several fronts at once. A large mix of on-premise and
remote staff handling money and customer records widens the chance of a business
email compromise or an accidental leak, while the bank's public profile makes it an
attractive target for attackers going after its user database or financial records.
On top of that, the coastal location adds natural hazards like hurricanes that can
interrupt supply chains and stop the bank from replenishing its daily funds.

## Risk register

| Risk | Description | Likelihood (1-3) | Severity (1-3) | Priority (L x S) |
|---|---|---|---|---|
| Business email compromise | An attacker spoofs or takes over a staff email account to trick employees into approving fraudulent transfers of the bank's funds. | 3 | 3 | 9 |
| Compromised user database | Attackers gain access to the database holding customer account details, exposing thousands of individual and commercial accounts. | 2 | 3 | 6 |
| Financial records leak | Sensitive financial records are disclosed, leading to lost profits, lost customers, and heavy regulatory fines. | 2 | 3 | 6 |
| Theft | Physical or digital theft of funds or assets from the bank. | 1 | 2 | 2 |
| Supply chain attack | A supply or power disruption, such as one caused by a coastal hurricane, prevents the bank from replenishing funds to meet Federal Reserve requirements. | 1 | 3 | 3 |

## How I scored likelihood

Business email compromise is one of the most common attacks against banks, and with
120 employees handling funds there are many chances for it to succeed, so I scored its
likelihood as 3. A compromised user database and a financial records leak are real and
recurring threats for a bank this visible, but they take more effort to pull off than a
phishing email, so I scored each as 2. Theft scored 1 because the bank is in a low
crime area, which lowers the chance of a physical break-in. The supply chain attack
also scored 1, since the hurricanes that would cause it only reach the bank every few
years.

## How I scored severity

Business email compromise scored 3 because a single approved fraudulent transfer moves
real money straight out of the bank and damages trust. The compromised user database
and the financial records leak both scored 3 as well, since they expose thousands of
customers, invite regulatory fines, and hurt the bank's reputation. Theft scored 2
because the harm is real but usually limited in scope and often insured. The supply
chain attack scored 3 because failing to meet the Federal Reserve's daily cash
requirement is a regulatory and operational problem the bank cannot afford.

## Priority and what it means

Multiplying likelihood by severity gives the priority score that the team can sort on.
Business email compromise came out on top at 9, so it deserves the most attention and
resources, things like email authentication, staff training, and stronger transfer
approvals. The compromised user database and the financial records leak both scored 6
and come next, followed by the supply chain attack at 3 and theft at 2.

| Priority | Risk |
|---|---|
| 9 | Business email compromise |
| 6 | Compromised user database |
| 6 | Financial records leak |
| 3 | Supply chain attack |
| 2 | Theft |

## Summary

I worked through the bank's risk register by scoring the likelihood and severity of
five risks to its funds and multiplying the two to get a priority score for each. The
scores put business email compromise first at 9, the compromised user database and the
financial records leak next at 6 each, the supply chain attack at 3, and theft last at
2. Laying the risks out this way turns a list of worries into a ranked plan, which is
the real point of a risk assessment. It lets the team put its time and money against
the risks most likely to hurt the bank instead of spreading effort evenly across
threats that are not equal.
