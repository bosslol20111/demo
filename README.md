<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Caro</title>
	<style>
		body{
			width: 1000px;
			height: auto;
		}
		.container{
			width: 310px;
			margin-left: 500px;
			margin-top: 150px;
		}
		.container div{
			width: 100px;
			height: 100px;
			border: 1px solid black; 
			font-size: 85px;
			text-align: center;
			line-height: 100px; 
			cursor: pointer;
		}
		.container div:hover{
			background-color:blue;
		}
		.box {
			float: left;
		}
		button {
			width: 130px;
			height: 70px;
			margin-left: 600px;
			margin-top: 10px;
		}
		span{
			margin: 0px;
			padding: 0px;
			margin-left: 550px;
			font-size: 80px;
		}
	</style>
</head>
<body>
	<span id="turn">Caro</span>
	<div class="container" id="main">
		<div class="box" id="box1"></div>
		<div class="box" id="box2"></div>
		<div class="box" id="box3"></div>
		<div class="box" id="box4"></div>
		<div class="box" id="box5"></div>
		<div class="box" id="box6"></div>
		<div class="box" id="box7"></div>
		<div class="box" id="box8"></div>
		<div class="box" id="box9"></div>
	</div>
	<form action="">
		<button onclick="replay();">Play again</button>
	</form>
	<script type="text/javascript">
		var turn = document.getElementById("turn");
		var boxes = document.querySelectorAll("#main div"),X_or_O=0,
		turn = document.getElementById("turn");
		function selectWinnerBoxes(b1,b2,b3){
			b1.style.background ="red";
			b2.style.background ="red";
			b3.style.background ="red";
			turn.innerHTML = b1.innerHTML + "Won Gratz";
		}
		function getWinner() {
		var box1= document.getElementById("box1"),
		box2= document.getElementById("box2"),
		box3= document.getElementById("box3"),
		box4= document.getElementById("box4"),
		box5= document.getElementById("box5"),
		box6= document.getElementById("box6"),
		box7= document.getElementById("box7"),
		box8= document.getElementById("box8"),
		box9= document.getElementById("box9");
			if(box1.innerHTML !== "" && box1.innerHTML === box2.innerHTML && box1.innerHTML=== box3.innerHTML)
				selectWinnerBoxes(box1,box2,box3);
			else if (box4.innerHTML !=="" && box4.innerHTML === box5.innerHTML && box4.innerHTML===box6.innerHTML) 
				selectWinnerBoxes(box4,box5,box6);
			else if (box7.innerHTML !== "" && box7.innerHTML === box8.innerHTML && box7.innerHTML===box9.innerHTML)
				selectWinnerBoxes(box7,box8,box9);
			else if (box1.innerHTML !== "" && box1.innerHTML === box4.innerHTML && box1.innerHTML===box7.innerHTML)
				selectWinnerBoxes(box1,box4,box7);
			else if (box2.innerHTML !== "" && box2.innerHTML === box5.innerHTML && box2.innerHTML===box8.innerHTML)
				selectWinnerBoxes(box2,box5,box8);
			else if (box3.innerHTML !== "" && box3.innerHTML === box6.innerHTML && box3.innerHTML===box9.innerHTML)
				selectWinnerBoxes(box3,box6,box9);
			else if (box1.innerHTML !== "" && box1.innerHTML === box5.innerHTML && box1.innerHTML===box9.innerHTML)
				selectWinnerBoxes(box1,box5,box9);
			else if(box3.innerHTML !== "" && box3.innerHTML === box5.innerHTML && box3.innerHTML===box7.innerHTML)
				selectWinnerBoxes(box3,box5,box7);
		}
		for(var i =0; i < boxes.length ; i++){
				boxes[i].onclick = function(){
					if(this.innerHTML !== "X" && this.innerHTML !== "O"){
					if(X_or_O%2===0){
						this.innerHTML = "X";
						getWinner();
						turn.innerHTML ="O turn";
						X_or_O +=1;
					}else
					{
						this.innerHTML ="O";
						getWinner();
						turn.innerHTML="X turn";
						X_or_O +=1;
					}
				}
			}
		}
		function replay(){
			for(var i =0; i<boxes.length;i++){
				boxes[i].innerHTML="";
			}
		}
	</script>
</body>
</html>
