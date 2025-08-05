# 🎥 Ultimate Video Summarizer Agent

An AI-powered tool for comprehensive video analysis and summarization with advanced features including sentiment analysis, keyword extraction, and multi-language support.

---

## ✨ Features

### 🎯 Core Functionality
- **Multi-input Support**: Process YouTube URLs or upload local video files  
- **AI-Powered Summarization**: Using OpenAI GPT models via LangChain  
- **Customizable Output**: Multiple formats (bullet points, narrative, markdown)  
- **Multi-language Support**: Generate summaries in 6+ languages  
- **Variable Length**: Short, medium, or long summaries  

### 📊 Advanced Analysis
- **Sentiment Analysis**: Emotional tone analysis using NLTK's VADER  
- **Keyword Extraction**: Automatic identification of key topics and themes  
- **Video Metadata**: Extract title, author, duration, views, and more  
- **Transcript Generation**: Full video transcription capabilities  

### 💾 Data Management
- **History Tracking**: Session-based storage of all summaries  
- **Export Options**: Download summaries in TXT, MD, or JSON formats  
- **Batch Processing**: Handle multiple videos efficiently  

### 🎨 User Experience
- **Responsive Design**: Works seamlessly on desktop and mobile  
- **Real-time Processing**: Live progress indicators  
- **Interactive Dashboard**: Rich visualizations and charts  
- **Intuitive Interface**: Clean, modern Streamlit-based UI  

---

## 🏗️ Architecture

### Backend (FastAPI)
- RESTful API with comprehensive endpoints  
- Async processing for better performance  
- Error handling and validation  
- File upload support with size limits  
- CORS enabled for frontend integration  

### Frontend (Streamlit)
- Multi-tab interface for different functionalities  
- Advanced settings sidebar  
- Real-time updates and progress tracking  
- Data visualization with charts and metrics  
- History management system  

---

## 🚀 Quick Start

### Prerequisites
- Python 3.8 or higher  
- OpenAI API key  
- Git (optional)  

### Installation

```bash
git clone https://github.com/Alisha-21-cloud/video-summarizer-agent.git
cd video-summarizer-agent
```
Or download and extract the ZIP file.

```bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On macOS/Linux
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Set up environment variables:

```bash
cp .env.example .env
# Edit .env file and add your OpenAI API key
```

### Run the backend:

```bash
# Terminal 1 - Backend
python backend.py
# or
uvicorn backend:app --host 0.0.0.0 --port 8000 --reload
```

### Run the frontend:

```bash
# Terminal 2 - Frontend  
streamlit run frontend.py
```

### Access the application
- **Frontend**: [http://localhost:8501](http://localhost:8501)  
- **Backend API**: [http://localhost:8000](http://localhost:8000)  
- **API Docs**: [http://localhost:8000/docs](http://localhost:8000/docs)  

---

## 📋 Usage Guide

### 1. YouTube Video Summarization
- Navigate to **"Summarize Video"** tab  
- Select **"YouTube URL"**  
- Paste any YouTube video URL  
- Configure settings:
  - Summary format (bullet points, narrative, markdown)
  - Length (short, medium, long)
  - Language (English, Spanish, French, etc.)
  - Enable sentiment analysis  
- Click **"Generate Summary"**  
- View results in multiple tabs:
  - Summary text  
  - Video details and keywords  
  - Sentiment analysis charts  
  - Full transcript  

### 2. Local Video File Analysis
- Select **"Upload Video File"** tab  
- Choose video file (MP4, AVI, MOV, MKV)  
- Configure analysis settings  
- Click **"Analyze Uploaded Video"**  
- View comprehensive analysis results  

### 3. History Management
- Access **"History"** tab to view all past summaries  
- Download summaries in various formats  
- Delete unwanted entries  
- Search and filter capabilities  

### 4. Settings & Customization
- Configure default preferences  
- Update API endpoints  
- View usage statistics  
- Manage data retention  

---

## 🛠️ Technical Stack

### Core Technologies
- **Backend**: FastAPI (Python web framework)  
- **Frontend**: Streamlit (Interactive web apps)  
- **AI Models**: OpenAI GPT via LangChain  
- **Video Processing**: MoviePy, pytube  
- **Speech Recognition**: Google Speech Recognition  

### AI & NLP
- **LangChain**: LLM orchestration and chains  
- **OpenAI GPT**: Text generation and summarization  
- **NLTK**: NLP and sentiment analysis  
- **YouTube Transcript API**: Transcript extraction  

### Data & Visualization
- **Pandas**: Data manipulation  
- **Matplotlib / Plotly**: Charts and visualizations  
- **NumPy**: Numerical computing  

### Utilities
- **Requests**: HTTP client  
- **Python-dotenv**: Environment variable management  
- **Regex**: Pattern matching and processing  

---

## 📁 Project Structure

```
video-summarizer-agent/
├── backend.py              # FastAPI backend server
├── frontend.py             # Streamlit frontend application
├── requirements.txt        # Python dependencies
├── .env.example            # Environment variables template
├── .env                    # Your environment variables (create this)
├── README.md               # This file
├── logs/                   # Application logs (auto-created)
└── temp/                   # Temporary files (auto-created)
```

---

## 🔧 Configuration

### Environment Variables

Create a `.env` file with:

```env
# Required
OPENAI_API_KEY=your_openai_api_key_here

