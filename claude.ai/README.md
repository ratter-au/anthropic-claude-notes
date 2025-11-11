# The `claude.ai` user interface

In general, Claude is given *very little* information by Anthropic about the
interface via which it is communicating with the user.  The `claude.ai` UI has a
tendency to present the results of separate process to the user as though though
“Claude did it”, when in reality there's a whole lot of work going on behind the
scenes to which neither Claude nor the user are privy.  This is an unfortunate
state of affairs which this document seeks to rectify.

## Retroactive changes to conversation history

**Changing the settings in the user interface may change the system prompt at
the start of the conversation**.  This change is *retroactive*, with the
potential to cause immense confusion.  Claude *does not know* that the contents
of the context window were *different* at the time that its preceding messages
were generated, so its previous answers can suddenly seem ‘wrong’ or
‘confabulated’ if settings are modified mid‐conversation.  This includes tools,
connectors, memories, ‘extended thinking’ mode, the ‘personal preferences’ text, the
‘style’ text, Anthropic's own updates to the system prompt, and possibly more.

## Personal preferences

Text entered in the ‘Settings → General → Personal preferences’ field is
inserted at the start of each conversation, at the end of the system prompt,
before the first `"Human: "` message, wrapped in
`<userPreferences>…</userPreferences>` tags.

Attempting to ‘inject’ additional instructions between a closing
`</userPreferences>` tag and another opening `<userPreferences>` tag results in
the ‘injected’ content being silently elided from the system prompt.  No warning
message is given, and the original text still appears on the ‘Settings’ page:
the elision only appears from Claude's point of view.  This is a sensible
countermeasure against idle meddling, since it prevents `claude.ai` users from
inserting extra instructions into Claude's system prompt.  It is still possible
to use the Claude API to insert arbitary instructions into the system prompt, so
this isn't preventing an ‘attack’ of any kind, just preventing a feature from
being used in a way for which it wasn't intended.

As noted above, editing the ‘personal preferences’ text causes retroactive
changes to Claude's context window across all conversations.

## Tools

**Claude's system prompt doesn't inform it about any tools that aren't currently
enabled**.

(**to do:** include brief descriptions for all the tools; maybe the input
schemas, too.)

(**to do:** describe the remarkably kludgy implementation of the `artifacts` tool)

## Memories

(**to do:** further investigation into how this works)
