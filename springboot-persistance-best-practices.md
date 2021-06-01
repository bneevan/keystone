## 1. Associations
### @OneToMany

```java

class User {
  @OneToMany(cascade = CascadeType.ALL, mappedBy = "creator", orphanRemoval = true)
  List<Assignment> assignments;
  
  public void addAssignment(Assignment assignment) {
    this.assignments.add(assignment);
    assignment.setCreator(this);
  }
  
  public void removeAssignment(Assignment assignment) {
    assignment.setCreator(null);
    this.assignments.remove(assignment);    
  }
}



class Assignment {
  @ManyToOne
  User creator;
}

```
