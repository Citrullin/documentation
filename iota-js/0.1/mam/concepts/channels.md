# MAM channels

**All MAM messages are published to MAM channels, which are encrypted data streams that are authenticated by a seed. Only the seed owner can publish messages to a channel. As a result, MAM channels are a useful way of authenticating that messages were published by a certain person or device.**

You can publish messages to any of the following channel modes:

* Public
* Private
* Restricted

MAM messages are sent in the `signatureMessageFragment` field of zero-value transactions.

When you publish messages to any channel, you receive a channel ID, which is the identifier that allows others to subscribe to it and fetch your messages. **A Channel ID is the address of the transaction that contains the MAM message**.

All MAM channels are created from a Merkle tree, where all messages are signed with one of the private keys in the leaves.

Because a single tree lasts for only a short period of time, each message contains the root of the next Merkle tree to allow the subscriber to continue fetching messages.

When a subscriber fetches messages from a MAM stream, the message is first authenticated by validating the signature and verifying that the signature belongs to one of the Merkle tree's leaves. If the signature verification fails, the entire message is considered invalid.

## Public channels

Public channels use the root as the address of the transaction that contains the MAM message (channel ID). As a result, anyone can decrypt messages in a public channel by using the address.

This mode could be used for public announcements or even a immutable social media application with built-in authentication.

## Private channels

Private channels use the hash of the root as the address of the transaction that contains the MAM message (channel ID). As a result, only those with the original root can decrypt the messages in a private channel.

This mode is useful for devices that want to communicate in private among each other.

## Restricted channels

Restricted channels adds an authorization key, called the side key, to private mode. The address of the transaction that contains the MAM message (channel ID) is the hash of the side key and the root. As a result, only those with the original root and the side key can decrypt messages in a private channel.

This mode is useful for being able to revoke access to the channel by changing the side key. When you change a side key, you just need to distribute it to the parties that are allowed to follow the rest of the channel.
