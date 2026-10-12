# Clarity Desk — release notes

Clarity Desk (Windows) and the Clarity iPhone app, for Clarity Counselling Australia.

**Version numbers** look like `1.8.0 (build 41)`:

- **1**.x.x — a big change in how Clarity works (rare).
- x.**8**.x — new features.
- x.x.**1** — fixes and small improvements only.
- *build* — counts every update the PC receives, so a newer build always replaces an older one, even within the
  same version.

The newest version is at the top. The build reads its version from the first `## [x.y.z]` heading below, so every
change adds or extends an entry here. (Maintainers: features → bump the middle number, fixes only → the last.)

## [1.8.1] — 2026-10-12

### Fixed
- Consent forms: long tick-box wording (like the optional transcript agreement) now sits beside its box instead of
  dropping underneath it.
- Telehealth consent: the **Call-back number** box now says it's the client's own mobile (it fills in from the
  client's phone number when one is saved).

## [1.8.0] — 2026-10-12

### New
- **Automatic updates (PC).** Clarity checks for a new version every few hours and downloads it in the background.
  When the bell says an update is ready, click **Restart to update**: it installs quietly and reopens in a few
  seconds. Settings → Updates shows the version and has **Check now**.
- **Updates are encrypted and signed.** The published files are unreadable to anyone else, and Clarity installs only
  updates signed by the official build.
- **Notifications bell** (PC sidebar, iPhone Home): new online bookings, bookings that failed the client-ID check,
  reminders to send for tomorrow, overdue invoices, problems to fix and "update ready". The number shows what's new;
  opening the bell marks it read.
- **Settings badge.** When something needs fixing (Google not connected or sign-in expired, a missing Google
  permission, can't reach Google, iPhone sync stopped, no recent backup) Settings shows a count and a warning sign,
  and the problems are listed at the top of Settings with what to do.
- Release notes (this file), with the version shown in Settings.

### Improved
- The Google status at the bottom of the PC sidebar turns amber/red with the reason, and opens Settings.
- Clarity now tells "Google sign-in needs redoing" apart from "the internet is down".

## [1.7.0] — 2026-10-12

### New
- **Client IDs for online booking.** Every client has an ID like `CC-7K4QX` on their Details tab, with Copy,
  **Email it to them** (with the booking link) and **New ID**.
- Online bookings must give a client ID that matches a client:
  - match → marked *client ID ✓* and linked to the client automatically;
  - no match → flagged **Unverified** straight away and (by default) cancelled in Google, with one polite email to
    the booker explaining how to get in touch. At most one such email a day per address.
- Setting: cancel and email / keep but flag / don't check. **Keep this booking** to override.

## [1.6.1] — 2026-10-12

### Fixed
- **Join Google Meet** and other links didn't open from the Windows app. They now open in your normal browser.
- Clearer messages when Google Calendar or the Meet API isn't switched on, versus a missing permission.

## [1.6.0] — 2026-10-12

### New
- **Appointments** on the PC and iPhone, from your Google booking page and Calendar: This week / Upcoming / Past /
  Cancelled, a Today card, **Join Google Meet**, call or directions.
- Book, change and cancel appointments; Google emails the client the invitation and any change.
- Reminder emails (and a "reminders to send for tomorrow" prompt).
- Session notes per appointment (they also appear in Session notes), and Meet transcripts with the client's consent,
  summarised into notes by Hermes.
- Create an invoice straight from an appointment.

## [1.5.0] — 2026-10-12

### New
- **Delete invoices** that never left the practice (unpaid and never emailed), on PC and iPhone. Invoices that were
  paid or emailed can still only be voided, because tax records must be kept.

## [1.4.1] — 2026-10-12

### Fixed
- Invoice emails were landing in spam: clearer subjects ("Invoice … from … – session"), bank details on the PDF
  only, larger text. A DNS guide for the email domain (SPF, DKIM, DMARC).

## [1.4.0] — 2026-10-12

### New
- **Insights on the iPhone**, matching the PC reports, with charts and CSV export.

### Improved
- iPhone client form uses proper date, time and option pickers instead of free text.

### Fixed
- Face ID didn't unlock automatically after the app had been in the background.

## [1.3.0] — 2026-10-12

### New
- **Consent forms and agreements** on the PC and iPhone: privacy, counselling consent, NDIS service agreement,
  sharing information, telehealth and community outings. Sign on screen or record a signed paper copy; PDFs are kept
  with the client and sync between devices. Reminders when a form is missing or expires.
- More intake details on clients (guardian, GP, referrer, goals, needs).

### Fixed
- Connecting Google now records which permissions were actually given and warns if any box was unticked.

## [1.2.0] — 2026-10-12

### New
- **Clarity on the iPhone**, kept in step with the PC through an encrypted hidden folder in Google Drive (Google
  can't read it). Pair with a one-time code shown on the PC.

### Fixed
- Google sign-ins made before the iPhone app could stop refreshing; sync diagnostics added on both apps.

## [1.1.0] — 2026-10-08

### New
- Invoice and receipt PDFs are also saved to your iCloud Drive folders automatically.
- **Resend** invoices and receipts, with an email history on each.

### Improved
- Australian dates (DD/MM/YYYY) everywhere.
- Hermes: setup guide, tidier API keys and clearer connection errors.

## [1.0.0] — 2026-10-08

### New
- First release of **Clarity Desk** for Windows: branded NDIS invoices and receipts, Gmail drafts with the PDF
  attached, clients, session notes with Hermes, reports, encrypted storage and daily encrypted backups.
