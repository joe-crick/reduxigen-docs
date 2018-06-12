# Quick Start

## Configure

1. Create a default state

```javascript
export default {
  test:""
}
```

2. Create a store

```javascript
import { createStore, applyMiddleware } from "redux";
import thunk from "redux-thunk"; // If you're using thunks
import { rootReducer } from "reduxigen/actions";
import DEFAULT from "state";

export default createStore(rootReducer(DEFAULT), 
   applyMiddleware(thunk));
```

### Create Actions

```javascript
import { update } from 'reduxigen/actions';

// Note that the value "test" corresponds to the "test" 
// field in the state object.
export const setTest = update("test");
```

### Connect the Actions to Your Component

```javascript
import React from 'react';
import * as actions from './test-actions';
import { connect } from "react-redux";

export const Test = ({test, setTest}) => 
   <button onClick={setTest}>{test}</button>;

const mapStateToProps = state => ({test: state.test})

export default connect(mapStateToProps, actions)(Test);
```

