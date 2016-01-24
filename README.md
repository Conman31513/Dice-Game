# Dice-Game
Made in JavaScript

function start(){
    
//Variables to be used in the while loop, and after the game.

    var win = 0;
    var loss = 0;
    var play = true;
    var cash = null;
    var roll = null;
    var bet = null;
    var guess = null;
    
//Initial intro to game.

    alert("Let's play a game! It's a betting game, if you don't want to play enter your bet as zero.");
    println("Let's play a game! It's a betting game, if you don't want to play enter your bet as zero.");
    alert("It's pretty basic. You enter a bet on a dice roll of 1-12 and you win or lose depending on range of numbers.");
    println("It's pretty basic. You enter a bet on a dice roll of 1-12 and you win or lose depending on range of numbers.");
    alert("Bring big bucks! You can lose in a heart beat!");
    println("Bring big bucks! You can lose in a heart beat!");
    
//Start of the game, the alerts and println's are for a more fulfilling dialogue. 

    cash = readInt("How much money did you bring? ");
    var mon = cash;
        
    while(true){
        if(mon <= 0){
            alert("You're broke pal. See ya sucker.");
            println("You're broke pal. See ya sucker.");
            break;
        }
        bet = readInt("How much money are willing you bet? ("+mon+")");
        if(bet == 0){
            alert("Have a nice day!");
            println("Have a nice day!");
            break;
        }
        while(bet > mon){
            bet = readInt("You don't have that much money try again. ("+mon+")");
        }
        guess = readInt("Pick a number 1-12. ");
        while(guess > 12){
            guess = readInt("The dice only has 12 sides you idiot. Try again.");
        }
        roll = Randomizer.nextInt(1,12);
        alert("The roll was "+roll+".");
        println("The roll was "+roll+".");
        if(guess == roll){
            alert("Wow! You guessed exact! You win 10 times your bet! ("+bet*10+")");
            println("Wow! You guessed exact! You win 10 times your bet! ("+bet*10+")");
            mon += (bet*10);
            win += bet*10;
            alert("You now have "+mon+".");
            println("You now have "+mon+".");
        }else if(guess == (roll-1) || guess == (roll+1)){
            alert("One off! You lose a quarter of your bet. ("+bet/4+")");
            println("One off! You lose a quarter of your bet. ("+bet/4+")");
            mon -= (bet/4);
            loss += bet/4;
            alert("You now have "+mon+" left.");
            println("You now have "+mon+" left.");
        }else if(guess == (roll-2) || guess == (roll+2)){
            alert("Two off! You lose half your bet. ("+bet/2+")");
            println("Two off! You lose half your bet. ("+bet/2+")");
            mon -= (bet/2);
            loss += bet/2;
            alert("You now have "+mon+" left.");
            println("You now have "+mon+" left.");
        }else if(guess == (roll-3) || guess == (roll+3)){
            alert("You're 3 off. You've lost your bet.");
            println("You're 3 off. You've lost your bet.");
            mon -= (bet);
            loss += bet;
            alert("You now have "+mon+" left.");
            println("You now have "+mon+" left.");
        }else{
            alert("You're more than 3 off. You'e lost your bet times 2.");
            println("You're more than 3 off. You'e lost your bet times 2.");
            mon -= (bet*2);
            loss += bet*2;
            alert("You now have "+mon+" left.");
            println("You now have "+mon+" left.");
        }
    }
    var even = win - loss;
        alert("Through out the game you won "+win+" dollars and lost "+loss+" dollars.");
        println("Through out the game you won "+win+" dollars and lost "+loss+" dollars.");
        if (even < 0){
            alert("Which means you lost more money than you gained.");
            println("Which means you lost more money than you gained.");
        }else{
            alert("Which means you broke even.");
            println("Which means you broke even.");
        }
}
