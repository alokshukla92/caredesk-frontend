# CareDesk — Testing Guide

> Replace `<URL>` with your deployed app URL. Seed demo data from Settings page for a pre-populated clinic.

---

## 1. Clinic Admin Setup
1. Open `<URL>/login` → sign in with Google
2. Register your clinic (name, slug, address, phone)
3. Land on **Dashboard** — see today's stats, revenue, sentiment breakdown

## 2. Add Doctors
1. Go to **Doctors** → click "Add Doctor"
2. Enter name, specialty, hours (`09:00–17:00`), consultation fee
3. Save — doctor is now available for bookings

## 3. Patient Books Appointment (Public — No Login)
1. Open `<URL>/app/book/<your-slug>` (e.g., `/app/book/sanjeevani-clinic`)
2. Pick a doctor, select date & time, enter name + phone
3. Click Book → get token number (e.g., `AS-001`)
4. Confirmation email sent automatically

## 4. Queue Management
1. **Appointments page** — see all today's bookings
2. **Queue page** — move patients: Booked → In-Queue → In-Consultation → Completed
3. **Waiting Room TV** — open `<URL>/app/queue-display/<slug>` (public, no login) — shows live "Now Serving" + waiting list

## 5. Doctor Writes Prescription
1. Click "Start Consultation" on a queued patient
2. Enter diagnosis, add medicines (name, dosage, morning/afternoon/night, duration)
3. Add advice + follow-up date → Save
4. Prescription is viewable and printable with clinic letterhead

## 6. Patient Gives Feedback (Public — No Login)
1. Open `<URL>/app/feedback/<appointment-id>`
2. Rate 1–5 stars, write a comment
3. **Zia AI** auto-detects sentiment (positive/negative/neutral) + extracts keywords
4. Admin sees all feedback with sentiment badges on the **Feedback** page

## 7. Patient Tracks Appointments (Public — No Login)
1. Open `<URL>/app/my-appointments`
2. Enter phone number → see all past & upcoming appointments across clinics
3. View prescriptions, give pending feedback

## 8. Multi-Tenancy
- Log in as a different user → register a second clinic
- Each clinic sees only its own data — doctors, patients, appointments, feedback
- Public booking pages are scoped per clinic via URL slug

---

## Status Flow
```
booked → in-queue → in-consultation → completed
                                     ↘ cancelled / no-show
```

## Demo Patient Phones (after seeding)
`9111111101` to `9111111110`
