---
title: "Getting Started"
date: 2019-10-01T10:57:18-07:00
draft: false
---
# Meeting
* We met with Github on 10/3/2019 to discuss the below questions.
* Greg Padak - product manager for enterprise cloud, and PM for SAML integration and sync services
* Erik Lind - Github 

# Questions
* Size of an organization: we are choosing a single org to house all innersource efforts. Any downsides to this approach, vs. having multiple orgs?
    - Greg: 2 main options: single org for innersource, or use Internal repos to give everyone in the company read-only to it. There's nothing wrong with using one org. If you had a bunch of Github orgs and projects already and wanted to innersource them, using Internal repos would be the best approach instead of moving them to a single org. But since you are starting green-field, it is probably easier to start with an innersource org. 

* Problems with forks
    * Forks leave the org and enter a personal account. Enforcement of SSO no longer applies to this code. This seems like a path for IP exfiltration. Any plans to correct this?
         * Greg: thought it could be disabled at the umbrella org level, but MRU tried and it didn't work. 	He doesn't want enterprise SSO to apply to a user's personal account. He'd prefer disabling forks for Enterprise users. He is going to create an Issue after the call to look into it.

* Internal repositories
    * Internal doesn't seem to have any benefit over private if all innersource work is in one org. Do we have this correct?
    * These allow forking, which we may not want to allow. Is there a way to disable forking for Internal? Or is there a way to disable use of Internal entirely (just allowing Private repos)?  

* Probot
    * Github documentation recommends the use of Probot for settings enforcement within an org. [Link](https://github.community/t5/Support-Protips/Best-Practices-for-Organizations/ba-p/10384)
    * What are the guarantees or SLA's for Github-hosted Probot Apps? Can we depend on these for critical features like enforcing security rules?
    * Are Github Actions a replacement for Probot? Or perhaps a complement to it? What is the roadmap for Probot?
    * If we need to customize the behavior of a Probot App, is the only route to host our own instance? Or can the Github App hosting be leveraged for these customized apps?
    * Our plan is to use a Shared Repo collaboration model with a default Write permission for the org, combined with branch protections for master in each repo. We plan on using a custom Probot app to add these branch protections upon repo creation. Is this a good approach?

* Branch protections - are there any plans to add a default branch protection option at the org level?
    * Greg: its a good idea, but couldn't find anything on the near-term roadmap to solve this.
     
* Repository namespace - Global today, so repo names must be unique. The public site uses an account to namespace the repos, so they only need to be unique per account. Any plans to add a level of user accounts within an org?
    * Greg:	Additional namespaces within an org has been discussed with the PMs.	The issue is: what level of the product does it reside? Enterprise collections (at root level), sub-org level? Still trying to figure out what to do.	It probably wouldn't be org / user / repo if the user departs from the org. We are correct in that Orgs are like users, they just have other features like they can have their own users and teams.


* Pages and Gists are always public. Will it be possible to scope these to an org in the future?

* User accounts
    * Need to provisioned separately. Ideally these would be fully integrated into SSO so users do not need to manage a separate identity.
    * How are companies managing these accounts? We had to create an awkward naming scheme for these.
        * They are exploring corporate accounts, but they'd still be Github accounts in a special namespace. Other SaaS providers may not have this issue like Slack, but Github's unique in that they are global community of developers… you join Github community when you join github.com.
    * Difficult to tell who someone is since we can't see their email
        * Use this setting https://help.github.com/en/articles/managing-the-display-of-member-names-in-your-organization
        * This only helps comments and issues, it would be nice if it applied to commits as well

*  Default community health files only work for public repos. Any plans to enable this for internal/private as well?

* Topics and Collections
    *  Are there any plans to have a private version of GitHub's Topics and Collections?  Both sites appear to be targeted toward public consumption.
  
* Repository Permissions
    * It appears self-service creation of repositories is controlled via a global setting for the organization.  Are there any plans to provide more granular controls over this permission?   

* Any opportunity for a reference call with a similar organization implementing Innersource on Github?

* Other questions
    * Flags for beta features to avoid suddenly changing our risk profile 
        * Greg: Most features are opt-in by customer. For Internal repos, they thought there was such demand that by making it public they could get feedback faster. However, if they could do it again, he'd probably protect it with a flag. Internal repos are going GA towards the end of October 2019, so hopefully its no longer an issue.
    * Difficult to know the implications of some of the options in the UI
        * Greg: They are trying to provide more context-sensitive help guides
    * Disabling contractors from contributing to innersource
        * Greg: Org owners might be able to override this. Most customers want enterprise-wide policies. Github is looking into a custom roles feature with additional granularity. 
    * Other identity providers besides Azure AD for additional authorization like Teams?
        * Greg: Yes, Okta is next on the list but they are waiting for Okta to implement a certain feature they need.
    * Any comments on our general approach?
        * Greg: Sounds normal.