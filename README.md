## Task Management Application 🪒

`nest new nestjs-task-management` -> to setup the project 

`tsconfig.build.json` -> used in production development when you want to exclude some files 
`tsconfig.json` -> tells the TypeScript compiler how to compile the project . This file is present in every typescript project. 

`yarn start:dev` -> run the server in the development mode 

### Nestjs Modules ▶️
<p> 
Each application has atleast one module called as root module .This is the starting point of the application.<br>
Modules are an effective way to organise components by closely related capabilities.<br>
Modules are singleton therefore they can be imported by other modules as well.<br>
Moduels are defined by annotating a class with the `@Module` decorator . Decorator provides the metadata that nestjs uses to organize the structure.<br>
 </p>

### `@Module decorator properties` ▶️
`providers` : Array of providers to be available within the module via dependency injection.<br>
`controllers` : Array of controllers to be instantiated within the module.<br>
`Exports` : Array of providers to export to other modules. Other modules will also have excess what this module exports. <br>
`Imports`: List of modules required by this module .<br>

`nest g module task` --> this command is used to create modules . It will create a new subfolder task inside which tasks module will be present and root module i.e AppModule that will be updated . 

### `Nestjs controllers` ▶️
Responsible for handling incoming requests and returning responses to the clients.<br>
Bound to the specific path . ( ex : task/ -> to get task resource).<br>
Contains handlers which handle the endpoints and request methods (GET , POST , DELETE , etc);<br>

### `How to define controllers ?`
`@Controller` -> controllers are defined by decorating a class with @Controller decorator. The decorator accepts a string , which is the `path` to be handles by the controller.<br>
`@Controller('/task')
export class TasksController {...}`

### `How to define Handlers ?`
Handlers are simply the http methods . Defined using decorators ex: `@Get, @Post , @Delete` etc.<br>
Example : 
`@Controller('/task')
export class TasksController {
    @Get()
    getAllTasks(){...},
    @Post()
    createTask(){...}
}`
These have same endpoints but different methods . 

 Data flow ➡️
`HTTP REQUEST 
    ⬇️
Request Routed To CONTROLLER (handler is called with arguments) 
    ⬇️
Parsing the request data . It will be available inside handler. 
    ⬇️ 
Performs the operation such as buisness logic and communication with services. 
    ⬇️
Handler returns the return value.` 


#### APP MODULE(ROOT)

#### TASKS MODULE -> TasksController, TasksService , TaskRepository, TaskEntity, StatusValidationPipe

#### AUTH MODULE -> AuthController ,AuthService , UserRepository , UserEntity , JWTStrategy

#### REST API ENDPOINTS ->

`GET : tasks/` -> get all the tasks (including the filters)

`GET : tasks/:id/` -> get a task 

`POST tasks/` -> create a task 

`DELETE task/:id/` -> delete a task 

`PATCH task/:id/status/`-> update task status 

#### AUTH ENDPOINTS -> 

`POST auth/signup/` -> Sign up 
`POST auth/signin/` -> Sign In


