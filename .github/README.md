# GitHub Template Repository

This is a template repository for creating new projects with Cursor-based agentic development.

## Using This Template

### Option 1: GitHub UI

1. Click the "Use this template" button at the top of the repository
2. Choose a name for your new repository
3. Select public or private
4. Click "Create repository from template"

### Option 2: GitHub CLI

```bash
gh repo create my-new-project --template yourusername/cursor-project-template
```

### Option 3: Manual Clone

```bash
git clone https://github.com/yourusername/cursor-project-template.git my-new-project
cd my-new-project
rm -rf .git
git init
git add .
git commit -m "Initial commit from template"
```

## What's Included

This template provides:

- **Modular Rules System** - `.cursor/rules/` for focused AI guidance
- **Core Configuration** - `.cursorrules`, `.gitignore`, `.cursorignore`
- **Documentation Structure** - LLM-optimized docs in `docs/`
- **Pattern Guides** - Workflows and agent specifications
- **Universal Scaffolding** - Works with any language/framework

## Next Steps

After creating your repository from this template:

1. **Customize for your stack** - Update configurations for your language/framework
2. **Fill in documentation** - Complete the skeleton docs for your project
3. **Add modular rules** - Create rules specific to your project
4. **Set up CI/CD** - Add GitHub Actions or other CI/CD workflows
5. **Start building** - Begin implementing your project

See `docs/PROJECT_SETUP.md` for detailed customization instructions.

## Template Features

### For Any Project Type

- Web applications
- Mobile applications  
- Backend APIs
- CLI tools
- Libraries
- Data science projects
- And more...

### Language/Framework Agnostic

No assumptions about:
- Programming language
- Framework
- Build tools
- Package managers
- Testing frameworks

Add what you need!

### LLM-Optimized

Documentation and structure designed for:
- Easy discovery with `@` references
- Clear context boundaries
- Semantic search friendly
- Modular and focused

## Contributing

Improvements to this template are welcome!

See `docs/CONTRIBUTING.md` for guidelines.

## Support

- **Documentation**: See `docs/README.md`
- **Issues**: Open an issue in this repository
- **Discussions**: Use GitHub Discussions for questions

## License

MIT License - see [LICENSE](../LICENSE)

---

**Ready to start?** Use this template to create your new project and follow the setup guide in `docs/PROJECT_SETUP.md`.

