# NutriFriend Backend (FastAPI)

## Quick start (local)

```bash
cd backend
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

Open Swagger UI:
- http://localhost:8000/docs

## Roles
- user: patient/general user
- caregiver: authorized assistant (consent-based)
- dietitian: hospital/professional user
- admin: system administrator

## Key flows
1) Register users
- POST `/users/register`
2) Login
- POST `/auth/token` (OAuth2 password form)
3) Create caregiver link request
- POST `/caregivers/links`
4) Approve caregiver link (user)
- POST `/caregivers/links/{id}/approve`
5) Caregiver logs meal for user
- POST `/meals?user_id=<userId>`

## Production notes
- Replace JWT secret
- Use Postgres and Alembic migrations
- Enable strict CORS
- Add rate limiting and audit logging
