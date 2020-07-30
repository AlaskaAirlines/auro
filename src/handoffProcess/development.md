# Development story

The role of the development story is the story assigned to the developer that will use the design spec to create the coded version of the design asset for the design system. 

This story will have the baseline specification definition as well as a checklist of deliverables. 

## Assignees 

The primary developer working on this story will be initially assigned. A reviewing developer will be assigned to this story to ensure a quality deliverable. 

## Labels 

Please be sure to address the following label expectations for story management. 

1. Project. Please be sure to assign the proper Epic project if applicable
1. Status. Either `Backlogged`, `Work In Progress` or `Complete / Ready to Merge`
1. Type. For these stories, please use `Feature`

Please see [Managing labels](https://auro.alaskaair.com/getting-started/handoff/labels) for more details regarding the use of Github labels. 

## Example

```
# User story

As a [persona], I want to be able to [intent, not feature(s)], so I can [describe benefit].

## Outline subtasks or tasks

> List specific steps required to deliver this work.

- [ ] Address all design and UX as proposed in the design comp in relation to using Auro specifications 
- [ ] A11y in regards to role and live notifications need to be coded into the final WC
- [ ] Review demo with the designer as well as the Auro team
- [ ] All new work to be reviewed by Auro team

## Definition of “Done” (exit criteria)

> The story is generally “done” when the user can complete the outlined task, but make sure to define what that is.

#### Has been tested in all browsers

- [ ] Chrome
- [ ] Firefox
- [ ] Edge (79 +)
- [ ] Safari
- [ ] Mobile Safari
- [ ] IE11

#### Has been tested for accessibility

- [ ] Screenreader
- [ ] Axe
- [ ] Keyboard use

#### Performance 

- [ ] Chrome Lighthhouse report 

#### Auro component features

- [ ] README doc completed with all relative information 
- [ ] API documentation created
- [ ] Bundled version tested and documented
- [ ] Examples and use case info created
- [ ] Pages added to the Auro Doc Site


## Audit

[link to parent audit if applicable]
```

Github's markdown supports a `checkbox` feature where users of the stories can checkoff items as they are completed. 

The REVIEW and SYMBOLIZING stories will have links to their respective child story. 

## Expectations

The expectation of this type of story is that assignees will check-off the items in the lists as they are completed. 

When the story is actively being worked on, an assignee is responsible for updating the label to `Status: Work In Progress` and please make sure that the story is in the `Current WIP Release` kanban column. Both these actions can be managed via the controls on the story page itself. 

## Handoff for code review

When the primary developer has completed their work, they are to create a PULL REQUEST and invite a senior Auro engineer to the review process. 

## Closing the story

Please see [Closing stories](https://auro.alaskaair.com/getting-started/handoff/close) for specific information.
