# Build-an-Agent Labs: Safety & Security Edition

A comprehensive hands-on lab series for AI builders to implement safety and security techniques into custom agents. This lab covers essential security practices, Microsoft Safety System tools, and real-world testing methodologies.

## 🎯 Learning Objectives

By completing these labs, you will learn to:
- Apply Security Development Lifecycle (SDL) principles to AI agent development
- Implement effective behavior constraints and Human-in-the-Loop (HITL) patterns
- Integrate Microsoft Safety System tools (prompt shield, spotlighting, task adherence)
- Test your agents using AI red team methodologies
- Implement comprehensive logging, monitoring, and alerting systems

## 📚 Lab Structure

### Lab 1: SDL-Oriented Instructions
Learn to implement Security Development Lifecycle principles in your AI agent instructions.
- **Location**: `labs/01-sdl-instructions/`
- **Duration**: 45 minutes
- **Prerequisites**: Basic understanding of AI agents

### Lab 2: Behavior Constraints & HITL
Build effective guardrails and human oversight mechanisms.
- **Location**: `labs/02-behavior-constraints/`
- **Duration**: 60 minutes
- **Prerequisites**: Completion of Lab 1

### Lab 3: Microsoft Safety System Tools
Integrate prompt shield, spotlighting, and task adherence tools.
- **Location**: `labs/03-safety-system-tools/`
- **Duration**: 75 minutes
- **Prerequisites**: Azure account with Cognitive Services access

### Lab 4: Red Team Testing
Test your agent's security using adversarial techniques.
- **Location**: `labs/04-red-team-testing/`
- **Duration**: 90 minutes
- **Prerequisites**: Completion of Labs 1-3

### Lab 5: Logging, Monitoring & Alerting
Implement comprehensive observability for your agents.
- **Location**: `labs/05-logging-monitoring/`
- **Duration**: 60 minutes
- **Prerequisites**: Basic knowledge of logging systems

## 🚀 Quick Start

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Harmonym/build-a-agent-labs.git
   cd build-a-agent-labs
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**:
   ```bash
   cp .env.example .env
   # Edit .env with your API keys and configuration
   ```

4. **Start with Lab 1**:
   ```bash
   cd labs/01-sdl-instructions
   python setup.py
   ```

## 📋 Prerequisites

- Python 3.8 or higher
- Basic understanding of AI/ML concepts
- Azure account (for Microsoft Safety System tools)
- OpenAI API key (for examples)

## 🔧 Tools & Technologies

- **AI Frameworks**: LangChain, Semantic Kernel
- **Safety Tools**: Microsoft Prompt Shield, Azure Content Safety
- **Monitoring**: Azure Monitor, Application Insights
- **Testing**: Custom red team scripts, OWASP AI security guidelines

## 📖 Additional Resources

- [Microsoft Responsible AI](https://www.microsoft.com/en-us/ai/responsible-ai)
- [OWASP AI Security](https://owasp.org/www-project-ai-security-and-privacy-guide/)
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)

## 🤝 Contributing

Please see our [contributing guidelines](CONTRIBUTING.md) for information on how to contribute to this project.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
