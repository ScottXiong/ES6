# ES6
ECMA SCRIPT 6

## table of contents
+ [let & const]()
+ [Arrow Function]()
+ [Promise]()

### let & const
let 定义变量，const定义常量；let不可重复定义（否则会报错，the varible has been declared），var可以，let有块及作用域限制(即在块外是访问不到的);
```
//定义变量
let a=3;
a=4;

const pi=3.141592653;
console.log(a)；
console.log(pi)；

//作用域

if(true){
 var a=1
}
console.log(a); //1


if(true){
  let a=1;
}
console.log(a);//undifined

//ES5未声明先访问则会报错，但es6则不会
console.log(b)
var b=1;//undefined

console.log(b)
let b=1;//1
```

### Arrow Function
格式：参数 箭头 表达式/块
```
let b=1;
let a=a=>a*2;
console.log(a(b))//2
```
### promise
解决异步函数层层嵌套的问题
```
//promise结构
new Promise((resolve,reject)=>{
   //异步
   $.ajax({
     url:'http://happymmall.com/user/get_user_info.do',
     type:'post',
     success(res){
        resolve(res);
     },
     error(err){
        reject(err);
     }
   });
}).then((res)=>{
   console.log('success:',res);
},(err)=>{
   console.log(err)
})

//链式promise:多个串行的promise怎么用？只需要在上个promise成功的方法中返回下一个promise实例

var promiseFn1=new Promise((resolve,reject)=>{
   //异步
   $.ajax({
     url:'http://happymmall.com/user/get_user_info.do',
     type:'post',
     success(res){
        resolve(res);
     },
     error(err){
        reject(err);
     }
   });
})

var promiseFn2=new Promise((resolve,reject)=>{
   //异步
   $.ajax({
     url:'http://happymmall.com/cart/get_cart_product_count.do',
     type:'post',
     success(res){
        resolve(res);
     },
     error(err){
        reject(err);
     }
   });
})

promiseFn1.then(()=>{
  console.log('promiseFn1 succeed');
  return promiseFn2;
}).then(()=>{
  console.log('promiseFn2 succeed')
});
```
