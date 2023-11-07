---
layout: post
title: GPT-4 Turbo, Assistants API, new modalities
subtitle: GPT-4 Turbo, Updated GPT-3.5 Turbo, Assistants API and more
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [ChatGPT, LLM, Python, OpenAI, Web]
comments: true
---

{: .box-note}

# Introducing OpenAI's Latest Innovations

OpenAI has been making significant strides in the field of artificial intelligence, and we are excited to announce some groundbreaking updates and features that are set to revolutionize the way you interact with AI. In this blog post, we will take a closer look at the latest developments, including the introduction of GPT-4 Turbo, updates to GPT-3.5 Turbo, the launch of the Assistants API, advancements in multimodal capabilities, and the introduction of GPTs for a more customizable ChatGPT experience.

## GPT-4 Turbo: A Leap Forward in AI

We are thrilled to introduce GPT-4 Turbo, our most advanced model to date. This powerhouse offers a context window of up to 128,000 tokens and is equipped with knowledge of world events up to April 2023. But that's not all – we've also made it more affordable. Input tokens are now priced at just $0.01 per 1,000 tokens, while output tokens cost only $0.03 per 1,000 tokens. This represents a remarkable 3x and 2x reduction in pricing, respectively, compared to the previous GPT-4 model.

GPT-4 Turbo doesn't stop at affordability; we've also enhanced its functionality. It now supports the ability to call multiple functions in a single message, ensuring that you always get valid functions with JSON mode. Additionally, we've improved accuracy in returning the right function parameters. Model outputs are more deterministic with our new reproducible outputs beta feature.

To access GPT-4 Turbo, simply pass 'gpt-4-1106-preview' in the API, with a stable production-ready model release planned for later this year.

## Updated GPT-3.5 Turbo

The new 'gpt-3.5-turbo-1106' is now your go-to option for even longer context. By default, it supports a context window of 16,000 tokens, and this extended context is available at significantly lower prices. Input tokens are now priced at $0.001 per 1,000 tokens, while output tokens cost $0.002 per 1,000 tokens.

Moreover, fine-tuning of this 16K model is available, making GPT-3.5 even more versatile. Fine-tuned GPT-3.5 is much more affordable, with input token prices decreasing by 75% to $0.003 per 1,000 tokens and output token prices dropping by 62% to $0.006 per 1,000 tokens. 'gpt-3.5-turbo-1106' now joins GPT-4 Turbo with improved function calling and reproducible outputs.

## Introducing the Assistants API

We're excited to present the beta version of our new Assistants API, designed to help you effortlessly build agent-like experiences in your applications. The potential use cases are endless, ranging from a natural language-based data analysis app to a coding assistant, an AI-powered vacation planner, a voice-controlled DJ, a smart visual canvas, and much more.

This API empowers the creation of purpose-built AI assistants that can follow specific instructions, leverage additional knowledge, and interact with models and tools to perform various tasks. Assistants now come with persistent Threads for developers, allowing you to hand off thread state management to OpenAI and work around context window constraints. They can also utilize new tools like Code Interpreter, Retrieval, and Function Calling. Our platform Playground offers you the opportunity to experiment with this new API without writing any code.

## Multimodal Capabilities

GPT-4 Turbo has taken a giant leap forward by supporting visual inputs in the Chat Completions API. This opens up exciting use cases like caption generation and visual analysis. You can access these vision features by using the 'gpt-4-vision-preview' model, which will be seamlessly integrated into the production-ready version of GPT-4 Turbo when it exits the preview phase later this year.

Additionally, you can now integrate DALL·E 3 for image generation into your applications via the Image generation API. We've also released text-to-speech capabilities through the newly introduced TTS model, featuring six natural-sounding voices to read text aloud for you.

## Customizable GPTs in ChatGPT

OpenAI is proud to launch a new feature called GPTs, which allows you to combine instructions, data, and capabilities to create a customized version of ChatGPT. This empowers you to control a larger portion of the experience, and GPTs can call developer-defined actions. We've designed plugins and actions to be very similar, making it a breeze to turn an existing plugin into an action. For more details, be sure to check out our documentation.

OpenAI continues to push the boundaries of AI innovation, and with these exciting updates, we're making it easier than ever for developers and users to harness the power of advanced AI models. The future of AI is here, and it's in your hands.

P.S. Written with a help of GPT-3.5
