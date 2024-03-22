# clai: command line artificial intelligence
[![Go Report Card](https://goreportcard.com/badge/github.com/baalimago/clai)](https://goreportcard.com/report/github.com/baalimago/clai)

`clai` integrates the OpenAI models with the terminal.
You can generate images, text, summarize content and chat while using native terminal functionality, such as pipes and termination signals.

![clai_in_action_example](./img/example.gif "Example of clai in action")

## Prerequisites
- **OpenAI API Key:** Set the `OPENAI_API_KEY` environment variable to your OpenAI API key. See here: [OpenAI API Key](https://platform.openai.com/docs/quickstart/step-2-set-up-your-api-key).
- **Glow (Optional):** Install [Glow](https://github.com/charmbracelet/glow) for formatted markdown output when querying text responses.

## Installation
```bash
go install github.com/baalimago/clai@latest
```

### Examples

Simple queries:
```bash
clai query My favorite color is blue, tell me some facts about it
```
```bash
clai -re `# Use the -re flag to use the previous query as context for some next query` \
    q Write a poem about my favorite colour 
```

Chatting:
```bash
clai chat new Lets have a conversation about Hegel
```
```bash
clai c continue 1 `# Continue some previous chat, list all chats with 'clai chat list'` 
```

Glob queries:
```bash
clai --raw `                    # Don't format output as markdown` \
    --chat-model gpt-3.5-turbo `# Use some other model` \
    glob '*.go' Generate a README for this project > README.md
```

Photos:
```bash
printf "flowers" `                  # Pipe any data into clai, such as a specialized prompt` \
    | clai  --photo-prefix flower ` # Photos are stored locally with randomized string as suffix, this sets prefix` \
            --photo-dir  /tmp/ `    # You can modify where to store the rendered image ` \ 
            -i `                    # Use xargs notation for replacing some substring with the piped in content` \
            photo A cat made of {}
```
Since -N alternatives are disabled for many newer OpenAI models, you can use [repeater](https://github.com/baalimago/repeater) to generate several responses from the same prompt:
```bash
NO_COLOR=true repeater -n 10 -w 3 -increment -file out.txt -output BOTH \
    clai -pp flower_INC p A cat made of flowers
```



```bash
clai help `# For more info about the available commands (and shorthands)`
```


## Configuration
On initial run, `clai` will create configuration files at `$HOME/.clai/`, one for photo and one for chat.
Here you can configure initial prompts, temperature and other settings.

Within `$HOME/.clai/conversations` you'll find all the conversations.
You can also modify the chats here as a way to prompt.

## Honorable mentions
This project is heavily inspired by: [https://github.com/Licheam/zsh-ask](https://github.com/Licheam/zsh-ask), many thanks to Licheam for the inspiration.
