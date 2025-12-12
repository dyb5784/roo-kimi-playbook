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

## Context Strategy
- Load critical files FIRST (first 25% of context)
- Keep error logs LAST (last 25% of context)
- Remove redundant information regularly
- Use `/clear` before complex tasks

## Reasoning Toggle
- **Medium** (default): Complex logic, architecture, refactoring
- **Low** (Turbo): Tests, docs, formatting, simple fixes

## Cost Governance
- Target: $3.00 per 1M tokens
- Alert: Reasoning tokens >40% of total
- Reset: Every 18 steps or when cost exceeds budget