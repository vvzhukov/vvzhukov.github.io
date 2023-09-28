---
layout: post
title: Exploring the New Web Parsing Features of ChatGPT
subtitle: Fetch content, Summarizing Articles, Comparing products and more
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [ChatGPT, LLM, Python, OpenAI, Web]
comments: true
---

{: .box-note}

## Purpose of the guide
In a world where information is abundant on the web, ChatGPT's new web parsing features are a game-changer. This latest update allows the AI model to not only understand and generate text but also extract valuable data from websites, making it a versatile tool for a wide range of tasks. In this blog post, we'll dive into the exciting world of ChatGPT's web parsing capabilities with some code examples.   
[openai API reference](https://platform.openai.com/docs/api-reference/introduction)  

# What Can ChatGPT Do with Web Parsing?
ChatGPT's web parsing features enable it to extract information from websites, such as:  
1. Fetching Content: It can retrieve text content, links, and other information from a given webpage.  
2. Summarizing Articles: ChatGPT can summarize articles or blog posts by analyzing the content and generating concise summaries.  
3. Answering Questions: You can ask questions about the information extracted from a webpage, and ChatGPT will provide answers based
on its understanding of the content.  
4. Comparing Products: It can compare products based on their specifications, prices, and user reviews from e-commerce websites.  
5. Providing Recommendations: ChatGPT can suggest products, services, or articles based on the content it extracts.  

Let's explore these capabilities with some code examples.  


## Example 1: Fetching Content from a Webpage
```python
import openai

# Your OpenAI API key
api_key = 'YOUR_API_KEY'

# URL of the webpage to parse
url = 'https://example.com'

# Prompt for web content extraction
prompt = f"Extract the main content from {url}"

# Call the ChatGPT API
response = openai.Completion.create(
    engine="davinci",
    prompt=prompt,
    max_tokens=150,
    api_key=api_key
)

# Extracted content
extracted_content = response.choices[0].text.strip()
print(extracted_content)
```

## Example 2: Summarizing an Article
```python
# Prompt for summarizing an article
prompt = "Summarize the following article: [Paste the article here]"

# Call the ChatGPT API with the article text
response = openai.Completion.create(
    engine="davinci",
    prompt=prompt,
    max_tokens=150,
    api_key=api_key
)

# Article summary
summary = response.choices[0].text.strip()
print(summary)
```

## Example 3: Answering Questions about Web Content
```python
# Web content extracted earlier
web_content = extracted_content

# Question about the content
question = "What is the main topic discussed in the article?"

# Combine the web content and question
prompt = f"Web Content: {web_content}\nQuestion: {question}"

# Call the ChatGPT API
response = openai.Completion.create(
    engine="davinci",
    prompt=prompt,
    max_tokens=50,
    api_key=api_key
)

# Answer to the question
answer = response.choices[0].text.strip()
print(answer)
```

These code examples illustrate how ChatGPT can be used to extract, summarize, and interact with web content. With these capabilities, 
ChatGPT becomes a powerful tool for automating tasks involving web data extraction and analysis. Whether you're a researcher, content 
creator, or just looking to gather information from the web, ChatGPT's web parsing features are here to help you streamline your workflow 
and make data retrieval a breeze.  

P.S. Written with a help of GPT-3.5
