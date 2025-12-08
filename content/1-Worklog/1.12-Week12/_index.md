---
title: "Week 12 Worklog"
date: "2025-09-11"
weight: 2
chapter: false
pre: " <b> 1.12. </b> "
---

### OBJECTIVES IN WEEK 12:
- Design Flow 3: Review Voting - implementing upvote/downvote toggle system with count management.
- Design Flow 4: Comment Threading - building nested comment system with thread depth tracking.
- Define database schema for social interactions (votes, comments, comment_likes, favorites).
- Plan user activity tracking and analytics integration.

### TASKS OF WEEK 12:
| Day | Task | Start Date | End Date | References |
|-----|------|------------|----------|------------|
| Mon | - Team Project Meeting: Social Interaction APIs <br> &emsp; - Design Flow 3: Review Voting <br> &emsp;&emsp; * POST /reviews/vote endpoint <br> &emsp;&emsp; * vote_type: "upvote" or "downvote" <br> &emsp;&emsp; * Toggle logic: new vote -> insert + increment | 24/11/2025 | 24/11/2025 | |
| Tue | - Continue Flow 3 Implementation <br> &emsp; - Vote toggle behaviors: <br> &emsp;&emsp; * Same vote clicked -> delete + decrement (toggle off) <br> &emsp;&emsp; * Different vote clicked -> update + adjust both counts <br> &emsp; - Define votes table schema and constraints | 25/11/2025 | 25/11/2025 | |
| Wed | - Design Flow 4: Comment Threading <br> &emsp; - POST /reviews/comment endpoint <br> &emsp;&emsp; * parent_comment_id provided -> Reply (thread_depth++) <br> &emsp;&emsp; * No parent -> Top-level comment <br> &emsp; - Increment comment_count on target (review/restaurant) | 26/11/2025 | 26/11/2025 | |
| Thu | - Design Additional Features <br> &emsp; - Favorites system: POST /restaurants/:id/favorite <br> &emsp; - Comment likes: POST /comments/:id/like <br> &emsp; - User activity tracking: user_activities table <br> &emsp; - Analytics event logging for user interactions | 27/11/2025 | 27/11/2025 | |
| Fri | - Team Project Meeting: Complete API Documentation <br> &emsp; - Finalize Flow 3 & Flow 4 specifications <br> &emsp; - Document all database tables: votes, comments, comment_likes, favorites, user_activities <br> &emsp; - Review complete API flow documentation | 28/11/2025 | 28/11/2025 | |

### ACHIEVEMENTS IN WEEK 12:
1. Designed complete Flow 3 (Review Voting):
   - POST /reviews/vote with vote_type parameter (upvote/downvote)
   - Implemented toggle logic: new vote inserts and increments count
   - Same vote toggle: deletes record and decrements count
   - Vote change: updates record and adjusts both upvote_count and downvote_count

2. Designed complete Flow 4 (Comment Threading):
   - POST /reviews/comment for creating comments on reviews/restaurants
   - Nested reply system using parent_comment_id
   - thread_depth tracking for proper indentation display
   - Automatic comment_count increment on target entity

3. Designed additional social features:
   - Favorites system for saving restaurants (favorites table)
   - Comment likes functionality (comment_likes table)
   - User activity tracking for analytics (user_activities table)

4. Documented complete database schema:
   - votes (upvotes/downvotes on reviews)
   - comments (comments on reviews/restaurants with threading)
   - comment_likes (likes on comments)
   - favorites (saved restaurants by users)
   - user_activities (analytics tracking for user interactions)
