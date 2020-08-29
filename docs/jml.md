## overview
JML (Jet Markup Language) is introduced by AndroJet for developing android UI easily. JML support [constant values](), [local library]() and [default elements]() as well. AndroJet converts JML to native android XML.

## Element
elements usually are interpreted as android components, for example `text` is interpreted as `TextView`. to see a complete list of elements visit [default value](./../naming/#elements-name) page.


!!! note
    AndroJet doesn't modify any name that does not exist in the list of elements. so `aa.bb.cc` is interpreted as `aa.bb.cc`. you can also use the orginal name of each component that is used in android xml.

## Attribute
attributes specify property of [elements](./#element) such as `height` or `width` or any specefic property of elements like `text` in `TextView`. AndroJet defines such names for attribute to code faster. for example you can use `h` instead of `layout_height` that is used in android xml. You can see the complete list of these attribute names in [this](./../naming/#general-attribute) page.


!!! note
    **1 :** AndroJet doesn't change any attribute that does not exist in the above list. so `abcd` is interpretd as `abcd`.

    **2 :** to use a specefic namespace (such as `tools`) that must be written in `namsapce.attribute` form, for example to use `tools:actionBarNavMode` you should write `tools.actionBarNavMode`.

each element have its own specific attributes, `textSize` in `TextView` for example. AndroJet defines some attributes for specific elements. in this situation you can use `size` instead of `textSize` for `TextView`. to see the compelete list of attributes of a specific element [click here](./../naming/#attribute-of-specific-element).



### Complex Attribute
some attributes have some properties for example [`shadow`](./../shadow) has `opacity`, `x`, `y` and `radius`. You can quantif‍y Complex Attribute in two ways: Element Style and Dash Style.

 The code below shows an example for `shadow`.
#### Element Style
``` sass
view{
  background: #a0a0a0
  shadow{
    x: 3dp
    y: 3dp
    radius: 5dp
    opacity: 50
  }
}
```

#### Dash Style
by Dash Style you can use this form: `parentattr-attribute`.

```sass
view{
  background: #a0a0a0
  shadow-x: 3dp
  shadow-y: 3dp
  shadow-radius: 5dp
  shadow-opacity: 50
}
```

### Value of attribute
for assignment vaule to an attribute you should use `:`. AndoJet defines some attributes value for fast coding. for example `mp` means `match_parent`. to see the complete list of values of specific attributes [click here](./../naming/#value-of-specific-attribute)



#### none as Value
assigning `none` to an attribute, makes that attribute to be ignored. so it wont be interpreted and shown in XML. none is useful for local library and parameters. 

!!! note
    If a default value is defined for an attribute (whether AndroJet defines it or you do) then `none` value makes the default value to be assigned to that attribute. for example if you write `h:none` in a `view` element, AndroJet uses default value and converts it to `h: wc`.

for complex attributes:

- in element form you should use [`sense` ](./#sense)

    ``` sass
    shadow{
        sense: false
        opacity: 50
    }
    ```

- in dash-style form you should quantif‍y general attribute as none

    ``` sass
    shadow: none
    shadow-opacity: 50
    ```


## Constant
constants are defined with a `@` at the begining of their name and are used an `&` folowed by their name (like parameter in local library):

```sass hl_lines="4 8"
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

constantes support Scope as well. value of variable in closest scope is used in case of existance of several const variables with same name:
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

## Define Default Attribute

in every JML file you can define default attributes for each element. for example you can define default `TextView` element to set `fontFamily` for all `TextView`s.

``` sass
default{
    text{
        font: 'sansarif.ttf'
    }
    button{
        padding: 20dp
    }
}
```

!!! note ""
    `default` statement should be defined before `activity` statement.

 AndroJet also deifnes Some default attributes for Some elements. ‍to see the complete list [click here](./../defaults/#default-attribute-of-elements)



## Special Attribtues

There is some Attribtues that are interpreted diffrently in comparison to normal attributes. (it is use for tell to AndroJet do something.)

### Sense

`sense` is used that elements or complex attributes be ignored by AndroJet. 

``` sass hl_lines="5"
activity {
  name: "Nino"
  frame{
    text{
      sense: false
      text: "This Text will Not be Shown! :("
    }
  }
}
```
