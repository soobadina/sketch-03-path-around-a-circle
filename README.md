# sketch-03-path-around-a-circle
Explored the circular formular around a circle


const canvasSketch = require('canvas-sketch');
const maht = require("canvas-sketch-util/math");

const settings = {
  dimensions: [ 1080, 1080 ]
};

const sketch = () => {
  return ({ context, width, height }) => {
    context.fillStyle = 'black';
    context.fillRect(0, 0, width, height);

    const degToRad = (degrees) => {
      return degrees / 180 * Math.PI;
    };

    const randomRange = (min, max) => {
      return Math.random() * (max - min) + min;
    };


    const cx = width/2;
    const cy = height/2;
    
    const diameter = 1;

    let x, y;
    
    const num = 12;
    const radius = width * 0.2;

 

    for (let j = 0; j < 1000; j++){
      for (let i = 0; i < num; i++) {
        const slice = degToRad(360 / num);
        const angle = (slice * i);
  
  
        x = cx + (radius + j + randomRange(9,10)) * Math.sin((j * 0.23) + angle);
        y = cy + (radius + j + randomRange(9,10)) * Math.cos((j * 0.23) + angle);
  
  
        context.save();
        context.beginPath();
        context.translate(x, y);
        //context.rotate(-angle);
        context.arc (0, 0, diameter + Math.cos(j), 0, degToRad(360));
        context.fillStyle = "white";
        context.fill();
        context.restore();


        // context.save();
        // context.beginPath();
        // context.arc(0,0, diameter, 0, degToRad(360));
        // context.fill();
        // context.restore();
      }
    }

  };
};

canvasSketch(sketch, settings);

