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
                <Route path="/" />
                <Route path="/cart" />
              </Routes>
            </Router>
          </div>
        )