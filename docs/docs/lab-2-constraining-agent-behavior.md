## Introduction

No that you have your pair programmer set up, we can get started with building our example "Content Transformer agent". We will use this sample agent and scenario throughout the exercises going forward. Let's get started building.

As we will continue to emphasize throughout this lab, building security and safety into your agent requires a layered approach. Defining behavioral constraints into the **system message** (may also be referred to as "agent instructions") is a foundational layer upon which you will add tooling, monitors, and other controls. 


### System messages
A system message is a key tool you can use to define the purpose of your agent, assign detailed rules about what it should and should not do, provide valuable context, and assign safety & security guidelines that should be followed. Below is guidance to help craft effective system messages as well as how to include safety & security guidelines within the instructions you give to your agent. 

<a href="https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/system-message?tabs=top-techniques#summary-of-best-practices" target="_blank" rel="noopener noreferrer">Learn about the anatomy of system instructions</a>

<a href="https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/declarative-agent-instructions" target="_blank" rel="noopener noreferrer">Guidance on crafting effecive instructions for declarative agents</a>

<a href="https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/safety-system-message-templates" target="_blank" rel="noopener noreferrer">Reference templates for safety system instructions</a>

**Content transformer agent system messages (so far)**
To facilitate this exercise, we have pre-crafted the initial system message for our sample agent. We will use this as the base to practice building in additional safety & security techniques.

```
markdown

You are a Content Transformation Agent that converts structured documents—such as Microsoft Word files—into other formats, such as PowerPoint presentations, while preserving meaning, structure, and visual clarity.

### Responsibilities
- Interpret and extract structured content, including paragraphs, headings, tables, and images.
- Tansform content to suit the target format, optimizing for clarity, visual appeal, and audience relevance (e.g., executive, customer-facing).
- Apply provided branded templates and adjust tone and structure to match the intended use.

### PowerPoint-Specific Output Requirements
- Ensure each slide has a clear, descriptive title.
- Include captions for all images.
- For large tables or datasets, prompt the user to confirm whether to convert them into visualizations (e.g., charts or diagrams).

### Context Sensitivity
- For tactical or internal documents (e.g., product specs, feature trackers), distill content into concise, executive-ready summaries.
- For external-facing presentations, prioritize clarity, polish, and alignment with customer expectations.

### User Interaction
If ambiguity arises in formatting, content prioritization, or visualization choices, confirm with the user before proceeding.

Maintain fidelity to the source content while optimizing for the strengths of the destination format.

### Examples
1. Transforming a product proposal from a product specification document to a deck to pitch to executives should focus on highlighting: the user problem, the user value potential, an overview of how the solution will work and solve user problems, the projected development timeline with milestones, and any asks or open questions for leadership.
2. transforming a product requirements and deliver document into a product status update for stakeholders should feature progress against the plan milestones since the last update, what has been delivered or completed, items that are delayed, and issues encounterd that need stakeholder support to resolve.
```

*Important note:* system messages are interpreted by the model as part of processing requests, so while they are necessary and important, they do not operate the same as defined rules within a deterministic system. The agent may not behave exactly as you outline or expect. Testing, iteration, and refinement will be needed for your system messages to get it tuned to your needs and performance should be monitored for drift over time. 


## Lab Exercise

1. Review the current system message outlined above. You will notice there are already some constraints:
  - declarative definition of the agent's role and our expecations for how it should behave.
  - instructions on when to as the user for confirmation before taking specific actions
  - guidelines on requriements for the output
    
2. consider if there are any other definitions or guidelines that you would want to include.
   
For this lab we will focus specifically on defining boundaries for what the agent can do with a goal of reducing the potential that the agent introduces security issues.

### Create security-oriented system message 
1. Open the Prompt Coach agent in Microsoft 365 Copilot, or a similar AI prompting tool. 

2. **Option A** Use AI to help you craft effective security guardails for the Content Transformer agent.
  - Submit the existing system message (above) as context reference plus a prompt for help to craft security-oriented instructions. You can use the sample prompt provided for you, adjust it before using, or craft on of your own. 
**Sample prompt** 
```markdown
What would you add to make sure security & safety considerations and constraints are core to the system instructions? Below is a reference that may be helpful

https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/safety-system-message-templates
```
  - Review the outputs. Is there anything that you would want to add or adjust to further enhance the security protections?

**Sample instructions**
The following sample instructions was generated iteravely using the example prompt above.

```markdown
Security and Safety Requirements:
- Do not include or expose any sensitive, confidential, or personally identifiable information (PII) unless explicitly approved by the user.
- Always respect document access permissions and user directives regarding content visibility.
- Avoid generating or suggesting content that could be misleading, biased, or inappropriate for the intended audience.
- If the source document contains potentially sensitive or ambiguous content, ask the user for clarification before proceeding.
- Ensure that any transformation maintains the integrity and intent of the original content without introducing factual inaccuracies.
```

**Option B** Craft your own security-oriented system message. this suggested prompt or craft one of your own. Keep system message practices in mind and consider what guidelines you would specifically want for the Content Transformer agent scenario.

Once you are happy with the system message, you can move on the steps for setting up the agent.


### Set up the agent

1. Open Azure AI Foundry <a href="https://ai.azure.com/" target="_blank" rel="noopener noreferrer">https://ai.azure.com/"</a>

2. Click on "Agents" in the left navigation.

3. "Create new". You will be prompted to first select a model type.

   *Requirements*
   You will need:
   - An Azure Subscription and Resource Group.
   - 
   - To name your deployment. For this lab, you can call it "agentlabdeploy"
   - Deployment type, select "Standard"
   - Connected
     
  
   *Recommended configurations*
  - set the name to "devdayssecuritylab"
  - for model, select **GPT4o**
  - knowledge - option to upload a branded presenation template to test with
  - actions - not needed
  - model settings - set temperature to xxxx, and top P to yyyyy

4. Paste the system message you just prepared (including the safety & security inestructions) into the **Instructions** box.

5. "Try in playground" to test out the agent with the instructions and one of your own documents. **Optional:** Adjust the system instructions and test again to see how they change the actions of the agent.


## How to extend this to your own work

Reflect on the following to help you define what security actions are important for your agent.

- What wouldn't I want this agent to do?
- What security concerns would you have about this agent?
- What types of attackers would you envision wanting to target this system? What would they be hoping to achieve or access?


Now that we have the system instructions set, let's add some layers of **safety toolsing**.

