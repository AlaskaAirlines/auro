# Design System working agreement

The purpose of this document is to illustrate the process from which new components may be added to the design system.

## Acceptance criteria

For any submission to the design system to be accepted, this contribution must meet a very specific set of criteria, that includes, but not limited to:


#### Design Criteria

- [ ] Does not replicate any existing design or functionality
- [ ] Must include mobile responsive experiences
- [ ] Must include accessibility experiences
- [ ] Must include contingency experiences
- [ ] Must meet all accessibility design standards
- [ ] All specifications and interactions are defined and documented
- [ ] All documentation should be approved by copywriter
- [ ] Work has been approved by peer review on new feature branch
- [ ] Engineering has been consulted prior to any peer review submission


#### General Engineering Criteria

- [ ] All functionality must meet minimal automated testing standards
    - Unit, acceptance, and integration tests added
    - No performance degradation
    - Logging, monitoring, and alerting are in place and up to date
- [ ] Work has been approved via techniocal peer review on new feature branch (Two sets of eyes on all code)
- [ ] Design has been consulted prior to any peer review submission (Final design review with designer)
- [ ] Must meet all accessibility standards (All guest-facing and employee-facing experiences are accessible)
- [ ] The change has a story, the commit comments reference the story and the change is recorded
- [ ] Must comply with the internal OSS Secure Software Development Standard

#### General Business Criteria

- [ ] When business is impacted, the change is measurable and existing measurements continue to work
- [ ] Has been tested/validated/approved by peers and subject to external testing if applicable
- [ ] Product Manager confirms acceptance criteria is met

#### Design System Criteria

- [ ] Must meet mobile-first support criteria
- [ ] All applicable design elements must use approved design tokens
- [ ] Any content structure must meet all SEO specifications
- [ ] All supporting documentation must be submitted with new work
- [ ] If applicable, full API must be documented
- [ ] If applicable, a full demonstrative version of new work must be added to the supporting documentation web site

## Submission workflow

Design and engineering work are not independent cycles. It will be considered non-compliant if one part of the process is committed and released before it's complimentary submission.

This workflow intends that neither designers nor engineers will have access to any new submission until all parts have been completed and approved and are ready for consumption by the organization as a whole.

### Identify problem to be solved

Prior to any work submission, the work must meet a basic criteria to assure that the effort is warranted and will be accepted into the design system.

- [ ] Problem is not already solved by other means of existing functionality and/or design
- [ ] Problem must be a valid use case across multiple projects and experiences
- [ ] Proposed solution to problem does not cause side-effects on any pre-existing scenarios

### Work submission process

The following is a baseline for a work submission process to ensure that the proposed work is compliant with all the standards as stated prior.

- [ ] Problem identified and proposed solution has been accepted
- [ ] Initial design work meets all previously stated criteria
- [ ] Engineering has been consulted for feedback prior to handoff
- [ ] Approved design work is communicated to engineering
- [ ] Initial engineering work meets all previously stated criteria
- [ ] Engineering reviews all work with design

### Approval for distribution

It is only once design and engineering have completed all the steps as outlined above and ensures that all design, documentation, feature(s) and functionality meet the defined specification, that either the design or engineering work will be merged into master branches and distributed for use across the organization.

Any outliers to this process will constitute non-compliant actions and any distributed work will be reverted and removed from general distribution.
