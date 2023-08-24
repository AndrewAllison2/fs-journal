# FULL STACK APPLICATIONS

## MONDAY

  - env setup in server and client
  - create table
  - create model, setup files

<!-- NOTE LinearGradient reference on Home page of InstaCult might fix inheritance on DnD Homepage -->


 - Only Join Cult Once
dbsetup - unique (cultId, accountId)

### REPO ITEM

- Repo Class
  - public abstract class RepoItem<T>
  {
    public T id {get; set;}
    public DateTime CreatedAt {get; set}
  }

  - cultmember model
  public class CultMember : RepoItem<int>

  > get cult to compare leaderId to userId


<!-- NOTE REFERENCE CULTIST FOR SHOWING ALL MEMBERS OF A CULT -->


<!-- NOTE cultMembersRepo getCult SQL REFERENCE FOR MEMBER COUNT AND LEFTJOIN-->

- LEFTJOIN used to join tables even if there is no data => join returned only cults that had members
- GROUP BY 

const cultData = {cultId: cultId} or {cultId}

# WEDNESDAY

<!-- SECTION -->
  - Only see shut down rest with getbyid if i am creator of rest

<!-- NOTE REFERENCE HELP_REVIEWS -> GETBYID -->

 - can pull out user info without authorizing the method -> controller

> string userId = null -> if it has value passed from controller it will keep that, if not will assign to null

<!-- REVIEW -->
 - OBJECT REF NOT SET TO INSTANCE OF OBJ ERROR -> trying to drill into null (ex: userInfo.id) -> use elvis operator

- this broke edit ^ because we call get by ID without passing it a user id(null => getbyId will fail test)

refactor service -> pass userId to any call to getById

- GET ALL ONLY RETURNS REST NOT SHUT DOWN
  - get userInfo from controller

  - SERVICE
    - List<T>FindAll

    restaurants = restaurants.FindAll(r => r.IsShutDown == false || r.CreatorId == userId) -> find us all restaurants that are not shut down OR that i'm a creator of

### EDIT ACCOUNT 
  reference help review account controller

## FRONT END

  home page router -> beforeEnter:authSettled -> wait for bearer token, attach to request and send -> get my restaurants wether opened or closed

  - ROUTER PUSH CONDITIONAL

    Push to home page on badrequest
      - router.push()  => in catch of function

## BACKEND AGAIN
  
  PAGE VISITS
    - service - utility function

  - SORT RESTAURANTS
     - sql -> order by => review docs/sqlBolt/mySqlTutorial

  - Query
    - GetRestaurants([FromQuery] string name) ==> controller -> get can take in query, service -> call diferent methods in repo based on query check in service

    name = $"%{name}%"




