<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Connect DLTD

A Laravel-based backend foundation and domain architecture for a comprehensive customer engagement platform developed during my internship at **DLTD Software Company**.

The project was designed to support a large-scale digital ecosystem combining customer accounts, products, ordering, loyalty, rewards, gamification, community engagement, recipes, campaigns, health and nutrition, store management, referrals, notifications, and content management.

> **Project Status:** Backend architecture and domain-model foundation  
> **Organization:** DLTD Software Company  
> **Context:** Internship Project  
> **Primary Role:** Software Engineering / Backend Development  
> **Backend:** Laravel 12 / PHP 8.2+  
> **Frontend:** Laravel starter frontend / Vite / Tailwind CSS  

---

## Overview

**Connect DLTD** represents the backend foundation of a broader customer engagement platform.

The objective of the project was to establish a scalable Laravel architecture capable of supporting multiple interconnected business domains rather than building the system as a collection of isolated features.

The domain architecture covers areas including:

- Customer accounts and authentication
- OTP verification and password recovery
- Products and flavors
- Nutrition information
- Flavor reviews and flavor passports
- Orders and order items
- Custom product boxes
- Delivery
- Stores and inventory
- Loyalty profiles
- IceCoins and transactions
- Loyalty tiers
- Rewards and reward redemption
- Challenges and user progress
- Games and game sessions
- Achievements
- Leaderboards
- Community posts
- Comments and likes
- Recipes and categories
- Campaigns and participation
- Referrals and milestones
- Health profiles and health logs
- News and brand stories
- Promotional banners
- Notifications and push notification logs
- Activity logging
- Application settings

The repository focuses primarily on establishing the **backend structure and domain model** required for these capabilities.

---

## Project Architecture

The platform is organized around multiple interconnected business domains.

```text
                         CONNECT PLATFORM
                                |
        +-----------------------+-----------------------+
        |                       |                       |
     CUSTOMER               COMMERCE               ENGAGEMENT
        |                       |                       |
   Authentication          Products                  Games
   User Profiles           Flavors                   Challenges
   OTP                     Orders                    Achievements
   Health                  Custom Boxes              Leaderboards
   Notifications           Delivery
                           Stores
                           Inventory
        |                       |                       |
        +-----------------------+-----------------------+
                                |
                           LOYALTY SYSTEM
                                |
                     +----------+----------+
                     |                     |
                  IceCoins             Rewards
                     |                     |
               Transactions         Redemptions
                     |
                Loyalty Tiers
                                |
        +-----------------------+-----------------------+
        |                       |                       |
     COMMUNITY               CONTENT               CAMPAIGNS
        |                       |                       |
     Posts                   Recipes                 Campaigns
     Comments                News                    Participation
     Likes                   Stories                 Referrals
     Reviews                 Banners                 Milestones
```

This structure allows the different areas of the application to evolve independently while remaining connected through the customer account and business domain.

---

# Core Domains

## Customer & Authentication

The project includes the foundation for customer identity and authentication.

### Components

- User accounts
- OTP verification
- Password reset tokens
- Session management
- Authentication configuration

The application follows Laravel's authentication conventions and provides the foundation for extending the customer account system with additional platform-specific functionality.

---

## Product & Flavor Management

The product domain separates products from individual flavors and related customer information.

### Models

- `Product`
- `Flavor`
- `FlavorNutrition`
- `FlavorPassportEntry`
- `FlavorReview`

This structure allows the platform to associate additional information with individual flavors, including nutritional information, customer reviews, and flavor-related experiences.

---

## Ordering & Commerce

The commerce domain provides the foundation for customer ordering.

### Models

- `Order`
- `OrderItem`
- `CustomBox`
- `CustomBoxItem`
- `Delivery`

The architecture supports both standard product ordering and customizable product boxes.

Conceptually:

```text
Customer
   |
   +---- Order
   |       |
   |       +---- Order Items
   |       |
   |       +---- Delivery
   |
   +---- Custom Box
           |
           +---- Custom Box Items
```

---

## Store & Inventory

The platform also models physical stores and their inventory.

### Models

- `Store`
- `StoreInventory`

This separation provides a foundation for features such as:

- Store discovery
- Product availability
- Store-specific inventory
- Location-based purchasing
- Pickup workflows

---

# Loyalty & Rewards

Loyalty is one of the major domains of the Connect platform.

### Models

- `CustomerLoyaltyProfile`
- `IcecoinTransaction`
- `LoyaltyTier`
- `Reward`
- `RewardRedemption`

The architecture separates the customer's loyalty profile from individual IceCoin transactions and reward redemptions.

```text
Customer
    |
    v
Loyalty Profile
    |
    +---- IceCoin Transactions
    |
    +---- Loyalty Tier
    |
    +---- Reward Redemptions
                 |
                 v
              Rewards
```

This provides a foundation for a scalable loyalty and rewards system.

---

# Gamification

The platform was designed with a significant gamification layer.

### Models

