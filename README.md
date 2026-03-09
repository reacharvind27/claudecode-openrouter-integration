
# Claude Code + OpenRouter Integration

Run **Claude Code CLI** using **OpenRouter models** instead of connecting directly to Anthropic.

This setup allows developers to use **multiple AI models (Claude, GPT, Gemini, Mistral, Llama, etc.) inside Claude Code** through a single API gateway.

---

# Overview

Claude Code normally connects directly to **Anthropic’s API**.
With this integration, requests are routed through **OpenRouter**, which acts as a compatibility layer.

## Architecture

```
Claude Code CLI
      │
      ▼
OpenRouter API
      │
      ▼
Multiple AI Providers
(Claude, GPT, Gemini, Llama, Mistral, etc.)
```

OpenRouter exposes an **Anthropic-compatible API**, allowing Claude Code to work with it seamlessly.

---

# Why Use OpenRouter?

OpenRouter adds flexibility, reliability, and cost optimization compared to using a single AI provider.

## 1. Access to 100+ AI Models

OpenRouter allows you to use multiple models through a single API.

Examples:

* Claude models
* GPT models
* Gemini models
* Llama models
* Mistral models

Instead of switching APIs, you can experiment with **multiple models using the same interface**.

---

## 2. Model Failover

If one provider fails, OpenRouter can route requests to another provider automatically.

Benefits:

* Higher reliability
* Less downtime
* Better availability for production workloads

---

## 3. Cost Optimization

Different models have different pricing. OpenRouter allows you to choose the best model for the task.

Example:

| Task              | Model        |
| ----------------- | ------------ |
| Simple coding     | Gemini Flash |
| Complex reasoning | Claude Opus  |
| Large context     | Qwen         |

This helps **reduce cost while maintaining quality**.

---

## 4. Centralized Billing

Instead of managing multiple providers:

* One API key
* One billing dashboard
* One usage report

All usage is tracked in the OpenRouter dashboard.

---

## 5. Experiment with Different AI Models

Claude Code normally restricts you to Claude models.

With OpenRouter you can:

* Switch models dynamically
* Test multiple AI systems
* Build multi-model workflows

---

# Prerequisites

Before starting, make sure you have the following installed:

* Node.js (v18 or later recommended)
* Claude Code CLI
* OpenRouter account
* OpenRouter API key
* Basic terminal knowledge

---

# Step-by-Step Setup Guide

Follow these steps carefully.

---

# Step 1 — Install Claude Code

Install Claude Code globally.

```bash
npm install -g @anthropic-ai/claude-code
```

Alternative installation method (Mac / Linux):

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Windows PowerShell:

```powershell
irm https://claude.ai/install.ps1 | iex
```

Verify installation:

```bash
claude --version
```

---

# Step 2 — Create an OpenRouter Account

1. Go to

```
https://openrouter.ai
```

2. Sign up for an account.

3. Navigate to the dashboard.

4. Generate a **new API key**. Save this key securely.
5. Add Openrouter credits for $10.
---

# Step 3 — Configure Environment Variables

Claude Code must be configured to use OpenRouter instead of Anthropic.

Add the following variables to your shell configuration file.

Example files:

```
~/.bashrc
~/.zshrc
~/.profile
```

Add the following:

```bash
export OPENROUTER_API_KEY="your-api-key"

export ANTHROPIC_BASE_URL="https://openrouter.ai/api"

export ANTHROPIC_AUTH_TOKEN="$OPENROUTER_API_KEY"

export ANTHROPIC_API_KEY=""
```

Important:

`ANTHROPIC_API_KEY` must be set to an **empty string** so Claude Code does not attempt to authenticate directly with Anthropic.

Reload the shell:

```bash
source ~/.bashrc
```

or

```bash
source ~/.zshrc
```

---

# Step 4 — Start Claude Code

Run the CLI:

```bash
claude
```

If everything is configured correctly, Claude Code will now route requests through OpenRouter.

---

# Step 5 — Verify the Setup

Inside Claude Code run:

```
/status
```

You should see information about:

* Active API endpoint
* Selected model
* Provider configuration

If OpenRouter is configured correctly, it will appear in the endpoint.

---

# Optional — Choose a Specific Model

You can configure the default model.

Example:

```bash
export ANTHROPIC_MODEL="google/gemini-2.5-flash"
```

Examples of models available through OpenRouter:

```
anthropic/claude-3.5-sonnet
google/gemini-2.5-flash
meta-llama/llama-3.1-405b
mistralai/mixtral-8x7b
```

---

# Example Developer Workflow

Start Claude Code:

```bash
claude
```

Example prompts you can run:

```
Generate a Spring Boot REST API
```

```
Refactor this React component
```

```
Write unit tests for this Java service
```

Flow of execution:

```
Claude Code
   ↓
OpenRouter API
   ↓
Selected AI Model
```

---

# Troubleshooting

## Issue: Authentication Error

Check that the environment variable is correctly set:

```
ANTHROPIC_AUTH_TOKEN
```

It must contain your **OpenRouter API key**.

---

## Issue: Claude Code still calling Anthropic

Make sure the following variable exists:

```
ANTHROPIC_API_KEY=""
```

If it contains a value, Claude Code will default to Anthropic.

---

## Issue: Model Not Found

Verify available models here:

```
https://openrouter.ai/models
```

---

# Security and Privacy Considerations

When using third-party API gateways, you should always review:

* API request logging policies
* Data retention settings
* Security configurations

Avoid sending:

* Sensitive credentials
* Proprietary source code
* Confidential production data

unless you fully trust the service.

---

# Disclaimer

⚠️ **Use at Your Own Risk**

This repository provides an **unofficial integration** between Claude Code and OpenRouter.

It is **not affiliated with or endorsed by**:

* Anthropic
* Claude Code
* OpenRouter

Potential risks include:

* API compatibility changes
* Unexpected billing charges
* Rate limits
* Security risks if environment variables are misconfigured

Before using this setup:

* Review the code
* Monitor API usage
* Avoid using sensitive production data

The maintainers of this repository **are not responsible for any misuse, data loss, or financial costs** resulting from the use of this integration.

---


# Summary

Using OpenRouter with Claude Code provides:

* Access to multiple AI models
* Better reliability through failover
* Cost optimization
* Centralized API management
* Flexibility for experimentation

This integration is useful for developers who want **more control and flexibility in AI-assisted development workflows**.


# Reference Link

| # | Site | Link |
| :---: | :--- | :--- |
| 1 | Openrouter Site | https://openrouter.ai/ |
| 2 | Openrouter - Claude Documentation | https://openrouter.ai/docs/guides/guides/coding-agents/claude-code-integration |
| 3 | Openrouter Models| https://openrouter.ai/models |


## Appendix


1. Verify Environment Variables (Most Important)

echo $env:ANTHROPIC_BASE_URL
echo $env:ANTHROPIC_API_KEY
echo $env:ANTHROPIC_MODEL

2. Set Variables Again (Correct Way)
$env:ANTHROPIC_BASE_URL="https://openrouter.ai/api/v1"
$env:ANTHROPIC_API_KEY="sk-or-v1-*****"
$env:ANTHROPIC_MODEL="openrouter/free"


3. Clear Claude Login Cache

C:\Users\<username>\.claude

4. Confirm Claude Version
claude --version
npm install -g @anthropic-ai/claude-code@latest


5. Test If API Key Works (Important)

curl https://openrouter.ai/api/v1/models -H "Authorization: Bearer sk-or-v1-***************"


