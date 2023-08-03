#### Refactor with React and ReactDOM

- Copy the code for Movie Watch List app you created in the last exercise
- Refactor the app to use `React` and `ReactDOM`
- We will use `React` to create element and `ReactDOM` to render the element on DOM
- Check if the application is working properly

#### Extra Info

CDN url for React and ReactDOM.

```html
<script
  crossorigin
  src="https://unpkg.com/react@17/umd/react.development.js"
></script>
<script
  crossorigin
  src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"
></script>
```
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

function createUi(data,root){
let ui = data.map((movie,i) => {
    return React.createElement('li',
    null,    
   React.createElement('label',
   {for: i},
 movie.name),
  React.createElement('button',{ id: i, onClick: handleChange},
  movie.watched ? 'Watched' : 'To Watch'
  
  )
  )

});
ReactDOM.render(ui,root);
}

createUi(allmovies,rootElm);










