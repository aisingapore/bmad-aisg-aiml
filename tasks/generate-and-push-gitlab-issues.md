# Generate and Push GitLab Issues Task (EXECUTION WORKFLOW)

## ⚠️ CRITICAL EXECUTION NOTICE ⚠️

**THIS IS AN EXECUTABLE WORKFLOW - NOT REFERENCE MATERIAL**

When this task is invoked:

1. **DISABLE ALL EFFICIENCY OPTIMIZATIONS** - This workflow requires full user interaction
2. **MANDATORY STEP-BY-STEP EXECUTION** - Each section must be processed sequentially with user feedback
3. **ELICITATION IS REQUIRED** - When steps require user input, you MUST wait for user response
4. **NO SHORTCUTS ALLOWED** - Issues cannot be created without following this workflow

**VIOLATION INDICATOR:** If you create GitLab issues without proper user interaction and verification, you have violated this workflow.

---
generationTemplate: ".bmad-core/templates/gitlab-issues-tmpl.yaml"
executionTemplate: ".bmad-core/templates/project-status.yaml"
---

# Generate and Push GitLab Issues Task

Create GitLab issues from project documentation, track issue status (open/closed/in-progress), manage assignments, and update project-status.json with current GitLab issue states.

## CRITICAL: Mandatory User Interaction Format

**When user input is required, this is a HARD STOP requiring user interaction:**

**YOU MUST:**

1. Present the current step/requirement clearly
2. Provide detailed rationale (explain choices, assumptions, decisions needed)
3. **STOP and present numbered options 1-9:**
   - **Option 1:** Always "Proceed with provided information"
   - **Options 2-9:** Select 8 methods from data/elicitation-methods for gathering requirements
   - End with: "Select 1-9 or just type your question/feedback:"
4. **WAIT FOR USER RESPONSE** - Do not proceed until user provides input or selects option

**WORKFLOW VIOLATION:** Creating GitLab issues or proceeding with API calls without proper user verification violates this task.

**NEVER assume configuration values or proceed without explicit user confirmation.**

## Processing Flow

1. **Check GitLab Issue Status** - Query existing issues and their current states
2. **Verify GitLab API Access** - Test connectivity and permissions
3. **Process Documentation** - Load user stories and sprint planning data
4. **Create Missing Issues** - Generate new GitLab issues as needed
5. **Update Issue Tracking** - Sync issue states, assignees, and progress
6. **Generate project-status.json** - Update project status file with GitLab data

## Process

### Step 1: Project Status Check

**CRITICAL - MANDATORY USER INTERACTION**: Always ask user for project context choice regardless of existing status.

**FIRST - Check for existing project status:**

Check if `docs/project-status.json` exists:
- **If EXISTS**: Read current project status and display to user for context
- **If NOT EXISTS**: Display "No existing project status found"

**If status file exists, display:**
```
🔍 EXISTING PROJECT STATUS FOUND:
- Project: [name] ([id])
- Last Updated: [timestamp]
- Current Status: [status]
- Sprint: [currentSprint]
- Issues Created: [successful]/[total]
- Next Actions: [nextActions array]
```

**If status file does NOT exist, display:**
```
🆕 NO EXISTING PROJECT STATUS FOUND:
- This appears to be a fresh project setup
- No previous sprint issues have been created
- Ready to start from scratch
```

**MANDATORY USER INTERACTION - STOP - Present numbered options 1-3:**
- **Option 1:** Continue with existing project context (use existing status and append new issues)
- **Option 2:** Start fresh sprint planning (ignore existing status, create new sprint)
- **Option 3:** Update existing sprint (modify current sprint configuration)
- End with: "Select 1-3 to choose your approach:"

**WAIT FOR USER RESPONSE** - Do not proceed until user selects project context approach.

### Step 2: GitLab Configuration Verification

**CRITICAL - MANDATORY USER INTERACTION**: Test GitLab configuration before proceeding.

