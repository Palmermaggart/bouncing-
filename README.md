MovingShape[] shapes; 
int maxShapes = 10;   
int shapeCount = 0;   

void setup() {
  size(600, 400);
  shapes = new MovingShape[maxShapes]; 
}

void draw() {
  background(200, 220, 255);

  
  for (int i = 0; i < shapeCount; i++) {
    shapes[i].update();
    shapes[i].drawShape();
  }
}

void mousePressed() {
  
  if (shapeCount < maxShapes) {
    shapes[shapeCount] = new MovingShape(mouseX, mouseY);
    shapeCount++;
  } else {
    
    for (int i = 1; i < maxShapes; i++) {
      shapes[i-1] = shapes[i];
    }
    
    shapes[maxShapes-1] = new MovingShape(mouseX, mouseY);
  }
}

class MovingShape {
  float x, y;
  float size;
  float speedX;
  float speedY;

  
  MovingShape(float startX, float startY) {
    x = startX;
    y = startY;
    size = random(20, 50);
    speedX = random(-2, 2);
    speedY = random(-2, 2);
  }

  void update() {
    x += speedX;
    y += speedY;

    
   
  }

  void drawShape() {
    fill(100, 150, 255);
    ellipse(x, y, size, size);
  }
}

