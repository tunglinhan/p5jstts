<template>
  <div class="container">
    <div class="p5Canvas"></div>
  </div>
</template>

<script>
import P5 from 'p5';

export default {
  data() {
    return {
      p5Canvas: null,
    }
  },
  created() {
    const sketch = p5 => {
        var x;
        var y;
        var r = 50;
        var mi;
        var mj;

        

        // let w = window.innerWidth;
        // let h = window.innerHeight;

        p5.setup = () => {
            p5.createCanvas(400, 400);
            x = 50;
            y = 50;
            p5.background(100);
            for(var i=0;i<7;i++){
              for(var j=0;j<7;j++){
                p5.fill(210);
                p5.circle(x+i*r, y+j*r, r);  
              }
            }
  
        };

        p5.draw = () => {
            if(p5.mouseIsPressed){
              mi=Math.round((p5.mouseX-50)/r);
              mj=Math.round((p5.mouseY-50)/r);
              print(mi, mj);
              for(var i=0;i<7;i++){
                for(var j=0;j<7;j++){
      
                  if(i===mi && j===mj){
                    p5.fill(255, 204, 0);
                    p5.circle(x+i*r, y+j*r, r);
                  }
                }
              }
            }
        };

    }

    this.p5Canvas = new P5(sketch, 'p5Canvas');
  },
  unmounted () {
    this.p5Canvas = null;
  },
}
</script>

<style>
#p5Canvas {
  width: 100vw;
  position: relative;
}

main {
  margin: 0 auto;
  width: 90vw;
}
</style>