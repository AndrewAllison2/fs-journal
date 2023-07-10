# Node


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