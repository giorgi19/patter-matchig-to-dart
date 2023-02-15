# Pattern matching to Dart

### Before
```dart
    List<Object> userInfo(Map<String, dynamic> json) {
      return [json['name'] as String, json['age'] as int];
    }
    
    var json = {name: 'Girogi', age: '24'};
      
    main(){
      var info = userInfo(json);
      var name = info[0] as String;
      var age = info[1] as int;
    }
    
 ```
### After 

```dart
    (String, int) userInfo(Map<String, dynamic> json) {
      return [json['name'] as String, json['age'] as int];
    }
    
    var json = {name: 'Girogi', age: '24'};
      
    main(){
      var (name, age) = userInfo(json);
    }

```
