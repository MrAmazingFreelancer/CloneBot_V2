# CloneBot V2

## Stack
- **Runtime**: Python 3.7+
- **Library**: Pyrogram (Telegram client)
- **Tools**: Gclone v1.59.1 (Google Drive cloning engine)
- **Deployment**: Docker, Fly.io, Railway, Heroku, VPS, Termux

## Project Structure
```
telegram_gcloner/     # Main bot logic
  handlers/           # Command handlers
  config/             # Configuration
  utils/              # Helper functions
Dockerfile            # Container build
docker-compose.yml    # Multi-container setup
requirements.txt      # Python dependencies
```

## Key Patterns
- **Service Accounts**: Uses Google service accounts to bypass 750GB upload limit
- **Gclone Config**: Config file URL provided via environment variable
- **Telegram API**: Pyrogram for bot commands, user interaction
- **Cloning**: Server-side only; no local bandwidth used
- **Multi-destination**: Can clone to multiple Google Drive folders

## Common Commands
```bash
pip install -r requirements.txt    # Install dependencies
python -m telegram_gcloner         # Run locally
docker build -t clonebot .         # Build Docker image
docker-compose up                  # Run with docker-compose
```

## Configuration
- **Env vars**: `API_ID`, `API_HASH`, `BOT_TOKEN`, `CONFIG_FILE_URL`
- **Channel mapping**: Format `-source:-destination` (e.g., `-10023352648:-100655379`)
- **Service accounts**: Upload via Dr.Graph, File Stream Bot, or GitHub Gist

## Important Files
- `config.py` — Telegram API credentials, channel IDs, bot token
- `telegram_gcloner/handlers/` — Command implementations
- `Dockerfile` — Container setup
- `Procfile` — For Heroku deployment

## Notes
- Never commit credentials; use `.env` or secrets management
- Gclone must be installed in Docker image; see Dockerfile
- Test locally with Telegram test accounts before deploying to production
