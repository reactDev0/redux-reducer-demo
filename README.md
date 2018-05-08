# Redux Reducer Demo

[![Build Status](https://travis-ci.org/AlecAivazis/redux-responsive.svg?branch=master)](https://travis-ci.org/AlecAivazis/redux-responsive)
[![Coverage Status](https://coveralls.io/repos/github/AlecAivazis/redux-responsive/badge.svg?branch=master)](https://coveralls.io/github/AlecAivazis/redux-responsive?branch=master)
[![npm](https://img.shields.io/npm/v/redux-responsive.svg)](https://www.npmjs.com/package/redux-responsive)

A redux reducer for managing the responsive state of your application.

## Example

```js
// MyComponent.js

import React from 'react'
import {connect} from 'react-redux'

// grab only the responsive state from the store
// (assuming you have put the `responsiveStateReducer` under
//  the key `browser` in your state tree)
function browserSelector({browser}) {
    return {browser}
}

@connect(browserSelector)
class MyComponent extends React.Component {
    render() {
        // grab the responsive state off of props
        const {browser} = this.props

        let message = `The viewport's current media type is: ${browser.mediaType}.`

        if (browser.lessThan.small) {
            message += 'Secret message for viewports smaller than than the "small" breakpoint!'
        } else if (browser.lessThan.medium) {
            message += 'Secret message for viewports between the "small" and "medium" breakpoints!'
        } else {
            message += 'Message for viewports greater than the "medium" breakpoint.'
        }

        return (
            <p>
                {message}
            </p>
        )
    }
}


