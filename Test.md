```
class Person {
  firstName : string;
  lastName : string;
  age : number;
  private \_ssn : string;

  constructor(firstName:string, lastName:string, age:number, ssn:string) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
    this.\_ssn = ssn;
  }
}

let p = new Person('John', 'Smith', 29, '123-90-4567');
console.log('Last Name' + p.lastName + ' SSN : ' + p.\_ssn); // error
```

```
class Person {
  firstName : string;
  lastName : string;
  age : number;
  private _ssn : string;

  constructor(firstName:string, lastName:string, age:number, ssn:string) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
    this._ssn = ssn;
  }
}

let p = new Person('John', 'Smith', 29, '123-90-4567');
console.log('Last Name' + p.lastName + ' SSN : ' + p.\_ssn); // error
```
