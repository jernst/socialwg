# 2026-05-21 Joint WG/CG Series B
Meeting held 19:00 Eastern Daylight Time (23:00 UTC)

## Present

- Darius Kazemi
- Evan Prodromou <acct:evanprodromou@socialwebfoundation.org>
- a <trwnh.com>
- Johannes Ernst https://j12t.org
- Jim DeLaHunt <acct:jdlh@mstdn.ca>
- Philippe Le Hegaret
- Lisa Dusseault
- Dmitri Zagidulin
- dBoredGuy
- Emelia Smith
- Chris Harrelson
- Tantek Çelik https://tantek.com/

## Agenda

* Administrivia
  * Scribe volunteer(s)? Johannes, a
  * Reminders: 
     * [Working Group Membership](https://www.w3.org/groups/wg/social/) and [Community Group Membership](https://www.w3.org/groups/cg/socialcg/)
     * [CG/WG incubation process](https://github.com/swicg/potential-charters/blob/main/stage-process.md)
     * [W3C Code of Conduct](https://www.w3.org/policies/code-of-conduct/)
* Welcome
* Brief introductions as necessary
* Task force updates (Dmitri/Johannes)
  * API (EP)
    * Evan: Lots of activity in the TF. New draft document (basic profile for AP servers): https://swicg.github.io/activitypub-api/basicprofile "Here are the parts of AP, OAuth, HTTP features that you should support as minimum". Open for review, issues on GitHub. https://github.com/swicg/activitypub-api
  * E2EE (EP)
    * Evan: Lots of conversations about structure of the E2EE system. Building on top of MLS, on top of AP, metadata is currently leaked so how can we improve that. Testing between Emissary and Bonfire internally, Bonfire-Bonfire and Emissary-Emissary is already working, now looking for interop
    * Darius: where is the code? Should not be in the production versions.
    * Evan: based on plugins. Don't install for production yet.
    * Emelia: can the TF prioritize working on the threat modeling document that MLS spec strongly recommends? as a prereq before additional work so things can be assessed against that threat model
    * Evan: unlikely to stop doing other work, however happy to get that started and look into MLS requirements
    * Emelia: not a "strict block" but without a threat model you can't really design it to be correct. who is attacking who? who is being protected and how?
    * Evan: we are a standards TF doesn't have the ability to block anyone from continuing; we can only deal with spec work
    * Emelia: basic threat modeling first will get you to a better place
    * Tantek (in chat): +1 Emelia, part of defining the use-cases for E2EE requires defining who is able to read which messages and who is not
      * Emelia (in chat): Yeah, I'd passively seen a bunch of E2EE work where I was confused by it because I didn't understand what the threat model was that I was reading under so my own personal threat model for E2EE is based on my experiences and affected communities 
    * Darius: +1 on understanding the threat model for the E2EE TF work. I did notice a lot of convos where there was contention about lack of threat model, should be as basic as having user stories. Isomorphic situation to trying to do spec work without user stories
    * Evan: Happy to put this at the top of the stack, draft ready for the next TF or CG meeting hopefully.
    * Darius: Maybe call for participation, open an issue and let people comment what should or should not be part of the threat model -- state actors, mods gone rogue, etc etc. Non-technical people should be able to chime in as well.
  * Trust and Safety (Emelia)
    * Emelia: Still waiting to hear back from NLNET; didn't make sense to do STF; still looking for another co-lead to replace Darius, and I am not always available due to illness. Any ideas for how to find someone for specifically that topic? Would like someone with experience with T&S moreso than AP.
    * Emelia: Timing of meeting depends on people showing up. We changed it back in October but not sure what else to change it to. Can't change meeting time without contributors.
    * Darius: no problem changing it around several times. Recommend getting commitment from people to show up for changed time before changing time
  * LOLA (Lisa)
    * Lisa: no news. got review of authorization model from Google folks (prompted by the person who attended last month). Thumbs up
    * Darius: any way to see output?
    * Lisa: no, it was in person and over email
    * Emelia: does LOLA reference any FEPs not part of some other standard? Could be a blocker on IP concerns
    * Chris: Looped in Sam Goto, all seems fine
    * Lisa: will look at FEPs
    * Lisa: Current draft is here https://swicg.github.io/activitypub-data-portability/lola
  * Handles (Jim)
    * Jim: Where are we on this? Question of scope and some issues I'd like to work on. Is a TF the right vehicle for this? Maybe we're not ready for that conversation this meeting, could take more time to figure it out.
    * Dmitri: Encourage you to bump the email thread and we can come back to it
    * Emelia: Earlier on mailing list I responded that TFs don't usually do outreach like this; they write documents and ask for input on those documents, not directly changing implementations. Suggesting a Handles TF because we do broadly speaking have a notion of handles but not formalized except in binding WebFinger. Need to tackle the internationalization issue per requirement from W3C
    * Emelia: email thread already discussed Handles TF proposal; we are stuck on finding a potential lead; I'm willing to help someone as a shadow lead but not be the official lead. Jim said he was interested in co-leading but we need one other person. Will ask on the mailing list.
    * Jim: I don't want to just write specs, I would like to see them used by implementers and users, want to do advocacy and outreach, not sign myself up for a bunch of tasks that prevent me from doing that.
    * Emelia: can we start a TF without having all leads
    * Darius: Let's find leads before we get to a vote
  * Website TF
    * Johannes: we should publish some updates on activitypub.rocks occasionally, from TFs and the WG. Please send things!
    * Evan: monthly meeting to figure out news to push to website?
    * Johannes: let's do that
* WG updates (Darius)
  * proposal for WG Draft triage meeting schedules
    * Darius: after looking at how other WGs to this (e.g. weekly meetings), Darius has a proposal, will put on mailing list.
    * Darius:2nd + 4th week of the month have WG meeting to go through issues related to WG drafts, so they can move forward. Keep the other two meetings joint WG + CG meetings
    * Darius: WG activity, as it is about WG docs, and contributors need to be WG members
    * Evan: make the issue triage the same thing
  * Status of Drafts for ActivityPub, ActivityStreams core, and Activity Vocabulary ([Stage 2](https://github.com/swicg/potential-charters/blob/main/stage-process.md#stage-2-formalization-community-group) of incubation process)
    * Evan: two tracks
      1. Github branch process. Open question: when do we create a branch to work on a new version
      2. Critical review of the docs. AS and AP Core. Still needs Activity Vocabulary. Everybody in the WG should contribute.
    * Darius: which version?
    * Evan: use editor's draft, because it includes corrected errata
    * Evan: process for issue triage is:
      * look at new issues
      * route them to next version (1.1 for this year) vs erratum vs extension/new functionality vs need new primer content
      * AP: 87 open issues, AS: 50 open issues, still a lot of work to do
    * Darius: WG member wanted to see a "status summary" / progress page / dashboard-eque kind of landing page
    * Philippe: we have tools to automatically generate periodic Github activity summaries etc. Rather not make more work for editors. Can send examples.
    * Darius: hope to get the specific WG member to explain what they wanted in more detail, but not present today.
    * PLH: for example: https://lists.w3.org/Archives/Public/public-webrtc/2026Apr/0027.html
    * a: are we at the point where the WG has accepted the CG documents and will adopt it?
    * Darius: we put the call out, there were no objection
    * PLH: you need to write down the decision and e-mail it
    * Evan: sounds like the decision was made, I will cut the branch
* Any Other Business (AOB)
  * Pseudonymous participation update (PLH)
    * PLH: It's in progress; kind of a non-update for now, sorry.
    * Emelia: Anonymous/Pseudonymous contribution is allowed in FEP, but maybe not at W3C.
    * PLH: No conflict actually, but W3C haven't documented how it handles that.
  * Emelia: If a W3C org unit receives a security report, what are the expectations?
    * PLH: not a staff priority
    * PLH: CG do not have a process
    * Emelia: What if people advocate a CG as a "standard"?
    * PLH: should not misrepresent CG documents as "standard"
    * Darius: by authors or who else?
    * Emelia: authors. Several encounters.
    * PLH: will clarify on how CG reports are published (including proposal for layout, respec etc), but website and reports should not misrepresent
    * Emelia: CG reports do not immediately look different from a standards doc
    * PLH: working on that very thing right now
