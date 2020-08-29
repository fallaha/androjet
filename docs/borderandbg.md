
overview
-----

AndroJet has tried to make background like css style. border and background are closely related. `border` is a [`complex attribute`](./../jml/#complex-attribute) that has `radius`, `color` and `width` attributes. in android (and consequently in AndroJet) every element can have a `background` attribute.

=== "Simple Background"

    <img src="/image/bg/simple-bg.png" alt="sample" title="sample" width="270" align="left" />

    ``` sass hl_lines="6 9"
    activity {
        name: "Nino"
        frame {
            h: mp
            w: mp
            background: #E1E7F1F6
            text {
            padding:20dp
            text: "Test Background"
            background: #00dae6
            align: c
            }
        }
    }
    ```

=== "Rounded Background"
    <img src="/image/bg/rounded-bg.png" alt="sample" title="sample" width="270" align="left" />

    ``` sass hl_lines="6 10 11"
    activity {
        name: "Nino"
        frame {
            h: mp
            w: mp
            background: #E1E7F1F6
            text{
            padding: 30dp
            text: "Test Background"
            background: #00dae6
            border-radius: 50dp
            align: c
            }
        }
    }
    ```
    for make background round, must be used `border-radius`.


=== "Border"
    <img src="/image/bg/border-rounded-bg.png" alt="sample" title="sample" width="270" align="left" />

   


    ``` sass hl_lines="11 12 13"
    activity {
        name: "Nino"
        frame {
            h: mp; w: mp
            background: #E1E7F1F6
            text {
            padding: 40dp
            text: "Test Background"
            background: #00dae6
            border-radius: 50dp
            border-color: #7AE9FF
            border-width: 10dp
            align: c
            }
        }
    }
    ```

     `border` attribute has 3 property: `radius`, `color` and `width`.

