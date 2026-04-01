# Super Mario Bros Clone (CS 360)

A Unity-based Super Mario Bros clone project built in C# as part of a CS 360 software engineering project.

This project focuses on recreating the feel and structure of the original Super Mario Bros while also exploring account management, save persistence, leaderboard support, scene-based game flow, and modular gameplay systems.

## Overview

This repository contains a 2D platformer built in Unity that recreates core Super Mario Bros gameplay and menu flow.

The current codebase includes:

- a playable first level (`1-1`)
- a main menu scene
- a login/register scene
- player movement and jumping systems
- enemy, block, and item system scaffolding
- game resource tracking for lives, coins, points, and time
- a MySQL-backed persistence layer for user accounts, saves, and leaderboard data

The original project documentation describes the larger intended scope as an 8-world, 4-level-per-world recreation of Super Mario Bros with offline account persistence, save/load support, and admin-oriented functionality. The current repository reflects a strong foundation toward that goal, with the first level and several supporting systems already in place.

## Project Goals

The goal of this project was to recreate Super Mario Bros in Unity as closely as possible within the time constraints of a semester-long software engineering project.

This project was also a way to strengthen skills in:

- Unity game development
- C# object-oriented programming
- game architecture and modular design
- database integration
- save-data modeling
- UI/menu development
- working with scenes, animations, and gameplay systems as part of a team project

## Current Status

This repository represents a solid partial implementation rather than a fully completed replica.

### Present in the current repository

- `1-1` gameplay scene
- `MainMenuScene`
- `LoginRegisterScene`
- modular gameplay code for players, enemies, blocks, items, audio, input, UI, and game state
- database-layer classes for:
  - users
  - saved games
  - leaderboard scores
- save data model for character, coins, lives, score, and unlocked stages
- stage-loading structure that supports adding future levels using a `world-level` naming pattern

### Not fully completed

- only the first level is currently present
- some systems are scaffolded or only partially implemented
- some gameplay/item/controller methods are still placeholders
- certain UI/game counters and support systems appear to be present in structure but not fully finished
- the broader 8-world project scope described in the documentation is not fully implemented in this repo

## Features

### Gameplay

- side-scrolling 2D platforming
- player movement and jumping
- collision-based enemy interaction
- lives, points, coins, and timer resource tracking
- stage transition structure through world-level scene naming

### Menu and account flow

- main menu scene
- login/register scene
- username/password input handling
- account-oriented flow tied to a database layer

### Persistence and data

- user records
- save-game records
- leaderboard/high-score records
- save data serialized for persistence

## Tech Stack

- **Engine:** Unity
- **Unity version:** 2020.3.17f1
- **Language:** C#
- **Game type:** 2D platformer
- **Database:** MySQL
- **Core Unity systems:** Tilemap, UI, 2D tools, animation, TextMeshPro

## Architecture Summary

The project is divided into a few major areas:

### 1. Game systems

Gameplay code is organized under `Assets/Code/Game` and includes:

- `GameManager`
- `GameResources`
- `InputManager`
- `SoundManager`
- `UIManager`
- `Player`
- `Mario`
- `Blocks/`
- `Enemies/`
- `Items/`

This structure keeps gameplay concerns separated by responsibility and makes it easier to add new entities or systems later.

### 2. Menu systems

The main authentication/menu flow lives under `Assets/Code/MainMenu`, with a dedicated controller for login/register behavior.

### 3. Database systems

The persistence layer lives under `Assets/Code/DB` and includes abstractions for:

- `DBClient`
- `UserTable`
- `GameSaveTable`
- `LeaderboardTable`

This allows the game to store and retrieve account data, save progress, and scoreboard information.

### 4. Shared data/state

The project uses shared game-resource tracking for values such as:

- coins
- lives
- points
- time left
- world number
- level number

This provides a central place for game-session state and UI updates.

## Project Structure

```text
.
|-- Assets/
|   |-- Code/
|   |   |-- DB/
|   |   |   |-- DBClient.cs
|   |   |   |-- DBException.cs
|   |   |   |-- GameSave.cs
|   |   |   |-- GameSaveTable.cs
|   |   |   |-- HighScore.cs
|   |   |   |-- LeaderboardTable.cs
|   |   |   |-- Table.cs
|   |   |   |-- User.cs
|   |   |   `-- UserTable.cs
|   |   |-- Game/
|   |   |   |-- Blocks/
|   |   |   |-- Enemies/
|   |   |   |-- Items/
|   |   |   |-- GameManager.cs
|   |   |   |-- GameResources.cs
|   |   |   |-- InputManager.cs
|   |   |   |-- Mario.cs
|   |   |   |-- Player.cs
|   |   |   |-- PlayerHealth.cs
|   |   |   |-- SoundManager.cs
|   |   |   `-- UIManager.cs
|   |   |-- MainMenu/
|   |   |   `-- AuthMenuController.cs
|   |   |-- CameraSystem.cs
|   |   |-- PlayerHealth.cs
|   |   |-- PlayerScore.cs
|   |   |-- SaveData.cs
|   |   `-- User.cs
|   |-- Scenes/
|   |   |-- 1-1.unity
|   |   |-- LoginRegisterScene.unity
|   |   `-- MainMenuScene.unity
|   |-- Sprites/
|   |-- Tiles/
|   `-- ...
|-- Packages/
|   `-- manifest.json
|-- ProjectSettings/
|   `-- ProjectVersion.txt
`-- ...
