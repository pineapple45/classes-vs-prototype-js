# Javascript Classes vs Prototype

### Classes Representation 

```javascript
    class Base{
        constructor(arg1,arg2){
            this.arg1 = arg1;
            this.arg2 = arg2;
        }

        function1(){
            ...
        }

        function2(){
            ...
        }
    }
```
### Prototype Representation

```javascript
   function Base(arg1,arg2){
        this.arg1 = arg1;
        this.arg2 = arg2;
   }
   
   Base.prototype.function1(){
       ...
   }

   Base.prototype.function2(){
       ...
   }
```

### Calling Objects representation

```javascript
    const base = new Base('val1','val2');
    base.function1(); // calling function1
    base.function2(); // calling function2
```

### Classes Representation 

```javascript
    class Inherited{
        constructor(arg1,arg2){
            this.arg1 = arg1;
            this.arg2 = arg2;
        }

        function1(){
            ...
        }

        function2(){
            ...
        }
    }

    class Base extends Inherited{
        constructor(arg1,arg2,arg3){
            super(arg1,arg2);
            this.arg3 = arg3;
        }

        function3(){
            ...
        }
    }
```

### Prototype Representation 

```javascript
    function Inherited(arg1,arg2){
        this.arg1 = arg1;
        this.arg2 = arg2;
    }

    // function Base(...args){
    //     Inherited.apply(this,args);
    //     this.arg3 = "some argument";
    // }

    function Base(arg1,arg2,arg3){
        Inherited.apply(this,args1,arg2);
        this.arg3 = arg3;

        // function3(){   not best practice
        //     ...
        // }
    }

    Inherited.prototype.function1(){
        ...
    }

    Inherited.prototype.function2(){
        ...
    }

    Base.prototype.function3(){
        ...
    }

```

### Calling Objects representation

```javascript
    const inherited = new Base('val1','val2');
    const base = new Inherited('val1','val2','val3');
    inherited.function1(); // calling function1
    inherited.function2(); // calling function2
    base.function3(); //calling function3 using base
```
### Method Chaining
```javascript
    class Base{
        constructor(arg1,arg2){
            this.arg1 = arg1;
            this.arg2 = arg2;
        }

        function1(){
            ...
            return this;
        }

        function2(){
            ...
            return this;
        }
    }

    const base = new Base('val1','val2');
    base.function1().function2(); //will not work if 'this' is not returned by both function1 and function2 of the class Base
```

