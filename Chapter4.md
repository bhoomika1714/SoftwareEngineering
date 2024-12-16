- User interaction modeling is important as it helps to identify user requirements. 
- Modeling system-to-system interaction highlights the communication problems that 
may arise.
- Modeling component interaction helps us understand if a proposed system 
structure is likely to deliver the required system performance and dependability.

 -  Use case modeling, which is mostly used to model interactions between a sys
tem and external agents (human users or other systems).
 -  Sequence diagrams, which are used to model interactions between system com
ponents, although external agents may also be included
## INTERACTION MODELS :
- Modeling user interaction is important as it helps 
to identify user requirements. 
- Modeling system-to-system interaction highlights 
the communication problems that may arise. 
-  Modeling component interaction helps us 
understand if a proposed system structure is 
likely to deliver the required system performance 
and dependability. 
  -  se case diagrams and sequence diagrams may 
be used for interaction modeling.

## USE CASE MODELING :
- Use cases were developed originally to support 
requirements elicitation and now incorporated 
into the UML.
 - Each use case represents a discrete task that 
involves external interaction with a system.
 - Actors in a use case may be people or other 
systems.
- Represented diagramatically to provide an 
overview of the use case and in a more detailed 
textual form.
---


| **Test ID** | **Description**                        | **Steps**                                                                                         | **Input**                       | **Expected Output**                                             | **Actual Output**                                           | **Test Case (Pass/Fail)** |
|-------------|----------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------|---------------------------------------------------------------|-----------------------------------------------------------|---------------------------|
| TC01        | Drone connects to the server           | 1. Power on the drone.<br>2. Attempt to connect to the server.                                   | Drone ID: D001, Server IP: 192.168.1.10 | Connection status shows "Connected."                        | Connection status shows "Connected."                      | Pass                      |
| TC02        | Drone receives a move command          | 1. Log in to the operator interface.<br>2. Send a "Move to Position" command.                    | Command: Move to X: 50, Y: 50  | Drone moves to the specified position and confirms.           | Drone moved to X: 50, Y: 50 and confirmed.                | Pass                      |
| TC03        | Drone avoids an obstacle autonomously  | 1. Place an obstacle ahead of the drone.<br>2. Enable autonomous mode.<br>3. Monitor its path.   | Obstacle at X: 20, Y: 20        | Drone changes its path to avoid the obstacle.                | Drone changed its path and avoided the obstacle.          | Pass                      |
| TC04        | Drone herds cattle to a boundary       | 1. Set herding boundaries.<br>2. Enable herding mode.                                            | Boundary: X: 0-100, Y: 0-100    | Drone herds cattle to stay within the specified boundary.     | Drone herded cattle within the boundary.                  | Pass                      |
| TC05        | Drone syncs updated cattle positions   | 1. Update cattle position.<br>2. Check all layers for synchronization.                          | New position: X: 70, Y: 80      | Updated position reflected across all layers.                | Position synchronized and reflected in all layers.        | Pass                      |
| TC06        | Manual override halts autonomous mode  | 1. Enable autonomous herding mode.<br>2. Send a "Return to Base" command.                       | Command: Return to Base         | Drone halts and returns to the base immediately.             | Drone halted and returned to the base.                   | Pass                      |
| TC07        | Drone telemetry is displayed correctly | 1. Open monitoring interface.<br>2. Observe telemetry data.                                     | Drone ID: D001                  | Real-time telemetry (battery, position) is displayed.         | Telemetry shows battery: 85%, Position: X: 10, Y: 15.    | Pass                      |

### Explanation of Simplifications:
- The **Inputs** include direct examples for easier testing.
- The **Expected Output** and **Actual Output** columns are based on basic success scenarios.
- Focused on core functionalities to simplify the scenarios.
---

| **Test ID** | **Description**                        | **Steps**                                                                                         | **Input**                       | **Expected Output**                                             | **Actual Output**                                           | **Test Case (Pass/Fail)** |
|-------------|----------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------|---------------------------------------------------------------|-----------------------------------------------------------|---------------------------|
| TC01        | Drone connects to the server           | 1. Power on the drone.<br>2. Attempt to connect to the server.                                   | Drone ID: D001, Server IP: 192.168.1.10 | Connection status shows "Connected."                        | Connection status shows "Failed to Connect."              | Fail                      |
| **Failure Reason**: Server was unreachable due to network issues or incorrect IP address.                                                                                                      |                                 |                                                                  |                                                           |                           |
| TC02        | Drone receives a move command          | 1. Log in to the operator interface.<br>2. Send a "Move to Position" command.                    | Command: Move to X: 50, Y: 50  | Drone moves to the specified position and confirms.           | Drone did not move to the specified position.             | Fail                      |
| **Failure Reason**: Command lost due to communication issues or invalid drone ID.                                                                                                             |                                 |                                                                  |                                                           |                           |
| TC03        | Drone avoids an obstacle autonomously  | 1. Place an obstacle ahead of the drone.<br>2. Enable autonomous mode.<br>3. Monitor its path.   | Obstacle at X: 20, Y: 20        | Drone changes its path to avoid the obstacle.                | Drone collided with the obstacle.                        | Fail                      |
| **Failure Reason**: Obstacle detection sensor malfunctioned or decision-making algorithm error.                                                                                              |                                 |                                                                  |                                                           |                           |
| TC04        | Drone herds cattle to a boundary       | 1. Set herding boundaries.<br>2. Enable herding mode.                                            | Boundary: X: 0-100, Y: 0-100    | Drone herds cattle to stay within the specified boundary.     | Cattle strayed out of the boundary.                      | Fail                      |
| **Failure Reason**: Drone's herding algorithm failed or cattle movement speed exceeded drone response.                                                                                       |                                 |                                                                  |                                                           |                           |
| TC05        | Drone syncs updated cattle positions   | 1. Update cattle position.<br>2. Check all layers for synchronization.                          | New position: X: 70, Y: 80      | Updated position reflected across all layers.                | Position not synchronized in all layers.                 | Fail                      |
| **Failure Reason**: Data sync issue in one or more layers due to latency or database failure.                                                                                               |                                 |                                                                  |                                                           |                           |
| TC06        | Manual override halts autonomous mode  | 1. Enable autonomous herding mode.<br>2. Send a "Return to Base" command.                       | Command: Return to Base         | Drone halts and returns to the base immediately.             | Drone did not halt autonomous operations.                | Fail                      |
| **Failure Reason**: Manual override command not received or override priority was not implemented correctly.                                                                                 |                                 |                                                                  |                                                           |                           |
| TC07        | Drone telemetry is displayed correctly | 1. Open monitoring interface.<br>2. Observe telemetry data.                                     | Drone ID: D001                  | Real-time telemetry (battery, position) is displayed.         | Telemetry data was missing or incorrect.                 | Fail                      |
| **Failure Reason**: Telemetry not updated due to a communication failure between the drone and server.                                                                                      |                                 |                                                                  |                                                           |                           |

