# Roblox Studio MCP Server

A Model Context Protocol (MCP) server implementation for Roblox Studio, written in TypeScript.

## Overview

This MCP server provides resources, tools, and prompts specifically designed for Roblox Studio development. It allows LLM applications to access Roblox Studio documentation, templates, code generation capabilities, and other features through a standardized interface.

## Features

- **Resources**: Access to Roblox Studio documentation, API references, and code templates
- **Tools**: Luau code generation and validation, asset searching, and game component creation
- **Prompts**: Specialized prompts for script generation, bug finding, and performance optimization
- **API Integration**: Direct connectivity to Roblox API and Open Cloud API
- **Interactive Systems**: Generation of dialogue systems, UI interfaces, and complex gameplay mechanics
- **Enhanced Performance**: Built-in caching and rate limiting for optimal performance
- **Robust Error Handling**: Comprehensive error management and graceful error recovery
- **Metrics and Monitoring**: Built-in health checks and performance metrics

## Prerequisites

- Node.js >= 18.x
- npm or yarn
- Roblox API Key (for API integration features)
- Roblox Open Cloud API Key (for Open Cloud features)

## Installation

1. Clone the repository
```bash
git clone https://github.com/dmae97/roblox-studio-mcp-server.git
cd roblox-studio-mcp-server
```

2. Install dependencies
```bash
npm install
```

3. Create a `.env` file based on `.env.example`
```bash
cp .env.example .env
```

4. Update the `.env` file with your Roblox API key and other configurations
```
ROBLOX_API_KEY=your_api_key_here
ROBLOX_OPEN_CLOUD_API_KEY=your_open_cloud_api_key_here
ROBLOX_OPEN_CLOUD_UNIVERSE_ID=your_universe_id_here
```

5. Build the project
```bash
npm run build
```

## Running the Server

Start the server in development mode:
```bash
npm run dev
```

Or start the production server:
```bash
npm start
```

The server starts on port 3000 by default (configurable in `.env`).

## Running with Docker (Future Support)

You can also run the server using Docker:

```bash
# Build the image
docker build -t roblox-studio-mcp-server .

# Run the container
docker run -p 3000:3000 -v .env:/app/.env roblox-studio-mcp-server
```

Or using docker-compose:

```bash
docker-compose up
```

## Configuration Options

The server can be configured using environment variables in the `.env` file:

### Server Configuration
- `PORT` - The port to run the server on (default: 3000)
- `SERVER_NAME` - The name of the server (default: "Roblox Studio MCP Server")
- `SERVER_VERSION` - The version of the server (default: "1.0.0")
- `NODE_ENV` - The environment (development/production)

### Logging Configuration
- `DEBUG` - Enable debug mode (true/false)
- `LOG_LEVEL` - The logging level (info, warn, error, debug)
- `LOG_TIMESTAMP` - Include timestamps in logs (true/false)
- `LOG_COLOR` - Colorize log output (true/false)

### Performance Settings
- `ENABLE_RATE_LIMITING` - Enable rate limiting (true/false)
- `RATE_LIMIT_WINDOW` - The time window for rate limiting (milliseconds)
- `RATE_LIMIT_MAX_REQUESTS` - The maximum number of requests per window
- `CACHE_TTL` - The time-to-live for cached data (seconds)
- `CACHE_CHECK_PERIOD` - The interval for checking expired cache entries (seconds)

### Security Settings
- `CORS_ORIGINS` - A comma-separated list of allowed origins, or * to allow all
- `JWT_SECRET` - The secret key for JWT token verification

## API Endpoints

- `GET /sse` - Server-Sent Events endpoint for MCP communication
- `POST /messages` - Message endpoint for MCP communication
- `GET /health` - Health check endpoint
- `GET /metrics` - Server metrics endpoint

## Resources

### Documentation

- `docs://api/{section}` - Access Roblox Studio API documentation
- `docs://api` - List available documentation sections
- `docs://luau` - Luau language documentation and best practices
- `docs://services/{service}` - Documentation for specific Roblox services

### Templates

