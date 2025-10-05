# AI Travel Planner 🌍✈️

An intelligent travel itinerary generator that creates personalized travel plans using Large Language Models (LLMs) and Retrieval Augmented Generation (RAG). The application combines user preferences with real-time destination data to generate contextually appropriate, dynamic itineraries.

## 🎯 Features

- **Personalized Itinerary Generation**: Creates custom travel plans based on user preferences across multiple activity categories (Outdoor, Shopping, Food & Drink, Cultural, Adventure)
- **RAG-Enhanced Planning**: Retrieves real-time destination information from Wikipedia to provide accurate, up-to-date context for itinerary generation
- **Smart Time Management**: Automatically adjusts activities based on arrival/departure times, avoiding early morning or late-night scheduling conflicts
- **Interactive Web Interface**: User-friendly Streamlit interface for easy input and visualization of travel plans
- **Flexible Activity Selection**: Multi-level preference selection allowing users to specify broad categories and specific interests

## 🛠️ Technologies Used

- **LLM Framework**: LangChain for prompt management and LLM orchestration
- **Language Model**: Llama 3 (via Ollama) for natural language generation
- **Frontend**: Streamlit for interactive web application
- **RAG Data Source**: Wikipedia API (Wikimedia) for destination information retrieval
- **Python Libraries**: `requests`, `langchain`, `langchain-community`

## 🏗️ Architecture

### RAG Implementation
The application implements Retrieval Augmented Generation to mitigate LLM hallucinations:

1. **Retrieval Phase**: Fetches destination-specific data from Wikipedia API based on user's travel location
2. **Augmentation Phase**: Injects retrieved context into the LLM prompt template
3. **Generation Phase**: LLM generates personalized itinerary using both user preferences and retrieved factual data

### Prompt Engineering
The system uses carefully engineered prompts to ensure:
- Coherent itinerary structure with logical activity sequencing
- Context-aware scheduling (respecting arrival/departure times)
- Balanced recommendations across user-selected preference categories
- Realistic time allocations for travel, meals, and rest

## 📋 Prerequisites

- Python 3.8+
- Ollama installed locally with Llama 3 model

## 🚀 Installation

1. Clone the repository:
```bash
git clone https://github.com/jaredteoh/ai-travel-planner.git
cd ai-travel-planner
```

2. Install required dependencies:
```bash
pip install streamlit langchain langchain-community requests
```

3. Install and start Ollama with Llama 3:
```bash
# Install Ollama (visit https://ollama.ai for platform-specific instructions)
ollama pull llama3
```

## 💻 Usage

1. Start the Streamlit application:
```bash
streamlit run travel_app.py
```

2. Open your browser to `http://localhost:8501`

3. Input your travel details:
   - Enter destination
   - Select arrival and departure dates/times
   - Choose activity preferences from available categories
   - Click "Generate Travel Plan"

4. View your personalized AI-generated itinerary

## 📁 Project Structure

```
ai-travel-planner/
│
├── travel_app.py                 # Main application script
├── README.md              # Project documentation
└── requirements.txt       # Python dependencies (if added)
```

## 🔑 Key Components

### `get_external_travel_data(destination)`
Retrieves destination information from Wikipedia API to provide factual context for the LLM.

**Input**: Destination name (string)  
**Output**: Destination description/extract from Wikipedia

### `LLMChain`
LangChain component that manages the prompt template and LLM interaction, ensuring consistent output formatting.

### Prompt Template
Structured template that includes:
- User travel dates and times
- Activity preferences
- Retrieved destination data
- Scheduling constraints

## 🎨 Example Use Case

**Input:**
- Destination: Tokyo, Japan
- Dates: 2025-10-15 to 2025-10-20
- Arrival: 22:00 | Departure: 08:00
- Preferences: Cultural (Museums, Historical Sites), Food & Drink (Local Cuisine, Street Food)

**Output:**
Personalized 5-day itinerary with:
- Light evening activities on arrival day (late arrival handling)
- Full-day cultural and culinary experiences
- Specific museum and historical site recommendations
- Local restaurant suggestions based on preferences
- No activities scheduled on departure morning (early departure handling)

## 🚧 Future Enhancements

- [ ] Add vector database (ChromaDB/Pinecone) for richer travel content retrieval
- [ ] Implement Google Places API integration for real-time location suggestions
- [ ] Add budget optimization features
- [ ] Include accommodation and transportation booking links
- [ ] Support multiple language outputs
- [ ] Add user feedback mechanism for itinerary refinement
- [ ] Implement caching for repeated destination queries

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is open source and available under the MIT License.

## 👤 Author

**Jared Teoh Jie Rui**
- LinkedIn: [linkedin.com/in/jaredteoh0725](https://www.linkedin.com/in/jaredteoh0725/)
- GitHub: [github.com/jaredteoh](https://github.com/jaredteoh)
- Email: teohjared@gmail.com

## 🙏 Acknowledgments

- LangChain for LLM orchestration framework
- Ollama for local LLM deployment
- Wikimedia Foundation for travel data API
- Streamlit for rapid web app development

---

*Built with ❤️ using LangChain, Llama 3, and Streamlit*
