# Solution Architecture

In this workshop, you will create the SparkMate agent: a conversational agent designed to collaborate with teams to help them with idea generation, brainstorming, and development of concept details for products.

## Components of the Agent App

1. **Azure AI Foundry**

    This agent is built on Azure AI services.

      - **Generative AI model**: The underlying LLM powering this app is the <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/models?tabs=global-standard%2Cstandard-chat-completions#gpt-4o-mini-and-gpt-4-turbo" target="_blank" rel="noopener noreferrer">Azure OpenAI gpt-4o</a> LLM.

      - **Control Plane**: The app and its architectural components are managed and monitored using the <a href="https://ai.azure.com" target="_blank" rel="noopener noreferrer"> Azure AI Foundry</a> portal, accessible via the browser.
      
      - **Content filters**: As part of the layered security and safety architecture, we will configure and add content filters on inputs and outputs for the agent. These are focused on objectionable/harmful content as well as cross-prompt injection attacks (XPIA). We will not cover it in this workshop, but there additional safety and security guardrails available for your use: <a href="https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/content-filtering" target="_blank" rel="noopener noreferrer">custom blocklist</a>, <a href="https://learn.microsoft.com/en-us/azure/defender-for-cloud/ai-threat-protection" target="_blank" rel="noopener noreferrer">security recommendations</a>, and <a href="https://learn.microsoft.com/en-us/purview/developer/secure-ai-with-purview" target="_blank" rel="noopener noreferrer">data controls (via Purview)</a>. 
  
      - **Safety evaluations**: Pre-deployment and ongoing adversarial testing are key elements of ensuring that your layered security and safety architecture is operating as expected. During the workshop, we will run an evaluation using the AI Red Teaming agent via the SDK. This will run automated tests and provide scoring for objectionable/harmful content. The <a href="https://github.com/Azure/PyRIT" target="_blank" rel="noopener noreferrer">Python Risk Identification Tool for generative AI (PyRIT)</a> tool offers an expanded range of testing focus areas as well.
  
      - **Monitoring and alerting**: In this workshop, we will focus on the <a href="https://learn.microsoft.com/en-us/azure/defender-for-cloud/ai-threat-protection" target="_blank" rel="noopener noreferrer">Defender for Cloud</a> specifically for monitoring & alerting, but there are additional threat protection capabilities available for generativeAI applications including: integrated threat intelligence, threat hunting, investigation, and incident response automation.
  
        
## Extending the workshop techniques

The techniques and tools taught in this workshop are foundational and extensible to a variety of AI scenario types and agent architectures. However, it is important to note that it is not comprehensive of all potential vulnerabilities and techniques that may be needed for your organizational or scenario requriements. As you begin any agent building project, start by evaluatig the potential threats (traditional and AI-specific) based upon your proposed architecture and scenarios of use. This will enable you to define the protections that will be needed for your AI system. <a href="aka.ms/security-for-ai" target="_blank" rel="noopener noreferrer"> Security for AI hub </a>

The agent used was intentionally kept simplistic to optimize for ease of workshop participants getting started without minimal dependencie, but you can easily adapt the agent scenario by adjusting the system instructions and adding Knowledge and Actions in the Agent builder UI in AI Foundry (or using the SDK). 

