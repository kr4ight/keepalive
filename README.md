# keepalive
A redstone system to keep two systems alive, if one system shuts off, the other one does as well

## Why use keepalive
keepalive is meant to keep two systems who are dependent of eachother alive if they both are turned on.

## how does keepalive work
Unlike other data transfers, keepalive does not actually transfer any contextual data, only a ping and a pong, which are the same signal.
Keepalive uses two streams, one for pings and one for pongs, and the roles reverse for the other peer.

#### Peer 1
1. Ping
2. Pong

#### Peer 2
1. Pong
2. Ping

The sender and receiver can be in both peers

### Sender
The ping is then routed back to pong, but with a comparator in between, and if the comparator is turned on, the signal from ping does not respond, indicating the device has shut off.

### Receiver
When the signal is off by a configured time (via a comparator delay), it should have captured the ping sent by the sender and the receiver gives the peer a signal indicating the other peer is still active.

### Ping/Pong loop
After the inital ping/pong, the peers will automatically keep ping ponging to each other until one of them shuts off.
