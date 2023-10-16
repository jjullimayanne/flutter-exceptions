# flutter-exceptions

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
