# BrokerVerse — MQTT-Based Multi-User Visualization in Java Swing

**BrokerVerse** is a simple Java Swing application that demonstrates real-time communication and shared state synchronization between multiple clients using the **MQTT protocol**.  
Each instance represents a player that moves around a shared world grid. Player movements are broadcast to all connected instances through a public MQTT broker.

## Features

- 🧩 **Publish–Subscribe architecture** via [Eclipse Paho MQTT](https://www.eclipse.org/paho/)
- 🧑‍🤝‍🧑 Multi-client synchronization using a shared topic
- 🪶 Lightweight **Swing GUI** displaying each player as a colored circle
- ⚙️ Thread-safe **Blackboard** shared-memory model
- 💬 Clean separation of model (Blackboard), view (WorldPanel), and controllers (Publisher/Subscriber/KeyListener)
- 🔄 Automatic reconnection and session management

> [!NOTE]
> Broker | `tcp://broker.hivemq.com:1883` (public)

## Technologies

| Component | Technology |
|------------|-------------|
| Language | Java 17+ |
| Messaging | MQTT (Eclipse Paho) |
| GUI | Java Swing |
| Build Tool | Maven |
| Broker | `tcp://broker.hivemq.com:1883` (public) |


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
