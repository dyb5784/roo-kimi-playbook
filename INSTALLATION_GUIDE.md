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

### For ACP Simulation Projects

Copy these files to your project root:

```bash
# From this playbook package:
cp kimi-k2-playbook-v4.1.0/docs/PLAYBOOK.md /path/to/your/project/
cp kimi-k2-playbook-v4.1.0/ZENODO_DESCRIPTION_v4.1.0.md /path/to/your/project/

# Optional: Copy for reference
cp kimi-k2-playbook-v4.1.0/ZENODO_METADATA_GUIDE_v4.1.0.md /path/to/your/project/
```

### For Other Projects

Use the configuration template:

1. Create `.roo/` directory in your project
2. Copy playbook: `cp kimi-k2-playbook-v4.1.0/docs/PLAYBOOK.md .roo/`
3. Reference it in your project documentation

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

## 🔧 Troubleshooting Installation

### "Invalid API Key" Error
**Solution**: 
1. Regenerate key from Kimi dashboard
2. Ensure no extra spaces
3. Check key starts with `sk-kimi-`

### "Connection Failed" Error
**Solution**:
1. Verify Base URL: `https://api.kimi.com/coding/v1`
2. Check internet connection
3. Ensure Legacy Format is **enabled**

### "Model Not Found" Error
**Solution**:
1. Confirm Model ID is exactly `kimi-for-coding`
2. Test with curl command (see Step 3 above)
3. Check Kimi dashboard for model availability

### High Token Usage Immediately
**Solution**:
1. Use `/clear` to reset context
2. Load only essential files first
3. Check for redundant information in context

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

---

## 📞 Support

If installation issues persist:

1. **Check**: `ZENODO_METADATA_GUIDE_v4.1.0.md` - Troubleshooting section
2. **Verify**: All steps in this guide completed
3. **Test**: API connection with curl command
4. **Review**: Roo Code logs for specific error messages

---

**Installation Complete!** You are now ready to use Kimi K2 with Roo Code for token-efficient AI engineering.