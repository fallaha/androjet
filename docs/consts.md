Constant
-----


const variables are denoted by a `@` followed by the variable’s name and can be used by adding an `&` before their name:

```sass
activity {
  name: "Nino"
  frame{
    @insidecolor: #B51993 // Define Constant
    w:120dp
    h:120dp
    align: c
    background: &insidecolor // use constant
  }
}
```
## Scope

const support Scope as well. if several const variables with same name are defined, by calling the name, value of variable in closest scope will be used:
```sass
@mytext: "Section 1"
activity {
  name: "Nino"
  frame{
    @mytext: "Section 2"
    text{
        @mytext: "Section 3" 
        text:&mytext // "Section 3" 
    }
  }
}
```