---
layout:           note
ref:              genAI
lang:             en
idiom:            en_US
imagepath:        'images/genAI/'
images:           
  -  'genAI_docker.png'
  -  'genAI_docker27.png'
  -  'genAI_nvidiaDriverGPU.png'
  -  'genAI_lastBuild.png'
  -  'genAI_running.png'

menu:             false
citation:         'Docker. Accelerated Development with AI & ML. Available at: https://www.docker.com/blog/introducing-a-new-genai-stack/ and, https://neo4j.com/developer-blog/genai-app-how-to-build/'
toc:              true
title:            'GenAI Stack Walkthrough: Behind the Scenes With Neo4j, LangChain, and Ollama in Docker'
headtitle:        'Stack GenAI con Docker, Neo4J, LangChain y Ollama.'
shorttitle:       'Installing Generative Artificial Intelligence Assistant, with an example from the Docker Team, for Windows 10.21H2, with GeForce GT 710 GPU: AI/MLearning integration made easy.'
year:             '2023'
author:           'Docker Team'
department:       ''
keywords:         
  -  'Generative AI; Docker; ChatGPT'

status:           'In process'
license:          '© 2024 Docker Inc. All rights reserved'
pubdate:          '2023-10-05'
modified_date:    '2024-03-11'
traductor:        'FJ Aguayo'
---





Control de citas: [^1], [^2], [^3], [^4], [^5], [^6], [^7], [^8], [^9], [^10], [^11], [^12], [^13], [^14], [^15], [^16], [^17], [^18], [^19], [^20], [^21], [^22], [^23], [^24], [^25], [^26], [^27], [^28], [^29], [^30], [^31], [^32], [^33], [^34], [^35], [^36], [^37], [^38], [^39], [^40], [^41], [^42], [^43], [^44], [^45], [^46], [^47], [^48], [^49], [^50], [^51], [^52], [^53], [^54], [^55], [^56], [^57], [^58], [^59], [^60], [^61], [^62], [^63], [^64], [^65], [^66], [^67], [^68], [^69], [^70], [^71], [^72], [^73], [^74], [^75], [^76], [^77], [^78], [^79], [^80], [^81], [^82], [^83], [^84], [^85], [^86], [^87], [^88].





> **{{ site.data.i18n[page.lang].abstract }}:**  At DockerCon 2023, with partners Neo4j, LangChain, and Ollama, we announced a new GenAI Stack. We have brought together the top technologies in the generative artificial intelligence (GenAI) space to build a solution that allows developers to deploy a full GenAI stack with only a few clicks.

**{{ site.data.i18n[page.lang].keywords}}:**  GenAI Stack, Docker, Neo4j, Ollama, LangChain, Generative Artificial Intelligence.

#   1. Introduction
  
  
  The requirements for deploying the Generative Artificial Intelligence application in a Docker container are found in **[^2]** on the Docker Documentation page. On Windows, the GenAI application can benefit from GPU acceleration only if the latest graphics card driver is installed. To do this, it is necessary to consult **[^3]** the Official NVidia Drivers Page. And they must be updated before beginning this installation and subsequent deployment. In the case of Linux, it will be necessary to proceed in the same way and perform a native installation (compiling) of the Docker Engine itself so that the GPUs work correctly. (See, https://docs.docker.com/guides/use-case/genai-pdf-bot/containerize/#prerequisites)
  
  
  







#  Abbreviations



The following abbreviations are used:

| Acron.  | Concept    |  
|  :---:     |  :---    |  
|  AI  |  Artificial Intelligence  | 
|  AOP  |  Agent-Oriented Programming  | 
|  AOSE  |  Agent-Oriented Software Engineering  | 
|  APL  |  Agent Programming Language  | 
|  BDI  |  Belief-Desire-Intention  | 
|  CPS  |  Cyber-Physical Systems  | 
|  DSL  |  Domain Specific Language  | 
|  HTN  |  Hierarchical Task Network  | 
|  Iot  |  Internet of Things  | 
|  MAPC  |  Multi-Agent Programming Contest  | 
|  MAS  |  Multi-Agent System  | 
|  OOP  |  Object-Oriented Programming  | 
|  PRS  |  Procedural Reasoning System  | 





#  References

[^1]:  **[1]**. Introducing a New GenAI Stack: Streamlined AI/ML Integration Made Easy. Visited (2024) [https://www.docker.com/blog/introducing-a-new-genai-stack/](https://www.docker.com/blog/introducing-a-new-genai-stack/).

[^2]:  **[2]**. Containerize a generative AI application. Visited (2024) [https://docs.docker.com/guides/use-case/genai-pdf-bot/containerize/](https://docs.docker.com/guides/use-case/genai-pdf-bot/containerize/).

[^3]:  **[3]**. Neo4j Developer Blog. M Hunger, T Bratanix, and O Hane. GenAI Stack Walkthrough: Behind the Scenes With Neo4j, LangChain, and Ollama in Docker. Visited (2024). [https://neo4j.com/developer-blog/genai-app-how-to-build/](https://neo4j.com/developer-blog/genai-app-how-to-build/)