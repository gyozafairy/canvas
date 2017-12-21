setActiveCanvas("Canvas");
var eventList = [];
// eraser size: 15
onEvent("Eraser", "click", function(event) {
  EraserTool(15, 15);
});
//pen size biggest button: 12
onEvent("PenSizeBiggest", "click", function() {
  if (g==true) {
    PenTool(12, 12, color);
  } else {
    PenTool(12,12, "black");
  }
});
//pen size big button: 8
onEvent("PenSizeBig", "click", function() {
  ;if (g==true) {
    PenTool(8, 8, color);
  } else {
    PenTool(8,8, "black");
  }
});
// pen size medium button: 5
onEvent("PenSizeMedium", "click", function() {
  if (g==true) {
    PenTool(5, 5, color);
  } else {
    PenTool(5,5, "black");
  }
});
// pen size small button: 2
onEvent("PenSizeSmall", "click", function() {
  if (g==true) {
    PenTool(2, 2, color);
  } else {
    PenTool(2,2, "black");
  }
});
//click and drag function
var click = false;
function ClickandDrag(n) {
  onEvent(n, "mousedown", function(event) {
    click = true; //if mousedown:do action
  });
  onEvent(n, "mouseup", function(event) {
    click = false; // if mouseup: stop action
  });
}
//eraser tool function
function EraserTool(w,h) {
  setFillColor("#ffffff");
  setStrokeColor("#ffffff");
  ClickandDrag("Canvas");
  onEvent("Canvas", "mousemove", function(event) {
    if (click==true) {//mouse is able to erase rect when mouse is down and mouse is moving
      rect(event.offsetX, event.offsetY, w, h);
    }
    appendItem(eventList, event);
  });
}
// pen tool function 
function PenTool(w,h,c) {
setStrokeColor(c);
setFillColor(c);
ClickandDrag("Canvas");
onEvent("Canvas", "mousemove", function(event) {
   if ( click==true) { //mouse is able to draw rect when mouse is down and mouse is moving
      rect(event.offsetX, event.offsetY, w, h);
  
    }
   appendItem(eventList, event);
   
  });
}
//clear canvas
onEvent("ClearBtn", "click", function(event) {
  eventList = [];
  clearCanvas();
});
// color input
var g = false; //if g is false draw black
var color = getText("TextInput");
onEvent("ColorBtn", "click", function(event) {
  g = true; //if g is true allow to draw pen in Inputed color
  color = getText("TextInput");
  console.log(color);
});
//Fill Canvas with inputed color
onEvent("BucketTool", "click", function(event) {
  setFillColor(color);
  setStrokeColor(color);
  for (var i = 0; i < 1000; i++) {
    circle(randomNumber(0, 400), randomNumber(0, 450), 30);
  }
});
