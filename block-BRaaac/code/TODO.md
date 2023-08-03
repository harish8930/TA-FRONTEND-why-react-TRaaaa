#### Movie App with createElement

- Create you own `createElement` function similar to `elm` function in the explainer videos
- Refactor the movie watch list app created in the previous exercise to use `createElement` function to create DOM element in the app.
- You can copy your code form previous exercise and refactor
- Make sure all the functionality of the application works properly






let input = document.querySelector("input");
let rootElm = document.querySelector(".movieList");

let allmovies = [
  {
name : "Forest Gump",
watched: false,
},
{
name : "Inception",
watched: true,
}
]

input.addEventListener("keyup",(event)=>{
if(event.keyCode === 13){
  allmovies.push({
    name: event.target.value,
    watched: false,
  });
  event.target.value = "";
  createUi(allmovies,rootElm)
}
})



function handleChange(event){
let id = event.target.id;

allmovies[id].watched = !allmovies[id].watched
createUi(allmovies,rootElm)

}



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
  
function createUi(data,root){
rootElm.innerHTML = "";
allmovies.forEach((movie,i) =>{
let btn = elm("button",
  {id:i},
movie.watched? "watched" : "to watch"
);
btn.addEventListener("click",handleChange)
  let li = elm("li",{},    
  elm("label",{
    for:i,
    innerText: movie.name,
  }),
btn
  )
rootElm.append(li);
});

}

createUi();
