# Netheret help desk, step 05: raise a request

A teaching example. Over sixteen steps we build a help desk web app for
Netheret, a made-up company that supports the IT of small businesses. This
step lets a customer raise a support request, and lets Tier 1 agents and
managers log one for a customer who phones in.

## What this step adds

- `helpdesk/tickets.py`, a new blueprint with:
  - `/requests/new`: the form. `check_request_form` checks every field and
    returns a dictionary of error messages;
  - `/requests/<id>/raised`: the confirmation page with the reference,
    like `NTH-0017`.
- `helpdesk/templates/_macros.html`: an error summary and per-field error
  messages that every form can use.
- A "Raise a request" link in the menu for the roles that can use it.

## Run it

```
python -m venv .venv
source .venv/bin/activate        # on Windows: .venv\Scripts\activate
pip install -r requirements.txt
python seed.py
flask --app helpdesk run --debug
```

Sign in as `customer@brightwell.example` (demo password `password123`) and
raise a request. Try sending the form empty to see the error messages, then
sign in as `tier1@netheret.example` and log one for a company.

## What to look at

- The checks happen on the server. The form says `novalidate` so you can see
  them working; a browser's own checks are easy to skip.
- Choices are checked against the lists in `models.py`, not just trusted.
- A customer's request always gets their own company, taken from their
  account and never from the form.
- The confirmation page answers 404 to a customer from another company.
- Each error message is linked to its field with `aria-describedby`.

## Learn this step

This is step 5 of 16 of **Task 2. Developing the solution**, a free series of T Level Digital Software Development
lessons that builds the Netheret help desk in agile sprints with Python and Flask. Read the lesson for this step:
[Raising a support request](https://mitsurutech.co.uk/resources/t-level/dsd-t2-05-raise-request).

- Previous step: [step 04, signing in, roles and sessions](https://github.com/mitsurutech/netheret-helpdesk-04-sign-in)
- Next step: [step 06, the request queue and filters](https://github.com/mitsurutech/netheret-helpdesk-06-queue)
- [Every free T Level Digital lesson](https://mitsurutech.co.uk/resources/t-level)
- [Teach these lessons to your class on MitsuruTech](https://mitsurutech.co.uk/learning), [see the pricing](https://mitsurutech.co.uk/pricing) or
  [start a free year for your college](https://mitsurutech.co.uk/signup)

## About

Written by [Mitsuru Technologies](https://mitsurutech.co.uk) (MitsuruTech) as a teaching example for T Level Digital
Software Development. The Netheret IT Support Solutions brief is from Pearson's sample assessment material; this code
and its notes are our own, and are not published, endorsed or approved by Pearson or the Department for Education.
'T Level' is a registered trade mark of the Department for Education.

