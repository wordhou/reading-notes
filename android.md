# Android fundamentals

Android is a widespread operating system for phones, tablets, and other mobile devices. It is a Linux system where every app is a different user, and every process runs on its own virtual machine. Each app also only has permissions to the components that it needs to function. The user must explicitly grant permission for an app to use device data such as the camera, location, or Bluetooth functionality, or access to user data such as contacts or files. In addition, the filesystem permissions are set so that files associated can only be accessed by that app. Also generally every app process will run in its own virtual machine, creating isolation between different processes.

# App building

Android apps are structured around components, which are entry points to the application. There are four different types of app components that encompass how the app is used or interacted with.

## Activities

Activities represent a single view with a user interface. Each activity is independent from other activities. An activity can be started from another activity or even from another app if allowed.

## Services

Services enable an app to keep running in the background. A service does not have a user interface, but instead runs in the background and performs some task. This task can be a variety of different things. Bound services provide an API to another process, whether from the same app or a different app or the android system.

## Broadcast Receiver

A broadcast receiver allows the system to deliver events to the app. Since this is an entry point to the app, a broadcast receiver allows allows the app to await some event without needing to remain running.

## Content provider

A content provider manages shared app data. This data can be stored in any persistent file storage system. The content provider provides a way for other processes to query and manage the data.

# Platform Fundamentals

## The Process Lifecycle

Android runs every application in its own process, and also manages the lifecycle of the processes necessary to run applications. Android will kill and resume processes and also manage their priority as necessary, depending on the what the user is doing and the resources that are available to the device.

## Tasks and the Back Stack

A task is a collection of activities that are related to doing one job. Each activity in a task is arranged in a stack, so that when the user goes "back" to their previous activity in a task, the current activity is popped off the stack and the previous activity takes focus. The inactive tasks on the stack are stopped, but the system retains their user interface.

One result of this system design is that an activity can be started more than once, and multiple instances of that activity can be on the stack at once. One way to arrive at this is to create a activity graph that is cyclic, meaning from a given activity there's a sequence of buttons you can follow that arrives back at that activity without ever pressing the back button. There are ways to prevent this or to modify this behavior.

The behavior of activities and tasks can be customized by specifying defaults for any activity in the Android manifest file, or by specifying flags on the Intent when an activity is opened.

## Intents

Intents represent a user action

# Storing Data

There are many different ways to store application data in the Android platform, from key-value stores on the local device to databases in the cloud.

## SharedPreferences

The Shared Preferences API allows apps to store data on the local device in files that represent a key-value store. Every activity has a default shared preferences file associated with it that can be requested with the `getPreferences()` method, and the app can also request and create shared preferences files by name with the `getSharedPreferences()` method.

The `SharedPreferences` object itself represents a key-value store that can store `Int`s and `String`s. For more reference material on the `SharedPreferences` API, see the [API docs](https://developer.android.com/reference/android/content/SharedPreferences).
