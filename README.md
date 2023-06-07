# Project_p5js
The p5js training project

# The Basics of Materials Science 

This project presents 2 topics. The first is the state of atoms and the crystal lattice when the temperature changes. The second is the visualization of the crystallization process with the formation and growth of alloy grains. 

Fullscreen

https://editor.p5js.org/iostwestcoast/full/x0j40FRru

Edit

https://editor.p5js.org/iostwestcoast/sketches/x0j40FRru

![Анимация](https://github.com/iostwestcoast/Project_p5js/assets/114690482/b1c4a2b7-b862-4509-b9e9-5d66437f831c)
```JS
let img;
let angle = 0;
let slider;
let offset = 100;
let i = 0;

function setup() {
  
  createCanvas(windowWidth, windowHeight);

  slider = createSlider(0, 10, 10);
  slider.position(80, 90);

  img = loadImage("1.png");
  s0 = loadImage("s0.png");
  s1 = loadImage("s1.png");
  s2 = loadImage("s2.png");
  s3 = loadImage("s3.png");
  s4 = loadImage("s4.png");
  s5 = loadImage("s5.png");
  
  button = createButton('home page');
  button.position(10, 200);
  button.mousePressed(home);
  
  button = createButton('atoms state ON');
  button.position(10, 250);
  button.mousePressed(loop);
  
  button = createButton('atoms state OFF');
  button.position(10, 280);
  button.mousePressed(noLoop);
  
  button = createButton('structure ON');
  button.position(10, 330);
  button.mousePressed(structure);
  
  button5 = createButton('scheme');
  button5.position(10, 360);
  button5.mousePressed(scheme);
  
  noLoop();
}

function draw() {
  
    let s = slider.value();
    background(0 + s*25, 200, 255 - s*25);
    textSize(25);
    text("State of atoms in a substance when the temperature changes", 30, 40);
    text("Сhange temperature:", 30, 80);
    translate(width/3, height/3);
  
    for (let x = 0; x < 3; x++) {
      for (let y = 0; y < 3; y++) {
      
        push()
        translate(x*offset, y*offset);
      
        if(s < 3 && x < 2){
          push()
          strokeWeight(7);
          line (0, 0, offset, 0);
          pop()
        }
        if(s < 3 && y < 2){
          push()
          strokeWeight(7);
          line (0, 0, 0, offset);
          pop()
        }
      
        fill(0 + s*25, 0, 255 - s*25);
        ellipse(cos(angle)*s*random(0, 5), sin(angle)*s*random(0, 5), 50);
      pop()
    }
  }
  angle += 0.05*s;
}

function home(){
  createCanvas(windowWidth, windowHeight)
  //translate(0, 0);
  background(255);
  textSize(30);
  text("Demo course", windowWidth/3, 60)
  text("THE BASICS OF MATERIALS SCIENCE", windowWidth/10, 160); 
  image(img, 50, 200);
}

function structure(){
  createCanvas(windowWidth, windowHeight)
  background(174, 255, 115);
  textSize(30);
  text("Scheme of forming the alloy structure during crystallization", windowWidth/10, 160); 
}

function scheme(){
    let scheme1 = [s0, s1, s2, s3, s4, s5];

    image(scheme1[i], 200, 200);
    i ++;
    if (i == 6){
      i = 0;
    }
    return i;
}
