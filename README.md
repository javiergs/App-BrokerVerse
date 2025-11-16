## **MQWorld: An MQTT-Based Multi-User Visualization in Java Swing**

**MQWorld** is a lightweight, multi-user 2D virtual space where each client moves across a shared grid in real time using the **MQTT protocol**. Every running instance acts as a player, publishing its position and subscribing to the positions of others. 
<p align="center">
  <img width="256" alt="MQWorld Logo" src="https://github.com/user-attachments/assets/9daa43d3-9c49-4271-8f12-72e9d1bf631b" />
</p>

> [!NOTE]
>
> Broker | `tcp://broker.hivemq.com:1883` (public)
>

## Features

- 🧩 **Publish–Subscribe architecture** via [Eclipse Paho MQTT](https://www.eclipse.org/paho/)
- 🧑‍🤝‍🧑 Multi-client synchronization using a shared topic
- 🪶 Lightweight **Swing GUI** displaying each player as a colored circle
- ⚙️ Thread-safe **Blackboard** shared-memory model
- 💬 Clean separation of model (Blackboard), view (WorldPanel), and controllers (Publisher/Subscriber/KeyListener)
- 🔄 Automatic reconnection and session management


## Running the Application

### 1. Build
Clone the repository and build with Maven:

```bash
git clone https://github.com/<yourusername>/BrokerVerse.git
cd BrokerVerse
mvn clean package
```
### 2. Run
Each instance represents a player. You can launch multiple clients (each with a different ID):

```bash
java -jar target/BrokerVerse-1.0.jar one
java -jar target/BrokerVerse-1.0.jar two
java -jar target/BrokerVerse-1.0.jar three
...
```
Each player will appear in the same virtual grid.  
When a player moves, its coordinates are published via MQTT and displayed by other connected clients.


## Controls

| Key | Action |
|-----|---------|
| ⬆️ Up Arrow | Move Up |
| ⬇️ Down Arrow | Move Down |
| ⬅️ Left Arrow | Move Left |
| ➡️ Right Arrow | Move Right |


## Structure

| Class | Responsibility |
|--------|----------------|
| `Main.java` | Entry point, creates UI and MQTT threads |
| `Blackboard.java` | Central shared model with PropertyChange support |
| `WorldPanel.java` | Renders players graphically |
| `Player.java` | Represents each participant |
| `MyKeyListener.java` | Handles arrow-key movement |
| `MyPublisher.java` | Publishes player state via MQTT |
| `MySubscriber.java` | Subscribes to MQTT topic and updates the model |

## GUI 
<img width="912" height="712" alt="Screenshot 2025-11-05 at 9 13 48 PM" src="https://github.com/user-attachments/assets/5560a930-5085-40e4-8f42-44d03872a30e" />


