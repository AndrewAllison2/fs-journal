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