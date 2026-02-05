# EasyInterview Development Guidelines

## Project Overview
EasyInterview is an AI-powered interview coaching platform that provides real-time feedback on both verbal responses and non-verbal cues during mock interviews.

## Key Technical Decisions

### Architecture
- **Client-side heavy**: All processing happens in the browser for privacy
- **Serverless approach**: Direct API communication with Google Gemini
- **Real-time processing**: Uses Web APIs for speech and video analysis

### Core Technologies
- **Frontend**: React 18 + TypeScript + Tailwind CSS
- **AI Engine**: Google Gemini 2.5 (Multimodal)
- **Speech**: Web Speech API (STT/TTS)
- **Video**: MediaStream API for webcam access
- **Build Tool**: Vite

### Performance Requirements
- Speech-to-Text latency: < 500ms
- AI response generation: < 2-3 seconds
- Video analysis: minimum 15 FPS

### Privacy & Security
- Local-first processing for video streams
- Ephemeral data - no permanent storage
- API keys secured via environment variables

## Development Standards

### Code Style
- Use TypeScript for all components
- Follow React 18 patterns (hooks, functional components)
- Implement proper error boundaries
- Use Tailwind for consistent styling

### Component Structure
- Keep components focused and single-responsibility
- Use custom hooks for complex logic (useSpeech, useMediaStream)
- Lift state to App.tsx for global session data
- Implement proper loading and error states

### Testing Approach
- Focus on critical user flows
- Test browser API integrations
- Validate AI prompt engineering
- Ensure cross-browser compatibility (Chrome, Edge, Brave)

## Hackathon Considerations
- Prioritize core functionality over polish
- Demonstrate multimodal AI capabilities
- Show real-time feedback in action
- Prepare demo scenarios with clear value proposition