**Execute this single command to verify everything:**

```bash
bash -c 'source .env && echo "=== GitLab Configuration Test ===" && echo "GitLab URL: $GITLAB_URL" && echo "Project ID: $PROJECT_ID" && echo "Testing API..." && curl -s -H "PRIVATE-TOKEN: $GITLAB_TOKEN" "$GITLAB_URL/api/v4/projects/$PROJECT_ID" | jq "{name, path_with_namespace, web_url}"'
```

**This command will:**
- Load all environment variables from .env
- Display GitLab URL and Project ID
- Test API connectivity and token permissions
- Show project name, path, and URL
- Confirm full access in one step

**If successful, you'll see project details. If it fails, see the GitLab API Integration section below for .env configuration setup.**

**Rationale:** One command tests everything needed - no separate file reading or multiple steps required.

**STOP - Present numbered options 1-2:**
- **Option 1:** Proceed with tested configuration
- **Option 2:** Set new configuration
- End with: "Select 1-2 or just type your configuration details:"

**WAIT FOR USER RESPONSE** - Do not proceed until user provides configuration or selects option.

### Step 3: Project Documentation Collection

**CRITICAL - MANDATORY USER INTERACTION**: Request project documentation files from the user.

**Present this requirement to user and STOP for interaction:**

**Required Project Documentation:**

1. **User Stories File** (optional - if no updates):
   - User stories file for requirement understanding (file path or content)

2. **Sprint Planning File** (required):
   - Sprint planning file that defines specific tasks/issues for this sprint (file path or content)
   - If provided, this will be the PRIMARY source for issue generation

**Rationale:** Project documentation determines the scope and accuracy of generated issues. Without proper documentation, issues may be incomplete or misaligned with project goals.

**STOP - Present numbered options 1-2:**
- **Option 1:** Enter the path of the documents and proceed with provided documentation (or none if not available)
- **Option 2:** Create User Stories and Sprint Planning templates in docs folder
- End with: "Select 1-2 or provide your documentation files/paths:"

**WAIT FOR USER RESPONSE** - Do not proceed until user provides documentation or selects option.

### Step 3.1: File Format Processing - Excel to CSV Conversion

**IF USER PROVIDES EXCEL FILES (.xlsx, .xls)**: Convert Excel files to CSV format for processing.

**Excel File Detection and Conversion Process:**

