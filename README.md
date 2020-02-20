# wdi-fundamentals-memorygame


<!DOCTYPE html>
<html>
	<head>
		<title>Memory Card Game</title>
		<link href="https://fonts.googleapis.com/css?family=Droid+Serif|Raleway:400,500,600,700" rel="stylesheet">
        <link href="css/style.css" rel="stylesheet" type="text/css">
	</head>
	
<body>
<header>
	<h1> Memory Game</h1>
</header>
<nav>
	<a href="#">Instructions</a>
<a href="#">Game</a>
</nav>
<main>
<h2> Instructions </h2>
<p>Concentration, also known as Match Match, Memory, Pelmanism, Shinkei-suijaku, Pexeso or simply Pairs, is a card game in which all of the cards are laid face down on a surface and two cards are flipped face up over each turn. The object of the game is to turn over pairs of matching cards.</p>
<div id="game-board" class="board clearfix"></div>
</main>
<footer class="clearfix">
	<p class="copyright">
		Copyright 2017
	</p>
	<p class="message">
		Created with &hearts; by <span class="name">GA</span>
	</p>
 </footer>
 <script src="js/main.js"></script>

</body>
</html>


body {
text-align: center;
	margin: 0;
}

header {
background-color: #F15b31;
color: #FFFFFF;
padding: 30px 20px 30px 20px;
}

nav {
	background-color: #00A6B3;
	color: #FFFFFF;
	padding: 20px 0 20px 0;
}

h1 {
margin: 0;	
font-family: "Raleway", sans-serif;
color: #FFFFFF;
letter-spacing: 1px;
font-weight: 400;
font-size: 45px;
}

a {
	font-family: "Raleway", sans-serif;
	letter-spacing: 1px;
	font-weight: 600;
	font-size: 18px;
	color: #FFFFFF;
	margin: 0 20px 0 20px;
	border-bottom: 2px solid transparent;
}

a:hover {
color: white;
}

h2 {
	font-family: "Raleway", sans-serif;
	color: #0D2C40;
	letter-spacing: 1px;
	font-weight: 600;
	font-size: 20px;
}

main {
	width: 850px;
	margin-top: 35px;
	margin-right: auto;
	margin-bottom: 850px;
	margin-left: auto;
}

img {
	margin: 40px 8px 0 8px;
}

p {
font-family: "Droid Serif", serif;
line-height: 26px;
font-size: 18px;
}

footer {
	padding: 20px;
	background-color: #0D2C40;
	color: white;
	font-size: 14px;
	letter-spacing: .08em;
	font-weight: 500;
}

.copyright {
    font-family: "Raleway", sans-serif;
    float: left;
 }

.message {
	font-family: "Raleway", sans-serif;
    float: right;
}

.name {
	color: #F15b31;
	font-weight: 700;
}

.clearfix:after {
visibility: hidden;
display: block;
content: " ";
clear: both;
height: 0;
font-size: 0;
};


let cards = [
{
rank: "queen",
suit: "hearts",
cardImage: "images/queen-of-hearts.png"
},
{
rank: "queen",
suit: "diamonds",
cardImage: "images/queen-of-diamonds.png"
},
{
rank: "king",
suit: "hearts",
cardImage: "images/king-of-hearts.png"
},
{
rank: "king",
suit: "diamonds",
cardImage: "images/king-of-diamonds.png"
},
];

let cardsInPlay = [];

function checkForMatch() {
  if (cardsInPlay[0] === cardsInPlay[1]) {
  	alert("You found a match!");
  } else {
  	alert("Sorry try again.");

  }
};

function flipCard() {
	const cardId = this.getAttribute('data-id');
	console.log("User flipped " + cards[cardId].rank);
	console.log(cards[cardId].cardImage);
	console.log(cards[cardId].suit);
	cardsInPlay.push(cards[cardId].rank);	
	this.setAttribute("src", cards[cardId].cardImage);
	if (cardsInPlay.length === 2) {
        checkForMatch ();
	}

};


function createBoard() {
	for (let i = 0; i < cards.length; i++) {
    let cardElement = document.createElement('img');
    cardElement.setAttribute('src', 'images/back.png');
    cardElement.setAttribute('data-id', i);
    document.getElementById("game-board").appendChild(cardElement);
    cardElement.addEventListener('click', flipCard);

}
};

createBoard();


