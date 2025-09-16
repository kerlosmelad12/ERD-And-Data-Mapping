# ERD-And-Data-Mapping

This repository contains several database design cases with their **ERD (Entity Relationship Diagrams)** and **Mapping**.  
The ERD shows the **entities, attributes, and relationships**, while the mapping explains how these are implemented in a relational schema (tables, primary keys, foreign keys, and relationships).

---

## 📌 Case 1: Musicana Records
**Problem Statement:**  
Musicana records want to store information on musicians, instruments, albums, and songs.

### ERD Explanation
- **Entities:** Musician, Instrument, Album, Song.  
- **Relationships:**
  - Musicians ↔ Instruments (Many-to-Many).
  - Songs ↔ Musicians (Many-to-Many).
  - Album ↔ Songs (1-to-Many).
  - Album ↔ Producer (1-to-1, producer is a musician).  
- This design allows flexibility in modeling music production.

### Mapping Explanation
- **Musician(ID, Name, Address, Phone)** → PK: ID.  
- **Instrument(Name, Key)** → PK: Name.  
- **Album(ID, Title, CopyrightDate, ProducerID)** → PK: ID, FK: ProducerID → Musician.  
- **Song(Title, Author, AlbumID)** → PK: Title, FK: AlbumID → Album.  
- **Musician_Instrument(MusicianID, InstrumentName)** → Composite PK, FKs.  
- **Musician_Song(MusicianID, SongTitle)** → Composite PK, FKs.  

### ERD
![Case1 ERD](https://drive.google.com/file/d/1XSyd-YB4bKTvf-w-qcDCeAiz2CKwDFCX/view?usp=sharing)

### Mapping
![Case1 Mapping](https://drive.google.com/file/d/19PZJ3E2weqzPaQckMKMjFSJF0Rlal9-2/view?usp=sharing)

---

## 📌 Case 2: Sales Offices and Properties
**Problem Statement:**  
A real estate firm with sales offices, employees, managers, properties, and owners.

### ERD Explanation
- **Entities:** SalesOffice, Employee, Property, Owner.  
- **Relationships:**
  - SalesOffice ↔ Employee (1-to-Many).
  - Each SalesOffice has one Manager (1-to-1).
  - SalesOffice ↔ Property (1-to-Many).
  - Property ↔ Owner (Many-to-Many, with % owned attribute).  

### Mapping Explanation
- **SalesOffice(OfficeNumber, Location)** → PK: OfficeNumber.  
- **Employee(ID, Name, OfficeNumber, IsManager)** → PK: ID, FK: OfficeNumber → SalesOffice.  
- **Property(ID, Address, City, State, Zip, OfficeNumber)** → PK: ID, FK: OfficeNumber → SalesOffice.  
- **Owner(ID, Name)** → PK: ID.  
- **Property_Owner(PropertyID, OwnerID, Percentage)** → Composite PK, FKs.

### ERD
![Case2 ERD](https://drive.google.com/file/d/1LA_PaCUU76D0TaWvVwGEvrcz00HP4V4V/view?usp=drive_link)

### Mapping
![Case2 Mapping](https://drive.google.com/file/d/1R86zj3rrRk-jofBMDKSvaYhJqNjGZl51/view?usp=drive_link)

---

## 📌 Case 3: General Hospital
**Problem Statement:**  
Hospital with wards, patients, consultants, nurses, and drugs.

### ERD Explanation
- **Entities:** Ward, Patient, Consultant, Nurse, Drug, Drug_Record, Drug_Brand.  
- **Relationships:**
  - Ward ↔ Patient (1-to-Many).
  - Patient ↔ Consultant (1-to-1 for leading consultant, Many-to-Many for examinations).
  - Ward ↔ Nurse (1-to-Many, plus 1-to-1 supervisor).  
  - Nurse ↔ Drug_Record ↔ Patient (to record drug administration).
  - Drug ↔ Drug_Brand (1-to-Many).  

### Mapping Explanation
- **Ward(ID, Name, SupervisorNurseID)** → PK: ID.  
- **Patient(ID, Name, DOB, WardID, ConsultantID)** → PK: ID, FK: WardID → Ward, FK: ConsultantID → Consultant.  
- **Consultant(ID, Name)** → PK: ID.  
- **Examine(PatientID, ConsultantID)** → Composite PK, FKs.  
- **Nurse(ID, Name, Number, Address, WardID)** → PK: ID, FK: WardID → Ward.  
- **Drug(Code, RecommendedDosage)** → PK: Code.  
- **Drug_Brand(Code, BrandName)** → Composite PK, FK: Code → Drug.  
- **Drug_Record(DrugCode, PatientID, NurseID, Time, Date, Dosage)** → Composite PK, FKs.  

### ERD
![Case3 ERD](https://drive.google.com/file/d/1P4m-gCljID8zhVN0-4MrQm5JSrV1TT0V/view?usp=drive_link)


### Mapping
![Case3 Mapping](https://drive.google.com/file/d/1F-ZuVJ3629ev295ml8gmF61VoDHBuCtp/view?usp=drive_link)

---


