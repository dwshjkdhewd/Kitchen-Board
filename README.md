# Kitchen Board

A shared family board for calling kids to dinner, summoning them, assigning chores and keeping a family calendar. Everyone opens the same link on their own phone, and changes show up for everyone right away.

**Live board:** https://claude.ai/artifact/WvfMZLkzVhR5QA7bozhsrk

## What it does

- **Calls:** parents tap **Dinner's ready**, **Come here** or **Send a message**, to everyone or to one person.
- **Lock screen until answered:** whoever is called gets a full-screen takeover that covers the board. It chimes and vibrates every 15 seconds and keeps the screen awake until they tap **Coming!**, **On my way** or **Got it**. Calls never expire. A parent can cancel one with the ✕ in their sent list.
- **Answer tracking:** parents see who has answered each call and who is still waiting.
- **Chores:** one-time with a due date, daily, weekdays or weekly. Each chore goes to a specific person or to anyone. Kids check chores off and the board records who did each one.
- **Calendar:** a month view with dots on days that have events. Each event has a time, who it's for and a note. Anyone can add events.
- **Today tab:** today's chores (kids see only their own), today's and tomorrow's events, and recent calls.

## Setting it up

1. Open the live board and add everyone in the house, starting with parents.
2. Share the board from its **Share** menu, and give each family member **Contributor** access. Viewers can see the board but can't check off chores or answer calls.
3. On each phone, tap the name chip at the top and pick **This is me**. Each phone remembers its choice.
4. Tap **🔔 Sound** on each phone so it chimes when that person is called.

## Limits

- It's a web page, so it can lock the board but not the phone. Calls only appear while the board is open, or the next time someone returns to it. A phone that's locked or has the browser closed gets nothing until then. To restrict the phone itself, use a parental-control app such as Google Family Link on Android or Screen Time on iPhone. Those can also limit a phone to a few allowed apps.
- Each phone picks its own name, so parent and kid roles run on trust.

## How it's built

`index.html` is a single file with no build step. It runs as a hosted Claude artifact, and its shared storage (the `db` capability) comes from that hosting, so opening the file on its own shows a "couldn't connect" message.

Data is stored in four collections:

| Collection | Holds |
| --- | --- |
| `family` | name, role (`parent`/`kid`), color, display order |
| `chores` | title, assignee, repeat rule, due date or weekday, completions keyed by date |
| `events` | title, date, time, who it's for, note |
| `calls` | type (`dinner`/`summon`/`note`), sender, recipient, message, answers, cleared flag |

To update the live board after you change `index.html`, republish the file to the same artifact link.
