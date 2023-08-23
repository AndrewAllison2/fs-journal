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

  - Only see shut down rest if i am creator

<!-- NOTE REFERENCE HELP_REVIEWS -> GETBYID -->

 - can pull out user info without authorizing the method

> string userId = null -> is it has value it will keep that, if not will assign to null

OBJECT REF NOT SET TO INSTANCE OF OBJ ERROR -> trying to drill into null (ex: userInfo.id) -> use elvis operator

