# Music Data Collection Pipeline

## 1. Overview

This document describes the data collection architecture for the Context-Based Music Recommendation System.

The goal is to automatically collect large-scale music data from YouTube and enrich it with metadata so that it can be used in a recommendation system.

Target dataset size:

100,000+ songs

Collected data will include:

* song title
* artist
* YouTube video ID
* genre
* tags
* popularity
* duration
* metadata features

The data collection pipeline consists of several stages.

Query Generation
↓
YouTube Data Collection
↓
Song Title Parsing
↓
Metadata Enrichment
↓
Data Cleaning
↓
Database Storage

---

# 2. Data Sources

The system collects data using the following APIs.

Primary Source

YouTube Data API

Used for:

* video search
* video metadata
* video statistics

Metadata Sources

MusicBrainz API
Last.fm API

Used for:

* genre information
* artist metadata
* music tags

---

# 3. Data Collection Architecture

The data pipeline is designed as a modular system.

Query Generator
↓
YouTube Collector
↓
Title Parser
↓
Metadata Enricher
↓
Data Cleaner
↓
Database Loader

Each module is responsible for a specific stage of the pipeline.

---

# 4. Query Generation

To collect a large dataset, the system generates a large set of search queries.

Queries are generated using combinations of music genres and keywords.

Example genres

lofi
jazz
rock
indie
pop
kpop
classical
rnb
edm

Example keywords

official audio
topic
playlist
album
music

Query generation strategy

genre + keyword

Example queries

lofi hip hop official audio
jazz topic
indie rock official audio
kpop official audio

This strategy allows the system to discover large numbers of songs from different genres.

Estimated dataset size

50 genres × 10 keywords × 200 results = 100,000 songs

---

# 5. YouTube Data Collection

The system retrieves videos using the YouTube Data API search endpoint.

Search parameters include:

query
maxResults
type = video

Returned fields include:

videoId
title
channelTitle
publishedAt

Example response data

videoId: abc123
title: IU - Love Poem (Official Audio)
channel: IU Official
publishedAt: 2020-01-01

The video ID will later be used to embed the YouTube player.

---

# 6. Song Title Parsing

The video title is parsed to extract song information.

Example title

IU - Love Poem (Official Audio)

Parsed result

artist: IU
song: Love Poem

The parser uses pattern matching to detect the common format:

Artist - Song Title

If the format cannot be parsed, the system stores the original title for later processing.

---

# 7. Metadata Enrichment

YouTube metadata alone is not sufficient for building a recommendation system.

Additional information is retrieved from music metadata APIs.

MusicBrainz

Provides:

artist information
release data
recording metadata

Last.fm

Provides:

genre tags
similar artists
listener statistics

Example enriched data

title: Love Poem
artist: IU
genre: ballad
tags: kpop, emotional, vocal

This information will later be used as features for recommendation algorithms.

---

# 8. Data Cleaning

Raw YouTube search results contain many videos that are not actual songs.

Examples include:

reaction videos
cover performances
lyric videos
interviews

Filtering rules are applied to remove irrelevant content.

Example filters

video duration > 60 seconds
title contains "official" or "topic"
remove titles containing:

cover
reaction
live cam
interview

These rules significantly improve dataset quality.

---

# 9. Database Storage

Cleaned and enriched data is stored in PostgreSQL.

songs table

id
title
artist
youtube_video_id
duration
genre
created_at

artists table

id
name

song_tags table

id
song_id
tag

The database is structured to support efficient recommendation queries.

---

# 10. Data Pipeline Automation

The pipeline is automated using scheduled jobs.

Pipeline workflow

Scheduler
↓
Query generation
↓
YouTube data collection
↓
Title parsing
↓
Metadata enrichment
↓
Data cleaning
↓
Database insertion

The scheduler runs periodically to collect new music data.

This allows the dataset to grow continuously.

---

# 11. Expected Dataset

After running the pipeline, the database will contain:

100,000+ songs
thousands of artists
genre and tag metadata

This dataset will serve as the foundation for the recommendation engine.

---

# 12. Future Improvements

Possible future improvements include:

audio feature extraction
tempo analysis
energy detection
valence prediction

These features can be used to build more advanced recommendation models.

Examples include:

context-aware recommendation
collaborative filtering
neural recommendation models
