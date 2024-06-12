# REACT

## Imports
  __Routing__
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

    