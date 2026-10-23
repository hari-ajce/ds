# 🏥 PulseTrack | Hospital Bed, ICU & Ventilator Inventory Manager

A high-performance, responsive web application designed for hospitals to rapidly track, allocate, and release specialized equipment and beds across different wards and floors during peak hours. 

Hosted directly via GitHub Pages using a single self-contained index.html file with built-in data structures and local browser persistence.

---

## 🧠 Core Data Structures Implemented

To handle efficient emergency allocations and constant-time lookups, the system relies on fundamental computer science data structures:

1. Max-Heap / Priority Queue: Automatically manages the emergency patient waitlist. Patients with higher triage urgency scores (1–10) are prioritized for automatic reallocation when beds are released.
2. HashMap: Provides $O(1)$ constant-time lookups for bed identification numbers (ICU-101, GEN-301, etc.) when updating statuses or discharging patients.
3. Hierarchical Tree / Ward Relational Model: Groups individual beds into designated wards and units (ICU Ward A, General Ward 1) for structured facility oversight.

---

## ✨ Features

- Live Inventory Dashboard: Real-time summary badges tracking ICU Occupancy percentage, Free Ventilators, and Total Free Beds.
- Interactive Ward Filters: Instant filtering switches (All, ICU, General) to isolate specific hospital wings.
- Emergency Triage Allocation: Assigns patients based on urgency scores; overflows are automatically routed to the priority waitlist queue.
- **Persistent Storage (localStorage)**: All allocations, discharges, and queue changes are automatically saved in your browser so data isn't lost on refresh.
- System Reset: Quick option to clear stored testing data and re-initialize default wards.

---

## 🚀 How to Run on GitHub Pages

1. Create a repository on GitHub (e.g., hospital-inventory-manager).
2. Upload the **index.html** file containing the full frontend and data structures logic.
3. (Optional) Upload **README.md** (this file).
4. Go to your repository Settings > Pages.
5. Under Build and deployment, select your main branch and / (root) folder, then click Save.
6. Access your live website at: https://<your-github-username>.github.io/<repository-name>/

---

## ☕ Java Backend Model (HospitalManager.java)

For academic or backend architecture demonstrations, a companion Java implementation modeling the same data structures (PriorityQueue and HashMap) is included in the project documentation:

`java
// Example snippet from backend logic
Map<String, Bed> bedInventory = new HashMap<>();
PriorityQueue<Patient> waitlist = new PriorityQueue<>(
    (a, b) -> Integer.compare(b.urgencyScore, a.urgencyScore)
);
