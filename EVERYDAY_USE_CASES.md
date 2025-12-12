# Everyday Use Cases - Kimi K2 & Roo Code v4.1.0

**Practical examples for common development tasks**

---

## 🚀 Quick Reference

| Task Type | Reasoning | Expected Steps | Token Budget |
|-----------|-----------|----------------|--------------|
| **Bug Fix** | Medium | 5-10 | 5K-10K |
| **Test Writing** | Low (Turbo) | 3-8 | 3K-8K |
| **Refactoring** | Medium | 8-15 | 10K-20K |
| **Code Review** | Medium | 5-12 | 8K-15K |
| **Documentation** | Low (Turbo) | 3-6 | 4K-8K |
| **Architecture** | Medium | 10-18 | 15K-30K |

---

## 🐛 Use Case 1: Bug Fix

### Scenario
User reports: "Button click doesn't update the counter"

### Session Flow

**Step 1: Load Context (Top Bias)**
```bash
/clear
# Load relevant files FIRST
src/components/Counter.tsx
src/store/counterSlice.ts
src/App.tsx

# Current error from logs
# "TypeError: Cannot read property 'count' of undefined"
```

**Step 2: Triage**
```bash
# Ask: "Analyze the counter update flow and identify the bug"
# Expected: 5-8 steps, ~6K tokens
```

**Step 3: Implement Fix**
```bash
# Ask: "Fix the undefined property error"
# Expected: 3-5 steps, ~4K tokens
```

**Step 4: Verify**
```bash
# Ask: "Write a test to verify the fix"
# Toggle to Low reasoning for test writing
# Expected: 3-4 steps, ~3K tokens
```

**Total**: ~13K tokens, 11-17 steps ✅ (within 18-step limit)

---

## 🧪 Use Case 2: Test Writing

### Scenario
Need to add unit tests for new API endpoint

### Session Flow

**Step 1: Load Context**
```bash
/clear
src/api/userEndpoints.ts
src/types/User.ts
```

**Step 2: Turbo Mode for Tests**
```bash
# Toggle Reasoning to Low (Turbo)
# Ask: "Generate comprehensive tests for userEndpoints.ts"
# Expected: 5-7 steps, ~5K tokens
```

**Step 3: Review and Refine**
```bash
# Ask: "Check test coverage and add edge cases"
# Expected: 2-3 steps, ~2K tokens
```

**Total**: ~7K tokens, 7-10 steps ✅ (very efficient)

---

## ♻️ Use Case 3: Refactoring

### Scenario
Extract reusable component from monolithic file

### Session Flow

**Step 1: Load and Analyze**
```bash
/clear
# Load large file first (top bias)
src/components/Dashboard.tsx (500+ lines)

# Ask: "Identify the best extraction candidates"
# Expected: 6-8 steps, ~8K tokens
```

**Step 2: Plan Extraction**
```bash
# Ask: "Create extraction plan for UserProfile section"
# Expected: 4-6 steps, ~6K tokens
```

**Step 3: Execute Extraction**
```bash
# Ask: "Extract UserProfile into separate component"
# Expected: 8-12 steps, ~12K tokens
```

**Step 4: Update Imports**
```bash
# Ask: "Update all imports in Dashboard.tsx"
# Toggle to Low reasoning for this rote task
# Expected: 2-3 steps, ~2K tokens
```

**Total**: ~28K tokens, 20-29 steps ⚠️ (exceeds 18-step limit)

**Solution**: Decompose into sub-tasks:
- Sub-task 1: Analysis (8 steps)
- Sub-task 2: Extraction (12 steps) 
- Sub-task 3: Import updates (3 steps)

---

## 👀 Use Case 4: Code Review

### Scenario
Review pull request with 5 files changed

### Session Flow

**Step 1: Load Files Strategically**
```bash
/clear
# Load most critical files first
src/core/auth.ts
src/middleware/protection.ts

# Then supporting files
src/routes/api.ts
src/utils/validation.ts
src/tests/auth.test.ts
```

**Step 2: Review Architecture**
```bash
# Ask: "Review authentication flow for security issues"
# Expected: 6-10 steps, ~10K tokens
```

**Step 3: Review Implementation**
```bash
# Ask: "Check for best practices and suggest improvements"
# Expected: 4-7 steps, ~7K tokens
```

**Step 4: Summarize Findings**
```bash
# Ask: "Create code review summary with action items"
# Expected: 2-3 steps, ~3K tokens
```

**Total**: ~20K tokens, 12-20 steps ✅ (manageable with monitoring)

---

## 📝 Use Case 5: Documentation

### Scenario
Document new API endpoint

### Session Flow

**Step 1: Load Context**
```bash
/clear
src/routes/newEndpoint.ts
src/types/ApiResponses.ts
```

**Step 2: Turbo Mode for Docs**
```bash
# Toggle Reasoning to Low
# Ask: "Generate API documentation for newEndpoint.ts"
# Expected: 4-6 steps, ~5K tokens
```

**Step 3: Format and Review**
```bash
# Ask: "Format documentation and add examples"
# Expected: 2-3 steps, ~2K tokens
```

