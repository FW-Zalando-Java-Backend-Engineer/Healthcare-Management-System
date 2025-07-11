# 📜 **Assignment Brief**

## 🏥 Healthcare Management System with Spring Boot + MongoDB

**Goal:**
Build a RESTful Healthcare Management System using Spring Boot and MongoDB.

You will design **multiple domain models** representing a simplified healthcare domain (patients, doctors, appointments, etc.), enforce **validation rules**, and implement **custom MongoDB queries**.

---

## ✅ 1️⃣ 📚 Domain Overview

Your system will manage:

* **Patients**
* **Doctors**
* **Appointments**
* **Medical Records**

Each of these will be separate **MongoDB collections** with clear relationships.

---

## ✅ 2️⃣ 💾 Database

* Use **MongoDB** as your data store.
* Use **Spring Data MongoDB** with `MongoRepository`.
* Configure connection in `application.properties` or `application.yml`.

---

## ✅ 3️⃣ 🗂️ Suggested Package Structure

```
com.example.healthcare
  ├── model
  │     ├── Patient.java
  │     ├── Doctor.java
  │     ├── Appointment.java
  │     └── MedicalRecord.java
  ├── repository
  │     ├── PatientRepository.java
  │     ├── DoctorRepository.java
  │     ├── AppointmentRepository.java
  │     └── MedicalRecordRepository.java
  ├── controller
  │     ├── PatientController.java
  │     ├── DoctorController.java
  │     ├── AppointmentController.java
  │     └── MedicalRecordController.java
  └── service
        ├── PatientService.java
        ├── DoctorService.java
        ├── AppointmentService.java
        └── MedicalRecordService.java
```

✅ **Hint:** This is a suggestion. You may simplify or expand it.

---

## ✅ 4️⃣ 🎯 Functional Requirements

### **A. Patients**

* Fields:

  * id (String / @Id)
  * name (required)
  * age (positive integer)
  * gender (enum or String, required)
  * email (valid email)
  * phoneNumber (10–15 characters)
* Validation:

  * NotBlank, Email, Pattern
* CRUD Endpoints:

  * Create patient
  * List all patients
  * Get by ID
  * Update
  * Delete
* **Custom Query Requirement:**

  * Find patients by age > given value
  * Find patients by gender

---

### **B. Doctors**

* Fields:

  * id
  * name (required)
  * specialty (required)
  * yearsOfExperience (min 0)
  * email
* Validation:

  * NotBlank, Min, Email
* CRUD Endpoints
* **Custom Query:**

  * Find doctors by specialty
  * Find doctors with experience > X years

---

### **C. Appointments**

* Fields:

  * id
  * patientId (reference)
  * doctorId (reference)
  * date (ISO date)
  * reason
  * status (Scheduled / Completed / Cancelled)
* Validation:

  * NotNull for patientId and doctorId
  * FutureOrPresent date
* Endpoints:

  * Create appointment
  * Get appointments for patient
  * Get appointments for doctor
* **Custom Query:**

  * Find appointments by status
  * Find appointments between dates

---

### **D. Medical Records**

* Fields:

  * id
  * patientId
  * diagnosis
  * treatment
  * createdDate
* Validation:

  * NotBlank fields
  * PastOrPresent createdDate
* Endpoints:

  * Create medical record
  * Get all records for patient

---

## ✅ 5️⃣ 🔍 Validation Requirements

* Use **javax.validation** annotations:

  * @NotBlank
  * @Email
  * @Pattern
  * @Min
  * @FutureOrPresent
  * @PastOrPresent
* Implement **@Valid** in controllers to enforce validation.

---

## ✅ 6️⃣ 🗃️ MongoRepository and Custom Queries

* Use **extends MongoRepository** for each entity.
* Create **custom finder methods** like:

  * `findBySpecialty(String specialty)`
  * `findByAgeGreaterThan(int age)`
  * `findByStatus(String status)`
  * `findByDateBetween(LocalDate start, LocalDate end)`
* At least **one @Query** annotation per repository (example: case-insensitive search).

---

## ✅ 7️⃣ 🌐 REST Endpoints

Design endpoints such as:

```
POST /patients
GET /patients
GET /patients/{id}
GET /patients/age-above/{age}
GET /patients/gender/{gender}
```

```
POST /doctors
GET /doctors/specialty/{specialty}
GET /doctors/experience-above/{years}
```

```
POST /appointments
GET /appointments/patient/{patientId}
GET /appointments/status/{status}
GET /appointments/between?start=2024-06-01&end=2024-07-01
```

```
POST /records
GET /records/patient/{patientId}
```

---

## ✅ 8️⃣ 💡 BONUS

- ✔️ Add a **service layer** between controllers and repositories.

- ✔️ Add **exception handling** (e.g., @ControllerAdvice).


---

## ✅ 9️⃣ 📌 Non-Functional Requirements

* Use **Spring Boot 3.x** or higher
* Use **Spring Data MongoDB**
* Validate all input
* Clear package structure
* Use Lombok (optional)
* Include README with:

  * Setup instructions
  * How to run

---

## ✅ 1️⃣0️⃣ 💼 Submission

Submit:

* Full Spring Boot project (ZIP or Git link)
* Must include:

  * Source code
  * README
  * Example requests (e.g., Postman collection or curl samples)

✅ Deadline: *\[Set your deadline here]*

---

## ✅ 1️⃣1️⃣ 🎯 Evaluation Criteria

* Correctness: models, validation, custom queries
* Code quality and structure
* Clear API design
* Proper use of MongoRepository
* Validation annotations working
* Extra credit for DTOs, services, error handling

---

## ✅ 1️⃣2️⃣ 🎓 Learning Objectives

By the end of this assignment you will be able to:

* Design a REST API in Spring Boot
* Model healthcare data in MongoDB
* Use Bean Validation for input correctness
* Build custom MongoDB queries
* Structure a maintainable Spring Boot app

---

## 🚀 **Get started!**

* 1️⃣ Plan your models and fields.
* 2️⃣ Set up MongoDB connection.
* 3️⃣ Create repositories.
* 4️⃣ Implement validation.
* 5️⃣ Expose REST endpoints.
* 6️⃣ Test your API!

---

✅ **Need help?**

* Ask in Slack.
* Meet in breakout rooms with your instructor.

---

**📌 Good luck building your Healthcare Management System!**
*We can't wait to see your creative designs and thoughtful queries.*

---
