[![Build Status](https://semaphoreci.com/api/v1/nikolalsvk/pusher-js-mock/branches/master/shields_badge.svg)](https://semaphoreci.com/nikolalsvk/pusher-js-mock)
[![Code Climate](https://codeclimate.com/github/nikolalsvk/pusher-js-mock/badges/gpa.svg)](https://codeclimate.com/github/nikolalsvk/pusher-js-mock)
[![Test Coverage](https://codeclimate.com/github/nikolalsvk/pusher-js-mock/badges/coverage.svg)](https://codeclimate.com/github/nikolalsvk/pusher-js-mock/coverage)

![pusher-js-mock logo](logo.jpg)

# pusher-js-mock

Mock Pusher.js in your JavaScript tests with ease

### Installing

Using yarn:
```
yarn add --dev pusher-js-mock
```

Or using npm:
```
npm install -D pusher-js-mock
```

### Example usage

#### Using PusherMock to mock Pusher client instance

If you need to mock a Pusher object in your tests that can
subscribe to channel, it's best to use PusherMock.

```javascript
import { PusherMock } from "pusher-js-mock";

// initializing PusherMock
const pusher = new PusherMock()

// subscribing to a Pusher channel
const channel = pusher.subscribe("my-channel")

// emitting an event
channel.emit("event-name")
```

#### Using PusherFactoryMock to mock Pusher Factory

If you're attaching a PusherFactory to a `window` object like this:

```javascript
window.PusherFactory = {
  pusherClient: function(pusherKey) {
    return new Pusher(pusherKey);
  }
};
```

It's best for you to use PusherFactoryMock.

```javascript
import { PusherFactoryMock } from "pusher-js-mock";

// initialize instance of PusherFactoryMock
const pusherFactoryMock = new PusherFactoryMock();
// replace it with the object that is attached to a window
window.PusherFactory = pusherFactoryMock;

// get the Pusher client reference
pusher = pusherFactoryMock.pusherClient()
```

### API 📦

Check out project docs on the information about API of the used
classes.

### [Code of Conduct](CODE_OF_CODUCT.md)

### [Contributing](CONTRIBUTING.md)

### Credits

Photo by [Octavian Rosca on Unsplash](https://unsplash.com/@tavi004)
