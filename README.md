# Practice Mail Console

A staff-only email administration dashboard for Kwandengezi Medical Centre, built as a front end
over the host's DirectAdmin so staff can manage practice email addresses without touching
Roundcube.

Roundcube's own interface is rough enough that people avoid it, which means mailboxes don't get
created and forwarding doesn't get set up. This replaces the front end and nothing else — the mail
server, the accounts and the storage are all still DirectAdmin's.

Separate application from the public site, and deliberately so: it holds a DirectAdmin login key
and must run on a Node server. Never a static export, never bundled with the marketing site.

## What it does

- **Mailboxes** — list, create, reset passwords, change storage quota, delete.
- **Forwarding and aliases** — route shared addresses like `info@` or `admin@` to real staff
  mailboxes.
- **Auth** — a single shared staff password with signed-cookie sessions. Every page is gated.
- **Demo mode** — runs on in-memory sample data with no mail server connected, so the whole
  interface is clickable before any credentials exist. This is the default, which means a new
  machine can run the app in one command.

Planned: reading and replying over IMAP/SMTP, per-user staff accounts, autoresponders, signatures,
and an audit log.

## Stack

Next.js 14, React 18, TypeScript. `imapflow` and `mailparser` for the mail side, `nodemailer` for
sending, `undici` for the DirectAdmin API. Runs on port 3100 so it never collides with the main
site's dev server.

## Status

Phase 1 built. Client work — repo is private.

---

<sub>Source is private — this repo is the write-up. [Shaun Madondo](https://github.com/TheC0deJunkie) · Durban, KwaZulu-Natal.</sub>
