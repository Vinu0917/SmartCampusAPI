# Smart Campus — Sensor & Room Management API

## Overview

This is a RESTful API built for the University of Westminster 
5COSC022W Client-Server Architectures coursework. It manages 
Rooms and Sensors across a university campus.

Built using JAX-RS (Jersey) on an embedded Grizzly HTTP server. 
All data is stored in-memory using ConcurrentHashMap. 
No database is used.

---

## How to Build and Run

### Prerequisites
- JDK 11 or higher
- NetBeans IDE
- Maven (built into NetBeans)

### Steps

**1. Clone the repository**
git clone https://github.com/YourUsername/SmartCampusAPI.git

**2. Open in NetBeans**
- File → Open Project
- Navigate to the cloned folder → Click Open

**3. Build the project**
- Right-click the project → Clean and Build
- Maven will download all dependencies automatically

**4. Run the server**
- Right-click Main.java → Run File
- Console will show:
Smart Campus API started!
Discovery endpoint: http://localhost:8080/api/v1
Press ENTER to stop the server.

**5. Test the API**
- Open Postman or browser
- Go to: http://localhost:8080/api/v1

---

## Sample curl Commands

### 1. Discovery endpoint
curl http://localhost:8080/api/v1

### 2. Get all rooms
curl http://localhost:8080/api/v1/rooms

### 3. Create a new room
curl -X POST http://localhost:8080/api/v1/rooms 
-H "Content-Type: application/json" 
-d '{"id":"HALL-01","name":"Main Hall","capacity":200}'

### 4. Filter sensors by type
curl http://localhost:8080/api/v1/sensors?type=CO2

### 5. Add a sensor reading
curl -X POST http://localhost:8080/api/v1/sensors/TEMP-001/readings 
-H "Content-Type: application/json" 
-d '{"value": 23.7}'

### 6. Delete a room that has sensors (returns 409)
curl -X DELETE http://localhost:8080/api/v1/rooms/LIB-301

### 7. Create sensor with invalid roomId (returns 422)
curl -X POST http://localhost:8080/api/v1/sensors 
-H "Content-Type: application/json" 
-d '{"id":"TEMP-999","type":"Temperature","status":"ACTIVE",
"currentValue":0,"roomId":"FAKE-ROOM"}'

---

## Author
- **Name:** Balasooriya Mudiyanselage Vinuji Jayandee Balasooriya  
- **Student ID:** w2120101 (IIT Id - 20240746)  
- **Module:** 5COSC022W Client-Server Architectures  
- **University:** University of Westminster
