---
title: "Week 11 Worklog"
date: "2025-09-11"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### OBJECTIVES IN WEEK 11:
- Design Flow 1: User Submits New Place - handling new location submissions with validation and admin approval workflow.
- Design Flow 2: Photo Upload - implementing S3 presigned URL pattern for direct client uploads.
- Define database schema for user-generated content (location_addresses, review_posts, photos).
- Plan admin moderation workflow and SQS embedding job triggers.

### TASKS OF WEEK 11:
| Day | Task | Start Date | End Date | References |
|-----|------|------------|----------|------------|
| Mon | - Team Project Meeting: API Flow Design <br> &emsp; - Design Flow 1: User Submits New Place <br> &emsp;&emsp; * POST /reviews/submit-new-place endpoint <br> &emsp;&emsp; * Input validation (300+ char review, phone, hours required) <br> &emsp;&emsp; * Duplicate detection using pg_trgm (similarity > 0.7) | 17/11/2025 | 17/11/2025 | |
| Tue | - Continue Flow 1 Design <br> &emsp; - Define database operations: <br> &emsp;&emsp; * Create location_addresses (status: pending) <br> &emsp;&emsp; * Create review_posts (linked to location) <br> &emsp; - Design admin review interface at /admin/locations/pending | 18/11/2025 | 18/11/2025 | |
| Wed | - Design Location Approval Flow <br> &emsp; - POST /reviews/approve-location endpoint <br> &emsp;&emsp; * Create restaurant record from approved location <br> &emsp;&emsp; * Update location_addresses (status: approved) <br> &emsp;&emsp; * Trigger SQS embedding job for search indexing | 19/11/2025 | 19/11/2025 | |
| Thu | - Design Flow 2: Photo Upload <br> &emsp; - POST /photos/upload-url endpoint <br> &emsp;&emsp; * Generate unique S3 key <br> &emsp;&emsp; * Create pending photo record in database <br> &emsp;&emsp; * Return presigned URL (5 min expiry) <br> &emsp; - Client direct upload to S3 <br> &emsp; - CDN URL generation for photo access | 20/11/2025 | 20/11/2025 | |
| Fri | - Team Project Meeting: Review & Documentation <br> &emsp; - Finalize Flow 1 & Flow 2 specifications <br> &emsp; - Document database tables: users, restaurants, location_addresses, review_posts, photos <br> &emsp; - Prepare for Week 12 implementation | 21/11/2025 | 21/11/2025 | |

### ACHIEVEMENTS IN WEEK 11:
1. Designed complete Flow 1 (User Submits New Place):
   - POST /reviews/submit-new-place with comprehensive input validation
   - Implemented duplicate detection using PostgreSQL pg_trgm extension (similarity threshold > 0.7)
   - Defined pending/approved status workflow for location_addresses table

2. Designed admin moderation workflow:
   - Admin review interface at /admin/locations/pending
   - POST /reviews/approve-location endpoint for approval process
   - Automated restaurant record creation upon approval
   - SQS job trigger for embedding generation (search indexing)

3. Designed complete Flow 2 (Photo Upload):
   - POST /photos/upload-url for presigned URL generation
   - S3 key generation strategy for organized storage
   - Pending photo record creation for tracking
   - 5-minute presigned URL expiry for security
   - CDN integration for optimized photo delivery

4. Documented database schema for:
   - users (user accounts)
   - restaurants (approved places)
   - location_addresses (pending/approved user-submitted locations)
   - review_posts (user reviews linked to locations)
   - photos (uploaded images with status tracking)
