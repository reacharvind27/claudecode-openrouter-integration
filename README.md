# ClaudeCode Openrouter Integration

Use this repo to run Claude Code completely for free using OpenRouter

## Reference Link

| # | Site | Link |
| :---: | :--- | :--- |
| 1 | Openrouter Site | https://openrouter.ai/ |
| 2 | Openrouter - Claude Documentation | https://openrouter.ai/docs/guides/guides/coding-agents/claude-code-integration |
| 3 | Openrouter Models| https://openrouter.ai/models |


## Pre-requisite Steps

### Claude Software Installation

1. Install Claude Code, use the below link to install the software

```
https://code.claude.com/docs/en/quickstart#native-install-recommended
```
2. Upgrade the claude code
   
```
npm install -g @musistudio/claude-code-router
```

3. Create the API Key
this is required and claude will ask on the first time launch

### Key things to Capture

#### Key Things

1. Openrouter API Key
   - see the step # 03 in the below table
2. Openrouter Claude Integration Keys/properties
   - see the step # 05 in the below table
3. Openrouter Model
   - see the step # 06 in the below table   

#### Steps 

| # | Step | Notes |
| :---: | :--- | :--- |
|1| Sign-up with Openrouter | Click on the Sign-up
|2| Email Verfification | you will receive email after sign=up
|3| Create OpenRouter API Key | https://openrouter.ai/settings/keys
|4| Add Credits in OpenRouter | https://openrouter.ai/settings/credits
|5| Capture the Claude Integration details from Openrouter docs | https://openrouter.ai/docs/guides/guides/coding-agents/claude-code-integration
|6| Find Model with $0 input tokens and $0 output tokens| add "free" in the textbox in https://openrouter.ai/models


## Project Creation

### Steps

1. Prepare the Claude Setting File
   - File to be placed in ""c:/user/<user-name>/.claude"
   - File Name = settings.json
   - File Content = see the text below
  
```
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://openrouter.ai/api",
    "ANTHROPIC_AUTH_TOKEN": "sk-or-v1-******",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_MODEL" : "stepfun/step-3.5-flash:free"     
  }
}
```

### Testing

1. Open the new terminal
2. launch the command "claude"
   - it prompts to select the theme : select your desired theme
   - it prompts to select the authentication mode
     -  select the 2nd option 
     -  wait for the authentication to comple
     -  exit the claude tool and the command propmpt
3. goto "c:/users/<user-name>/.claude
4. paste the settings.json file
4. Open the new terminal
5. enter claude

<img width="1331" height="576" alt="image" src="https://github.com/user-attachments/assets/4827c46c-3d52-442c-8148-cfa45379da62" />


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


