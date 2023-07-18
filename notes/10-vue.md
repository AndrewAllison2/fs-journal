# Vue

<!-- SECTION -->
## Monday Lecture 'Intro to Vue'

    main.js is entry point into our app


  - all files now have html, java, and css in same place

  - style scoped will scope to only its containing component

  Vite is used to spin up page through run/debug => vite doesn't require respin or refresh to show changes


router view ties to router.js - points to pages where we will inject vue pages

1. Pages -> HomePage -> template
  - can start wrting html in template tag
  - scoped css only applies to elements in file
  - variable in return object (cheese: 0) script tag
  - double curly bois with the variable name to inject javascript

 <!-- NOTE  -->
 # {{variable name}} INJECT JAVASCRIPT INTO HTML

 anything javascript we want to access MUST be inside the return object

 ERROR - accessed during rended but not defined on instance => variable is outside of return object

 anything in setup above return object is private function/variable

 Return something thats private to make it public


2. Onclick Script-Homepage
    - img v-on:click="mineCheese()"
    v-on:click--- vue version of onclick

### Reactive Cheese
  - let cheese = ref(0) - takes inner value and returns mutable ref object
  - cheese.value++   --- drill into cheese to pull value and increment

    - ref takes value and wraps it in listeners and other built in reactivity

<!-- NOTE -->
## Use logger instead of console log

3. APPSTATE
    - put cheese object inside const export appstate
        - under account -> write our variables

4. Bring in Cheese from Appstate
    - in return object
      - cheese: Appstate.cheese - import appstate and inject into html

      above is non reactive, below is reactive

      cheese: computed(() => {return Appstate.cheese})

      computed is a function that takes in function as arguement and returns value you want reactive

      implied return = only points towards one value to return, doesn't need curly bois

      this is controller and shouldnt change things in appstate => create service

5. Service
    service does not change within Vue
      - homepage -> cheeseService.mineCheese() --- may have to manually import -> vue file talking to java file
      - service -> appstate.cheese++

  can rename things from appstate within components if desired


6. Upgrades
  - create upgrade model
    
  - APPSTATE -> create upgrades in appstate and write data for it

    use dev tools to see it in appstate

  - Home Page -> upgrades: computed(() => Appstate.upgrades),

  Draw to Page
    v-for=
      - div v-for="upgrade in upgrades"
                  upgrade = alias out each object in collection
                  upgrades = the array we are looking through

        -key = unique property for each object -> name is our property for out upgrades
        :key="upgrade.name" -> colon binds it to each iteration

7. Upgrade Buttons
   property binding - key to v-for is binding

   data binding - conditionally bind class, if upgrade is type click, provide btn success
   :class="{'btn-success': upgrade.isTypeClick,}"
    everything after parens is javascript when databinding

    - colors, font weight, disabled attributes


8.  Buy Upgrade
  @click same as v-on same as onclick
    @click button buyUpgrade
    can pass entire upgrade as arguement in funtion


9. Click Power Compute
    clickPower: computed(() => {
      const clickUpgrades = appstate.upgrades.filter( u=>u.isTypeClick)
      let total = 0
      clickupgrades.forEach(u => total += u.multiplier * u.quantiy)
      return total
    })

10. Components
    - .vue files

    - vt - generate template
    paste html
    <component />

11. V-IF
    - v-if="autopower > 0" => only render span if this is true

    v-if => great for rendering things if user is logged in
<!-- NOTE -->
### Vue Dev Tools

<!-- SECTION -->
# Day 2 Lecture

<!-- NOTE -->
#### AXIOS API KEY
  setting up new instance of axios with api key

  _Axios Service_
  params: key value pair, will append it to end of url
  can store multiple values to append and query - ex: filter by rating
  can store strings as keys -> can drill into string objects

  keep this as basic as possible 
    axios service - export const movieApi = axios.create({
      baseUrl: "",
      timeout: ,
      params: {
        api_key: ""
      }
    })

<!-- SECTION -->
#### Getting Started
  Homepage.vue -> start here most of the time
    
    onMounted - constructor inside controller that runs on page load
    in setup - 
      onMounted(()=> {
        logger.log('')
      })

  in setup -> private function to get movies that onMounted will call
    - onMounted will call get movies every time the home page loads (component loads) -> any .vue can use lifecycle hooks
    async function getMovies()

  Movies Service
    get movies

- create class model with data we return from api
    this.poster = `url/${}`

- movie array set up in appstate, add intel line
- map movies and store in appstate
<!-- NOTE -->
 Check log from console to check where data is stored!

Data dump
  - {{movies}}
  - movies: computed(()=> Appstate.movies) - get movies from appstate so we can use in html

<!-- NOTE -->
 Setup is for private functions, lifecycle hooks (onMounted) is used to call functions on page load

<!-- SECTION -->
#### Drawing Movies
    - v-for="movie in movies" :key="movie.id"
    {{movie.title}}

  movie - alias of each object in appstate array, movies - array of movies in appstate
  movie only exists in div containing v-for

:attribute - bind property from javascript
img :scr="movie.poster"

<!-- SECTION -->
#### ADDING MORE PAGES
  appstate - create place to store pages
    page: 0
    totalPages: 0
  service - store page and total pages in the appstate from getMovies()

  compute pages in setup == page: computed(()=> appstate.page)
                            totalPages: computed(()=>appstate.totalpages)

  inject into html with {{}}
  add in buttons for page nav
  @click="getNextPage()"

  write getNextPage function in return and pass to the service
  string interpolate inside of url to format query and increment
  map, add to appstate, (reusing same code from get movies except 1 piece)

  <!-- NOTE REFACTOR -->
    attach this method to each button, interpolate and increment
    async getNewPageOFMovies(pageNumber)
    pass to service

    interpolate page number we passed down ${pageNumber}

    attach this method to both buttons
- Button for previous page
    :disabled="page == 1"
    :disabled="page == totalPages"

<!-- SECTION -->
#### Abstract Code To Components

  - create new component in components file
    moviecard.vue

  - vt to generate template for component

  - <component />

  - move component into v-for to render one for each movie

- set up props in moviecard
  props:{
    movieProp: {type: Movie (imported from model), required: true}
  }

  props set up under export default in script

- home page
  - <MovieCard :movieProp="movie" />

  {{movieProp.title}} in movie card

using props when v-for over a collection 95% of time

collection is computed in parent component
props are on the child element

<!-- SECTION -->
#### Page Nav

  router-link = :to="{name: 'where we want to go'}" - must supply a :to="" or all vue breaks

  create new page -> MovieDetailsPage.vue -> vt
  
  - create new route object in router.js => loadPage('must match the name of your file')
  - movie card -> change name in router link to name in router.js
  - store optional params on url path with :/paramater -> movies/:movieId

  -movie card
    routerlink :to="{name: 'Movie', params: {movieId: movieProp.id},}"
  - movie details page setup
    const route = useRoute
    get movie by id function
    onMounted(()=> {
      getMovieById()})
      alias movieId and pass to service
      string interpolate movie id on the url

  - create place to store active Movie in appstate
    create new movie w/ model and store

  compute to bring in active movie

  ? -> does this have value, yes = drill into it, null = return undefined -- will keep vue from breaking by drilling into undefined, compute will draw that change when appstate loads.
    or
  v-if="movie" on div containing what we are injecting into

  if property is null on page load, need an elvis operator(?) or v-if check to avoid breaking vue

  v-if is better because it checks for all props vs elvis required on each property
  