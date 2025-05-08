# cursor-rules
A set of rules to be applied to cursor to enable automated access and functionality in the everyday workflow of an engineer.

## Overview
This repository contains a collection of rules that enhance Cursor's capabilities by integrating with various development tools and services. The rules are organized by technology and can be easily applied to any workspace.

## Directory Structure
- `*-rules/`: Directories named with the pattern `*-rules` contain integration rules for specific technologies (e.g., `gh-linear-rules`, `gh-jira-rules`)
- `templates/`: Contains template files that should be copied to your workspace's `.cursor/rules/templates/` directory
- `archive/`: Contains deprecated or archived rules

## Templates
The system includes two default templates that serve as integration points for the rules:
1. `issue.md`: Template for issue creation
2. `pr.md`: Template for pull request creation

These templates are optional and can be replaced with custom templates to match your team's workflow. When using custom templates, ensure they are placed in your workspace's `.cursor/rules/templates/` directory. **Important**: Custom templates must maintain the exact filenames (`issue.md` and `pr.md`) as the rules rely on these specific names for integration. The rules will integrate with whatever templates are present in this location, but they must be named correctly to be recognized.

## Authentication
The rules system expects authentication tokens to be available in the environment. These tokens should be set up before using the rules. Each integration may require different authentication methods, which are documented in their respective rule directories.

## Applying Rules to a Workspace
To apply these rules to your workspace:

1. Clone this repository to your local machine
2. Copy the desired rule directories to your workspace's `.cursor/rules/` directory
3. Either:
   - Copy the default templates from the root `templates/` directory to your workspace's `.cursor/rules/templates/` directory, or
   - Place your custom templates in your workspace's `.cursor/rules/templates/` directory (ensuring they are named `issue.md` and `pr.md`)
4. Ensure all required environment variables are set

### Workspace Rule Guidelines
When setting up rules in your workspace, please note these important considerations:

1. **Rule Precedence**: 
   - Use `always` for general rules that should apply in most cases
   - Use other rule types for specific cases, as these will take precedence over `always` rules
   - **Recommendation**: For best results, we recommend using only one `always` rule in your workspace. The rules provided in this repository include a comprehensive `always` rule that you can build upon.

2. **Best Practices**:
   - Keep all related rules in a single file
   - Use clear, specific rule types for different scenarios
   - Avoid splitting rules across multiple files unless absolutely necessary

## Available Integrations
- GitHub Linear Integration (`gh-linear-rules/`)
- GitHub Jira Integration (`gh-jira-rules/`)

Each integration directory contains specific rules and documentation for that particular service.

## Contributing
Feel free to contribute new rules or improvements to existing ones. Please follow the established directory structure and include appropriate documentation.

### Rule Organization Guidelines
When contributing rules, please note the following important considerations:

1. **Rule Similarity**: Rules are very similar between different technologies, with only the interfacing portions differing.

2. **Rule Compilation**: Cursor works best with a single, comprehensive set of rules. It's recommended to compile all rules into a single file rather than splitting them across multiple files.

3. **Composition Limitations**: 
   - **Important**: Currently, Cursor does not reliably support rule composition through references
   - While it might be tempting to reduce duplication by referencing rules from other files, this approach is not recommended
   - Each rule set should be self-contained and complete
   - Duplication is preferred over composition until Cursor's rule handling improves
