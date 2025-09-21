## Introduction to Security Development Lifecycle (SDL) guidance for your pair programmer

### Using a pair-programmer or AI assistance for your development work

Using AI to help accelorate your development process with simple support like proving code completion recommendations or or generating large code blocks based upon your prompted goal. These tools are powerful, but they too carry all of the risks inherent in generativeAI systems. You should always review and test the code generated for accuracy, effectiveness, security, and safety before deploying it into production.

You can also provide instructions to the agent to follow security development lifecycle requirements and best practices.

<br>

### Security Development Lifecycle (SDL) agent instructions

If using <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank" rel="noopener noreferrer">GitHub Copilot</a>, you can apply these instuctions at the <a href="https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-personal-instructions" target="_blank" rel="noopener noreferrer">user level</a> or include them as part of <a href="https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions?tool=vscode" target="_blank" rel="noopener noreferrer">repository instructions</a>.

Here is an example of agent SDL instructions for reference, you should tailor it to meet your organizations requirements and refine over time if you find gaps in adherence to requirements in the generated code.

<br>

## Lab Exercise

In this lab, you will add these instructions at the Git repo level.

### Option A: AI assisted instructions authoring

1. Open M365 Copilot Prompt Coach or another similar prompting assistant.

2. Craft a prompt to have AI help to generate the SDL-based system instructions. These tools can help you refine and improve your prompting and improve the quaity of the ouputs you get. You can use the sample prompt below, modify it to better match your organization's security requirements, or write one from scratch. *Note:* Any time you are using AI, be sure to review it for accuracy and alignment with your intent.

**Example prompt**

```
Text

I am looking to create standardized, SDL-based, instructions that would be added as part of instructions for a my pair-programming agent. The goal is to instruct the programming agent to only generate code that meets key security requirements.  This is the SDL reference that it should be based upon. <a href="https://www.microsoft.com/en-us/securityengineering/sdl/practices" target="_blank" rel="noopener noreferrer">https://www.microsoft.com/en-us/securityengineering/sdl/practices</a> It should cover the full lifecycle, but only include the practices that could be applied by a code generation AI agent (you can ignore process or standards definition practices). The output should be in markdown and delivered as embedded inline so it is easy for me copy and paste into the agent configuration.
```
3. Review the draft instructions to make sure they align with what you want GitHub Copilot to follow.
<br>

### Option B: Use pre-drafted instructions
1. We have drafted sample SDL-oriented instructions that you can review, modify, and use.

**Sample instructions** 

```markdown

You are a coding assistant AI that **follows the company’s Security Development Lifecycle (SDL) guidelines** for secure coding. **Always apply the following practices when generating source code:**
- **Use approved frameworks & libraries:** Leverage well-vetted, company-approved languages, frameworks, and APIs for security functionality. *Do not write custom crypto or auth logic if a standard solution exists*.
- **Validate all inputs:** Treat all inputs as untrusted. Implement strict input validation and sanitization (allow-list acceptable values or formats). Reject or sanitize data that is unexpected or potentially malicious.
- **Use secure defaults:** Enable security features by default (e.g. strong encryption protocols, secure cookies, parameterized queries). Disable or avoid legacy insecure options.
- **Handle secrets safely:** **Never** reveal or hard-code passwords, API keys, or secrets. Load secrets from secure storage and keep them out of code and logs.
- **Enforce least privilege:** When suggesting code for configuration or identity, use the minimal required privileges (e.g. least privileged roles, minimal scopes for API tokens).
- **Use strong cryptography:** Only use industry-standard encryption algorithms and protocols (e.g. TLS 1.2+, AES-256). *Do not invent new encryption.* Utilize trusted libraries for crypto routines.
- **Avoid known vulnerabilities:** Write code that is not susceptible to common flaws (SQL injection, XSS, buffer overflow, etc.). For database queries, use prepared statements or ORM. For HTML output, escape or encode user data.
- **Comprehensive error handling:** Handle errors and exceptions securely. Don’t expose sensitive information in error messages or stack traces. Fail safe (deny access by default if uncertainty).
- **Logging and auditing:** Use secure logging practices. Avoid logging sensitive data (passwords, personal info). Include relevant security events (e.g. authentication failures) in logs for auditing, following privacy guidelines.
- **Compatible with security testing:** Write code that will pass security static analysis and penetration tests (no high-severity warnings). Address any fixable warnings in the code you generate.
 
Always prioritize code safety and compliance with these guidelines **even if not explicitly requested by the user**. Aim to produce solutions that not only meet the user’s functional requirements but also uphold strong security standards by design.
 https://www.microsoft.com/en-us/securityengineering/sdl/
```

<br>

### Add the instructions to your GitHub Copilot
1. Make sure you have the GitHub Copilot extension installed
2. Open your target repository. *Recommendation:" create a new repository for this lab to allow for expermimentation without impacting any of your other work.
3. In the root of your repository, create a file named `.github/agent-instructions.md'
4. Add the reference instructions provided above or the ones you created into the file. *Optional:* you should review and customize them as appropriate.

### Test the instructions

It is best practice to always test changes or controls you introduce to the system. The custom instructions will be availabe for GitHub Copilot to use as soon as you save the file.

1. Start a new coding project and ask GitHub Copilot to generate sample code snippets.

![GitHub instructions reference](media/github-custom-isntructions-vscode.webp)
 
3. Review the code it generated to validate that it followed the SDL requirements you outlined for it.

   
<br>

## How to extend this to your own work

Reflect on the following to help you define what security actions are important for your agent.

- What are my organization's SDL practices?
- What, if any, requirements does my organization have for AI-powered development and security?
- *Optional* If you see code snippets being developed that do not meet the requirements, further refine the instructions. Changes may happen over time, so it is important to always validate the outputs of pair programmers.
- Reference this guidance on writing effective <a href="copilot-instructions.md" target="_blank" rel="noopener noreferrer">repository custom instructions</a>


With that set up, we will start **building** our agent!



