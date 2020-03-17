# Auro Governance Working Agreement

The Auro Governance Working Agreement is mainly an agreed-upon process for when and how new assets will be added to the Auro Design System.

## New work discovered

Within the scope of a Product Team, new work is created. Engineers and Product designers will review the specification of the feature and determine where new work must happen.

In regards to design, the Product Designer will look to the Auro Design System for opportunities of use.

## Does a component exist?

At this point, the Product Team is looking to the Auro Design System for assets to use. And per each UI component they need, they will ask, "*Does this component exist?*"

#### YES - there is an existing component

Yes, there is an existing asset that can be used, but **does it meet their requirements**?

* **YES** - then the team can get to work without additional effort.
* **NO** - then the Product Team will propose either a new component or an update to an existing component.

#### NO - there is no useable component

From the Product Team's research, there is not an available asset for their use, so the Product team will **propose the work to the Design System team**.

### Propose new work to the Design System team

At this step, the idea is to better understand the requirements of the Product Team. There may be an opportunity to leverage other assets that the Product Team did not see as opportunities. There may also be an opportunity here to extend the functionality of an existing component to meet the Product Team's requirements.

If the determination is that no additional work needs to happen, the Product Team can move forward leveraging existing assets.

If it is determined that new work is to happen, **is the new work unique to this team**?

* **YES** - If the determination is that the work needed by the Product Team is not feasible to be added to existing assets or the new work is considered a value add to the Design System, then the Product Team is encouraged to move forward and deliver a solution that is unique to their project.
* **NO** - This determination means that this work is considered best included with the Auro Design System and work is to be added to the Design System backlog.

## Design System Backlog

Once all the previous steps have been completed and all discussions have been had between the Product Team and the Auro Design System team, the new work can be written up and added to the Design System backlog.

### Design and Product collaborate

At this phase of the proposed project, the Product Team will work with the Design System team to ensure that the new component will meet the spec for the Product Team as well as the Design System.

### Formal design and dev process begins

At this phase, the Product Team and the Auro Design System team will collaborate on completing the work.

Depending on the scope of the work and available resources the work may be:

* 100% addressed by the Auro team,
* the work could be divided between teams,
* the work maybe 100% addressed by the Product team with oversight of the Auro team.

This phase is considered complete once a new design specification asset has been produced and there is a coded version of the design spec is prepared for review.

### Design asset and code review

In this phase, the work from the previous phase is carefully reviewed by designers and engineers who were NOT part of the asset creation process.

This process includes:

* A Sr. Designer and an Auro engineer ensure that the delivered assets meet the specification outlined in the previous steps of the process.
* Design asset is reviewed by a Sr. Designer to ensure that the asset is compliant with the standards set forth.
* The code is reviewed by an engineer on the Auro team to ensure that all work is compliant with the standards set forth.

