---
title: "Delay the call with callback() in JS"
datePublished: Mon Oct 26 2020 11:24:58 GMT+0000 (Coordinated Universal Time)
cuid: cldva77c600r6vonv34lrccpn
slug: delay-the-call-with-callback-in-js-37009f5f2697

---

Functions are input output machine. One side we provide input the other side it provides the output. The calculations are done by processor and it may take time to calculate the output.

For the websites the responses can be delayed as the data travels over the network. This concept can be understood better by some analogy.

Suppose it’s tea time and you send your servent to bring some snacks and milk for you. Both the shops are in different directions. So the servent will first go to milk shop and then make tea and then bring the snacks.

Now imagine you hire a cook. The time will be reduced as the servent just go to milk shop give it to cook. In the time, the tea is being prepared servent may go and bring the snacks.

> Talk is cheap Show me the code, so here it is :)

```
// Pretend that this response is coming from the server  
const teaServed= [  
    {name: "Green Tea", ingredient: "Plain Water"},  
    {name: "Lemon Tea", subject: "Lemon Water"}  
]  
  
  
**function makeTea**(milkTea, **callback**){  
    setTimeout(function() {  
        teaServed.push(milkTea);  
        console.log("Milk Tea is ready!"); //task complete in bg  
 **callback();**    }, 3000);  
}  
// Tea is prepared in 3 seconds
```

```
**function serveTea**(){  
    setTimeout(function() {  
        let str = "";  
        teaServed.forEach(function(tea){  
            str += `<li> ${tea.name}</li>`  
        });
```

```
 document.getElementById('students').innerHTML = str;  
        console.log("Milk Tea has been served");  
    }, 1000);  
}
```

// Tea is being served in 1 seconds ; 

//Callback prevents Tea to be served until it has been made

```
`let newTea= {name:"Milk Tea", ingredient:"Cow Milk"}  
makeTea(newTea,getTea);  
//serveTea();` 
```

  
// **Output**  
// Without Callback  
// Green Tea Lemon Tea

// With Callback  
// Green Tea Lemon Tea Milk Tea

So first we define our teaServed (object array) with green tea and lemon tea already present as objects.

After that we call functions makeTea() which computes in 3 secs and **without callback function** it returns it pushes milkTea in milkServed array. Another function serveTea() populates that array inside our HTML to view on webpage which completes in 1 second.

The output of makeTea() returns late as a result it doesn’t get displayed on our webpage through serveTea function

Here comes the **callback function** through which we can delay the computation by putting it as argument in syntax of function which we want to compute.

After we have used the callback function, setTimout waits for 3 seconds executes lines(push milkTea object into teaServed array) and after that it calls the serveTea() to display the results on the webpage. This time it includes milkTea in the teaServed Array.