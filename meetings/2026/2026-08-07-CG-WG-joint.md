# 2026-08-07 Joint WG/CG Series A

10:00 Eastern Daylight Time (14:00 UTC)

## Proposed Agenda

* Administrivia
  * Scribe volunteer(s)? Ryan
  * Reminders: 
     * [Working Group Membership](https://www.w3.org/groups/wg/social/) and [Community Group Membership](https://www.w3.org/groups/cg/socialcg/)
     * [CG/WG incubation process](https://github.com/swicg/potential-charters/blob/main/stage-process.md)
     * [W3C Code of Conduct](https://www.w3.org/policies/code-of-conduct/)
* Welcome
* Brief introductions as necessary
* Discussion of incubation process and IPR (Philippe)
* Handles task force proposal (Anuj Ahooja)
* Task force updates (Dmitri/Johannes)
* WG updates (Darius)
  * Update on WG draft meetings (Darius)
  * Status of Drafts for ActivityPub, ActivityStreams core, and Activity Vocabulary ([Stage 2](https://github.com/swicg/potential-charters/blob/main/stage-process.md#stage-2-formalization-community-group) of incubation process)
- https://github.com/w3c/activitypub/issues/589 "indexable" and "discoverable" flags
- https://github.com/w3c/activitypub/issues/590 "interactionPolicy"
- https://github.com/w3c/activitypub/issues/591 miscellaneous terms (Hashtag, manuallyApprovesFollowers, movedTo, sensitive)
- https://github.com/w3c/activitystreams/issues/787 licensing

* Any Other Business (AOB)


## Attendees _(please sign in!)_

- [Ted Thibodeau Jr](https://www.linkedin.com/in/macted/) (he/him) (OpenLinkSw.com) // GitHub:[@TallTed](https://github.com/TallTed) // Mastodon:[@TallTed](https://mastodon.social/@TallTed)
- Darius Kazemi
- David Roetzel (Mastodon)
- [Ryan Barrett](https://snarfed.org/)
- [Evelyn Osman](https://eskahlay.com)
- Cristiano Longo
- Anuj Ahooja
- Emelia Smith
- plh
- Chris Harrelson 
- bumblefudge
- Dmitri Zagidulin
- Jim DeLaHunt
- Evan Prodromou
- 

## Minutes

### Introductions, disclaimers, etc

### Incubation process, IP handling

- History of patent-encumbered technologies ending up in standards, and implementers getting shaken down for fees, royalties, etc. 
- Standards bodies have required patent disclaimers, License agreement, etc. (Copyright, too!) since then. 
- CG is somewhat different. CLA applies, but only to your own contributions, not others
- If you haven't signed the CLA, you can't/shouldn't contribute to the CG
- (This came up in a task force, considering how/whether to include text from an outside source)
- Emelia: in T&S task force, looked at incorporating issues/feedback, some was from GotoSocial, but needed to reconcile licenses etc
- Juan: author of much of the doc, didn't think about generic content FEPs etc from non-members as substantive enough to be IP sensitive
- Darius: makes sense but generally not up to human judgment, have to CLA everything
- Evan: just do it like normal, contributors have to CLA, or we find another technical way to achieve the goal
- Emelia + Phillipe: ideally find a way to help/contribute other people's work. but still CLA
- Philippe: W3C bot on GitHub

### Handles task force proposal

- Anuj: emailed proposal to list, may try to resend
- For specifying handles more clearly, evolving them to include eg domains, i18n, etc
- Emelia: current spec doesn't really specify handles enough, just says AP + Webfinger
- Non-goal: DIDs
- Evan: TF is proposal, not research? We've already had a webfinger TF
- Emelia/Anuj: goal is framework. establish concept of handle, figure out what that means, how it interops
- Darius: soften doc to start w/use cases etc
- Jim DeLaHunt is contributing
- is this ATProto handles? ...no. DIDS are out of scope; ATProto handles are just domains anyway
- Jim: I'm in! for i18n
- Juan: use cases! and, alsoKnownAs. ideally don't break webfinger
- Evan: again, I'm in as long as this isn't ATProto-focused

PROPOSED: Form a Handles Task Force within the CG. 

Juan, Ryan, Darius, Emelia, David, Anuj, Chris: +1
Dmitri, plh, Ted: +0
Evan: -0

### Task force updates

- Evan: E2EE: new version of MLS, incorporated learnings from Emissary, Bonfire
  https://swicg.github.io/activitypub-e2ee/mls
- Emelia: T&S: received grants from NLNet, working on MOU for next grant
  NLNet is soliciting more task force people to grant!

### WG updates

- Come to the WG mtgs!
- [Interaction Policies](https://github.com/w3c/activitypub/issues/590) being looked at by the Trust & Safety taskforce as a work item.

### Misc AP/AS2 terms

- CG could add extension (misc) terms
  - https://swicg.github.io/extensions-policy/
  - https://swicg.github.io/miscellany/
- Evan: want to move them forward and formalize them
- Juan: This is the natural life cycle. Does need effort from CG though
- David: current misc terms came from Mastodon, would love to move them forward!
- Emelia: Should discoverable and indexable be added to Miscellany? 
- Evan: maybe yes
- Darius: :thumbsup:

## Post-meeting note: FedCM Point of Contact

Emelia is still looking for a point of contact to bridge between FedCM and ActivityPub / Fediverse applications. We have made some progress on decentralizing FedCM, and are seeking feedback.

## Action Items
- [ ] Dmitri to add the W3C bot on GitHub to swicg
- [ ] Darius to draft additional text for the stage process 
