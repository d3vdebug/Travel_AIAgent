# Sacred Trails India - Travel Booking Agent

# [Demo Video (Linkedin)](https://www.linkedin.com/feed/update/urn:li:ugcPost:7402762913830264832)

> [!IMPORTANT]
> _This project was developed for the Murf AI Voice Agent Hackathon at TechFest IIT Bombay.
It is built on top of Murf AI’s official demo repository, which was cloned and used solely for initial setup and environment configuration.
All core features, integrations, and customizations — including the design and implementation of the Sacred Trails India AI Voice Agent travel booking system — were independently developed during the hackathon.
I hereby declare that this submission represents my original work, created within the hackathon timeline, while appropriately leveraging the provided demo resources._

## About the Agent
'Sacred Trails India' is an AI Voice Agent powered travel booking system that revolutionizes travel planning and booking for destinations across India.



## Repository Structure

This is a **monorepo** that contains both the backend and frontend for building voice agent applications. It's designed to be your starting point for each day's challenge task.

```
Travel_Booking_Agent/
├── backend/          # LiveKit Agents backend with Murf Falcon TTS
├── frontend/         # React/Next.js frontend for voice interaction
├── start_app.sh      # Convenience script to start all services
└── README.md         # This file
```

### Backend

The backend is based on [LiveKit's agent-starter-python](https://github.com/livekit-examples/agent-starter-python) with modifications to integrate **Murf Falcon TTS** for ultra-fast, high-quality voice synthesis.

**Features:**

- Complete voice AI agent framework using LiveKit Agents
- Murf Falcon TTS integration for fastest text-to-speech
- LiveKit Turn Detector for contextually-aware speaker detection
- Background voice cancellation
- Integrated metrics and logging
- Complete test suite with evaluation framework
- Production-ready Dockerfile

[→ Backend Documentation](./backend/README.md)

### Frontend

The frontend is based on [LiveKit's agent-starter-react](https://github.com/livekit-examples/agent-starter-react), providing a modern, beautiful UI for interacting with your voice agents.

**Features:**

- Real-time voice interaction with LiveKit Agents
- Camera video streaming support
- Screen sharing capabilities
- Audio visualization and level monitoring
- Light/dark theme switching
- Highly customizable branding and UI

[→ Frontend Documentation](./frontend/README.md)

## Quick Start

### Prerequisites

Make sure you have the following installed:

- Python 3.9+ with [uv](https://docs.astral.sh/uv/) package manager
- Node.js 18+ with pnpm
- [LiveKit CLI](https://docs.livekit.io/home/cli/cli-setup) (optional but recommended)
- [LiveKit Server](https://docs.livekit.io/home/self-hosting/local/) for local development

### 1. Clone the Repository

```bash
git clone https://github.com/d3vdebug/Travel_AIAgent.git

```

### 2. Backend Setup

```bash
cd backend

# Install dependencies
uv sync

# Copy environment file and configure
cp .env.example .env.local

# Edit .env.local with your credentials:
# - LIVEKIT_URL
# - LIVEKIT_API_KEY
# - LIVEKIT_API_SECRET
# - MURF_API_KEY (for Falcon TTS)
# - GOOGLE_API_KEY (for Gemini LLM)
# - DEEPGRAM_API_KEY (for Deepgram STT)
# - MONGODB_URI
# - MONGODB_DB_NAME
# - MONGODB_COLLECTION
# - SMTP_EMAIL (for booking confirmations)
# - SMTP_PASSWORD (for booking confirmations)

# Download required models
uv run python src/agent.py download-files
```

For MongoDB Atlas Cloud Setup:

```bash
cd backend
npm install mongodb

```

For LiveKit Cloud users, you can automatically populate credentials:

```bash
lk cloud auth
lk app env -w -d .env.local

```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
pnpm install

# Copy environment file and configure
cp .env.example .env.local

# Edit .env.local with the same LiveKit credentials
```

### 4. Run the Application

#### Install livekit server

```bash
brew install livekit
```

You have two options:

#### Option A: Use the convenience script (runs everything)

```bash
# From the root directory
chmod +x start_app.sh
./start_app.sh
```

This will start:

- LiveKit Server (in dev mode)
- Backend agent (listening for connections)
- Frontend app (at http://localhost:3000)

#### Option B: Run services individually

```bash
# Terminal 1 - LiveKit Server
livekit-server --dev

# Terminal 2 - Backend Agent
cd backend
uv run python src/agent.py dev

# Terminal 3 - Frontend
cd frontend
pnpm dev
```

Then open http://localhost:3000 in your browser!


## Documentation & Resources

- [Murf Falcon TTS Documentation](https://murf.ai/api/docs/text-to-speech/streaming)
- [LiveKit Agents Documentation](https://docs.livekit.io/agents)
- [Original Backend Template](https://github.com/livekit-examples/agent-starter-python)
- [Original Frontend Template](https://github.com/livekit-examples/agent-starter-react)

## Testing

The backend includes a comprehensive test suite:

```bash
cd backend
uv run pytest
```

Learn more about testing voice agents in the [LiveKit testing documentation](https://docs.livekit.io/agents/build/testing/).

# How to Use Sacred Trails India
## Sample Conversation Flow
1. Greeting: The AI agent introduces itself as "Nikhil" from Sacred Trails India
2. Destination Selection: "I want to plan a trip to Goa"
3. Travel Details: Provide dates, number of travelers, origin city
4. Preferences: Specify budget range and desired amenities
5. Travel Mode: Choose from available transport options with cost calculations
6. Hotel Selection: Review and select from AI-recommended hotels
7. Contact Details: Provide name, mobile number, and email
8. Booking Confirmation: Receive booking ID and email confirmation

## Example Commands
- "I want to travel to Mumbai from Delhi"
- "My budget is medium, and I prefer hotels with Wi-Fi and breakfast"
- "Show me travel options to Goa"
- "What's my booking status for booking ID ABC12345?"
- "Cancel my booking ABC12345"

## License

This project is based on MIT-licensed templates from LiveKit and includes integration with Murf Falcon. See individual LICENSE files in backend and frontend directories for details.
