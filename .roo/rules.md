# Roo Code Rules - Kimi K2 Configuration

## Provider Settings
**Provider**: OpenAI Compatible  
**Base URL**: https://api.kimi.com/coding/v1  
**Model**: kimi-for-coding  
**Max Output**: 16384  
**Reasoning**: Medium

## Critical Rules
1. **ALWAYS** enable Legacy Format in Roo Code Advanced settings
2. **NEVER** exceed 18 steps without decomposition
3. **ALWAYS** load CONTEXT.md first (top bias exploitation)
4. **MONITOR** reasoning token ratio (alert if >40%)
5. **USE** `/cost` command every 5-7 prompts

## Context Management Strategy
**Top Bias Exploitation (First 25%):**
- Load `CONTEXT.md` first for architectural guidance
- Load critical configuration files early
- Place high-priority instructions at session start

**Tail Bias Exploitation (Last 25%):**
- Keep current error logs at context end
- Recent conversation history
- Immediate task reminders

**Context Window Limits:**
- Do not read files > 500 lines entirely
- Use grep/sed for specific ranges
- Keep routine tasks under 8k tokens
- Expand to full 200k+ only for global reviews

## Reasoning Toggle Protocol
**Medium Reasoning (Default):**
- Complex refactoring tasks
- Architecture design decisions
- Multi-file coordination
- Performance optimization

**Low Reasoning (Turbo):**
- Test writing
- Code formatting
- Documentation generation
- Simple bug fixes

## Financial Safety Rails
**Daily Budget:** $5.00/day hard limit on API key  
**Balance Alert:** $10.00 threshold for low balance warnings  
**Cost Monitoring:** Track per-task cost, alert if exceeds $0.75  
**Target Rate:** $3.00 per 1M tokens

## Mode Engineering
**Architect Mode (Kimi K2 Thinking):**
- Complex reasoning, planning, system design
- High context, read-only operations
- Use for: Analyzing PRDs, designing schemas, planning refactors

**Code Mode (Kimi K2 Turbo):**
- Fast implementation, syntax, execution
- High context, read/write operations
- Use for: Writing code, executing tests, fixing lint errors

**Orchestrator Mode (Kimi K2 Thinking):**
- Task management, delegation, workflow coordination
- Low context, meta-only operations
- Use for: Managing multi-step workflows, maintaining state

## Prompt Caching Strategy
**Cache Hit Rate Target:** >75% for optimal cost reduction

**Optimization Techniques:**
- **Stable System Prompts:** Avoid editing .clinerules during active sessions
- **Linear History:** Use Roo Code's natural linear history for caching
- **Context Loading Order:** Load large static files first to maximize cache hits
- **Cache Invalidation:** Avoid "Delete Message" feature which invalidates cache

**Cost Impact:**
- Input (Cache Miss): $0.60 / 1M tokens
- Input (Cache Hit): $0.15 / 1M tokens (75% discount)
- Output: $2.50 / 1M tokens

## Error Handling & Loop Prevention
**Stop Conditions:**
- If tool output contradicts internal assumption: STOP and ask user
- Do not retry same command more than once
- If repeating sequence > 3 times: STOP and request help

**Error Analysis:**
- Analyze error messages in detail
- Do not blindly retry failed commands
- Provide clear error context to user

## Hybrid Model Strategy
**Recommended Model Mix:**
- **Kimi K2 Thinking:** Architecture, orchestration, complex debugging (reasoning tasks)
- **Kimi K2 Turbo:** Code implementation, syntax fixes, test writing (speed tasks)
- **DeepSeek V3:** Alternative for pure coding when available

**TCO Optimization:**
- Use Kimi's reasoning for planning
- Use faster models for execution
- Typical cost reduction: 50-75%

## Performance Targets
**Success Rate:** >95% within 18 sequential tool calls  
**Failure Threshold:** 28+ steps (degrade rapidly)  
**Task Completion:** 92% single-attempt benchmark  
**Token Efficiency:** 25% reduction vs baseline  
**Cost per Task:** $0.50-$0.75 typical range