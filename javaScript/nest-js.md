# How does NestJS handle dependency injection?
NestJS uses a built-in dependency injection (DI) container. Services, repositories, 
and other providers are registered in modules, 
and NestJS automatically injects dependencies where needed using decorators like `@Injectable()` and `@Inject()`.

# Key properties of @Module:
1. **imports**: Modules that should be imported into the current module.
2. **controllers**: Controllers that should be instantiated by the NestJS runtime.
3. **providers**: Providers that should be instantiated by the NestJS runtime.
4. **exports**: Providers that should be exported from the current module.

# Request lifecycle:
1. **Incoming Request**: A client sends an HTTP request to the NestJS server.
2. **Middleware**: The request first passes through any middleware functions that are applied.
3. **Guards**: After middleware, guards are executed to determine whether the request should be allowed to proceed.
4. **Interceptors (Pre-Processing)**: Interceptors are executed before and after the route handler to transform requests and responses.
5. **Pipes (with DTOs)**: Pipes are executed after interceptors. This is where DTOs come into play for validation and transformation of request data.
6. **DTOs**: Data Transfer Objects are used to define the shape of the data and apply validation rules using decorators from the `class-validator` package.
7. **Validation Pipe**: A validation pipe is used to automatically validate the incoming request data against the DTO.
8. **Route Handler**: The request is then handled by the appropriate route handler (controller method).
9. **Interceptors (Post-Processing)**: After the route handler has processed the request, interceptors can again modify the response.
10. **Exception Filters**: If an exception is thrown, it is caught by exception filters.
11. **Outgoing Response**: The final response is sent back to the client.

# What is the purpose of the Reflector class in NestJS?
The Reflector class in NestJS is used to read metadata from classes and their properties. 
It is used internally by NestJS decorators to read and set metadata on classes and their properties.

# How do you implement custom decorators in NestJS?
Custom decorators can be implemented using the `@SetMetadata` function or by creating a function that returns a decorator. For example:

```typescript
import { SetMetadata } from '@nestjs/common';

export const CustomDecorator = (value: string) => SetMetadata('customKey', value);
```

# How do you handle file uploads in NestJS?
File uploads can be handled using the `@nestjs/platform-express` package along with the `MulterModule`. 
You can use the `@UploadedFile()` decorator to access the uploaded file in your controller.

# How do you implement custom pipes in NestJS?
Custom pipes can be implemented by creating a class that implements the `PipeTransform` interface and using the `@Injectable()` decorator.

```typescript
import { PipeTransform, Injectable, ArgumentMetadata, BadRequestException } from '@nestjs/common';

@Injectable()
export class CustomPipe implements PipeTransform {
  transform(value: any, metadata: ArgumentMetadata) {
    if (!value) {
      throw new BadRequestException('Validation failed');
    }
    return value;
  }
}
