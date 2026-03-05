# Context-Based Music Recommendation System 🎧

A full-stack music recommendation platform that suggests songs based on user context such as **time, mood, and listening history**.

This project aims to simulate a simplified architecture similar to modern recommendation systems used by large platforms.

---

# Overview

This system recommends songs using contextual signals such as:

* Time of day
* Day of week
* User mood
* Listening history
* Song features

Songs are collected automatically from YouTube and enriched with music metadata.

---

# System Architecture

User
↓
Frontend (Next.js)
↓
Backend API (Spring Boot)
↓
Recommendation Engine
↓
Database (PostgreSQL)
↓
External APIs (YouTube Data API + Metadata APIs)

---

# Tech Stack

Frontend

* Next.js
* React
* TypeScript

Backend

* Spring Boot
* REST API

Database

* PostgreSQL

Data Pipeline

* Python

External APIs

* YouTube Data API
* Music metadata APIs

---

# Core Features

Daily Song Recommendation

A system that recommends a song every day based on contextual information.

Context signals include:

* Morning / Night
* Weekday / Weekend
* Mood selection
* Listening behavior

Example API:

GET /api/today-song

Response:

{
"title": "Love Poem",
"artist": "IU",
"youtubeId": "abc123",
"reason": "Thursday morning focus music"
}

---

# Recommendation Strategy

The recommendation system combines several signals.

Score(song) =
0.4 × user preference
0.3 × context match
0.2 × popularity
0.1 × randomness

Context signals include:

* Time
* Day
* Mood

---

# Database Design

songs

id
title
artist
youtube_video_id
genre
energy
valence
tempo

users

id
name

listening_history

id
user_id
song_id
played_at

likes

id
user_id
song_id

---

# Data Pipeline

Songs are automatically collected from YouTube using the YouTube Data API.

Steps:

1. Search music-related queries on YouTube
2. Extract video metadata
3. Parse song title and artist
4. Enrich metadata using music APIs
5. Store structured data in PostgreSQL

The pipeline enables large-scale music dataset creation.

---

# Future Work

* Personalized recommendation
* Machine learning models
* Collaborative filtering
* Two-Tower recommendation model
* Real-time recommendation updates

---

# Goal

The goal of this project is to explore the design of a **context-aware recommendation system** while practicing full-stack development and data engineering.
