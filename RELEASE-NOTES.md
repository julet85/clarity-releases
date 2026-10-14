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

## [1.17.0] — 2026-10-14

### Changed
- **NDIS service agreement, version 2.0**, following the NDIS guidance on making a service agreement. It now covers
  who it's for and who can help them (nominee, family, advocate); the supports, the plan budget they come from and the
  participant's goals; **how and when** they're delivered (who, in person/telehealth, usual schedule); **cost** with
  notice before any price change; **how the provider is paid** (worded for self-, plan- or NDIA-managed plans);
  cancellations (and that the participant is never charged when the provider cancels); **important dates and
  reviews**; both parties' responsibilities; **the participant's rights**; **what to do if something goes wrong**
  (provider, NDIS Commission, NDIA, independent advocacy); changes and ending; privacy. It says it doesn't limit the
  NDIS Code of Conduct, can be explained or given in another format, and asks the participant to confirm they had the
  chance to ask questions. The GST sentence follows your GST registration. Clients with the old version are flagged to
  re-sign.

### Fixed
- Consent PDFs failed to generate when a heading contained an apostrophe.

## [1.16.1] — 2026-10-13

### Fixed
- **iPhone: online bookings now come straight from Google Calendar.** The iPhone's request to Calendar was
  rejected ("Google: Bad Request") because the time zone in it (+08:00) wasn't encoded properly, so new bookings
  only appeared after the PC had picked them up. The same fix applies to fetching Meet transcripts and to sync's
  file listing.
- **iPhone: really back where you left off.** Leaving the app still locks it straight away (the keys are dropped and
  Face ID is needed), but the open page is no longer emptied while locked — emptying it made iOS close pages opened
  from a list (like a session note), so you landed back on the list. *Lock now* in Settings still clears everything.

## [1.16.0] — 2026-10-13