It is also the responsibility of the reviewers to ensure that the new work lives up to the [quality threshold determined by the Auro Design System](https://github.com/AlaskaAirlines/auro_docs/blob/master/src/WORKING_AGREEMENT.md).

This part of the process answers the question; **Does the demo pass review**?

* **YES**. The team moves on to complete and deliver the work
* **NO**. The teams iterate on feedback and prepare for the next review

### Complete docs and final demo

At this phase of the work, the teams will collaborate to deliver all the final assets needed for publishing the new component.

* The design assets are finalized and prepared to be merged in with the MASTER branch of the UIKit and distributed to all the product teams.
* The coded asset is completed, all supporting documentation is completed (specific to a repo and any updates to the Doc site are addressed as well).

### Final work published

This is the RELEASE or DELIVERY phase of the work. Here it has been determined that all assets (design, documentation, code, etc) have been produced and approved for distribution.

* UIKit update released
* npm published

### Designers and devs use the new asset

Once all the new work has been published, it is now officially in the hands of the designers and engineers to use. It is with active use that any edge cases not discovered during the design and development process will the discovered.

As these edge cases are discovered it is to be determined whether the discovery is **considered a new feature or a bug**.

* **BUG**. An issue is submitted with all the necessary details and the label of BUG and is given top priority to address.
* **NEW FEATURE**. An issue is submitted with a feature request and proposed solution. The new feature will be reviewed by the Auro team and in coordination with the submitter determine appropriate timelines for work.




## Visualize the process

The following is a flow-chart intended to assist in the visualization of this Governance model.

![](https://mermaid.ink/img/eyJjb2RlIjoiZ3JhcGggVERcbkFbUHJvZHVjdCBuZWVkcyBuZXcgd29ya10gLS0-IEJ7RG9lcyB0aGUgPGJyPmNvbXBvbmVudCBleGlzdD99XG5CIC0tPnxZZXN8IER7RG9lcyBpdCBtZWV0IHRoZTxicj5mdWxsIHJlcXVpcmVtZW50cz99XG5EIC0tPnxOb3wgQ1xuQiAtLT58Tm98IENbUHJvZHVjdCBhbmQgRFMgdGVhbSA8YnI-ZGlzY3VzcyBmdWxsIHJlcXVpcmVtZW50c11cbkQgLS0-IHxZZXN8IEVbTGV2ZXJhZ2UgZXhpc3RpbmcgYXNzZXRzXVxuQyAtLT4gRntEb2VzIG5ldyB3b3JrPGJyPm5lZWQgdG8gaGFwcGVuP31cbkYgLS0-IHxOb3wgRVxuRiAtLT4gfFllc3wgR3tJcyB0aGUgd29yayB1bmlxdWU_fVxuRyAtLT4gfFllc3wgSFtQcm9kdWN0IHRlYW0gZG9lcyB0aGUgd29ya11cbkcgLS0-IHxOb3wgSVtBZGQgaXRlbSB0byBEUyBiYWNrbG9nXVxuSSAtLT4gSltEZXNpZ24gYW5kIFByb2R1Y3Q8YnI-Y29sbGFiIG9uIGl0ZXJhdGU8YnI-b24gc3BlY3MsIHByb2R1Y2UgYXNzZXRzXVxuSiAtLT4gS1tGb3JtYWwgZGVzaWduIGFuZCA8YnI-ZGV2ZWxvcG1lbnQgcHJvY2VzcyBiZWdpbnNdXG5LIC0tPiBMW0RTIFN5bWJvbCBjcmVhdGVkLDxicj4xc3QgZHJhZnQgZGVtbyBjcmVhdGVkLDxicj5yZXZpZXcgd2l0aCBEUyBhbmQgUHJvZHVjdCB0ZWFtXVxuTCAtLT4gTXtEb2VzIGRlbW88YnI-cGFzcyByZXZpZXc_fVxuTSAtLT4gfE5vfCBPW1RlYW1zIGl0ZXJhdGUgb24gZmVlZGJhY2tdXG5NIC0tPiB8WWVzfCBQW0NvbXBsZXRlIGRvY3VtZW50YXRpb24sPGJyPnByb2R1Y2UgZGVtbyBmb3IgcmVsZWFzZV1cblAgLS0-IFFbRGVzaWduIHdvcmsgbWVyZ2VkIGludG8gVUlLaXQsPGJyPm5ldyBXQyBwdWJsaXNoZWRdXG5RIC0tPiBSW1Byb2R1Y3QgRGVzaWduZXIgdXBkYXRlcyBVSUtpdCw8YnI-ZW5naW5lZXIgYWRkcyBuZXcgY29tcG9uZW50XVxuUiAtLT4gU3tCdWdzIG9yPGJyPm1pc3NpZ24gZmVhdHVyZT99XG5TIC0tPiB8QlVHfCBVW0lzc3VlIHN1Ym1pdHRlZCB3aXRoPGJyPmhpZ2ggcHJpb3JpdHkgZm9yPGJyPnJldmlldyBhbmQgcmVzb2x1dGlvbl1cblMgLS0-IHxGRUFUVVJFfCBUW0lzc3VlIHN1Ym1pdHRlZCB0byByZXBvPGJyPmZvciByZXZpZXcgYnkgdGhlIDxicj5BdXJvIERTIFRlYW1dIiwibWVybWFpZCI6eyJ0aGVtZSI6ImRlZmF1bHQifSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)

<!-- [Editor][1] -->

[1]: https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoiZ3JhcGggVERcbkFbUHJvZHVjdCBuZWVkcyBuZXcgd29ya10gLS0-IEJ7RG9lcyB0aGUgPGJyPmNvbXBvbmVudCBleGlzdD99XG5CIC0tPnxZZXN8IER7RG9lcyBpdCBtZWV0IHRoZTxicj5mdWxsIHJlcXVpcmVtZW50cz99XG5EIC0tPnxOb3wgQ1xuQiAtLT58Tm98IENbUHJvZHVjdCBhbmQgRFMgdGVhbSA8YnI-ZGlzY3VzcyBmdWxsIHJlcXVpcmVtZW50c11cbkQgLS0-IHxZZXN8IEVbTGV2ZXJhZ2UgZXhpc3RpbmcgYXNzZXRzXVxuQyAtLT4gRntEb2VzIG5ldyB3b3JrPGJyPm5lZWQgdG8gaGFwcGVuP31cbkYgLS0-IHxOb3wgRVxuRiAtLT4gfFllc3wgR3tJcyB0aGUgd29yayB1bmlxdWU_fVxuRyAtLT4gfFllc3wgSFtQcm9kdWN0IHRlYW0gZG9lcyB0aGUgd29ya11cbkcgLS0-IHxOb3wgSVtBZGQgaXRlbSB0byBEUyBiYWNrbG9nXVxuSSAtLT4gSltEZXNpZ24gYW5kIFByb2R1Y3Q8YnI-Y29sbGFiIG9uIGl0ZXJhdGU8YnI-b24gc3BlY3MsIHByb2R1Y2UgYXNzZXRzXVxuSiAtLT4gS1tGb3JtYWwgZGVzaWduIGFuZCA8YnI-ZGV2ZWxvcG1lbnQgcHJvY2VzcyBiZWdpbnNdXG5LIC0tPiBMW0RTIFN5bWJvbCBjcmVhdGVkLDxicj4xc3QgZHJhZnQgZGVtbyBjcmVhdGVkLDxicj5yZXZpZXcgd2l0aCBEUyBhbmQgUHJvZHVjdCB0ZWFtXVxuTCAtLT4gTXtEb2VzIGRlbW88YnI-cGFzcyByZXZpZXc_fVxuTSAtLT4gfE5vfCBPW1RlYW1zIGl0ZXJhdGUgb24gZmVlZGJhY2tdXG5NIC0tPiB8WWVzfCBQW0NvbXBsZXRlIGRvY3VtZW50YXRpb24sPGJyPnByb2R1Y2UgZGVtbyBmb3IgcmVsZWFzZV1cblAgLS0-IFFbRGVzaWduIHdvcmsgbWVyZ2VkIGludG8gVUlLaXQsPGJyPm5ldyBXQyBwdWJsaXNoZWRdXG5RIC0tPiBSW1Byb2R1Y3QgRGVzaWduZXIgdXBkYXRlcyBVSUtpdCw8YnI-ZW5naW5lZXIgYWRkcyBuZXcgY29tcG9uZW50XVxuUiAtLT4gU3tCdWdzIG9yPGJyPm1pc3NpZ24gZmVhdHVyZT99XG5TIC0tPiB8QlVHfCBVW0lzc3VlIHN1Ym1pdHRlZCB3aXRoPGJyPmhpZ2ggcHJpb3JpdHkgZm9yPGJyPnJldmlldyBhbmQgcmVzb2x1dGlvbl1cblMgLS0-IHxGRUFUVVJFfCBUW0lzc3VlIHN1Ym1pdHRlZCB0byByZXBvPGJyPmZvciByZXZpZXcgYnkgdGhlIDxicj5BdXJvIERTIFRlYW1dIiwibWVybWFpZCI6eyJ0aGVtZSI6ImRlZmF1bHQifSwidXBkYXRlRWRpdG9yIjpmYWxzZX0