# Optional
OPENAI_MODEL=gpt-3.5-turbo
OPENAI_TEMPERATURE=0.3
MAX_FILE_SIZE_MB=100
```

### API Settings

- **Backend Port**: 8000  
- **Frontend Port**: 8501  
- **Max File Size**: 100MB  
- **Request Timeout**: 300 seconds  

---

## 📊 API Endpoints

### Main Endpoints

| Method | Endpoint              | Description                      |
|--------|-----------------------|----------------------------------|
| POST   | `/summarize`          | Summarize YouTube video          |
| POST   | `/summarize/upload`   | Analyze uploaded video           |
| GET    | `/summaries`          | Get all summaries                |
| GET    | `/summaries/{id}`     | Get specific summary             |
| DELETE | `/summaries/{id}`     | Delete summary                   |
| GET    | `/download/{id}`      | Download summary                 |
| GET    | `/health`             | Health check                     |

### Request/Response Example

#### Summarize YouTube Video

```json
POST /summarize
{
  "url": "https://www.youtube.com/watch?v=example",
  "format": "bullet_points",
  "length": "medium",
  "language": "english",
  "include_sentiment": true
}
```

#### Response

```json
{
  "id": "uuid-string",
  "summary": "Generated summary text...",
  "metadata": {
    "title": "Video Title",
    "author": "Channel Name",
    "duration": 600,
    "views": 10000
  },
  "transcript": "Full transcript...",
  "sentiment": {
    "overall": "positive",
    "compound": 0.25,
    "positive": 0.7,
    "neutral": 0.2,
    "negative": 0.1
  },
  "keywords": ["keyword1", "keyword2", "..."],
  "timestamp": "2024-01-01T12:00:00"
}
```

---

## 🐛 Troubleshooting

### Common Issues

1. **Backend won't start**  
   - Check if port 8000 is free  
   - Ensure `.env` is properly configured  
   - Reinstall dependencies  

2. **"Cannot connect to backend API" error**  
   - Ensure backend is running  
   - Verify `API_BASE_URL` in `frontend.py`  

3. **Video processing fails**  
   - Check file format and size  
   - Ensure stable internet  

4. **Sentiment analysis not working**  
   ```bash
   python -c "import nltk; nltk.download('vader_lexicon')"
   ```

5. **Out of memory errors**  
   - Lower file size  
   - Close other applications  

---

## 🔒 Security Considerations

### API Keys
- Do **NOT** commit API keys  
- Store them in `.env`  
- Rotate regularly  
- Monitor usage  

### File Uploads
- Limit size and type  
- Use temp storage  
- Scan for malware (production)  

### Production Deployment
- Use HTTPS  
- Enable CORS for trusted domains  
- Add rate limiting and auth  
- Reverse proxy via NGINX  

---

## 🚀 Advanced Features

### Custom Model Integration

```python
from transformers import pipeline
summarizer = pipeline("summarization", model="facebook/bart-large-cnn")
```

### Database Integration

```python
from sqlalchemy import create_engine, session
# Add models and operations
```

### Batch Processing

```python
import asyncio
async def process_videos(urls):
    tasks = [summarize_video(url) for url in urls]
    return await asyncio.gather(*tasks)
```

---

## 🤝 Contributing

1. Fork the repository  
2. Create a feature branch  
3. Commit your changes  
4. Push and open a Pull Request  

### Development Setup

```bash
pip install -r requirements-dev.txt
pytest
black .
flake8 .
```

---

## 📄 License

This project is licensed under the **MIT License** – see the `LICENSE` file for details.

---

## 🙏 Acknowledgments

- OpenAI (GPT models)  
- LangChain  
- Streamlit  
- FastAPI  
- The open-source community ❤️  

---

## 🗺️ Roadmap

### v1.1 (Planned)
- Real-time video processing  
- Batch video processing  
- Custom model fine-tuning  
- Advanced analytics dashboard  

### v1.2 (Future)
- Video chaptering & timestamps  
- Multi-speaker identification  
- Integration with more platforms  
- Mobile app version  

### v2.0 (Vision)
- AI-powered video editing  
- Automatic highlight generation  
- Social media integrations  
- Enterprise features  

---

## 📈 Version History

- **v1.0.0** - Initial release  
- **v0.9.0** - Beta release  
- **v0.5.0** - Alpha release  

---

> Made by Ahmad for the AI community
