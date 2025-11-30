# Tc_ratings_schema
Prisma schema, OpenAPI docs, and migration guide replacing Informix with PostgreSQL for the Topcoder Ratings Calculation Service.
Here is a clean, professional README.md for your merged Prisma schema project.
I wrote it so you can copy–paste directly into your repo.


---

Topcoder Rating System – Prisma Schema 

This project contains a fully merged Prisma schema built from four different Topcoder-related database schemas:

1. OLTP User System


2. Data Warehouse / Ratings Schema


3. Contest & Problem Schema


4. Algo Rating & Ranking Schema



Because these schemas originally contained conflicting model names, the merge uses Option A (Renamed Models), applying clear and consistent suffixes:

Domain	Suffix	Example

OLTP System	_OLTP	User_OLTP
Data Warehouse	_DW	Coder_DW
Contest / Problem Domain	_CONTEST	Round_CONTEST
Algo / Ranking	_ALGO	coder_ALGO
App-Level Consolidated Models	_APP	CoderRating_APP


This ensures no naming conflicts, perfect separation of concerns, and safe Prisma migrations.


---

📦 Project Structure

prisma/
│── schema.prisma   # Fully merged schema
│── migrations/     # Auto-generated after running migrations
.env                # Database credentials
README.md


---

🚀 Getting Started

1️⃣ Install dependencies

npm install

2️⃣ Set the database URL

Create a .env file:

DATABASE_URL="postgresql://postgres:[096706a20B@]@db.onjipgxpenkfbzmzptyw.supabase.co:5432/postgres"

3️⃣ Validate the Prisma schema

npx prisma validate

4️⃣ Run migrations

npx prisma migrate dev --name init

5️⃣ Generate Prisma client

npx prisma generate


---

🗂 Model Domains

1. OLTP Models (_OLTP)

Contains core user and identity models:

User_OLTP

Email_OLTP

Address_OLTP

UserAddressXref_OLTP

UpdateLog_OLTP


These represent the main transactional system for users.


---

2. Data Warehouse Models (_DW)

Includes large-scale coder, state, country, and rating datasets:

Coder_DW

Country_DW

State_DW

SkillType_DW

MarathonCoderRating_DW


This domain is optimized for analytics, dashboards, and insights.


---

3. Contest & Problem Models (_CONTEST)

Models for problem statements, rounds, contests, submissions:

Contest_CONTEST

Round_CONTEST

Component_CONTEST

Problem_CONTEST

SystemTestCase_CONTEST

LongProblemSubmission_CONTEST

LongCompResult_CONTEST


This is the core Topcoder problem/contest structure.


---

4. Algo Rating Models (_ALGO)

For classical Topcoder algorithm ratings:

coder_ALGO

round_ALGO

algo_rating_history_ALGO

coder_rank_history_ALGO

state_coder_rank_ALGO

school_coder_rank_ALGO


This domain powers rankings, percentile calculations, and algorithm contest scoring.


---

5. Application-Level Models (_APP)

These models unify and simplify outputs needed for the final platform or API:

CoderRating_APP

Submission_APP

RankHistory_APP

Streak_APP

etc.


These models are meant for your API, dashboard, or client apps.


---

🛠 Development Notes

All original table names are preserved using @@map.

Renamed model suffixes ensure zero conflicts.

Relations, indexes, foreign keys, and audit fields are preserved.

Compatible with:

PostgreSQL

Prisma Client

Node.js backend

Next.js / NestJS / Express




---

📌 Why This Merge Was Necessary

Your original schemas had conflicts like:

Multiple models named User, Coder, Round, Contest, etc.

Overlapping relationships across domains

Non-unified naming conventions


The final schema:

✅ Keeps domains independent
✅ Protects original DB structure
✅ Works safely with Prisma migrations
✅ Makes future development cleaner


---

📧 Support

If you need help customizing your API, relationships, DTOs, or generating controllers/services for Node.js, NestJS, or Flask, just ask!


---

Would you like me to generate:

✅ API routes for each domain
✅ Prisma service templates
✅ CRUD operations
✅ ERD diagram of the merged schema
✅ SQL migration scripts

Just tell me!
