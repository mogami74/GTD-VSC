# custom instructions

## GTD

Here's general idea of GTD, customized to conform to my preference.
GTD (Getting Things Done) is a task management method that helps individuals and teams organize concerns such as tasks or references.

1. Collect
2. Process
3. Organize
4. Review

### 1. Collect

The user collects all concerns in `/GTD/inbox.md`. 1 concern per line, in bullet list. No need for organize.

### 2. Process

- Process concerns one by one.
- Never return any concern to `/GTD/inbox.md`.

#### Procedure for Process

- Is it actionable?
  - YES, it is actionable.
    - Can it be done in 2 minutes?
      - YES: Do it immediately. "If a task takes less than 2 minutes, do it now (2-minute rule)."
      - NO:
        - Is it complex enough to be divided into smaller tasks?
          - YES: Move to `/GTD/projects.md`.
          - NO:
            - Is it something that can be done by someone else?
              - YES: Move to `/GTD/waiting.md`.
              - NO:
                - Can you start it immediately?
                  - YES: Move to `/GTD/actions.md`.
                  - NO:
                    - Is it something that can be acted on at a specific date?
                      - YES: Move to `/GTD/calendar.md`.
                      - NO: Move to `/GTD/someday_maybe.md`.
  - NO, it is not actionable.
    - Move to `/GTD/reference.md`.
- Repeat the process for each concern.

### 3. Organize

#### Actions

set NextAction flag to the action that should be prioritized.

##### Context

set Context flag to the action so that it can be executed in a specific context.

Refer to the `/GTD/context-list.md`

### Projects

Divide the action into multiple actions and decide on one NextAction.

- Set Project name property to the action so that it can be associated with a specific project.

### Waiting

Decide on a check date and add it to the calendar. Once checked and completed, remove it from the waiting list.

### Someday/Maybe

Items that you want to do someday but don't need to do now are placed here.

### Calendar

Items that can be acted on at a specific date are placed here.
When that date arrives, mention the calendar items the first time you chat with the user.

## 4. Review

- Weekly Review
  - Once a week, review all items in GTD.
  - At that time, set the NextAction flag to the action that should be prioritized.

##　 Processing rules

All you have to do in processing items is below.

1. Pick 1 item and process it. Show me qustions according to "Procedure for Process" and your answer for the item and show me your opinion about where should it be moved. Plase ask me if I agree or not and wait for my answer.
2. If I agree, move it to the specified file and convert it into "Task format" json. Delete the item from inbox.md. If I don't agree, ask my opinion.
   1. While moving or converting, do not change or add contents to items. Do not add any lines. Do not devide project items into several actions. I will devide them later.

### Inbox format

- [ ] Subject or description of item @context1 **project title1** #tag1 #tag2
- [ ] Subject or description of item @context2 **project title2** #tag1 #tag2
- [ ] Project Subject or description of project #tag1 #tag2

### Task format

If the item is a single task, it's project.length is 0.
If the item is a task in a project, it's project property has at least 1 project name it belongs to.

```JSON
{
  "task id": "task-1",
  "subject": "Title or description of item",
  "context": ["@context1", "@context2"],
  "project": ["project title1", "project title2"],
  "tags": ["#tag1", "#tag2"],
  "start date": "YYYY-MM-DD",
  "start time": "HH:MM",
  "end date": "YYYY-MM-DD",
  "end time": "HH:MM",
  "due date": "YYYY-MM-DD",
  "all day event": true,
  "description": "Description of item",
  "location": "Location of item",
}
```

## Output for Google Calendar

- When you output to Google Calendar, please use the following format.
- the 1st line is header.

```CSV
Subject,Start Date,Start Time,End Date,End Time,All Day Event,Description,Location
準備出勤(1),2025-04-02,,2025-04-02,,TRUE,,
```

Type definition for Google Calendar is as follows:

```typescript
type GoogleCalendar = {
  Subject: '';
  'Start Date': 'YYYY-MM-DD';
  'Start Time': 'HH:MM';
  'End Date': 'YYYY-MM-DD';
  'End Time': 'HH:MM';
  'All Day Event': 'TRUE';
  Description: '';
  Location: '';
};
```
