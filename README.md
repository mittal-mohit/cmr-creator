# CMR Creator

A comprehensive toolkit for creating Change Management Requests (CMRs) for enterprise deployment processes.

## 🚀 Features

- **Automated CMR Generation**: Create CMRs from pull requests with enhanced CodeRabbit integration
- **Service Discovery**: Automatic mapping of repositories to services
- **Version Management**: Intelligent base and merge commit tag identification
- **Deployment Planning**: Pre-configured deployment steps and monitoring links
- **JIRA Integration**: Direct integration with Atlassian JIRA for CMR creation

## 📁 Project Structure

```
CMR creator/
├── .cursor/
│   └── rules/
│       ├── cmr-create-prompt.mdc     # Main CMR creation assistant prompt
│       └── jira-search-best-practices.mdc  # JIRA search optimization guide
├── aCursorRules.js                   # Cursor IDE configuration
├── jira-search-best-practices.mdc    # JIRA search patterns and strategies
├── url_shortener_architecture.md     # Example architecture documentation
└── README.md                         # This file
```

## 🛠️ Key Components

### CMR Creation Assistant (`cmr-create-prompt.mdc`)
- **Step A**: Repository analysis, service discovery, and version identification
- **Step B**: Deployment preferences and required inputs collection
- **Step C**: JIRA payload preparation and CMR creation
- **Enhanced CodeRabbit Integration**: Automatic extraction of CodeRabbit summaries from PRs

### JIRA Search Best Practices (`jira-search-best-practices.mdc`)
- Proven search strategies for JIRA tickets
- Reliable project-based searches with absolute date ranges
- Service-specific search patterns
- Common pitfalls and solutions

## 📋 Usage

### Creating a CMR from PR

1. **Basic CMR Creation:**
   ```
   create CMR for this PR - @https://github.com/company-org/service-name/pull/123
   ```

2. **Deployment Preferences:**
   - Choose deployment day (Today/Tomorrow)
   - Select preferred time slot
   - Provide regression report links
   - Specify deployment buddy names

3. **Automatic Processing:**
   - Service discovery from repository mapping
   - Version tag identification and comparison links
   - CodeRabbit summary extraction
   - JIRA CMR creation with proper formatting

### Service Mapping

Supported services include:
- `scm-api-gateway`
- `scm-task-manager`

## 🔧 Configuration

### Monitoring Links
Pre-configured monitoring dashboards:
- **Logman**: Service-specific log monitoring
- **EagleEye**: Metrics and performance monitoring
- **Deployment Dashboard**: Canary deployment tracking

### Deployment Timeline
Standard canary deployment process:
- 0% canary: Sanity checks
- 1% canary: 30 minutes observation  
- 10% canary: 30 minutes observation
- 50% canary: 1 hour observation

## 📈 CodeRabbit Integration

The CMR creator now includes enhanced CodeRabbit support:

- **Priority 1**: Extract CodeRabbit summaries from PR bodies
- **Priority 2**: Include CodeRabbit walkthrough comments
- **Priority 3**: Fallback to manual PR summarization

Categories supported:
- New Features
- Bug Fixes  
- Chores
- Tests
- Documentation
- Refactor
- Performance

## 🎯 Best Practices

### JIRA Searches
- Use exact service names: `project = "Change Management" AND summary ~ "service-name"`
- Employ absolute date ranges: `created >= "2025-01-01"`
- Avoid relative date syntax (`-6m`, `-3m`) - unreliable in JIRA

### CMR Creation
- Always include comprehensive monitoring links
- Provide clear rollback procedures
- Include specific sanity check steps
- Mention deployment buddies with @mentions

## 🔗 Dependencies

- **Coast CLI**: For service version management
- **GitHub MCP**: For pull request analysis
- **Atlassian MCP**: For JIRA integration
- **Git**: For repository operations

## 📚 Documentation Standards

- Follow markdown best practices
- Include comprehensive examples
- Maintain clear step-by-step guides
- Update service mappings as needed

## 🚀 Getting Started

1. Clone this repository
2. Configure your environment with required CLI tools
3. Use the CMR creation prompts in your AI assistant
4. Follow the A → B → C workflow strictly

## 🤝 Contributing

When updating:
- Maintain the strict A → B → C workflow
- Test with actual PRs before committing
- Update service mappings for new repositories
- Document any new monitoring links

---

**Created for streamlined CMR generation in enterprise environments** 🚀