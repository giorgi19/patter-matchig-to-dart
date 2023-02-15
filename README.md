# Pattern matching to Dart

### Multiple returs
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


### Control flow in argument lists
### Before

```dart
    ListTile(
     leading: const Icon(Icons.weekend),
     title: const Text('Welcome'),
     enabled: hasNextStep,
     subtitle: hasNextStep ? const Text('Tap to Advanced') : null,
     onTap: hasNextStep ? () { advance(); } : null,
     traling: hasNextStep ? null : const Icon(Icons.stop),
    )
```

### After

```dart

  ListTile(
     leading: const Icon(Icons.weekend),
     title: const Text('Welcome'),
     enabled: hasNextStep,
     if(hasNextStep) ...(
     subtitle:  const Text('Tap to Advanced'),
     onTap: () { advance(); },
     ) else ...(
     traling: const Icon(Icons.stop),
     )
    )

```

### JSON Destructing
### Before

```dart
var json = {'user': ['Lily', 20]};
if (json is Map<String, dynamic> &&
    json.length == 1 &&
    json.containsKey('user')) {
 var user = json [user];
 if (user is List<dynamic> &&
    user.length == 2 &&
    user [0] is String &&
    user [1] is int) {
  var name = user [2] as String;
  var age = user [1] as int;
  print('User $name is $age years old.');
 }
}
```

### After

```dart
var json = {'user: ['Lily,' 20]};
switch(json){
    case {'user': [String name, int age]}:
        print('User': $name is $age years old,');
        break;
        
    default:
        throw 'Unknow message';
}

```
