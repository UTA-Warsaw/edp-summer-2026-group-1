# Online Food Delivery System

## Event-Driven Architecture Example

------------------------------------------------------------------------

# 1. Introduction

Event-Driven Architecture (EDA) is a system design where components
communicate using **events**. When an event occurs, different components
called **event handlers** react automatically.

This document describes a **Food Delivery System** designed using
Event-Driven Architecture.

------------------------------------------------------------------------

# 2. System Overview

The system allows customers to order food from restaurants and receive
delivery from drivers.

Instead of components communicating directly, they react to **events**
generated in the system.

Example:

Customer places an order → Event created → Multiple services respond.

------------------------------------------------------------------------

# 3. Architecture Components

## 3.1 Event Producers

Event producers generate events when something happens.

Examples:

  Producer               Description
  ---------------------- ---------------------------------
  Customer Application   Creates new food orders
  Payment System         Confirms payments
  Restaurant System      Updates food preparation status
  Delivery Application   Updates delivery status

Example:

Customer submits an order → **OrderPlaced event**

------------------------------------------------------------------------

## 3.2 Events

Events represent important actions in the system.

  Event              Description
  ------------------ ------------------------------
  OrderPlaced        Customer places an order
  PaymentCompleted   Payment is successful
  OrderAccepted      Restaurant accepts the order
  FoodPrepared       Food is ready
  DriverAssigned     Driver assigned to order
  OrderDelivered     Order delivered to customer

Example event:

Event: OrderPlaced OrderID: 45872 Customer: Alex Restaurant: Pizza House
Time: 18:35

------------------------------------------------------------------------

## 3.3 Event Channel (Event Bus)

The **Event Bus** is responsible for distributing events across the
system.

Responsibilities:

-   Receive events from producers
-   Send events to all interested handlers
-   Enable asynchronous communication

------------------------------------------------------------------------

## 3.4 Event Handlers

Event handlers respond to events and perform actions.

  Handler                Action
  ---------------------- ---------------------------
  Payment Service        Processes payment
  Restaurant System      Starts preparing food
  Delivery Service       Assigns driver
  Notification Service   Sends updates to customer
  Tracking System        Updates order tracking

------------------------------------------------------------------------

# 4. Event Processing Flow

1.  Customer places order
2.  Event **OrderPlaced** is generated
3.  Event sent to **Event Bus**
4.  Event handlers receive the event
5.  Handlers perform actions

Next events occur:

-   PaymentCompleted
-   FoodPrepared
-   DriverAssigned
-   OrderDelivered

------------------------------------------------------------------------

# 5. System Architecture Diagram

Customer App \| \| OrderPlaced v +------------+ \| Event Bus \|
+------------+ \| \| \| \| v v v v Payment Restaurant Delivery
Notification Service System System Service

------------------------------------------------------------------------

# 6. Advantages of Event-Driven Architecture

-   Fast response to events
-   Services are loosely coupled
-   High scalability
-   Easy to add new services

------------------------------------------------------------------------

# 7. Conclusion

Event-Driven Architecture helps large systems handle many actions
efficiently. In a food delivery system, multiple services react to
events such as orders, payments, and deliveries, allowing the platform
to operate reliably and scale easily.

