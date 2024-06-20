# TODO_App

# To-Do List Application

This project is a simple To-Do list application. Users can add tasks, and these tasks are displayed in a random order.

## Table of Contents
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Screenshots](#screenshots)
- [License](#license)

## Features
- Random ordering of tasks
- Task listing

## Requirements
- Android Studio
- Kotlin 1.3+ (for Android project)

## Installation
1. Clone or download this project.
    ```sh
    git clone https://github.com/yourusername/todolist.git
    ```
2. Open the project in Android Studio.

## Usage
1. Open the project in Android Studio.
2. Connect your device or emulator.
3. Click the Run button to start the application.

## Project Structure

### MainActivity.kt
This file is the main entry point of the application. It creates the task list, shuffles it, and displays it using a RecyclerView.

```kotlin
package com.example.todolist

import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import androidx.recyclerview.widget.LinearLayoutManager
import androidx.recyclerview.widget.RecyclerView
import kotlin.random.Random

class MainActivity : AppCompatActivity() {

    private lateinit var recyclerView: RecyclerView
    private lateinit var taskAdapter: TaskAdapter
    private val taskList = mutableListOf<Task>()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        recyclerView = findViewById(R.id.recyclerView)
        taskAdapter = TaskAdapter()

        recyclerView.layoutManager = LinearLayoutManager(this)
        recyclerView.adapter = taskAdapter

        // Adding example tasks
        taskList.add(Task("Task 1"))
        taskList.add(Task("Task 2"))
        taskList.add(Task("Task 3"))
        taskList.add(Task("Task 4"))
        taskList.add(Task("Task 5"))

        // Shuffle the task list randomly
        taskList.shuffle(Random(System.currentTimeMillis()))

        taskAdapter.submitList(taskList)
    }
}