```bash
# Function to detect and convert Excel files
process_documentation_files() {
    local product_backlog_file="$1"
    local sprint_planning_file="$2"
    
    echo "=== PROCESSING DOCUMENTATION FILES ==="
    
    # Create docs/converted directory if it doesn't exist
    mkdir -p docs/converted
    
    # Process Product Backlog file
    if [[ "$product_backlog_file" == *.xlsx ]] || [[ "$product_backlog_file" == *.xls ]]; then
        echo "📋 Converting Product Backlog Excel file to CSV..."
        
        # Extract filename without path and extension
        backlog_basename=$(basename "$product_backlog_file" .xlsx)
        backlog_basename=$(basename "$backlog_basename" .xls)
        
        # Convert to CSV using LibreOffice (preferred method)
        if command -v libreoffice &> /dev/null; then
            echo "Converting using LibreOffice headless mode..."
            libreoffice --headless --convert-to csv --outdir docs/converted "$product_backlog_file" 2>/dev/null
            echo "✅ Product Backlog converted: docs/converted/${backlog_basename}.csv"
            PRODUCT_BACKLOG_CSV="docs/converted/${backlog_basename}.csv"
        elif command -v python3 &> /dev/null && python3 -c "import pandas" 2>/dev/null; then
            echo "Converting using Python pandas..."
            python3 -c "
import pandas as pd
df = pd.read_excel('$product_backlog_file')
df.to_csv('docs/converted/${backlog_basename}.csv', index=False)
print('✅ Product Backlog converted using pandas')
"
            PRODUCT_BACKLOG_CSV="docs/converted/${backlog_basename}.csv"
        else
            echo "❌ No Excel conversion tool available (libreoffice or pandas)"
            echo "Please manually convert $product_backlog_file to CSV format"
            return 1
        fi
    else
        echo "📋 Product Backlog is already in CSV format"
        PRODUCT_BACKLOG_CSV="$product_backlog_file"
    fi
    
    # Process Sprint Planning file
    if [[ "$sprint_planning_file" == *.xlsx ]] || [[ "$sprint_planning_file" == *.xls ]]; then
        echo "📋 Converting Sprint Planning Excel file to CSV..."
        
        # Extract filename without path and extension
        sprint_basename=$(basename "$sprint_planning_file" .xlsx)
        sprint_basename=$(basename "$sprint_basename" .xls)
        
        # Convert to CSV using LibreOffice (preferred method)
        if command -v libreoffice &> /dev/null; then
            echo "Converting using LibreOffice headless mode..."
            libreoffice --headless --convert-to csv --outdir docs/converted "$sprint_planning_file" 2>/dev/null
            echo "✅ Sprint Planning converted: docs/converted/${sprint_basename}.csv"
            SPRINT_PLANNING_CSV="docs/converted/${sprint_basename}.csv"
        elif command -v python3 &> /dev/null && python3 -c "import pandas" 2>/dev/null; then
            echo "Converting using Python pandas..."
            python3 -c "
import pandas as pd
df = pd.read_excel('$sprint_planning_file')
df.to_csv('docs/converted/${sprint_basename}.csv', index=False)
print('✅ Sprint Planning converted using pandas')
"
            SPRINT_PLANNING_CSV="docs/converted/${sprint_basename}.csv"
        else
            echo "❌ No Excel conversion tool available (libreoffice or pandas)"
            echo "Please manually convert $sprint_planning_file to CSV format"
            return 1
        fi
    else
        echo "📋 Sprint Planning is already in CSV format"
        SPRINT_PLANNING_CSV="$sprint_planning_file"
    fi
    
    echo ""
    echo "📁 PROCESSED FILES:"
    echo "- Product Backlog CSV: $PRODUCT_BACKLOG_CSV"
    echo "- Sprint Planning CSV: $SPRINT_PLANNING_CSV"
    echo ""
}
```

