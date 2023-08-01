#### Movie App with createElement

- Create you own `createElement` function similar to `elm` function in the explainer videos
- Refactor the movie watch list app created in the previous exercise to use `createElement` function to create DOM element in the app.
- You can copy your code form previous exercise and refactor
- Make sure all the functionality of the application works properly
function elm(type, attr = {}, ...children){
let element = document.createElement(type);
for(let key in attr){
    if(key.startsWith("data-")){
        element.setAttribute(key,attr[key]);
    }else{
        element[key] = attr[key]
    }
}
children.forEach((child)=>{
    if(typeof child === "object"){
        element.append(child);
    }if(typeof child === "string"){
        let node = document.createTextNode(child);
        element.append(node);
    }
})
return element;
}






let input = document.querySelector(`input[type="text"]`);
let rootElm = document.querySelector(".movieList")

let allmovies = [{
name: "forest Gump",
watched: false,
},

{
name: "Inception",
watched: false,
}


]

input.addEventListener("keyup",(event)=>{
  if(event.keyCode === 13){
    allmovies.push({
      name: event.target.value,
      watched: false,
    });
    createUi();
     // Clear the input field after adding a movie
  }
});




function handledelete(event){
let id = event.target.dataset.id;
allmovies.splice(id,1)
createUi();
}

function handlechange(event){
    let id = event.target.id;
    allmovies[id].watched = !allmovies[id].watched
}

function createUi(){
rootElm.innerHTML = ""; 
  allmovies.forEach((movie,i) =>{
let li = elm("li",
{},
elm("input",
{
type: "checkBox",
className: "styled-checkBox",
"data-id": i,
checked: movie.watched
}),
elm("label",{
for: i,
ineerText: movie.name
}),
elm("span",{
    
},"X")

)

span.addEventListener("click",handledelete);
span.setAttribute("data-id",i)
rootElm.append(li)
  });

}

createUi();
