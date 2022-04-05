# ES6

## this

- default
```js
//최상위는 window

1. console.log(this) // window

2. function example(){
    console.log(this) //window  ( example을 담고 있는 애도 window )
}
```

- Object

```js
3. let object= {
    name : 'kim'
    age : 20
    fuc : function(){
        console.log(this); // object  ( 나를 포함한 오브젝트 )
    }
} //object.fuc(); 

3-1. let object= {
    name : 'yoo'
    age : 27
    data: {
        fuc : function(){
            console.log(this) // object.data; ( 나를 포함한 바로 위 오브젝트 ) 
        }
    }
} //object.data.fuc();

3-2. let object= {
    name : 'sik'
    age : 30
    data: {
        fuc : () => {  // arrow function
            console.log(this) // window ( 함수 밖에 있던 것 그대로 사용 ) 
        }
    }
} 
```
- constructor
```js
4. 

function ex(){
    this.name = 'kim'
}

let object = new ex(); // ex { name : 'kim' }
```

- **이벤트리스너**
```js
$('#id').on('click',function(){
    this; // e.currentTarget;  -> 현재 이벤트가 동작하는 곳
})
```