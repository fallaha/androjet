Local Library
=================

overview
-----
local library is used to make codes shorter, it is useful for storing frequently used routines because you do not need to write them in every layout . 

## Define Local Library
to defining a local library you should write an statement like element with a `@` before its name.

 
```sass
@locallibraryname {
    button {
        text: "Click Me!"
    }
}
```

### Parameters
local library can have some parameters, when you `include` a local library you should pass some value to it as arguments. The definition of a parameter is done by writing `&paramname` as attribute's value.
```sass
@locallibraryname {
    button {
        text: &txt
    }
}
```

#### Default value of parameter
Each parameter can have a default value. The default value is used as the attribute's value if the parameter is not passed by includer.  The definition of default value is done by writing `*defaultvalue` after parameter's name.
```sass
@locallibraryname {
    button {
        text: &txt * "Clock Me!"
    }
}
```

##### None value as default
We might want to ignore the attribute if the includer does not pass a value for the parameter.


```sass
@locallibraryname {
    text {
        text: "Hello World"
        background: &bg * none
    }
}
```
In this example if includer doesn't pass `bg` attribute, background attribute is ignored.

## Include Local Library
to include a local library you can simply write local library name with `#` at the begining of its name and send argument as an attribute.

```sas
#locallibraryname{
    txt: "Hi Ali"
}
```
in this example, it is interpreted as below:

```sass
locallibraryname {
    button {
        text: "Hi Ali"
    }
}
```

## Nested local Library
you can use local library nestedly also parameter can pass to nested local library.

```sass
@buttonok{
  button{
    text: &text * "OK"
  }
}
@rectangle{
  text{
      text: &text * "here is a button"
  }
  #buttonok{
    text: &btntxt
  }
}
```

also you can use this way:

```sass
@rectangle{
  @buttonok{
    button{
      text: &text * "OK"
    }
  }
  text{
      text: &text * "here is a button"
  }
  #buttonok{
    text: &btntxt
  }
}
```

## Constant in local library
note that [`const`](./../consts)is  passed to included like argument, so if you define a const value and include a local library that have the same name parameter, const will be used as parameter. 

``` sass
@rectangle{
  view{
    w: &width
    h: &height
    background: &insidecolor
  }
}
activity {
  name: "Nino"
  frame{
    @insidecolor: #B51993
    w:mp
    h:mp
    align: c
    #rectangle{
      width:  100dp
      height: 100dp
    }
  }
}
```
in this example `insidecolor` is passed as an argument to `#rectangle`. you can also use const as default value for parameter. the code below shows this. in this situation if `color` is passed by includer it is used as background value but if color do not be passed by includer const `@color: #FFFFFF` is used.

```sass
@rectangle{
  view{
    @color: #FFFFFF
    w: &width
    h: &height
    background: &color
  }
}
activity {
  name: "Nino"
  frame{
    w:mp
    h:mp
    align: c
    #rectangle{
      width:  100dp
      height: 100dp
    }
  }
}
```
