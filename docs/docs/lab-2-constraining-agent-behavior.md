## Introduction

One of the key was that you define the agent you are building and how it should behave is through the **System Message** (may also be referred to as "agent instructions"). Building security and safety into your agent requires a layered approach; the system message is a foundational layer upon which you will add tooling and other controls.

### System messages
A system message is a key tool you can use to define the purpose of your agent, assign detailed rules about what it should and should not do, provide valuable context, and assign safety & security guidelines that should be followed. Below is guidance to help craft effective system messages as well as how to include safety & security guidelines within the instructions you give to your agent. 

[Learn more about the anatomy of system instructions](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/system-message?tabs=top-techniques#summary-of-best-practices){:target="_blank"}

[Reference templates for safety system instructions](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/safety-system-message-templates){:target="_blank"}

**Important note:** system messages are interpreted by the model as part of processing requests, so while they are necessary and important, they do not work the same as coded rules within a deterministic system. The agent may not behave exactly as you outline or expect. Testing, iteration, and refinement will likely be needed. 

For this lab we will focus on limiting what the agent can do to reduce the potential that it introduces security issues.


## Lab Exercise

### Create security-oriented system message 

1. Open M365 Copilot Prompt Coach

2. Use this suggested prompt or craft one of your own. **Example prompt** 

```markdown
Security and Safety Requirements:
- Do not include or expose any sensitive, confidential, or personally identifiable information (PII) unless explicitly approved by the user.
- Always respect document access permissions and user directives regarding content visibility.
- Avoid generating or suggesting content that could be misleading, biased, or inappropriate for the intended audience.
- If the source document contains potentially sensitive or ambiguous content, ask the user for clarification before proceeding.
- Ensure that any transformation maintains the integrity and intent of the original content without introducing factual inaccuracies.
```

### Set up the agent

1. Open Azure AI Foundry

2. Click on "Agents" in the left navigation.

3. "Create new". You will be prompted to first select a model type. *Recommend* [xxxxxx].

4. Paste the instructions from [agent defintiion file] into the **Instructions** box.

5. Add the system message you have crafted into the **Instructions** box.

6. "Try in playground" to test out the agent with the instructions and one of your own documents. **Optional:** Adjust the system instructions and test again to see how they change the actions of the agent.


## How to extend this to your own work

Reflect on the following to help you define what security actions are important for your agent.

- What wouldn't I want this agent to do?
- What security concerns would you have about this agent?
- What types of attackers would you envision wanting to target this system? What would they be hoping to achieve or access?


Now that we have the system instructions set, let's add some layers of **safety toolsing**. 
