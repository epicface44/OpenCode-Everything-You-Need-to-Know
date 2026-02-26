# Migration Guide for Experienced Developers

> **Switching from Claude Code, Cursor, or GitHub Copilot to OpenCode**

## 🎯 Why Migrate to OpenCode?

If you're already using AI coding tools, OpenCode offers significant advantages:

| Advantage | OpenCode | Other Tools |
|-----------|----------|-------------|
| **Model Freedom** | 75+ providers | Limited selection |
| **Pricing** | Pay-as-you-go | Monthly subscriptions |
| **Customization** | Unlimited skills/agents | Limited plugins |
| **Workflow** | Terminal-native | Desktop/IDE-bound |
| **Open Source** | Full control | Proprietary |

### Quick Comparison Table

| Feature | OpenCode | Claude Code | Cursor | GitHub Copilot |
|---------|----------|-------------|--------|----------------|
| **Primary Interface** | Terminal TUI | Desktop app | Desktop app | IDE plugin |
| **Model Selection** | 75+ providers | Claude only | Limited | GitHub models |
| **Pricing Model** | Pay-per-token | $20/month | $20/month | $10/month |
| **File Context** | Entire project | Current file | Project | Current file |
| **Customization** | Skills, agents, MCP | Limited | Limited | Very limited |
| **Team Features** | Workspaces, SSO | Basic | Basic | Organization |

---

## 🔄 Migration from Claude Code

### What You'll Recognize
- **AI-assisted coding** in your development environment
- **Conversation history** and context awareness
- **File references** and analysis capabilities
- **Multi-step task execution**

### What's Different
1. **Model Flexibility**: Use any AI model, not just Claude
2. **Pricing**: Pay only for what you use vs $20/month
3. **Interface**: Terminal-based vs desktop application
4. **Extensibility**: Create custom skills and agents

### Step-by-Step Migration

#### Week 1: Foundation
```bash
# 1. Install OpenCode
curl -fsSL https://opencode.ai/install | bash

# 2. Set up Zen (includes Claude models)
opencode
/connect
# Select "opencode" and get your API key

# 3. Try familiar workflows
[Plan] How would you implement this feature?
[Build] Implement it as planned
```

#### Week 2: Advanced Features
```bash
# 1. Create Claude-specific agent
# ~/.config/opencode/agents/claude-style.md
name: Claude-Style Coder
model: claude-sonnet-4.6
temperature: 0.3

# 2. Set up project skills
# .opencode/skills/review.md
/review @src/ --focus security

# 3. Learn TUI shortcuts
# Tab: Plan/Build switch
# @: File references
# !: Shell commands
```

#### Week 3: Optimization
```bash
# 1. Monitor costs
!opencode stats
# Compare: Claude Code $20/month vs OpenCode usage

# 2. Create team workspace (if applicable)
# Visit: https://opencode.ai/team

# 3. Set up CI/CD integration
# Use OpenCode in your build pipeline
```

### Cost Comparison Example
**Claude Code**: $20/month (unlimited usage on Claude models)

**OpenCode with Claude**:
- 100,000 tokens input + 50,000 tokens output
- Using Claude Sonnet 4.6: (0.1 * $5) + (0.05 * $20) = $0.50 + $1.00 = $1.50
- **Savings**: $18.50/month for same usage

> **💡 Tip**: Use Zen's free models (MiniMax M2.5 Free) for experimentation, then switch to Claude for production work.

---

## 🔄 Migration from Cursor

### What You'll Recognize
- **AI-powered code generation** and editing
- **Project context understanding**
- **Edit commands** and refactoring
- **Multi-file operations**

### What's Different
1. **Philosophy**: Open-source community vs proprietary company
2. **Integration**: Terminal workflow vs IDE integration
3. **Extensibility**: Skills system vs limited plugins
4. **Pricing**: Transparent usage-based vs subscription

### Step-by-Step Migration

#### Week 1: Core Workflow
```bash
# 1. Install and configure
curl -fsSL https://opencode.ai/install | bash
opencode
/connect

# 2. Practice file referencing
# Cursor: Click files in sidebar
# OpenCode: Use @ syntax
Can you explain @src/components/Button.tsx?

# 3. Learn edit patterns
# Instead of Cursor's edit commands:
[Build] Refactor this function to use async/await @src/utils/api.ts
```

