# CMR Creator

A comprehensive toolkit for creating Change Management Requests (CMRs) from pull requests with automated JIRA integration.

## 🚀 Features

- **Automated CMR Generation**: Create CMRs from PRs with CodeRabbit integration
- **Service Discovery**: Automatic repo-to-service mapping and version identification
- **JIRA Integration**: Direct CMR creation with proper formatting and custom fields
- **Deployment Planning**: Pre-configured steps, monitoring links, and canary timelines

## 📁 Project Structure

```
CMR creator/
├── .cursor/rules/                    # AI assistant configuration
├── sample-cmr-request.json          # Complete JIRA MCP request example
├── jira-search-best-practices.mdc   # JIRA search optimization guide
└── sampleCursorSettings.json        # Cursor IDE settings
```

## 📋 Quick Start

**Create CMR from PR:**
```
create CMR for this PR - @https://github.com/company-org/service-name/pull/123
```

**Follow the A→B→C workflow:**
- **Step A**: Repository analysis and version identification
- **Step B**: Deployment preferences (day, time, buddies, regression links)
- **Step C**: Automated JIRA CMR creation

**Supported Services:**
- `scm-api-gateway`
- `scm-task-manager`

## 🛠️ Key Components

**CMR Creation Assistant** - Complete A→B→C workflow with CodeRabbit integration
**Sample Request JSON** - Full JIRA MCP structure with all required fields
**JIRA Search Guide** - Proven search patterns and troubleshooting

## 🎯 Best Practices

**JIRA Searches:**
- Use: `project = "Change Management" AND summary ~ "service-name"`
- Use absolute dates: `created >= "2025-01-01"`
- Avoid relative syntax (`-6m`) - unreliable

**CMR Creation:**
- Include monitoring links and rollback procedures
- Mention deployment buddies with @mentions
- Follow standard canary timeline: 0% → 1% (30min) → 10% (30min) → 50% (1hr)

---

**Enterprise CMR automation toolkit** 🚀