- `template://roblox/{category}/{name}` - Access code templates
- `template://roblox` - List available templates
- `template://ui/{component}` - UI component templates using Roblox UI

## Tools

### Code Generator

The `generate-roblox-code` tool generates Roblox Luau code based on user specifications.

Parameters:
- `scriptType`: The type of script to generate (ServerScript, LocalScript, ModuleScript)
- `functionality`: A description of what the script should do
- `includeComments`: Whether to include comments in the code
- `targetRobloxVersion`: (Optional) The target Roblox version

### Asset Finder

The `find-roblox-assets` tool searches for Roblox assets based on user criteria.

Parameters:
- `assetType`: The type of asset to search for (Model, Decal, Mesh, Animation, Sound, Texture)
- `keywords`: Search keywords or tags
- `maxResults`: The maximum number of results to return
- `includeDetails`: Whether to include detailed asset information

### Script Validator

The `validate-roblox-script` tool validates Luau scripts for syntax errors and best practices.

Parameters:
- `scriptContent`: The Luau script content to validate
- `scriptType`: The script type (ServerScript, LocalScript, ModuleScript)
- `checkBestPractices`: Whether to check for best practices
- `checkPerformance`: Whether to check for performance issues

### New Tools

#### Data Store Manager

The `create-datastore-system` tool generates complete DataStore code for persistent data management.

Parameters:
- `datastoreName`: The name of the DataStore
- `dataStructure`: The structure of the data to be stored
- `sessionCaching`: Whether to include session caching logic
- `backupStrategy`: The data backup strategy
- `playerData`: Whether it is player data

#### Physics System Generator

The `create-physics-system` tool generates physics-based systems for Roblox.

Parameters:
- `objectName`: The name of the physical object
- `objectType`: The type of physical object
- `size`: Size dimensions
- `material`: Material type
- `physicsProperties`: Density, friction, etc.
- `constraints`: Optional physical constraints

#### UI Builder

The `create-ui-system` tool generates Roblox UI code.

Parameters:
- `uiType`: The type of UI (Menu, HUD, Dialog, Inventory)
- `elements`: The UI elements to include
- `responsive`: Whether the UI should be responsive
- `stylePreset`: The visual style preset to use

### Roblox API Connector

Tools for direct connection to the Roblox API:

#### Asset Search API

The `roblox-search-assets` tool searches for assets using the official Roblox API.

#### Open Cloud Integration

The `roblox-open-cloud` tool provides access to Roblox Open Cloud API features.

Parameters:
- `feature`: The Open Cloud feature to use
- `universeId`: The Universe ID to operate on
- `actionType`: The type of action to perform
- `data`: Data for the operation

## Prompts

### Script Generator

The `generate-script` prompt helps generate Roblox scripts with AI assistance.

Parameters:
- `scriptType`: The type of script to generate
- `functionality`: A description of what the script should do
- `includeComments`: Whether to include comments in the code
- `complexity`: Level of complexity (Beginner, Intermediate, Advanced)
- `targetAudience`: Target audience (Child, Teen, Adult)

### Bug Finder

The `find-bugs` prompt analyzes bugs and suggests improvements.

Parameters:
- `scriptContent`: The Luau script content to analyze
- `scriptType`: The script type
- `checkPerformance`: Whether to check for performance issues
- `checkSecurity`: Whether to check for security issues
- `suggestImprovements`: Whether to suggest improvements

### Performance Optimizer

The `optimize-performance` prompt analyzes and optimizes Roblox scripts for better performance.

Parameters:
- `scriptContent`: The script to optimize
- `targetFPS`: The target frames per second
- `optimizationLevel`: The level of optimization to apply
- `preserveReadability`: Whether to prioritize readability

## Development

### Project Structure

- `src/index.ts` - Main server file
- `src/utils/` - Utility functions
- `src/middleware/` - Express middleware for error handling, rate limiting, etc.
- `src/tools/` - MCP tool implementations
- `src/resources/` - MCP resource implementations
- `src/prompts/` - MCP prompt implementations
- `src/api/` - Roblox API client implementations
- `src/tools/interactive/` - Interactive systems and UI tools
- `src/tools/physics/` - Physics system tools
- `src/tools/datastore/` - DataStore management tools
- `src/tools/opencloud/` - Open Cloud API integration

