# Node


REQ, RES, NEXT

<!-- REVIEW -->
  > ORM's and what's used when interacting w/ MongoDB
      mongoose
  

  > MongoDB Relationships
      - 1:1 => embedding whenever possible

      - 1:N => embedding can work on low write traffic apps
               linking works but can have lots of reads on DB
               bucketing when possibility of splitting documents into descreet batches

      - N:M => 2 way embedding
               1 way embedding
               Third Collection embedding - most effiecient



<!-- SECTION MONDAY LECTURE -->

  <!-- NOTE -->
    comment out code in main.js and Startup.js


   <!-- NOTE GETTING STARTED -->
      -   created cats controller - all controllers load through startup
      - all controllers in node 'inherit' class

        export class CatsController extends BaseController{
          constructor(){
            super('api/cats')
            this.router
            .get('', this.getCats)
          }
        }

        .get actually comes after the router this.router.get()

        super = calls contructor on base controller to run code

        bring in router from base controller to cats controller to accept requests from client

<!-- REVIEW -->
      all methods in controller take in 3 arguments
        - req, res, next

          request from client (body/payload/token/ect)
          response object - what we send back to the user
          next - default error handling, goes inside our catch


<!-- NOTE SAVE AND RESPIN SERVER IN VS TO UPDATE LOCALHOST FOR ANY CHANGES -->

  <!-- NOTE FAKE DB -->

      - created fakeDB in db file => not using actual database today
      - export data to bring in elsewhere

      catsController
        - res.send(cats) - don't want to do in controller => still using mvc pattern w/ service

  <!-- NOTE CATS SERVICE -->

      CC - const cats = await catsService.getCats()

      alias out response to send to user

      CS - return cats => service returns cats, const cats is now the response of cats in api, send cats to client


  <!-- SECTION NEW METHOD -->

    CC - .get('/:id', this.getCatById)

    string appended to url
    /: express knows this is a property that the user can change

    write getCatById function

<!-- REVIEW BREAKPOINTS AND DEBUG TOOL -->
      - click red dot on left of code to set breakpoint
      - breakpoints are debugged within vs code
      - code pauses when hitting bp and options to run in dev tools in vs
    


  req.params => cat object had params on it that contain id


    const catId = req.params.catId

    const cat = await catsService.getCatById(catId) => send to service

    use id and find method to fins the cat with that id
      return found cat => return value from find function

  <!-- NOTE NO FOUND CAT ERROR HANDLING -->

    CS conditional statement
      if(!foundCat){
        throw new BadRequest
      }

  <!-- SECTION POST CATS -->

    CC - .post() => under get requests

    .post('', this.createCat)

    createCat(req, res, next){
      const catData = req.body
    }

    request stores data in body

    use postman to see the post request is working

    create cat in service
    give it id and push it to array


  <!-- SECTION POSTMAN -->

      mocks built client and sends requests


  <!-- SECTION DELETE CATS -->

      .delete('/:id', deleteCat)

      findIndex to find the cat by id we cant to delete
      set up conditional for error handling
      splice foundcat out of the array
      dont need to return anything because we are just removing an object

  <!-- SECTION PUT -->

      put('/:catId', updateCat)

      need info to update - req.body

      pass 2 params through (catId, catData)

      catToUpdate.name = catData.name => only allow changes to name, cant store any random info in database

      use checks (or, if) to keep default from setting properties to null

<!-- SECTION END OF MONDAY LECTURE NOTES -->



<!-- SECTION TUESDAY LECTURE NOTES -->

    Env.js
      - set up database connection

!!! DO NOT PUSH ENV TO GITHUB !!! => template set up for git to ignore this file 

  <!-- NOTE FILL OUT ENV -->
      - go to mongodb and get connection string in drivers, paste in .env
      - replace password with your user password in the connection string, password must be url safe
      - port defaults to 3000, dont need to fill it out
      - get domain, client id from auth0 => app/app/myapp || audience => api tab => copy paste into .env
      - go into env.js is client folder and fill out auth0 credentials
      - add string before ? on connection string to create a new collection on mongodb
      - backend should serve and connect with mongo db

  <!-- NOTE MAKE SURE TO SPIN UP PROJECT FROM THE CORRECT FOLDER -->

    Schema allows for validation checks on the backend

  <!-- SECTION SCHEMA -->
      car.js - export const CarSchema = new Schema{}

        ALL SCHEMA MODELS WILL FOLLOW THIS FRAMEWORK BELOW

      import mongoose
      export const *datatype*Schema = new Schema{
        property: {type: string/number/bool, required: true/false, max and min length}
      }

  <!-- NOTE ENUM MEANS IT HAS TO BE ONE OF THESE THINGS --> see engine type in cars.js
          enum: ['', '', '']

  IN VALUES.JS COPY TIMESTAMPS: TRUE AND PASTE IN MODEL => SEE CARS.JS

  <!-- SECTION DB CONTEXT.JS -->
      reference values and accounts

      plural datatype = datatype.model('data name', dataschema)


  <!-- SECTION CONTROLLER -->

    export class TypeController extends Basecontroller{}

  <!-- SECTION SERVICE -->

      async getCars(){
        const cars = dbContext.Cars.find()
      }

      find is a mongoose method and different than find in javascript

  mongoose translates mongoDb binary script into javascript

    dbDatabase.collection => mongoose method

    mongoose create makes a new car object and stores it in the database -- do not need to push
    mongoose - create, find


  STORE CREATOR ID ON SCHEMA AS REQUIRED TO AUTHENTICATE USERS AND ACTIONS - see cars.js

  <!-- SECTION MIDDLEWARE -->
      controller
        .use(Auth0Provider.getAuthorizedUserInfo)
in
        everything under this now requires you to be logged in

    Postman - authorization/bearer token -> get and paste into postman to get authorization

    in controller - carData.creatorId = req.userInfo.id

    this will create and/or overwrite the id sent up when making requests => defensive coding


  removeCar
    - null check with get car by id => set up error handling in function
    - .remove() will clear it out of the database

    alias and get the user id in the controller, pass car id and user id to service

<!-- REVIEW DELETE IN SERVICE AND CHECKS -->

    after changing properties --- originalCar.save() => mongoose method, update properties, save to db, send to user


<!-- NOTE IF CLONING DOWN GO TO CONSOLE, CD INTO GREGSLIST NODE SERVER, RUN NPM I -->



<!-- SECTION WEDNESDAY LECTURE DATA-->
DATA RELATIONSHIPS

    - 1 to Many - many pages point to 1 book, but 1 page will never point to 2 books

    - Many to Many - 2 way street to find info stored in database by ids

  
