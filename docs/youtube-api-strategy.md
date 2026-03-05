# YouTube API Strategy

## Overview

The YouTube Data API is used as the primary source for music video discovery.

However, the API enforces strict quota limits that restrict the number of requests per day.

This document explains the quota limitations and strategies used to collect large-scale datasets efficiently.

---

# YouTube API Quota System

Each API request consumes quota units.

Daily quota limit:

10,000 units per day

Example cost per request

search.list → 100 units
videos.list → 1 unit

Because search operations are expensive, naive crawling quickly exhausts the quota.

Example

100 searches × 100 units = 10,000 units

This would consume the entire daily quota.

---

# Efficient Collection Strategy

The system uses several techniques to maximize data collection.

1. Query batching

Each search request retrieves up to 50 results.

Instead of performing many small searches, the system retrieves the maximum number of results per request.

---

2. Pagination

The API supports pagination using nextPageToken.

This allows additional results to be retrieved from the same query.

Example

lofi hip hop official audio

Page 1 → 50 results
Page 2 → 50 results
Page 3 → 50 results

This significantly increases the number of songs collected per query.

---

3. Query Expansion

To avoid duplicate results, the system generates many unique queries.

Example query structure

genre + keyword

Examples

lofi hip hop official audio
indie rock topic
kpop official audio

This allows the crawler to explore different parts of the YouTube music graph.

---

4. Duplicate Filtering

Many queries return overlapping results.

Duplicate detection is performed using:

videoId

If a video already exists in the database, it is skipped.

---

# Large Scale Collection Strategy

To build a dataset of 100,000 songs, the system uses a distributed query strategy.

Example

50 genres
10 keywords
20 pages per query

Estimated result count

50 × 10 × 100 = 50,000+ songs

Repeated crawling over time allows the dataset to grow continuously.

---

# Scheduling Strategy

The crawler runs periodically using scheduled jobs.

Example schedule

once per hour

Each run performs:

10 queries
10 × 50 results = 500 videos

Estimated daily collection

12,000 videos per day

After filtering duplicates, approximately 3,000–5,000 unique songs remain.

---

# Future Improvements

Possible improvements include:

multiple API keys
distributed crawling
message queue based data pipelines

These improvements would allow the system to scale to millions of songs.
