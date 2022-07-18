let gamebox = document.querySelector(".gamebox");
let ctx = gamebox.getContext("2d");
let scoretext = document.querySelector(".scoretext");
let restartbtn = document.querySelector(".restart");
let gamewidth = gamebox.width;
let gameheight = gamebox.height;
let running = false;
let unitsize = 23;
let xvol = unitsize;
let yvol = 0;
let foodx;
let foody;
let score = 0;


let snake = [
    {x:unitsize * 4 , y:0},
    {x:unitsize * 3 , y:0},
    {x:unitsize * 2 , y:0},
    {x:unitsize , y:0},
    {x:0 , y:0}
];

window.addEventListener("keydown", changethedirction);
restartbtn.addEventListener("click" , restartthegame);


startgame();


function startgame()
{
    running = true;
    
    gettick();
    createfood();

};

function gettick()
{
      if(running){
        setTimeout(() => {
            
            creategamebox();
            drawfood();
            movethesnake();
            drawsnake();
            checkgameover();
            gettick();

        }, 80);
    }else
    {
        displaygameover();
    }

};

function creategamebox()
{
    ctx.fillStyle = "gray";
    ctx.fillRect(0 , 0 , gamewidth , gameheight);
};

function createfood()
{
    function randomfood(max , min)
    {
        let ranfood = Math.round((Math.random() * (max - min) + min) / unitsize) * unitsize;
        return ranfood 
    }
    foodx = randomfood(0 , gamewidth - unitsize);
    foody = randomfood(0 , gamewidth - unitsize);

};

function drawfood()
{ 
    ctx.fillStyle = "red";
    ctx.fillRect(foodx,foody,unitsize,unitsize)

};

function movethesnake()
{
    let head = {x:snake[0].x + xvol ,
         y:snake[0].y + yvol};

    snake.unshift(head);

    if(snake[0].x == foodx && snake[0].y == foody)
    {
        score++;
        scoretext.textContent = score;
        createfood();
    }
    else
    {
        snake.pop();
    }

};

function drawsnake()
{
    ctx.fillStyle = "lightgreen"
    ctx.strokeStyle = "black"
    snake.forEach(snakepart =>{
        ctx.fillRect(snakepart.x,snakepart.y,unitsize,unitsize)
        ctx.strokeRect(snakepart.x,snakepart.y,unitsize,unitsize)
    });

};

function changethedirction(e)
{
    let keypressed = e.keyCode;
    let left = 37;
    let up = 38;
    let right = 39;
    let down = 40;

    let goingup = (yvol == -unitsize);
    let goingdown = (yvol == unitsize);
    let goingright = (xvol == unitsize);
    let goingleft = (xvol == -unitsize);

    switch(true){
        case(keypressed == left && !goingright):
            xvol = -unitsize;
            yvol = 0;
            break;
        case(keypressed == up && !goingdown):
            xvol = 0;
            yvol = -unitsize;
            break;
        case(keypressed == right && !goingleft):
            xvol = unitsize;
            yvol = 0;
            break;
        case(keypressed == down && !goingup):
            xvol = 0;
            yvol = unitsize;
            break;
    }


};


function checkgameover()
{
    switch(true)
    {
        case(snake[0].x < 0):
        running = false;
        break;
        case(snake[0].x >= gamewidth ):
        running = false;
        break;
        case(snake[0].y < 0):
        running = false
        break;
        case (snake[0].y >= gameheight):
            running = false
            break;
    };
    for(let i = 1; i < snake.length; i++)
    {
        if(snake[i].x == snake[0].x && snake[i].y == snake[0].y)
        {
            running = false;
        }

    }

};


function displaygameover()
{
    ctx.font = "90px Arial";
    ctx.fillStyle = "black";
    ctx.textAlign = "center";
    ctx.fillText("Game Over!", 250, 250);

};

function restartthegame()
{
    score = 0;
    scoretext.textContent = score;
    xvol = unitsize;
    yvol = 0;
    snake = [
        {x:unitsize * 4 , y:0},
        {x:unitsize * 3 , y:0},
        {x:unitsize * 2 , y:0},
        {x:unitsize , y:0},
        {x:0 , y:0}
    ];
    startgame();
};

// (;