**Total**: ~7K tokens, 6-9 steps ✅ (very efficient)

---

## 🏗️ Use Case 6: Architecture Design

### Scenario
Design new microservice for user notifications

### Session Flow

**Step 1: Load Context (Top Bias)**
```bash
/clear
# Architecture and existing patterns first
docs/ARCHITECTURE.md
src/services/README.md

# Current related services
src/services/emailService.ts
src/services/pushService.ts
```

**Step 2: Requirements Gathering**
```bash
# Ask: "Based on existing patterns, design notification microservice"
# Expected: 8-12 steps, ~15K tokens
```

**Step 3: Design Review**
```bash
# Ask: "Review design for scalability and maintainability"
# Expected: 5-8 steps, ~10K tokens
```

**Step 4: Implementation Plan**
```bash
# Ask: "Create step-by-step implementation plan"
# Expected: 4-6 steps, ~8K tokens
```

**Total**: ~33K tokens, 17-26 steps ⚠️ (approaching limit)

**Solution**: Stop at 18 steps, document progress, continue in new session

---

## 💡 Best Practices for Everyday Use

### 1. **Start Every Session with `/clear`**
```bash
/clear
# Then load only what you need
```

### 2. **Load Files Strategically**
```bash
# GOOD: Load critical files first
src/core/auth.ts
src/middleware/protection.ts

# AVOID: Loading everything at once
src/**/*  # Too much context, wastes tokens
```

### 3. **Monitor Every 5-7 Prompts**
```bash
/cost
# Check: Total tokens, reasoning ratio, budget remaining
```

### 4. **Toggle Reasoning Appropriately**
```bash
# Complex logic: Medium (default)
# Test writing: Low (Turbo)
# Documentation: Low (Turbo)
# Bug fixes: Medium
# Code review: Medium
```

### 5. **Reset Before Complex Tasks**
```bash
# Before starting something big:
/clear
# Load fresh context
# This prevents context degradation
```

### 6. **Decompose Large Tasks**
```bash
# Instead of: "Build entire feature"
# Do: "Design API schema" (sub-task 1)
# Then: "Implement endpoint" (sub-task 2)
# Then: "Add tests" (sub-task 3)
```

---

## 📊 Cost Tracking Examples

### Daily Development (4 hours)
- **Bug fixes**: 3 sessions × 10K = 30K tokens
- **Test writing**: 2 sessions × 7K = 14K tokens
- **Refactoring**: 1 session × 15K = 15K tokens
- **Total**: ~59K tokens = $0.18

### Weekly Sprint (20 hours)
- **Daily work**: 59K × 5 days = 295K tokens
- **Code reviews**: 5 × 12K = 60K tokens
- **Architecture**: 2 × 20K = 40K tokens
- **Total**: ~395K tokens = $1.19

### Monthly (80 hours)
- **Weekly average**: 395K × 4 weeks = 1.58M tokens
- **Buffer for complex tasks**: +0.5M tokens
- **Total**: ~2.08M tokens = $6.24

**Budget target**: $5-10 per month for heavy usage

---

## 🎯 Session Templates

### Template 1: Quick Bug Fix
```bash
/clear
# Load: Affected files
# Ask: "Fix bug in [specific location]"
# Test: "Verify fix works"
# Cost: ~10K tokens
```

### Template 2: Feature Implementation
```bash
/clear
# Load: Related files, architecture docs
# Ask: "Design [feature] following existing patterns"
# Steps: 1-2 (stop at 18, continue in new session)
# Cost: ~15K tokens per session
```

### Template 3: Code Review
```bash
/clear
# Load: Changed files (most important first)
# Ask: "Review for security and best practices"
# Summarize: "Create review summary"
# Cost: ~12K tokens
```

---

## ⚡ Efficiency Tips

### Maximize Token Efficiency
1. **Use `/clear` frequently** - Every 5-7 prompts or 18 steps
2. **Load files strategically** - Critical files first, then supporting
3. **Toggle Reasoning** - Low for rote, Medium for complex
4. **Monitor with `/cost`** - Track usage patterns
5. **Decompose large tasks** - Stay under 18-step limit

### Minimize Costs
1. **Batch similar tasks** - Group test writing, documentation
2. **Use Turbo mode** - Low reasoning for simple operations
3. **Optimize context** - Remove redundant information
4. **Reuse patterns** - Don't reinvent solutions
5. **Plan before coding** - Reduces rework

---

## 📈 Success Metrics

Track these for your projects:

| Metric | Target | How to Measure |
|--------|--------|----------------|
| **Task Completion** | 92% | Successful sessions / Total sessions |
| **Token Efficiency** | 25% reduction | Compare to v4.0.0 baseline |
| **Cost per Task** | <$0.50 | Track with `/cost` command |
| **Session Length** | <18 steps | Count tool calls per session |
| **Reasoning Ratio** | <40% | Check `/cost` output |

---

**Version**: 4.1.0  
**Applies to**: Kimi K2 with Roo Code  
**Last Updated**: December 12, 2025