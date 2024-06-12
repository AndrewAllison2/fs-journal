# REACT

## Imports/Setup
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

  ##### components between Router and Routes persist across pages (ex: Navbar component)

    - import Link component from react-router-dom for routes (see navbar comp in ecommshop)
    ##### Links require a 'to' prop for routing
      <Link to="/"> Home <Link/>

    
## Style
  - create _COMP NAME_ .css in same place as component. Individual style sheets for components/pages