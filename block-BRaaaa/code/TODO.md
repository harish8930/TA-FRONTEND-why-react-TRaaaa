#### Movie App

So before going into React let's try to understand the problem it solves. To do that we will be making a small application using JavaScript named "Movie Watch List App". To create this application use HTML, CSS and JavaScript.

![Movie Watch List](https://github.com/nnnkit/ac-js-images/blob/master/react/movie-watch.jpg?raw=true)

#### Requirements

- User can enter a movie name
- If you press enter the movie name will be added to the list below
- Each movie will have status (either watched or to watch)
- Default status will be `To Watch`
- Clicking on button should change the state form `To Watch` to `Watched` or vice versa.

#### How to make app

- In this folder you will find a `html`, `css` and `js` file.
- Add code in the respective files
Html
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



 <script src="script.js"></script> 
</body>
</html>

style
/* Reset default padding and margin */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  
  body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
  }
  
  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }
  
  h1 {
    text-align: center;
    margin-bottom: 20px;
  }
  
  input[type="text"] {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-bottom: 10px;
  }
  
  ul {
    list-style: none;
  }
  
  li {
    display: flex;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ccc;
  }
  
  label {
    margin-left: 10px;
    flex: 1;
    font-size: 16px;
  }
  
  span {
    margin-left: 10px;
    cursor: pointer;
    color: #ff4d4d;
    font-size: 18px;
  }
  
  input.styled-checkbox[type="checkbox"] {
    position: absolute;
    opacity: 0;
  }
  
  input.styled-checkbox[type="checkbox"] + label {
    position: relative;
    cursor: pointer;
    padding: 0;
  }
  
  input.styled-checkbox[type="checkbox"] + label:before {
    content: "";
    margin-right: 10px;
    display: inline-block;
    vertical-align: text-top;
    width: 20px;
    height: 20px;
    background: #fff;
    border: 1px solid #ccc;
    border-radius: 3px;
  }
  
  input.styled-checkbox[type="checkbox"]:checked + label:before {
    background: #007bff;
    border: 1px solid #007bff;
  }
  
  /* Remove default checkbox styles */
  input.styled-checkbox[type="checkbox"] + label:before {
    content: none;
  }
  
  /* Style checked checkbox */
  input.styled-checkbox[type="checkbox"]:checked + label:before {
    content: "\2713";
    font-size: 14px;
    text-align: center;
    line-height: 20px;
    color: #fff;
  }
  
  /* Add hover effect on list items */
  li:hover {
    background-color: #f5f5f5;
  }
  
  /* Add styling to the "Add" button */
  .add-button {
    display: block;
    width: 100%;
    text-align: center;
    background-color: #007bff;
    color: #fff;
    padding: 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    margin-top: 10px;
  }
  
  .add-button:hover {
    background-color: #0056b3;
  }
  
  .add-button:focus {
    outline: none;
  }


  javascript
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
   
    let li = document.createElement("li");
    let input = document.createElement("input");
    input.classList.add("styled-checkbox");
    input.type = "checkbox";
    input.id = i;
    input.checked = movie.watched;
    input.addEventListener("change",handlechange)
    let label = document.createElement("label");
    label.for = i;
    label.innerText = movie.name;
    let span = document.createElement("span");
    span.innerText = "X";
    span.addEventListener("click",handledelete);
span.setAttribute("data-id",i)
    li.append(input, label, span);
    rootElm.append(li);
  });
}








