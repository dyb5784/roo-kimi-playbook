# Kimi K2 & Roo Code Playbook - Installation Guide

**Version 4.1.0** - Complete setup instructions for Kimi K2 integration with Roo Code

---

## 📋 Prerequisites

Before installing the Kimi K2 playbook, ensure you have:

1. **Roo Code extension** installed in VS Code
2. **Kimi API access** (Membership Dashboard: https://platform.kimi.com/)
3. **API Key** from Kimi (starts with `sk-kimi-...`)
4. This playbook package extracted or cloned

---

## 🔧 Configuration Files to Modify

You need to modify **2 main files** in your Roo Code configuration:

### 1. Roo Code Settings (`settings.json`)

**Location**: VS Code → Settings → Extensions → Roo Code → Settings JSON

### 2. Roo Code Provider Configuration

**Location**: Roo Code chat → Click gear icon → "Edit Provider Settings"

---

## 🚀 Step-by-Step Installation

### Step 1: Configure Roo Code Provider Settings

1. Open Roo Code in VS Code
2. Click the gear icon (⚙️) in the Roo Code chat window
3. Select "Edit Provider Settings"
4. Fill in these exact values:

| Setting | Value |
|---------|-------|
| **Provider** | `OpenAI Compatible` |
| **Base URL** | `https://api.kimi.com/coding/v1` |
| **API Key** | `sk-kimi-...` (your key from Kimi dashboard) |
| **Model ID** | `kimi-for-coding` |
| **Max Output** | `16384` |
| **Reasoning** | `Medium` |

5. Click "Save"

### Step 2: Enable Legacy Format (Critical)

1. In Roo Code, click the gear icon (⚙️)
2. Select "Advanced Settings"
3. Find "Legacy Format" toggle
4. **Enable it** (turn ON)
5. This ensures compatibility with Kimi's response format

### Step 3: Verify API Connection

Test your configuration:

```bash
# Open terminal and run:
curl -H "Authorization: Bearer sk-kimi-YOUR-KEY-HERE" \
     https://api.kimi.com/coding/v1/models

# Should return JSON with model information
```

If you get an error, check:
- API key is correct
- No extra spaces in Base URL
- Legacy format is enabled

---

## 📁 Files to Copy to Your Project

### For New Projects

Copy these files to your project root:

```bash
# Copy configuration files
cp .clinerules /path/to/your/project/
cp -r .roo /path/to/your/project/

# Copy documentation for reference
cp PLAYBOOK.md /path/to/your/project/
cp INSTALLATION_GUIDE.md /path/to/your/project/
cp EVERYDAY_USE_CASES.md /path/to/your/project/
```

### Configuration Files Explained

**`.clinerules`** - Critical AI assistant instructions:
- 18-step limit enforcement
- Context-first loading strategy
- Boomerang handoff pattern
- 95% success threshold within 18 steps
- Error loop prevention

**`.roo/rules.md`** - Roo Code specific configuration:
- Kimi K2 endpoint settings
- Token efficiency rules
- Context management strategy
- Financial safety rails ($5/day budget)
- Mode engineering (Architect/Code/Orchestrator)
- Prompt caching strategies
- Hybrid model recommendations

---

## 🔧 Optional: LiteLLM Proxy Setup (Enterprise)

For enterprise teams, routing requests through LiteLLM provides additional control:

### Why Use LiteLLM?
- Per-user/project budget tracking
- Rate limiting
- Parameter remapping (max_completion_tokens to max_tokens)
- Centralized cost monitoring

### Installation
```bash
# Install LiteLLM
pip install litellm

# Run proxy
litellm --model moonshot/kimi-k2-thinking --port 4000

# Configure Roo Code to use proxy
# Base URL: http://localhost:4000/v1
```

### Benefits
- **Cost Control:** Set daily/weekly limits per user
- **Parameter Mapping:** Fixes max_completion_tokens issues
- **Analytics:** Detailed usage reports
- **Failover:** Automatic fallback to backup models

---

## ✅ Verification Checklist

After installation, verify:

### API Connection
- [ ] Roo Code shows "Connected" status
- [ ] `/cost` command works in Roo Code chat
- [ ] Can send test message successfully

### Configuration
- [ ] Base URL is `https://api.kimi.com/coding/v1`
- [ ] Model ID is `kimi-for-coding`
- [ ] Max Output is `16384`
- [ ] Reasoning is `Medium`
- [ ] Legacy Format is **enabled**

### Token Efficiency
- [ ] Can monitor token usage with `/cost`
- [ ] Understand 18-step horizon concept
- [ ] Know how to toggle Reasoning (Medium/Low)

---

## 🎯 First Test Session

Run this test to verify everything works:

```bash
# In Roo Code chat:
/clear

# Load critical context first (exploit top bias)
# Paste your project context here

# Test basic functionality
# Ask: "What is the 18-step horizon and how do I manage it?"

# Check cost
/cost

# Expected: Should see token usage, no errors
```

---

## 📊 Expected Results After Installation

### Successful Configuration
- **Connection**: Roo Code shows green "Connected" status
- **Cost**: ~0.3¢ per 1K tokens ($3.00 per 1M)
- **Performance**: 92% task completion rate
- **Token Efficiency**: 25% reduction vs v4.0.0

### First Session Metrics
- **Session length**: Should handle 10-18 steps reliably
- **Reasoning ratio**: Should be <40% for most tasks
- **Context loading**: Top/tail bias working if files load strategically

---

## 🎓 Next Steps

1. **Read the playbook**: Review `PLAYBOOK.md` thoroughly
2. **Practice context management**: Experiment with file loading order
3. **Monitor costs**: Use `/cost` regularly to track efficiency
4. **Optimize workflows**: Apply 18-step horizon to complex tasks
5. **Consider LiteLLM**: For enterprise deployments with multiple users

---

## 📞 Support

If installation issues persist:

1. **Check**: `PLAYBOOK.md` - Troubleshooting section
2. **Verify**: All steps in this guide completed
3. **Test**: API connection with curl command
4. **Review**: Roo Code logs for specific error messages
5. **Consider**: LiteLLM proxy for complex enterprise setups

---

**Installation Complete!** You are now ready to use Kimi K2 with Roo Code for token-efficient AI engineering.

**Version**: 4.1.0  
**Last Updated**: December 12, 2025