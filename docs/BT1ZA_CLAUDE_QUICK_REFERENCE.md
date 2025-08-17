# BT1ZA Claude Upgrade Quick Reference

## Emergency Repository Access Issue

🚨 **ISSUE**: `g2goose/bt1za_claude` repository returns 404 (not found)

**Possible Causes**:
1. Repository is private and requires authentication
2. Repository name has changed or been moved
3. Repository has been deleted
4. Typo in repository name
5. Organization name changed

**Resolution Steps**:
1. **Verify Repository Name**: Double-check spelling and organization
2. **Check Alternative Names**: Search for similar repositories under g2goose
3. **Contact Repository Owner**: Reach out to g2goose for clarification
4. **Alternative Access**: Use SSH if HTTPS fails, or check personal tokens

```bash
# Alternative access attempts
git clone git@github.com:g2goose/bt1za_claude.git
git clone https://username:token@github.com/g2goose/bt1za_claude.git

# Search for similar repositories
gh repo list g2goose --limit 50 | grep -i claude
gh repo list g2goose --limit 50 | grep -i bt1za
```

## Quick Implementation Summary

### Phase 1: Assessment (When Repository Accessible)
```bash
# 1. Clone and analyze
git clone https://github.com/g2goose/bt1za_claude.git
cd bt1za_claude

# 2. Quick assessment
bash -c 'echo "=== Project Structure ==="; tree -L 2 -a'
bash -c 'echo "=== Language Distribution ==="; find . -name "*.py" | wc -l | xargs echo "Python files:"; find . -name "*.js" -o -name "*.ts" | wc -l | xargs echo "JS/TS files:"'
bash -c 'echo "=== Existing AI Context ==="; find . -name "*claude*" -o -name "*CLAUDE*" -o -name "*context*" -type f'
```

### Phase 2: Framework Installation
```bash
# 1. Backup
git checkout -b backup/pre-kit-upgrade
git push origin backup/pre-kit-upgrade
git checkout -b feature/claude-kit-upgrade

# 2. Install kit
git clone https://github.com/g2goose/Claude-Code-Development-Kit.git kit-temp
./kit-temp/setup.sh

# 3. Configure
# Choose: Context7 MCP [Y], Gemini Assistant MCP [Y], Notifications [Y/N]
```

### Phase 3: Documentation Setup
```bash
# 1. Create master context
# Edit CLAUDE.md with project-specific information

# 2. Create project structure
# Fill out docs/ai-context/project-structure.md

# 3. Create component contexts
# Add CONTEXT.md files to major components
```

### Phase 4: Testing
```bash
# Test commands
/full-context "test framework integration"
/create-docs "backend/CONTEXT.md"
/update-docs "test documentation update"
```

## Configuration Quick Reference

### Essential Files Created
```
bt1za_claude/
├── .claude/
│   ├── commands/          # Custom AI orchestration
│   ├── hooks/             # Automation scripts
│   └── settings.local.json # Claude Code configuration
├── docs/
│   └── ai-context/        # 3-tier documentation
├── CLAUDE.md              # Master AI context
└── MCP-ASSISTANT-RULES.md # Coding standards
```

### Key Commands
- `/full-context` - Orchestrated development with sub-agents
- `/code-review` - Multi-perspective code analysis
- `/update-docs` - Maintain documentation currency
- `/create-docs` - Generate new component documentation
- `/gemini-consult` - Expert AI consultation
- `/handoff` - Session continuity management

### MCP Server Integration
```json
{
  "mcpServers": {
    "gemini-assistant": {
      "command": "npx",
      "args": ["@peterkrueck/mcp-gemini-assistant"]
    },
    "context7": {
      "command": "npx", 
      "args": ["@context7/mcp-server"]
    }
  }
}
```

## Troubleshooting Common Issues

### Issue: Setup Script Fails
```bash
# Check permissions
chmod +x ./kit-temp/setup.sh

# Check requirements
which git && echo "Git: OK" || echo "Git: MISSING"
which node && echo "Node: OK" || echo "Node: MISSING"
```

### Issue: Hooks Not Working
```bash
# Check hook permissions
chmod +x .claude/hooks/*.sh

# Test hook directly
./.claude/hooks/gemini-context-injector.sh test
```

### Issue: MCP Servers Not Connecting
```bash
# Verify installation
npm list -g | grep -E "(gemini-assistant|context7)"

# Check configuration
cat .claude/settings.local.json | grep -A 10 mcpServers
```

## Success Validation Checklist

### ✅ Installation Complete
- [ ] `.claude/` directory exists with all components
- [ ] `CLAUDE.md` created from template
- [ ] Hooks executable and configured
- [ ] MCP servers installed (if selected)

### ✅ Basic Functionality
- [ ] Commands load without errors
- [ ] Context injection working
- [ ] Security scanning operational
- [ ] Documentation auto-loading functional

### ✅ Advanced Features
- [ ] Multi-agent orchestration working
- [ ] External AI consultations successful
- [ ] Documentation maintenance automated
- [ ] Project-specific customizations applied

## Rollback Procedure

If upgrade needs to be reversed:

```bash
# Return to backup branch
git checkout backup/pre-kit-upgrade

# Remove kit files (if needed)
rm -rf .claude/
rm -f CLAUDE.md MCP-ASSISTANT-RULES.md
rm -rf docs/ai-context/

# Verify rollback
git status  # Should show clean working directory
```

## Next Actions Required

1. **🔴 CRITICAL**: Resolve repository access issue
   - Contact g2goose organization
   - Verify repository name and location
   - Obtain necessary permissions

2. **📋 ASSESSMENT**: Once accessible, run assessment checklist
   - Use `BT1ZA_CLAUDE_ASSESSMENT_CHECKLIST.md`
   - Complete compatibility scoring
   - Determine implementation approach

3. **🚀 IMPLEMENTATION**: Execute upgrade strategy
   - Follow `BT1ZA_CLAUDE_UPGRADE_STRATEGY.md`
   - Use this quick reference for commands
   - Document project-specific adaptations

---

**Contact Information for Support**:
- Claude Code Development Kit: GitHub Issues
- Repository Access: g2goose organization
- Technical Questions: Framework documentation

*Last Updated: [Current Date]*