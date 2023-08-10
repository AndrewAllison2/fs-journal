#### Sockets

- env.js => sockets = true

 - handler in client and server will handle sockets


### Backend Socket Handler
export class LightHandler extends SocketHandler{
  constructor(io, socket){
    super(io, socket)

    this.on('Get light status', this.getLightStatus)
  }

  getLightStatus(){
    this.socket.emit('Light status', isOn)
  }
}


- create new handler and have it extend the socketHandler
- constructor takes in io, socket, optional useAuth


##### IO - is the entire server
##### Socket - sends to user who made request


### Frontend Socket Handler

- create light handler in handlers on client side

class Lighthandler extends Sockethandler(){
  constructor(){
    super()

    this.on('Light Status', this.setLightStatus)
  }

  setLightStatus(isOn){
    Appstate.isOn = isOn
  }
}

export const lightHandler = new LightHandler()


onMounted(()=>{
  lightHandler.emit('Get light status')
})

use "magic strings" to trigger effects between server and client

toggleLightBulb(){
  lightHandler.emit('Toggle_Light_Bulb') <= this is a magic string, network/sockets/messages will show it fire the message
}


###### server side
toggleLightBulb(){
  isOn != isOn
  this.io.emit('Light_Status', isOn)
}

emits and listens messages between client and server, 


if requiring auth in server side, pass true through super on client handler


this.io.to('CARS_PAGE') <= send data to specific page
this.io.to('Notifications').emit('light_status', message: 'You hav a notification')


socket.io
serverside events -> push notifications


<!-- SECTION -->
### Socket Lecture Pt. 2

regionHandler.EnterRegion

enter region onMounted
leave region onBeforeRouteLeave

add or skip -> finds message by id, pushes it if no found message


<!-- SECTION -->
### VUE TOUR

Getting Started
 - npm-i vue3-tour in the client folder
 - import vue3-Tour in entrypoint of app (main.js)
 - import vue3-Tour style sheet
 - root -> .use(vue3-Tour) 

 <!-- NOTE .use must be above the mount -->


  - use class/id to target elements in the dom
  - insert vue-tour tag
  - under export -> name ='my-tour'
  - under return -> array of steps: [
      target: '#v-step-0',
      header: {
        title: 'Welcome to the tour'
      },
      content: `discover <strong>Vue Tour</strong>!`
  ]

  - after setup -> mounted: function(){
    this.$tours['myTour'].start()
  }


use a component to use tour across multiple pages

tour component
<v-tour name="myTour" :steps="steps" :callbacks="tourCallbacks"></v-tour> -> put tag in component
move mounted fuction
pass steps prop to component and call component on home page

- create next steps on new page -> does not matter if numerial across app -> read by numbers per page

target elements with class selectors

array of steps: [
      target: '#v-step-0',
      header: {
        title: 'Welcome to the tour'
      },
      content: `discover <strong>Vue Tour</strong>!`,
      params: {
        placement: 'top',

      }
  ]

  tourCallbacks -> calls function to router.push to new page

  tourCallbacks: {
    onFinish(()=> {
      router.push(normal router push format here)
    })
  }


Only See Tour Once
account model in server

add needsTour property
write put request on account controller to edit account -> updateAccount built into template service
added needsTour to sanitize body function -> allows needs tour to be an editable account property

onSkip(()=> {accountService.editAccount({needsTour: false})})

v-if ="account.needsTour" -> put on every place component is imported

