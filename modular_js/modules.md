# Modular Patterns:

## Douglas Crockford Style

```javascript
const Car = (name) => {
    //private vars
    let gas = 100;
    const self = {}

    //private method
    const useGas = (amount) => {
        gas -= amount
    }

    //public var
    self.name = name

    //public methods
    self.drive = (distance)=>{
        useGas(distance/5)
    }
    self.getGasLevel = ()=>{
        return gas
    }

    return self;
};

const myCar = Car("Awesome Car");
console.log(myCar.getGasLevel())
myCar.drive(10)
console.log(myCar.getGasLevel())
```

## MDN Style

```JavaScript
const Car = function(name) {
  //private var
  let gas = 100;

  //private method
  const useGas = (amount) => {
    gas -= amount;
  }

  //public methods
  this.drive = (distance) =>{
    useGas(distance/5);
  }
  this.getGasLevel = () => {
    return gas;
  }  

}

const myCar = new Car("Awesome Car");
console.log(myCar.getGasLevel())
myCar.drive(10)
console.log(myCar.getGasLevel())
```

## ES6 Class

This one is different, because basically everything is public, but some stuff can be hidden upon creation

```JavaScript
class Car {
    constructor(){
        //private vars
        this.gas = 100;
        this.useGas = (amount) => {
            this.gas -= amount
        }
    }
    //public methods
    drive(distance){
        this.useGas(distance/5)
    }
    getGasLevel(){
        return this.gas;
    }
}
const myCar = new Car("Awesome Car");
console.log(myCar.getGasLevel())
myCar.drive(10);
console.log(myCar.getGasLevel())
```
