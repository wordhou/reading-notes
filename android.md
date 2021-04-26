# Android fundamentals

Android is a widespread operating system for phones, tablets, and other mobile devices. It is a Linux system where every app is a different user, and every process runs on its own virtual machine. Each app also only has permissions to the components that it needs to function. The user must explicitly grant permission for an app to use device data such as the camera, location, or Bluetooth functionality, or access to user data such as contacts or files. In addition, the filesystem permissions are set so that files associated can only be accessed by that app. Also generally every app process will run in its own virtual machine, creating isolation between different processes.

# App building

Android apps are structured around components, which are entry points to the application. There are four different types of app components that encompass how the app is used or interacted with.

## Activities

Activities are a single screen with user interface. Each activity is independent from other activities. An activity can be started from another activity or even from another app if allowed.

## Services

Services enable an app to keep running in the background. A service does not have a user interface, but instead runs in the background and performs some task. This task can be a variety of different things. Bound services provide an API to another process, whether from the same app or a different app or the android system.

## Broadcast Receiver

A broadcast receiver allows the system to deliver events to the app. Since this is an entry point to the app, a broadcast receiver allows allows the app to await some event without needing to remain running.

## Content provider

A content provider manages shared app data. This data can be stored in any persistent file storage system. The content provider provides a way for other processes to query and manage the data.
