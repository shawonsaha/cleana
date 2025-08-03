# 🧼 Product Requirements Document (PRD)

**Product Name:** Cleana
**Platform:** Mobile-Responsive Web App
**Framework:** Next.js (with TailwindCSS and Supabase)
**Target Users:** Hotel/hostel supervisors and cleaning staff

---

## 📌 Objective

To streamline the assignment, monitoring, and reporting of room cleaning tasks in hospitality environments. This digital solution replaces traditional whiteboards or paper-based workflows with a responsive, real-time dashboard optimized for mobile use.

---

## 🎯 User Roles

### 1. **Supervisor**

* Assign rooms to cleaners
* Monitor cleaning progress
* Leave remarks
* View cleaner performance

### 2. **Cleaner**

* View assigned tasks
* Update room cleaning status
* Add remarks or notes (optional)

---

## 🧩 Functional Modules

### 🟩 1. Room Visualization & Status

* Rooms grouped by:

  * **Wings**: South Wing, Right Wing
  * **Floors**: Floor 1, Floor 2

* Each room box displays:

  * Assigned cleaner (with profile pic or name)
  * Current cleaning status
  * Cleaning priority (color coded)
  * Remarks (if any)

#### Room Status Types:

* 🟡 **Occupied – Normal clean**
* 🔴 **Checkout – Empty – Immediate full clean (New check-in expected)**
* 🟠 **Partial clean – Some beds empty**
* ✅ **Cleaned (Box turns green)**

#### Priority Levels:

* 🔺 **High:** Upcoming guest, fully/partially empty
* ⬆️ **Medium:** Fully empty, no upcoming reservation
* 🔻 **Low:** Fully occupied, needs general cleaning

---

### 🧑‍🔧 2. Supervisor Interface

* **Batch Assign**

  * Select multiple rooms
  * Assign to a cleaner

* **Cleaner Performance Dashboard**

  * Track each cleaner’s task count & completion rate
  * Reward / Scoring metrics per cleaner

* **Remarks Panel**

  * Supervisor can leave notes
  * Remarks visible to assigned cleaner

---

### 🧹 3. Cleaner Overview Page

* List of assigned rooms
* Filter by:

  * Floor
  * Status (pending / in-progress / done)

* Profile picture display
* “Mark as Cleaned” button for each room
* Optional: Add notes/comments

---

## 🖥️ Pages & Routing (Next.js App)

| Route              | Description                                 |
| ------------------ | ------------------------------------------- |
| `/login`           | Auth screen for supervisor or cleaner       |
| `/dashboard`       | Supervisor control panel                    |
| `/cleaner/[id]`    | Cleaner-specific dashboard                  |
| `/room/[id]`       | Room detail with current status + update UI |
| `/history`         | Cleaning logs (by room/cleaner/date)        |

---

## 🧱 Key Components

### `<RoomBox />`

* Displays: Room number, status color, cleaner, remarks
* Color-coded
* Clickable to update or assign

### `<CleanerCard />`

* Name + profile picture
* Tasks summary
* Completion percentage

### `<BatchAssignModal />`

* Multi-select rooms
* Select cleaner
* Confirm assignment

### `<RemarksModal />`

* Text input per room
* Read-only for cleaner, editable for supervisor

---

## 🛠️ Tech Stack

| Layer      | Tech                                   |
| ---------- | -------------------------------------- |
| Frontend   | Next.js (App Router)                   |
| Styling    | TailwindCSS + Shadcn                   |
| Backend    | Supabase (Auth, DB, Storage, Realtime) |
| State Mgmt | React Context or Zustand (lightweight) |
| Animations | Framer Motion (for transitions)        |

---

## 🛡️ Access Control

| Feature             | Supervisor | Cleaner      |
| ------------------- | ---------- | ------------ |
| View all rooms      | ✅          | ❌            |
| Assign cleaner      | ✅          | ❌            |
| Mark as cleaned     | ❌          | ✅            |
| View personal tasks | ❌          | ✅            |
| View remarks        | ✅          | ✅            |
| Leave remarks       | ✅          | ✅            |

---

## 🧪 Cleaning Flow Logic

1. Supervisor views dashboard with current statuses
2. Selects rooms for cleaning & assigns to cleaner
3. Cleaner logs in → sees only their assigned tasks
4. Upon completion, cleaner marks room as “Cleaned”
5. Room box changes to green in the dashboard
6. Optional: remarks or scoring by supervisor

---

## 📱 Mobile Responsiveness Design Notes

* Optimized for vertical layout
* Sticky bottom navigation (Cleaner view)
* Grid layout that stacks rooms in 2 columns
* Full-screen modals for assignments & updates

---

## 📈 Future Enhancements (Post-MVP)

* AI Agent for auto-assignment (currently excluded)
* PWA support for offline task queue
* Notifications for task updates
* Cleaner performance analytics export
