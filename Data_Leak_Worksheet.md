# Data Leak Worksheet and Least Privilege Review

## Project description

I work for an educational technology company whose application grades assignments
automatically and handles data from schools, instructors, parents, and students. The
team was alerted to a leak of internal business plans that showed up on social media,
and the investigation found that an employee had accidentally shared confidential
documents with an external business partner. The principle of least privilege was not
followed during a sales meeting. My job was to review the incident, look at the
controls already in place, and recommend improvements so it does not happen again. I
recorded my analysis in a data leak worksheet built around the NIST Cybersecurity
Framework and NIST SP 800-53 control AC-6.

## Incident summary

A customer success representative was given access to a folder of internal documents
by a manager. The folder held files tied to a new product offering, including customer
analytics and marketing materials. The manager forgot to unshare the folder afterward.
Later the representative meant to copy a link to just the marketing materials to share
with a business partner on a sales call, but instead shared a link to the entire
folder. The business partner received the link to the internal documents and posted it
to their social media page.

## Issue(s)

The leak happened because least privilege broke down at several points. The
representative was granted access to a whole folder of internal documents when only the
marketing materials were needed, and the manager forgot to remove that access once it
was no longer required. With no review or oversight of the sharing, a single copied
link exposed customer analytics and confidential plans to an outside partner.

## Review of NIST SP 800-53: AC-6

AC-6 is the Least Privilege control. It says the organization should only allow users
the access they specifically need to do their assigned jobs and nothing more. The
control comes with enhancements that tighten this further, such as regularly reviewing
the privileges each user holds and logging when privileged functions are used, so that
excess access is caught and removed before it can be abused or cause a leak.

## Recommendation(s)

Two control enhancements from AC-6 would have helped prevent this leak:

- AC-6(7) Review of User Privileges. Access rights should be reviewed on a set schedule
  to confirm each user still needs what they have. A periodic review would have flagged
  the folder the manager forgot to unshare and removed the representative's access
  before the link was ever created.
- AC-6(9) Log Use of Privileged Functions. Sharing and access to sensitive folders
  should be logged and monitored. Logging would have made the broad folder access
  visible to the security team, giving them a chance to spot and correct the
  oversharing before it left the company.

## Justification

These two enhancements attack the exact gaps that caused the leak. Reviewing user
privileges on a schedule stops access from lingering after it is needed, which is what
let the forgotten folder stay shared. Logging the use of privileged functions gives the
team visibility into who can reach sensitive data, so unusual sharing is caught early
instead of surfacing on social media after the damage is done.

## Summary

The leak came down to too much access left in place with no oversight. A representative
received a full folder of internal documents when only the marketing files were needed,
the manager never revoked that access, and nothing was watching the sharing, so one
mistaken link exposed confidential plans to an outside partner. Applying AC-6(7) to
review privileges on a schedule and AC-6(9) to log the use of privileged functions
would close both gaps, keeping access tight and making risky sharing visible before it
turns into another leak.