- `Game`
- `GameSession`
- `Challenge`
- `UserChallengeProgress`
- `Achievement`
- `UserAchievement`
- `LeaderboardEntry`

These entities provide the foundation for:

- Interactive games
- Game sessions
- Customer challenges
- Challenge progress
- Achievements
- User progression
- Leaderboards

The architecture allows engagement activities to be tracked independently from the core commerce system.

---

# Community

The Connect platform also includes a social/community domain.

### Models

- `CommunityPost`
- `PostLike`
- `PostComment`
- `FlavorReview`
- `ReviewLike`
- `ReviewReport`

Community posts and product/flavor reviews are modeled separately because they serve different purposes.

```text
Community
    |
    +---- Posts
    |      |
    |      +---- Likes
    |      +---- Comments
    |
    +---- Flavor Reviews
           |
           +---- Likes
           +---- Reports
```

---

# Recipes & Content

The project includes a content-oriented recipe system.

### Models

- `Recipe`
- `RecipeCategory`
- `RecipeView`

Recipes are separated from their categories and view activity, creating a foundation for future content organization and engagement analytics.

---

# Campaigns & Referrals

The platform contains a dedicated campaign and referral domain.

### Models

- `Campaign`
- `CampaignParticipation`
- `Referral`
- `ReferralMilestone`

This structure provides a foundation for customer engagement campaigns and referral-based activities.

Potential use cases include:

- Promotional campaigns
- Customer participation tracking
- Referral programs
- Referral milestones
- Campaign-based rewards

---

# Health & Nutrition

The project models health-related customer information separately from product nutrition data.

### Models

- `HealthProfile`
- `HealthLog`
- `FlavorNutrition`

This allows the platform to maintain a distinction between:

**Customer health information**

and

**Product/flavor nutritional information.**

The repository establishes the domain foundation for future personalized nutrition-related functionality.

---

# News & Brand Content

The project includes several content-management entities.

### Models

- `NewsArticle`
- `LegacyStory`
- `CarouselBanner`
- `AppSetting`

These components can support:

- News
- Brand stories
- Promotional content
- Homepage banners
- Application-level configuration

---

# Notifications & Activity Tracking

The application also contains notification and activity-tracking models.

### Models

- `Notification`
- `PushNotificationLog`
- `ActivityLog`

This provides a foundation for:

- In-app notifications
- Push notification tracking
- User activity logging
- Engagement monitoring

---

# Technology Stack

## Backend

- **PHP 8.2+**
- **Laravel 12**
- **Laravel Eloquent ORM**

## Frontend / Build Tools

- **Vite**
- **Tailwind CSS**
- **JavaScript**
- **Axios**

## Database

Laravel's database configuration supports common relational database systems, with SQLite configured as the default development database.

Supported database drivers include:

- SQLite
- MySQL
- MariaDB
- PostgreSQL
- SQL Server

## Testing

- PHPUnit
- Laravel testing infrastructure

## Package Management

- Composer
- npm

---

# Repository Structure

```text
connect-DLTD/
|
├── app/
│   ├── Http/
│   │   └── Controllers/
│   │
│   ├── Models/
│   │   └── Domain Models
│   │
│   └── Providers/
│
├── bootstrap/
│
├── config/
│
├── database/
│   ├── factories/
│   ├── migrations/
│   └── seeders/
│
├── public/
│
├── resources/
│   ├── css/
│   ├── js/
│   └── views/
│
├── routes/
│   ├── web.php
│   └── console.php
│
├── storage/
│
├── tests/
│   ├── Feature/
│   └── Unit/
│
├── artisan
├── composer.json
├── package.json
├── phpunit.xml
├── vite.config.js
└── README.md
```

---

# Domain Models

The repository contains a broad set of Laravel Eloquent models representing the platform's planned business domains.

### Customer

```text
User
OtpVerification
PasswordResetToken
HealthProfile
HealthLog
Notification
ActivityLog
```

### Commerce

```text
Product
Flavor
FlavorNutrition
FlavorPassportEntry
Order
OrderItem
CustomBox
CustomBoxItem
Delivery
Store
StoreInventory
```

### Loyalty

```text
CustomerLoyaltyProfile
IcecoinTransaction
LoyaltyTier
Reward
RewardRedemption
```

### Gamification

```text
Game
GameSession
Challenge
UserChallengeProgress
Achievement
UserAchievement
LeaderboardEntry
```

### Community

```text
CommunityPost
PostLike
PostComment
FlavorReview
ReviewLike
ReviewReport
```

### Content

```text
Recipe
RecipeCategory
RecipeView
NewsArticle
LegacyStory
CarouselBanner
```

### Marketing & Growth

```text
Campaign
CampaignParticipation
Referral
ReferralMilestone
```

### System

```text
AppSetting
PushNotificationLog
```

---

# Development Setup

## Requirements

Before running the project, install:

- PHP 8.2 or newer
- Composer
- Node.js
- npm
- SQLite or another supported relational database

---

## Installation

Clone the repository:

```bash
git clone https://github.com/codebyrifaf/connect-DLTD.git
cd connect-DLTD
```

