# systemArchitecture

Overview
This document describes the technical structure of Lumit, including the main components, data flow, and rationale for key technology choices. The design prioritizes modularity, scalability, and accessibility.

Frontend
The frontend is a responsive web or mobile interface that lets users upload materials, select characters, configure language and accessibility settings, and interact with AI-driven lessons. The UI includes the home screen, character selection, learning dashboard, settings, and accessibility panels. Recommended frontend frameworks include React for web and Flutter for cross-platform mobile, chosen for component-based design and performance on low-end devices.

Backend
The backend handles file ingestion, document parsing, session management, AI orchestration, and user authentication. A service layer accepts uploaded documents, extracts text and structure, and prepares content for the AI engine. The backend also coordinates avatar rendering and voice synthesis requests. Recommended backend frameworks include Node.js with Express or a Python option such as FastAPI for flexible API design.

AI and media services
Natural language understanding and conversational logic are provided by large language model APIs. Text-to-speech services provide character voice output. Avatar and animation generation are handled by specialized media services or third-party solutions that accept script-like inputs and produce short animated segments. A modular approach allows swapping service providers as costs, quality, or latency change.

Database and storage
A relational or document database stores user profiles, preferences, learning history, session transcripts, and analytics. Recommended options include PostgreSQL or MongoDB depending on the data model. Uploaded files and generated media assets are stored in cloud object storage to optimize delivery and reduce backend load.

Component communication and flow
1. The frontend sends a document upload request to the backend.
2. The backend extracts and structures content, creating lesson segments.
3. The backend requests AI-generated explanations from the language service.
4. Generated text is routed to voice synthesis and avatar rendering services as needed.
5. The backend returns interactive content and streams responses to the frontend in near real time.
6. User interactions and questions are sent back to the backend for context-aware responses.

Accessibility and multilingual support
Language selection is available at the user or session level. Text and voice outputs are generated in the selected language or regional variation. Sign language avatar output is prepared by converting AI-generated scripts into avatar animations and subtitles. Accessibility features are configurable in the settings screen.

Security and privacy
All user uploads and session data are transmitted over secure connections and stored with encryption at rest. Authentication should support modern standards such as OAuth2 and multi-factor authentication for institutional accounts. Privacy policies must be clear about data usage, retention, and deletion options.

Scalability and deployment
Microservice architecture is recommended to separate concerns such as document processing, AI orchestration, media generation, and analytics. Containerization with orchestration services supports horizontal scaling. CDN-backed delivery ensures media assets are served efficiently to users across regions.

Operational considerations
1. Monitor latency and costs for AI and media services to maintain a balance between responsiveness and operating expenses.
2. Implement logging and analytics to measure engagement, lesson completion, and retention.
3. Design fallback modes for low-bandwidth users such as audio-only explanations or downloadable lesson packets.

Next steps
1. Define the MVP scope focusing on PDF ingestion, single-character interaction, Q&A, and language selection.
2. Implement a prototype that demonstrates document-to-lesson conversion and live Q&A with a single character voice.
3. Test accessibility modes including subtitle rendering and a basic sign language avatar output.

Diagram note
A simple architectural diagram showing frontend, backend, AI services, storage, and CDN is recommended for visual clarity. This diagram can be created in draw.io, Miro, or a similar tool and added to the repository as an image file.
