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



<!-- SECTION NOTES TUESDAY -->

  env.js environment
  
  - change environment base url
  - create cars controller and mount
  - create path for cars in router
  - nav bar add button for cars page
  - in controller use method to get data from api
    async getCars()
  - create service, export new service
  - bring in axios api instance
  - get(appended url)
  - this.getCars in controller - exists in class so this for this class
  - create model for cars
  - new Date(data.createdAt) - date object to format date
  - this.creator = data.creator - nested object does not change process today
  - create car array in appstate
  - map data into array
  - store in appstate
  - listener to draw cars in controller
  - create get for template in model
  - write draw function
  - create form to submit cars
  - in controller createCar()
  - form handler
  - send to service => pass cardata down through function to service
  - post method in service
  - domain/audience/client copy past int env.js from auth0 api
  - log from controller to service to make sure data goes down
  - store new car object in appstate => push builtCar
  - emit to draw cars in appstate
  - create delete button on model html
  - create delete function in controller
  - pass delete to service and use delete method
  - pop.confirm check on delete button
  - car deleted from api but need to remove from appstate
  - use find index and splice to find and remove car from appstate
  - check after find index to make sure found correct object
  - emit to draw cars on delete
  - get computeDeleteButton in model => only have button if i am creator
  - appstate.account.id => id created by api stored in appstate on car models
  - listener in cars controller for the account property to draw button on loggin/reload
  - button d-none class
  - function to take class off of button
    

  
  <!-- SECTION Post -->

  in service - 
  async createCar(carData){
    const res = await api.post('appended url', body/payload)
  }
  async createCar(carData){
    const res = await api.post('api/cars', carData)
  }

<!-- SECTION DELETE -->

  async deleteCar(carId) - try/catch => send to service w carId

  in service
    put id in url of delete request
    delete requests only have appeneded url DO NOT have body

  async deleteCar(carId)
    const res = await api.delete(`api/cars/${carId}`)  

const carIndex = appstate.cars.findIndex(c => car.id == carId)
if(carIndex == -1){
  throw new Error()
}

appsate.cars.splice(carIndex, 1)


function _showFormButton(){
  if(!account){
    return
  }
}



<!-- NOTE -->
  view api array in console before making a model to make model creation easier by copying object into code to see properties

  name on form handler must match property name in api to store new objects

  .map only exists on an array class

  findIndex can return negative numbers, running splice will delete wrong things