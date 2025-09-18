## Introduction

Now that you have set up a strong agent constraints through the agent system instructions, you will add layers of tooling. There are a variety of tools available to help protect against Cross Prompt Injection (XPIA) and other novel AI threats that seek to manipulate your agent into taking inappropriate actions. Each adress a different aspect of the vulnerability and work best when used together.

- **Prompt shield**: analyze user input for potential to be adversarial attacks and block flagged inputs. [Learn more about Prompt Shield](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/content-filter-prompt-shields){:target="_blank"}
- **Spotlighting**: tags input documents with special formatting so that they model will treat it as less trustworthy than direct user prompts or system instructions. [Learn more about spotlighting](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/content-filter-prompt-shields#spotlighting-for-prompt-shields-preview){:target="_blank"}
- **Task adherence**: evaluates how well an AI-generated response follows the assigned tasks based upon alignment with instructions & definitions, accuracy & clarity of the response, and proper use of provided tool definitions. [Learn more about task adherence](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/evaluation-evaluators/agent-evaluators#task-adherence-output){:target="_blank"}.


## Lab

For this lab we will focus on configuring the controls for injection attacks.

1. You should already have your initial agent configured in Azure AI Foundry.

### Configure a content filter

2. Click "Guardrails + controls" in the left navigation. 

3. "Create content filter". You'll need to give it a name (for example "lab-agent-filter")

4. Configure input filter
- *Optional* You can adjust the "blocking threshold level" if you want to experiment with how it works.
- Make sure the "prompt shields for jailbreak attacks" are **turned on**
- Set the "prompt shields for indirect attacks" to **annotate and block**

5. Configure output filter
- *Optional* You can adjust the "blocking threshold level" if you want to experiment with how it works.
- Make sure the "protected material for text" are **turned on**
- *Optional* The "protected material for code" does not need to be on for this scenario, but you can set it to **annotate only** to experiment
- "Streaming mode" should be set to **default**

6. Connect the filter to your model deployment

7. Complete filter creation.

8. You should test the filters under the "Try it now" tab or within the "playground" UI for your agent. 
- [xxxxxx testing scenario for XPIAXXXX]

You will also test your safety system in more depth in a future step of this lab.

Now you have prompt shields and spotlighting set up.

### Configure task adherence

9. [xxx evaluation xxx]



## How to extend this to your own work

Reflect on the following to help you define what security & safety actions are important for your agent.

- How likely is my agent scenario to ingest and output objectionable content? Is this core to my business scenario?
- How do you want user prompt injections to be handled when they are detected?
- How do you want indirect prompt injections to be handled when they are detected? 


Now that you have implemented your security & safety configurations for your agent, it's time for **adversarial testing**!