### Notes on Failures:
1. **Common Root Causes**:
   - Network connectivity issues between drone and server.
   - Malfunctions in sensors or hardware components.
   - Software logic errors in communication or decision-making layers.
   - Synchronization and database write latency in multi-layer systems.

2. **Steps for Debugging**:
   - Check drone-server connectivity and logs.
   - Verify input commands and the integrity of transmitted data.
   - Analyze logs and exception traces from each architectural layer.
   - Test sensors and drone hardware independently for malfunctions.
---


### 1. **Test Case for User Registration**

| **Test Case ID** | **Description**                           | **Expected Output**               | **Actual Output**           | **Result (Pass/Fail)** |
|------------------|-------------------------------------------|-----------------------------------|-----------------------------|------------------------|
| TC_01            | Test valid user registration with all fields filled | User is successfully registered, a confirmation message is displayed | User is successfully registered, confirmation message displayed | Pass                   |
| TC_02            | Test user registration with missing mandatory fields | Error message: "All fields are required" | Error message: "All fields are required" | Pass                   |
| TC_03            | Test user registration with invalid email format | Error message: "Invalid email format" | Error message: "Invalid email format" | Pass                   |
| TC_04            | Test user registration with weak password | Error message: "Password must contain at least 8 characters, including a number and a special character" | Error message: "Password must contain at least 8 characters, including a number and a special character" | Pass                   |

### 2. **Test Case for User Login**

| **Test Case ID** | **Description**                           | **Expected Output**               | **Actual Output**           | **Result (Pass/Fail)** |
|------------------|-------------------------------------------|-----------------------------------|-----------------------------|------------------------|
| TC_05            | Test valid login with registered user | User is successfully logged in, and redirected to the dashboard | User successfully logged in, dashboard loaded | Pass                   |
| TC_06            | Test login with incorrect email | Error message: "Email not found" | Error message: "Email not found" | Pass                   |
| TC_07            | Test login with incorrect password | Error message: "Incorrect password" | Error message: "Incorrect password" | Pass                   |

### 3. **Test Case for Journal Submission**

| **Test Case ID** | **Description**                           | **Expected Output**               | **Actual Output**           | **Result (Pass/Fail)** |
|------------------|-------------------------------------------|-----------------------------------|-----------------------------|------------------------|
| TC_08            | Test submitting a journal with all required fields | Journal is submitted successfully, confirmation message displayed | Journal submitted, confirmation message displayed | Pass                   |
| TC_09            | Test submitting an empty journal | Error message: "Journal content cannot be empty" | Error message: "Journal content cannot be empty" | Pass                   |
| TC_10            | Test submitting a journal with a file attachment larger than the allowed size | Error message: "File size exceeds the limit" | Error message: "File size exceeds the limit" | Pass                   |

### 4. **Test Case for Commenting on a Journal**

| **Test Case ID** | **Description**                           | **Expected Output**               | **Actual Output**           | **Result (Pass/Fail)** |
|------------------|-------------------------------------------|-----------------------------------|-----------------------------|------------------------|
| TC_11            | Test adding a valid comment to a journal | Comment is successfully added, displayed below the journal | Comment added, displayed below the journal | Pass                   |
| TC_12            | Test adding a comment with empty content | Error message: "Comment cannot be empty" | Error message: "Comment cannot be empty" | Pass                   |
| TC_13            | Test adding a comment with inappropriate language | Error message: "Inappropriate language is not allowed" | Error message: "Inappropriate language is not allowed" | Pass                   |

### 5. **Test Case for User Profile Update**

| **Test Case ID** | **Description**                           | **Expected Output**               | **Actual Output**           | **Result (Pass/Fail)** |
|------------------|-------------------------------------------|-----------------------------------|-----------------------------|------------------------|
| TC_14            | Test updating the user's profile with valid data | Profile is successfully updated, confirmation message displayed | Profile updated, confirmation message displayed | Pass                   |
| TC_15            | Test updating the user's profile with an invalid email | Error message: "Invalid email format" | Error message: "Invalid email format" | Pass                   |


