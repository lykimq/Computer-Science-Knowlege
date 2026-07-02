# AI Engineer

## Core LLM Elements

![Core LLM Elements](pics/Mastering_Large_Language_Model_Parameters.png)


### Tokens
A token is the smallest unit of text an LLM processes. A token can be a full word, part of a word (subword), or a single character.
Because the model predicts the next token in a sequence, tokens directly affect:
- API cost (usually calculated from input and output tokens)
- Processing speed
- Context window limits (the maximum number of tokens the model can read at once)

### Context
Context is all information the model can see before it generates a response.
Context commonly includes:
- The current user query
- System instructions or prompt
- Previous conversation turns
- Supporting materials (RAG content, attached files, related data)

The clearer and more relevant the context is, the more accurate and coherent the response tends to be.

### Sampling Parameters
Sampling parameters are settings that control how the model chooses the next token.
They influence the balance between:
- Stability and creativity
- Safety and risk-taking
- Consistency and diversity

### Temperature
Temperature controls how random text generation is.
- Low temperature (for example, 0.1-0.3): stable output with less deviation, useful for tasks that require high accuracy
- Medium temperature (0.4-0.8): a balance between accuracy and natural variation
- High temperature (0.9+): more creative output, but more likely to drift and become less consistent

Practical tip: if you need safer and more predictable answers, lower temperature before tuning other parameters.

### Top-K
Top-K allows the model to choose the next token only from the K most likely options.
- Smaller K: more conservative choices, fewer surprises
- Larger K: more options, more diverse responses

Examples:
- K = 1 is similar to greedy decoding (always picks the highest-probability token)
- K = 40 often produces more natural results than K = 1

### Top-P (Nucleus Sampling)
Top-P does not use a fixed number of tokens like Top-K.
Instead, the model selects the smallest set of tokens whose cumulative probability is at least P.
- Low P (for example, 0.3-0.5): narrow token set, focused and stable output
- Medium P (0.8-0.9): good balance for many use cases
- High P (0.95-0.99): wider token set, more creativity, but potentially lower accuracy

Key difference:
- Top-K limits by a fixed number of tokens
- Top-P limits by cumulative probability, so it adapts more flexibly to each context

### Repetition Penalties
Repetition penalties help reduce repeated words or phrases during generation.

Two common types:
- Frequency penalty: the more often a token appears, the stronger the penalty
- Presence penalty: once a token has appeared, it gets penalized regardless of how many times it appears

Effects:
- Reduces repeated ideas
- Increases language diversity
- Can make text sound unnatural if penalties are too strong