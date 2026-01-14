# OpenAI Tool Calling Tutorial

This is a comprehensive example demonstrating OpenAI's function calling (tool calling) feature for AI developers.

## What is Tool Calling?

Tool calling allows Large Language Models to interact with external functions, APIs, and tools. Instead of just generating text, the model can decide when to call functions to retrieve information or perform actions.

## Setup

1. **Install dependencies:**
```bash
npm install openai
# or
npm install --save-dev @types/node typescript ts-node
```

2. **Set your OpenAI API key:**
```bash
export OPENAI_API_KEY='your-api-key-here'
```

3. **Run the example:**
```bash
npx ts-node toolcall.ts
```

## What's Included

### 1. **Basic Tool Calling Example**
- Shows how to define tools
- Demonstrates making API calls with tools
- Handles tool execution and responses

### 2. **Multi-Turn Conversations**
- Maintains conversation context
- Handles multiple queries in sequence
- Demonstrates stateful interactions

### 3. **Streaming with Tool Calls**
- Shows how to use streaming API with tools
- Processes tool calls from streamed responses

### 4. **Error Handling**
- Proper error handling for API calls
- Function execution error management
- JSON parsing safeguards

## Tool Definition Structure

```typescript
{
  type: 'function',
  function: {
    name: 'function_name',
    description: 'Clear description of what the function does',
    parameters: {
      type: 'object',
      properties: {
        param1: {
          type: 'string',
          description: 'Parameter description',
        },
      },
      required: ['param1'],
    },
  },
}
```

## Key Concepts

1. **Tool Choice**: Control when tools are used
   - `auto`: Model decides (recommended)
   - `required`: Force tool use
   - `none`: Disable tools
   - `{type: "function", function: {name: "..."}}`: Force specific tool

2. **Message Flow**:
   - User message → Model with tools
   - Model responds with tool_calls
   - Execute functions → Send results back
   - Model generates final response

3. **Function Implementation**:
   - Define tools in OpenAI format
   - Implement actual functions separately
   - Route tool calls to implementations
   - Return JSON strings as results

## Use Cases

- **Data Retrieval**: Weather, database queries, API calls
- **Calculations**: Math operations, conversions, analytics
- **Actions**: Send emails, create records, trigger workflows
- **Integrations**: Connect LLMs to any external system

## Best Practices

1. ✅ Write clear, specific function descriptions
2. ✅ Use proper JSON Schema for parameters
3. ✅ Handle errors gracefully
4. ✅ Return structured JSON responses
5. ✅ Validate function arguments before execution
6. ✅ Keep function implementations simple and focused
7. ✅ Test with various inputs and edge cases

## Common Pitfalls

1. ❌ Vague function descriptions → Model won't use them correctly
2. ❌ Missing required parameters → Parsing errors
3. ❌ Not sending tool results back → Incomplete responses
4. ❌ Forgetting to handle tool_calls → Logic errors
5. ❌ Not maintaining message history → Lost context

## Exercise Ideas

1. Add a new tool for currency conversion
2. Implement a tool that interacts with a real API
3. Create a tool that reads/writes to a database
4. Build a multi-agent system using tool calling
5. Add validation and error messages to tools

## Resources

- [OpenAI Function Calling Guide](https://platform.openai.com/docs/guides/function-calling)
- [OpenAI API Reference](https://platform.openai.com/docs/api-reference)
- [JSON Schema Documentation](https://json-schema.org/)

## License

MIT - Feel free to use this for teaching and learning!
