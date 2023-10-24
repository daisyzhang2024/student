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
    startCells.forEach((cell, index) => {
        const cellElement = document.createElement('div')
        cellElement.classList.add('square')
        gameBoard.append(cellElement)
    })
}
createBoard()
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

#gameboard {
    width: 300px;
    height: 300px;
    background-color: black;
    display: flex;
    flex-wrap: wrap;
}

.square { /*class of square*/
    width: 100px;
    height: 100px;
    background-color: white;
}
</style>