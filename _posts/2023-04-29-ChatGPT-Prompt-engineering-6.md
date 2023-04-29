---
layout: post
title: ChatGPT Prompt engineering VI
subtitle: Prompt expanding
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [ChatGPT, LLM, Python]
comments: true
---

{: .box-note}

## Previous guides
- [ChatGPT Prompt engineering I: Intro to get familiar with the prompt strategies.](https://vvzhukov.github.io/2023-04-29-ChatGPT-Prompt-engineering-1/)
- [ChatGPT Prompt engineering II: Prompt development strategies](https://vvzhukov.github.io/2023-04-29-ChatGPT-Prompt-engineering-2/)
- [ChatGPT Prompt engineering III: Prompt summarizings](https://vvzhukov.github.io/2023-04-29-ChatGPT-Prompt-engineering-3/)
- [ChatGPT Prompt engineering IV: Prompt inferring](https://vvzhukov.github.io/2023-04-29-ChatGPT-Prompt-engineering-4/)
- [ChatGPT Prompt engineering V: Prompt transforming](https://vvzhukov.github.io/2023-04-29-ChatGPT-Prompt-engineering-5/)

## Setup
```python
import openai
import os

from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv()) # read local .env file

openai.api_key  = os.getenv('OPENAI_API_KEY')

def get_completion(prompt, model="gpt-3.5-turbo",temperature=0): # Andrew mentioned that the prompt/ completion paradigm is preferable for this class
    messages = [{"role": "user", "content": prompt}]
    response = openai.ChatCompletion.create(
        model=model,
        messages=messages,
        temperature=temperature, # this is the degree of randomness of the model's output
    )
    return response.choices[0].message["content"]
```

## Customize the automated reply to a customer email given the sentiment from the lesson on "inferring", and the original customer message, customize the email

```python
sentiment = "negative"
```

### review for a blender

```python
review = f"""
So, they still had the 17 piece system on seasonal \
sale for around $49 in the month of November, about \
half off, but for some reason (call it price gouging) \
around the second week of December the prices all went \
up to about anywhere from between $70-$89 for the same \
system. And the 11 piece system went up around $10 or \
so in price also from the earlier sale price of $29. \
So it looks okay, but if you look at the base, the part \
where the blade locks into place doesn’t look as good \
as in previous editions from a few years ago, but I \
plan to be very gentle with it (example, I crush \
very hard items like beans, ice, rice, etc. in the \ 
blender first then pulverize them in the serving size \
I want in the blender then switch to the whipping \
blade for a finer flour, and use the cross cutting blade \
first when making smoothies, then use the flat blade \
if I need them finer/less pulpy). Special tip when making \
smoothies, finely cut and freeze the fruits and \
vegetables (if using spinach-lightly stew soften the \ 
spinach then freeze until ready for use-and if making \
sorbet, use a small to medium sized food processor) \ 
that you plan to use that way you can avoid adding so \
much ice if at all-when making your smoothie. \
After about a year, the motor was making a funny noise. \
I called customer service but the warranty expired \
already, so I had to buy another one. FYI: The overall \
quality has gone done in these types of products, so \
they are kind of counting on brand recognition and \
consumer loyalty to maintain sales. Got it in about \
two days.
"""
```

```python
prompt = f"""
You are a customer service AI assistant.
Your task is to send an email reply to a valued customer.
Given the customer email delimited by ```, \
Generate a reply to thank the customer for their review.
If the sentiment is positive or neutral, thank them for \
their review.
If the sentiment is negative, apologize and suggest that \
they can reach out to customer service. 
Make sure to use specific details from the review.
Write in a concise and professional tone.
Sign the email as `AI customer agent`.
Customer review: ```{review}```
Review sentiment: {sentiment}
"""
response = get_completion(prompt)
print(response)
```

## Remind the model to use details from the customer's email

```python
prompt = f"""
You are a customer service AI assistant.
Your task is to send an email reply to a valued customer.
Given the customer email delimited by ```, \
Generate a reply to thank the customer for their review.
If the sentiment is positive or neutral, thank them for \
their review.
If the sentiment is negative, apologize and suggest that \
they can reach out to customer service. 
Make sure to use specific details from the review.
Write in a concise and professional tone.
Sign the email as `AI customer agent`.
Customer review: ```{review}```
Review sentiment: {sentiment}
"""
response = get_completion(prompt, temperature=0.7)
print(response)
```

## Temperature
Parameter of the model responsible for the 'randomness' of the output. 
The higher the temperature the more chances to get uniques response.

### Example
My favourite drink is: lemonade [53%], water [30%], rum [17%]  
Temperature = 0 -> lemonade, lemonade, lemonade  
Temperature = 0.3 -> lemonade, water, lemonade  
Temperature = 0.7 -> rum, water, lemonade  

#### References
- [deeplearning.ai courses](https://www.deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/)
- [deeplearning.ai prompt engineering](https://learn.deeplearning.ai/chatgpt-prompt-eng)
- [chatgpt](https://chat.openai.com)
- [chatgpt docs](https://platform.openai.com/docs/introduction)
