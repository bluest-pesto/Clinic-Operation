# Clinic-Operation
10-9-25
Non è PDF file
1. OOA Analysis

The Small Clinic Management System needs to manage patients, doctors, and appointments.
From the requirements, we identify the following objects:

Patient

Attributes: name, ID, age, medical history (appointments).

Operations: schedule appointments, view history.

Chronic Patient (special type of Patient)

Inherits from Patient.

Additional attributes: chronic condition, last check-up date.

Operation: schedule appointment with stricter rules (every 3 months).

Doctor

Attributes: name, ID, specialization, assigned appointments.

Operations: assign appointments, update appointment status, view schedule.

Appointment

Attributes: ID, date, time, reason, status, patientID, doctorID.

Operations: display details, update status.
Clinic

Attributes: collection of patients, doctors, and appointments.

Operations: add/remove patients or doctors, schedule/cancel appointments, display all records.

Relationships:

Patients can have multiple appointments.

Doctors can have multiple appointments.

Appointments are linked to both patients and doctors.

ChronicPatient is a subclass of Patient (single inheritance).
2. Class Design & Inheritance

Inheritance:

ChronicPatient inherits from Patient.

We override the scheduleAppointment method to enforce chronic care rules (reminders for frequent checkups).

This demonstrates polymorphism — the same method (scheduleAppointment) behaves differently for Patient and ChronicPatient.

Encapsulation:

Private data members (e.g., appointment details, doctor schedule) are accessed only through public methods.

This ensures data safety and controlled access.

Use of shared_ptr:

Smart pointers are used to manage object lifetimes safely and avoid memory leaks.
3. Code Walkthrough

Appointment class:

Generates unique appointment IDs automatically (static int nextId).

Stores details like date, time, reason, status, linked patient and doctor IDs.

Supports updateStatus and display.

Patient class:

Stores patient info and medical history.

Defines a virtual method scheduleAppointment (default scheduling logic).

Implements displayInfo to show patient and appointment details.

ChronicPatient class:

Inherits from Patient.

Overrides scheduleAppointment to emphasize more frequent visits.

Adds attributes condition and lastCheckupDate.

Doctor class:

Holds doctor info and assigned appointments.

Can assign new appointments, view them, and update appointment status.

Clinic class:
Manages patients, doctors, and appointments.

Provides functions like addPatient, addDoctor, addAppointment, and cancelAppointmentByID.

Has display functions for listing all entities.

Main function:

Creates sample patients (regular and chronic), doctors, and appointments.

Demonstrates scheduling, canceling, and updating appointments.

Outputs system state before and after modifications.
4. Test Results & Sample Output
Doctor added: John Smith (ID: 101)
Doctor added: Emily Jones (ID: 102)
Patient added: Alice Brown (ID: 201)
Patient added: Bob White (ID: 202)
Appointment ID 1 created.
Appointment ID 2 created.

All patients:
Patient name: Alice Brown
ID: 201
Age: 30
Medical history count: 1
Appointment ID: 1 | Date: 2024-07-15 | Time: 10:00
Reason: Regular Checkup
Status: Scheduled | PatientID: 201 | DoctorID: 101

Patient name: Bob White
ID: 202
Age: 45
Medical history count: 1
Appointment ID: 2 | Date: 2024-07-20 | Time: 14:00
Reason: Skin Rash
Status: Scheduled | PatientID: 202 | DoctorID: 102
Chronic Condition: Diabetes
Last check-up: N/A

Updated appointment ID 2 status to Completed
Appointment ID 1 canceled.
The realest part: LLM usage
1: Prompt: “How should I override scheduleAppointment for ChronicPatient?”
The AI explained that overriding with additional constraints (e.g., 3-month rule) demonstrates inheritance and polymorphism.
2: Prompt: upgrade and fix all mistakes and typos
3: Prompt: demonstrate and explain all lines
The AI help generating alternatives choices for the code

This is a review, no more no less. Peace.
