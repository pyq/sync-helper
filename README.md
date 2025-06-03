# sync-helper

## Setup script
```
uv venv
source .venv/bin/activate
uv sync
```

## User Interaction Flows

### Flow 1: Daily Sync Generation
**Trigger**: User types `@sync start`
**Goal**: Generate a personalized daily standup script

#### Step 1: Initial Context Gathering
- **Action**: Slack modal opens with structured form
- **Inputs**: 
  - What I have done
  - What I will do
  - Any blockers or dependencies
- **UX**: Clean, tabbed interface with optional fields marked clearly

#### Step 2: AI Processing & Follow-up
- **Action**: Submit initial info to AgentHub API (http://anyon-api/api/v1 with api-key proivided)
- **Response**: AI analyzes context and generates targeted follow-up questions
- **Examples**:
  - "You mentioned a blocker with the API - do you need help from a specific team member?"
  - "Your priority includes testing - what type of testing are you focusing on?"
- for each agenthub communication, we will create a session for each sync update.

#### Step 3: Dynamic Q&A Session
- **Action**: Present follow-up questions in conversational style
- **UX**: Chat-like interface within Slack modal


#### Step 4: Script Generation & Refinement
- **Action**: AI generates 30-60 second speaking script
- **Output**: 
  - Structured script with clear talking points
  - Estimated speaking time
  - Key phrases highlighted

#### Step 5: Delivery & Feedback
- **Actions**:
  - Copy to clipboard