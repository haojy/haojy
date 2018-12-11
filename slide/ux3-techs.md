class: middle, center

# UX3 Technique Stack

---
name: agenda
# Agenda

1. Introduction
1. Coding Guide
1. React
1. Redux
1. Redux-Saga
1. Sass
1. Webpack/Babel

---
# Introduction

UX3 applies

- state management, managed by [Redux][2]
- component composition with [React][1]
- side effects (like async invokes) with [Redux-Saga][3]
- ES transform with [Babel][4]
- building with [Webpack][5]
- extending CSS with [Sass][6]

[1]: https://reactjs.org
[2]: https://redux.js.org
[3]: https://redux-saga.js.org
[4]: https://babeljs.io
[5]: https://webpack.js.org
[6]: https://sass-lang.com/guide
---
# Coding Guide

We code Javascript in [ES6][7] and [JSX][8] for React component.
- any files using JSX will be suffixed with .**jsx**, others with **js**
- [.babelrc][9] presets `env` for es2015, es2016, es2017 and `react` for JSX
- in Kiwi, [polyfills.js][10] add shims for IE
- code style guide is based on [airbnb][11] with a little change in [.eslintrc][12]
- UX3 uses Babel 6 

[7]: https://babeljs.io/docs/en/learn
[8]: https://reactjs.org/docs/introducing-jsx.html
[9]: https://bitbucket.org/openwave/peridot/src/packages/ux/.babelrc?at=uxlab%2Fuxdevelop-mail
[10]: https://bitbucket.org/openwave/peridot/src/869d6e08c982936608aa8423e51e399753fd166a/packages/ux/src/polyfills.js?at=uxlab%2Fuxdevelop-mail
[11]: https://github.com/airbnb/javascript
[12]: https://bitbucket.org/openwave/peridot/src/869d6e08c982936608aa8423e51e399753fd166a/packages/ux/.eslintrc.yml?at=uxlab%2Fuxdevelop-mail


---
# React

- a library to build the view layer of an MVC application
- compose components like a tree which rendered as a virtual DOM 
- efficiently sync VDOM with the 'real' DOM by `ReactDOM`
- unidirectional data flow guarantees an immutable state for composition components

---
# Component 'Login'
```javascript
import React from 'react'
import PropTypes from 'prop-types'
class Login extends React.PureComponent {
  constructor(props) {
    super(props)
    const { username, password } = props
    this.state = { username, password }
    this.handleLogin = this.handleLogin.bind(this)
    this.handleUsername = this.handleUsername.bind(this)
    this.handlePassword = this.handlePassword.bind(this)
  }
  handleLogin(event) {
    this.props.login && this.props.login(this.state)
  }
  handleUsername(event) {
    this.setState({ username: event.target.value })
  }
  handlePassword(event) {
    this.setState({ password: event.target.value })
  }
  render() {
    const { username, password } = this.state
    return (
      <form className="login">
        <input type="text" required value={username} onChange={this.handleUsername} />
        <input type="password" required value={password} onChange={this.handlePassword} />
        <button onClick={this.handleLogin}> Login </button>
      </form>
    )
  }
}

Login.propTypes = {
  username: PropTypes.string,
  password: PropTypes.string,
}
```
---
# React Component
- use JS class to define a component
- component properties `props` defines the function and interface of a component with `prop-types`
- component `state` holds private data in a component life cycle
- `PureComponent` guarantees to render when `props` changed; `Component` and function component will update on every render chance by default.
- `PureComponent` is default component type in UX3

---
# React Component LifeCycle

.left[<iframe width="1080" height="500" frameborder=0 allowfullscreen  src="http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/">]


---
# Redux

- synchronously manage state by ruled operations
- put whole states in an object tree within a single **`store`**
- only way to change state by emitting an **action** like `dispatch(action)`
- pure function **`reducer`** transform the state per **action**

---
# Redux data flow

.center[![data flow](https://blog.gisspan.com/img/redux.gif)]

---
# Redux-Saga

---
# Webpack

---
