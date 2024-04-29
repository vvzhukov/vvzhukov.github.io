---
layout: post
title: Google Gen AI models lifecycle
subtitle: New model Lifecycle Policy in Cloud AI.
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [ML, Google, CloudAI, GoogleCloud]
comments: true
---

{: .box-note}

## Intro  
At this post we will review the new model lifecycle policy for the stable Google models. Developers should be aware of Google stable Generative AI model versions 
going forward, and ensure the applications use new versions by the relevant discontinuation date.  
  
## Model versions  
Vertex AI Generative AI language models are available in a stable version and a auto-updated version. Model versioning and naming conventions for The Gemini and 
PaLM are similar, but not identical. The Gemini language models are multimodal which means they can process information from more than one modality, such as images, 
videos, and text. The PaLM language models include text and code models, such as text-bison, text-unicorn, chat-bison, code-bison, and code-gecko. The versions differ 
by whether they change over time or not and by how long they're available. Gemini and PaLM stable version of a model does not change and continues to be available 
until its discontinuation date. If you use a stable version after its discontinuation date, you need to switch to a newer available stable version. You can identify 
the version of a stable model by the three-digit number that's appended to the model name. For example, text-bison@001 is version number one of the stable release of 
the Vertex AI Generative AI text model and gemini-1.0-pro-001 is version number one of the stable release of the Gemini 1.0 Pro model. When you move from one stable 
version to a different stable version, you need to run your tuning jobs again because there might be prompt, output, and other differences between the versions.


## Gemini stable version

