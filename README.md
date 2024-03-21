# BirdSight

<p align="center">
  <img src="https://github.com/MBarc/BirdSight/assets/42979055/77f4506f-77cb-4bcd-b91a-f9dfb5054d86" width="200" />
</p>
<p align="center">
  <b> BirdSight </b>
</p>
<p align="center">
  Iot Birdhouse Camera and Conservation Web App
</p>

## Summary ##

This project aims to develop an ESP32 camera system integrated into a birdhouse, allowing users to remotely monitor bird activity in the area via a Rust-programmed web application.

## Conservation Benefits ##
* Monitoring Bird Populations: The project enables continuous monitoring of bird populations in a specific area, providing valuable data on species diversity, abundance, and distribution over time. This information is crucial for assessing the health of bird populations and identifying potential conservation priorities.
* Engaging Citizen Scientists: The web application encourages community members to participate in citizen science initiatives by collecting and sharing data on bird activity and behavior. Citizen scientists play a vital role in conservation efforts by contributing valuable data that can inform research, management, and policy decisions.

## Key Elements and Their Features ##
* ESP32 with Camera
  * Hosts a webserver to make the livestream of the camera accessible.
  * When motion is detected, via a PIR sensor, a still-image of the livestream is uploaded to the MongoDB with the following payload: the actual image, the datetime the picture was taken, and the coordinates of the ESP32.
* Rust Web Application
  * Accessible from any device that has an Internet connection.
  * Users have to log in for authorization.
  * After a successful login, users will be greeted with a grid of squares. Each grid is a separate camera that the user can click on to tune into the livestream.
  * The livestream page will contain the following elements: A video window that the livestream will be playing in, the name of the device, the coordinates of the device, and another tab (called “Calendar View”) that will display a calendar where the user can select a day and view all the still-images that were taken on the selected day.
    * On the backend of the Calendar View feature, it utilizes the Python API.
  * Is containerized with Docker.
* MongoDB
  * A collection is created for every day. For example, for pictures taken on January 1, 2024, the collection will be called 01-01-2024 (mm-dd-yyyy).
  * Each document in the collection will have the following information: the actual picture, the coordinates, and the datetime the picture was taken (including seconds).
  * Is containerized with Docker.
* Python API
  * To be built with Flask.
  * Has functions to be able to grab all the data from MongoDB
  * Is containerized with Docker.
