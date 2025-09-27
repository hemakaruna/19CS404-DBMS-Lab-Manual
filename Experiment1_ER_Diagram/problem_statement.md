# Experiment 1: Entity-Relationship (ER) Diagram

🎯 **Objective:**  
To understand and apply ER modeling concepts by designing an ER diagram for a City Library system that manages book lending, events, speakers, and room bookings.

---

📚 **Purpose:**  
The purpose of this exercise is to visually represent the structure of a library management database including entities, relationships, attributes, and constraints.

---

# Scenario: City Library Event and Book Lending System

## User Requirements

- Members register with the library and provide contact details.  
- Books are catalogued with unique IDs, titles, authors, and categories.  
- Loans are tracked with loan date, return date, and fines (if overdue).  
- Events are organized by the library with details like event name, type, and date.  
- Members can register for multiple events, and events may have multiple members.  
- Events can have one or more speakers, and speakers may present at many events.  
- Rooms are available in the library, each with capacity and booking history.  
- Bookings are made for rooms either for events or study purposes.  


---

## 📝 Tasks
1. Identify entities, relationships, and attributes.  
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).  
3. Include:  
   - Cardinality & participation constraints  
   - Billing/Fine support for late book returns  
4. Explain:  
   - Why you chose the entities and relationships  
   - How you modeled billing/fines  
5. Submit ER Diagram and Explanation.

---

## Entities and Attributes

- **Member**  
  - MemberID (Primary Key)  
  - Name  
  - Email  
  - Phone  

- **Book**  
  - BookID (Primary Key)  
  - Title  
  - Author  
  - Category  

- **Loan**  
  - LoanID (Primary Key)  
  - LoanDate  
  - ReturnDate  
  - Fine  

- **Event**  
  - EventID (Primary Key)  
  - EventName  
  - EventDate  
  - EventType  

- **Speaker**  
  - SpeakerID (Primary Key)  
  - Name  
  - Topic  

- **Room**  
  - RoomID (Primary Key)  
  - RoomName  
  - Capacity  

- **Booking**  
  - BookingID (Primary Key)  
  - BookingDate  
  - Purpose  

---

## ER Diagram:

![WhatsApp Image 2025-08-29 at 10 39 15_ecfd2c7f](https://github.com/user-attachments/assets/0b472523-d1d1-4aab-a717-a0a98c75ca45)


## Relationships and Constraints

1. **Borrows (Member ↔ Loan ↔ Book)**  
   - Cardinality: Many-to-Many  
   - Participation: Total on Loan, Partial on Member and Book  

2. **Registers (Member ↔ Event)**  
   - Cardinality: Many-to-Many  
   - Participation: Partial for both  

3. **Presents (Event ↔ Speaker)**  
   - Cardinality: Many-to-Many  
   - Participation: Partial for both  

4. **Held In (Event ↔ Room)**  
   - Cardinality: One-to-Many  
   - Participation: Total on Event, Partial on Room  

5. **Books (Room ↔ Booking)**  
   - Cardinality: One-to-Many  
   - Participation: Total on Booking, Partial on Room  

---

## Assumptions
- A book can be borrowed by only one member at a time.  
- Overdue fines apply only when books are returned late.  
- Only registered members can attend events.  
- Rooms may be booked for events or study purposes.  

---

## Design Choices
- **Entities** were chosen to reflect the core operations of the library: Members, Books, Loans, Events, Speakers, Rooms, and Bookings.  
- **Relationships** represent real-world interactions: members borrow books, attend events, speakers present at events, and rooms are booked for usage.  
- **Constraints** ensure valid data: each event must take place in one room, loans must link a member and a book, etc.  

---

## Result
Thus, the ER diagram effectively models the City Library Event and Book Lending System, representing borrowing, event participation, speaker management, and room bookings in a structured database design.

