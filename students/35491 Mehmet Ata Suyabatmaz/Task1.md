# 🎮 Event-Driven Battle Arena: System Architecture

Welcome to the technical documentation for the **Battle Arena Backend**, a high-performance, real-time multiplayer game engine built on **Event-Driven Architecture (EDA)**. 

This system is designed to handle thousands of concurrent player interactions (attacks, movement, loot) by decoupling game logic from state persistence using a high-speed message broker.

---

## 🏗️ System Overview

In a fast-paced multiplayer environment, traditional request-response cycles create bottlenecks. Our architecture uses an **Asynchronous Event Loop** to ensure smooth gameplay.

### The Flow:
1. **Client Action:** Player triggers an action (e.g., "Cast Fireball").
2. **Ingress Gateway:** Validates the session and pushes a `SKILL_ACTIVATED` event to the **Message Bus**.
3. **Downstream Consumers:** Multiple services (Combat, Mana, VFX, Achievements) process this event simultaneously.
4. **Broadcaster:** The final state is pushed back to all players in the vicinity via WebSockets.

---

## ⚡ Core Event Schema

Standardization is key for scalability. Every event in the system follows this structured JSON format:

```json
{
  "eventId": "evt_88291x",
  "type": "PLAYER_DAMAGED",
  "timestamp": 1709669533,
  "payload": {
    "attackerId": "player_01",
    "targetId": "player_02",
    "damageAmount": 25,
    "hitType": "CRITICAL",
    "remainingHp": 75
  },
  "metadata": {
    "region": "eu-central-1",
    "version": "v2.4"
  }
}
