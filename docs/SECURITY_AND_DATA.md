# Security and dataset handling for public sharing

## Excluded from this GitHub starter

- Local `.env` and other settings containing credentials; private keys and tokens
- `db.sqlite3` (may contain accounts, uploaded file metadata, history or access tokens)
- `media/`, `staticfiles/`, original uploaded CSV/XES/Parquet files and runtime outputs
- `prediction/trained_models/` and the duplicate Group 7 trained models / serialized objects
- Local Python virtual environments, Git history from a teammate's separate project archive, caches and machine files
- Test license seeding command with predictable license codes

## Small source hardening applied in portfolio snapshot

1. `config/settings.py`: require an environment-provided `SECRET_KEY` and default `DEBUG=False`.
2. `accounts/management/commands/seed_admin.py`: require a provided admin password instead of using the original predictable fallback. Prefer `createsuperuser`.
3. `accounts/management/commands/create_license_codes.py`: use cryptographically secure randomness instead of `random.choices`.
4. `config/urls.py`: restore the `/uploads/` route that was accidentally swallowed by an inline source comment.

These changes were made **only to this GitHub export** and may need full integration testing. This is **not** a security audit. Review permissions, uploads, model deserialization, password policy, settings and environment configuration before production deployment.

## Data rights and models

Real user/event-log uploads, trained weights, `.pkl` files and personal information are *not* redistributed by default. A team agreement to publish the project code does not by itself guarantee rights to publish third-party event logs or model training data. Serialized Python objects (pickle/joblib) must be treated as untrusted unless their provenance is confirmed; loading can execute arbitrary code.
