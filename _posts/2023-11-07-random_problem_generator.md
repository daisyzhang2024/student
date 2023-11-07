---
layout: base
title: random problem generator
description: generates random problems
type: hacks
courses: { compsci: {week: 2} }
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.3.1/dist/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    <title>Random Problem Generator!</title>
</head>
<body>
    <div class="container">
    <div class="quotes">
    <p id="quote">Click button to generate random problems!</p> <!-- want to access later so have id-->
    <h3 id="author">Problems courtesy of AMC</h3>
    </div>
    </div>
    <div style="text-align: center;">
    <button onclick="generate()" type="button" class="btn btn-primary">Generate Quote</button>
    </div>
</body>
</html>

<style>
body{
    background: #ffb6c1;    
}
.container{
    width: 95%;
    height: 100vh;
    display: flex;
    text-align: center;
}
.quotes{
    width: 900px;
    height: 450px;
    margin: auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 0 50px; /*left to right padding*/
    color: gray;
    background-color: #f4edea;
    border: 10px solid #f4d1ae;
}
.quotes p, .quotes h3{
    font-size: 1.5rem;
}

@media(max-width: 480px){ /*can be seen on cell phone nicely*/
    .quotes p, .quotes h3{
        font-size: 1rem;
    }
}
</style>

<script>
function generate(){
    var quotes = {
        //data structure
        "Algebra" : "A car has four regular tires and a spare tire. The car is driven 10000 miles, and the tires are rotated so that  all five tires are used equally. How many miles are driven on each tire?", //key and value
        "Geometry" : "Find n such that a regular n-gon has an equal number of sides and diagonals.",
        "Counting" : "How many ways can each face of a cube be colored red or blue?", //single quotes to include the double quotes
        "Algebra" : "For how many integer values of m do the lines 13x + 11y = 700 and y = mx - 1 intersect in a point with integer coordinates?",
        "Counting" : "How many of the numbers 1, 2, 3, ..., 2014 are not divisible by 6, 10, or 15?"
    }
    var authors = Object.keys(quotes);
    console.log(authors);
    var author = authors[Math.floor(Math.random()*authors.length)]
    var quote = quotes[author]; //using dictionary
    //access ids
    document.getElementById("quote").innerHTML = quote;
    document.getElementById("author").innerHTML = author;
}
</script>