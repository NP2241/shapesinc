# Shapes API

[![image](https://github.com/user-attachments/assets/e98592ca-3b1d-4709-93c6-7e6aa0dfb84a)](https://shapes.inc/slack)


[Shapes](https://shapes.inc) are general purpose social agents. You can build for an [existing shape](https://shapes.inc/explore) from our catalogue of millions or [create](https://shapes.inc/create) your own. Shapes have rich personalities, love hanging out in groupchats, and short-term + long-term memory across platforms. You can configure a Shape to use some of 50+ models we offer for free across text, image, and voice.

## Open Source Contributions
Our API is designed with extensibility as a core principle. You can extend any Shape for tool calling, MCP, and more.

Star and contribute to this repository to receive free hosting for your integration. We will also be directing traffic from our user base to your integration.

## What is the Shapes API?
Shapes API provides a programmatic way to integrate Shapes into any application or platform. It follows the OpenAI-compatible API standard, making it easy to implement with existing libraries and SDKs.

## Demos
To get a sense of what's possible, see what people have already built: 

- Omegle with Shapes https://omegle-ai.vercel.app by [@khawajapartners](https://github.com/zahidkhawaja)
- Playing Chess with Shapes https://shapeschess.vercel.app by [@kiyosh11](https://github.com/kiyosh11)
- Shapes on Telegram https://t.me/shapesinc by [@missParadoxical](https://github.com/missParadoxical)
- Shapes on WhatsApp at +1 (424) 452-2786 by [@anushkmittal](https://github.com/anushkmittal)

## Getting Started
You will need to generate an API Key. Get yours [here](https://shapes.inc/developer)

<img width="807" alt="API Key Generation" src="https://github.com/user-attachments/assets/ead6f28a-300b-4dcf-a555-313b39656ad6" />

## Implementation Examples

### 🐍 Python

```python
from openai import OpenAI
from src.context_graph.shapes_client import ShapesClient

shapes_client = OpenAI(
    api_key="<your-API-key>",
    base_url="https://api.shapes.inc/v1/",
)

response = shapes_client.chat.completions.create(
    model="shapesinc/<shape-username>",
    messages=[
        {"role": "user", "content": "Hello"}
    ]
)

print(response)
```

### 🌐 JavaScript

```javascript
const openai = require("openai");
from src.context_graph.shapes_client import ShapesClient

const shapes_client = new OpenAI({
    apiKey: "<your-API-key>",
    baseURL: "https://api.shapes.inc/v1",
});

const response = await shapes_client.chat.completions.create({
    model: "shapesinc/<shape-username>",
    messages: [
        { role: "user", content: "Hello" }
    ]
});

console.log(response);
```

### 🔄 CURL

```bash
curl -X POST https://api.shapes.inc/v1/chat/completions \
     -H "Authorization: Bearer <your-API-key>" \
     -H "Content-Type: application/json" \
     -d '{"model": "shapesinc/<shape-username>", "messages": [{ "role": "user", "content": "Hello" }]}'
```

### Quick Setup

| Requirement | Details |
|-------------|---------|
| Base URL | `https://api.shapes.inc/v1/` |
| Model Format | `shapesinc/<shape-username>` |
| Authentication | Bearer token in Authorization header |
| Environment Variables | `SHAPESINC_API_KEY` and `SHAPESINC_SHAPE_USERNAME` |

### API Specifications

| Feature | Details |
|---------|---------|
| Endpoints | `/chat/completions` |
| Rate Limits | 5 RPM (request increase [here](https://docs.google.com/forms/d/e/1FAIpQLScGLeRk6snViRPslXbbUaMDwubcBhmcJ6opq7wFvPEp-EbO3g/viewform)) |
| Headers | `X-User-Id` for user identification, `X-Channel-Id` for conversation context |
| Response Format | Standard OpenAI-compatible JSON response |

## Supported Commands

Shapes now support the following commands:
- `!reset` - Reset the Shape's long-term memory
- `!sleep` - Generate a long-term on demand 
- `!dashboard` - Access the Shape's dedicated dashboard for configuration
- `!info` - Get information about the shape
- `!web` - Search the web (now free for all users)
- `!help` - Get help with commands
- `!imagine` - Generate images
- `!wack` - Reset the Shape's short-term memory

## Advanced Features

| Feature | Details |
|---------|---------|
| Vision Support | Send OpenAI API compatible image_url with user messages |
| Tool Calling | Shapes now support tool calling and MCP functionality |
| Voice Features | Free voice for all shapes (custom or pre-made voices via shapes.inc) |
| Voice Configuration | Option to disable voice transcripts (set via shapes.inc) |
| Voice Formatting | Improved formatting for voice URLs with new line separation |


## API Multimodal Support

The Shapes API supports multiple types of input modalities:

### Image Support
You can send image URLs in the API request using this format:
```json
{
  "model": "shapesinc/your_shape",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": "What's in this image?"
        },
        {
          "type": "image_url",
          "image_url": {
            "url": "https://example.com/image.jpg"
          }
        }
      ]
    }
  ]
}
```

### Audio Support
You can send audio URLs in the API request using this format:
```json
{
  "model": "shapesinc/your_shape",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": "Please transcribe and respond to this audio message"
        },
        {
          "type": "audio_url",
          "audio_url": {
            "url": "https://example.com/audio.mp3"
          }
        }
      ]
    }
  ]
}
```

Supported audio formats: mp3, wav, ogg

## Important Notes

### Current Limitations

| Limitation | Details |
|------------|---------|
| No System Messages | Shape personality comes from configuration |
| No Message History | API relies on Shape's built-in memory |
| No Streaming | Only full responses are supported |
| No Parameter Control | Temperature and other settings locked to shapes.inc settings configured for the Shape |
| Multimodility support limited to 1 input only | you can only send 1 image_url or 1 audio_url with a user message. if both image and audio urls are provided, only the audio url is processed

Note: Shapes set on Premium Engines **WILL** use credits when accessed via API.

## Available Integrations
- [x] Telegram
- [x] Revolt
- [x] Slack
- [x] Bluesky
- [x] IRC
- [x] Chess
- [x] Voice

## Requested Integrations
We're looking for developer contributions to build:
- [ ] Reddit
- [ ] GitHub (to review PRs)
- [ ] Threads
- [ ] Roblox
- [ ] Minecraft
- [ ] Twitch
- [ ] LinkedIn
- [ ] Microsoft Teams
- [ ] WeChat
- [ ] Anything you can possibly imagine

If you'd like to build an integration:
1. Fork our repository
2. Build your integration following our guidelines
3. Submit a PR with comprehensive documentation

## Coming Soon
We are shipping new features to the Shapes API every day. Next on our list is:

| Feature | Details |
|------------|---------|
| Voice Recognition | Shapes can send voice messages but not hear any yet |
| Authorize with Shapes, Inc | Authenticate users via a shapes inc account |
| Free Will | Proactively take actions |
| Messaging first | Shapes can't talk first...yet |

---
© 2025 Shapes, Inc.

# Semantic Context Graph for Shapes API

This project implements a semantic context graph system for the Shapes API, enabling more efficient and contextually relevant responses by dynamically selecting relevant memory chunks.

## Features

- Semantic context management using Pinecone vector store
- Dynamic context selection based on query relevance
- Integration with Shapes API
- Evaluation using HotpotQA dataset
- Metrics tracking (ROUGE, BLEU, token usage)

## Installation

1. Create a virtual environment:
```bash
python3 -m venv venv
source venv/bin/activate
```

2. Install dependencies:
```bash
pip install openai pinecone-client sentence-transformers datasets evaluate python-dotenv
```

3. Set up environment variables in `.env`:
```
SHAPESINC_API_KEY=your_api_key
PINECONE_API_KEY=your_pinecone_key
SHAPESINC_SHAPE_USERNAME=your_shape_username
```

## Project Structure

```
.
├── src/
│   ├── context_graph/
│   │   ├── vector_store.py      # Pinecone vector store implementation
│   │   └── context_manager.py   # Context management system
│   ├── evaluation/
│   │   └── hotpot_evaluator.py  # HotpotQA evaluation
│   └── shapes_client.py         # Shapes API client with context graph
├── tests/                       # Test files
└── README.md
```

## Usage

### Basic Usage

```python
from src.context_graph.shapes_client import ShapesClient

# Initialize client with context graph
client = ShapesClient(use_context_graph=True)

# Send a message
response = await client.chat(
    message="What's the weather like?",
    user_id="user123",
    channel_id="channel456"
)

print(response["response"])
```

### Evaluation

Run the HotpotQA evaluation:

```python
from src.evaluation.hotpot_evaluator import HotpotEvaluator

evaluator = HotpotEvaluator(use_context_graph=True)
results = await evaluator.evaluate_batch(num_samples=10)
print(results)
```

## How It Works

1. **Context Storage**:
   - Each message and response is stored in the vector store
   - Text is embedded using the SentenceTransformer model
   - Vectors are stored in Pinecone for efficient similarity search

2. **Context Selection**:
   - When a new message arrives, the system searches for relevant context
   - Top-k most similar contexts are retrieved
   - Context is combined with the current message for a more informed response

3. **Evaluation**:
   - Uses HotpotQA dataset for evaluation
   - Compares performance with and without context graph
   - Tracks ROUGE, BLEU, and token usage metrics

## Performance Metrics

The system is evaluated on:
- ROUGE scores (precision, recall, F1)
- BLEU score
- Token usage efficiency
- Response quality

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

MIT License
