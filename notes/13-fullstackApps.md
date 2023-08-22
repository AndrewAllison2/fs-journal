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
