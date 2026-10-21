# course-catalog-api

Standalone FastAPI backend for the course catalog (moved from `lib/courses.ts`) — Advanced Web Technologies, Aimabek Aidar, IT3-2301.

## How to run

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\Activate.ps1
pip install -r requirements.txt
fastapi dev main.py
```

Open http://127.0.0.1:8000/docs for the interactive documentation.

## What was verified

| Request | Result |
| --- | --- |
| `GET /` | 200, `{"message": "Course Catalog API is running"}` |
| `GET /courses` | 6 courses, `ai-integration` first (32 likes), `api-design` last (11) |
| `GET /courses?is_elective=true` | 2: ai-integration, api-design |
| `GET /courses?is_elective=false` | 4: modern-frontend, web-security, backend-fastapi, databases-postgresql |
| `GET /courses?sort=title` | 6 alphabetically: ai-integration, api-design, backend-fastapi, modern-frontend, databases-postgresql, web-security |
| `GET /courses?page=1&page_size=2` | ai-integration, modern-frontend |
| `GET /courses?page=2&page_size=2` | web-security, backend-fastapi |
| `GET /courses?page=3&page_size=2` | databases-postgresql, api-design |
| `GET /courses?page=4&page_size=2` | `[]` |
| `GET /courses/web-security` | 200, one course |
| `GET /courses/nope` | 404, `{"detail": "Course not found"}` |
| `/docs` | exactly three routes: `GET /`, `GET /courses`, `GET /courses/{course_id}` |