#### Week 2: Advanced Patterns
```bash
# 1. Create project-specific skills
# .opencode/skills/refactor.md
/refactor @src/ --pattern "callback-to-async"

# 2. Set up code review workflow
@code-reviewer Review @src/
[Build] Implement suggested changes

# 3. Use shell integration
# Cursor: Limited terminal access
# OpenCode: Full shell integration
!git status | /analyze-changes
```

#### Week 3: Customization
```bash
# 1. Build custom agents
# ~/.config/opencode/agents/frontend.md
name: Frontend Specialist
model: gpt-5.2-codex
# Specialized for React/TypeScript

# 2. Create MCP servers
# Extend OpenCode with custom tools
# See: docs/MCP-GUIDE.md

# 3. Optimize model usage
/models
# Select best model for each task type
```

### Workflow Comparison
**Cursor Workflow**:
1. Open project in Cursor IDE
2. Use AI commands from command palette
3. Edit files directly in editor
4. Limited to Cursor's feature set

**OpenCode Workflow**:
1. Work in your preferred editor/IDE
2. Use OpenCode TUI in separate terminal
3. Reference files with `@` syntax
4. Extend with custom skills and agents
5. Execute shell commands with `!`

> **💡 Tip**: Keep using your favorite editor (VS Code, Neovim, etc.) and use OpenCode as an AI assistant in a separate terminal window.

---

## 🔄 Migration from GitHub Copilot

### What You'll Recognize
- **AI code completion** and suggestions
- **Multi-language support**
- **IDE integration** (though different)
- **Context-aware suggestions**

### What's Different
1. **Scope**: Full AI assistant vs autocomplete
2. **Interaction**: Conversational vs predictive
3. **Context**: Entire project vs current file
4. **Pricing**: Usage-based vs $10/month subscription

### Step-by-Step Migration

#### Week 1: Mindset Shift
```bash
# 1. Install OpenCode
curl -fsSL https://opencode.ai/install | bash

# 2. Think beyond autocomplete
# Copilot: Predicts next line
# OpenCode: Conversational assistant
How would you implement user authentication in this project?

# 3. Use project-wide context
# Copilot: Current file context
# OpenCode: Entire project context
Based on @src/auth/ and @src/models/user.ts, design auth system
```

#### Week 2: Integration
```bash
# 1. Use both tools together
# Keep Copilot for line completion
# Use OpenCode for complex tasks

# 2. Create Copilot-like skills
# .opencode/skills/complete.md
/complete "function to validate email"

# 3. Set up quick access
# Alias for common tasks
alias oc="opencode ."
```

#### Week 3: Advanced Usage
```bash
# 1. Create documentation skills
/docs api --output markdown

# 2. Set up testing workflow
/tdd "User registration"
# Creates tests first, then implementation

# 3. Monitor and optimize
!opencode stats
# Compare costs with Copilot $10/month
```

### Complementary Usage Pattern
**For line completion**: Keep GitHub Copilot
**For complex tasks**: Use OpenCode

**Example workflow**:
1. Write code with Copilot suggestions
2. When stuck, switch to OpenCode terminal:
   ```bash
   opencode .
   Help me debug this issue in @src/utils/validation.ts:45
   ```
3. Implement solution with OpenCode's help
4. Return to editor with Copilot for continued coding

### Cost Analysis
**GitHub Copilot**: $10/month (unlimited usage)

**OpenCode**:
- Light usage (10K tokens/day): ~$3-5/month
- Heavy usage (100K tokens/day): ~$30-50/month
- **Strategy**: Use both - Copilot for daily coding, OpenCode for complex tasks

> **💡 Tip**: OpenCode complements Copilot well. Use Copilot for 80% of coding (autocomplete) and OpenCode for the 20% of complex problems.

---

## 🛠️ Technical Migration Checklist

### Phase 1: Setup (Day 1)
- [ ] Install OpenCode
- [ ] Set up Zen or preferred providers
- [ ] Test basic commands
- [ ] Configure shell aliases

### Phase 2: Workflow (Week 1)
- [ ] Practice TUI navigation
- [ ] Learn keyboard shortcuts
- [ ] Create first custom agent
- [ ] Set up project skills

