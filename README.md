void setup(){
  size(500, 500);
}

float x = 25, y = 25;
float x1 = 50, y1 = 50;
float x2 = 1, y2 = 1;
float scaleFactor = 1;
float maxScaleFactor = 4;
boolean growing = true;

void draw(){
  background(0);
  pattern();
  
  if (growing) {
    scaleFactor += 0.01;
    if (scaleFactor >= maxScaleFactor) {
      growing = false;
    }
  } else {
    scaleFactor -= 0.01;
    if (scaleFactor <= 1) {
      growing = true;
    }
  }
}

void pattern(){
  for (int j = 0; j < height; j += width / 10){
    for (int i = 0; i <= width; i += width / 10){
      noFill();
      stroke(146,234,147);
      ellipse(x, y, x1 * x2 * scaleFactor, y1 * y2 * scaleFactor);
      stroke(46,164,247);
      rect(x - 25, y - 25, x1 * x2 * scaleFactor, y1 * y2 * scaleFactor);
      stroke(160,23,247);
      ellipse(x + 25, y + 25, (x1 / 2) * x2 * scaleFactor, (y1 / 2) * y2 * scaleFactor);
      x += 50;
    }
    x = 25;
    y += 50;
  }
  y = 25;
}
