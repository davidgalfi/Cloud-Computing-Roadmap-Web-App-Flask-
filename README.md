# Cloud Roadmap App (Flask)

An interactive Flask web application to plan and track a Cloud Computing learning journey from beginner to expert. It features:
- Interactive roadmap with task states: todo → in_progress → done
- Streak counter based on daily/weekly learning activity
- Learning-period planner: target completion in N weeks/months/years
- Animated, modern UI (CSS animations, micro-interactions)
- Extensible structure for new tracks, tasks, and features

## Quick start

### Prerequisites
- Python 3.11+
- pip
- Node (optional, if you later add a build step)

### Setup
```
git clone <your-repo-url> cloud-roadmap-app
cd cloud-roadmap-app
python -m venv .venv
source .venv/bin/activate # Windows: .venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env
flask --app wsgi run --debug
```


Visit http://127.0.0.1:5000.

### Configuration
Set environment variables in `.env`:
```
FLASK_ENV=development
SECRET_KEY=change-me
DATABASE_URL=sqlite:///app.db
```

### Roadmap data
Roadmaps live as YAML/JSON in `app/seeds/`. Use `sample_roadmap.yaml` as a template. You can swap in your own generated roadmaps here, or later via an admin UI.

### Core concepts

- Task lifecycle: `todo` → `in_progress` → `done`
- Streaks: increments when learning activity is recorded for a day; breaks if no activity
- Learning period planner: choose target duration and weekly hours; system distributes suggested pace and shows a progress bar
- Extensibility: add new tracks/modules as YAML; services calculate progress; API supplies the UI

### Tech stack
- Flask, Jinja2
- SQLite (default) via SQLAlchemy (optional later; initial version uses in-memory store for simplicity)
- Vanilla JS for interactivity; progressively enhance with your preferred frontend later

### Scripts
```
./scripts/dev.sh # run dev server with auto-reload
./scripts/format.sh # format with black + isort
./scripts/lint.sh # lint with flake8
```


### Testing
```
pytest -q
```


### Deployment
- Add a proper DB (Postgres) and set `DATABASE_URL`
- Use the provided `Procfile` and `wsgi.py` on platforms like Render/Heroku/Fly.io
- Set `FLASK_ENV=production` and a strong `SECRET_KEY`

### Roadmap (project)
- [ ] Auth (email, OAuth) and user profiles
- [ ] Persistent DB models (Users, Roadmaps, Tasks, ActivityLogs)
- [ ] Import/export roadmaps (YAML/JSON)
- [ ] Advanced scheduler (auto-plan with weekly hours)
- [ ] Streak widgets, badges, and reminders
- [ ] Offline-capable PWA
- [ ] Rich animations and theming
- [ ] Admin UI for roadmap authoring

### Contributing
See CONTRIBUTING.md and CODE_OF_CONDUCT.md.

### Security
See SECURITY.md.

### License
MIT
