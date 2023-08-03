#### Movie App with JSX

- Copy the code from previous exercise.
- Refactor it to use `JSX` using babel
- Use the links given below for babel
- Make sure to follow the example for writing JSX

#### Basic Info

CDN url for babel to use in our project.

```html
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
```

While using Babel don't forget to change `type` attribute of `script` element.

```html
<script type="text/babel">
  // JSX code goes here
</script>
```




<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Movie app</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Movie Watch App</h1>
        <input type="text" placeholder="Enter the movie name"/>
        <ul class="movieList"></ul>
    </div>






    <script
    crossorigin
    src="https://unpkg.com/react@17/umd/react.development.js"
  ></script>
  <script
    crossorigin
    src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"
  ></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
 <script type="text/babel">

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
    return(
<li  key = {movie.name} >
  <label htmlFor = {i} >{movie.name}</label>
  <button id = {i} onClick = {handleChange}>{movie.watched ? 'Watched' : 'To Watch'}</button>

  </li>
    )
});
ReactDOM.render(ui,root);
}
createUi(allmovies,rootElm);

 </script> 
</body>
</html>



















