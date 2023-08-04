#### Create Article Card Using JSX

- Create an article card using JSX
- Have a look at UI down below
- Use the object below for the information in the card

```js
let cardInfo = {
  title: 'City Lights in New York',
  date: new Date('2017-01-26'),
  comments: 67,
  subTitle: 'The city that never sleeps.',
  description:
    'New York, the largest city in the U.S., is an architectural marvel with plenty of historic monuments, magnificent buildings and countless dazzling skyscrapers.',
  category: 'photos',
  imageURL:
    'https://images.unsplash.com/photo-1610874933184-7728fd666162?ixid=MXwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHwzfHx8ZW58MHx8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=60',
};
```

#### Preview
.
![Article Card](./assets/card.jpg)

let root = document.getElementById("column");
  const monthname = [
"january",
"febuary",
"March",
"April",
"May",
"June",
"July",
"August",
"September",
"October",
"November",
"December",
  ]

let cardInfo = {
  title: 'City Lights in New York',
  date: new Date('2017-01-26'),
  comments: 67,
  subTitle: 'The city that never sleeps.',
  description:
    'New York, the largest city in the U.S., is an architectural marvel with plenty of historic monuments, magnificent buildings and countless dazzling skyscrapers.',
  category: 'photos',
  imageURL:
    'https://images.unsplash.com/photo-1610874933184-7728fd666162?ixid=MXwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHwzfHx8ZW58MHx8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=60',
};



let ui = (
    <div className = "post-module hover">
        <div className = "thumbnail">
            <div className="date">
<div className = "day">{cardInfo.date.getDate()}</div>
    <div className="month">{monthname[cardInfo.date.getMonth()].slice(0,3)} </div>
    </div>
    <img src = {cardInfo.imageURL}/>
    </div>
    <div className = "post-content">
        <div className="category">{cardInfo.category}</div>
        <h1 className ="title">{cardInfo.title}</h1>      
        <h2 className = "subtitle">{cardInfo.subTitle}</h2>
        <p className="description">{cardInfo.description}</p>
        <div className ="post-meta">
            <span className ="comments">
                <i className = "fa fa-comments"></i>
                    <a href="#">{cardInfo.comments}comments</a>
                    </span>
                    </div>
                    </div>
                    </div>   
    ) 
ReactDOM.render(ui,root);

 </script>


























