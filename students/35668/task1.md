# Event-Driven Architecture Example  
## Smart Building Fire Response System

### Introduction
Event-Driven Architecture (EDA) is a design pattern where system components communicate through **events**.  
Instead of directly calling each other, components react when something important happens in the system.

This document demonstrates EDA using a **Smart Building Fire Response System**.

---

## Core Elements of the Architecture

### 1. Events
An **event** represents a change or action that occurs in the system.

Examples in the fire protection system:
- Smoke detected
- Temperature threshold exceeded
- Emergency alarm button pressed
- Fire confirmed by monitoring system

Example event:

SmokeDetected {
    location: "Floor 3 – Room 305",
    timestamp: "2026-03-05T14:12:00"
}

---

### 2. Event Producers
Event producers are devices or services that **generate events** when something happens.

Examples:
- Smoke sensors
- Heat detectors
- Manual fire alarm buttons
- Security monitoring system

Example:
A **heat sensor** detects abnormal temperature and publishes the event `HighTemperatureDetected`.

---

### 3. Event Channel (Event Broker)
The **event channel** distributes events to all systems interested in them.

Typical implementations:
- Message broker
- Event bus
- Streaming platform

Responsibilities:
- Receive events from producers
- Deliver them to subscribed event handlers
- Ensure reliable communication

---

### 4. Event Handlers (Event Consumers)
Event handlers are components that **listen for events and react accordingly**.

Examples in the system:

#### Fire Alarm Controller
Actions:
- Activate building sirens
- Turn on warning lights

#### Sprinkler System
Actions:
- Activate water sprinklers in affected zones

#### Emergency Notification Service
Actions:
- Send alerts to building security
- Notify local fire department

#### Elevator Safety Controller
Actions:
- Stop elevator operation
- Send elevators to the ground floor

#### Access Control System
Actions:
- Unlock emergency exits
- Disable restricted access doors

---

## Example Event Flow

Step 1  
A smoke detector identifies smoke particles.

Step 2  
The detector publishes the event:

SmokeDetected

Step 3  
The event broker receives the event and distributes it.

Step 4  
Multiple event handlers react simultaneously:

- Alarm system activates sirens
- Sprinklers release water
- Security team receives notification
- Elevators move to safe position
- Emergency exits unlock

---

## Advantages of Event-Driven Design

Scalability  
New systems can subscribe to events without modifying existing components.

Loose Coupling  
Components are independent and communicate only through events.

Real-Time Response  
Systems react immediately to critical situations.

Flexibility  
Additional services (analytics, logging, monitoring) can be added easily.

---

## Conclusion
The Smart Building Fire Response System illustrates how **Event-Driven Architecture** enables multiple independent subsystems to respond quickly and efficiently to critical events. This design improves reliability, scalability, and response time in safety-critical environments.