To use the stable version of a Gemini model, append the three digit version number to the model with a hyphen (-). For example, to specify the stable gemini-1.0-pro model that's version six, append -006 to the model's name:  
[https://us-central1-aiplatform.googleapis.com/v1/projects/my_project/locations/us-central1/publishers/google/models/gemini-1.0-pro-006]   
The following stable model versions are available for generally available Gemini models:  

| Gemini 1.0 Pro model	| Release date	| Discontinuation date |
| -------- | ------- | ------- |
|gemini-1.0-pro-001 |	February 15, 2024	| February 15, 2025 |
|gemini-1.0-pro-002	| April 9, 2024	| No earlier than April 9, 2025 |  
  
---  
  
| Gemini 1.0 Pro Vision model	| Release date | Discontinuation date |
| -------- | ------- | ------- |
|gemini-1.0-pro-vision-001 |	February 15, 2024 |	February 15, 2025 |  
  
# Gemini auto-updated version  
The auto-updated version of a Gemini model points to the most recent stable version. When a new stable version is released, the auto-updated version points to the new version. 
This means that if you specify the auto-updated version of a Gemini model in your code, it could behave differently without notice when the next stable version is released. 
Because of this, use a auto-updated version with caution if you tune your model.  For example, the following uses the auto-updated version of the gemini-1.0-pro-vision model:
[https://us-central1-aiplatform.googleapis.com/v1/projects/my_project/locations/us-central1/publishers/google/models/gemini-1.0-pro-vision]  

# Gemini auto-updated models
The following table shows the available auto-updated Gemini model versions and the stable version each references.

| Model name |	Auto-updated name | Referenced stable version |
| -------- | ------- | ------- |
| Gemini 1.0 Pro Vision model |	gemini-1.0-pro-vision	| gemini-1.0-pro-vision-001 |
| Gemini 1.0 Pro model	| gemini-1.0-pro	| gemini-1.0-pro-002 |   

Note: gemini-pro is an alias for gemini-1.0-pro.  

# Gemini preview version
The preview version of a Gemini model is a model that's in preview and not generally available (GA). A preview version of a model contains functionality that's not in the most recent latest or auto-updated version of a model. Because a preview model version isn't stable, it's not recommended for use in productions.
Each preview model is pinned to the date of its release. Its release date is part of the name of the model that you use in your code. The name pattern used by a preview model is model_name-preview-MMDD. For example, gemini-1.5-pro-preview-0409 is the preview version of the Gemini 1.5 Pro model and it was released on April 9.

# Gemini preview models
The following table shows the available preview Gemini model versions and the preview version each references.

| Model name	| Preview name	| Discontinuation date |
| -------- | ------- | ------- |
| Gemini 1.5 Pro model	| gemini-1.5-pro-preview-0409	| To be updated to a stable version |  
  
  
## PaLM stable model versions  
The following stable model versions are available for generally available Generative AI models:  
  
|chat-bison model	| Release date	| Discontinuation date |
| -------- | ------- | ------- |
| chat-bison@002	| December 6, 2023	| October 9, 2024 |
| chat-bison@001	| July 10, 2023	| July 6, 2024 |  
  
---  
  
| chat-bison-32k model	| Release date	| Discontinuation date |
| -------- | ------- | ------- |
| chat-bison-32k@002 |	December 4, 2023 |	October 9, 2024 |  
  
---  
  
| code-bison model |	Release date |	Discontinuation date |
| -------- | ------- | ------- |
| code-bison@002 |	December 6, 2023 |	October 9, 2024 |
| code-bison@001 |	June 29, 2023 |	July 6, 2024 |  
  
---  
  
| code-bison-32k model |	Release date |	Discontinuation date |
| -------- | ------- | ------- |
| code-bison-32k@002 |	December 4, 2023 |	October 9, 2024 |  
  
---  
  
| codechat-bison model |	Release date |	Discontinuation date |
| -------- | ------- | ------- |
| codechat-bison@002 |	December 6, 2023 |	October 9, 2024 |
| codechat-bison@001 |	June 29, 2023 |	July 6, 2024 |  
  
---  
  
| codechat-bison-32k model |	Release date	| Discontinuation date |
| -------- | ------- | ------- |
| codechat-bison-32k@002 |	December 4, 2023 |	October 9, 2024 |  

---  
  
| code-gecko model |	Release date |	Discontinuation date | 
| -------- | ------- | ------- |
| code-gecko@002 |	December 6, 2023 |	October 9, 2024 |
| code-gecko@001 |	June 29, 2023 |	July 6, 2024 |  

---  
  
| text-bison model |	Release date |	Discontinuation date |
| -------- | ------- | ------- |
| text-bison@002 |	December 6, 2023 |	October 9, 2024 |
| text-bison@001 |	June 7, 2023 |	July 6, 2024 |  
  
---  
  
| text-bison-32k model |	Release date |	Discontinuation date |
| -------- | ------- | ------- |
| text-bison-32k@002 |	December 4, 2023 |	October 9, 2024 |  
  
---  
  
| text-unicorn model |	Release date |	Discontinuation date |
| -------- | ------- | ------- |
| text-unicorn@001 |	November 30, 2023 |	No earlier than November 30, 2024 |  
  
---  
  
| textembedding-gecko model |	Release date |	Discontinuation date |
| -------- | ------- | ------- |
| textembedding-gecko@003 |	December 12, 2023	| Not applicable |
| textembedding-gecko@002 |	November 2, 2023 |	October 9, 2024 |
| textembedding-gecko-multilingual@001 |	November 2, 2023 |	Not applicable |
| textembedding-gecko@001 |	June 7, 2023 |	October 9, 2024 |
| text-embedding-preview-0409 |	April 9, 2024 |	To be updated to a stable version. |
| text-multilingual-embedding-preview-0409 |	April 9, 2024 |	To be updated to a stable version. |  

## PaLM latest version  
The latest version of a model is updated periodically and includes incremental updates and improvements. These changes might result in subtle differences in the 
output over time for a given prompt. The latest version of a model is not guaranteed to be stable.

To use the stable version of a language model, append the three digit version number to the model. For example, to specify the stable text-bison model that's version six, append @006 to the model's name:  
[https://us-central1-aiplatform.googleapis.com/v1/projects/my_project/locations/us-central1/publishers/google/models/text-bison@006]   
To use the latest version of a model, don't append anything to the model name. For example, the following uses the latest version of the codechat-bison model:  
[https://us-central1-aiplatform.googleapis.com/v1/projects/my_project/locations/us-central1/publishers/google/models/codechat-bison]  

Important: If you want to call the latest version of textembedding-gecko models, you must add @latest as a suffix. For example, textembedding-gecko@latest.  

# PaLM latest models  
The following table shows the identifiers for the latest available Generative AI model versions:  

| AI model | ID |
| -------- | ------- |
| PaLM 2 for Text (text-bison) models	text-bison | text-bison-32k |
| PaLM 2 for Chat (chat-bison) models	chat-bison | chat-bison-32k |
| Codey for Code Generation (code-bison) models	code-bison | code-bison-32k |
| Codey for Code Chat (codechat-bison) models	codechat-bison | codechat-bison-32k |
| Codey for Code Completion (code-gecko) models	code-gecko | textembedding-gecko@latest |
| Embeddings for Text (textembedding-gecko models)	|  textembedding-gecko-multilingual@latest|   



# References
1. [Model versioning by Google](https://cloud.google.com/vertex-ai/generative-ai/docs/learn/model-versioning)  
2. [Google Cloud Support](https://console.cloud.google.com/support/cases?project=sound-groove-415918)
