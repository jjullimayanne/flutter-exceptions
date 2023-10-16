# flutter-exceptions

### first of all
#### What is a exception
An exception is an event, which occurs during the execution of a program, that disrupts the normal flow of the program's instructions.

### Async funciton that returns a User inside a try and catch bloc, when we had a status code equal to 200 which means its okay about our request we return a User model. Otherwise 

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

The reason for that is the rethrow from that getRequest is called whatever this function is called so to solve that we need wrap that called in a try catch bloc 

