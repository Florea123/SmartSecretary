# SmartSecretary

**Smart University Secretary System** - An intelligent platform for automating and optimizing university administrative processes with AI integration for advanced conversational assistance.

## 📋 Description

SmartSecretary is a modern and integrated solution that digitalizes and automates administrative processes in the university environment. The system combines an intuitive web interface with artificial intelligence capabilities to provide real-time support to students and university staff.

### Key Features

- 🎓 **Student Management**: Registration, authentication, and profile administration
- 📋 **Digital Forms**: Creation, completion, and automated management of university forms
- 🤖 **AI Assistant**: Intelligent chatbot with RAG technology for contextual responses
- 📅 **Calendar System**: Management of events, exams, and academic schedules
- 🎫 **Ticketing System**: Request management and communication with secretariat
- 📄 **Document Processing**: Upload, conversion, and automated processing of PDF/DOCX documents
- 🎙️ **Audio Transcription**: Conversion of audio recordings to text using Whisper AI
- 📊 **Administration Dashboard**: Dedicated interfaces for administrators and secretariat staff

## 🏗️ System Architecture

### Backend (Spring Boot)
- **Framework**: Spring Boot 3.4.4 with Java 17
- **Database**: PostgreSQL with Spring Data JPA
- **Security**: JWT Authentication + Spring Security
- **API Documentation**: SpringDoc OpenAPI (Swagger)
- **Email Services**: SendGrid
- **Document Processing**: Apache PDFBox, Apache POI for DOCX
- **Port**: 8081

### Frontend (Angular)
- **Framework**: Angular 19.2
- **UI Components**: Angular Material, Bootstrap 5.3
- **Features**: 
  - Interactive calendars (angular-calendar)
  - Integrated PDF viewer (pdfjs-dist)
  - Responsive interface
  - Complex routing with authentication guards

### AI/LLM Component (Python)
- **Framework**: FastAPI for APIs
- **RAG System**: LangChain + ChromaDB for retrieval augmented generation
- **Embeddings**: HuggingFace sentence-transformers (all-MiniLM-L6-v2)
- **Transcription**: OpenAI Whisper for audio-to-text conversion
- **OCR**: Tesseract + pdf2image for scanned document processing

## 🚀 Installation and Configuration

### System Requirements
- Java 17+
- Node.js 18+ and npm
- Python 3.8+
- PostgreSQL 12+
- Git

### 1. Clone the Repository
```bash
git clone https://github.com/Florea123/SmartSecretary.git
cd SmartSecretary
```

### 2. Backend Configuration

#### Install Dependencies
```bash
cd backend
./mvnw clean install
```

#### Database Configuration
Create a `.env` file in the `backend/` directory with the following variables:
```properties
DB_IP=localhost
DB_NAME=smartsecretary_db
DB_USERNAME=your_username
DB_PASSWORD=your_password
JWT_SECRET=your_jwt_secret_key_here
EMAIL_API_KEY=your_sendgrid_api_key
```

#### Start the Application
```bash
./mvnw spring-boot:run
```
The backend will be available at `http://localhost:8081`

### 3. Frontend Configuration

```bash
cd frontend
npm install
npm start
```
The frontend will be available at `http://localhost:4200`

### 4. AI Component Configuration

#### Install Python Dependencies
```bash
cd llm
python -m venv venv
venv\Scripts\activate  # Windows
# or
source venv/bin/activate  # Linux/Mac

pip install fastapi uvicorn langchain-chroma langchain-huggingface langchain-community pdf2image pytesseract pillow openai-whisper
```

#### OCR Configuration
For Windows, download and install Tesseract OCR, then update the path in `create_embeddings.py`.

#### Data Preparation and Service Startup
```bash
# 1. Add PDF files to the pdfuri/ directory
# 2. Generate embeddings
python create_embeddings.py

# 3. Start the RAG API
python rag_api.py

# 4. Start the transcription API (separate terminal)
python transcription_api.py
```

## 💻 Usage

### Roles and Access

#### 👨‍🎓 Students
- Authentication with registration number
- Form completion and submission
- Academic calendar and exam viewing
- Chat with AI assistant
- Support ticket management

#### 👩‍💼 Secretariat Staff
- Student management (adding, viewing)
- Form upload and organization
- Student request processing
- Academic calendar upload
- News and announcements management

#### 👨‍💻 Administrators
- User management (secretaries, administrators)
- AI system file administration
- System monitoring and configuration
- Report generation

### Main API Endpoints

#### Authentication
- `POST /api/auth/signin` - Login
- `POST /api/auth/signup` - Student registration
- `POST /api/auth/forgot-password` - Password reset

#### Forms
- `GET /api/forms` - Active forms list
- `POST /api/forms` - Create new form
- `GET /api/forms/{id}/fields` - Form fields

#### AI Services
- `POST /rag` - Questions to AI assistant
- `POST /transcribe` - Audio file transcription

## 🗂️ Project Structure

```
SmartSecretary/
├── backend/                    # Spring Boot Application
│   ├── src/main/java/com/example/demo/
│   │   ├── controller/         # REST Controllers
│   │   ├── service/           # Business Logic
│   │   ├── entity/            # JPA Entities
│   │   ├── repository/        # Data Access Layer
│   │   └── util/              # Utilities (JWT, Encryption)
│   └── src/main/resources/
│       ├── application.properties
│       └── scripts/           # Database scripts
├── frontend/                   # Angular Application
│   └── src/app/
│       ├── components/        # Reusable components
│       ├── pages/            # Page components
│       ├── guards/           # Route guards
│       └── services/         # HTTP services
├── llm/                       # AI/ML Components
│   ├── rag_api.py            # RAG System API
│   ├── transcription_api.py  # Audio transcription
│   ├── create_embeddings.py  # Vector database setup
│   └── pdfuri/              # Documents for processing
└── docs/                     # Architecture documentation
    ├── uml/                  # UML Diagrams
    ├── lvl1-4/              # C4 Architecture diagrams
    └── productBacklog/      # Project management docs
```

## 🔧 Advanced Configuration

### Environment Variables
All sensitive configurations are managed through environment variables for security and deployment flexibility.

### Database Schema
The system uses Hibernate for automatic database schema management with `spring.jpa.hibernate.ddl-auto=update`.

### Security
- JWT authentication with automatic expiration
- AES encryption of sensitive data
- Server-side validation for all inputs
- CORS configured for frontend

## 🤝 Contributing

To contribute:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/NewFeature`)
3. Commit your changes (`git commit -m 'Add NewFeature'`)
4. Push to the branch (`git push origin feature/NewFeature`)
5. Open a Pull Request

## 📄 License

This project is developed for academic purposes and is available for educational use.

## 🆘 Support

For issues and questions:
- Consult the documentation in the `docs/` directory
- Check existing issues
- Create a new issue with problem details

## 🔄 Development Status

- ✅ Backend API fully functional
- ✅ Frontend with all major features
- ✅ AI integration with RAG and transcription
- ✅ Authentication and authorization system
- ✅ Document and form management
- 🚧 Ongoing optimizations and improvements

---

**Developed for the Romanian university environment** 🇷🇴