# React Scrollama

## Install

React Scrollama can be installed as an [npm package](https://www.npmjs.com/package/react-scrollama2):
```
$ npm install react-scrollama2
```

**Note: You must include the [IntersectionObserver polyfill](https://www.npmjs.com/package/intersection-observer) yourself for cross-browser support. Also consider including a [`position: sticky` polyfill](https://github.com/dollarshaveclub/stickybits).**

## Usage

A simple example with no frills.

```js
import React, { Component } from 'react';
import { Scrollama, Step } from 'react-scrollama2';

class Graphic extends Component {
  state = {
    data: 0,
  };

  onStepEnter = ({ element, data, direction }) => this.setState({ data });

  render() {
    const { data } = this.state;

    return (
      <div>
        <p>data: {data}</p>
        <Scrollama onStepEnter={this.onStepEnter}>
          <Step data={1}>
            <p>step 1</p>
          </Step>
          <Step data={2}>
            <p>step 2</p>
          </Step>
        </Scrollama>
      </div>
    );
  }
}
```

## API

#### `<Scrollama/>`

| Prop        | Type   | Default | Description                                                                            |
|-------------|--------|---------|----------------------------------------------------------------------------------------|
| offset      | number | 0.5     | How far from the top of the viewport to trigger a step. Value between 0 and 1.         |
| debug       | bool   | false   | Whether to show visual debugging tools.                                                |
| onStepEnter | func   |         | Callback that fires when the top or bottom edge of a step enters the offset threshold. |
| onStepExit  | func   |         | Callback that fires when the top or bottom edge of a step exits the offset threshold.  |

The `onStepEnter` and `onStepExit` callbacks receive one argument, an object, with the following properties:

```
{
  element, // The DOM node of the step that was triggered
  data, // The data supplied to the step
  direction, // 'up' or 'down'
}
```

#### `<Step/>`

| Prop     | Type           | Default     | Description                                                      |
|----------|----------------|-------------|------------------------------------------------------------------|
| data     | any            | _undefined_ | Data to be given to `<Scrollama>` callbacks when step triggered. |
| children | PropTypes.node |    N/A      | Children must always be one component, not an array              |

## Features roadmap

* viewportAbove and viewportBelow intersection observers
* thresholds and progress
* preserving order

## Contributing

You're welcome to contribute to React Scrollama. To setup the project:
1. Fork and clone the repository.
2. `npm install` in the library and the `example/`.
3. `npm start` in the library and the `example/`.

The docs page will then be served on http://localhost:8000/ in watch mode, meaning you don't have refresh the page to see your changes.

## License

MIT
