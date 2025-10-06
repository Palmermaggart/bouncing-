MovingShape[] shapes; 
int numShapes = 5;    

void setup() {
  size(600, 400);

  shapes = new MovingShape[numShapes];
  for (int i = 0; i < numShapes; i++) {
    float x = random(50, width - 50);
    float y = random(50, height - 50);
    float size = random(30, 60);  
    float speed = random(2, 5);
    shapes[i] = new MovingShape(x, y, size, speed);
  }
}

void draw() {
  background(200, 220, 255);

 
  for (MovingShape shape : shapes) {
    shape.update();
    shape.drawShape();
  }
}

class MovingShape {
  float x, y;    
  float size;    
  float speed;   
  
  MovingShape(float x_, float y_, float size_, float speed_) {
    x = x_;
    y = y_;
    size = size_;
    speed = speed_;
  }

  void update() {
    x += speed;
    if (x > width - size/2 || x < size/2) {
      speed = -speed;
    }
  }

  void drawShape() {
    fill(100, 150, 255, 180);
    noStroke();
    ellipseMode(CENTER);
    ellipse(x, y, size, size);  
  }
}


