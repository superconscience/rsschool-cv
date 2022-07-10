# HLIB HODOVANIUK

### Middle Frontend Developer (React)

====

Email: gleb.godovanyuk@gmail.com

Phone: +380950928411

LinkedIn: [www.linkedin.com/in/hlib-hodovaniuk-5385b6211](www.linkedin.com/in/hlib-hodovaniuk-5385b6211)

====

I am an experienced Frontend developer interested in building usable, useful,
well-constructed websites and applications. Interested in continuation of
learning and cooperation with excellent people.

====

## Skills

- Expertise in JavaScript, React JS, Redux, PHP, MYSQL, Restful API
- Command over HTML and CSS and their allied tools (SCSS, Styl)
- Basic knowledge of TypeScript
- Experience with Laravel
- Familiar with Node JS and Express
- Working knowledge of Webpack, Babel, Git, Docker
- Team collaboration, Git repository, time management

====

## Experience

- 4 years of handling customer requirements for technical solutions
- 2 years of experience in coding and developing web applications in React JS environment
- Over 4 years of working with JavaScript technology-based solutions
- 3 years of experience in developing and maintaining restful interfaces with MVC architecture for complex web apps utilizing PHP and MYSQL

====

## Work History

**Company: AFSMD**

Duration: September 2016 – March 2022 (5+ years)

Role: Junior Fullstack Developer / Middle Fullstack Developer / Middle Frontend Developer

**Projects**

- Multiple online trading platforms
    - Developed dynamic and multi-browser compatible pages using
      React JS, TypeScript, SCSS.
    - Built custom components for UX-library consisting Accordions,
      Filters, Dropdowns, Tables, Buttons, Checkboxes, Inputs.
    - Maintained React state management strategies with Redux.
    - Implemented platform integration with multiple trading APIs,
      streaming the data feeds (Crypto, Stocks, Futures, CFD) and other
      features.
    - Created and maintained complex presentation and business logic
      layers for both client and admin pages intended for trading,
      account management, investments, clients management, business
      customization.
- [Taskea – Full-time Digital Service Platform](https://taskea.net)
    - Developed custom API layer to handle all CRUD operations using
      Laravel, MYSQL, Eloquent.
    - Identified and solved issues caused by plugins under PHP,
      Javascript and Jquery.

====

## Code Examples

**The State Reducer Pattern** inverts control over the state
management of your hook and/or component to the developer using it so they can
control the state changes that happen when dispatching events.

```javascript
import * as React from 'react'
import {Switch} from '../switch'

const callAll = (...fns) => (...args) => fns.forEach(fn => fn?.(...args))

const actionTypes = {
  toggle: 'toggle',
  reset: 'reset',
}

function toggleReducer(state, {type, initialState}) {
  switch (type) {
    case actionTypes.toggle: {
      return {on: !state.on}
    }
    case actionTypes.reset: {
      return initialState
    }
    default: {
      throw new Error(`Unsupported type: ${type}`)
    }
  }
}

function useToggle({initialOn = false, reducer = toggleReducer} = {}) {
  const {current: initialState} = React.useRef({on: initialOn})
  const [state, dispatch] = React.useReducer(reducer, initialState)
  const {on} = state

  const toggle = () => dispatch({type: actionTypes.toggle})
  const reset = () => dispatch({type: actionTypes.reset, initialState})

  function getTogglerProps({onClick, ...props} = {}) {
    return {
      'aria-pressed': on,
      onClick: callAll(onClick, toggle),
      ...props,
    }
  }

  function getResetterProps({onClick, ...props} = {}) {
    return {
      onClick: callAll(onClick, reset),
      ...props,
    }
  }

  return {
    on,
    reset,
    toggle,
    getTogglerProps,
    getResetterProps,
  }
}
// export {useToggle, toggleReducer, actionTypes}

// import {useToggle, toggleReducer, actionTypes} from './use-toggle'

function App() {
  const [timesClicked, setTimesClicked] = React.useState(0)
  const clickedTooMuch = timesClicked >= 4

  function toggleStateReducer(state, action) {
    if (action.type === actionTypes.toggle && clickedTooMuch) {
      return {on: state.on}
    }
    return toggleReducer(state, action)
  }

  const {on, getTogglerProps, getResetterProps} = useToggle({
    reducer: toggleStateReducer,
  })

  return (
    <div>
      <Switch
        {...getTogglerProps({
          disabled: clickedTooMuch,
          on: on,
          onClick: () => setTimesClicked(count => count + 1),
        })}
      />
      {clickedTooMuch ? (
        <div data-testid="notice">
          Whoa, you clicked too much!
          <br />
        </div>
      ) : timesClicked > 0 ? (
        <div data-testid="click-count">Click count: {timesClicked}</div>
      ) : null}
      <button {...getResetterProps({onClick: () => setTimesClicked(0)})}>
        Reset
      </button>
    </div>
  )
}

export default App
```

## Languages

- English - Intermediate/Upper-intermediate (according to the online test at [EF-SET](https://www.efset.org/quick-check/))
    - ![EFSET results](/images/efset.png)
- Ukrainian/Russian - native