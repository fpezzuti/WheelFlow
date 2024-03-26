# WheelFlow: assistente smart all’accessibilità urbana

This repository contains the code and the documentation for the project "WheelFlow - assistente smart all'accessibilità urbana" presented at conference "Città 30 corriamo! L’urbanismo tattico, strada virtuosa per la mobilità sostenibile" in occasion of the European Mobility Week held in Pisa in 16/09/2022.

<p align="center">
  <img src="./poster-wheelflow.svg" width="500" title="WheelFlow poster" alt="WheelFlow poster presented at European Mobility Week 16/09/2022.">
</p>

## What is WheelFlow?
Paths’ accessibility is an important problem for user with mobility issues. WheelFlow focuses on **collecting** and **sharing** **geo-localized accessibility information** about routes in order to **assist wheelchair
users**.

- WheelFlow is a **crowd-sourced**, **Android application** where users can search for a path from a source to a destination and receive accessibility information about the path
- WheelFlow uses a **KNN classifier** to classify four possible kinds of surfaces that can be encountered in the built environment, depending on accelerometer, gyroscope and the magnetometer data.
- The data collection has been performed using the **Record application** whose code is available [here](./RecordApplication).

However, the project is described in detail in **paper** [WheelFlow](./paper-wheelflow.pdf).

## Architecture of WheelFlow

The **architecture** of WheelFlow is composed by:
- a [Python server](./PythonServer) hosted via _ngrok_ to **store data**, **classify** it, and **answer** to path's accessibility queries
- an [Android frontend application](./Frontend) for **searching accessibility information** about paths, areas and routes
- an [Android record application](./RecordApplication) for **contributing to the data collection**

<p align="center">
  <img src="https://github.com/fpezzuti/WheelFlow/assets/75533556/a380e448-bcaa-4f4f-8e38-048fed7370ab" width="600" title="Architecture of WheelFlow" alt="Architecture of WheelFlow">
</p>

