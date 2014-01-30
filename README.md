# qb-nats

A pub/sub [nats](https://github.com/derekcollison/nats) dialect for [qb](https://github.com/rafflecopter/node-qb)

_Note_: I suggest running the [gnatsd](https://github.com/apcera/gnatsd) server which is written in Go. I like Go better than ruby (also its probably faster).

## Usage

```
npm install qb-nats --save
```

```javascript
qb.speaks(require('qb-nats'), { nats: natsOptions })
  .start()

  // Access a channel using nats and qb's `contact` polymethod
  .contact('nats://new-users-channel')
    // Listen for messages on this channel
    .subscribe(function onNewUser(msg) {})
    // Or you can directly invoke a service queue
    .subscribe('service-to-execute-with-message');

// Or you can create an alias
qb.contacts('nats://some-channel', 'some-channel')
  .contact('some-channel')
  // And lastly, you can publish on channels
  .publish({a: 'message', to: 'be', deliv:'ered'});
```

Options:

See the [node nats client](https://github.com/derekcollison/node_nats) for documentation on the nats options.

## License

MIT in LICENSE file