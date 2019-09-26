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
      "title": "Buy cat food",
      "created": "2019-09-26T18:08:29.770Z"
    },
    {
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
      "created": "2019-09-26T18:08:29.770Z"
    },
    {
      "title": "Avoid cat quantum superposition",
      "created": "2019-09-26T18:24:57.298Z"
    },
    {
      "title": "Feed the 🦁",
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
      "title": "Get more cardboard boxes",
      "created": "2019-09-26T18:48:53.570Z"
    },
    {
      "title": "Avoid cat quantum superposition",
      "created": "2019-09-26T18:24:57.298Z"
    },
    {
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
    "index": 1
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
      "created": "2019-09-26T18:08:29.770Z"
    },
    {
      "title": "Feed the 🦁",
      "created": "2019-09-26T18:33:17.434Z"
    }
  ]
}
```