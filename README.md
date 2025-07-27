# Inventory Dashboard – Flask App

Un tableau de bord web pour gérer un parc informatique (PC, écrans, etc.), avec authentification, recherche, filtres et audit des modifications.  
Développé avec **Flask**, **SQLAlchemy**, **Bootstrap 5** et **WTForms**.



## Fonctionnalités

- Authentification avec rôles (`admin`, `technicien`)
- CRUD complet pour les équipements
- Recherche & filtres dynamiques
- Sélecteur de date et validation WTForms
- Export CSV des données
- Pagination automatique
- Historique des modifications (audit log)
- Templates HTML responsive (Bootstrap)
- Pages d’erreurs stylisées (`403`, `404`)



## Architecture du projet

```

inventory-dashboard/
├── app/
│   ├── __init__.py
│   ├── models.py
│   ├── auth.py
│   ├── forms.py
│   ├── routes.py
│   └── extensions.py
├── static/
│   └── js/
│       ├── filters.js
│       └── date\_picker.js
├── templates/
│   ├── search.html
│   ├── home.html
│   ├── edit_equipment.html
│   ├── layout.html
│   ├── dashboard.html
│   ├── login.html
│   ├── equipment_form.html
│   ├── equipment_details.html
│   ├── 403.html / 404.html
│   └── _filters.html
├── run.py
├── init_db.py
├── MANUAL.md
├── README.md
└── requirements.txt
```

## Installation locale

### 1. Cloner le projet

```bash
git clone https://github.com/Mfoucault002/inventory-dashboard.git
cd inventory-dashboard
````

### 2. Créer un environnement virtuel

```bash
python -m venv venv
source venv/bin/activate      # Linux/macOS
venv\Scripts\activate         # Windows
```

### 3. Installer les dépendances

```bash
pip install -r requirements.txt
```

### 4. Lancer l'application

```bash
flask --app run.py run
```


## Comptes de test

Créer manuellement un compte admin depuis le shell Python :

```bash
flask --app run.py shell
>>> from app import db
>>> from app.models import User
>>> from werkzeug.security import generate_password_hash
>>> admin = User(username="admin", password=generate_password_hash("adminpass"), role="admin")
>>> db.session.add(admin)
>>> db.session.commit()
```


## Tests (à venir)

Des tests unitaires peuvent être ajoutés avec **pytest** ou **unittest**.


## 🛰️ Déploiement (Render / PythonAnywhere)

* Crée un fichier `.env` pour contenir `SECRET_KEY` et URI de la base
* Utilise un serveur WSGI (ex: Gunicorn)
* Rends la config SQLAlchemy adaptable avec `os.getenv("DATABASE_URL")`


## À propos

* Auteur : \Mfoucault002
* Projet de démonstration pour reconversion pro dans l'informatique / portfolio


## Licence

Ce projet est libre d’utilisation à des fins pédagogiques.

```
