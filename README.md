# RoomMVVMDemo

Application Android développée en Java démontrant l’architecture MVVM avec :

- Room Database
- Repository Pattern
- ViewModel
- LiveData
- RecyclerView

Le projet illustre une architecture Android moderne permettant de gérer des notes avec persistance locale via SQLite grâce à Room.

---

# Fonctionnalités

- Ajouter une note
- Afficher la liste des notes
- Supprimer une note avec un clic long
- Persistance locale des données
- Mise à jour automatique de l’interface avec LiveData
- Architecture MVVM complète

---
<img width="306" height="539" alt="Screenshot 2026-05-08 170638" src="https://github.com/user-attachments/assets/5ded2972-963a-494c-be42-65a423548a96" />

# Architecture du projet

```text
UI (Activity + RecyclerView)
        ↓
ViewModel
        ↓
Repository
        ↓
DAO
        ↓
Room Database (SQLite)
```

---

# Structure du projet

```text
com.example.roommvvmdemo
│
├── data
│   ├── Note.java
│   ├── NoteDao.java
│   └── NoteDatabase.java
│
├── repository
│   └── NoteRepository.java
│
├── viewmodel
│   └── NoteViewModel.java
│
├── adapter
│   └── NoteAdapter.java
│
├── MainActivity.java
│
└── res
    ├── layout
    └── values
```

---

# Technologies utilisées

- Java
- Android Studio
- Room Persistence Library
- LiveData
- ViewModel
- RecyclerView
- SQLite

---

# Dépendances principales

Ajoutez dans `build.gradle` :

```gradle
dependencies {

    implementation 'androidx.room:room-runtime:2.6.1'
    annotationProcessor 'androidx.room:room-compiler:2.6.1'

    implementation 'androidx.lifecycle:lifecycle-livedata:2.8.2'
    implementation 'androidx.lifecycle:lifecycle-viewmodel:2.8.2'

    implementation 'androidx.recyclerview:recyclerview:1.3.2'
}
```

---

# Fonctionnement MVVM

## Entity

Représente une table SQLite.

```java
@Entity(tableName = "notes")
public class Note {
    ...
}
```

## DAO

Interface contenant les opérations SQL.

```java
@Dao
public interface NoteDao {
    ...
}
```

## Room Database

Point central d’accès à SQLite.

```java
@Database(entities = {Note.class}, version = 1)
public abstract class NoteDatabase extends RoomDatabase {
    ...
}
```

## Repository

Couche intermédiaire entre Room et le ViewModel.

```java
public class NoteRepository {
    ...
}
```

## ViewModel

Conserve les données lors des rotations d’écran.

```java
public class NoteViewModel extends AndroidViewModel {
    ...
}
```

## LiveData

Observe automatiquement les changements de données.

```java
viewModel.getAllNotes().observe(this, notes -> {
    adapter.setNotes(notes);
});
```

---

# Pourquoi utiliser MVVM ?

- Séparation claire des responsabilités
- Code plus maintenable
- Meilleure gestion du cycle de vie Android
- Évite la perte des données lors des rotations
- Architecture scalable et professionnelle

---

# Exécution du projet

## Cloner le dépôt

```bash
git clone https://github.com/youness-lahdiri01/RoomMVVMDemo.git
```

## Ouvrir avec Android Studio

```text
Open Project
```

## Synchroniser Gradle

Attendre le téléchargement des dépendances.

## Lancer l’application

Exécuter sur un émulateur Android ou un appareil réel.

---

# Tests à réaliser

- Ajouter plusieurs notes
- Vérifier la persistance après fermeture
- Tester la rotation de l’écran
- Supprimer une note avec clic long
- Vérifier la mise à jour automatique du RecyclerView

---

# Résultat attendu

L’application doit afficher :

- Un champ titre
- Un champ description
- Un bouton Ajouter
- Une liste des notes sauvegardées

---

# Auteur

Youness Lahdiri

GitHub : https://github.com/youness-lahdiri01v
