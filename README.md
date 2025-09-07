> This repository is auto synced and readonly
# Dambel API Documentation

Welcome to the Dambel API documentation. This guide provides a comprehensive, organized overview of all available API endpoints, grouped by resource and version. Use the navigation below to quickly find the endpoint you need.

---

## Table of Contents
- [Authentication](#authentication)
- [Gyms](#gyms)
- [Users](#users)
- [Training](#training)
- [AI](#ai)
- [Tracker](#tracker)
- [Media](#media)
- [Ratings](#ratings)
- [Posts](#posts)
- [Comments](#comments)
- [Payments](#payments)
- [Notifications](#notifications)
- [Reports](#reports)
- [Chats](#chats)
- [Admin](#admin)
- [Global Schemas & Errors](#global-schemas--errors)

---

## Usage Tips
- **All endpoints are under `/api/v1`**
- **Click endpoint names** to view detailed documentation, including parameters, permissions, request/response examples, and error handling.
- **Resource endpoints** are grouped for clarity. Nested resources are indented.
- **Refer to [Global Schemas & Errors](#global-schemas--errors)** for shared response formats and error types.
- **Production API is hosted on https://api.dambel.io/api/v1 and Staging is hosted on https://api.staging.dambel.io/api/v1**

---

## Authentication
- [`POST /api/v1/auth/login`](auth/login.md)
- [`POST /api/v1/auth/register`](auth/register.md)
- [`GET /api/v1/auth/me`](auth/me.md)

## Gyms
- [`GET /api/v1/gyms`](gyms/index.md)
- [`POST /api/v1/gyms`](gyms/create.md)
- `/api/v1/gyms/{gym-id}`
    - [`PUT`](gyms/update.md)
    - [`DELETE`](gyms/delete.md)
    - [`GET /working-periods`](gyms/working-periods/index.md)
    - [`POST /working-periods`](gyms/working-periods/create.md)
    - `/working-periods/{working-period-id}`
        - [`PUT`](gyms/working-periods/update.md)
        - [`DELETE`](gyms/working-periods/delete.md)
    - [`GET /equipment`](gyms/equipment/index.md)
    - [`POST /equipment`](gyms/equipment/create.md)
    - `/equipment/{gym-equipment-id}`
        - [`PUT`](gyms/equipment/update.md)
        - [`DELETE`](gyms/equipment/delete.md)
    - [`GET /equipment/compare/{workout-plan-id}`](gyms/equipment/compare.md)
    - [`GET /plans`](gyms/plans/index.md)
    - [`POST /plans`](gyms/plans/create.md)
    - `/plans/{plan-id}`
        - [`PUT`](gyms/plans/update.md)
        - [`DELETE`](gyms/plans/delete.md)
    - [`GET /buffet-items`](gyms/buffet-items/index.md)
    - [`POST /buffet-items`](gyms/buffet-items/create.md)
    - `/buffet-items/{buffet-item-id}`
        - [`PUT`](gyms/buffet-items/update.md)
        - [`DELETE`](gyms/buffet-items/delete.md)
    - [`GET /admins`](gyms/admins/index.md)
    - [`POST /admins`](gyms/admins/create.md)
    - `/admins/{admin-id}`
        - [`PUT`](gyms/admins/update.md)
        - [`DELETE`](gyms/admins/delete.md)
    - [`POST /subscriptions/subscribe/{plan-id}`](gyms/subscriptions/subscribe.md)
    - [`GET /subscriptions/my-subscriptions`](gyms/subscriptions/my-subscriptions.md)
    - [`POST /subscriptions/checkin/{subscription-id}`](gyms/subscriptions/checkin.md)
    - [`POST /subscriptions/checkout/{subscription-id}`](gyms/subscriptions/checkout.md)
    - [`DELETE /subscriptions/delete-checkin/{subscription-id}/{checkin-id}`](gyms/subscriptions/delete-checkin.md)
    - [`GET /subscriptions/manage`](gyms/subscriptions/manage/index.md)
    - [`POST /subscriptions/manage`](gyms/subscriptions/manage/create.md)
    - `/subscriptions/manage/{gym-subscription-id}`
        - [`PUT`](gyms/subscriptions/manage/update.md)
        - [`DELETE`](gyms/subscriptions/manage/delete.md)
    - [`GET /data/peak-hours`](gyms/data/peak-hours.md)
    - [`GET /data/search-stats`](gyms/data/search-stats.md)

## Users
- [`GET /api/v1/users`](users/index.md)
- [`POST /api/v1/users`](users/create.md)
- `/api/v1/users/{user-id}`
    - [`PUT`](users/update.md)
    - [`DELETE`](users/delete.md)
    - [`POST /attach-role/{role-id}`](users/attach-role.md)
    - [`POST /detach-role/{role-id}`](users/detach-role.md)
    - [`GET /championships`](users/championships/index.md)
    - [`POST /championships`](users/championships/create.md)
    - `/championships/{championship-id}`
        - [`PUT`](users/championships/update.md)
        - [`DELETE`](users/championships/delete.md)
    - [`GET /education`](users/education/index.md)
    - [`POST /education`](users/education/create.md)
    - `/education/{education-id}`
        - [`PUT`](users/education/update.md)
        - [`DELETE`](users/education/delete.md)

## Training
- [`GET /api/v1/training/services`](training/services/index.md)
- [`POST /api/v1/training/services/{user-id}`](training/services/create.md)
- `/api/v1/training/services/{training-service-id}`
    - [`PUT`](training/services/update.md)
    - [`DELETE`](training/services/delete.md)
- [`GET /api/v1/training/services/{training-service-id}/data/search-stats`](training/services/data/search-stats.md)
- [`GET /api/v1/training/trainees`](training/trainees/index.md)
- [`POST /api/v1/training/trainees`](training/trainees/create.md)
- `/api/v1/training/trainees/{trainee-id}`
    - [`PUT`](training/trainees/update.md)
- [`GET /api/v1/training/diet-plans`](training/diet-plans/index.md)
- [`POST /api/v1/training/diet-plans`](training/diet-plans/create.md)
- `/api/v1/training/diet-plans/{diet-plan-id}`
    - [`PUT`](training/diet-plans/update.md)
    - [`DELETE`](training/diet-plans/delete.md)
    - [`GET /meals`](training/diet-plans/meals/index.md)
    - [`POST /meals`](training/diet-plans/meals/create.md)
    - `/meals/{meal-id}`
        - [`PUT`](training/diet-plans/meals/update.md)
        - [`DELETE`](training/diet-plans/meals/delete.md)
    - [`GET /supplements`](training/diet-plans/supplements/index.md)
    - [`POST /supplements`](training/diet-plans/supplements/create.md)
    - `/supplements/{supplement-id}`
        - [`PUT`](training/diet-plans/supplements/update.md)
        - [`DELETE`](training/diet-plans/supplements/delete.md)
- [`GET /api/v1/training/workout-plans`](training/workout-plans/index.md)
- [`POST /api/v1/training/workout-plans`](training/workout-plans/create.md)
- `/api/v1/training/workout-plans/{workout-plan-id}`
    - [`PUT`](training/workout-plans/update.md)
    - [`DELETE`](training/workout-plans/delete.md)
    - [`GET /sessions`](training/workout-plans/sessions/index.md)
    - [`POST /sessions`](training/workout-plans/sessions/create.md)
    - `/sessions/{session-id}`
        - [`PUT`](training/workout-plans/sessions/update.md)
        - [`DELETE`](training/workout-plans/sessions/delete.md)
        - [`GET /exercises`](training/workout-plans/sessions/exercises/index.md)
        - [`POST /exercises`](training/workout-plans/sessions/exercises/create.md)
        - `/exercises/{exercise-id}`
            - [`PUT`](training/workout-plans/sessions/exercises/update.md)
            - [`DELETE`](training/workout-plans/sessions/exercises/delete.md)

## AI
- [`GET /api/v1/ai/threads`](ai/threads/index.md)
- [`POST /api/v1/ai/threads`](ai/threads/create.md)
- `/api/v1/ai/threads/{thread-id}`
    - [`DELETE`](ai/threads/delete.md)
    - [`GET /messages`](ai/threads/messages/index.md)
    - [`POST /messages`](ai/threads/messages/create.md)
    - `/messages/{message-id}`
        - [`DELETE`](ai/threads/messages/delete.md)

## Tracker
- [`GET /api/v1/tracker/data/average-sleep-duration`](tracker/data/average-sleep-duration.md)
- [`GET /api/v1/tracker/data/records`](tracker/data/records.md)
- [`GET /api/v1/tracker/data/today`](tracker/data/today.md)
- [`GET /api/v1/tracker/wakeups`](tracker/wakeups/index.md)
- [`POST /api/v1/tracker/wakeups`](tracker/wakeups/create.md)
- `/api/v1/tracker/wakeups/{tracker-wakeup-id}`
    - [`PUT`](tracker/wakeups/update.md)
    - [`DELETE`](tracker/wakeups/delete.md)
- [`GET /api/v1/tracker/sleeps`](tracker/sleeps/index.md)
- [`POST /api/v1/tracker/sleeps`](tracker/sleeps/create.md)
- `/api/v1/tracker/sleeps/{tracker-sleep-id}`
    - [`PUT`](tracker/sleeps/update.md)
    - [`DELETE`](tracker/sleeps/delete.md)
- [`GET /api/v1/tracker/weights`](tracker/weights/index.md)
- [`POST /api/v1/tracker/weights`](tracker/weights/create.md)
- `/api/v1/tracker/weights/{tracker-weight-id}`
    - [`PUT`](tracker/weights/update.md)
    - [`DELETE`](tracker/weights/delete.md)
- [`GET /api/v1/tracker/supplements`](tracker/supplements/index.md)
- [`POST /api/v1/tracker/supplements`](tracker/supplements/create.md)
- `/api/v1/tracker/supplements/{tracker-supplement-id}`
    - [`PUT`](tracker/supplements/update.md)
    - [`DELETE`](tracker/supplements/delete.md)
- [`GET /api/v1/tracker/waters`](tracker/waters/index.md)
- [`POST /api/v1/tracker/waters`](tracker/waters/create.md)
- `/api/v1/tracker/waters/{tracker-water-id}`
    - [`PUT`](tracker/waters/update.md)
    - [`DELETE`](tracker/waters/delete.md)
- [`GET /api/v1/tracker/meals`](tracker/meals/index.md)
- [`POST /api/v1/tracker/meals`](tracker/meals/create.md)
- `/api/v1/tracker/meals/{tracker-meal-id}`
    - [`PUT`](tracker/meals/update.md)
    - [`DELETE`](tracker/meals/delete.md)
- [`GET /api/v1/tracker/workouts`](tracker/workouts/index.md)
- [`POST /api/v1/tracker/workouts`](tracker/workouts/create.md)
- `/api/v1/tracker/workouts/{tracker-workout-id}`
    - [`PUT`](tracker/workouts/update.md)
    - [`DELETE`](tracker/workouts/delete.md)
    - [`GET /sets`](tracker/workouts/sets/index.md)
    - [`POST /sets`](tracker/workouts/sets/create.md)
    - `/sets/{tracker-workout-set-id}`
        - [`PUT`](tracker/workouts/sets/update.md)
        - [`DELETE`](tracker/workouts/sets/delete.md)
- [`GET /api/v1/tracker/shares`](tracker/shares/index.md)
- [`POST /api/v1/tracker/shares`](tracker/shares/create.md)
- `/api/v1/tracker/shares/{shared-tracker-id}`
    - [`PUT`](tracker/shares/update.md)
    - [`DELETE`](tracker/shares/delete.md)

## Media
- [`POST /api/v1/media`](media/create.md)
- `/api/v1/media/{media-id}`
    - [`DELETE`](media/delete.md)
    - [`GET`](media/download.md)

## Ratings
- [`GET /api/v1/ratings`](ratings/index.md)
- [`POST /api/v1/ratings`](ratings/create.md)
- [`GET /api/v1/ratings/all`](ratings/all.md)
- `/api/v1/ratings/{rating-id}`
    - [`PUT`](ratings/update.md)
    - [`DELETE`](ratings/delete.md)

## Posts
- [`GET /api/v1/posts`](posts/index.md)
- [`GET /api/v1/posts/blog`](posts/blog.md)
- [`POST /api/v1/posts`](posts/create.md)
- `/api/v1/posts/{post-id}`
    - [`PUT`](posts/update.md)
    - [`DELETE`](posts/delete.md)
- [`GET /api/v1/posts/{post-id}/data/search-stats`](posts/data/search-stats.md)

## Comments
- [`GET /api/v1/comments`](comments/index.md)
- [`POST /api/v1/comments`](comments/create.md)
- `/api/v1/comments/{comment-id}`
    - [`PUT`](comments/update.md)
    - [`DELETE`](comments/delete.md)

## Payments
- [`GET /api/v1/payments`](payments/index.md)
- [`POST /api/v1/payments/deposit`](payments/deposit.md)
- [`POST /api/v1/payments/verify-deposit`](payments/verify-deposit.md)
- [`GET /api/v1/payments/balance`](payments/balance.md)
- [`GET /api/v1/payments/prices`](payments/prices.md)
- [`POST /api/v1/payments/withdrawal`](payments/withdrawal.md)
- [`POST /api/v1/payments/buy-premium`](payments/buy-premium.md)
- [`POST /api/v1/payments/boost`](payments/boost.md)
- [`GET /api/v1/payments/data/stats`](payments/data/stats.md)
- [`GET /api/v1/payments/data/chart`](payments/data/chart.md)

## Notifications
- [`GET /api/v1/notifications`](notifications/index.md)
- [`POST /api/v1/notifications/mark-read/{notification-id?}`](notifications/mark-read.md)

## Reports
- [`GET /api/v1/reports`](reports/index.md)
- [`POST /api/v1/reports`](reports/create.md)
- `/api/v1/reports/{report-id}`
    - [`PUT`](reports/update.md)
    - [`DELETE`](reports/delete.md)

## Chats
- [`GET /api/v1/chats`](chats/index.md)
- [`POST /api/v1/chats`](chats/create.md)
- `/api/v1/chats/{chat-id}`
    - [`PUT`](chats/update.md)
    - [`DELETE`](chats/delete.md)
    - [`GET /messages`](chats/messages/index.md)
    - [`POST /messages`](chats/messages/create.md)
    - `/messages/{message-id}`
        - [`PUT`](chats/messages/update.md)
        - [`DELETE`](chats/messages/delete.md)

## Admin
- [`GET /api/v1/admin/roles`](admin/roles/index.md)
- [`POST /api/v1/admin/roles`](admin/roles/create.md)
- `/api/v1/admin/roles/{role-id}`
    - [`PUT`](admin/roles/update.md)
    - [`DELETE`](admin/roles/delete.md)
- [`GET /api/v1/admin/permissions`](admin/permissions/index.md)
- [`GET /api/v1/admin/brands`](admin/brands/index.md)
- [`POST /api/v1/admin/brands`](admin/brands/create.md)
- `/api/v1/admin/brands/{brand-id}`
    - [`PUT`](admin/brands/update.md)
    - [`DELETE`](admin/brands/delete.md)
- [`GET /api/v1/admin/countries`](admin/countries/index.md)
- [`POST /api/v1/admin/countries`](admin/countries/create.md)
- `/api/v1/admin/countries/{country-id}`
    - [`PUT`](admin/countries/update.md)
    - [`DELETE`](admin/countries/delete.md)
- [`GET /api/v1/admin/states`](admin/states/index.md)
- [`POST /api/v1/admin/states`](admin/states/create.md)
- `/api/v1/admin/states/{state-id}`
    - [`PUT`](admin/states/update.md)
    - [`DELETE`](admin/states/delete.md)
- [`GET /api/v1/admin/cities`](admin/cities/index.md)
- [`POST /api/v1/admin/cities`](admin/cities/create.md)
- `/api/v1/admin/cities/{city-id}`
    - [`PUT`](admin/cities/update.md)
    - [`DELETE`](admin/cities/delete.md)
- [`GET /api/v1/admin/majors`](admin/majors/index.md)
- [`POST /api/v1/admin/majors`](admin/majors/create.md)
- `/api/v1/admin/majors/{major-id}`
    - [`PUT`](admin/majors/update.md)
    - [`DELETE`](admin/majors/delete.md)
- [`GET /api/v1/admin/exercises`](admin/exercises/index.md)
- [`POST /api/v1/admin/exercises`](admin/exercises/create.md)
- `/api/v1/admin/exercises/{exercise-id}`
    - [`PUT`](admin/exercises/update.md)
    - [`DELETE`](admin/exercises/delete.md)
- [`GET /api/v1/admin/equipment`](admin/equipment/index.md)
- [`POST /api/v1/admin/equipment`](admin/equipment/create.md)
- `/api/v1/admin/equipment/{equipment-id}`
    - [`PUT`](admin/equipment/update.md)
    - [`DELETE`](admin/equipment/delete.md)
- [`GET /api/v1/admin/supplements`](admin/supplements/index.md)
- [`POST /api/v1/admin/supplements`](admin/supplements/create.md)
- `/api/v1/admin/supplements/{supplement-id}`
    - [`PUT`](admin/supplements/update.md)
    - [`DELETE`](admin/supplements/delete.md)

## Global Schemas & Errors
- [Pagination data](_globals/pagination-data.md)
- [Broadcasting](_globals/broadcasting.md)
- [Localization](_globals/localization.md)
- [Validation errors](_globals/validation-errors.md)
- [Authentication errors](_globals/authentication-errors.md)
- [Server errors](_globals/server-errors.md)
- [Rate-limit errors](_globals/rate-limit-errors.md)
- [Method-not-allowed errors](_globals/method-not-allowed-errors.md)
- [Not-found errors](_globals/not-found-errors.md)
- [Permission errors](_globals/permission-errors.md)
