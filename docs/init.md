
- Open File Explorer and navigate to the folder/location you want to create project in. In the address bar, type `cmd` and hit ++enter++.

- to make project with name `MyFirstProject` and with ApplicationId `com.example.app` type following command in cmd:
    ``` bash
    androjet make:app MyFirstProject com.example.app
    ```
- now go to project directory that you created.
    ``` bash
    cd MyFirstProject
    ```

- to make activity with name `Main`, type:
    ``` bash
    androjet make:activity Main
    ```

- now you can build the project to create xml and kotlin file.
    ``` bash
    androjet build:all
    ```


here is all command.

=== "make"
    |SubCommand   | description
    |----------------|--------------
    |app             |  create scaffold of a project. `make:app` give 2 argument first for `project Name` and second for `Application ID`.
    |activity        |  create an actitivy with Pre-written JML code in `JetSource` folder.
    |fragment        |  create an fragment with Pre-written JML code in `JetSource` folder.
    |kotlin          |  creat `Kotlin` directory in project folder. it's used to change default Kotlin Code for activity, fragment and list.

=== "build"
    |SubCommand      | description
    |----------------|--------------
    |all             |  build project and make Kotlin file, xml file and change Manifest.

=== "set"
    |SubCommand      | description
    |----------------|--------------
    |hot             |  make an activity as First Activity that run in Application. this method change Manifest.xml file.
    |key             |  register AndroJet with key.
