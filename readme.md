# Javascript Classes vs Prototype

### Classes Representation

```javascript
    class Base {
        constructor(arg1,arg2) {
            this.arg1 = arg1;
            this.arg2 = arg2;
        }

        function1() {
            ...
        }

        function2() {
            ...
        }
    }
```

### Prototype Representation

```javascript
   function Base(arg1,arg2) {
        this.arg1 = arg1;
        this.arg2 = arg2;
   }

   Base.prototype.function1() {
       ...
   }

   Base.prototype.function2() {
       ...
   }
```

### Calling Objects of the classes

```javascript
const base = new Base('val1', 'val2');
base.function1(); // calling function1
base.function2(); // calling function2
```

### Inheritance in Classes

```javascript
    class Inherited {
        constructor(arg1,arg2) {
            this.arg1 = arg1;
            this.arg2 = arg2;
        }

        function1() {
            ...
        }

        function2() {
            ...
        }
    }

    class Base extends Inherited {
        constructor(arg1,arg2,arg3) {
            super(arg1,arg2);
            this.arg3 = arg3;
        }

        function3() {
            ...
        }
    }
```

### Inheritance using prototype

```javascript
    function Inherited(arg1,arg2) {
        this.arg1 = arg1;
        this.arg2 = arg2;
    }

    // function Base(...args){
    //     Inherited.apply(this,args);
    //     this.arg3 = "some argument";
    // }

    function Base(arg1,arg2,arg3) {
        Inherited.apply(this,args1,arg2);
        this.arg3 = arg3;

        // function3(){   not best practice
        //     ...
        // }
    }

    Inherited.prototype.function1() {
        ...
    }

    Inherited.prototype.function2() {
        ...
    }

    Base.prototype.function3() {
        ...
    }

```

### Calling Objects of the classes

```javascript
const inherited = new Base('val1', 'val2');
const base = new Inherited('val1', 'val2', 'val3');
inherited.function1(); // calling function1
inherited.function2(); // calling function2
base.function3(); //calling function3 using base
```

### Method Chaining

```javascript
    class Base {
        constructor(arg1,arg2) {
            this.arg1 = arg1;
            this.arg2 = arg2;
        }

        function1() {
            ...
            return this;
        }

        function2() {
            ...
            return this;
        }
    }

    const base = new Base('val1','val2');
    base.function1().function2(); //will not work if 'this' is not returned by both function1 and function2 of the class Base
```

### classes full example with inheritence

```javascript
class Inherited {
  constructor(i1, i2) {
    this.i1 = i1;
    this.i2 = i2;
  }

  sum() {
    console.log(this.i1 + this.i2);
    return this;
  }

  product() {
    console.log(this.i1 * this.i2);
    return this;
  }
}

class Base extends Inherited {
  constructor(b1, b2, b3) {
    super(b1, b2);
    this.b1 = b1;
    this.b2 = b2;
    this.b3 = b3;
  }

  sum_base() {
    return this.b1 + this.b2 + this.b3;
  }
}

const b = new Base(1, 2, 3);
// b.sum_base();
b.sum();
b.product().sum();
```
