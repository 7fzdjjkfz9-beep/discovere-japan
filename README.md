# Discover Japan — Independent community website

A standalone FastAPI + SQLite travel community. No Lovable/Higgsfield dependency.

## Run locally

```bash
pip install -r requirements.txt
COOKIE_SECURE=0 uvicorn app:app --reload
```

Visit http://127.0.0.1:8000.

## Deploy

Deploy this folder to any host that runs a Python web service (Render, Railway, VPS, etc.). Set start command `uvicorn app:app --host 0.0.0.0 --port $PORT`. Set `DATABASE_PATH` to a **persistent mounted disk path**, e.g. `/var/data/community.sqlite3`; without persistent storage, posts may disappear on restart. Enable HTTPS, backups, monitoring, and a proper moderation workflow before promoting widely. Default `COOKIE_SECURE=1` expects HTTPS.

## Security and limitations

- Shared posts/comments/likes, optional prefecture and categories, reports with auto-hide after 3 reports, per-cookie rate limiting, simple URL spam check, honeypot.
- HTML is escaped by Jinja2; no public file uploads; no fabricated testimonials.
- Guest cookie identity is not a robust account system; users can reset cookies to bypass limits. Production operation needs admin moderation, IP/edge abuse controls, CAPTCHA, CSRF protection, deletion/privacy request workflow, retention policy, backups, and terms/privacy pages.
- Images in Shiga guide are illustrative stock photos, not necessarily the pictured location.
