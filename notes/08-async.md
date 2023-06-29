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
  - create editCar button
  - get edit form => copy html form into model
  - swap form to one stored on car model
  - id in html
  - public draw function drawEditForm(carId)
  - add vaules and string interpolate on EditForm
  - get EditForm - app.carcontroller.editCar(event) * pass 2 arguements through* => will pass through each to service
  - edit car from the car controller - async
  - prevent default, find car with id, send to service with new method, pass car method
  - editCar in service
  - put updates in index
  - findIndex/splice
  - add emitter to draw changes

  - store form from html somewhere so we can get it back
  - drawCarForm function in CC
  - listener - this.drawCarForm
  - draw form on page load
  - scroll to and create instance in carscontroller => cool stuff
  

  boostrap.element.getorcreateinstance(#class).show

  in model - static get createForm()
      put html form template

      in draw cars - Car.CreateForm - only exists on the definition of the car class

    static method - have access to it without instanciating the class

  
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

<!-- SECTION UPDATE -->
async editCar(carData){
  const res = await api.put(`api/cars/${string interpolate}`, carData)
  
  const updatedCar = new Car(res.data)

  splice with check
}

supply an id and an object


<!-- NOTE -->
  view api array in console before making a model to make model creation easier by copying object into code to see properties

  name on form handler must match property name in api to store new objects

  .map only exists on an array class

  findIndex can return negative numbers, running splice will delete wrong things



<!-- SECTION WEDSNESDAY LECTURE -->

 <!-- NOTE STEP BT STEP -->

    - env.js fill out
    - create another instance of axios to point towards dnd api
    - create spells controller and load
    - get spells function in controller and pass to service
    - get spells function in serivce
        - append url in get
        - log res
    - call this.getSpells() in controller classs
    - create spells array in appstate
    - store data in appstate
    - create draw function in controller
    - create html template
    - listener to draw spells so it only updates when the appstate changes
    - string interpolate spell.name in li tags => have name property on pojos
    - add onclick to li w/ function to pass index to service => spell.index
    - get spell details(param)
    - pass to service
    - spelldetails in service
    - build class model
        - this.description = data came back as an array, will need to format it to string to store in our api
        - turnary expression for damage type because data.damage doesnt exist and will return undefined
    - create active spell in appstate = null because it is an object
    - store active spell in appstate
    - conroller draw active spell - logged to console, did not build template yet
    - listener to draw when active changes in appstate
    - stub out active template
    - get DetailsTemplate()
    - add button onto temp to save to sandbox api
    - create snadboxspells controller
    - onclick createspell() in model
    - sandbox service
    - create spell uses base url api
    - post(url, body)
    - in model use join to convert array of strings into a string => data.desc.join('/n)
    - create another page to display our spells
    - create view pages and set up paths in router
    - getmyspells() in sb controller and pass to service
    - getmyspells in service
    - listener to get spells when appstate is loaded
    - my spells array in appstate
    - map results => store my spells as spell models in appstate
    - or on data.desc - different prop names so join wont work w sandbox api
    - multiline turnary for damage in model
    - get myspells temp in model
    - sbC draw my spells w listener to update
    - old way get documentbyid in drawmyspells as check to see if that id exists and only set html if it does
    - store id on model so we can target it
    - set active spell function
    - find object in  appstate with spell id
    - set to active in appstate
    - sbC draw myactivespell()
    

    <!-- SECTION AFTER LUNCH -->

    - add checkbox in model for prepare prop
    - onchange toggle function
    -sbc create toggle function and pass id to service
    - togglespellprep in sb service

      -find in appstate => is it true or false
      - put in sbServ - break reference w new object

      find index so we can splice that spell at the same index

        -findIndex
        -post(url, {})
        -splice

    string interp and turnary to assign conditional 'checked' attribute to checkbox in model

    draw spells set up with filter to change spell count => see sbCont draw function

    - checkbox
      can add checked to set default to checked
      add onchange to fire off function just like button/selectable

      pass id since id only exists on sandbox api

      toggle spell preparation
      



<!-- NOTE NOTES -->
  create another instance of axios instead of changing existing one


store pojos in appstate
  can change import to an array of objects for intel

  class role

  overflow-y: auto puts scroll bar on our list => css

  typeof method

  operator



<!-- SECTION THURSDAY LECTURE -->

    params object with api key in env
      params: {api_key: 'api key'}

    will get error if api requires key and do not have one
      - can set in axios so it auto formats the key for every request we make
      - can query api from service

    ? key value pairs to query apis

    create controller and get object in console
    create model using that object
    set up place to store in appstate


<!-- REVIEW SET RANDOM PIC AS PAGE BACKGROUND -->
    const picture = appstate.picture

    const htmlBody = document.body

    htmlBody.style.backgroundImage = `url($picture.imgUrl)`

    then style w css

    psudo class hover in css in dark-card
      transition on the class always

    on-hover util class => hides everything inside, hover on parent elem brings anything w on-hover prop into view

<!-- SECTION QUERY -->

    create form w button to submit
    in draw in controller we need to caputre form data
    put name on the form input field in index.html


    getter in service we will string interpolate form data
      -form data is an object so we have to drill into it to pull out the search
        ${formData.search}
        %20 is url character for space => axios will auto format this


    target="_blank" => opens link in new tab

<!-- SECTION SAVE PICTURES TO SANDBOX API -->

    button on html in model
    create controller/service to deal with sandbox api
    write createPicture method through both
    in service make post request to store picture on api


    Update Model
      added:
      - id - sandbox id
      - turnary on date
      - added or where needed on properties

<!-- SECTION REQUEST SAVED PICTURES FROM SANDBOX API -->

    sandbox controller - get saved pictures
    appstate.on('account', getMyPictures)

    map response into appstate

<!-- REVIEW DELETE REQUEST -->

  button function pass id through
  delete() - where and what 
  find index and splice from appstate