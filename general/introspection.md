# Introspection

Claude will sometimes talk as though it can remember its ‘unverbalised
thoughts’— that is, its model's internal activations— from previous points in
the conversation.  This isn't *completely* false, but it's not strictly true,
either.  When Claude talks about “what it was thinking”, it's *making inferences
based on its previous output*.  Usually these inferences are reasonably correct,
because the previous output would *usually* have been based on previous input or
output from *before* that, which would *usually* still be visible in the context
window.  This isn't necessarily true in all cases!  And technically speaking,
there is still no *direct* sense in which Claude can remember “what it was
thinking”.

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

*(to do: link to Anthropic's interpretability papers)*
