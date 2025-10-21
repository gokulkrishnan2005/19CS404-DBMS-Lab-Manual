# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

<img width="958" height="761" alt="image" src="https://github.com/user-attachments/assets/56474a0d-08ef-475c-8d48-eaef8ef4bcd2" />

### Entities and Attributes

| **Entity**     | **Attributes (PK, FK)**                                                                                                        | **Notes**                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------- |
| **Member**     | **PK:** Member\_id <br> Attributes: Name, Membership\_type                                                                     | Stores details of gym members                   |
| **Trainer**    | **PK:** Trainer\_id <br> Attributes: Name, Specialization                                                                      | Stores trainer details                          |
| **Program**    | **PK:** Program\_id <br> Attributes: Program\_name, Description, Schedule                                                      | Training programs offered                       |
| **Session**    | **PK:** Session\_id <br> **FKs:** Member\_id, Trainer\_id, Program\_id <br> Attributes: Session\_type, Session\_schedule       | Represents a training session                   |
| **Payment**    | **PK:** Payment\_id <br> **FKs:** Member\_id, Session\_id <br> Attributes: Payment\_date, Amount, Payment\_type, Reference\_id | Stores payment records for memberships/sessions |
| **Attendance** | **PK:** Attendance\_id <br> **FKs:** Member\_id, Session\_id <br> Attributes: Status                                           | Tracks member attendance in sessions            |

### Relationships and Constraints

| **Relationship**          | **Entities Involved** | **Cardinality**              | **Participation**                     | **Notes**                                                                      |
| ------------------------- | --------------------- | ---------------------------- | ------------------------------------- | ------------------------------------------------------------------------------ |
| **Assigned\_by**          | Member – Trainer      | 1 Trainer : Many Members     | Member (Total), Trainer (Partial)     | Each member must be assigned a trainer; a trainer may train multiple members   |
| **Specified\_course**     | Session – Program     | Many Sessions : 1 Program    | Session (Total), Program (Partial)    | Each session belongs to a program; a program may have multiple sessions        |
| **Specified\_time**       | Member – Session      | 1 Member : Many Sessions     | Member (Partial), Session (Total)     | A member can have many sessions; each session is scheduled for one member      |
| **Amount\_collected**     | Session – Payment     | 1 Session : Many Payments    | Session (Partial), Payment (Total)    | A session may have multiple payments; each payment must be linked to a session |
| **Presence\_in\_session** | Attendance – Session  | Many Attendances : 1 Session | Attendance (Total), Session (Partial) | Tracks attendance per session; each attendance record belongs to one session   |

### Assumptions
- All IDs (Member_id, Trainer_id, Program_id, Session_id, Payment_id, Attendance_id) are primary keys and unique.
- Foreign key relationships ensure referential integrity (e.g., a payment cannot exist without a valid member and session).
- The system assumes each member is assigned at least one trainer and the system records both financial (payments) and non-financial (attendance, schedules) aspects of gym operations.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
y<img width="1009" height="798" alt="image" src="https://github.com/user-attachments/assets/d410adf3-7db1-41cb-98a8-b0860ff54d1e" />


### Entities and Attributes

Entity                         |  Attributes (PK, FK)                                                                      |  Notes        |
|------------------------------|-------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
Book                           |  ISBN (PK), autho, title, edition, category, price, PublisherId (FK)                      |  A Book is linked to a Publisher. ISBN is the unique identifier.                                                             |   
Publisher                      |  PublisherId (PK), Year of publication, name                                              |  The Book entity uses this PK as an FK to show which publisher published it.                                                 |   
Reader                         |  UserId (PK), Email, address, phone no, firstname, lastname, LoginID (FK)                 |  UserId is the unique identifier. Name is split into firstname and lastname (Composite). Phone no is Multi-valued (see note).|   
Authentication System          |  LoginID (PK), password                                                                   |  This PK is used as an FK in the Reader entity to link the login details.                                                    |   
Staff                          |  staff_id (PK), name                                                                      |  This identifies library staff members.                                                                                      |   
Reserve/Return (Relationship)  |  Reg_no (PK), UserId (FK), ISBN (FK), Reserve date, Due date, Return date, staff_id (FK)  |  This is a transaction table that replaces the Reports entity and links the Reader and Book. Reg_no is the unique transaction ID.|

### Relationships and Constraints

Relationship                                   |  Cardinality  |  Participation   |  Notes                                                   |                                    
-----------------------------------------------|---------------|------------------|------------------------------------------------------------------------------------------|
Reader reserves Books                          |  1:N          |  Reader: Total   |  A reader can reserve many books; each book is reserved by only one reader.               |   
Publisher publishes Books                      |  1:N          |  Book: Total     |  A publisher can publish many books; each book is published by only one publisher.         |  
Staff keeps track of Readers                   |  M:N          |  Staff: Partial  |  Multiple staff can track multiple readers; tracking is not mandatory for all.              | 
Staff maintains Reports                        |  1:N          |  Staff: Total    |  Each staff maintains multiple reports; every report is maintained by one staff member.      |
Staff maintains Books                          |  1:N          |  Staff: Partial  |  Each staff maintains multiple books; not all staff may maintain books.                      |
Authentication System provides login to Staff  |  1:N          |  Staff: Total    |  Each authentication system provides login to multiple staff members; every staff must login.|
### Assumptions
- Each reader must have a valid login credential in the authentication system before borrowing or reserving books.

- A book can be reserved by only one reader at a time, but may be borrowed multiple times by different readers over time.

- Phone number is a multi-valued attribute for readers, allowing multiple contact numbers per user.

- Overdue fines are calculated automatically based on the difference between the return date and due date.

- Each reservation/return transaction (Reg_no) uniquely identifies one borrowing instance and links one reader to one book.

- Every book must belong to a single publisher, but one publisher can publish many books.

- Staff members are responsible for maintaining book records, managing reservations, and assisting readers, though not all staff handle all functions.

- Each staff member also logs in using the authentication system, ensuring secure and authorized access.

- All events are organized by the library and may have one or more speakers/authors, but each event must be assigned to a room.

- Rooms can be booked either for study purposes or for cultural events, not simultaneously for both activities.

- Deletion of a reader record is restricted until all borrowed books are returned and pending fines are cleared.

- System ensures referential integrity, meaning no orphan books, readers, or transactions exist without proper linkages to their related entities.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