**File Processing Instructions:**
1. **Detect File Extensions**: Check if provided files are Excel (.xlsx/.xls) or CSV
2. **Convert Excel Files**: Use LibreOffice or pandas to convert Excel to CSV
3. **Save to docs/converted/**: All converted files saved in organized folder
4. **Update File Paths**: Use converted CSV files for subsequent processing
5. **Verify Conversion**: Confirm successful conversion before proceeding

**MANDATORY USER INTERACTION**: After file conversion, confirm processed files before proceeding.

**Conversion Tools Priority:**
1. **LibreOffice** (headless mode) - Primary method, most reliable for complex Excel files, suppresses Java warnings
2. **Python pandas** - Secondary method for simple Excel files with standard formatting
3. **Manual conversion** - Fallback if automated tools unavailable

**LibreOffice Benefits:**
- Handles complex Excel formatting and formulas
- Preserves data integrity during conversion
- Built-in CSV export with proper delimiter handling
- Headless mode prevents GUI interference

### Step 3.2: Option 2 - Create User Stories and Sprint Planning Templates

**IF USER SELECTS OPTION 2**: Create structured templates for User Stories and Sprint Planning.

**Template Creation Process:**

1. **Create Product Backlog Template** in `docs/product-backlog.csv`:
   - Create Excel-compatible CSV file with columns:
     - S/N, Type of User, Perform Some Task, Achieve Some Goal, Component, Date Created, Created By, Status, Priority, Remarks

2. **Create Sprint Planning Template** in `docs/sprint-planning.csv`:
   - Create Excel-compatible CSV file with columns:
     - S/N, Task, Short Description/Details, Days, Priority, Remarks

**Template Creation Commands:**

```bash
# Create docs directory if it doesn't exist
mkdir -p docs

# Create product backlog CSV template (can be opened in Excel)
echo "S/N,Type of User,Perform Some Task,Achieve Some Goal,Component,Date Created,Created By,Status,Priority,Remarks" > docs/product-backlog.csv

# Create sprint planning CSV template (can be opened in Excel)
echo "S/N,Task,Short Description/Details,Days,Priority,Remarks" > docs/sprint-planning.csv
```

**After template creation, present to user:**

"✅ Templates created successfully:
- `docs/product-backlog.csv` - For User Stories documentation
- `docs/sprint-planning.csv` - For Sprint Planning documentation

**Next Steps:**
1. Fill out the templates with your project details
2. Save as Excel files if preferred (.xlsx)
3. Provide the file paths when ready to continue

**Please provide the file paths of your completed documentation:**
- Product Backlog file path: 
- Sprint Planning file path: 

Once you provide the file paths, we'll continue with the GitLab issue generation process."

**STOP and WAIT FOR USER RESPONSE** - Do not proceed until user provides the completed file paths.

### Step 4: Sprint Planning Strategy Selection

**Conditional Logic Based on Available Files**:

**IF Sprint Planning File is PROVIDED**:
- Use the sprint planning file as the primary source for generating issues
- Follow the tasks/issues defined in the sprint planning document
- Extract task breakdowns, assignments, and priorities from the sprint planning
- Supplement with user stories file for additional context if needed

**IF Sprint Planning File is NOT PROVIDED**:
- Ask user: "No sprint planning file provided. Would you like to generate issues based on your user stories file?"
- If YES and user stories file exists: Use user stories as basis for issue generation
- If NO or no user stories file: Proceed with manual sprint planning input collection (Step 4)

### Step 5: Manual Sprint Planning Input Collection (Fallback)

**Only if no sprint planning file and user chooses not to use user stories file**:

Request detailed sprint planning input from the user:

1. **Sprint Information**:
   - Sprint number and name
   - Sprint duration and dates  
   - Sprint goals and objectives
   - Project type (100E or SIP)

2. **User Stories**:
   - AISG team user stories for this sprint
   - Client user stories for this sprint
   - User story IDs from product backlog
   - Priority and acceptance criteria

3. **Technical Requirements**:
   - Specific deliverables for this sprint
   - Technical tasks and dependencies
   - Infrastructure and tooling needs
   - Integration requirements

4. **Team Information**:
   - Available apprentices and their GitLab user IDs
   - Senior developer availability for guidance
   - Specialized expertise requirements

### Step 6: Task Breakdown and Issue Generation

Break down sprint requirements into 1-3 day tasks with GitLab-ready format:

**CRITICAL: Load Generation Template**
Load the generation template for proper issue structure:
```bash
# Load generation template for issue formatting
cat .bmad-core/templates/gitlab-issues-tmpl.yaml
```
Use the template's `issue_structure` section for JSON formatting.

**CRITICAL - MANDATORY USER INTERACTION**: Generate issues file for verification before GitLab push.

**IMPORTANT NOTES:**
- **Product Backlog = User Stories Source**: If user has provided a product backlog file, treat it as the user stories source
- **Check Current GitLab Board**: Before generating issues, check current GitLab issue board to avoid duplicates
- **User Stories Format**: Generate user story issues with format: `[User Story <S/N>] As a <persona>, I want to <feature>, so that <reason>`
- **Sprint Planning Deduplication**: Cross-reference sprint planning tasks with existing GitLab issues to prevent duplicates

**🚨 CRITICAL USER STORY COVERAGE CHECK 🚨**
- **MANDATORY**: If user uploaded Product Backlog file, you MUST check ALL user stories for completeness
- **WORKFLOW VIOLATION**: Proceeding without comprehensive user story coverage check violates this task
- **COMMON MISTAKE**: Only checking sprint tasks while missing user story gaps leads to incomplete issue generation
- **REQUIREMENT**: Compare EVERY user story in Product Backlog against existing GitLab "[User Story X]" issues
- **ACTION**: Generate missing user stories FIRST, then add sprint planning tasks

**Present this requirement to user and STOP for interaction:**

**Issue Generation and Verification Process:**

1. **Check Current GitLab Issues**: Query existing issues to avoid duplicates
2. **🔍 MANDATORY USER STORY COMPLETENESS CHECK**: If Product Backlog provided, perform comprehensive user story analysis
   - **Count Total User Stories**: Identify all valid user stories in Product Backlog (exclude empty/invalid entries)
   - **Query Existing User Story Issues**: Get all existing "[User Story X]" issues from GitLab
   - **Gap Analysis**: Compare Product Backlog user stories vs existing GitLab user story issues
   - **Missing User Stories Identification**: Create list of missing user stories that need to be generated
   - **STOP and Inform User**: Present missing user story analysis before proceeding
3. **Process User Stories**: Convert missing product backlog entries to user story issues
   - **User Story Deduplication**: Cross-reference with existing GitLab "[User Story X]" issues  
   - **User Stories Format**: Generate user story issues with format: `[User Story <S/N>] As a <persona>, I want to <feature>, so that <reason>`
   - **Priority Order**: Generate missing user stories FIRST before sprint tasks
4. **Process Sprint Tasks**: Convert sprint planning tasks to technical issues if provided
5. **Generate Issues File**: Create a comprehensive file containing all generated issues for user review
6. **User Verification**: Allow user to review, modify, or approve the generated issues
7. **File Location**: Ask user for preferred save location or default to docs folder

**File Save Location Options:**
- Specify custom path for the issues file
- **Default location: docs/gitlab-issues-generated.json** (always save in docs folder)
- Include timestamp for version tracking
- **IMPORTANT**: All generated files should be saved in the docs folder for organization

**Rationale:** User verification prevents incorrect or unwanted issues from being created in GitLab. This step allows review and modification before permanent creation.

**STOP - Present numbered options 1-2:**
- **Option 1:** Generate issues file with default location (docs/gitlab-issues-generated.json)
- **Option 2:** Modify task assignments or priorities
- End with: "Select 1-2 or specify your preferred file location:"

**WAIT FOR USER RESPONSE** - Do not proceed until user provides file location or selects option.

**STEP 6.1: Check Existing GitLab Issues for Deduplication**

**MANDATORY BEFORE ISSUE GENERATION**: Query current GitLab issue board to prevent duplicate issue creation.

```bash
# Get all current issues from GitLab project
bash -c "source .env && curl -s -H \"PRIVATE-TOKEN: \${GITLAB_TOKEN}\" \
 \"\${GITLAB_URL}/api/v4/projects/\${PROJECT_ID}/issues?state=opened&per_page=100\" | \
 jq -r '.[] | \"\(.iid): \(.title)\"'"

# Get all issues (opened and closed) for comprehensive check
bash -c 'source .env && curl -s -H "PRIVATE-TOKEN: ${GITLAB_TOKEN}" \
     "${GITLAB_URL}/api/v4/projects/${PROJECT_ID}/issues?per_page=100" | \
     jq -r ".[] | \"\(.iid): \(.title) (Status: \(.state))\""'
```

**Deduplication Process:**
1. **Query All Existing Issues**: Get current GitLab issues (opened and closed)
2. **Compare Sprint Tasks**: Cross-reference sprint planning tasks with existing issue titles
3. **Compare User Stories**: Cross-reference product backlog entries with existing issues
4. **Filter Duplicates**: Remove any tasks/stories that already exist as GitLab issues
5. **Document Skipped Items**: Log which items were skipped due to duplication

**Issue Structure for API**:

**REFERENCE: Use Generation Template Structure**
- **For User Stories**: Use `user_story_format` from `.bmad-core/templates/gitlab-issues-tmpl.yaml`
- **For Sprint Tasks**: Use `sprint_task_format` from `.bmad-core/templates/gitlab-issues-tmpl.yaml`

The templates provide the exact JSON structure needed for GitLab API calls.

**CRITICAL NOTE**: Issues are organized by **milestone assignment only** - no sprint labels (like "sprint::3") should be used. The milestone_id field determines sprint organization and should be set to the appropriate sprint milestone in GitLab.

**Generate and Save Issues File:**
Create a JSON file containing all generated issues with complete API-ready structure for user verification before GitLab execution. **ALWAYS save in docs folder for organization.**

### Step 7: GitLab API Execution Using Generated File

**CRITICAL - MANDATORY USER INTERACTION**: Execute GitLab API commands using the verified issues file.

**IMPORTANT FILE MANAGEMENT**: 
- **All generated files MUST be saved in docs/ folder**
- **Default file location: docs/gitlab-issues-generated.json**
- **Scripts and temporary files: Save in root directory, but reference docs/ files**

**Present file-based execution plan to user and STOP for interaction:**

**Verified Issues File Ready for Execution:**
- **File location: docs/gitlab-issues-generated.json** (standard location in docs folder)
- File contains: [NUMBER] issues ready for GitLab creation
- File verified by user: [CONFIRMATION_STATUS]

**API Execution Plan:**
- Source file: [ISSUES_FILE_PATH]
- Total issues to create: [NUMBER]
- Target GitLab project: [PROJECT_URL]
- Assigned milestone: [MILESTONE_NAME]
- Estimated execution time: [TIME]

**Rationale:** Using the verified issues file ensures that only user-approved issues are created in GitLab. This provides a clear audit trail and prevents unwanted issue creation.

**STOP - Present numbered options 1-9:**
- **Option 1:** Execute API calls using the verified issues file
- **Option 2:** Clarify task requirements or modify descriptions
- **Option 3:** Adjust priority levels for specific issues
- **Option 4:** Review and modify team assignments
- **Option 5:** Change effort estimates (days) for tasks
- **Option 6:** Add or remove specific issues from the list
- **Option 7:** Modify component categorization or labels
- **Option 8:** Update sprint or milestone information
- **Option 9:** Cancel execution and start over
- End with: "Select 1-9 or type 'EXECUTE' to proceed with issue creation from file:"

**WAIT FOR USER RESPONSE** - Do not execute API calls until user explicitly authorizes.

**EXECUTE GitLab API commands using the verified issues file:**

Read the verified issues file and execute API calls for each issue:

```bash
# Read from verified issues file and execute API calls
ISSUES_FILE="docs/gitlab-issues-generated.json"  # Always use docs folder location

while IFS= read -r issue_json; do
  echo "Creating issue from file: $(echo "$issue_json" | jq -r '.title')"
  
  curl --header "PRIVATE-TOKEN: ${GITLAB_TOKEN}" \
       --header "Content-Type: application/json" \
       --data "$issue_json" \
       "${GITLAB_URL}/api/v4/projects/${PROJECT_ID}/issues"
       
  # Rate limiting - wait 1 second between requests
  sleep 1
done < <(jq -c '.[]' "$ISSUES_FILE")
```

### Step 8: Execution Verification and Error Handling

**Verify each issue creation:**
- Check API response for successful creation (HTTP 201)
- Capture created issue IID and URL
- Handle any API errors or permission issues
- Retry failed requests with exponential backoff

**Error Handling:**
- Invalid token: Prompt user to check token permissions
- Project not found: Verify project ID and access
- Milestone not found: Create milestone or prompt user
- Assignee not found: Verify user IDs and project access
- Rate limiting: Implement proper delays between requests

### Step 9: Post-Creation Actions

**After successful issue creation:**

1. **Update Project Status**: Document created issues in project-status.json for tracking
2. **Generate Summary Report**: Document all created issues with URLs
3. **Create Sprint Board**: Organize issues in GitLab project board if configured
4. **Notify Team**: Generate notification summary for team members

### Step 10: Documentation and Reporting

Generate comprehensive report including:

**Execution Summary**:
- Total issues created successfully
- Any failed creations with reasons
- GitLab project and milestone information
- Team assignment distribution

**Created Issues List**:
- Issue IID, title, and GitLab URL for each created issue
- Assigned apprentice and effort estimation
- Component and user story mapping
- Direct links for easy access

**Next Steps**:
- Instructions for apprentices to access assigned issues
- Mentor notification about new sprint issues
- Project agent synchronization status

### Step 11: Project Status File Generation

**CRITICAL - MANDATORY FINAL STEP**: Create or update project status file for PM agent tracking.

**CRITICAL: Load Execution Template**
Load the execution template for proper project status structure:
```bash
# Load execution template for project-status.json formatting
cat .bmad-core/templates/project-status.yaml
```
Use the template's `project_status_structure.json_format` for the project-status.json file structure.

**Present this requirement to user and STOP for interaction:**

**Project Status File Management:**

1. **File Location**: `docs/project-status.json`
2. **File Handling**: 
   - **If file does NOT exist**: Create new project-status.json
   - **If file exists**: Update existing project-status.json with new information
3. **Purpose**: Enable pm-agent to track project status and provide updates
4. **Content**: Complete sprint execution summary with GitLab integration and detailed issue tracking

**REFERENCE: Use Execution Template Structure**
Use the complete JSON format from `.bmad-core/templates/project-status.yaml` under `project_status_structure.json_format`.

The execution template provides the exact project-status.json structure with all required fields for PM agent tracking.

**CRITICAL INTEGRATION NOTES**:
- **PM Agent**: Will read this file to provide status updates and track progress
- **Future Tasks**: This task will check for existing status file before running
- **Status Tracking**: Enables project-wide status monitoring

**GitLab API Queries for Issue Status Tracking:**

```bash
# Get detailed information for all issues (for issue tracking section)
bash -c 'source .env && curl -s -H "PRIVATE-TOKEN: ${GITLAB_TOKEN}" \
     "${GITLAB_URL}/api/v4/projects/${PROJECT_ID}/issues?per_page=100" | \
     jq -r ".[] | {
       id: .iid,
       title: .title,
       state: .state,
       assignee: (.assignee.name // \"Unassigned\"),
       created_at: .created_at,
       updated_at: .updated_at,
       closed_at: .closed_at,
       web_url: .web_url,
       labels: .labels,
       milestone: (.milestone.title // null)
     }"'

# Get merge requests associated with issues (for merge review tracking)
bash -c 'source .env && curl -s -H "PRIVATE-TOKEN: ${GITLAB_TOKEN}" \
     "${GITLAB_URL}/api/v4/projects/${PROJECT_ID}/merge_requests?state=all&per_page=100" | \
     jq -r ".[] | select(.description | contains(\"Closes #\") or contains(\"Fixes #\")) | {
       merge_request_iid: .iid,
       title: .title,
       state: .state,
       created_at: .created_at,
       merged_at: .merged_at,
       web_url: .web_url
     }"'

# Map issue states to sprint board states:
# - "opened" → "open" or "in-progress" (based on labels or assignee activity)
# - Issues with "doing" label → "doing" 
# - "closed" → "closed"
# - Check for recent activity to determine if "in-progress"
```

**GitLab Issue Status Mapping Logic:**
- **open**: GitLab state "opened" and no activity/assignee
- **sprint-backlog**: GitLab state "opened" with sprint milestone but unassigned
- **in-progress**: GitLab state "opened" with assignee and recent activity
- **doing**: Issues with "doing", "in-progress", or "wip" labels
- **closed**: GitLab state "closed"

**Status Determination Priority:**
1. GitLab issue state (opened/closed)
2. GitLab labels (doing, wip, in-progress override other indicators)
3. Assignee status (assigned = in-progress if recent activity)
4. Milestone assignment (sprint-backlog if in sprint but unassigned)

**Rationale:** The status file provides centralized tracking that enables the PM agent to monitor project progress, provide status updates, and coordinate next steps without re-executing the entire workflow.

**STOP - Present numbered options 1-9:**
- **Option 1:** Generate project status file with extracted information
- **Options 2-9:** [Select 8 methods from data/elicitation-methods]
- End with: "Select 1-9 or confirm status file generation:"

**WAIT FOR USER RESPONSE** - Do not proceed until user authorizes status file creation.

## GitLab API Integration

### Prerequisites Setup

**Environment Variables (in .env file)**:
```bash
GITLAB_URL="https://gitlab.com"  # or your GitLab instance
GITLAB_TOKEN="your-personal-access-token"
PROJECT_ID="your-project-id"
```

**Token Permissions Required**:
- `api` scope for full API access
- `read_user` for user information
- `write_repository` for issue creation

**Quick Test**:
```bash
source .env && curl -s -H "PRIVATE-TOKEN: $GITLAB_TOKEN" "$GITLAB_URL/api/v4/projects/$PROJECT_ID" | jq .name
```

### API Commands Template


**Bulk Issue Creation Script**:
```bash
#!/bin/bash
# bulk_create_sprint_issues.sh

source_issue_data="sprint_issues.json"
failed_issues=()
created_issues=()

while IFS= read -r issue_json; do
  echo "Creating issue: $(echo "$issue_json" | jq -r '.title')"
  
  response=$(curl --silent --show-error \
                  --header "PRIVATE-TOKEN: ${GITLAB_TOKEN}" \
                  --header "Content-Type: application/json" \
                  --data "$issue_json" \
                  "${GITLAB_URL}/api/v4/projects/${PROJECT_ID}/issues")
  
  if echo "$response" | jq -e '.iid' > /dev/null; then
    issue_iid=$(echo "$response" | jq -r '.iid')
    issue_url=$(echo "$response" | jq -r '.web_url')
    created_issues+=("$issue_iid:$issue_url")
    echo "✅ Created issue #$issue_iid: $issue_url"
  else
    error_msg=$(echo "$response" | jq -r '.message // "Unknown error"')
    failed_issues+=("$(echo "$issue_json" | jq -r '.title'):$error_msg")
    echo "❌ Failed to create issue: $error_msg"
  fi
  
  # Rate limiting - wait 1 second between requests
  sleep 1
done < <(jq -c '.[]' "$source_issue_data")

echo "
📊 SUMMARY:
- Created: ${#created_issues[@]} issues
- Failed: ${#failed_issues[@]} issues
"
```




## CRITICAL REMINDERS

**❌ NEVER:**

- Execute API calls without explicit user authorization
- Assume configuration values or credentials
- Proceed with issue creation without user verification
- Skip the mandatory 1-9 elicitation format when user input is required

**✅ ALWAYS:**

- Use exact 1-9 format when user interaction is required
- Wait for user response before proceeding with each critical step
- Present detailed rationale explaining decisions and risks
- End with "Select 1-9 or just type your question/feedback:"
- Verify all configuration before API execution

## Key Principles

- **Execution Excellence**: Actually create issues in GitLab, don't just generate templates
- **Error Resilience**: Handle all common API errors gracefully
- **Progress Transparency**: Show real-time progress during issue creation
- **Verification**: Confirm each issue creation and provide URLs
- **Integration**: Update project-status.json for comprehensive tracking
- **User Experience**: Provide clear summaries and next steps
- **Mandatory Interaction**: Follow elicitation workflow for all critical decisions