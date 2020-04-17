# Front-End Web Development with React
- Course: Front-End Web Development with React

Started: 14.04.2020

Source code is in private repository, because Courseras Honor Code forbids sharing of content which is required for peer review assignments.

# Week 1

`yarn add create-react-app@1.5.2`
`create-react-app confusion`
`cd confusion`
`yarn start`

Error message:

> A template was not provided. This is likely because you're using an outdated version of create-react-app. Please note that global installs of create-react-app are no longer supported.

I switched therefore to the current method provided by
https://create-react-app.dev/docs/getting-started/

`npm uninstall -g create-react-app`
`rm -rf confusion`
`yarn create react-app confusion`
`cd confusion`
`yarn start`

Now there is a template, so `yarn start` works.

```
yarn add bootstrap@4.0.0
yarn add reactstrap@5.0.0
yarn add react-popper@0.9.2
```

https://reactstrap.github.io/

Installed https://atom.io/packages/language-javascript-jsx, because Atom Beautifier looked terrible, but did not really help.


### Array.prototype.map

https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Array/map

```
const menu = this.state.dishes.map((dish) => {
    return (
      <div key={dish.id} className="col-12 mt-5">
        <Media tag="li">
          <Media left middle>
              <Media object src={dish.image} alt={dish.name} />
          </Media>
          <Media body className="ml-5">
            <Media heading>{dish.name}</Media>
            <p>{dish.description}</p>
          </Media>
        </Media>
      </div>
    );
});
```

### state

do not access it directly, use .thisSetState

### react developer tools

Inspect state of components:
https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi/related?hl=de

### Pass id back to another parent component (click event)

In the MenuComponent.js:
```
    <Card onClick={() => this.props.onClick(dish.id)}>
```

In the MainComponent.js, take id and execute method:
```
  <Menu dishes={this.state.dishes} onClick={(dishId) => this.onDishSelect(dishId)} />
```
### Functional components

https://reactjs.org/docs/components-and-props.html

```
  <RenderDish dish={props.dish} />
```

```
  function RenderDish({dish}){
        return(
```


```
import React from 'react';
import { Card, CardImg, CardText, CardBody,
    CardTitle } from 'reactstrap';


    function RenderDish({dish}) {

      . . .

    }

    function RenderComments({comments}) {

      . . .

    }

    const  DishDetail = (props) => {

      . . .

    }

export default DishDetail;
```

Is used afterwards with ```<DishDetail dish={myDish} />```

2Read: https://levelup.gitconnected.com/react-component-patterns-ab1f09be2c82



#### Functional Stateless Components in React
https://www.jackfranklin.co.uk/blog/functional-stateless-components-react/

```
const Username = function(props) {
  return <p>The logged in user is: {props.username}</p>;
};
// OR:
const Username = ({ username }) => <p>The logged in user is: {username}</p>;
```

See also: https://tylermcginnis.com/functional-components-vs-stateless-functional-components-vs-stateless-components/


## Week 2

### React Router

```
yarn add react-router-dom@4.2.2
```

### .bind

```
constructor(props){
  super(props);

  this.state = {
    isNavOpen:false
  }

  // we need to bind the function, to use it in render (alternative: arrow function inline)
  this.toggleNav = this.toggleNav.bind(this);
}

toggleNav(){
  // negating the value
  this.setState({isNavOpen:!this.state.isNavOpen});
}

```


### .filter

only use dishes which have .featured=true, use first array item
```
        <Home dish={this.state.dishes.filter((dish) => dish.featured)[0]} />
```

Render it in a component (given as props):

```
import React from 'react';
import { Card, CardImg, CardText, CardBody,
    CardTitle, CardSubtitle} from 'reactstrap';

function RenderCard({item}) {

    return(
        <Card>
            <CardImg src={item.image} alt={item.name} />
            <CardBody>
            <CardTitle>{item.name}</CardTitle>
            {item.designation ? <CardSubtitle>{item.designation}</CardSubtitle> : null }
            <CardText>{item.description}</CardText>
            </CardBody>
        </Card>
    );

}

function Home(props){
  return(
       <div className="container">
           <div className="row align-items-start">
               <div className="col-12 col-md m-1">
                   <RenderCard item={props.dish} />
               </div>
               <div className="col-12 col-md m-1">
                   <RenderCard item={props.promotion} />
               </div>
               <div className="col-12 col-md m-1">
                   <RenderCard item={props.leader} />
               </div>
           </div>
       </div>
   );
}

export default Home;
```
