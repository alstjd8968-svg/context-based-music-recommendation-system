# Database Design

## Overview

The database stores music data, user information, and interaction history required for the recommendation engine.

PostgreSQL is used as the primary database.

---

# Entity Relationship

Main entities

Songs
Artists
Users
Listening History
Likes

---

# Songs Table

songs

id
title
artist_id
youtube_video_id
genre
energy
tempo
created_at

---

# Artists Table

artists

id
name

---

# Users Table

users

id
name
created_at

---

# Listening History

history

id
user_id
song_id
played_at

---

# Likes

likes

id
user_id
song_id
created_at

---

# Design Goals

The schema is designed to support efficient recommendation queries and user behavior analysis.
