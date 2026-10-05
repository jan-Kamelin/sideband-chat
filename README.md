# Sideband Chat

A peer-to-peer chatting app in a single HTML file. Choose your own peer ID, connect with friends, and create group chats without hosting a server.

## Get started

1. Download `peer-chat.html` from this repository (use **Download raw file** on GitHub).
2. Open the file in a modern browser with internet access. No build or installation is needed.
3. Choose a unique peer ID and click **Go online**. Each person needs a different ID and their own copy of the file.
4. Share your ID with a friend. Enter their ID under **Direct chat** and click **Connect**.
5. Write a message and press Enter to send. Use Shift+Enter for a new line.

Peer IDs are case-sensitive, up to 64 characters, and support letters and numbers with single spaces, hyphens, or underscores between them. An ID is reserved only while online.

## Group chats

Enter a room name and click **Create**. Copy the invite code and share it privately. Friends can paste the code under **Group chat** and click **Join room**.

Rooms support up to 12 members. The creator's browser relays messages to the other members, so the creator must keep the tab open and stay connected. Group members connect to the creator rather than to every other member. If the creator disconnects, group messaging stops; members must rejoin after the creator returns. Reloading the creator's tab removes the room, requiring a new room and invite code.

## How it connects

The file loads PeerJS 1.5.5 from unpkg and uses the public PeerJS Cloud signaling service to find peers and establish WebRTC connections. Direct messages travel over a WebRTC data channel. Group messages travel through WebRTC channels to and from the room creator's browser. You do not need to run a signaling server or chat server.

Internet access is required for the library, signaling, and connection discovery. Some restrictive networks or NAT configurations require a TURN relay. This app does not configure a TURN server, so connections may fail on those networks. Public signaling service availability is outside this app's control.

## Privacy and limits

- Messages and room information stay in the tab's memory and disappear on reload. There is no server-side history or offline delivery.
- New group members do not receive earlier messages.
- WebRTC encrypts transport. The group creator can read all group messages.
- Peer IDs are not verified identities or password-protected accounts. An ID can be claimed by someone else when its previous user goes offline.
- Anyone with a room invite code can join while capacity is available. Keep codes private.
- Messages are limited to 8,000 characters. Each conversation retains up to 500 message entries in memory.
- The interface includes connection status, errors, and copy/paste support for room codes.

## Validation

Simulated tests cover custom IDs, direct text messaging, three-person group joins and relays, sender attribution, unknown-room rejection, membership updates after disconnection, and retaining unsent text when disconnected. Live connections between separate devices and networks have not yet been verified.

## License

MIT. See [LICENSE](LICENSE). PeerJS is a separate dependency with its own license.
