#### Create a new object type based on old object type.

1. New object type must contain same keys as old object keys but the key assignee types should be different.

Example: 
```ts
type CurrentType = {
  firstName: string;
  age: number;
}

type DesiredType = {
  firstName: { defaultValue: 'myname', value: 'subrato'};
  age: {defaultValue: 20, value: 24};
}
```
Solution: 
```ts
type Greeting = {
  firstName: string;
  age: number;
}

type NewValueTypeOfGreeting<T> = {
  defaultValue: T;
  value: T;
}

type PropertiesBoolean<Type> = {
  [key in keyof Type]: NewValueTypeOfGreeting<Type[key]>;
};

const a: PropertiesBoolean<Greeting> ={
  firstName: { defaultValue: 'sdf', value: 'string'},
  age  : {defaultValue:0, value:0},
}

type OutputGreeting = {
  firstName: { defaultValue: string; value: string; }
  age: { defaultValue: number; value: number;}
}
```
