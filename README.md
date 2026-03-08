# 🏨 Hotel Management System

A **Spring Boot + Spring Data JPA + Oracle Database** based backend application to manage hotel rooms and customer bookings.

This project implements a **3-Layer Architecture**:

* **Controller Layer** – Handles HTTP requests
* **Service Layer** – Contains business logic
* **Repository Layer** – Handles database operations using Spring Data JPA

---

# 📌 Technologies Used

* Java
* Spring Boot
* Spring Data JPA
* Oracle Database
* Maven
* REST API
* Git & GitHub

---

# 📂 Project Structure

```
com.hotelmanagement

controller
    RoomController
    BookingController

service
    RoomService
    BookingService

service.impl
    RoomServiceImpl
    BookingServiceImpl

repository
    RoomRepository
    BookingRepository

entity
    Room
    Booking

HotelManagementApplication
```

---

# 🧩 Modules

## 1️⃣ Room Management

Manages hotel rooms including room type, price, and availability.

### Room Fields

| Field      | Description                      |
| ---------- | -------------------------------- |
| roomId     | Primary Key                      |
| roomNumber | Unique Room Number               |
| roomType   | Single / Double / Deluxe / Suite |
| price      | Price per day                    |
| status     | Available / Occupied             |

### Room APIs

| Method | API           | Description    |
| ------ | ------------- | -------------- |
| POST   | `/rooms`      | Add Room       |
| GET    | `/rooms`      | Get All Rooms  |
| GET    | `/rooms/{id}` | Get Room by ID |
| PUT    | `/rooms/{id}` | Update Room    |
| DELETE | `/rooms/{id}` | Delete Room    |

---

## 2️⃣ Booking Management

Handles customer room bookings.

### Booking Fields

| Field         | Description                  |
| ------------- | ---------------------------- |
| bookingId     | Primary Key                  |
| customerName  | Customer Name                |
| customerPhone | Phone Number                 |
| checkInDate   | Check-in Date                |
| checkOutDate  | Check-out Date               |
| roomId        | Foreign Key referencing Room |

### Booking APIs

| Method | API              | Description       |
| ------ | ---------------- | ----------------- |
| POST   | `/bookings`      | Create Booking    |
| GET    | `/bookings`      | Get All Bookings  |
| GET    | `/bookings/{id}` | Get Booking by ID |
| PUT    | `/bookings/{id}` | Update Booking    |
| DELETE | `/bookings/{id}` | Cancel Booking    |

---

# 🗄️ Database Schema

## Room Table

```
CREATE TABLE ROOM (
ROOM_ID NUMBER PRIMARY KEY,
ROOM_NUMBER VARCHAR2(20),
ROOM_TYPE VARCHAR2(20),
PRICE NUMBER,
STATUS VARCHAR2(20)
);
```

## Booking Table

```
CREATE TABLE BOOKING (
BOOKING_ID NUMBER PRIMARY KEY,
CUSTOMER_NAME VARCHAR2(100),
CUSTOMER_PHONE VARCHAR2(20),
CHECKIN_DATE DATE,
CHECKOUT_DATE DATE,
ROOM_ID NUMBER,
CONSTRAINT FK_ROOM
FOREIGN KEY (ROOM_ID)
REFERENCES ROOM(ROOM_ID)
);
```

---

# ⚙️ Application Configuration

Example `application.properties`:

```
spring.datasource.url=jdbc:oracle:thin:@localhost:1521:xe
spring.datasource.username=system
spring.datasource.password=oracle

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

---

# 🚀 Running the Application

1. Clone the repository

```
git clone https://github.com/yourusername/hotel-management-system.git
```

2. Open the project in **Eclipse / IntelliJ**

3. Configure **Oracle Database**

4. Run:

```
HotelManagementApplication.java
```

5. Test APIs using **Postman**

---

# 📬 Example API Request

### Create Room

```
POST /rooms
```

```
{
  "roomId":1,
  "roomNumber":"101",
  "roomType":"Deluxe",
  "price":3000,
  "status":"Available"
}
```

---

# 👨‍💻 Author

**Deepak Kumar**

BTech Computer Science
Full Stack Developer
