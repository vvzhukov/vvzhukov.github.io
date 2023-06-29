---
layout: post
title: ChatGPT OpenAI CLI
subtitle: Set up and some hints
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [ChatGPT, LLM, Python, OpenAI, CLI]
comments: true
---

{: .box-note}

## Guide purpose
Use this guide if you faced any issues with setting up the environment for openai CLI / toolbox.
[openai API reference](https://platform.openai.com/docs/api-reference/introduction)

# Setup
1. Install the openai package with dependencies:
```bash
pip install --upgrade openai
```
you may also install it using npm, brew or other package managers.

2. Set your OPENAI_API_KEY environment variable :
```bash
export OPENAI_API_KEY="<OPENAI_API_KEY>"
```
3. Now in order to run openai script as a CLI tool we need to:  
- add shortcut to the bin
- make the script executable (for unix/mac)
```bash
python3 -m site --user-site
```
That will give you path to the user-site packages directory (for me'/home/vzhukov/.local/lib/python3.8/site-packages'). 
Add 'openai/_openai_scripts.py' and run the following command:
```bash
sudo chmod +x /home/vzhukov/.local/lib/python3.8/site-packages/openai/_openai_scripts.py
sudo sh -c 'echo python3 /home/vzhukov/.local/lib/python3.8/site-packages/openai/_openai_scripts.py \$\@ > /usr/local/bin/openai'
```
Here the first command will make script executable and the second will create link to 'openai' call.  
From now on you can use openai as a CLI tool, for example:
```bash
openai api fine_tunes.list
```


P.S. curl could be also handy when you are working with OpenAI API:
```bash
curl https://api.openai.com/v1/completions \
  -H "Authorization: Bearer <OPENAI_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{"prompt": "Why do I weven write these guides? :)", "model": "curie:ft-responder-2023-06-28-04-36-35"}'
```
