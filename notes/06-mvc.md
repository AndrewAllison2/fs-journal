# MVC

      bcw create in cmd line
      mvc

  bootstrap is already brought in
  
  
  class
    classes are capitalized and colored green

  constructor()
    this is similar to calling functions at bottom of js
    run code when class is built out

  new

  this - refers to property on same object

    <!-- NOTE -->
      store global variables in app State now

  autocomplete import 
  error 404 = check import syntax first

  GET
    get MUST return a value
    get DOES NOT take in any parameters


    Export:
      strings
      functions
      array
      booleans

      <!-- NOTE -->

      CLASSES
        bundle like things together to send collections of data out to the application

        store variables, functions
        can export that class

        method is function written inside object

      <!-- NOTE -->
        Service
        encapsulated controller
        used for security
          only thing that changes out data on our models (app state)

          view => app.js/router.js => controller => service => models(app state)


    export - all controllers need to export to run
    constructor - run code when class is built out
    import to router.js
    method inside constructor


    export class NameOfFile {
      constructor(){
      }

      method(){

      }
    }


  underscores _ before private functions

<!-- SECTION SERVICE -->
  do not generally have constructor

  don't export class

  class PlayerService{

  }

  export const playerService = new PlayerService()


<!-- SECTION MVC LECTURE 9/20 -->


    <!-- SECTION Step by Step -->

      1. remove view in html and router =>router path/view =''
      2. create coin variable in AppState in class Observable AppState   coins=0
      3. created sections/page layout in html => coin section and button
      4. create coins controller to add coin on button click
          -export = first thing we add
          - class = what are we exporting
          - name = name of controller
          - constructor - every time we build controller run code in here
          - log if controller is hooked up
          - go to router and choose what contoller we are using !!!Import controller to router!!!

          export class CoinsController(){
            constructor(){
              console.log('')
            }
          }

          Should log to console, controller is mounted
          console should see coins controller

      5. write method in coins controller - must be inside of export class for index to use it - console should see app.coinscontroller.method
      6. hook up button in html => must tell it where to find method => app.Coinscontroller.addCoin()
      7. changing variable in appstate so we need a service to change that variable => create serviceController
      8. build coins service class and export
      
        class CoinsService{

        }
       export const coinService = new CoinsService()

      9. import coinsService to coinscontroller
      10. create method in coins controller = ctrl click to create in coins service => addCoin()
      11. coin service - const coins = appstate.coins => bringing in coins from appstate
      12. increase coins => appstate.coins++ - increases value stored in the app state
      13. update html => coinsController
      14. private functions at top of CC above export function
          _drawCoins()
          set id in html - coinCount
          set text => 'coinscount', appstate.coins
          call draw function
          let stringofcoins = ''
          for loop in draw coins to change number to coin emoji
      15. create class model for gatchamon => gachamon.js

           export class Gachamon{
            constructor(data){        passing through an object that we can drill into and pull properties
              this.name = data.name
              this.rarity = data.rarity
              this.emoji = data.emoji
            }
      }
      
      16. go to appstate and create array of gachamon => 
          gatchamon = [
          new Gachamon({name: '', emoji: '🪨', rarity: ''})
          ] 
      17. type in appstate abv gatchamon array - change value to array of gachamon for better intel
      18. debugger in model under consrtuctor
      19. create gachamon Controller - import appstate

          export class GachamonsController{
            constructor(){
              console.log(AppState.gachamon)
            }
          }

          link to controller in router => can pass array of controllers - make sure to import
          should log our gachamon to console now

      20. in gachamon model - 
            get gachamonsmalltemplate(){
              return `
              smallGachamonTemplate`
            }

            write html in html file NOT java!

      21. write html that we will change *selectable class in bootstrap so we can click it, elevation adds some shadow to element, title tag adds lil text when you hover
      
      22. copy code and move it to class models, 
      23. go to Gachamon controller to draw them
      24. function drawGachamon
          placeholder string = ''
          forEach
          set html => id in html (gachamonCatalog)
          call on page load = inside constructor
          in model - string interpolate ${this.name}
          should draw each gachamon to page

          do not have to invoke gets

      25. gacha model
          onclick on our html = app.GachamonsController.showcaseGachamon('')

          call inside class def in gachamonsController
          in model - pass property through showcase to know which one we click
          in controller - set parameter - gachamonName
          create gachamonsService

            class GachamonsService{

            }
            export const GachamonService = new GachamonService()

      26. find gachamon in gachamonservice
      27. pass gachamonName from gacha controller to gacha service ex line 22-25 in gachamonsController
      28. draw small one to page on click
          - create variable in appstate to store single one => activeGachamon = 0 - you dont have value
          - Gachamonservice => appstate.activegachamon = foundgachamon
          - logging appstate should add one we clicked to activeGachamon
          - gachamonsController => drawActiveGachamon()
      
      29. create element in html - style w css if you want to
      30. copy code - comment out - write get in gachamon model => gachamonLargeTemplate
      31. id in html => activeGachamon
      32. string interpolate in model to draw active mon
      
      <!-- SECTION add coins and purchase -->

      33. button onclick='app.gachamonsController.rollForGachamon()
      34. Gcontroller => write method roll4Gachamon()
      35. all business logic done in service => serviceGachamon.roll4Gachamon
      36. write in gSrvice
      37. write our logic check
      38. add listener in the coins controller
      39. in Gservice get random gachamon
      40. create myGachamons array in appState
      41. in Gservice push randomG into aappstate
            appstate.mygachamons.push(randomGachamon)
      42. add lsietner on Gcontroller
      43. id in html
      44. in Gcontroller create drawMyG function
      45. trigger listener in G service (see below)
      46. service will handle local storage
      47. 


          

    <!-- SECTION NOTES -->

      2. create variable that goes up on button click
         no model because it is just a number incrementing by 1

         use new to create new version of a class

         listener = .on
          says that anytime coins changes in the appState it will call drawCoins

          in coins controller in constructor
          appstate.on('coins', _drawCoins)

          manual trigger listener = appstate.emit(event)
          appState.emit('myGachamons')



  <!-- SECTION STEP by STEP -->

    1. Router - change html on home page in view
    2. R - Set up new router path
      - path
      - controller
      - view start small - h1 on page
    3. Create new controller -cars controller
    4. Index - create another link in navbar
    5. Index - stub what we want cars page to look like
    6. Index - stub out car template
    7. CarView - Abstract car view out to keep router clean
        export const CarView = ` STUBBED HTML `
        import car view into router
        change view in router to CarView
        injects car temp when car button clicked
    8. Models - create car model
        constructor(data){
          this.make = data.make
          this.ect = data.ect
        }

        Generate ID => utility class
          this.id = generateID()
    9. CarModel - get card template
        move html into get
    10. Appstate make car
    11. Cars - Date()
        this.listingdate = new Date()
    12. CarCont - log cars in colsole
    13. Car Cont - create private draw function
    14. id in carview - carListings
    15. set html in CC
    16. call draw function in CarsC class
    17. model - string interpolate
    18. Owned By GMa
        computeGrandmaBanner
    19. Create Form
        - paste collapse in carview
        - create form inside of collapse in carview
        - 
    20. Inline style
    21. write form in html
        - name on input matching objects in array so it will format a new object in array with those properties
        - look at the input types and forms
    22. move form to CarsView
    23. onsubmit event => createCar
    24. CC write create car function 
          ! pass event through // prevent default so page wont reload
          test small - log if form submits

          const form = event.target
          const carData = getFormData(form)  ==== utility class

          carData.ownedByGrandma = carData.ownedByGrandma == 'on' ? true : false   a one line if statement => 
            if carData.ownedByGrandma is 'on' return true, otherwise return false
    25. store data in appstate => carService
    26. create carService
    27. CC call create car and pass car data through to service
    28. Write method in CS
        turn car data into new car model
          createCar(carData)
            const newCar = new Car(data)
            appstate.cars.push(newCar)
            appstate.emit('cars')
    29. Listener in CC
        appstate.on()
    30. Cs save cars function - utility -- call on push
    31. appstate load cars
    32. delete items
          cm -create button on eash that deletes
          pass id through
          write function in CC - pass param down
          pass id to service
    33. Service deleteCar()
          findIndex()
          splice()
          savecars()
          emit()
  



  <!-- SECTION NOTES WEDNESDAY -->
    router is an array of objects
    provide path\controllers\view
    a href = link tag in html
    only loads contollers that router has called after load
    if view is nothing it won't overwrite last page

    date class
        Date()

        if no arguement will give you current date from system internal clock
        can pass arguments to get specific date

        since Date is a class it has methods we can use it
        toLocaleString() => format date to standard

        add required attribute to forms to have that check before submit
        required on checkbox means must be checked

        || default => see cars model for use

        Splice
          can add or remove objects from an array
          splice(start, delete count)

<!-- REVIEW  -->
  input types in html



<!-- SECTION THURSDAY LECTURE -->
    1. started with model - case.js
    2. get listTemplate so we can get a page draw - case.js
    3. create data to work with - appstate
        new case
    4. set date and unlock automatically
        new Date turnary
        unlocked turnary
        || or statement 'no report'
    5. draw data - create controller
    6. create cases service
      singleton => dont export service
    7.draw case list
    8. create place in appstate to store active case = null
    9. set up active case from case controller to appstate
    10. draw active case
    11. create get Redacted Template in case
    12. case.js - create logic for locking/unlocking
    13. create bad words array in appstate
    14. split array into words in case model
    15. map function => creates copies of array with results of function
        let arr = this.report.split(' ') {
        let mapped = arr.map(word => {
          if(_badWords.includes(word.toLowerCase())) {
            return '⬛'
          }
          return word
        })
        return mapped.join(' ') ==> splitting and joining on the space
        }
    16. create form - html


    ... => spread object = takes objects out of original array and puts them in new array with added objects = similar to push but triggers emit

    text area CC - on blur  - when someone leaves text area

      create interval functions in controller 

    in draw temp += cases.length

    or

    id in router, set text to id in draw

    get can create new firmat for stored data


