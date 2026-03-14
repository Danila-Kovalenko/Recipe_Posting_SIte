# Foodgram – Rezeptplattform mit Einkaufslisten

Foodgram ist eine Full-Stack-Webanwendung zum Veröffentlichen, Entdecken und Organisieren von Rezepten. Benutzer:innen können eigene Rezepte erstellen, anderen Profilen folgen, Favoriten pflegen und Zutaten aus ausgewählten Rezepten in eine persönliche Einkaufsliste übernehmen.

## Kernfunktionen

- Benutzerregistrierung und Anmeldung (Token-basierte Authentifizierung).
- Rezepte erstellen, bearbeiten, anzeigen und löschen.
- Zutaten und Tags zur strukturierten Suche/Filterung von Rezepten.
- Favoriten und persönliche Einkaufslisten.
- Autor:innen abonnieren und deren neue Rezepte verfolgen.
- Admin-Bereich über Django Admin.

## Tech-Stack

- **Backend:** Django, Django REST Framework, Djoser
- **Frontend:** React
- **Datenbank:** PostgreSQL
- **Infra/Deployment:** Docker Compose + Nginx

## Projektstruktur

- `backend/` – Django-Projekt mit API, Modellen und Admin.
- `frontend/` – React-Frontend.
- `infra/` – Docker-Compose- und Nginx-Konfiguration.

## Schnellstart mit Docker

### 1) Repository klonen

```bash
git clone <DEIN_REPO_LINK>
cd Recipe_Posting_SIte
```

### 2) Umgebungsvariablen anlegen

Erstelle die Datei `infra/.env` (Beispiel):

```env
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
SECRET_KEY=change-me
DEBUG=False
```

### 3) Container starten

```bash
cd infra
docker-compose up -d --build
```

### 4) Migrationen, statische Dateien, Admin-User

```bash
docker-compose exec backend python manage.py migrate
docker-compose exec backend python manage.py collectstatic --noinput
docker-compose exec backend python manage.py createsuperuser
```

### 5) Testdaten laden (optional)

```bash
docker-compose exec backend python manage.py load_data
```

## Lokale Entwicklung (ohne Docker)

```bash
cd backend
python -m venv venv
source venv/bin/activate  # unter Windows: venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
python manage.py migrate
python manage.py collectstatic --noinput
python manage.py runserver
```

Optional können Testdaten geladen werden:

```bash
python manage.py load_data
```

## API und Oberfläche

- Backend/API lokal: `http://127.0.0.1:8000/`
- Admin: `http://127.0.0.1:8000/admin/`
- API-Endpunkte: `http://127.0.0.1:8000/api/`

Bei Docker-Start über Nginx ist die Anwendung typischerweise unter Port `80` erreichbar.
