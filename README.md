# js
# flattening object in js with `_` pattern 
```
ob = {
  a: {
    b: {
      c: (a, b) => a + b
    },
    d: (a, b) => a - b
  },
  f: (a, b) => a * b
};
obj = {};
function applyVal(t,parent) {
   
         for(let o of Object.keys(t)) {  
       //console.log(o)
           if(typeof(t[o]) == 'object') {
             parent ? applyVal(t[o],parent+'_'+o) :
             applyVal(t[o],o)
           }
           else {
               parent ? obj[parent+'_'+o] = t[o]:
               obj[o] = t[o];
           }
        
        console.log(obj);
      }
     return obj;
}

console.log(applyVal(ob));