### Testing (Future Support)

Run unit tests:
```bash
npm test
```

Run integration tests:
```bash
npm run test:integration
```

Generate a full test coverage report:
```bash
npm run test:coverage
```

### MCP Integration Examples

Examples of how to use this MCP server in various LLM applications:

#### Example 1: Using the API with Claude

```javascript
// Example code to call the MCP server from a web application using Claude
async function callRobloxMcp() {
  const response = await fetch('https://your-claude-api-endpoint/messages', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer your-claude-api-key'
    },
    body: JSON.stringify({
      model: "claude-3.7-sonnet-20250219",
      messages: [
        {
          role: "user",
          content: "Can you help me create a platformer game in Roblox Studio?"
        }
      ],
      tool_choice: "auto",
      tools: [
        {
          function: {
            name: "mcp",
            description: "Call the Roblox Studio MCP server",
            parameters: {
              type: "object",
              properties: {
                server_url: {
                  type: "string",
                  description: "The URL of the MCP server"
                },
                tool_name: {
                  type: "string",
                  description: "The name of the MCP tool to call"
                },
                tool_parameters: {
                  type: "object",
                  description: "Parameters for the MCP tool"
                }
              },
              required: ["server_url", "tool_name"]
            }
          }
        }
      ]
    })
  });
  
  return await response.json();
}
```

#### Example 2: Using the MCP Server with a CLI Tool

You can also use the MCP server via the command line:

```bash
# Install the MCP client CLI
npm install -g @modelcontextprotocol/cli

# Connect to the MCP server
mcp connect http://localhost:3000

# Use an MCP tool
mcp tool generate-roblox-code --scriptType=ServerScript --functionality="Handle player movement" --includeComments=true

# Access a template
mcp resource template://roblox/game/platformer
```

#### Example 3: Connecting with Anthropic's Claude

```python
import anthropic
from anthropic.tool_use import MCP

# Initialize the Claude client
client = anthropic.Client(api_key="your-anthropic-api-key")

# Create an MCP connection
mcp = MCP(server_url="http://localhost:3000")

# Send a message to Claude with the MCP tool
response = client.messages.create(
    model="claude-3.7-sonnet-20250219",
    max_tokens=1000,
    system="You are a helpful AI assistant with access to a Roblox Studio MCP server.",
    messages=[
        {
            "role": "user",
            "content": "I want to create a multiplayer game in Roblox Studio. What tools should I use?"
        }
    ],
    tools=[mcp.to_tool()]
)

print(response.content)
```

### Scripts

- `npm run build` - Build the project
- `npm run dev` - Run in development mode with hot reloading
- `npm start` - Run the production server
- `npm run lint` - Run linting
- `npm test` - Run tests

## Troubleshooting

### Common Issues

1. **Connection Errors**: Ensure your Roblox API key is configured correctly.
2. **High Memory Usage**: Adjust the cache TTL settings to manage memory usage.
3. **Rate Limit Errors**: Adjust the `RATE_LIMIT_*` settings to suit your environment.

### Logging

To debug issues, enable detailed logging by setting `LOG_LEVEL=debug`.

## Recent Updates

- Enhanced error handling with custom middleware
- Improved logging system with configurable levels and formatting
- Implemented caching system for performance improvements
- Added rate limiting to prevent abuse
- Expanded metrics endpoint for better monitoring
- Added graceful shutdown handling
- Updated to the latest Roblox API endpoints
- Fixed name inconsistency (Roblex → Roblox)

## Future Planned Features

- **JWT Authentication**: For enhanced security
- **API Documentation**: OpenAPI/Swagger integration
- **Docker Support**: Containerization for easy deployment
- **Test Suite**: Comprehensive unit and integration tests
- **CI/CD Pipeline**: Automated testing and deployment

## Contributing

Contributions are welcome! Feel free to submit pull requests.

## License

MIT
