- [One-to-One chat storage](#one-to-one-chat-storage)
  - [Storage requirements](#storage-requirements)
  - [Initial schema](#initial-schema)
  - [Improved schema: Decouple msg content from sender and receiver](#improved-schema-decouple-msg-content-from-sender-and-receiver)
- [Group chat storage](#group-chat-storage)
  - [Storage requirements](#storage-requirements-1)
  - [Initial schema](#initial-schema-1)
  - [Improved schema: User could customize properties on chat thread](#improved-schema-user-could-customize-properties-on-chat-thread)

# One-to-One chat storage
## Storage requirements
* Requirement1: Query all 1-on-1 conversations a user participates in after a given timestamp.
* Requirement2: For each conversation, load all messages within that conversation created later than a given timestamp.

## Initial schema

![](../.gitbook/assets/im_groupchat_recentContact_one_to_one.png)

## Improved schema: Decouple msg content from sender and receiver
* Intuition:
  * Even if sender A deletes the message on his machine, the receiver B should still be able to see it
  * Create a message\_content table and message\_index table

![](../.gitbook/assets/im_groupchat_recentContact_1to1_decouple.png)

# Group chat storage
## Storage requirements
* Requirement1: Query all group conversations a user participates in after a given timestamp.
* Requirement2: For each conversation, load all messages within that conversation created later than a given timestamp.
* Requirement3: For each conversation, load all participates inside it. 

## Initial schema

![](../.gitbook/assets/im_groupchat_recentContact_group.png)

## Improved schema: User could customize properties on chat thread

* Intuition:
  * User could mute a chat thread. Create a customized name for a group chat.
  * Expand the thread table with three additional fields including owner\_id, ismuted, nickname

![](../.gitbook/assets/im_groupchat_recentContact_group_customize.png)
