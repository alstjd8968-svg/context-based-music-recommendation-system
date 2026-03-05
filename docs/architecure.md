                User
                 │
                 ▼
           Next.js Frontend
                 │
                 ▼
             API Gateway
                 │
        ┌────────┴────────┐
        ▼                 ▼
 Recommendation       User Service
     Service            
        │
        ▼
  Feature Store(추천용 데이터 저장소)
        │
        ▼
      Database
   (PostgreSQL)
        │
        ▼
  Data Pipeline
        │
        ▼
YouTube API + Music APIs

# System Architecture

## Overview

The Context-Based Music Recommendation System is a full-stack platform designed to recommend songs based on contextual information such as time, mood, and listening history.

The system integrates multiple components including frontend applications, backend APIs, recommendation engines, and external music data sources.

---

# High-Level Architecture

User
↓
Frontend (Next.js)
↓
API Server (Spring Boot)
↓
Recommendation Engine
↓
Database (PostgreSQL)
↓
External APIs (YouTube)

---

# Component Description

Frontend

The frontend provides the user interface for interacting with the system.

Main responsibilities:

display recommended songs
play music using YouTube player
collect user feedback
mood selection

---

Backend API

The backend exposes REST APIs that connect the frontend with the recommendation engine and database.

Example APIs

GET /api/today-song
GET /api/recommend
POST /api/like

---

Recommendation Engine

The recommendation engine selects songs based on contextual signals.

Inputs

time of day
day of week
user mood
listening history

Outputs

recommended song list

---

Database

The database stores structured information about songs, artists, and user interactions.

---

External APIs

External APIs provide music data used by the system.

Primary source

YouTube Data API
