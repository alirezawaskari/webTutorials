---
description: From Zero to Expert
---

# NestJS Pro Course

### Introduction

This course is for beginners with HTML, CSS, basic JavaScript (variables, functions, arrays), some React and Vue knowledge, and familiarity with TypeScript (from the previous course). You’ll learn **NestJS**, a Node.js framework for building scalable, server-side applications with TypeScript. NestJS uses a modular, Angular-inspired architecture, making it ideal for APIs and backend services that pair with Vue/Nuxt frontends. By the end, you’ll master NestJS’s core and advanced features, integrate it with a database, and build a project to solidify your skills. This is a hands-on, no-BS guide to make you a NestJS pro.

**What You’ll Learn**:

1. NestJS basics (modules, controllers, services).
2. Advanced features (dependency injection, middleware, pipes).
3. Database integration with TypeORM.
4. Building REST APIs and integrating with Vue.
5. Project: A task management API with NestJS.

**Tools Needed**:

* **Node.js**: [Download LTS](https://nodejs.org) (installs `npm`).
* **VS Code**: [Free download](https://code.visualstudio.com/) with [NestJS CLI extension](https://marketplace.visualstudio.com/items?itemName=ivanzusko.nestjs).
* A browser (Chrome recommended) and [Postman](https://www.postman.com/downloads/) for API testing.
* **Database**: SQLite (included with TypeORM) or PostgreSQL.

**How to Use This Document**:

* Save as `NestJS_Pro_Course.md` or convert to PDF (e.g., VS Code with “Markdown PDF” extension).
* Follow each section, code the examples, and do the exercises.
* Set up a project (Part 5) to code along.
* Build the project in Part 6 to apply your skills.
* Refer to resources for extra learning.

**Time Commitment**: \~15-20 hours (spread over days/weeks).

***

### Part 1: NestJS Basics

#### 1.1 What is NestJS?

NestJS is a **Node.js framework** for building scalable server-side applications. It uses TypeScript, Express under the hood, and a modular structure with controllers, services, and modules.

* **Why NestJS?**
  * TypeScript by default for type safety.
  * Modular architecture for clean code.
  * Great for REST APIs, GraphQL, and microservices.
  * Pairs well with Vue/Nuxt frontends.
  * Used by companies like Adidas and Autodesk.
* **Example**: A REST API for managing tasks, integrated with a Vue frontend.

#### 1.2 Setting Up NestJS

Install the NestJS CLI and create a project.

**Steps**:

```bash
npm i -g @nestjs/cli
nest new nest-api
cd nest-api
npm run start:dev
```

* Opens `http://localhost:3000`.
*   Creates:

    ```
    nest-api/
    ├── src/
    │   ├── app.controller.ts
    │   ├── app.module.ts
    │   ├── main.ts
    ├── test/
    ├── package.json
    ```

**Example (src/app.controller.ts)**:

```typescript
import { Controller, Get } from '@nestjs/common';

@Controller()
export class AppController {
  @Get()
  getHello(): string {
    return 'Yo, NestJS!';
  }
}
```

* Access at `http://localhost:3000` to see “Yo, NestJS!”.

**Exercise**:

1. Create a new NestJS project.
2. Add a `/welcome` endpoint that returns “Welcome to Nest!”.

**Answer**:

```typescript
// src/app.controller.ts
import { Controller, Get } from '@nestjs/common';

@Controller()
export class AppController {
  @Get()
  getHello(): string {
    return 'Yo, NestJS!';
  }

  @Get('welcome')
  getWelcome(): string {
    return 'Welcome to Nest!';
  }
}
```

* Test with Postman or browser at `http://localhost:3000/welcome`.

***

### Part 2: Modules, Controllers, and Services

#### 2.1 Modules

Modules organize code into feature-based units.

**Example**:

```bash
nest g module users
nest g controller users
nest g service users
```

```typescript
// src/users/users.module.ts
import { Module } from '@nestjs/common';
import { UsersController } from './users.controller';
import { UsersService } from './users.service';

@Module({
  controllers: [UsersController],
  providers: [UsersService],
})
export class UsersModule {}
```

```typescript
// src/users/users.service.ts
import { Injectable } from '@nestjs/common';

@Injectable()
export class UsersService {
  private users = [{ id: 1, name: 'Dude' }];

  findAll() {
    return this.users;
  }
}
```

```typescript
// src/users/users.controller.ts
import { Controller, Get } from '@nestjs/common';
import { UsersService } from './users.service';

@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Get()
  findAll() {
    return this.usersService.findAll();
  }
}
```

* Access at `http://localhost:3000/users` to see `[{ id: 1, name: 'Dude' }]`.

**Exercise**:

1. Create a `products` module, controller, and service with a `/products` endpoint.

**Answer**:

```typescript
// src/products/products.module.ts
import { Module } from '@nestjs/common';
import { ProductsController } from './products.controller';
import { ProductsService } from './products.service';

@Module({
  controllers: [ProductsController],
  providers: [ProductsService],
})
export class ProductsModule {}
```

```typescript
// src/products/products.service.ts
import { Injectable } from '@nestjs/common';

@Injectable()
export class ProductsService {
  private products = [{ id: 1, name: 'Laptop', price: 999 }];

  findAll() {
    return this.products;
  }
}
```

```typescript
// src/products/products.controller.ts
import { Controller, Get } from '@nestjs/common';
import { ProductsService } from './products.service';

@Controller('products')
export class ProductsController {
  constructor(private readonly productsService: ProductsService) {}

  @Get()
  findAll() {
    return this.productsService.findAll();
  }
}
```

***

### Part 3: Database Integration with TypeORM

Use TypeORM for database operations with SQLite.

**Setup**:

```bash
npm install @nestjs/typeorm typeorm sqlite3
```

```typescript
// src/app.module.ts
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';
import { AppController } from './app.controller';
import { UsersModule } from './users/users.module';

@Module({
  imports: [
    TypeOrmModule.forRoot({
      type: 'sqlite',
      database: 'db.sqlite',
      entities: [__dirname + '/**/*.entity{.ts,.js}'],
      synchronize: true,
    }),
    UsersModule,
  ],
  controllers: [AppController],
})
export class AppModule {}
```

```typescript
// src/users/user.entity.ts
import { Entity, Column, PrimaryGeneratedColumn } from 'typeorm';

@Entity()
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  name: string;
}
```

```typescript
// src/users/users.module.ts
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';
import { UsersController } from './users.controller';
import { UsersService } from './users.service';
import { User } from './user.entity';

@Module({
  imports: [TypeOrmModule.forFeature([User])],
  controllers: [UsersController],
  providers: [UsersService],
})
export class UsersModule {}
```

```typescript
// src/users/users.service.ts
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { User } from './user.entity';

@Injectable()
export class UsersService {
  constructor(
    @InjectRepository(User)
    private usersRepository: Repository<User>,
  ) {}

  findAll(): Promise<User[]> {
    return this.usersRepository.find();
  }

  create(name: string): Promise<User> {
    const user = this.usersRepository.create({ name });
    return this.usersRepository.save(user);
  }
}
```

```typescript
// src/users/users.controller.ts
import { Controller, Get, Post, Body } from '@nestjs/common';
import { UsersService } from './users.service';

@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Get()
  findAll() {
    return this.usersService.findAll();
  }

  @Post()
  create(@Body('name') name: string) {
    return this.usersService.create(name);
  }
}
```

* Test with Postman:
  * GET `http://localhost:3000/users`
  * POST `http://localhost:3000/users` with `{ "name": "Dude" }`.

**Exercise**:

1. Add a `Task` entity and endpoint to create tasks.

**Answer**:

```typescript
// src/tasks/task.entity.ts
import { Entity, Column, PrimaryGeneratedColumn } from 'typeorm';

@Entity()
export class Task {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  title: string;
}
```

***

### Part 4: Advanced NestJS

#### 4.1 Dependency Injection

NestJS uses dependency injection for services.

**Example**:

```typescript
// src/users/users.service.ts
import { Injectable } from '@nestjs/common';

@Injectable()
export class UsersService {
  getUsers() {
    return ['Dude', 'Alice'];
  }
}
```

```typescript
// src/app.controller.ts
import { Controller, Get } from '@nestjs/common';
import { UsersService } from './users/users.service';

@Controller()
export class AppController {
  constructor(private readonly usersService: UsersService) {}

  @Get('users')
  getUsers() {
    return this.usersService.getUsers();
  }
}
```

**Exercise**:

1. Create a `TasksService` and inject it into `AppController`.

#### 4.2 Pipes and Validation

Use pipes for input validation.

**Setup**:

```bash
npm install class-validator class-transformer
```

```typescript
// src/users/dto/create-user.dto.ts
import { IsString, MinLength } from 'class-validator';

export class CreateUserDto {
  @IsString()
  @MinLength(3)
  name: string;
}
```

```typescript
// src/users/users.controller.ts
import { Controller, Post, Body, ValidationPipe } from '@nestjs/common';
import { UsersService } from './users.service';
import { CreateUserDto } from './dto/create-user.dto';

@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Post()
  create(@Body(ValidationPipe) createUserDto: CreateUserDto) {
    return this.usersService.create(createUserDto.name);
  }
}
```

* POST `{ "name": "ab" }` fails (too short).

**Exercise**:

1. Add validation to ensure `Task.title` is at least 5 characters.

***

### Part 5: Project Setup

1. **Install Node.js**: [Download LTS](https://nodejs.org).
2.  **Create Project**:

    ```bash
    npm i -g @nestjs/cli
    nest new task-api
    cd task-api
    npm install @nestjs/typeorm typeorm sqlite3 class-validator class-transformer
    npm run start:dev
    ```
3. Open `http://localhost:3000`.

**Structure**:

```
task-api/
├── src/
│   ├── tasks/
│   ├── app.module.ts
│   ├── main.ts
├── package.json
```

***

### Part 6: Project: Task Management API

**Goal**: Build a REST API for tasks with CRUD operations.

**Code (src/tasks/task.entity.ts)**:

```typescript
import { Entity, Column, PrimaryGeneratedColumn } from 'typeorm';

@Entity()
export class Task {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  title: string;

  @Column()
  completed: boolean;
}
```

**Code (src/tasks/dto/create-task.dto.ts)**:

```typescript
import { IsString, MinLength } from 'class-validator';

export class CreateTaskDto {
  @IsString()
  @MinLength(5)
  title: string;
}
```

**Code (src/tasks/tasks.service.ts)**:

```typescript
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { Task } from './task.entity';
import { CreateTaskDto } from './dto/create-task.dto';

@Injectable()
export class TasksService {
  constructor(
    @InjectRepository(Task)
    private tasksRepository: Repository<Task>,
  ) {}

  findAll(): Promise<Task[]> {
    return this.tasksRepository.find();
  }

  create(createTaskDto: CreateTaskDto): Promise<Task> {
    const task = this.tasksRepository.create({
      title: createTaskDto.title,
      completed: false,
    });
    return this.tasksRepository.save(task);
  }

  async toggle(id: number): Promise<Task> {
    const task = await this.tasksRepository.findOneBy({ id });
    task.completed = !task.completed;
    return this.tasksRepository.save(task);
  }

  async delete(id: number): Promise<void> {
    await this.tasksRepository.delete(id);
  }
}
```

**Code (src/tasks/tasks.controller.ts)**:

```typescript
import { Controller, Get, Post, Body, Param, Delete, Put, ValidationPipe } from '@nestjs/common';
import { TasksService } from './tasks.service';
import { CreateTaskDto } from './dto/create-task.dto';

@Controller('tasks')
export class TasksController {
  constructor(private readonly tasksService: TasksService) {}

  @Get()
  findAll() {
    return this.tasksService.findAll();
  }

  @Post()
  create(@Body(ValidationPipe) createTaskDto: CreateTaskDto) {
    return this.tasksService.create(createTaskDto);
  }

  @Put(':id/toggle')
  toggle(@Param('id') id: string) {
    return this.tasksService.toggle(+id);
  }

  @Delete(':id')
  delete(@Param('id') id: string) {
    return this.tasksService.delete(+id);
  }
}
```

**Code (src/tasks/tasks.module.ts)**:

```typescript
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';
import { TasksController } from './tasks.controller';
import { TasksService } from './tasks.service';
import { Task } from './task.entity';

@Module({
  imports: [TypeOrmModule.forFeature([Task])],
  controllers: [TasksController],
  providers: [TasksService],
})
export class TasksModule {}
```

**Code (src/app.module.ts)**:

```typescript
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';
import { AppController } from './app.controller';
import { TasksModule } from './tasks/tasks.module';

@Module({
  imports: [
    TypeOrmModule.forRoot({
      type: 'sqlite',
      database: 'db.sqlite',
      entities: [__dirname + '/**/*.entity{.ts,.js}'],
      synchronize: true,
    }),
    TasksModule,
  ],
  controllers: [AppController],
})
export class AppModule {}
```

**Steps**:

1. Set up the project (Part 5).
2. Create `src/tasks/task.entity.ts`, `src/tasks/dto/create-task.dto.ts`, `src/tasks/tasks.service.ts`, `src/tasks/tasks.controller.ts`, `src/tasks/tasks.module.ts`.
3. Update `src/app.module.ts`.
4. Run `npm run start:dev`.
5. Test with Postman:
   * GET `http://localhost:3000/tasks`
   * POST `http://localhost:3000/tasks` with `{ "title": "Learn NestJS" }`
   * PUT `http://localhost:3000/tasks/1/toggle`
   * DELETE `http://localhost:3000/tasks/1`

**Exercises**:

1. Add an endpoint to update task titles.
2. Integrate with the Vue task tracker (from the Vue course) to fetch tasks.
3. Add a `description` field to `Task`.

**Answer (Update Title)**:

```typescript
// src/tasks/dto/update-task.dto.ts
import { IsString, MinLength } from 'class-validator';

export class UpdateTaskDto {
  @IsString()
  @MinLength(5)
  title: string;
}
```

```typescript
// src/tasks/tasks.service.ts
async update(id: number, updateTaskDto: UpdateTaskDto): Promise<Task> {
  const task = await this.tasksRepository.findOneBy({ id });
  task.title = updateTaskDto.title;
  return this.tasksRepository.save(task);
}
```

```typescript
// src/tasks/tasks.controller.ts
@Put(':id')
update(@Param('id') id: string, @Body(ValidationPipe) updateTaskDto: UpdateTaskDto) {
  return this.tasksService.update(+id, updateTaskDto);
}
```

***

### Part 7: Pro Practices

#### 7.1 Optimization

* **Config**: Use `@nestjs/config` for environment variables.
* **Performance**: Enable caching with `@nestjs/cache-manager`.
* **Testing**: Use `@nestjs/testing` for unit tests.

#### 7.2 Debugging

* Use VS Code’s debugger with `npm run start:debug`.
* Log errors with `@nestjs/common` Logger.

#### 7.3 Deployment

* Build: `npm run build`.
* Deploy to Heroku, AWS, or Render.

***

### Part 8: Next Steps

1. **Advanced NestJS**: Explore GraphQL, microservices, WebSockets.
2. **Integrations**: Pair with Vue/Nuxt, Tailwind, TypeORM.
3. **Projects**: Build a full-stack app with Nuxt frontend.
4. **Resources**:
   * [NestJS Docs](https://nestjs.com)
   * X’s #NestJS tag for community tips

***

### Conclusion

You’ve mastered NestJS: modules, controllers, services, TypeORM, and REST APIs. The task management API project applies these skills in a real-world backend. Keep practicing by extending the project or building new APIs. Search X for #NestJS if you’re stuck, or ask me for help!