Install PHP dependencies:

```bash
composer install
```

Install frontend dependencies:

```bash
npm install
```

Create the environment file:

```bash
cp .env.example .env
```

Generate the Laravel application key:

```bash
php artisan key:generate
```

Configure the database in `.env`.

For a local SQLite setup:

```bash
touch database/database.sqlite
```

Then configure:

```env
DB_CONNECTION=sqlite
```

Run migrations:

```bash
php artisan migrate
```

Build the frontend assets:

```bash
npm run build
```

Start the Laravel development server:

```bash
php artisan serve
```

For frontend development with Vite:

```bash
npm run dev
```

---

# Development Workflow

A typical development workflow is:

```text
Requirement
     |
     v
Domain Design
     |
     v
Eloquent Model
     |
     v
Migration
     |
     v
Factory / Seeder
     |
     v
Controller / Service
     |
     v
API / Web Route
     |
     v
Frontend Integration
     |
     v
Testing
```

The repository currently represents the earlier architectural stages of this workflow, particularly domain modeling and Laravel project structure.

---

# Current Project Status

The repository should be considered a **backend foundation / architectural prototype**, rather than a completed production application.

### Implemented / Established

- Laravel 12 project
- PHP backend structure
- Eloquent model structure
- Large domain model set
- Migration structure
- Factory structure
- Seeder structure
- Authentication foundation
- Database configuration
- Vite frontend tooling
- Tailwind CSS setup
- PHPUnit testing infrastructure

### Planned / Not Fully Implemented

The repository does not currently contain complete implementations for:

- Full REST API layer
- Domain controllers
- Complete Eloquent relationships
- Complete business logic
- Production database schema
- Fully populated factories
- Production seed data
- Complete ordering workflow
- Payment processing
- Delivery tracking
- Full loyalty engine
- Complete gamification engine
- Production community functionality
- Push notification delivery infrastructure
- Complete frontend application

The distinction is intentional: the repository documents the **architectural and domain foundation** of the Connect platform.

---

# Engineering Focus

The main engineering focus of this project was establishing a scalable structure for a large multi-domain application.

Instead of placing all functionality around a single customer or product model, the architecture separates the platform into distinct business domains.

This makes it possible to independently develop and evolve:

```text
Commerce
Loyalty
Gamification
Community
Content
Campaigns
Health
Customer Management
Notifications
Store Management
```

while maintaining the customer account as a common platform entity.

---

# Internship Contribution

This project was developed as part of my internship experience at **DLTD Software Company**.

My work involved software engineering around the Connect platform's backend foundation and domain architecture.

The project provided practical experience working with:

- Laravel application architecture
- PHP backend development
- Eloquent ORM
- Relational data modeling
- Database migration design
- Domain decomposition
- Authentication infrastructure
- Backend project organization
- Large-scale feature planning
- Software architecture for interconnected business domains

The project also provided exposure to designing software for a real business context rather than an isolated academic assignment.

---

# Relationship With SavoyConnect Prototype

This repository is related to another internship project, **SavoyConnect**, but the two projects represent different aspects of the product development process.

### SavoyConnect Prototype

Focused primarily on:

- User experience
- Application screens
- User journeys
- Product interaction
- Customer-facing features
- High-fidelity frontend prototyping

### Connect DLTD

Focused primarily on:

- Backend architecture
- Domain modeling
- Laravel structure
- Data modeling
- Business entities
- Backend foundation

Together, they represent different layers of the broader Connect platform concept.

---

# Future Development

The architecture can be extended toward a production-ready platform by implementing:

1. Complete database schemas
2. Eloquent relationships
3. Domain services
4. RESTful API endpoints
5. Authentication APIs
6. Authorization and roles
7. Product and inventory management
8. Complete order processing
9. Payment integration
10. Delivery management
11. Loyalty and IceCoin business rules
12. Reward redemption workflows
13. Gamification services
14. Community APIs
15. Recipe/content APIs
16. Campaign management
17. Referral processing
18. Notification infrastructure
19. Automated tests
20. Production deployment infrastructure

---

# Key Takeaways

The project demonstrates the design of a **large, interconnected customer engagement platform** using Laravel.

Rather than focusing on a single feature, the architecture establishes separate domains for:

- Commerce
- Customer management
- Loyalty
- Gamification
- Community
- Content
- Marketing
- Health and nutrition
- Store management
- Notifications

The repository therefore serves as a foundation for building a much larger digital platform while maintaining separation between major business concerns.

---

# Project Information

**Project:** Connect DLTD  
**Organization:** DLTD Software Company  
**Context:** Internship Project  
**Role:** Software Engineering / Backend Development  
**Framework:** Laravel 12  
**Language:** PHP  
**Database:** Relational Database  
**Build Tools:** Vite, npm  
**Testing:** PHPUnit  

---

# Author

**Rifaf**

Software Engineering Graduate  
Islamic University of Technology (IUT)

GitHub: [codebyrifaf](https://github.com/codebyrifaf)

---

# Acknowledgements

Developed as part of my
