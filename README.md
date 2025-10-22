# Vimeo Clipper

A Flask web application that downloads Vimeo videos, transcribes them using Deepgram, and generates AI-powered profiles using OpenAI.

## Features

- Download Vimeo videos using the Vimeo API
- Transcribe audio using Deepgram's speech-to-text service
- Generate AI profiles using OpenAI's GPT-4
- Web interface for easy interaction

## Deployment to Render

### Prerequisites

1. A Render account
2. API keys for:
   - OpenAI (for GPT-4 profile generation)
   - Deepgram (for audio transcription)
   - Vimeo (for video access)

### Deployment Steps

1. **Push your code to GitHub** (if not already done)
2. **Connect to Render:**
   - Go to [Render Dashboard](https://dashboard.render.com)
   - Click "New +" → "Web Service"
   - Connect your GitHub repository
   - Select the `GMNG` folder as the root directory

3. **Configure Environment Variables:**
   - In Render dashboard, go to your service settings
   - Add the following environment variables:
     - `OPENAI_API_KEY`: Your OpenAI API key
     - `DEEPGRAM_API_KEY`: Your Deepgram API key
     - `VIMEO_ACCESS_TOKEN`: Your Vimeo access token

4. **Deploy:**
   - Render will automatically build and deploy your application
   - The service will be available at `https://your-app-name.onrender.com`

### Local Development

1. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Set up environment variables:**
   - Copy `env.example` to `.env`
   - Fill in your API keys

3. **Run the application:**
   ```bash
   python app.py
   ```

## API Endpoints

- `GET /`: Main web interface
- `POST /api/run_pipeline`: Process a Vimeo video (download + transcribe)
- `POST /api/generate-profile`: Generate AI profile from text

## File Structure

```
GMNG/
├── app.py                          # Main Flask application
├── requirements.txt                # Python dependencies
├── Procfile                       # Render deployment configuration
├── render.yaml                    # Advanced Render configuration
├── env.example                    # Environment variables template
├── VimeoTools/                    # Core functionality modules
│   ├── videoDownloader.py        # Vimeo video download
│   └── deepgramTranscriber.py    # Audio transcription
└── MatchMakingUI/                 # Web interface
    └── bio_psycho_social_generator_clean.html
```

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `OPENAI_API_KEY` | OpenAI API key for GPT-4 | Yes |
| `DEEPGRAM_API_KEY` | Deepgram API key for transcription | Yes |
| `VIMEO_ACCESS_TOKEN` | Vimeo API access token | Yes |

## Notes

- The application runs on port 5000 by default
- Render will automatically assign a port via the `PORT` environment variable
- Debug mode is disabled in production for security
- All API keys should be kept secure and not committed to version control
