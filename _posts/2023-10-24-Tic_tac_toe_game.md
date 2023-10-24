---
toc: false
comments: false
layout: post
title: Tic-Tac-Toe
description: Simple Tic-Tac-Toe game made from youtube tutorial
type: hacks
courses: { compsci: {week: 7} }
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Tic-tac-toe JavaScript</title>
    <link rel="stylesheet" href="styvles.css">
</head>
<body>
    <div id="gameboard"></div>
    <p id="info"></p>
</body>
</html>

<script>
const gameBoard = document.querySelector('#gameboard')
const infoDisplay = document.querySelector('#info')
const startCells = [
    "", "", "", "", "", "", "", "", ""
    ]

function createBoard(){
    startCells.forEach((_cell, index) => {
        const cellElement = document.createElement('div')
        cellElement.classList.add('square')
        cellElement.id = index //giving id to each box element
        cellElement.addEventListener('click', addGo)
        gameBoard.append(cellElement)
    })
}
createBoard()


function addGo(e) { //add circle or cross if nothing is there yet
    console.log(e.target) //returns id of square each time you click it
    const goDisplay = document.createElement('div')
    goDisplay.classList.add('circle') //add class of circle every time we click, append to whatever we click on
    e.target.append(goDisplay) //append element that we just created
}
</script>

<style>
body {
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 100vh;
}

#gameboard { /*hashtag for ID*/
    width: 300px;
    height: 300px;
    background-color: black;
    display: flex;
    flex-wrap: wrap;
    border: solid 1px black;
}

.square { /*class of square*/
    width: 100px;
    height: 100px;
    background-color: white;
    border: solid 2px black;
    box-sizing: border-box;
    display: flex;
    justify-content: center; /*centering O*/
    align-items: center;
}

.circle {
    height: 90px;
    width: 90px;
    border-radius: 50%;
    border: 15px solid blue;
    box-sizing: border-box;
}
</style>