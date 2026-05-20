# SocialWeb CG and WG Joint Call

Meeting to be held 10:00 Eastern Daylight Time (14:00 UTC)

## Agenda

* Administrivia
  * Scribe volunteer(s)? (Evan)
  * Reminders: 
     * [Working Group Membership](https://www.w3.org/groups/wg/social/) and [Community Group Membership](https://www.w3.org/groups/cg/socialcg/)
     * [CG/WG incubation process](https://github.com/swicg/potential-charters/blob/main/stage-process.md)
     * [W3C Code of Conduct](https://www.w3.org/policies/code-of-conduct/)
* Welcome (Darius & Dmitri)
* Brief introductions as necessary
* Task force updates
* WG updates
  * Status of Drafts for ActivityPub, ActivityStreams core, and Activity Vocabulary ([Stage 2](https://github.com/swicg/potential-charters/blob/main/stage-process.md#stage-2-formalization-community-group) of incubation process)
* T&S discussion (Emelia)
* Task force for internationalization of handles (Emelia)
* Any Other Business (AOB)


## Attendees

- Evan Prodromou <acct:evanprodromou@socialwebfoundation.org>
- a <trwnh.com>
- David Roetzel (Mastodon)
- PLH
- bumblefudge.com
- [Ted Thibodeau Jr](https://www.linkedin.com/in/macted/) (he/him) (OpenLinkSw.com) // GitHub:[@TallTed](https://github.com/TallTed) // Mastodon:[@TallTed](https://mastodon.social/@TallTed)
- Andy Piper <acct:andypiper@macaw.social>
- Dmitri Zagidulin
- Ryan Barrett
- Emelia Smith
- Darius Kazemi
- Chris Harrelson
- Jim DeLaHunt <acct:jdlh@mstdn.ca>
- 

## Minutes

- DK: Welcome, A series meeting, B series is offset 2 weeks
    - EP is scribe 👋🏼
    - CLA or WG agreements please for all substantive contributions
    - Incubation from CG to WG
    - Code of conduct

### Introductions

- Jim DeLaHunt: interests in i18n of Fediverse handles, new CG member
- Bumblefudge: new grant, can be more participative in task forces

### Task Force updates

- Evan: Groups TF had its first ever meeting, very interesting, central dynamic involved discussion of https://w3id.org/fep/1b12 which is a simpler model based only on Announcing things to followers
- a: Groups TF wants to cover managing join/leave process for groups, invitations, expulsions. Similar to how Forums TF organizes posts together, we want to organize members together. Members separate from followers (should be able to support either without the other). Please look over repo and file issues for additional user stories; we are working on state diagrams for membership management proposals

- ES: Trust and Safety TF
    - No Grant so far, waiting on NLNet
    - Behind on writing docs, we need contributors!
    - Co-lead sought! Must have understanding of trust and safety (not necessarily just technical, also legal, social, and policy)
    - Inviting other TF members to show up to our meetings too, wherever their concerns align with ours; horizontal review but be respectful of our time and we can try to help. Please open an issue on our issue tracker stating the issue area and asking we place it on our agenda.
    
### Participation without CLA?

- Evan: another concern was with pseudonymous and anonymous participation, how do we include people and their feedback without requiring them to leak their id via CLA?
    - DK: ideas can start outside the CG, and get brought in by someone who spans those two groups
- a: pseudonymous persons already participate?
    - DK: Let's say that someone doesn't want to participate for some reason
- ES: can we push this to W3C? plh? Many groups outside Social are by professionals using their real name at work.
- plh: we have a process for this
- ES: document?
- plh: can get it
- ES: we should add this to agendae
- Bumblefudge: 
- plh: You can participate indirectly via someone who has signed the CLA? We really want everything done in our CG/WG to be royalty free so there is no way around that.
- Emelia: Can FEPs include an IPR? FEPs are already CC0 public domain.
- Darius: Need to run this by W3C legal
- Bumblefudge: CC0 is license free, not patent free
- Emelia: <https://codeberg.org/fediverse/fep/issues/844> for tracking it on FEP's side

### Working group updates

- Errata:
    We have one errata document for both Activity Streams 2.0 Core and Vocabulary:
    https://github.com/w3c/activitystreams/blob/main/ERRATA.md

    And a separate errata document, as a wiki page, for ActivityPub:
    https://www.w3.org/wiki/ActivityPub_errata

- Diffs
    ActivityStreams Core:
    https://services.w3.org/htmldiff?doc1=https%3A%2F%2Fwww.w3.org%2FTR%2Factivitystreams-core%2F&doc2=https%3A%2F%2Fw3c.github.io%2Factivitystreams%2Fcore%2F

    Activity Vocabulary: 
    https://services.w3.org/htmldiff?doc1=https%3A%2F%2Fwww.w3.org%2FTR%2Factivitystreams-vocabulary%2F&doc2=https%3A%2F%2Fw3c.github.io%2Factivitystreams%2Fvocabulary%2F

    ActivityPub:
    https://services.w3.org/htmldiff?doc1=https%3A%2F%2Fwww.w3.org%2FTR%2Factivitypub%2F&doc2=https%3A%2F%2Fw3c.github.io%2Factivitypub%2F
    
    
1 week elapsed on mailing list, so let the standard 2 week period run through, Darius to also seek comments on mailing list via reminder / followup
    
### Issue triage

* Evan: Second meeting on Tuesdays at a time that works for East Asia, Australia and South Asia? could also do longer meetings (2h instead of 1h)
* a: we have a backlog of issues moreso than new issues as well; formally adopting the drafts at the WG level would allow us to start moving

### T&S Discussion

- ES: Need a note that when implementing a social spec  social software has social consequences
    - CSAM, harassment, other issues that aren't considered
- EP: Non-normative?
    - ES: Maybe non-normative means "this can be ignored"? Prefer informative over non-normative, even though both don't change spec requirements.
    - Others: no!
    - plh: non-normative is for things that can't be defined and verified technically
- EP: https://github.com/w3c/activitypub/issues/575 <-- tracking this issue for now

### Task force for internationalization of handles

- ES: ActivityPub doesn't have a concept of handles
- ActivityPub + Webfinger
- "handle" hasn't been so defined
- EP: https://www.w3.org/TR/activitypub/#preferredUsername
- Jim: we have so many users who want to use this

- DK: Question: Emelia can you explain why a preferredUsername is separate conceptually from a handle? colloquially they seem the same to me?
    - Emelia: This answered in chat, but just adding that preferredUsername is "preferred" and relative to the "server" (I guess?), where as handles are intended to be globally/universally unique.

- CH: https://www.w3.org/TR/activitypub/#i18n-concerns
- Jim: bringing up issues with existing implementations
- PLH: this is a requirement at W3C, if it's an issue then horizontal review will catch it and make problems for us

- Darius: put together a proposal on the mailing list and we can vote on it at our next meeting
