# Class ComponentからFunctional Component に移行する

[How To Convert React Class Components to Functional Components with React Hooks - DigitalOcean](https://www.digitalocean.com/community/tutorials/five-ways-to-convert-react-class-components-to-functional-components-with-react-hooks)  

## 1. State及びライフサイクルメソッドがないCCをFCに移行する

```jsx
import React, { Component } from 'react';

function App = () => {// class App extends Component {
  // alertName = () => {
  const alertName = () => {
    alert('John Doe');
  };

  // render() {
  return (
    <div>
      <h3>This is a Class Component</h3>
      <button onClick={this.alertName}>
        Alert
      </button>
    </div>
  );
  // }
};

export default App;
```

## 2. Stateを`useState`に置き換える

複数のStateはそれぞれ別の`useState`で持つ。  

## 3. `componentDidMount()`,`componentDidUpdate()` -> `useEffect()`  

```jsx

```

## 4. `PureComponent` -> `React.memo()`

```jsx
```
