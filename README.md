project video link: https://youtu.be/Nk-ciOQkMc8

project Mimic link: https://mimicproject.com/code/050e25bd-6986-5e0a-5eaa-71284dbacfb5



# Talking light by dancing Morse Code

# see all details of project description link: https://www.notion.so/Talking-light-by-dancing-Morse-Code-7b4c34473b3b413a91d1588d9f30eddd

### What it is

I made the project named ‘Talking light by dancing Morse Code’. I use the Morse Code sound to interact with my graphics.

### Why I make it

I watched a funny video about Morse Code; it talked about the spies communicated with other spies through Morse Code. Some prisoners of war using Morse Code to call for help. Even prisoners of war say ‘Fuck Hitler’ through Morse code secretly.

I think it is quite funny and it even makes me a little fascinated. I began to wonder if I could apply this inspiration to my creative coding project.

First, programming languages are unknown code to many people who haven’t learned. Morse code is a kind of unknown code too if the listener has not trained ever. The most exciting thing is Morse Code have a sort of connection with binary.

### How I make it

At first, I thought that how to make Morse Code looks funny. Just use the sound is not enough and seems tasteless. After research, I found that sailors usually use strong signal lights to communicate with other shippings in terrible weather. Fantastic useful and this is also an application of Morse Code. That’s so cool, twinkle twinkle light will be an amazing visualisation.

The project contains knowledge Three.js, shader and sound visualisation from our term 1. After learning shader, I am surprised by its power, and I created my graphics by glslsandbox. The graphics which I called it talking light because it interacts with my sound and the secret information I hidden in my project. I tried different shapes of my ‘talking light’. Eventually, I choose strong colours. It makes me more feel to receive information from the mystery sea in one of the terrible weather.

I learned many fantastic works from [glslsandbox](http://glslsandbox.com/). This is my first trying: [http://glslsandbox.com/e#70526.0](http://glslsandbox.com/e#70526.0).

After different trying I got my final shader code: http://glslsandbox.com/e#70636.0

```
////This is the precision. This must be set first
precision mediump float; //set the precision
////grab the uniform from the management code (in JS)
    ////These uniforms need to be set up in your management code
    uniform vec2 resolution; 
    uniform vec2 mouse;
    uniform float time;
    
    ////This i s the main loop
    void main() {
    
    ////Takes width and height, divide it by two, give to the pos vector
    ////Draw in the middle
    vec2 pos = vec2(resolution.x/2.0, resolution.y/2.0);
    
    //vec2 pos = vec2(resolution.x/3.*mouse.x, resolution.y/2.*mouse.y);
    //vec2 pos = resolution.xy/2.0;
	////colour depends on the current fragment positon and the centre of the screen
    ////Geth the distance from the centre to the current fragment, then use it to determine a colour 
    float colour = distance(gl_FragCoord.xy, pos);
    colour *= 0.009; ////This scales the distance field a bit
    
    
    float changingSize = abs(sin(time/1.0))/0.3;
    
    
    ////Colorful background
    //vec4 graidentColor = vec4(abs(sin(time)), 0.0, abs(cos(time)), 1.0)*2.; 
    
    ////White background
    vec4 gradientColor = vec4(abs(sin(time))*0.9, abs(cos(time))*1.4, abs(cos(time)), 1.0)*0.8; 

    vec4 breathingCircle = vec4(vec3(colour), 1.0)*changingSize;
    gl_FragColor = gradientColor*breathingCircle;
    
    //gl_FragColor = breathingCircle;

    
    ////Below is for squared distance
    ////Calculate the difference between the centre of our circle to the current pixel location
    //vec2 pos = gl_FragCoord.xy-resolution/2.;
    
    ////dot product tells the intersection between the two vectors
    ////Calculate the magnitudes
    //float dist_squared = dot(pos, pos)*0.0001;
    
	//gl_FragColor = vec4(vec3(dist_squared), 1.0);
    }
```

Then through the functions which we learnt in term 1, I combined the sound and graphics successfully.

```
    var wave = 0;
    var counter = 0;
	var maxiJs = maximilian();
    var audio = new maxiJs.maxiAudio();      
  	var myOsc1 = new maxiJs.maxiOsc();   

    let morse = new maxiJs.maxiSample();
  
    let myClock = new maxiJs.maxiClock();

    audio.init();

    audio.loadSample('morse.wav', morse);  

    audio.play = function() {
      
    myClock.ticker();

    s1 = morse.play()*myOsc1.sinebuf(21)*2.5;

    wave = (s1)*1.3;
        counter++;
return wave;
};
</script>

```


/*

-.-.  ---  -..  ..  -.  --.   ..  ...   -  ---  ..-  --.  ....  --..--   -...  ..-  -   --  ..  --  ..   .--  ..  .-..  .-..   -.-  .  .  .--.   -  .-.  -.--  ..  -.  --.  .-.-.-

‘Coding is tough, but Mimi will keep trying.’

*/



### Reference materials:

https://thebookofshaders.com/

https://www.youtube.com/watch?v=HY_OIwideLg&ab_channel=D%21NG

https://www.youtube.com/watch?v=WOt83AouoGU

https://www.youtube.com/watch?v=aniLPEyp9SA&ab_channel=DenizOK




