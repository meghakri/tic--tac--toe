HTML codes 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tic-Tac-Toe Game</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="msg-container  hide" >
        <p id="msg">Winner</p>
        <button id="new-btn">New Game</button>
    </div>
    <main>
        <h1>Tic Tac Toe</h1>
     <div class="container">
        <div class="game">
         
            <button class="box"></button>
            <button class="box"></button>
            <button class="box"></button>
            <button class="box"></button>
            <button class="box"></button>
            <button class="box"></button>
            <button class="box"></button>
            <button class="box"></button>
            <button class="box"></button>


        </div>
     </div>

     <button id="reset-btn">Reset Game</button>
    </main>
    
        
    <script src="app.js"></script>
</body>
</html>




                                             CSS code

*
{
    margin:0;
    padding:0;
}

body{
    background-color: #548687;
    text-align: center;
}

.container{
    height:70vh;
    display:flex;
    
    justify-content: center;
    align-items:center;

   
}

.game{
    height: 60vmin;
    width: 60vmin;
    display:flex;
    flex-wrap :wrap;
    justify-content: center;
    align-items:center;
    gap:1.5vmin;

}

.box{
    height:18vmin;
    width:18vmin;
    border-radius: 1rem;
    border:non;
    box-shadow:0 0 1rem rgba(0,0,0,0.3);

    font-size:7vmin;
    color:#b0413e;
    background-color:#F7D560;
}
#reset-btn
{
    padding:1rem;
    font-size:1.25rem;
    background-color: #191913;
    color:#fff;
    border-radius:1rem;
    border:none;

}

#new-btn{
    padding:1rem;
    font-size:1.25rem;
    background-color: #191913;
    color:#fff;
    border-radius:1rem;
    border:none;

}
#msg
{
    color:#ffffc7;
    font-size:5vmin;

}
.msg-container
{
    height:100vmin;
    display:flex;
    justify-content: center;
    align-items:center;
    flex-direction: column;
    gap:4rem;
    
}
.hide
{
    display:none;
}


                                                       java script 


let boxes= document.querySelectorAll(".box");
 let resetbtn=document.querySelector("#reset-btn");
let newgamebtn=document.querySelector("#new-btn");
let msgcontainer=document.querySelector(".msg-container");
let msg =document.querySelector("#msg");


 let turn0=true;

 const winpattern=[
    [0,1,2],
    [0,3,6],
    [0,4,8],
    [1,4,7],
    [2,5,8],
    [2,4,6],
    [3,4,5],
    [6,7,8],
 ];

 const resetgame=()=>{
    turn0=true;
    enableboxes();
    msgcontainer.classList.add("hide");
 }

 boxes.forEach((box)  => {
    box.addEventListener("click",()=>{
        
       if(turn0)
       {
        box.innerText="O";
        turn0=false;
       }
       else{
        box.innerText="X";
        turn0=true;
       }
       box.disabled=true;

       checkwinner();
       
    });
 });

 const disableboxes=()=>{
    for(let box of boxes){
        box.disable=true;
    }
 };
 const enableboxes=()=>{
    for(let box of boxes){
        box.disabled=false;
        box.innerText="";
    }
 };

 const showinner=(winner)=>{
    msg.innerText=`congratulation,winner is ${winner}`;
  msgcontainer.classList.remove("hide");
   disableboxes();
};

 const checkwinner =()=>{
    for(let pattern of winpattern)
    {
    //     console.log(pattern[0],pattern[1],pattern[2]);
    //   console.log(boxes[pattern[0]].innerText,boxes[pattern[1]].innerText,boxes[pattern[2]].innerText);
    
     let pos1val=boxes[pattern[0]].innerText;
     let pos2val=boxes[pattern[1]].innerText;
     let pos3val=boxes[pattern[2]].innerText;
    
     if(pos1val!="" && pos2val!="" && pos3val !=""){

     if(pos1val===pos2val && pos2val===pos3val){
        
        showinner(pos1val);
        
     }
     }
    }
};
    newgamebtn.addEventListener("click",resetgame);
    resetbtn.addEventListener("click",resetgame);
                                                       


                                             
