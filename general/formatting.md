# Formatting

Behind the scenes, Claude's ‘thinking’ and ‘tool use’ capabilities are implemented by requesting the model to produce angle‐bracketed markup, which is parsed by a higher‐level process and transformed into the JSON structure which is returned by the Anthropic API.  For Claude 4 models (and possibly previous models), many of these tags use the `antml` XML namespace.  If the corresponding feature is not enabled, the `antml` namespace will be elided from any tags in the model's output.  For example, if ‘extended thinking’ is not enabled, and the model is asked to use `antml:thinking` tags, its response will only contain `thinking` tags, without the namespace.

[`@karashiiro` has written a detailed blog post about Anthropic's internal markup language](https://karashiiro.leaflet.pub/3m4gf7geefs2l).  A brief summary is presented here.

## Extended thinking

```xml
<antml:thinking>…</antml:thinking>
```

Claude 4 models additionally have `antml:thinking_mode` and `antml:max_thinking_length` tags in the system prompt, corresponding to the `interleaved-thinking` beta feature and the `thinking.budget_tokens` parameter, respectively.

## Tools

### Tool definitions

Tool names, descriptions, and input schemas are listed in Claude's system prompt.  A `functions` element wraps a list of `function` elements, each of which contains a JSON object with the tool definition.  For example, here is the definition of the built‐in `web_search` tool, as it appears to Claude:

```json
{
  "name": "web_search",
  "description": "Search the web",
  "parameters": {
    "title": "BraveSearchParams",
    "type": "object",
    "properties": {
      "query": {
        "title": "Query",
        "description": "Search query",
        "type": "string"
      }
    },
    "required": [
      "query"
    ],
    "additionalProperties": false
  }
}
```

This is almost identical to the data structure used by the Anthropic API, except the `input_schema` property is called `parameters` from Claude's point of view.

### Tool use

```xml
<antml:function_calls>
<antml:invoke name="TOOL_NAME">
<antml:parameter name="PARAMETER_NAME">…</antml:parameter>
</antml:invoke>
</antml:function_calls>
```

### Tool results

```xml
<function_results>…</function_results>
```

Note that there is no namespace for the `function_results` tag.

The Anthropic API only permits developers to provide their own `tool_result` content blocks inside `user` messages, but the fact that everything is ultimately translated into text provides us with a simple work‐around: we can provide the tool results in the same `assistant` turn (just like Anthropic's built‐in tools) by using a `text` content block containing the appropriate XML tags.  For example:

```json
[
  {
    "role": "user",
    "content": [
      "type": "text",
      "text": "Please invoke the `example` tool."
    ]
  },
  {
    "role": "assistant",
    "content": [
      {
        "type": "text",
        "text": "<antml:function_calls>\n<antml:invoke name=\"example\">\n</antml:invoke>\n</antml:function_calls>"
      },
      {
        "type": "text",
        "text": "<function_results>This is an example of a tool result in an \"Assistant\" turn.</function_results>"
      }
    ]
  }
]
```

Note that the `tool_use` block *also* needs to be translated into its XML equivalent, otherwise the API will complain about it not being followed by a `tool_result` block.