### New
- **Audit log** (Settings → Audit log, and *Audit log* on each client's Details tab). Every view, change, email and
  export of a client record — client details, session notes, invoices and their PDFs, files, appointments, consent
  forms, CSV exports, backups, sign-ins — is recorded with the date and time, **who** was signed in, **which device**
  (PC or iPhone) and the client. Filter by views / changes / exports / sign-ins, device or text, and export to CSV for
  an audit. Entries can't be edited or deleted; the iPhone's entries reach the PC with the next sync.
- **Billing sign-in** (Settings → People who can sign in). Give a bookkeeper their own password: they can do
  invoices, payments, appointments and reports, but can't open session notes, transcripts, Hermes, consent forms,
  clinical client details (referral reason, goals, needs, GP) or files other than receipts, and can't change
  settings. Refused attempts are logged.
- **Record retention.** Each client shows *Keep records until* (7 years after the last contact, or until a child
  turns 25). Session notes, activity notes and record files (forms, referrals, reports, plans, letters, receipts)
  can only be deleted within 24 hours of adding them — for mistakes. Copies of ID documents and "Other" files can
  be deleted at any time.
- **Privacy & security** in Settings: where client information is stored, how it's encrypted and who can see it.
  The full statement (architecture, encryption at rest and in transit, data flows, APP mapping, retention, ATO
  invoicing) is in docs/PRIVACY-AND-SECURITY.md.

### Changed
- **Privacy & collection notice, version 2.0.** It now tells clients exactly where their information is kept (on
  your devices in Australia; encrypted copies in Google Drive; appointment times with their name and email in Google
  Calendar; emails via Gmail; session addresses to Google Maps) and has an **optional box for the AI writing
  assistant**. Existing clients are flagged to re-sign it.
- **Hermes only for clients who said yes:** the assistant now runs only for clients who ticked the AI box on the new
  notice (version 1 told clients their information isn't given to AI services).
- **Invoices follow the ATO rules for your GST status** (new switch: Settings → Business details → *Registered for
  GST*, off by default). Not registered: titled *Invoice*, no GST line, and "No GST is charged: … is not registered
  for GST" (the old line wrongly called the supplies "GST-free under the GST Act"). Registered: titled *Tax invoice*
  with the GST line and "GST-free supply: NDIS supports under the participant's plan". Invoices already issued keep
  their wording. Same on the iPhone and in the emails.
- The invoice wizard's service-agreement reminder only mentions the ATO when you're registered for GST.

## [1.15.1] — 2026-10-13

### Fixed
- **iPhone: back where you left off.** Switching to another app and back no longer drops you on the Home page —
  after Face ID you're on the same tab, page and form. The lock screen now covers everything (open forms
  included) while locked.
- iPhone: a session note being typed when you switch apps is saved before Clarity locks (it could be lost).
- **iPhone: online bookings not showing.** The iPhone reads new bookings straight from Google Calendar; if that
  fails (for example the Calendar API isn't switched on for the iPhone's Google sign-in), it now says so on the bell
  and on Appointments, with Google's reason, instead of failing silently. Until it's fixed, bookings still arrive
  once the PC has picked them up and synced.

## [1.15.0] — 2026-10-13

### New
- **Files for each client** (PC: the client's new *Files* tab; iPhone: the *Files* card on the client's page).
  Keep referrals, completed forms, receipts, reports, NDIS plans, letters and ID documents with the client:
  - **Add** on the PC by dragging files onto the page or with *Add files…*; on the iPhone from Files, the photo
    library, or by **scanning** a paper document with the camera.
  - Each file has a **type** (Completed form, Referral, Report / assessment, NDIS plan, Receipt, Letter, ID document,
    Other) — Clarity guesses it from the file name and you can change it from the drop-down — and a name you can edit.
  - Each shows **when it was added, by whom and on which device** (e.g. "added 13 Oct 2026, 9:14am by Joanne on the
    iPhone"), its size and file type. Filter the list by type.
  - **Open** them on the PC (PDFs and photos inside Clarity, Word/Excel and others in their own app; or save a copy)
    and on the iPhone (Quick Look).
  - **Delete** them (on both devices).
  - Adding a file shows in the client's Activity.
- PDFs, photos and Word/Excel/PowerPoint/Pages documents, up to 20 MB each. Program files are refused.

### Security
- Files are stored encrypted with the client's record and travel to the iPhone the same way invoice PDFs do —
  encrypted before they reach Google Drive. A file opened in another app is a temporary copy that's wiped when
  Clarity locks or closes (on the iPhone, when the preview closes).

### Improved
- Sync is ready for future additions: changes for a kind of record a device doesn't know yet are kept until it's
  updated, instead of being skipped.

## [1.14.2] — 2026-10-13

### Improved
- **iPhone appointments:** the buttons are grouped like on the PC — *Remind* and *Change* side by side, *Completed* and
  *No-show* side by side, and *Cancel* / *Delete* as small red links at the bottom. An in-person session's address
  is a card that opens directions in Apple Maps. Dates show the day too ("Thursday 15 October"), and in-person
  sessions have a people icon instead of the pin that looked like an anchor.
- **iPhone new invoice:** choose the client first; the session, times and travel then appear already filled in (no more
  1:15am–1:15am). *Save invoice* is a proper button with *Preview PDF* under it.
- **iPhone session notes:** the client and date are tidy rows (the stray grey shapes behind them are gone).

### Fixed
- iPhone Home said "Synced in 0 seconds"; it now says "Synced just now".
- iPhone: an invoice said "Support" for counselling sessions; it now shows the session type.

## [1.14.1] — 2026-10-13

### Improved
- **A tidier, more polished PC app.** A pass over every screen:
  - Appointment and invoice panels group their buttons: the main action on top, everyday actions in a neat two-column
    grid, and *Cancel* / *Delete* as quiet red links at the bottom, so they're harder to hit by mistake.
  - Settings has a jump bar of its sections (Gmail, Appointments, TeslaMate, Google Maps, Backups…) that stays at
    the top while you scroll.
  - Icons in option buttons (Google Meet / Phone / In person) now line up with their text; drop-down menus have a
    matching arrow; boxes are the same height across a row.
  - Home: the to-do list keeps invoice numbers on one line; the "Today's appointments" card no longer repeats "Today".
  - The invoice wizard's session date says *From the appointment* underneath instead of squeezing the label, and the
    invoice summary no longer stretches to the bottom of the page.
  - Reports: the date range stays on one line and the travel log no longer splits dates and invoice numbers.
  - Appointments: the Counselling / Support work filter lines up with the tabs; appointment rows line up their
    times and highlight on hover.
  - Matching thin scrollbars throughout.

### Fixed
- The Session notes list was indented unevenly (it picked up the notifications panel's spacing).
- An invoice's panel said "Support" for counselling sessions; it now shows the session type.

## [1.14.0] — 2026-10-13

### New
- **iPhone: plan the route with Apple Maps.** In the iPhone's invoice form (Travel) and on a past appointment, list
  the stops in the order you drove and Apple Maps works out each leg and the total driving distance — no key needed.
  The route is saved on the appointment, so the PC shows it on the session's map too.
- **iPhone uses routes saved on the PC.** If a session's route was worked out on the PC (Get from Tesla or Google
  Maps), the iPhone's invoice form fills in the kilometres and route from it.

### Notes
- Tesla trips are still read on the PC only: TeslaMate's database login stays on the PC (home network).

## [1.13.1] — 2026-10-13

### Fixed
- **Hermes assistant:** the question box had white text on a white background, so typing was invisible.
- The assistant now works like a chat: the conversation scrolls in the middle, the message box is at the bottom
  (Enter to send, Shift+Enter for a new line), and you can **reply to Hermes** — follow-ups include the last few
  exchanges so its questions can be answered. Replies show headings, lists and bold properly.

### Security
- What you type to Hermes (and the earlier exchanges sent with a follow-up) now goes through the same name/number
  hiding as the note itself. Before, only the note was redacted.

## [1.13.0] — 2026-10-13

### New
- **Reports: counselling vs support work.** One slim bar under the headline figures shows how the period splits
  between counselling and NDIS support work, with each side's income, hours and sessions (PC Reports and iPhone
  Insights). The accountant CSV export has a new *Type* column.

## [1.12.0] — 2026-10-13

### New
- **Sessions up to 8 hours.** Appointment lengths now go from 30 minutes to 8 hours (PC and iPhone), for full-day
  NDIS supports; the usual length in Settings goes up to 8 hours too.
- **Past appointments from older invoices.** On a client's Details tab, *Create past appointments* turns each
  invoice that has no appointment into a completed appointment on its date and times (or links the appointment
  already on that day). These stay in Clarity only — nothing is added to Google Calendar and the client isn't
  emailed. With TeslaMate connected, each session is matched to the Tesla's trips and clear matches are saved as
  the session's route and map; you see the billed km next to the Tesla km. Invoices themselves don't change.
- **Record a past session by hand.** *New appointment* now accepts past dates: a session that has already finished
  is recorded in Clarity only (no Google Calendar, nobody emailed), you can pick that day's invoice to link it to,
  and the appointment opens straight on *Session travel* so you can add the km from Tesla or Google Maps.
  Past appointments without an invoice also offer *Link to invoice …* for that day's invoice.
- **Counselling or NDIS support work.** Every appointment and invoice has a session type, shown as a coloured label
  and filterable under Appointments. Video and phone sessions default to counselling and in-person to support work;
  change it on the appointment (until it's invoiced). Counselling invoices use their own line wording and rate
  (Settings → Session types), and a client can have their own counselling rate (Edit details → Billing). Existing
  invoices count as support work.
- **Delete appointments** (PC and iPhone). Choose whether the client is told (Google emails a cancellation) or not;
  it's removed from Google Calendar too so it doesn't come back. Invoiced sessions can't be deleted — void the
  invoice first. Session notes are kept.

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
