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


