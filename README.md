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

### Roadmap
As of 2016-05-08 the bot is minimally functioning, with all features that the previous Niancat
had. The immediate tasks are:

- Bug fixes, when found.
- Persistent puzzle storage.
- Store unsolutions as reminders.
- Extract current bot design into a bot library? I'm unclear on this, as I think the design became
  bulky and not very quick to work with.

In addition, the underlying libraries DandelionSlack.jl and WebSocketClient.jl are only minimally
functioning. They require more error handling, as well as documentation and features.
Some time in the future I would like to implement server functionality for WebSocketClient.jl as
well, and rename it to reflect that.

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

## DandelionSlack.jl
This is a Slack API, used by Niancat. It uses WebSocketClient.jl for WebSocket communication.

### Roadmap
Currently, this package only exists for the benefit of Niancat.jl. Hence, the roadmap will
prioritize those tasks that Niancat.jl depends on.

- Reconnect RTM.
    + Depends on state changes working properly in WebSocketClient.jl
- State change handling.
- Handle errors when deserializing objects.
- Implement more objects in WebApi
- Implement more events in RTM

## WebSocketClient.jl
This is the WebSocket client used by DandelionSlack.jl for Real Time Messaging (RTM) in Slack.

### Roadmap

- Propagate state changes
- Proper handling of network errors

Long term:

- Implement WebSocket server support.

## Open source
These packages are open source, obviously, but they have currently not been made available to the
greater Julia community. Partly this is because they're highly incomplete, but also because
DandelionSlack.jl depends on pull requests in Requests.jl that haven't been accepted yet. Before
the pull request is accepted there is almost no meaning in submitting it as a Julia package.

The WebSocketClient.jl package should be cleaned up, made to work with all minimal features (such as
binary messages). After that we should rename it to something not client-specific, since supporting
WebSocket servers is a plan.
