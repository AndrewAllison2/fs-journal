# REACT

## Imports/Setup

__Getting Started__
  npm create vite@latest _Project-Name_ -- --template react

    - note that react can be changed for other frameworks like vue

  - rafc = React Arrow Function Component => this is good for scaffolding components
  - rafce = React Arrow Function Component Export

## Routing
    - install react-router-dom in dependecies
    - import {BrowserRouter as Router, Routes, Route} from react-router-dom
    -set up router in App.jsx

        return (
          <div>
            <Router>
              <Routes>
                <Route path="/" element={ <Home /> }/>
                <Route path="/cart" element={ <Cart /> }/>
              </Routes>
            </Router>
          </div>
        )

###### Button/Link Routing To Pages
  - import { useNavigate } from "react-router-dom";
  - const navigate = useNavigate()
  - onClick={() => navigate('/')}


  ##### components between Router and Routes persist across pages (ex: Navbar component)

    - import Link component from react-router-dom for routes (see navbar comp in ecommshop)
    ##### Links require a 'to' prop for routing
      <Link to="/"> Home <Link/>

    
## Style
  - create _COMP NAME_ .css in same place as component. Individual style sheets for components/pages

## MAPPING DATA
  {_array-name_.map((item) => (<Component data={item} key={item.id}/>))}


# STATE MANAGEMENT
  - use context to manage single state across multiple components (see ecommshop1 shopContext)


# CONDITIONAL RENDERING


