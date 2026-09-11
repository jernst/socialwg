# 2026-09-04 Joint WG/CG Series A
Meeting to be held 10:00 Eastern Daylight Time (14:00 UTC)

# Attendees

- Darius Kazemi, WG Chair
- David Roetzel
- Matthias Pfefferle
- a <trwnh.com>
- Ryan Barrett snarfed.org
- Johannes Ernst https://j12t.org, CG co-chair
- Dmitri Zagidulin
- [Ted Thibodeau Jr](https://www.linkedin.com/in/macted/) (he/him) (OpenLinkSw.com) // GitHub:[@TallTed](https://github.com/TallTed) // Mastodon:[@TallTed](https://mastodon.social/@TallTed)
(counting 14 people)

## Agenda

* Administrivia
  * Scribe volunteer(s)? Ryan
  * Reminders: 
     * [Working Group Membership](https://www.w3.org/groups/wg/social/) and [Community Group Membership](https://www.w3.org/groups/cg/socialcg/)
     * [CG/WG incubation process](https://github.com/swicg/potential-charters/blob/main/stage-process.md)
     * [W3C Code of Conduct](https://www.w3.org/policies/code-of-conduct/)
* Welcome
* Brief introductions as necessary
* LOLA Draft as CG Report? (Johannes/Lisa)
* Extensions policy (Evan)
  * https://swicg.github.io/extensions-policy/
* Alternative Identifiers (Ryan/bumblefudge)
* WG updates (Darius)
* Task force updates (Dmitri/Johannes)
* Any Other Business (AOB)

## Minutes

### LOLA Draft as CG Report? (Johannes/Lisa) https://swicg.github.io/activitypub-data-portability/lola

- Johannes: propose to publish it as a CG draft
- Evan: do we have group will to work on this and move it forward? and high level, do we think it's the right idea?
- We have two implementations, DTI and Emissary
- Bumblefudge: doesn't need to be the only data portability method, we just need to support it. Doesn't have to be overly normative
- Ryan: it's AP and AS idiomatic, fits
- Lisa is ready to continue supporting it and moving it forward

PROPOSAL: publish as draft?
6 +1s, no objections


### Extensions policy (Evan) https://swicg.github.io/extensions-policy/

Came in via transfer, we've made small revisions
- Would add to https://www.w3.org/ns/activitystreams#extensions
> Process and criteria for extensions approval is being finalised and will be described or linked to here in due course.
- Misc terms doc https://swicg.github.io/miscellany/ is the first testbed extension for this policy
- Now that the WG is open, CG may not be the right owner. WG instead?
- Ryan: could we do both?
- a: keep extension policy/context w/CG authority? have a CG context governed by the community
- Ryan/Dmitri: not a unique problem for us. W3C has struggled with this before.
    - Evergreen registry idea https://www.w3.org/policies/process/#registries works but is new and overly heavyweight
    - CCG has done a lot of this
    - Contexts published by WGs should be immutable
    - Proposal: both fixed WG context and ongoing CG context?
- Evan: let's continue iterating on this
- a: Security v1 is an example of a well-known context that could be added to a registry but not to the normative context
- Evan: adding security terms would be helpful!
    - Should WG just adopt misc terms directly? it wouldn't be the guinea pig/test for extension policy then. Which is maybe fine
        - a: WG can have that conversation but CG imo can move on its own a bit 


### Alternative Identifiers (Ryan/bumblefudge)

- Ryan: AP right now is effectively HTTP based, but not a MUST. We probably don't want to specify others, but want to enable people to try others. Bumblefudge suggested to work on use cases first.
- Bumblefudge: yes, AP v1.1 should probably just clarify the existing state. v2 could maybe change more drastically?
- Let's do a call (or thread etc) on user stories? Maybe incubate in CG
- Evan: Sounds like a TF!
- Dmitri: revive portability TF?
- Bumblefudge: worried that we don't quite know what this is yet
- Others: TFs don't need to be too heavy or formal. OK for them to evolve!

Next step is an exploratory call. Bumblefudge will host.


### WG updates (Darius) https://github.com/w3c/socialwg/blob/main/meetings/2026/2026-08-27-WG-AP-suite.md

- Last mtg:
    - HTTP vs other transports
    - Actor definition(s)
    - ...


### Task force updates (Dmitri/Johannes)

- Johannes: TF inventory! https://github.com/jernst/meetings/blob/pr-tf-table/DELIVERABLES-TASKFORCES.md
    - API: no mtg
    - Data portability: already discussed
    - HTML Discovery: no mtg
    - E2EE: proposed taking MLS doc to draft. Didn't reach consensus, need more qualified people involved. https://pad.w3.org/p/ActivityPub_E2EE_Task_Force_25_Aug_2026
    - Forums: has list of FEP candidates to write
    - Geo: ?
    - Groups: ongoing
    - Handles: scheduling first mgt
    - HTTP Sigs: published report as final. Tracking support for RFC9421 https://swicg.github.io/activitypub-http-signature/RFC9421
        - Broad support for re-establishing TF but need a volunteer to run it
    - Remix: ?
    - Trust & Safety: Victor and Echo can take over
    - Web site: want to overhaul https://activitypub.rocks/
- Johannes will continue maintaining TF table and publicize it


### Any other business

- FediForum in Oct! https://fediforum.org/
- Oct 24/30: TPAC in Dublin
