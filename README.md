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
