# React responsive dynamic tabs


#### Responsive

- Hide tabs under the 'Show more' option when they don't fit into the screen
- Transform tabs into the accordion when the wrapper width reaches the `transformWidth` value

![Responsive tabs](https://cloud.githubusercontent.com/assets/3485490/11324577/f6536f2c-913d-11e5-80b0-8755a2ec11cb.gif)

#### Accessible

The component outputs HTML code that follows accessibility principles (aka [WAI-ARIA](https://en.wikipedia.org/wiki/WAI-ARIA)) and uses ARIA attributes such as `role`, `aria-selected`, `aria-controls`, `aria-labeledby` etc.

![Accessible tabs](https://cloud.githubusercontent.com/assets/3485490/11324576/f4775a4c-913d-11e5-9ec2-f13beb8bd578.gif)

#### Fast

We are using [`react-resize-detector`](https://github.com/maslianok/react-resize-detector). No timers. Just pure event-based element resize detection.

## Installation

`npm install responsivedynamictabs`

## Example

```javascript
import React, { Component } from 'react';
import { render } from 'react-dom';
import Tabs from 'responsivedynamictabs';

// IMPORTANT you need to include the default styles
import 'responsivedynamictabs/styles.css';

const presidents = [
  { name: 'George Washington', biography: '...' },
  { name: 'Theodore Roosevelt', biography: '...' },
];

function getTabs() {
  return presidents.map((president, index) => ({
    title: president.name,
    getContent: () => president.biography,
    /* Optional parameters */
    key: index,
    tabClassName: 'tab',
    panelClassName: 'panel',
  }));
}

const App = () => <Tabs items={getTabs()} />;

render(<App />, document.getElementById('root'));
```

## API

All entities listed below should be used as props to the `Tabs` component.

| Prop             | Type          | Description                                                                  | Default   |
| ---------------- | ------------- | ---------------------------------------------------------------------------- | --------- |
| items            | Array         | Tabs data                                                                    | []        |
| beforeChange     | Function      | Fires right before a tab changes. Return `false` to prevent the tab change   | undefined |
| onChange         | Function      | onChange callback                                                            | undefined |
| selectedTabKey   | Number/String | Selected tab                                                                 | undefined |
| showMore         | Bool          | Whether to show `Show more` or not                                           | `true`    |
| showMoreLabel    | String/Node   | `Show more` tab name                                                         | `...`     |
| transform        | Bool          | Transform to accordion when the wrapper width is less than `transformWidth`. | `true`    |
| transformWidth   | Number        | Transform width.                                                             | 800       |
| unmountOnExit    | Bool          | Whether to unmount inactive tabs from DOM tree or not                        | `true`    |
| tabsWrapperClass | String        | Wrapper class                                                                | undefined |
| tabClassName     | String        | Tab class                                                                    | undefined |
| panelClassName   | String        | Tab panel class                                                              | undefined |
| allowRemove      | Bool          | Allows tabs removal.                                                         | `false`   |
| removeActiveOnly | Bool          | Only active tab has removal option                                           | `false`   |
| showInkBar       | Bool          | Add MaterialUI InkBar effect                                                 | `false`   |
| uid              | any           | An optional external id. The component rerenders when it changes             | undefined |
