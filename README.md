# Claude Code Spec-Driven Development

A Kiro-style Spec-Driven Development framework for Claude Code using hooks and slash commands.

**Original Author**: [gotalab](https://github.com/gotalab/claude-code-spec)

## Overview

This project implements a structured development workflow that follows a rigorous 3-phase approval process: Requirements → Design → Tasks → Implementation. It leverages Claude Code's hook system and custom slash commands to automate progress tracking and maintain project context.

## Features

- **Steering Documents**: Persistent project knowledge through markdown files
- **3-Phase Approval Workflow**: Structured development process with human approval gates
- **Automated Progress Tracking**: Real-time task completion monitoring
- **Spec Compliance Checking**: Ensures alignment with project specifications
- **Context Preservation**: Maintains project knowledge across sessions

## Quick Start

### 1. Initialize Steering Documents (Recommended)
```
/steering-init          # Generate initial steering documents
/steering-update        # Update steering after changes
/steering-custom        # Create custom steering for specialized contexts
```

### 2. Create Your First Specification
```
/spec-init [feature-name]           # Initialize spec structure
/spec-requirements [feature-name]   # Generate requirements
/spec-design [feature-name]         # Generate technical design
/spec-tasks [feature-name]          # Generate implementation tasks
```

### 3. Track Progress
```
/spec-status [feature-name]         # Check current progress and phases
```

## Development Workflow

### Phase 0: Steering Generation (Optional)
Generate project steering documents to establish context and guidelines.

### Phase 1: Requirements Generation & Approval
1. **Generate**: Create requirements document
2. **Review**: Human reviews and edits requirements.md
3. **Approve**: Manually update spec.json to set `"requirements": true`

### Phase 2: Design Generation & Approval
1. **Generate**: Create technical design (requires requirements approval)
2. **Review**: Human reviews and edits design.md
3. **Approve**: Manually update spec.json to set `"design": true`

### Phase 3: Tasks Generation & Approval
1. **Generate**: Create implementation tasks (requires design approval)
2. **Review**: Human reviews and edits tasks.md
3. **Approve**: Manually update spec.json to set `"tasks": true`

### Implementation
Begin implementation only after all three phases are approved.

## Clarification Process

After `/spec-init`, the AI will:
1. Analyze project description for unclear details
2. Ask 5-10 clarification questions
3. Wait for user responses
4. Merge responses into requirements.md
5. Mark `clarifications_collected: true` in spec.json

## Steering System

### Core Steering Documents
- **product.md**: Product overview, features, use cases, value proposition
- **tech.md**: Architecture, tech stack, development environment
- **structure.md**: Directory organization, code patterns, naming conventions

### Custom Steering
Create specialized steering documents for:
- API standards
- Testing approaches
- Code style guidelines
- Security policies
- Database conventions
- Performance standards
- Deployment workflows

## Automation Features

- **Task Progress Tracking**: Automatic checkbox parsing and completion monitoring
- **Spec Compliance**: Validation against project specifications
- **Context Preservation**: Maintains project knowledge during compaction
- **Steering Drift Detection**: Identifies when steering documents need updates

## Development Rules

1. Consider running `/steering-init` before major development
2. Follow the 3-phase approval workflow strictly
3. Manual approval required for each phase
4. No skipping phases - each builds on the previous
5. Update task status as work progresses
6. Keep steering documents current
7. Use `/spec-status` to verify alignment

## Active Specifications

- **ai-auto-slug-plugin**: WordPress AI-powered slug generator (initialized)

Use `/spec-status [feature-name]` to check progress on any specification.

## Language Note

Development guidelines: Think in English, generate responses in Traditional Chinese (使用英文思考，繁體中文回答).

## Getting Started

1. Initialize steering: `/steering-init`
2. Create your first spec: `/spec-init [your-feature-name]`
3. Follow the workflow through requirements, design, and tasks
4. Begin implementation after all approvals

## Contributing

This framework emphasizes quality through structured approval gates. Each phase requires explicit human review and approval to ensure accuracy and alignment with project goals.