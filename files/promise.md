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
