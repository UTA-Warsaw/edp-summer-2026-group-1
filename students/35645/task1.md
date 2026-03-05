[event_driven_traffic_light.md](https://github.com/user-attachments/files/25774375/event_driven_traffic_light.md)
# Event-Driven Architecture Example: Traffic Light System

## What is Event-Driven Architecture?

Event-Driven Architecture (EDA) is a system design where components
respond to events. An **event** is something that happens in the system
that other components react to.

------------------------------------------------------------------------

# Example: Traffic Light System

A pedestrian wants to cross the street and presses the crossing button.
This action generates an event that the traffic light system reacts to.

------------------------------------------------------------------------

## 1. Event

An **event** is a signal that something happened.

Example events: - Pedestrian presses crossing button - Timer expires -
Emergency vehicle detected - Car detected by road sensor

Example event:

    PedestrianButtonPressed

------------------------------------------------------------------------

## 2. Event Producer

The **event producer** is the component that generates the event.

Example producer: - Pedestrian crossing button

When the button is pressed, it produces the event:

    PedestrianButtonPressed

------------------------------------------------------------------------

## 3. Event Channel / Event Bus

The **event channel** transfers the event from the producer to the
components that need it.

Example flow:

    Pedestrian Button
           ↓
       Event Bus
           ↓
    Traffic Controller

------------------------------------------------------------------------

## 4. Event Handler (Consumer)

The **event handler** reacts to the event and performs actions.

Example handler: - Traffic Light Controller

Handler logic:

    on PedestrianButtonPressed:
        wait for safe moment
        set car_light = RED
        set pedestrian_light = GREEN

------------------------------------------------------------------------

## 5. Multiple Event Handlers

One event can trigger multiple handlers.

Example event:

    EmergencyVehicleDetected

Handlers: - Traffic Light Controller → changes traffic lights - Traffic
Monitoring System → logs the event - City Dashboard → updates traffic
status

------------------------------------------------------------------------

## Full Event Flow

    Pedestrian presses button
            ↓
    EVENT: PedestrianButtonPressed
            ↓
    Event Bus
            ↓
    Traffic Light Controller
            ↓
    Traffic lights change

------------------------------------------------------------------------

## Advantages of Event-Driven Architecture

-   Loose coupling between components
-   Real-time response
-   Scalable systems
-   Easy to extend with new services

------------------------------------------------------------------------

## Summary

Event-Driven Architecture works by reacting to events.

Example flow: 1. Event occurs 2. Event is sent through an event channel
3. Event handlers react and perform actions

