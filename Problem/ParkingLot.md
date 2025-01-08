
### Feature

Multiple floors with parking spots.
Different vehicle types (car, bike, truck).
Calculate parking charges based on duration.

#####  Advanced Features
Payment integration (e.g., cash, card).
Reservation system for booking spots in advance.

### Step 1: Identify Core Entities

* ParkingLot: Represents the entire parking lot.
* Floor: Represents individual floors within the parking lot.
* ParkingSpot: Represents each spot.
* Vehicle: Represents vehicles.
* Ticket: Issued when a vehicle parks.
* Reservation: For booking a spot.
* Payment: Handles payments.

### Step 3: Core Workflows

1. Park a Vehicle
* Driver enters the parking lot.
* The system assigns an available spot.
* A ticket is generated with the entry time and spot details.

2. Unpark a Vehicle
* Driver provides the ticket.
* The system calculates the parking fee based on duration and pricePerHour.
* Driver makes the payment.

3. Reserve a Spot
* Driver reserves a spot online for a specific time.
* A reservation is created, blocking the spot.
* Driver parks at the reserved spot when they arrive.

4. Payment
* Driver pays using cash or card.
* The payment is recorded for accounting.

Here's a detailed **Use Case** and **Diagram** for the Parking Lot System:

---

### **Use Cases**

#### **Actors**
1. **Driver**: Uses the parking system to park, unpark, and reserve spots.
2. **System Admin**: Manages parking lot, floors, and pricing.
3. **Payment Processor**: Handles payment transactions.

---

#### **Use Case 1: Park a Vehicle**
- **Actor**: Driver
- **Description**: A driver enters the parking lot and parks their vehicle in an available spot.
- **Preconditions**: The system has at least one available spot matching the vehicle type.
- **Steps**:
  1. Driver enters the parking lot.
  2. System identifies an available parking spot.
  3. System assigns the spot and generates a parking ticket.
  4. Driver parks the vehicle.
- **Postconditions**: The parking spot is marked as occupied.

---

#### **Use Case 2: Unpark a Vehicle**
- **Actor**: Driver
- **Description**: A driver leaves the parking lot and pays for the time parked.
- **Preconditions**: Driver has a valid parking ticket.
- **Steps**:
  1. Driver provides the parking ticket.
  2. System calculates the parking fee based on the time duration.
  3. Driver pays the fee.
  4. System marks the parking spot as available.
- **Postconditions**: The parking spot is freed for future use.

---

#### **Use Case 3: Reserve a Spot**
- **Actor**: Driver
- **Description**: A driver reserves a parking spot in advance.
- **Preconditions**: The parking spot must be available for the requested time slot.
- **Steps**:
  1. Driver selects a parking spot and time slot online.
  2. System checks availability.
  3. System confirms the reservation and blocks the spot.
- **Postconditions**: The parking spot is blocked for the reservation period.

---

#### **Use Case 4: Admin Manages Parking Lot**
- **Actor**: System Admin
- **Description**: Admin configures parking lot floors, spots, and pricing.
- **Preconditions**: Admin has access credentials.
- **Steps**:
  1. Admin adds or modifies floors and spots.
  2. Admin sets or updates pricing rules.
  3. System updates the parking lot configuration.
- **Postconditions**: Configuration changes are saved.

---

### **Use Case Diagram**

Here's a detailed **workflow** for the Parking Lot System, including steps for **park**, **unpark**, and **reservation** scenarios:

---

### **Workflow 1: Parking a Vehicle**

#### **Steps**
1. **Driver Entry:**
   - Driver enters the parking lot and provides vehicle details.
   - System determines the type of vehicle (e.g., car, bike, truck).

2. **Spot Allocation:**
   - System scans for an available spot matching the vehicle type.
   - If a spot is found:
     - Assign the spot to the vehicle.
     - Generate a parking ticket with details:
       - Spot ID
       - Entry time
       - Vehicle information
   - If no spot is available:
     - Notify the driver that parking is full.

3. **Vehicle Parks:**
   - Driver parks the vehicle in the assigned spot.
   - System updates the spot status to **occupied**.

---

### **Workflow 2: Unparking a Vehicle**

#### **Steps**
1. **Driver Exit:**
   - Driver provides the parking ticket at the exit.

2. **Fee Calculation:**
   - System calculates the parking fee based on:
     - Entry time from the ticket.
     - Current time.
     - Spot’s hourly pricing.

3. **Payment:**
   - Driver pays the parking fee (cash/card).
   - System records the payment.

4. **Spot Update:**
   - System updates the parking spot status to **available**.
   - Driver exits the parking lot.

---

### **Workflow 3: Reserving a Parking Spot**

#### **Steps**
1. **Driver Request:**
   - Driver accesses the reservation system (via app or web).
   - Inputs details:
     - Vehicle type
     - Desired time slot (start and end times)

2. **Availability Check:**
   - System checks for available spots matching:
     - Vehicle type
     - Requested time slot

3. **Reservation Confirmation:**
   - If a spot is available:
     - System reserves the spot for the requested duration.
     - Generates a reservation confirmation with:
       - Spot ID
       - Time slot
       - Vehicle details
   - If no spot is available:
     - Notify the driver about unavailability.

4. **Driver Arrival:**
   - Driver parks at the reserved spot during the specified time.
   - System updates the spot status to **occupied**.

---

### **Workflow 4: System Admin Managing Parking Lot**

#### **Steps**
1. **Admin Login:**
   - Admin logs into the parking system with credentials.

2. **Configuration Management:**
   - Add or update floors:
     - Add new floors with parking spots.
   - Configure parking spots:
     - Assign spot types (car, bike, truck).
     - Set hourly pricing.

3. **Save Changes:**
   - System validates and saves configuration updates.
   - Updates parking lot layout and availability.

---

### **Workflow Diagram (Text Representation)**

```plaintext
1. Driver Enters ---> [Check Availability] ---> Available?
                                | Yes                     | No
                                v                        v
                     [Generate Ticket]           Notify Driver (Full)
                                |
                        Assign Spot ---> Update Spot (Occupied)

2. Driver Exits ---> [Calculate Fee] ---> Driver Pays ---> Update Spot (Available)
```

---
