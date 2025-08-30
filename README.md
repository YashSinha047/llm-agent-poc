# LLM Agent POC: Browser-Based Multi-Tool Reasoning

[![Live Demo](https://img.shields.io/badge/Live-Demo-brightgreen)](https://yourusername.github.io/llm-agent-poc)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow.svg)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3.0-purple.svg)](https://getbootstrap.com/)

A proof-of-concept implementation of an LLM-powered agent that can combine language model output with external tools like web search, AI workflows, and live code execution - all running entirely in the browser.

Agent Demo

<img width="1906" height="828" alt="Screenshot 2025-08-21 050627" src="https://github.com/user-attachments/assets/deaf043d-650d-4dd4-959b-68d9268dae9d" />
<img width="1904" height="838" alt="Screenshot 2025-08-21 050654" src="https://github.com/user-attachments/assets/73286fec-bd07-4d1d-bc32-2b72e45027b7" />
<img width="1907" height="850" alt="Screenshot 2025-08-21 050720" src="https://github.com/user-attachments/assets/466737b2-6380-470f-b792-2000d354c4aa" />
<img width="1898" height="818" alt="Screenshot 2025-08-21 050746" src="https://github.com/user-attachments/assets/111af947-cd99-4f5c-ac3c-80a98c64271d" />




## 🌟 Features

### 🤖 **Core Agent Logic**
- **Multi-step reasoning loop** - Continues until task completion
- **Dynamic tool selection** - LLM chooses appropriate tools based on context
- **Conversation memory** - Maintains context across multiple exchanges
- **Error recovery** - Graceful handling of tool failures

### 🛠️ **Three Integrated Tools**
1. **🔍 Google Search** - Real-time web search with custom API integration
2. **🧠 AI Pipe Workflows** - Additional LLM processing for complex tasks  
3. **⚡ JavaScript Execution** - Live code execution with result display

### 🎨 **User Experience**
- **Clean Bootstrap UI** - Professional, responsive interface
- **Real-time chat** - Conversational interaction with the agent
- **Tool execution visibility** - See exactly what tools are being called
- **Configuration panels** - Easy setup for LLM providers and search APIs
- **Error notifications** - User-friendly error handling

## 🚀 Quick Start

### Option 1: Direct Use (Recommended)
1. **Visit the live demo**: [https://yashsinha047.github.io/llm-agent-poc/](https://yashsinha047.github.io/llm-agent-poc/)
2. **Authenticate** with AI Pipe (redirects automatically)
3. **Start chatting** - Try: *"Search for Python tutorials and create a learning plan"*

### Option 2: Local Development
```bash
# Clone the repository
git clone https://github.com/yourusername/llm-agent-poc.git
cd llm-agent-poc

# Serve locally (Python)
python -m http.server 8000
# OR (Node.js)
npx serve . -p 8000

# Open browser
open http://localhost:8000
```

## 🔧 Configuration

### LLM Provider Setup
1. Click **"Configure LLM"** button
2. Choose from:
   - **AI Pipe** (free, recommended for testing)
   - **OpenAI API** (requires API key)
   - **OpenRouter** (requires API key)

### Google Search Setup (Optional)
1. Click **"Configure Search"** button
2. Enter your [Google Custom Search API](https://developers.google.com/custom-search/v1/overview) credentials:
   - **API Key**: Get from [Google Cloud Console](https://console.cloud.google.com/)
   - **Search Engine ID**: Create at [Custom Search Engine](https://cse.google.com/)
3. Toggle **"Use real Google Search API"** to enable

> **Note**: Without real search API, the agent uses realistic mock data for demonstration.

## 💬 Example Conversations

### Multi-Tool Workflow
```
User: Help me plan a Python learning roadmap based on current trends

Agent: I'll search for current Python trends and create a personalized plan for you.

Tool: Executing google_search with: { "query": "Python programming trends 2024" }
Tool: [Real search results displayed]

Tool: Executing aipipe_workflow with: { "prompt": "Create a learning roadmap based on..." }
Tool: [Comprehensive learning plan generated]

Agent: Based on current trends, here's your personalized Python learning roadmap...
```

### Code Execution
```
User: Calculate compound interest on $10,000 at 5% for 10 years

Tool: Executing execute_javascript with: { 
  "code": "const principal = 10000; const rate = 0.05; const time = 10; 
          const amount = principal * Math.pow(1 + rate, time); 
          Math.round(amount * 100) / 100;" 
}
Tool: Code executed successfully. Result: 16288.95

Agent: The compound interest calculation shows that $10,000 invested at 5% annually for 10 years would grow to $16,288.95...
```

## 🏗️ Architecture

### Core Components
```
├── LLM Integration (OpenAI-compatible APIs)
├── Tool System (Function calling interface)
│   ├── Google Search API
│   ├── AI Pipe Workflows  
│   └── JavaScript Execution
├── Agent Loop (Multi-step reasoning)
├── UI Layer (Bootstrap + vanilla JS)
└── Configuration Management
```

### Agent Reasoning Loop
```python
# Conceptual implementation (actual code in JavaScript)
def agent_loop():
    while not task_complete:
        llm_response = call_llm(conversation_history, available_tools)
        
        if llm_response.tool_calls:
            for tool_call in llm_response.tool_calls:
                result = execute_tool(tool_call)
                conversation_history.append(result)
        else:
            display_final_response(llm_response)
            break
```

## 🛠️ Technical Stack

- **Frontend**: Vanilla JavaScript ES6+, Bootstrap 5.3
- **LLM Integration**: AI Pipe, OpenAI API, OpenRouter
- **Search**: Google Custom Search API
- **Deployment**: GitHub Pages, Netlify, Vercel compatible
- **Dependencies**: 
  - [`bootstrap-llm-provider`](https://github.com/sanand0/bootstrap-llm-provider) - LLM configuration UI
  - [`bootstrap-alert`](https://github.com/sanand0/bootstrap-alert) - Toast notifications
  - [`aipipe`](https://github.com/sanand0/aipipe) - Free LLM API access

## 📁 Project Structure

```
llm-agent-poc/
├── index.html          # Complete application (HTML + CSS + JS)
├── README.md          # This file
└── LICENSE            # MIT License
```

## 🧪 Testing

### Manual Test Cases
1. **Basic Chat**: `"Hello, what can you do?"`
2. **Search Tool**: `"Search for machine learning tutorials"`
3. **Code Tool**: `"Calculate factorial of 5"`
4. **AI Workflow**: `"Write a haiku about programming"`
5. **Multi-Tool**: `"Research React frameworks and create a comparison table"`

### Features Testing
- [ ] LLM provider configuration
- [ ] Google Search API integration  
- [ ] JavaScript code execution
- [ ] AI Pipe workflow calls
- [ ] Error handling and recovery
- [ ] Mobile responsiveness
- [ ] Tool enable/disable toggle

## 🚀 Deployment

### GitHub Pages (Recommended)
1. Fork this repository
2. Go to Settings → Pages
3. Select "Deploy from branch" → "main" → "/ (root)"
4. Your app will be live at `https://yourusername.github.io/llm-agent-poc`

### Other Options
- **Netlify**: Drag and drop `index.html`
- **Vercel**: `npx vercel` in project directory
- **Surge**: `npm install -g surge && surge`

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Test thoroughly
5. Submit a pull request

### Development Guidelines
- Keep the single-file architecture for simplicity
- Maintain compatibility with modern browsers
- Follow existing code style and patterns
- Test all three tool integrations

## 📋 Roadmap

### Current Version (v1.0)
- [x] Core agent reasoning loop
- [x] Three tool integrations
- [x] Bootstrap UI with configuration
- [x] Error handling and recovery

### Future Enhancements (v2.0)
- [ ] Additional tool integrations (email, calendar, file processing)
- [ ] Conversation export/import
- [ ] Advanced search result processing
- [ ] Plugin system for custom tools
- [ ] Voice interaction support

## 🔒 Security & Privacy

- **API Keys**: Stored securely in browser localStorage
- **Code Execution**: Sandboxed JavaScript execution
- **Data Privacy**: No conversation data stored on servers
- **HTTPS**: All API calls use secure connections

## 📚 Educational Use

This project demonstrates:
- **LLM Agent Architecture** - Multi-step reasoning and tool use
- **API Integration** - RESTful API consumption patterns
- **Modern Web Development** - ES6+, Bootstrap, responsive design
- **Error Handling** - Graceful degradation and recovery
- **User Experience** - Professional UI/UX patterns

Perfect for:
- Computer Science coursework
- AI/ML project demonstrations  
- Web development portfolios
- Learning LLM integration patterns

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [AI Pipe](https://aipipe.org) - Free LLM API access
- [Bootstrap](https://getbootstrap.com/) - UI framework
- [OpenAI](https://openai.com/) - GPT models and function calling API
- [Google](https://developers.google.com/custom-search) - Custom Search API

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/yourusername/llm-agent-poc/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/llm-agent-poc/discussions)
- **Demo**: [Live Application](https://yourusername.github.io/llm-agent-poc)

---

⭐ **Star this repository if you find it helpful!** ⭐
