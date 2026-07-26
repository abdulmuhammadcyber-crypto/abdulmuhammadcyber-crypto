# Access Control Worksheet and Incident Review

## Project description

I am the first cybersecurity professional hired by a growing business. A deposit was
made from the company to an unknown bank account, the finance manager confirmed it was
not their mistake, and the payment was stopped in time. The owner asked me to
investigate so it does not happen again. I reviewed the event log of the incident,
cross referenced it against the employee directory, identified the access control
issues that let it happen, and recommended fixes. The whole business currently manages
its files on one shared cloud drive that everyone can reach, which is where most of the
problem starts.

> Note: the exact name, IP address, and timestamp below come from the Event log and
> Employee directory tabs of the Accounting exercise spreadsheet. I have described what
> the log reveals so the reasoning is clear, and marked where the specific values drop
> in.

## Notes about the user

The event log shows the payment was made outside of normal business hours, which is a
red flag on its own since finance activity should happen during the workday. The IP
address in the log does not match the address the finance team normally works from,
so the action came from an unfamiliar location. When I matched the account against the
employee directory, the user tied to the event was not someone whose role should have
access to payroll or payment files, which points to either a former employee whose
account was never disabled or an account being used by the wrong person.

## Access control issues

- The business runs on a single shared cloud drive where every employee can open every
  file. There is no least privilege and no separation by role, so payment files sit
  wide open to people who have no business reason to touch them.
- Access is not tied to the person's current role or employment status. An account that
  should have been limited or removed was still active and still had reach into
  sensitive finance files, which is exactly what the attacker used.

## Recommendations

- Apply the principle of least privilege with role based access control. Give each
  employee access only to the files their job requires, and move payroll and payment
  files off the shared drive into a folder restricted to the finance team.
- Put a formal offboarding process in place that revokes accounts and access the moment
  an employee leaves, and review access rights on a regular schedule so nothing lingers.
- Require multi-factor authentication on all accounts, especially any with access to
  financial systems, so a stolen or leftover password is not enough to get in.
- Turn on logging and alerting for finance actions, including logins outside business
  hours or from unfamiliar IP addresses, so a strange payment is caught as it happens
  instead of after the money is gone.

## Summary

The fraudulent deposit succeeded because the business trusted a single shared drive and
never matched access to who people actually are or what their jobs need. The event log
gave it away with an out-of-hours action from an unfamiliar IP tied to an account that
should not have reached the payment files. Locking the company down with least
privilege, proper offboarding, multi-factor authentication, and real logging closes the
gaps that made this possible and makes a repeat far less likely.
