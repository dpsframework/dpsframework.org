---
layout:           note
ref:              genAI
lang:             es
idiom:            es_ES
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
title:            'IA-Generativa en Docker con Neo4j, LangChain, y Ollama'
headtitle:        'Stack GenAI con Docker, Neo4J, LangChain y Ollama.'
shorttitle:       'Instalacción de Asistente de Inteligencia Artficial Generativa, con ejemplo del Equipo de Docker, para Windows 10.21H2, con GPU GeForce GT 710: integración AI/MLearning de manera sencilla.'
year:             '2023'
author:           'Docker Team'
department:       ''
keywords:         
  -  'Generative AI; Docker; ChatGPT'

status:           'En proceso'
license:          '© 2024 Docker Inc. All rights reserved'
pubdate:          '2023-10-05'
modified_date:    '2024-03-11'
traductor:        'FJ Aguayo'
---







Control de citas: [^1], [^2], [^3], [^4], [^5], [^6], [^7], [^8], [^9], [^10], [^11], [^12], [^13], [^14], [^15], [^16], [^17], [^18], [^19], [^20], [^21], [^22], [^23], [^24], [^25], [^26], [^27], [^28], [^29], [^30], [^31], [^32], [^33], [^34], [^35], [^36], [^37], [^38], [^39], [^40], [^41], [^42], [^43], [^44], [^45], [^46], [^47], [^48], [^49], [^50], [^51], [^52], [^53], [^54], [^55], [^56], [^57], [^58], [^59], [^60], [^61], [^62], [^63], [^64], [^65], [^66], [^67], [^68], [^69], [^70], [^71], [^72], [^73], [^74], [^75], [^76], [^77], [^78], [^79], [^80], [^81], [^82], [^83], [^84], [^85], [^86], [^87], [^88].



> **{{ site.data.i18n[page.lang].abstract }}:**  En la conferencia de Docker [DockerCon 2023](https://www.dockercon.com/), los patrocinadores [Neo4j](https://neo4j.com/), [LangChain](https://www.langchain.com/), y [Ollama](https://ollama.ai/), han anunciado la disponibilidad de un nuevo Stack (agrupación) de Inteligencia Artificial Generativa (GenAI Stack). Ellos han reunido lo mejor y más avanzado de la tecnología del espacio definido por la Gen-AI y aportan una solución para permitir a los Desarrolladores contar con este Stack de GenAI completo con unos pocos cliks. Este documento es una traducción y una guía para su despliegue en Windows 10 con GForce GT 710.

**{{ site.data.i18n[page.lang].keywords}}:**  GenAI Stack, Docker, Neo4j, Ollama, LangChain, Generative Artificial Intelligence.

#   1. Introducción
  
  
  Los requisitos para desplegar en contenedor de Docker, a la aplicación de Inteligencia Artificial Generativa, se encuentran en **[^2]** en la págian de Documentación de Docker. En Windows, la aplicación GenAI puede beneficiarse de la aceleración de la GPU sólo si se instala el último driver de la tarjeta gráfica. Para ello es necesario consultar en **[^3]** la Página Oficial de los Drivers de NVidia. Y deben ser actualizados antes de comenzar esta instalación y el posterior despliegue. En el caso de Linux será necesario proceder del mismo modo y realizar una instalación nativa (compilando), al propio Docker Engine para que funcionen las GPU correctamente. (Véase, https://docs.docker.com/guides/use-case/genai-pdf-bot/containerize/#prerequisites )
  
  
  






#  Abreviaturas



Se han utilizado las siguientes abreviaturas:

| Acron.  | Concept    |     Concepto  | 
|  :---:     |  :---    |   :---  |  
|  AI  |  Artificial Intelligence  |  Inteligencia artificial  | 
|  AOP  |  Agent-Oriented Programming  |  Programación Orientada al Agente  | 
|  AOSE  |  Agent-Oriented Software Engineering  |  Ingeniería de Software Orientada al Agente  | 
|  APL  |  Agent Programming Language  |  Lenguaje de programación del agente  | 
|  BDI  |  Belief-Desire-Intention  |  Creencia-Deseo-Intención  | 
|  CPS  |  Cyber-Physical Systems  |  Sistemas ciberfísicos  | 
|  DSL  |  Domain Specific Language  |  Lenguaje específico de dominio  | 
|  HTN  |  Hierarchical Task Network  |  Red jerárquica de tareas  | 
|  Iot  |  Internet of Things  |  Internet de las Cosas  | 
|  MAPC  |  Multi-Agent Programming Contest  |  Concurso Programación Multiagente  | 
|  MAS  |  Multi-Agent System  |  Sistema Multi-Agente  | 
|  OOP  |  Object-Oriented Programming  |  Programación orientada a objetos  | 
|  PRS  |  Procedural Reasoning System  |  Sistema de razonamiento procedimental    | 





#  Bibliografía

#  References



[^1]:  **[1]**. Introducing a New GenAI Stack: Streamlined AI/ML Integration Made Easy. Visited (2024) https://www.docker.com/blog/introducing-a-new-genai-stack/.


[^2]:  **[2]**. Containerize a generative AI application. Visited (2024) https://docs.docker.com/guides/use-case/genai-pdf-bot/containerize/.

[^3]:  **[3]**. Neo4j Developer Blog. M Hunger, T Bratanix, and O Hane. GenAI Stack Walkthrough: Behind the Scenes With Neo4j, LangChain, and Ollama in Docker. Visited (2024). [https://neo4j.com/developer-blog/genai-app-how-to-build/](https://neo4j.com/developer-blog/genai-app-how-to-build/)











