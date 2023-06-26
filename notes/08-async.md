# Async


<!-- SECTION MONDAY LECTURE -->

    Application Programming Interface

    log data from api to console
     - create controller
     - request data from the api
        in controller: getMonsters() (see try\catch)
        error message in catch to update on errors
      - create Service - link to method in the controller
      - in service getMonsters() => fetch
          async --- await
      - response returned and needs to be converted
          see THE HARD WAY
      
      - add script tag for axios
      - create axios service
        export const zeldaApi = axios.create({
          baseURL = '' - generic url usually listed on api
          timeout: 8000 - gives timeout to get data, if interval ends it will throw an error - trigger catch - pop message in consoel
        })

      - monster service (const response is what we call variable almost every time we request data from api)
            const response = await zedlaApi.get()

      - async and await in getMonsters() in controller so the service can run code before controller runs try\catch
      - create class model to store objects in appstate
      - store data in appstate
          - in service
              const arrayOfMonsters = response.data.data.map(monsterPojo => new Monster(mosterPojo))
          save to appstate
      - create draw function
      - add listener to draw
      
    


    
    
    
    try catch - if error happens, stops running code at try and catches error => runs code inside catch
      see Monsters Controller

      try catch will carry through with any other functions, error in service will still trigger catch in controller

      ftech request takes time to run, java runs fetch and immediately logs response, needs to await
        fetch data but wait for data to come before logging response

    promise pending => did not wait for promise to be resolved




    <!-- REVIEW NETWORK TAB -->
    status: 200 http response code => successful request
    status: 404 => not found = usually issue with request url
    status: 405 => method not allowed