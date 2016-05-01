# Notes
Public TODO list for dandeliondeathray.

## Dandelion Slack bot
The Dandelion Death Ray Slack bot library will be used for niancat, and presumably other bots
as well.

Things we're working on:

- A Slack API
- A WebSocket client, needed by the Slack API

Things we will work on, eventually:

- A Slack bot library, as a more usable layer built ontop of Slack API
- Niancat

## Ideas
A "KAFKA" bot that keeps info on the next meeting, and reminds people. The bot should register with the name "Franz".

## Niancat

### Core features
- Keep todays puzzle
- Commands
    + !nian
    + !setnian
    + !help
- Handle solutions attempts in private channels with users
- Notify main channel on solution
- Solution notification includes user name and SHA256 hash of solution and user

### Other features
- Store latest puzzle on filesystem, and recover it on startup
- User can store unsolutions as reminders, automatically posted when the next puzzle is set.
- The bot will verify that the puzzle has a solution, to help with typos
- The bot will notify the channel if there is more than one solution