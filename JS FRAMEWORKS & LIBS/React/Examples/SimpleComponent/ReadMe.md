# React

## Simple Component

```jsx
import React from 'react';
import './App.css';

class App extends React.Component {

		myName = "Webia1";
		constructor (props) {
		    super(props);
		    this.state = {
			    myName: this.myName
			};
		}

```