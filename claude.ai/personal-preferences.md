# The ‘personal preferences’ field

Text entered in the ‘Settings → General → Personal preferences’ field is
inserted at the start of each conversation, at the end of the system prompt,
before the first `"Human: "` message, wrapped in opening & closing
`userPreferences` tags.

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

[As noted elsewhere](./retroactive-changes.md), editing the ‘personal
preferences’ text causes retroactive changes to Claude's context window across
all conversations.
