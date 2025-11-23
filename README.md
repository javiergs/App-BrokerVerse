# MQWorld

**A lightweight multi‑user 2D "shared world" synchronized via MQTT**

This is a simple Java Swing application where multiple instances connect to a shared virtual grid and publish or receive each other’s positions in real time via MQTT.
It demonstrates the publish–subscribe pattern using the Eclipse Paho MQTT client library and a public MQTT broker. It also serves as a teaching tool for IoT and network-messaging courses, showing how devices share state through topics. Additionally, it offers a fun testbed for experimentation—change the topic, swap the broker, adjust the visuals, scale the world, or extend the logic however you like.

<p align="center">
  <img width="256" alt="MQWorld Logo" src="https://github.com/user-attachments/assets/9daa43d3-9c49-4271-8f12-72e9d1bf631b" />
</p>

## 🚀 Features

-   MQTT publish--subscribe architecture using Paho.\
-   Real‑time synchronization of multiple clients in the same shared
    "world".\
-   Lightweight Java Swing GUI.\
-   Thread‑safe "Blackboard" shared‑memory model separating model, view,
    and controller.\
-   Automatic reconnection and MQTT session management.\
-   Easily extensible.

## 🛠 Run the application

    java -jar target/MQWorld-1.0.jar player1
    java -jar target/MQWorld-1.0.jar player2

## 🕹️ Controls

  Key   Action
  ----- ------------
  ↑     Move Up
  ↓     Move Down
  ←     Move Left
  →     Move Right

## 📁 Project Structure

-   Main.java -- entry point\
-   Blackboard.java -- shared model\
-   WorldPanel.java -- renderer\
-   Player.java -- player model\
-   Publisher.java -- MQTT publisher\
-   Subscriber.java -- MQTT subscriber
