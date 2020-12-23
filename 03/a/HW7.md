# 第八週
* PC
    * [PC.hdl](https://github.com/www-abcdefg/co109a/tree/master/03/a/PC.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/03/a/PC.hdl

    /**
    * A 16-bit counter with load and reset control bits.
    * if      (reset[t] == 1) out[t+1] = 0
    * else if (load[t] == 1)  out[t+1] = in[t]
    * else if (inc[t] == 1)   out[t+1] = out[t] + 1  (integer addition)
    * else                    out[t+1] = out[t]
    */

    CHIP PC {
        IN in[16],load,inc,reset;
        OUT out[16];

        PARTS:
        // Put your code here:
        Inc16(in=PC,out=InPC);
        Mux16(a=PC,b=InPC,sel=inc,out=x);
        Mux16(a=x,b=in,sel=load,out=y);
        Mux16(a=y,b=false,sel=reset,out=z);
        Register(in=z,load=true,out=PC,out=out);
    }
    ```
![picture](https://github.com/www-abcdefg/co109a/blob/master/03/a/HW7.jpg)