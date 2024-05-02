# clai: command line artificial intelligence
[![Go Report Card](https://goreportcard.com/badge/github.com/baalimago/clai)](https://goreportcard.com/report/github.com/baalimago/clai)

`clai` integrates AI models of multiple vendors via with the terminal.
You can generate images, text, summarize content and chat while using native terminal functionality, such as pipes and termination signals.

The multi-vendor aspect enables easy comparisons between different models, also removes the need for multiple subscriptions: most APIs are usage-based (some with expiration time).

![clai_in_action_example](./img/example.gif "Example of clai in action")

## Features
* Text summarization from:
    * Piped data
    * Globbed file input
* Conversations
* Tools calling [with easily forkable + extendable tools](./internal/tools/)
* Photo generation
* Human readable / robot readable output
* 100% standard go library (except for /x/net)
    

## Prerequisites
- **Go:** Install Go from [here](https://golang.org/doc/install).
- **OpenAI API Key:** Set the `OPENAI_API_KEY` env var to your [OpenAI API key](https://platform.openai.com/docs/quickstart/step-2-set-up-your-api-key). [Text models](https://platform.openai.com/docs/models/gpt-4-and-gpt-4-turbo), [photo models](https://platform.openai.com/docs/models/dall-e).
- **Anthropic API Key:** Set the `ANTHROPIC_API_KEY` env var to your [Anthropic API key](https://console.anthropic.com/login?returnTo=%2F). [Text models](https://docs.anthropic.com/claude/docs/models-overview#model-recommendations).
- **Mistral API Key:** Set the `MISTRAL_API_KEY` env var to your [Mistral API key](https://console.mistral.ai/). [Text models](https://docs.mistral.ai/getting-started/models/)
- **Glow**(Optional): Install [Glow](https://github.com/charmbracelet/glow) for formatted markdown output when querying text responses.

Note that you can only use the models that you have bought an API key for.

Most text and photo based models within the respective vendors are supported, see [model configurations](./EXAMPLES.md#Models) for how to swap.

## Get started
```bash
go install github.com/baalimago/clai@latest
```

Either look at `clai help` or the [examples](./EXAMPLES.md) for how to use `clai`.

## Honorable mentions
This project was originally inspired by: [https://github.com/Licheam/zsh-ask](https://github.com/Licheam/zsh-ask), many thanks to Licheam for the inspiration.
