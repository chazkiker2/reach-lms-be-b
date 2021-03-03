# Java User Model Final Version / Exceptions Final Application / Security Initial Application

## Introduction

This is a database scheme with Users, Roles, UserRoles, UserEmails, Programs, Courses, Modules, UserTeachers, and UserStudents. This Java Spring REST API application will provide endpoints for clients to read various data sets contained in the application's data. This application will also form the basis of a user authentication application developed elsewhere in the course.

# Reach Learning Management System

You can find the frontend project deployed at: https://b.reachlms.dev/ <br>
You can find the backend project deployed at: https://reach-team-b-be.herokuapp.com/ <br>
You can find the backend project documentation at: https://reach-team-b-be.herokuapp.com/swagger-ui.html

## Contributors
|                                          [Wayne Abbruscato](https://github.com/Callisto1981)                                                            |                                                       [Seth Bradshaw](https://github.com/seth-bradshaw)                                                    |                                                      [Sara Cearc](https://github.com/cearc-sara)                                                       |                                                       [Christopher Girvin](https://github.com/)                                               |                                                      [Matias Iturbide](https://github.com/JDMTias)                                                 |                                                      [Chaz Kiker](https://github.com/chazkiker2/)                                                     |                                         [Brendan Lai-Tong](https://github.com/kai-blt/)                                                             |                                         [Shane Slone](https://github.com/shaneslone)                                                                   |                            
| :-----------------------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------: |:-----------------------------------------------------------------------------------------------------------------------------------------------------: |
| [<img src="https://www.dalesjewelers.com/wp-content/uploads/2018/10/placeholder-silhouette-male.png" width = "200" />](https://github.com/Callisto1981) | [<img src="https://www.dalesjewelers.com/wp-content/uploads/2018/10/placeholder-silhouette-male.png" width = "200" />](https://github.com/seth-bradshaw)   |[<img src="https://www.dalesjewelers.com/wp-content/uploads/2018/10/placeholder-silhouette-female.png" width = "200" />](https://github.com/cearc-sara) | [<img src="https://www.dalesjewelers.com/wp-content/uploads/2018/10/placeholder-silhouette-male.png" width = "200" />](https://github.com/)   | [<img src="https://www.dalesjewelers.com/wp-content/uploads/2018/10/placeholder-silhouette-male.png" width = "200" />](https://github.com/JDMTias) | [<img src="https://www.dalesjewelers.com/wp-content/uploads/2018/10/placeholder-silhouette-male.png" width = "200" />](https://github.com/chazkiker2) | [<img src="https://www.dalesjewelers.com/wp-content/uploads/2018/10/placeholder-silhouette-male.png" width = "200" />](https://github.com/kai-blt/) |  [<img src="https://www.dalesjewelers.com/wp-content/uploads/2018/10/placeholder-silhouette-male.png" width = "200" />](https://github.com/shaneslone) |
|                                [<img src="https://github.com/favicon.ico" width="15"> ](https://github.com/Callisto1981)                                |                            [<img src="https://github.com/favicon.ico" width="15"> ](https://github.com/seth-bradshaw)                                      |                          [<img src="https://github.com/favicon.ico" width="15"> ](https://github.com/cearc-sara)                                       |                          [<img src="https://github.com/favicon.ico" width="15"> ](https://github.com/NandoTheessen)                           |                           [<img src="https://github.com/favicon.ico" width="15"> ](https://github.com/JDMTias)                                     |                           [<img src="https://github.com/favicon.ico" width="15"> ](https://github.com/chazkiker2)                                     |                           [<img src="https://github.com/favicon.ico" width="15"> ](https://github.com/kai-blt/)                                     |                           [<img src="https://github.com/favicon.ico" width="15"> ](https://github.com/shaneslone)                                      |
|     [ <img src="https://static.licdn.com/sc/h/al2o9zrvru7aqj8e1x2rzsrca" width="15"> ](https://www.linkedin.com/in/wayne-abbruscato-orr-767a2b90/)      |                 [ <img src="https://static.licdn.com/sc/h/al2o9zrvru7aqj8e1x2rzsrca" width="15"> ](https://www.linkedin.com/in/seth-bradshaw/)             |                [ <img src="https://static.licdn.com/sc/h/al2o9zrvru7aqj8e1x2rzsrca" width="15"> ](https://www.linkedin.com/in/sara-cearc/)             |      [ <img src="https://static.licdn.com/sc/h/al2o9zrvru7aqj8e1x2rzsrca" width="15"> ](https://www.linkedin.com/in/christopher-girvin/)      |                [ <img src="https://static.licdn.com/sc/h/al2o9zrvru7aqj8e1x2rzsrca" width="15"> ](https://www.linkedin.com/in/matias-iturbide/)    |                [ <img src="https://static.licdn.com/sc/h/al2o9zrvru7aqj8e1x2rzsrca" width="15"> ](https://www.linkedin.com/in/chaz-kiker/)            |                [ <img src="https://static.licdn.com/sc/h/al2o9zrvru7aqj8e1x2rzsrca" width="15"> ](https://www.linkedin.com/in/brendan-lai-tong/)    |                [ <img src="https://static.licdn.com/sc/h/al2o9zrvru7aqj8e1x2rzsrca" width="15"> ](https://www.linkedin.com/in/shane-slone/)            |

<br>
<br>


![MIT](https://img.shields.io/packagist/l/doctrine/orm.svg)

### Database layout

The table layout is similar to the initial version with the following exceptions:

* The join table userroles is explicitly created. This allows us to add additional columns to the join table
* Since we are creating the join table ourselves, the Many to Many relationship that formed the join table is now two Many to One relationships
* All tables now have audit fields

Thus the new table layout is as follows

* User is the driving table.
* Useremails have a Many-To-One relationship with User. Each User has many user email combinations. Each user email combination has only one User.
* Roles have a Many-To-Many relationship with Users.
* Programs have three distinct relationships to User. 
   * One-To-One - Authenticated user is assigned as Admin upon program initialization.
   * Many-To-Many - UserTeachers is a join table between User and Program. (filter users by role teacher)
   * Many-To-Many - UserStudents is a join table between User and Program. (filter users by role student)
<br>
* Program is the driving table.
* Courses have a Many-To-One relationship to Program.
<br>
* Course is the driving table.
* Modules have a Many-To-One relationship to Course.


![Image of Database Layout](reachlmsdbschema.png)

Using the provided seed data, expand each endpoint below to see the output it generates.

<details>
<summary>http://localhost:2019/useremails/useremails</summary>

```JSON
[
    {
        "useremailid": 5,
        "useremail": "admin@email.local",
        "user": {
            "userid": 4,
            "username": "admin",
            "primaryemail": "admin@lambdaschool.local",
            "roles": [
                {
                    "role": {
                        "roleid": 3,
                        "name": "DATA"
                    }
                },
                {
                    "role": {
                        "roleid": 1,
                        "name": "ADMIN"
                    }
                },
                {
                    "role": {
                        "roleid": 2,
                        "name": "USER"
                    }
                }
            ]
        }
    },
    {
        "useremailid": 6,
        "useremail": "admin@mymail.local",
        "user": {
            "userid": 4,
            "username": "admin",
            "primaryemail": "admin@lambdaschool.local",
            "roles": [
                {
                    "role": {
                        "roleid": 3,
                        "name": "DATA"
                    }
                },
                {
                    "role": {
                        "roleid": 1,
                        "name": "ADMIN"
                    }
                },
                {
                    "role": {
                        "roleid": 2,
                        "name": "USER"
                    }
                }
            ]
        }
    },
    {
        "useremailid": 8,
        "useremail": "cinnamon@mymail.local",
        "user": {
            "userid": 7,
            "username": "cinnamon",
            "primaryemail": "cinnamon@lambdaschool.local",
            "roles": [
                {
                    "role": {
                        "roleid": 2,
                        "name": "USER"
                    }
                },
                {
                    "role": {
                        "roleid": 3,
                        "name": "DATA"
                    }
                }
            ]
        }
    },
    {
        "useremailid": 9,
        "useremail": "hops@mymail.local",
        "user": {
            "userid": 7,
            "username": "cinnamon",
            "primaryemail": "cinnamon@lambdaschool.local",
            "roles": [
                {
                    "role": {
                        "roleid": 2,
                        "name": "USER"
                    }
                },
                {
                    "role": {
                        "roleid": 3,
                        "name": "DATA"
                    }
                }
            ]
        }
    },
    {
        "useremailid": 10,
        "useremail": "bunny@email.local",
        "user": {
            "userid": 7,
            "username": "cinnamon",
            "primaryemail": "cinnamon@lambdaschool.local",
            "roles": [
                {
                    "role": {
                        "roleid": 2,
                        "name": "USER"
                    }
                },
                {
                    "role": {
                        "roleid": 3,
                        "name": "DATA"
                    }
                }
            ]
        }
    },
    {
        "useremailid": 12,
        "useremail": "barnbarn@email.local",
        "user": {
            "userid": 11,
            "username": "barnbarn",
            "primaryemail": "barnbarn@lambdaschool.local",
            "roles": [
                {
                    "role": {
                        "roleid": 2,
                        "name": "USER"
                    }
                }
            ]
        }
    }
]
```

</details>

<details>
<summary>http://localhost:2019/useremails/useremail/8</summary>

```JSON
{
    "useremailid": 8,
    "useremail": "cinnamon@mymail.local",
    "user": {
        "userid": 7,
        "username": "cinnamon",
        "primaryemail": "cinnamon@lambdaschool.local",
        "roles": [
            {
                "role": {
                    "roleid": 2,
                    "name": "USER"
                }
            },
            {
                "role": {
                    "roleid": 3,
                    "name": "DATA"
                }
            }
        ]
    }
}
```

</details>

<details>
<summary>DELETE http://localhost:2019/useremails/useremail/8</summary>

```TEXT
No Body Data

Status OK
```

</details>


<details>
<summary>PUT http://localhost:2019/useremails/useremail/9/email/favbun@hops.local</summary>

OUTPUT

```TEXT
Status OK
```

</details>

<details>
<summary>http://localhost:2019/useremails/useremail/9</summary>

```JSON
{
    "useremailid": 9,
    "useremail": "favbun@hops.local",
    "user": {
        "userid": 7,
        "username": "cinnamon",
        "primaryemail": "cinnamon@lambdaschool.local",
        "roles": [
            {
                "role": {
                    "roleid": 2,
                    "name": "USER"
                }
            },
            {
                "role": {
                    "roleid": 3,
                    "name": "DATA"
                }
            }
        ]
    }
}
```

</details>

<details>
<summary>POST http://localhost:2019/useremails/user/14/email/favbun@hops.local</summary>

OUTPUT

```TEXT
Status CREATED

Location Header: http://localhost:2019/useremails/useremail/15
```

</details>

<details>
<summary>http://localhost:2019/useremails/useremail/15</summary>

```JSON
{
    "useremailid": 15,
    "useremail": "favbun@hops.local",
    "user": {
        "userid": 14,
        "username": "misskitty",
        "primaryemail": "misskitty@school.lambda",
        "roles": [
            {
                "role": {
                    "roleid": 2,
                    "name": "USER"
                }
            }
        ]
    }
}
```

</details>

---

<details>
<summary>http://localhost:2019/roles/roles</summary>

```JSON
[
    {
        "roleid": 1,
        "name": "ADMIN",
        "users": [
            {
                "user": {
                    "userid": 4,
                    "username": "admin",
                    "primaryemail": "admin@lambdaschool.local",
                    "useremails": [
                        {
                            "useremailid": 5,
                            "useremail": "admin@email.local"
                        },
                        {
                            "useremailid": 6,
                            "useremail": "admin@mymail.local"
                        }
                    ]
                }
            }
        ]
    },
    {
        "roleid": 2,
        "name": "USER",
        "users": [
            {
                "user": {
                    "userid": 14,
                    "username": "misskitty",
                    "primaryemail": "misskitty@school.lambda",
                    "useremails": [
                        {
                            "useremailid": 15,
                            "useremail": "favbun@hops.local"
                        }
                    ]
                }
            },
            {
                "user": {
                    "userid": 13,
                    "username": "puttat",
                    "primaryemail": "puttat@school.lambda",
                    "useremails": []
                }
            },
            {
                "user": {
                    "userid": 11,
                    "username": "barnbarn",
                    "primaryemail": "barnbarn@lambdaschool.local",
                    "useremails": [
                        {
                            "useremailid": 12,
                            "useremail": "barnbarn@email.local"
                        }
                    ]
                }
            },
            {
                "user": {
                    "userid": 7,
                    "username": "cinnamon",
                    "primaryemail": "cinnamon@lambdaschool.local",
                    "useremails": [
                        {
                            "useremailid": 9,
                            "useremail": "favbun@hops.local"
                        },
                        {
                            "useremailid": 10,
                            "useremail": "bunny@email.local"
                        }
                    ]
                }
            },
            {
                "user": {
                    "userid": 4,
                    "username": "admin",
                    "primaryemail": "admin@lambdaschool.local",
                    "useremails": [
                        {
                            "useremailid": 5,
                            "useremail": "admin@email.local"
                        },
                        {
                            "useremailid": 6,
                            "useremail": "admin@mymail.local"
                        }
                    ]
                }
            }
        ]
    },
    {
        "roleid": 3,
        "name": "DATA",
        "users": [
            {
                "user": {
                    "userid": 4,
                    "username": "admin",
                    "primaryemail": "admin@lambdaschool.local",
                    "useremails": [
                        {
                            "useremailid": 5,
                            "useremail": "admin@email.local"
                        },
                        {
                            "useremailid": 6,
                            "useremail": "admin@mymail.local"
                        }
                    ]
                }
            },
            {
                "user": {
                    "userid": 7,
                    "username": "cinnamon",
                    "primaryemail": "cinnamon@lambdaschool.local",
                    "useremails": [
                        {
                            "useremailid": 9,
                            "useremail": "favbun@hops.local"
                        },
                        {
                            "useremailid": 10,
                            "useremail": "bunny@email.local"
                        }
                    ]
                }
            }
        ]
    }
]
```

</details>

<details>
<summary>http://localhost:2019/roles/role/3</summary>

```JSON
{
    "roleid": 3,
    "name": "DATA",
    "users": [
        {
            "user": {
                "userid": 4,
                "username": "admin",
                "primaryemail": "admin@lambdaschool.local",
                "useremails": [
                    {
                        "useremailid": 5,
                        "useremail": "admin@email.local"
                    },
                    {
                        "useremailid": 6,
                        "useremail": "admin@mymail.local"
                    }
                ]
            }
        },
        {
            "user": {
                "userid": 7,
                "username": "cinnamon",
                "primaryemail": "cinnamon@lambdaschool.local",
                "useremails": [
                    {
                        "useremailid": 9,
                        "useremail": "favbun@hops.local"
                    },
                    {
                        "useremailid": 10,
                        "useremail": "bunny@email.local"
                    }
                ]
            }
        }
    ]
}
```

</details>

<details>
<summary>http://localhost:2019/roles/role/name/data</summary>

```JSON
{
    "roleid": 3,
    "name": "DATA",
    "users": [
        {
            "user": {
                "userid": 4,
                "username": "admin",
                "primaryemail": "admin@lambdaschool.local",
                "useremails": [
                    {
                        "useremailid": 5,
                        "useremail": "admin@email.local"
                    },
                    {
                        "useremailid": 6,
                        "useremail": "admin@mymail.local"
                    }
                ]
            }
        },
        {
            "user": {
                "userid": 7,
                "username": "cinnamon",
                "primaryemail": "cinnamon@lambdaschool.local",
                "useremails": [
                    {
                        "useremailid": 9,
                        "useremail": "favbun@hops.local"
                    },
                    {
                        "useremailid": 10,
                        "useremail": "bunny@email.local"
                    }
                ]
            }
        }
    ]
}
```

</details>

<details>
<summary>POST http://localhost:2019/roles/role</summary>

DATA

```JSON
{
    "name" : "ANewRole"
}
```

OUTPUT

```TEXT
Status CREATED

Location Header: http://localhost:2019/roles/role/16
```

</details>

<details>
<summary>http://localhost:2019/roles/role/name/anewrole</summary>

```JSON
{
    "roleid": 16,
    "name": "ANEWROLE",
    "users": []
}
```

</details>

<details>
<summary>PUT http://localhost:2019/roles/role/16</summary>

DATA

```JSON
{
    "name" : "ANewRole"
}
```

OUTPUT

```TEXT
Status OK
```

</details>

---

<details>
<summary>http://localhost:2019/users/users</summary>

```JSON
[
    {
        "userid": 4,
        "username": "admin",
        "primaryemail": "admin@lambdaschool.local",
        "useremails": [
            {
                "useremailid": 5,
                "useremail": "admin@email.local"
            },
            {
                "useremailid": 6,
                "useremail": "admin@mymail.local"
            }
        ],
        "roles": [
            {
                "role": {
                    "roleid": 3,
                    "name": "DATA"
                }
            },
            {
                "role": {
                    "roleid": 1,
                    "name": "ADMIN"
                }
            },
            {
                "role": {
                    "roleid": 2,
                    "name": "USER"
                }
            }
        ]
    },
    {
        "userid": 7,
        "username": "cinnamon",
        "primaryemail": "cinnamon@lambdaschool.local",
        "useremails": [
            {
                "useremailid": 9,
                "useremail": "favbun@hops.local"
            },
            {
                "useremailid": 10,
                "useremail": "bunny@email.local"
            }
        ],
        "roles": [
            {
                "role": {
                    "roleid": 2,
                    "name": "USER"
                }
            },
            {
                "role": {
                    "roleid": 3,
                    "name": "DATA"
                }
            }
        ]
    },
    {
        "userid": 11,
        "username": "barnbarn",
        "primaryemail": "barnbarn@lambdaschool.local",
        "useremails": [
            {
                "useremailid": 12,
                "useremail": "barnbarn@email.local"
            }
        ],
        "roles": [
            {
                "role": {
                    "roleid": 2,
                    "name": "USER"
                }
            }
        ]
    },
    {
        "userid": 13,
        "username": "puttat",
        "primaryemail": "puttat@school.lambda",
        "useremails": [],
        "roles": [
            {
                "role": {
                    "roleid": 2,
                    "name": "USER"
                }
            }
        ]
    },
    {
        "userid": 14,
        "username": "misskitty",
        "primaryemail": "misskitty@school.lambda",
        "useremails": [
            {
                "useremailid": 15,
                "useremail": "favbun@hops.local"
            }
        ],
        "roles": [
            {
                "role": {
                    "roleid": 2,
                    "name": "USER"
                }
            }
        ]
    }
]
```

</details>

<details>
<summary>http://localhost:2019/users/user/7</summary>

```JSON
{
    "userid": 7,
    "username": "cinnamon",
    "primaryemail": "cinnamon@lambdaschool.local",
    "useremails": [
        {
            "useremailid": 9,
            "useremail": "favbun@hops.local"
        },
        {
            "useremailid": 10,
            "useremail": "bunny@email.local"
        }
    ],
    "roles": [
        {
            "role": {
                "roleid": 2,
                "name": "USER"
            }
        },
        {
            "role": {
                "roleid": 3,
                "name": "DATA"
            }
        }
    ]
}
```

</details>

<details>
<summary>http://localhost:2019/users/user/name/cinnamon</summary>

```JSON
{
    "userid": 7,
    "username": "cinnamon",
    "primaryemail": "cinnamon@lambdaschool.local",
    "useremails": [
        {
            "useremailid": 9,
            "useremail": "favbun@hops.local"
        },
        {
            "useremailid": 10,
            "useremail": "bunny@email.local"
        }
    ],
    "roles": [
        {
            "role": {
                "roleid": 2,
                "name": "USER"
            }
        },
        {
            "role": {
                "roleid": 3,
                "name": "DATA"
            }
        }
    ]
}
```

</details>

<details>
<summary>http://localhost:2019/users/user/name/like/da</summary>

```JSON
[]
```

</details>

<details>
<summary>POST http://localhost:2019/users/user</summary>

DATA

```JSON
{
    "username": "Mojo",
    "primaryemail": "mojo@lambdaschool.local",
    "password" : "Coffee123",
    "useremails": [
        {
            "useremail": "mojo@mymail.local"
        },
        {
            "useremail": "mojo@email.local"
        }
        ],
    "roles": [
        {
            "role": {
                "roleid": 1
            }
        },
        {
            "role": {
                "roleid": 2
            }
        }
    ]
}
```

OUTPUT

```TEXT
No Body Data

Location Header: http://localhost:2019/users/user/17
Status 201 Created
```

</details>

<details>
<summary>http://localhost:2019/users/user/name/mojo</summary>

</details>

<details>
<summary>PUT http://localhost:2019/users/user/14</summary>

DATA

```JSON
{
    "username": "stumps",
    "primaryemail": "stumps@lambdaschool.local",
    "password" : "EarlGray123",
    "useremails": [
        {
            "useremail": "stumps@mymail.local"
        },
        {
            "useremail": "stumps@email.local"
        }
        ],
    "roles": [
        {  
            "role": {
                "roleid": 3
            }
        },
        {  
            "role": {
                "roleid": 1
            }
        }
    ]
}
```

OUTPUT

```TEXT
No Body Data

Status OK
```

</details>

<details>
<summary>http://localhost:2019/users/user/name/stumps</summary>

```JSON
{
    "userid": 16,
    "username": "stumps",
    "primaryemail": "stumps@lambdaschool.local",
    "useremails": [
        {
            "useremailid": 19,
            "useremail": "stumps@mymail.local"
        },
        {
            "useremailid": 20,
            "useremail": "stumps@email.local"
        }
    ],
    "roles": [
        {
            "role": {
                "roleid": 1,
                "name": "ADMIN"
            }
        },
        {
            "role": {
                "roleid": 3,
                "name": "DATA"
            }
        }
    ]
}
```

</details>

<details>
<summary>PATCH http://localhost:2019/users/user/7</summary>

DATA

```JSON
{
    "username": "cinabun",
    "primaryemail": "cinabun@lambdaschool.home",
    "useremails": [
    {
            "useremail": "cinnamon@mymail.home"
    },
    {
            "useremail": "hops@mymail.home"
    },
    {
            "useremail": "bunny@email.home"
    }
    ]
}
```

OUTPUT

```TEXT
No Body Data

Status OK
```

</details>

<details>
<summary>http://localhost:2019/users/user/name/cinabun</summary>

```JSON
{
    "userid": 7,
    "username": "cinabun",
    "primaryemail": "cinabun@lambdaschool.home",
    "useremails": [
        {
            "useremailid": 21,
            "useremail": "cinnamon@mymail.home"
        },
        {
            "useremailid": 22,
            "useremail": "hops@mymail.home"
        },
        {
            "useremailid": 23,
            "useremail": "bunny@email.home"
        }
    ],
    "roles": [
        {
            "role": {
                "roleid": 2,
                "name": "USER"
            }
        },
        {
            "role": {
                "roleid": 3,
                "name": "DATA"
            }
        }
    ]
}
```

</details>

<details>

<summary>DELETE http://localhost:2019/users/user/14</summary>

```TEXT
No Body Data

Status OK
```

</details>
