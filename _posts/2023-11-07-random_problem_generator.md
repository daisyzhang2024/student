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
    <h3><b id="author">Problems courtesy of AMC</b></h3>
    <p id="answer"><em>Answer will appear here</em></p>
    </div>
    </div>
    <div style="text-align: center;">
    <button onclick="generate()" type="button" class="btn btn-primary">Generate Problem</button>
    <button onclick="showme()" type="button" class="btn btn-primary">Show me the answer!</button>
    </div>
</body>
</html>

<style>
@import url('https://fonts.googleapis.com/css2?family=Anek+Latin&family=PT+Serif&display=swap');
body{
    background: #ffb6c1;  
    font-family: 'Anek Latin', sans-serif;  
}
.container{
    width: 95%;
    height: 70vh;
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
    color: #4B4B4B;
    background-color: #f4edea;
    border: 10px solid #f4d1ae;
}
.quotes p, .quotes h3, .quotes h4{
    font-size: 1.5rem;
}
#quote{
    font-family: 'PT Serif', serif;
}
@media(max-width: 480px){ /*can be seen on cell phone nicely*/
    .quotes p, .quotes h3, .quotes h4{
        font-size: 1rem;
    }
}
</style>

<script>
var index = 0;
function generate(){
    var quotes = {
        //data structure
        "Practice AMC 12 Q1" : "A car has four regular tires and a spare tire. The car is driven 10000 miles, and the tires are rotated so that  all five tires are used equally. How many miles are driven on each tire?", 
        //key and value

        "Practice AMC 12 Q3" : "Find n such that a regular n-gon has an equal number of sides and diagonals.",

        "Practice AMC 12 Q5" : "How many ways can each face of a cube be colored red or blue?", 
        //single quotes to include the double quotes

        "Practice AMC 12 Q7" : "For how many integer values of m do the lines 13x + 11y = 700 and y = mx - 1 intersect in a point with integer coordinates?",

        "Practice AMC 12 Q10" : "How many of the numbers 1, 2, 3, ..., 2014 are not divisible by 6, 10, or 15?"
    }
    var authors = Object.keys(quotes);
    console.log(quotes);
    index = Math.floor(Math.random()*authors.length)
    console.log("index of key: "+index);
    var author = authors[index]
    var quote = quotes[author] //using dictionary, referencing key
    //access ids
    document.getElementById("quote").innerHTML = quote;
    document.getElementById("author").innerHTML = author;
}
var daan = "";
function showme(){
    const answers = [8000, 5, 10, 2, 1478]
    console.log("index of answer: "+index);
    daan = answers[index]
    console.log(daan);
    document.getElementById("answer").innerHTML = daan;
}
</script>