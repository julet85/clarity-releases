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

## [1.11.1] — 2026-10-13

### Fixed
- Settings → TeslaMate / Google Maps: the example text in empty boxes (like "192.168.1.202") looked like a real value,
  so **Test connection** stayed greyed out. Examples are now in italics and start with "e.g.", and the test buttons
  light up as soon as you type (they save before testing).

## [1.11.0] — 2026-10-13

### New
- **Plan the route with Google Maps** when TeslaMate isn't available: type the stops in the order you drove (it
  starts with the client's address), and Google works out each leg and the total driving distance. Reorder or remove
  stops, check the map, then use it. Available in the invoice wizard and on any past appointment.
- **A map of each session** under Appointments → *Session travel*: the kilometres, the route and a map — for a Tesla
  route it's the actual path driven (from TeslaMate's GPS points); for a Google Maps route, the roads between the
  stops. On the iPhone the map is drawn with Apple Maps.
- The route is saved on the appointment, so invoicing that session fills in the kilometres and route by itself.
- Settings → **Google Maps** for the API key, with a test (see docs/GOOGLE-MAPS.md). Without a key, Tesla routes
  show as a simple outline and nothing is sent to Google.

### Changed
- The TeslaMate read-only login also needs to read `positions` for the route map (one extra GRANT, docs/TESLAMATE.md).

## [1.10.0] — 2026-10-13

### New
- **Every invoice belongs to an appointment.** The invoice wizard (PC and iPhone) starts with *Which session is this
  for?*: pick one of the client's appointments from the last 4 months that hasn't been invoiced. The date comes from
  the appointment, each appointment can be invoiced only once (unless that invoice is voided), and a past "booked"
  session is marked completed. Older invoices are unchanged.
- **Not in the calendar?** Choose *Log a past session*: it's added to Appointments as completed (no invitation is
  sent) and the invoice is linked to it.
- Appointments show *invoiced CA-…*, and the appointment opens its invoice.
- **Kilometres from your Tesla (PC).** With TeslaMate connected (Settings → TeslaMate), **Get km from Tesla** in the
  invoice wizard reads the trips around the session and ticks the ones that start and end in the client's suburb
  during it — your commute there and home is left out. You see every trip and confirm before anything is billed;
  the route (e.g. Bedfordale → Armadale → Bedfordale) fills in too. Read-only, from the PC on your home network.

## [1.9.1] — 2026-10-12

### Fixed
- **Restart to update** showed a ".NET Framework — unhandled exception 'master'" box. Clarity now closes itself
  cleanly first, and the installer starts a few seconds later and reopens Clarity when it's done.
- Before installing, Clarity checks the downloaded update once more and refuses it if the file has changed.

## [1.9.0] — 2026-10-12

### New
- **Activity on each client** (PC: below the client's details; iPhone: on the client page). Log a call, text, email
  or quick note in seconds, e.g. "Tried calling Rachel — no answer". The time fills in as now and can be changed.
- One-tap quick notes: *No answer*, *Left voicemail*, *Spoke with …*, *Texted*, *Emailed*.
- The timeline also shows what Clarity already knows about the client: invoices, payments, emails, signed forms,
  appointments, reminders and session notes. Switch to **Notes only** to see just your own entries.
- Edit or delete your own entries; they sync between the PC and iPhone like everything else.

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
