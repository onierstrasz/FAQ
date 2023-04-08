# Mailman-FAQ

**NB:** Mostly moved to http://scg.unibe.ch/wiki/faq/mailman

## Q How do I reduce spam attacks?

You can hide the list from the overview. That has always been possible. It's the top item in `Settings -> List Identity`.
Then you can auto-reject or `-discard` posts from non-members (`Settings -> Message Acceptance -> Default action to take when a non-member posts to the list`). Reject will inform the sender, that his mail was rejected. Discard will silently discard it.

## Q Which options are most important to configure?

- `General options>Prefix`
- `General options>Description`
- `General options>Send welcome message ...`
	- turn off initially for existing lists
- `General options>Send goodbye message ...`
- `General options>Maximum length`
- `General options>Should administrator get notices of subscribes`
	- should be Yes for non-public lists
- `Non-digest options>Footer`
- `Privacy options...>Subscription rules>What steps are required for subscription?`
	- should be Confirm and approve for non-public lists!
- `Privacy options...>Sender filters>moderate member postings`
	- set to Yes for public lists
- `Privacy options...>Sender filters>action for non-member postings`
- `Privacy-option>Recipient filters>Must posts...`
	- no to avoid implicit desitination errors
- `Privacy options...>Spam filters>Spam Filter Rule 1 -- X-Spam-Flag: YES`
- `Archiving Options>Archive messages`
- `Archiving Options>public or private`
	- should normally be private

## Q How do I ensure that all members of the list are moderated?

There is a checkbox at the bottom of the member list to toggle this flag.

## Q How do you set the reply-to field?
`General options>Reply-to`

## Q Where do you configure the standard footer?
Digest options

## Q How do I get rid of "Message has implicit destination" warnings?
Configure `Privacy-option>Recipient filters`
(Either set "Must posts ..." to "no", or add the ok CC aliases.)

## Q How do I get spam to be automatically discarded?
`Privacy Options>Spam Filters`
Set a Spam Filter Rule to match "X-Spam-Flag: YES" and Discard

## Q How can I turn off daily reminders?
`General options>Should the list moderators get ... daily notices about collected ones?` -> NO

## Q How can I force mailman to list all members on one page?
See: http://www.hoboes.com/NetLife/pytown/mailman/list-all-members/

NB: mailman is installed in /usr/lib/mailman/
