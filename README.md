# Flutter exceptions: 

### First of all
#### What is an exception
An exception is an event, which occurs during the execution of a program, that disrupts the normal flow of the program's instructions.

## The usual mode:

### Async function that returns a User inside a try and catch bloc, when we had a status code equal to 200 which means it is okay about our request we return a User model. Otherwise 

~~~dart
class ErrorController {
  Future<User> getRequest() async {
    try {
      final response = await http.get(
        Uri.parse('url'),
      );
      if (response.statusCode == 200) {
        return User.fromJSON(response.body);
      }
      throw 'Some unexpected error occurred';
    } catch (e) {
      rethrow;
    }
  }
}
~~~

When we call this class inside the view we can see an exception, why do we get this?

<img width="660" alt="Captura de Tela 2023-10-16 às 13 39 04" src="https://github.com/jjullimayanne/flutter-exceptions/assets/79465402/a884d1e5-8501-45ac-ba1c-caf6b967fd5f">


The reason for that is the rethrow from that getRequest is called whatever this function is called so to solve that we need to wrap that called in a `try catch` bloc and subsequently the UI code responsible for displaying either the success or failure text like that:

<img width="346" alt="Captura de Tela 2023-10-16 às 15 11 21" src="https://github.com/jjullimayanne/flutter-exceptions/assets/79465402/c6434074-04e6-45c3-8cdc-6038eb903e74">

### So why not to do that: 

Imagine that we will wrap all of our functions in `try catch` blocs for all our code, it`s easy to forget that rule and unnecessary because the exception handles itself. All our problem is in the function signature that does not specify whether we need to handle the error.

### How solve that:

A efficiente solution is use DartZ



#### util links:

[Functional error handling](https://resocoder.com/2019/12/14/functional-error-handling-in-flutter-dart-2-either-task-fp/)
[Advanced exceptions](https://www.youtube.com/watch?v=8AQC3hXmZ_w)








