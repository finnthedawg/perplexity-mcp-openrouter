# OpenRouter Perplexity MCP Server

Access Perplexity's powerful search models directly in Claude Code and Cursor through OpenRouter's unified API gateway. This MCP server brings real-time web search, deep research, and advanced reasoning capabilities to your AI coding assistant.

## 🚀 Why OpenRouter?

- **Unified Billing**: One API key, one invoice for all your AI models
- **No Waitlists**: Instant access to Perplexity's latest models including Sonar Pro, Deep Research, and Reasoning
- **Simple Integration**: OpenAI-compatible API means seamless integration
- **Usage Tracking**: Monitor costs and usage across all models in one dashboard
- **High Availability**: OpenRouter's infrastructure ensures reliable access

## 🎯 Features

This MCP server provides three powerful tools:

- **`perplexity_ask`**: Real-time web search using Sonar Pro for quick, accurate answers
- **`perplexity_research`**: Deep research capabilities for comprehensive analysis
- **`perplexity_reason`**: Advanced reasoning with Perplexity's Sonar Reasoning Pro (powered by DeepSeek R1)

## 📦 Quick Start

### For Claude Code

1. **Clone and build the project:**
```bash
git clone https://github.com/yourusername/perplexity-mcp-openrouter.git
cd perplexity-mcp-openrouter/perplexity-ask
npm install && npm run build
```

2. **Get your OpenRouter API key:**
   - Sign up at [OpenRouter](https://openrouter.ai/)
   - Generate an API key from your [dashboard](https://openrouter.ai/keys)

3. **Install in Claude Code:**
```bash
# From the perplexity-ask directory
claude mcp add openrouter-perplexity -s user -- env OPENROUTER_API_KEY=YOUR_API_KEY_HERE node "$(pwd)/dist/index.js"
```

That's it! Look for the hammer icon in Claude Code to access your new tools.

### For Cursor

1. Open Cursor Settings (`Cmd/Ctrl + ,`)
2. Navigate to **Models** → **Model Context Protocol**
3. Click **"Add new MCP server"**
4. Add this configuration:

```json
{
  "openrouter-perplexity": {
    "command": "node",
    "args": ["/path/to/perplexity-mcp-openrouter/perplexity-ask/dist/index.js"],
    "env": {
      "OPENROUTER_API_KEY": "YOUR_API_KEY_HERE"
    }
  }
}
```

5. Restart Cursor to activate the tools

## 🛠️ Available Tools

### perplexity_ask
Engage in conversations with real-time web search capabilities. Perfect for:
- Getting current information
- Fact-checking
- Quick research queries

### perplexity_research  
Perform deep, multi-step research with comprehensive citations. Ideal for:
- In-depth technical research
- Comparative analysis
- Literature reviews

### perplexity_reason
Advanced reasoning and problem-solving using Sonar Reasoning Pro. Best for:
- Complex problem decomposition
- Step-by-step analysis
- Mathematical and logical reasoning

## 💡 Usage Examples

Once installed, you can use these tools naturally in your conversations:

- "Use perplexity_ask to find the latest React 19 features"
- "Research the performance differences between Bun and Node.js"
- "Help me reason through this algorithm's time complexity"

## 🐳 Docker Support

For containerized deployments:

```bash
# Build the image
docker build -t mcp/openrouter-perplexity -f perplexity-ask/Dockerfile .

# Run the container
docker run -i --rm -e OPENROUTER_API_KEY=YOUR_API_KEY_HERE mcp/openrouter-perplexity
```

## 🔧 Configuration

### Environment Variables
- `OPENROUTER_API_KEY`: Your OpenRouter API key (required)

### Advanced Options
Modify request parameters in `perplexity-ask/index.ts`:
- Temperature, max_tokens, and other OpenAI-compatible parameters
- See [OpenRouter docs](https://openrouter.ai/docs) for full options

## 📊 Monitoring Usage

Track your usage and costs in the [OpenRouter dashboard](https://openrouter.ai/activity):
- Real-time usage statistics
- Cost breakdown by model
- Request logs and debugging

## 🐛 Troubleshooting

### MCP Server shows "failed" status
1. Verify you're in the `perplexity-ask` directory when running the install command
2. Check your API key is valid at [OpenRouter dashboard](https://openrouter.ai/keys)
3. Try removing and re-adding:
   ```bash
   claude mcp remove openrouter-perplexity
   # Then run the install command again
   ```

### "Connection closed" errors
- Ensure `dist/index.js` exists (run `npm run build`)
- Check file permissions: `chmod +x dist/index.js`

### Tools not appearing
- Restart Claude Code or Cursor after installation
- Check for the hammer icon (Claude) or tool menu (Cursor)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🔗 Resources

- [OpenRouter Documentation](https://openrouter.ai/docs)
- [MCP Specification](https://modelcontextprotocol.io)
- [Perplexity API Reference](https://docs.perplexity.ai/api-reference)

---

Built with ❤️ to make AI-powered research accessible in your favorite coding tools.