# Aanlog-Clock

//HTML

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="analogclock.css">
    <title>Analog Clock</title>
</head>
<body>
    <div class="clock">
        <div class="hand hour-hand" data-hour-hand></div>
        <div class="hand min-hand" data-min-hand></div>
        <div class="hand second-hand" data-second-hand></div>
        <div class="number number1">1</div>
        <div class="number number2">2</div>
        <div class="number number3">3</div>
        <div class="number number4">4</div>
        <div class="number number5">5</div>
        <div class="number number6">9</div>
        <div class="number number7">7</div>
        <div class="number number8">8</div>
        <div class="number number9">9</div>
        <div class="number number10">10</div>
        <div class="number number11">11</div>
        <div class="number number12">12</div>
    
    </div>

    <script>
        setInterval(setClock,1000);
        const hourHand=document.querySelector(`[data-hour-hand]`)
        const minHand=document.querySelector(`[data-min-hand]`)
        const secondHand=document.querySelector(`[data-second-hand]`)
        const currentDate= newDate();
        console.log("hello");
        function setClock(){
            const currentDate= new Date();
            const secondRatio=currentDate.getSeconds()/60;
            console.log("currentDate");
            const minuteRatio=(secondRatio+currentDate.getMinutes())/60;
            const hourRatio=(minuteRatio+currentDate.getHours())/12;

            setRotation(secondHand, secondRatio);
            setRotation(minHand, minuteRatio);
            setRotation(hourHand, hourRatio);

        }
        function setRotation(element,rotationRatio){
            element.style.setProperty('--rotation',rotationRatio * 360);
        }
        setClock()

    </script>
    
</body>
</html>

//CSS


*{
    margin: 0;
    padding: 0;
    font-family: sans-serif;
    box-sizing: border-box;
}
body{
    background-color: rgba(79, 85, 126, 0.797);
    
    overflow: hidden;
   justify-content: center;
   text-align: center;
   min-height: 100vh;
}
.clock{
    width: 300px;
    height: 300px;
    background-color: rgba(215, 218, 239, 0.8);
    border-radius: 50%;
    border: 2px solid black;
    position: relative;
    margin-left: auto;
    margin-right: auto;
    margin-top:200px;
}
.clock::after{
    content: '';
    position: absolute;
    width:20px;
    background-color: black;
    z-index: 12;
    height: 20px;
    bottom: 46%;
    left: 50%;
    border-radius: 50%;
    transform: translate(-50%);
}
.clock .number{
    --rotation:0;
    position: absolute;
    width: 100%;
    height: 100%;
    text-align: center;
    transform: rotate(var(--rotation));
    font-size: 1.5rem;
}
.clock .number1{--rotation: 30deg;}
.clock .number2{--rotation: 60deg;}
.clock .number3{--rotation: 90deg;}
.clock .number4{--rotation: 120deg;}
.clock .number5{--rotation: 150deg;}
.clock .number6{--rotation: 180deg;}
.clock .number7{--rotation: 210deg;}
.clock .number8{--rotation: 240deg;}
.clock .number9{--rotation: 270deg;}
.clock .number10{--rotation: 300deg;}
.clock .number11{--rotation: 330deg;}

.clock .hand{
    --rotation:0;
    position: absolute;
    width:10px;
    background-color: black;
    left: 50%;
    bottom: 50%;
    height: 40%;
    border-top-right-radius:10px ;
    border-top-left-radius: 10px;
    border-top-color: #fff;
    transform-origin: bottom;
    z-index: 5;
    transform: translateX(-50%) rotate(calc(var(--rotation)*1deg));
}
.clock .hour-hand{
    width:10px ;
    height: 30%;
    background-color: purple;
}
.clock .min-hand{
    width:7px ;
    height: 35%;
    background-color: green;
}
.clock .second-hand{
    width:5px ;
    height: 40%;
    background-color: red;
}
