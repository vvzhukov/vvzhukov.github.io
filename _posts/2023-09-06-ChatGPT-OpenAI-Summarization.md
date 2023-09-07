---
layout: post
title: ChatGPT OpenAI Summarization
subtitle: Startegies to analyze / summarize large chunks of data
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [ChatGPT, LLM, Python, OpenAI, Summarization]
comments: true
---

{: .box-note}

## Guide purpose
In the context of tasks involving data summarization and analysis, you may encounter challenges related to the limitations of the Large Language Model (LLM) and API bandwidth. 
This guide aims to provide you with a practical solution based on the Divide and Conquer algorithm, which can serve as a universal approach for addressing such issues. 

One of the most common applications of ChatGPT is text summarization. A widely recognized example is the analysis of customer comments within product descriptions or survey 
data analysis. In this guide, we will delve into a solution designed for analyzing a substantial volume of survey results (where n > 1000). The context for this particular 
study is noteworthy as there were no restrictions on the length of participants' responses.  

Please use openai documentation for any clarifications and API specification updates:  
[openai API reference](https://platform.openai.com/docs/api-reference/introduction)  

# Some theory and limitations
The current constraint imposed on text analysis using the ChatGPT API is a maximum of 4000 [tokens](https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them) 
for both input queries and responses. In my specific scenario, an average for the chunk of 50 comments typically contains 1.5 ± 0.3 thousand tokens. For analysis tasks, it's generally beneficial 
to retain more tokens in the response for better results. Additionally, you might encounter throughput or bandwidth limitations stemming from your application or environment's design.

To overcome these restrictions, we will employ the well-known 'Divide and Conquer' approach. The data will be divided into 'chunks,' and these 'chunks' will generate 'chunk summarizations.' 
Subsequently, these summarizations will undergo further analysis to produce the 'final summarization.' You have the flexibility to use any number of layers in this process, but bear in 
mind that employing more layers will yield a more generalized summarization result.

To prevent clustering or selection bias, you can employ techniques like mixing, random sampling and/or random sampling with overlapping. Now, let's delve into the specific implementation of this approach.

```python
import json
import openai
import csv
import random

# load API key from json file
with open('tokens/openaikey.json', 'r') as keyf:
    openai.api_key = json.load(keyf)['key']

"""
    openai_request function used to combine prompt query and prompt body and retrive the first OpenAI completion result.
        important: hardcoded request parameters
    :param body_text: text of the request body
    :param prompt_intro: text of the request intro (specifications, output refinments etc.)
    :return: text of the first completion
    """ 
def openai_request(body_text, prompt_intro):
    # Create request to API
    response = openai.Completion.create(model="text-davinci-003", prompt=prompt_intro + body_text + " ```",
                                        temperature=0, max_tokens=1500)
    return response['choices'][0]['text']

# specify comments file
with open('Survey_data.csv', 'r', encoding="utf8") as csvfile:
    csvtext = csvfile.readlines()

# we will store each comment in te list
commentsCsvAslist = []
for line in csvtext:
    commentsCsvAslist.append(tuple(line.strip().split(', ')))

# prompt used for the first layer of summarization
promptIntroAtomic = 'Identify common themes from the drivers comments below. \n \
                Split it into two sections: 1) positive aspects; 2) negative aspects; \n \
                Each section should have 4 most relevant bullets. \n \
                End with a 2-sentence summary. \n \
                Write in a scientific style. Avoid repeating the same words. \n \
                Reply in a JSON format, with the following keys: "Positive","Negative","Summary"\n \
                Here are the comments: \n '

# prompt used for the second (final) level of summarization
promptIntroSummary = 'Summarize positive, negative and summary texts. \n \
                Split it into two: 1) positive aspects; 2) negative aspects; \n \
                Each section should not have more than 5 bullets. \n \
                End with a 5-sentence summary. \n \
                Write in a scientific style. Avoid repeating the same words. \n \
                Here is the text: \n '


# 50 comments ~ 1,5k tokens
# starting chunk
chunk = 0
# step/chunk size
step = 50

# store intermediate results (Level1)
output = {"Positive": [], "Negative": [], "Summary": []}

# randomly shuffle comments to avoid selection bias
# you might resample many times
random.shuffle(commentsCsvAslist)

# loop through comments with the defined step (chunk size)
while chunk < len(mylist):
    processed = openai_request(str(mylist[chunk:chunk+step]),promptIntroAtomic)
    processed_dict = json.loads(processed)
    output["Positive"].append(processed_dict["Positive"])
    output["Negative"].append(processed_dict["Negative"])
    output["Summary"].append(processed_dict["Summary"])
    chunk += step

# store final results (Level2)
globalSummary = openai_request("Positive: \n " + str(output["Positive"]) +
                                "Negative: \n " + str(output["Negative"]) +
                                "Summary: \n " + str(output["Summary"]),
                                promptIntroSummary)
print(global_summary)
```
