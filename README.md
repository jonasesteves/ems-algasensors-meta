# Sensor Alert Configuration

System developed during the course Microservices Specialist.
The system envolve techs like Java, Spring, RabbitMQ.

Some functionalities below:

Implement the functionality: **Sensor Alert Configuration**

You need to develop a feature to manage temperature alerts for sensors.  
Each sensor can have configurable temperature limits (maximum and minimum), which will be used to generate alerts.  
These configurations must be stored and retrieved from a database.

---

## System Requirements

The system must allow:

- Retrieve the details of a sensor's alert configuration.
- Create or update a sensor's alert configuration.
- Delete a sensor's alert configuration.

---

## 1. Entity: SensorAlert

Should represent the alert configuration in the system with the following fields:

- **id**: Unique identifier (SensorId)
- **maxTemperature**: Maximum temperature for an alert (Double)
- **minTemperature**: Minimum temperature for an alert (Double)

---

## 2. Repository: SensorAlertRepository

Must allow basic CRUD operations (create, read, update, delete) using **Spring Data JPA**.

---

## 3. DTOs (Input and Output)

Each should contain the following properties:

**SensorAlertInput:**

- `maxTemperature`: Double
- `minTemperature`: Double

**SensorAlertOutput:**

- `id`: TSID
- `maxTemperature`: Double
- `minTemperature`: Double

---

## 4. Controller: SensorAlertController

Should expose the following REST endpoints:

### **GET /api/sensors/{sensorId}/alert**

- Returns `SensorAlertOutput`.
- Returns `200 OK` on success.
- If the configuration does not exist, returns `404 Not Found`.

### **PUT /api/sensors/{sensorId}/alert**

- Creates or updates a sensor's alert configuration.
- Returns `SensorAlertOutput`.
- Returns `200 OK` on success.
- If the configuration does not exist, creates a new record.

### **DELETE /api/sensors/{sensorId}/alert**

- Removes a sensor's alert configuration.
- Returns `204 No Content` on success.
- If the configuration does not exist, returns `404 Not Found`.

---

## Validation Rules

- The **sensor ID** is required in all operations.
- The temperatures (**maximum** and **minimum**) may be null.

---

## Challenge Tasks

- Implement the **SensorAlert** entity using **JPA**.
- Create the repository for data persistence.
- Define the input (`SensorAlertInput`) and output (`SensorAlertOutput`) DTOs.
- Implement the REST controller with the specified endpoints.
- Ensure the HTTP responses are correct (`200`, `404`, `204`).

---

## Tips

- Use `@Builder` to simplify object creation.
- Use `ResponseStatusException` for error handling.
- Consider that **SensorId** is an object encapsulating a **TSID**.
- Store the TSID value as **BigInt**.
- Test the endpoints using **Postman**.  
