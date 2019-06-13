# .graph

:smile: Let's welcome new serialisation format. The only role of the format is to hold the structure without data and types.

If you think graph, there are no arrays there there are only nodes and connections. 

Deserialisation is up to you also

## Why?

World is moving towards graph sourced systems.

## Example

So assume we have a file `DatabaseStructure.graph` with the following contnent:

Structure

```
Person {
    animals
    friends
    gender
    age
}
```

That's `34` bytes

### Deserialization

So this graph code could be deserialized as using pseudocode

```
code = Graph.parse("JackSparrow.graph")
```

```json
{
    "Person":{
        "animals":{},
        "friends":{},
        "gender":{},
        "age":{}
    }
}
```
To define the same structure in json it takes `59` bytes.  Of course you can deserialise it in other way this is just an example.

As we can see the size of that .graph file differs from .json file and its only 67% of size

### Real world usage - Tests

```
Webpage{
    Pages{
        Home{
            menuButton
            heading1
            heading2
            testimonials{
                Jerry
                John
                Patricia
            }
        }
        About{
            menuButton
            Team{
                Jennifer
                Eve
                Tom
                Robert
            }
        }
        Contact{
            menuButton
            form{
                email
                message
                send
            }
        }
    }
}
```

Now using some testing framework I can bind exact string values to my elements and click them without writting this creepy structure:
```json
{
    "Webpage":{
        "Pages":{
            "Home":{
                "menuButton": "menuButton",
                "heading1": "heading1",
                "heading2": "heading2",
                "testimonials": {
                    "Jerry": "Jerry",
                    "John": "John",
                    "Patricia": "Patricia"
                }
            },
            "About":{
                "menuButton": "menuButton",
                "Team":{
                    "Jennifer": "Jennifer",
                    "Eve": "Eve",
                    "Tom": "Tom",
                    "Robert":"Robert"
                }
            },
            "Contact":{
                "menuButton": "menuButton",
                "form":{
                    "email": "email",
                    "message": "message",
                    "send": "send"
                }
            }
        }
    }
}
```


### Real world usage UX planning

```
MainScreen{
    openTutorial{
        skipLesson
        checkLesson
    }
    openProjects{
        createProject{
            typeName
            submit
        }
        loadProject
        deleteProject
    }
    openHelp{
        search
        sendFeedback
    }
    openConsole{
        submitCommand
    }
}
```

### Real world usage UI planning 


```
LoginScreen{
    googleLogin
    githubLogin
    usernameInput
    passwordInput
    submit
}
TodosScreen{
    todoList{
        name
        done
    }
    newTodo{
        nameInput
        submit
    }
}
```