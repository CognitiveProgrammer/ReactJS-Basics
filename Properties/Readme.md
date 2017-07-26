# ReactJS [2] - The Properties

__Properties__  _are the communication mechanism between_ __Components__. _All ReactJS Components can send and receive properties_.

## 2.1 - Passing Properties in the Components

_Just like HTML Tags properties, ReactJS components can pass the properties using similar syntax. For example, if we want to Pass a poerty in_ __FirstReactCompoent__ _we made in last chapter, we'll do something like this_

```
ReactDOM.render(<FirstReactComponent Param="ABCDEF"/>, document.getElementById('root'));
```
_Here we're passing a_ __Param__ _with value_ __"ABCDEF"__ _as property in_ __FirstReactCompoent__

## 2.2 - Accessing Property inside Components

_Now we know that component properties can be passed as paramaters similar to that of HTML tags. but inside the compoent we need access the property to be able to do something about it_.

_ReactJS components receive the properties as class member_ __this.props__. _We can use_  __{this.props.propertyname}__ _(enclosed in curly braces} to access the property inside the class as in example below_

```
class FirstReactComponent extends React.Component {
 render() {
  return (
   <h1>Hello {this.props.Param}</h1>
  );
 }
}

ReactDOM.render(<FirstReactComponent Param="ABCDEF"/>, document.getElementById('root'));

```
_We can use the properties inside the components multiple times using the same syntax_

```
class FirstReactComponent extends React.Component {
 render() {
  return (<div>
   <h1>Hello {this.props.Param}</h1>
   <h2>{this.props.Param}</h2>
  </div>
  );
 }
}

ReactDOM.render(<FirstReactComponent Param="ABCDEF"/>, document.getElementById('root'));

```

## 2.3 - Passing Multiple Properties

_There is no limit to number of properties which can be passed inside the ReactJS components using HTML tags like syntax. For example our_ __FirstReactComponent__ _can very well handle multiple properties as depicted in code below_

```
class FirstReactComponent extends React.Component {
 render() {
  return (<div>
   <h1>Hello {this.props.Param1}</h1>
   <h2>{this.props.Param2}</h2>
  </div>
  );
 }
}

ReactDOM.render(<FirstReactComponent Param1="ABCDEF" Param2="123456"/>, document.getElementById('root'));

```

## 2.4 - Multiple Instances of Compoenents with Different Properties

_When we call a component enclosed within_ ```<>``` _, it creates a unique instance of the component. When we call the component multiple time with different property values, it acts as a different instance with different property values. For example, we are create two instances of_ __FirstReactComponent__ _below_

```
ReactDOM.render(<div>
    <FirstReactComponent Param1="ABCDEF" Param2="123456"/>
    <FirstReactComponent Param1="abc" Param2="xyz"/>
  </div>,
document.getElementById('root'));
```

## 2.5 - Chaining Properties

_The way we are calling Compoenents with static values inside_ __ReactDOM.render(...)__ _function, the same way can be used to call a compoennt with associated property inside the component_ __render(...)__ _function_

```
class SecondReactComponent extends React.Component {
  render() {
    return(
      <h2> Thank you for passing the Value => {this.props.SecondParam} </h2>
    );
  }
}   
class FirstReactComponent extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello {this.props.Param}</h1>
        <SecondReactComponent SecondParam="12345"/>
      </div>
    );
  }
}

ReactDOM.render(<FirstReactComponent Param="ABCDEF"/>, document.getElementById('root'));

```
_However, its possible to send the dynamic values to_ __SecondReactComponent__ _by using the component properties values as depicted in example below_

```
class SecondReactComponent extends React.Component {
  render() {
     return(
      <h2> Thank you for passing the Value => {this.props.SecondParam} </h2>
    );
  }
}   
class FirstReactComponent extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello {this.props.Param}</h1>
        <SecondReactComponent SecondParam={this.props.Param}/>
      </div>
    );
  }
}

ReactDOM.render(<FirstReactComponent Param="ABCDEF"/>, document.getElementById('root'));

```
_In this case, we're propagating the values received in_ __FirstReactComponent__ _to the_ __SecondReactComponent__ _using access properties syntax._ 

## 2.6 - Summary 

__Properties__ _allows us to communicate between components using statuic and dynamic values._
