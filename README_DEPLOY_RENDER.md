# NutriFriend API – Deploy on Render (Blueprint)

## Recommended approach (Blueprint)
1. Create a new GitHub repo and push this `backend_api/` folder.
2. In Render, choose **New +** → **Blueprint** and point it at your repo.
3. Render will create:
   - a Docker web service (`nutrifriend-api`)
   - a managed Postgres database (`nutrifriend-db`)

## Required environment variables
This code reads from `.env` locally and from environment variables in production.
- `DATABASE_URL` (Render provides from the database)
- `JWT_SECRET_KEY` (Render can generate)
- `CORS_ORIGINS` (set to your Expo Update / web origins if you want to restrict)

## One-time seeding
After deploy, you can seed initial admin/foods by running `python seed.py` locally against the Render DB
or by creating an admin endpoint in Admin UI.

## Health check
`GET /` returns status OK.

