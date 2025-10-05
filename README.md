# STEPS

We're using Python (need >=3.10). You must first sign up to [LiveKit Cloud](https://cloud.livekit.io/). And create a LK project to link this code project to.

-   `brew install livekit-cli` to install the LK CLI in your system. We use this extensively when scaffolding our project.

-   `lk cloud auth`. Associates this project with your LK project.

-   [OpenAI Realtime API](https://platform.openai.com/docs/guides/realtime)

-   From inside the repo root initialize `uv` with `uv init . --bare`. This sets up a `pyproject.toml` file.

-   We dont want to use the STT-LLM-TTS pipeline. For more life-life voice experiences we want to use the realtime models. The following command installs the OpenAI Realtime SDK and [Krisp](https://krisp.ai/) noise cancellation. It could take a minute.

```
uv add \
  "livekit-agents[openai]~=1.2" \
  "livekit-plugins-noise-cancellation~=0.2" \
  "python-dotenv"
```

-   `touch .gitignore` and add the following to your .gitignore

```
# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
env/
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
*.egg-info/
.installed.cfg
*.egg
.pytest_cache/

# Virtual Environments
venv/
.venv/

# Environment variables
.env
.env.*

# uv specific
.uv/
.venv/

# IDE specific files
.idea/
.vscode/
*.swp
*.swo
.DS_Store

```

-   Run the following command to populate your LiveKit Cloud API keys into a .env.local file: `lk app env -w`. Inspect it to make suer you have the following:

```
LIVEKIT_API_KEY
LIVEKIT_API_SECRET
LIVEKIT_URL
NEXT_PUBLIC_LIVEKIT_URL
```

-   `touch agent.py` and add the Realtime Agent code. Then `uv run agent.py download-files` and this will download the model files which can be quite large. We need to download these models to use the `turn-detector`, `silero`, and `noise-cancellation` plugins,

-