### Phase 3: Integration (Week 2)
- [ ] Integrate with existing tools
- [ ] Set up team workspace (if applicable)
- [ ] Create CI/CD pipeline integration
- [ ] Monitor usage and costs

### Phase 4: Optimization (Week 3+)
- [ ] Fine-tune agent configurations
- [ ] Build custom MCP servers
- [ ] Create skill templates
- [ ] Share with team/community

---

## 🔧 Configuration Examples

### Claude Code Migration Config
```yaml
# ~/.config/opencode/config.yaml
providers:
  opencode:
    api_key: ${ZEN_API_KEY}
    default_model: claude-sonnet-4.6

agents:
  claude-style:
    path: ~/.config/opencode/agents/claude-style.md
    default: true

skills:
  project:
    path: .opencode/skills/
    auto_load: true
```

### Cursor Migration Config
```yaml
# ~/.config/opencode/config.yaml
ui:
  theme: dracula
  compact_mode: true

keybinds:
  switch_agent: "Tab"
  file_search: "@"
  shell_command: "!"

agents:
  frontend: .opencode/agents/frontend.md
  backend: .opencode/agents/backend.md
```

### GitHub Copilot Integration
```yaml
# ~/.config/opencode/config.yaml
integration:
  editors:
    vscode:
      command: "code {file}:{line}"
    neovim:
      command: "nvim +{line} {file}"

skills:
  copilot:
    - name: "complete"
      command: "Suggest completion for: {query}"
    - name: "explain"
      command: "Explain this code: @{file}"
```

---

## ❓ Common Migration Questions

### Q: Can I use OpenCode alongside my current tool?
**A**: Yes! Many developers use:
- GitHub Copilot for line completion
- OpenCode for complex tasks
- Their preferred editor for writing code

### Q: How do I handle keyboard shortcut conflicts?
**A**: OpenCode keybinds are customizable:
```json
// ~/.config/opencode/keybinds.json
{
  "switch_agent": "Ctrl+Space",
  "file_search": "Ctrl+F",
  "shell_command": "Ctrl+!"
}
```

### Q: What about my existing workflows?
**A**: Recreate them as OpenCode skills:
```bash
# Old workflow: Manual steps
# New workflow: Single command
/pr "Add user authentication"
# Creates branch, commits, tests, PR
```

### Q: How do I train my team?
**A**: 
1. Share this migration guide
2. Create team skill templates
3. Set up shared workspace
4. Schedule weekly knowledge sharing

---

## 📈 Success Metrics

### Track Your Migration Success

| Metric | Before | After 1 Month | Goal |
|--------|--------|---------------|------|
| **Monthly Cost** | $20 (Claude Code) | $5-15 | Reduce by 25-75% |
| **Task Completion Time** | X hours | X-30% hours | Reduce by 30% |
| **Code Quality** | Manual review | Automated review | Improve consistency |
| **Team Onboarding** | Weeks | Days | Reduce by 70% |

### Example Success Story
**Team**: 5 developers switching from Claude Code
**Timeline**: 4-week migration
**Results**:
- **Cost**: Reduced from $100/month to $35/month (65% savings)
- **Productivity**: 40% faster code reviews
- **Quality**: 25% fewer bugs in production
- **Satisfaction**: 4.8/5 team rating

---

## 🆘 Getting Help

### Migration Support
- **Community**: [Discord](https://discord.gg/opencode)
- **Documentation**: [docs.opencode.ai](https://docs.opencode.ai)
- **Examples**: [GitHub Examples](https://github.com/anomalyco/opencode-examples)

### Professional Services
- **Consulting**: Migration planning and training
- **Custom Development**: Tailored skills and agents
- **Team Training**: Workshops and certification

---

## 🎯 Next Steps

1. **Start small**: Migrate one project or workflow
2. **Measure results**: Track costs and productivity
3. **Share learnings**: Contribute to community
4. **Scale up**: Expand to entire team/organization

Remember: Migration is a journey, not a destination. Start with what works for you and gradually adopt more OpenCode features as you become comfortable.

> **🚀 Ready to begin?** Start with the [Quick Start Guide](../README.md#-quick-start-5-minutes) and take it one step at a time.

---

*Last updated: February 2026*  
*For migration assistance, join our [Discord community](https://discord.gg/opencode)*