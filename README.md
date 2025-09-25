# bouncing-
MovingShape shape;

void setup() {
  size(600, 400);
  ellipseMode(RADIUS);
  shape = new MovingShape(100, height/2, 30, 4); // x, y, radius, speed
}

void draw() {
  background(200, 220, 255);
  shape.update();
  shape.display();
}

class MovingShape {
  float x, y;
  float r;
  float speed;

  MovingShape(float x_, float y_, float r_, float speed_) {
    x = x_;
    y = y_;
    r = r_;
    speed = speed_;
  }

  void update() {
    x += speed;

   
    if (x > width - r || x < r) {
      speed = -speed;
    }
  }

  void display() {
    fill(255, 400, 10);
    ellipse(x, y, r, r);
  }
}
