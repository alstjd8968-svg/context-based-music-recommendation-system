# Recommendation System

## Overview

The recommendation engine selects songs using contextual information and user preferences.

The system initially uses a rule-based recommendation approach and later expands to machine learning based methods.

---

# Context-Based Recommendation

The system constructs a context object containing:

day of week
time of day
user mood

Example

context

day: Thursday
time: morning
mood: focus

---

# Recommendation Process

1. Context creation
2. Candidate song selection
3. Feature filtering
4. Score calculation
5. Song selection

---

# Scoring Function

score(song) =

0.4 × user preference
0.3 × context similarity
0.2 × popularity
0.1 × randomness

---

# Future Machine Learning Models

Possible models include

collaborative filtering
matrix factorization
two-tower recommendation models
