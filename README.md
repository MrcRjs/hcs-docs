HCS Full Stack Challenge
===

## App challenge description

Application consisting of a task manager, to create, read, update, and delete tasks.

#### REST API Layer

  - An API with endpoints to perform every action for tasks.
  - API users must be authenticated to perform actions.

#### Front-end Layer

  - Web app using a framework of choice, Vue, React or Angular.
  - Perform user authentication, form validation and error display.
  - Main page app to manage tasks for authenticated user.

## Software Constraints

- Node.js
- Express.js
- MongoDB
- Front-end framework -> React

*Pre-built frameworks that
accommodate all features out-of-the-box will not be accepted.*

## DB Schema

UserSchema
```json
{   
  "user":
  {
    "name": String,
    "email": String,
    "password": String  
  },
  tasks:
  [
    {
      "title": String,
      "created": Date
    }
  ]
}
```



## API Endpoints

#### Get all user tasks

**`GET /tasks`**

##### Response

```
Status: 200 OK
```
```json
{
  "user":
  {
    "name": "Alice",
    "email": "Alice@nexus6.com"    
  },
  "tasks": 
  [
    {
      "_id": "5d8dc2f6413c802eacd089b4",
      "title": "Buy cat food",
      "created": "2019-09-26T18:08:29.770Z"
    },
    {
      "_id": "5d8dc2f6413c802eacd089b4",
      "title": "Avoid cat quantum superposition",
      "created": "2019-09-26T18:24:57.298Z"
    }
  ]
}

```


#### Create a new task

**`POST /tasks`**

##### Parameters

| Name        | Type        | Description  |
| ------------|-------------| ------------ |
| `title`     | `String` | **Required.** The task title. |

##### Example

```json
  {
    "title": "Feed the 🦁"
  }
```

##### Response

```
Status: 201 Created
```
```json
{
  "user":
  {
    "name": "Alice",
    "email": "Alice@nexus6.com"    
  },
  "tasks":
  [
    {
      "title": "Buy cat food",
      "_id": "5d8dc0b5413c802eacd089b0",
      "created": "2019-09-26T18:08:29.770Z"
    },
    {
      "title": "Avoid cat quantum superposition",
      "_id": "5d8dc0bb413c802eacd089b1",
      "created": "2019-09-26T18:24:57.298Z"
    },
    {
      "title": "Feed the 🦁",
      "_id": "5d8dc276413c802eacd089b2",
      "created": "2019-09-26T18:33:17.434Z"
    }
  ]
}
```

#### Edit a task

Edit a specified task using index.
This endpoint returns a 404 Not Found status if the task does not exist. 

**`PATCH /tasks`**

##### Parameters

| Name        | Type        | Description  |
| ------------|-------------| ------------ |
| `title`     | `string` | **Required.** The task title. |
| `index`     | `integer` | **Required.** The task index to update. |

##### Example

```json
  {
    "title": "Get more cardboard boxes🦁",
    "index": 0
  }
```

##### Response

```
Status: 200 OK
```
```json
{
  "user":
  {
    "name": "Alice",
    "email": "Alice@nexus6.com"    
  },
  "tasks":
  [
    {
      "_id": "5d8dc2e2413c802eacd089b3",
      "title": "Get more cardboard boxes",
      "created": "2019-09-26T18:48:53.570Z"
    },
    {
      "_id": "5d8dc2f6413c802eacd089b4",
      "title": "Avoid cat quantum superposition",
      "created": "2019-09-26T18:24:57.298Z"
    },
    {
      "_id": "5d8dc329413c802eacd089b5",
      "title": "Feed the 🦁",
      "created": "2019-09-26T18:33:17.434Z"
    }
  ]
}
```

#### Remove a task

Removes a specified task from tasklist.
This endpoint returns a 404 Not Found status if the task does not exist.

**`DELETE /tasks`**

##### Parameters

| Name        | Type        | Description  |
| ------------|-------------| ------------ |
| `index`     | `integer` | **Required.** The task index to update. |

##### Example

```json
  {
    "index": "5d8dc2f6413c802eacd089b3"
  }
```

##### Response

```
Status: 200 OK
```
```json
{
  "user":
  {
    "name": "Alice",
    "email": "Alice@nexus6.com"    
  },
  "tasks":
  [
    {
      "title": "Buy cat food",
      "_id": "5d8dc2f6413c802eacd089b4",
      "created": "2019-09-26T18:08:29.770Z"
    },
    {
      "title": "Feed the 🦁",
      "_id": "5d8dc2f6413c802eacd089b5",
      "created": "2019-09-26T18:33:17.434Z"
    }
  ]
}
```

#### Create a new user

**`POST /users`**

##### Parameters

| Name        | Type        | Description  |
| ------------|-------------| ------------ |
| `name`     | `String` | **Required.** User name. |
| `email`     | `String` | **Required.** User email. |
| `password`     | `String` | **Required.** User password. |

##### Example

```json
  {
    "name": "Fulanito🦁",
    "email": "fulanito@nexus6.com",
    "password": "mypass" 
  }
```

##### Response

```
Status: 201 Created
```
```json
{
  "user":
  {
    "name": "Alice",
    "email": "Alice@nexus6.com"    
  },
  "tasks":
  []
}
```

#### Login

**`POST /login`**

##### Parameters

| Name        | Type        | Description  |
| ------------|-------------| ------------ |
| `email`     | `String` | **Required.** User email. |
| `password`     | `String` | **Required.** User password. |

##### Example

```json
  {
    "email": "fulanito@nexus6.com",
    "password": "mypass" 
  }
```

##### Response

```
Status: 200 OK
```
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7ImVtYWlsIjoiYm9iQG5leHVzNi5jb20ifSwiaWF0IjoxNTY5NTcyMTU0LCJleHAiOjE1Njk2NTg1NTR9.WFTOR51Drqqjmj60-UTjkGJPVBmM1_58XCceQRRooko",
    "status": 200
}
```