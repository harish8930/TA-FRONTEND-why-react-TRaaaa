#### Adding PropTypes To Article App Components

- Get the code from the app you have created in the previous exercise (Articles App)
- Add prop types to all the components
- All the props that a component accepts should be validated

[Typechecking With PropTypes](https://reactjs.org/docs/typechecking-with-proptypes.html).


import PropTypes from 'prop-types'
function Article(props){
return(
<li>
<figure>
<img src= {props.urlToImage} alt= {props.title}/>
<figcaption>
<h3>{props.title}</h3>
</figcaption>
</figure>
<p>{props.description}</p>
<a href= {props.url}>Read More </a>
</li>
)
}
Article.propTypes = {
    author:PropTypes.string,
    content: PropTypes.string,
    description:PropTypes.string,
    publishedAt:PropTypes.string,
    title:PropTypes.string,
    url: PropTypes.string,
    urlToImage:PropTypes.string

}


export default Article;
