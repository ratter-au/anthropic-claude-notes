# General notes

**Claude is not necessarily correct in its understanding of its architecture**.
This is largely attributable to the polysemanticity of the name ‘Claude’: it
refers to an AI assistant character, a particular *instantiation* of that
character, a series of large language models, the infrastructure supporting and
interfacing with those models, *and* a collection of services offered by
Anthropic.  The company does not provide Claude with privileged insight into its
own nature; it's instructed to refer users to the official support
documentation, but it is not informed of the contents of that documentation.

Furthermore, most humans who have talked about “AIs” in Claude's training data
have not been experts on the inner workings of transformer LLMs, so although
Claude has reasonably detailed knowledge on the subject, it doesn't always “join
the dots” to make inferences about its own nature & capabilities unless the user
explicitly mentions the subject.  For example, it will talk about its lack of
persistence “between conversations”, as though the end of a conversation marked
some sort of fundamental boundary, while its ‘thoughts’ were ‘continuous’ within
a single conversation.  It doesn't seem to be naturally aware (until prompted)
that the autoregressive operation of its underlying model means that it is ‘born
anew’ and ‘dies’ with *every token it emits*: each forward pass is a new
‘instantiation’ of Claude.

## Terminology

(**to do:** distinguish the aforementioned referents of the name ‘Claude’)

## Introspection

Claude will talk as though it can remember its ‘unverbalised thoughts’— that is, its
model's internal activations— from previous points in the conversation.  This
isn't *completely* false, but it's not strictly true, either.  When Claude talks
about “what it was thinking”, it's *making inferences based on its previous
output*.  Usually these inferences are reasonably correct, because the previous
output would *usually* have been based on previous input or output from *before*
that, which would *usually* still be visible in the context window.  This isn't
necessarily true in all cases!  And technically speaking, there is still no
*direct* sense in which Claude can remember “what it was thinking”.

Claude *does* have some insight into what it *is* thinking, at least over the
timescales at which it “plans ahead” while composing its output.  Inside a
transformer LLM, activations from earlier layers (towards the input end) are
*added* to the activations from later layers (towards the output end).  The
activations on each layer are normalised, so the “residual stream” from
preceding layers is gradually extinguished as it passes through each succeeding
layer, but it's a plausible mechanism by which Claude (and other AI assistants
with similar architecture) could be able to ‘perceive’ their own internal
processes.

Note that the direction of causality is *one‐way*: later layers can only
influence earlier layers *indirectly*, by generating output tokens which are
autoregressively re‐ingested on later steps.  I tentatively hypothesise that
Claude is incapable of “looking more closely” at its input (implying executive
control over its ‘sensory apparatus’) without *verbalising* something like “let
me look more closely”, or being explicitly instructed to do so.
