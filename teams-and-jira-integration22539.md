Teams and Jira integration

## Setup



------

 https://www.msteams-atlassian.com/JiraServer/#authorization



1. Add Jira Server App by clicking the ellipsis in the left bar.
2. Open the Jira App in same or new tab.
3. Type connect jira.company.com in the chat.
4. Click on Sign-in and sign with your Company Microsoft account
5. Get and enter d1-----0-e--c-4--1-8--0-c1--------ad as Jira connector id.
6. Click on Authorize, authorize it on the opened web page and enter authorization token to complete the integration.
7. Type help to explore.



## Usage



------

1. help shows the following. Use these commands to work with individual Jira issues.

   **connect \*Jira ID\*** - connect a Jira Server instance to your Microsoft Teams account

   **create** - create a new issue

   **find** - provide a summary keyword (e.g. **find "as a user I want"**) to find the issue

   **assign** - assign the issue to yourself (e.g. **assign MP-47**)

   **edit** - open the issue card to change priority, summary, and description of the issue

   **log** - log time spent on the issue

   **watch** - start watching the issue (e.g. **watch MP-47**)

   **unwatch** - stop watching the issue (e.g. **unwatch MP-47**)

   **vote** - vote on the issue

   **unvote** - unvote on the issue

   **comment** - comment the issue

   **disconnect** - disconnect Jira Server instance you've connected from Microsoft Teams

   **cancel** - cancel current dialog

2. log <jira-id> may be the most useful command since you may do it on a daily basis.

3. The horizontal bar shows other options like "Assigned to me", "Watched by me" etc..
   A good idea is to create a custom Jira filter and view it in the "My filters" section. Select this filter every time you visit this section, hopefully Atlassian fixes this soon.



Tags: productivity, jira, teams
