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
    <p>
            <input id="message-input" type="text">
    </p>
    <button onclick="getMessage()">Submit</button>
    <p id="message-output" style="text-align: center;"></p>
    <h2 id="result">😆</h2>
    <p id="answer"><em>Answer will appear here</em></p>
    <p><em id="count">Count appears here</em></p>
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
#count{
    font-family: Arial, Helvetica, sans-serif;
    font-size: 1rem;
}
#answer{
    font-family: Arial, Helvetica, sans-serif;
    font-size: 1rem; 
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
    document.getElementById("result").innerHTML = "";
    var quotes = {
        //data structure
        "Practice AMC 12 Q7" : "For how many integer values of m do the lines 13x + 11y = 700 and y = mx - 1 intersect in a point with integer coordinates?",

        "Practice AMC 12 Q3" : "Find n such that a regular n-gon has an equal number of sides and diagonals.",

        "Practice AMC 12 Q5" : "How many ways can each face of a cube be colored red or blue?", 

        "Practice AMC 12 Q10" : "How many of the numbers 1, 2, 3, ..., 2014 are not divisible by 6, 10, or 15?",

        "Practice AMC 12 Q1" : "A car has four regular tires and a spare tire. The car is driven 10000 miles, and the tires are rotated so that  all five tires are used equally. How many miles are driven on each tire?"
        //key and value
        //single quotes to include the double quotes
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
    document.getElementById("message-output").innerHTML = "";
}
var simple_answer = "";
var count = 0;
function showme(){
    var solutions = {  
        "2" : "2. Sub y = mx - 1 into 13x + 11y = 700 and get 13x + 11(mx-1) = 700 so 13x + 11mx = 711, x = 711/(13+11m) in which the only values that work are m= -9 and m = 79.", 

        "5" : "5. Try the polygons. A pentagon works.",

        "10" : "10. Casework. 1 (all sides red) + 2 (2 sides blue) + 2 (3 sides blue) and multiply by 2 due to symmetry.",
        
        "1478" : "1478. Use PIE. Divisible by 6, 10, or 15 is floor(2014/6) + floor(2014/10) + floor(2014/15). Then subtract multiples of 6 & 10, 6 & 15, 15 & 10. In each case, a multiple of 30 so floor(2014/30). Add back multiple of all three or floor(2014/30).",

        "8000" : "8000. Divide the total number of miles by each of the 4 tires being used at a time by 5. (1000*4)/5 = 8000."
        
    }
    console.log("index of answer: "+index);
    var simple_answers = Object.keys(solutions); //setting array of keys
    console.log("array of keys: "+simple_answers);
    simple_answer = simple_answers[index] //getting key corresponding to index, simple answer
    console.log("simpleanswer1: "+simple_answer);
    var solution = solutions[simple_answer] //getting solution (value) from key
    console.log("simple answer: "+simple_answer);
    console.log("solution: "+solution);
    count += 1;
    document.getElementById("count").innerHTML = "Number of problems done: " + count;
    document.getElementById("answer").innerHTML = solution;
}

/*Passing along user input*/
const messageInput = document.getElementById("message-input");
messageInput.addEventListener("keydown", function(event){
    if(event.key == "Enter")
        getMessage();
})
function getMessage(){
    document.getElementById("message-output").innerHTML = "Your answer: " + messageInput.value;
    console.log("input: "+messageInput.value);
    console.log("simpleanswer: "+simple_answer);
    console.log(messageInput.value==simple_answer);
    if(messageInput.value == simple_answer){
        document.getElementById("result").innerHTML = "Correct!"
    }
    else{
        document.getElementById("result").innerHTML = "Incorrect :("
    }
    messageInput.value = "";
}
</script>