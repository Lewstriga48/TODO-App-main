# TODO_App Arda Ata ARSLAN 35817   HAVA BASASLAN 38248

# Aplikacja Listy Zadań

Ten projekt to prosta aplikacja listy zadań. Użytkownicy mogą dodawać zadania, a te zadania są wyświetlane w losowej kolejności.

## Spis Treści
- [Funkcje](#funkcje)
- [Wymagania](#wymagania)
- [Instalacja](#instalacja)
- [Użycie](#użycie)
- [Struktura Projektu](#struktura-projektu)
- [Zrzuty Ekranu](#zrzuty-ekranu)
- [Licencja](#licencja)

## Funkcje
- Losowa kolejność zadań
- Lista zadań

## Wymagania
- Android Studio
- Kotlin 1.3+ (dla projektu Android)

## Instalacja
1. Sklonuj lub pobierz ten projekt.
    ```sh
    git clone https://github.com/Lewstriga48/TODO-App-main.git
    ```
2. Otwórz projekt w Android Studio.

## Użycie
1. Otwórz projekt w Android Studio.
2. Podłącz swoje urządzenie lub emulator.
3. Kliknij przycisk Uruchom, aby rozpocząć aplikację.

## Struktura Projektu

### MainActivity.kt
Ten plik jest głównym punktem wejścia aplikacji. Tworzy listę zadań, tasuje ją i wyświetla za pomocą RecyclerView.


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

Struktura Projektu
MainActivity.kt:

Reprezentuje główny ekran aplikacji i wyświetla listę zadań użytkownikowi.
CreateCard.kt:

Aktywność umożliwiająca użytkownikom tworzenie nowych zadań.
UpdateCard.kt:

Aktywność służąca do aktualizacji istniejących zadań.
SplashScreen.kt:

Ekran startowy wyświetlany podczas uruchamiania aplikacji.
Adapter.kt:

Klasa adaptera dla RecyclerView. Umożliwia wyświetlanie zadań w postaci listy.
DAO.kt:

Obiekt dostępu do bazy danych. Definiuje i wykonuje operacje na bazie danych.
Entity.kt:

Definiuje encje bazy danych.
DataObject.kt:

Klasa pomocnicza do operacji na bazie danych.
CardInfo.kt:

Klasa zawierająca informacje o zadaniach.
Folder layout:

Pliki XML zawierające projekt interfejsu użytkownika (activity_main.xml, activity_create_card.xml, activity_update_card.xml).
Folder values:

Zasoby aplikacji (kolory, ciągi znaków, tematy).
Działanie Aplikacji
Ekran startowy:

Zarządzany przez SplashScreen.kt i wyświetlany podczas uruchamiania aplikacji.
Lista zadań:

MainActivity.kt wyświetla listę zadań użytkownikowi. Użytkownik może przeglądać istniejące zadania oraz dodać nowe zadanie klikając odpowiedni przycisk.
Tworzenie nowego zadania:

Użytkownik klikając przycisk "Nowe zadanie" zostaje przeniesiony do aktywności CreateCard.kt. Wprowadza tam szczegóły zadania i zapisuje je.
Aktualizacja zadania:

Użytkownik może zaktualizować zadanie klikając na nie, co przenosi go do aktywności UpdateCard.kt, gdzie może zaktualizować informacje o zadaniu i je zapisać.
Dodatkowe Informacje
Proguard:

Plik konfiguracyjny Proguard (proguard-rules.pro) służy do minimalizacji i zaciemniania kodu aplikacji.
Gradle:

Pliki konfiguracyjne Gradle (build.gradle, gradle.properties, settings.gradle) zarządzają zależnościami projektu i procesem budowania.
