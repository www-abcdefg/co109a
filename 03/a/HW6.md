# 第七週
* RAM8
    * [RAM8.hdl](https://github.com/www-abcdefg/co109a/tree/master/03/a/RAM8.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/03/a/RAM8.hdl

    /**
    * Memory of 8 registers, each 16 bit-wide. Out holds the value
    * stored at the memory location specified by address. If load==1, then 
    * the in value is loaded into the memory location specified by address 
    * (the loaded value will be emitted to out from the next time step onward).
    */

    CHIP RAM8 {
        IN in[16], load, address[3];
        OUT out[16];

        PARTS:
        // Put your code here:
        DMux8Way(in=load,sel=address,a=x0,b=x1,c=x2,d=x3,e=x4,f=x5,g=x6,h=x7);
        Register(in=in,load=x0,out=r0);
        Register(in=in,load=x1,out=r1);
        Register(in=in,load=x2,out=r2);
        Register(in=in,load=x3,out=r3);
        Register(in=in,load=x4,out=r4);
        Register(in=in,load=x5,out=r5);
        Register(in=in,load=x6,out=r6);
        Register(in=in,load=x7,out=r7);
        Mux8Way16(a=r0,b=r1,c=r2,d=r3,e=r4,f=r5,g=r6,h=r7,sel=address,out=out);
    }
    ```
* RAM64
    * [RAM64.hdl](https://github.com/www-abcdefg/co109a/blob/master/03/a/RAM64.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/03/a/RAM64.hdl

    /**
    * Memory of 64 registers, each 16 bit-wide. Out holds the value
    * stored at the memory location specified by address. If load==1, then 
    * the in value is loaded into the memory location specified by address 
    * (the loaded value will be emitted to out from the next time step onward).
    */

    CHIP RAM64 {
        IN in[16], load, address[6];
        OUT out[16];

        PARTS:
        // Put your code here:
        DMux8Way(in=load,sel=address[3..5],a=x0,b=x1,c=x2,d=x3,e=x4,f=x5,g=x6,h=x7);
        RAM8(in=in,load=x0,address=address[0..2],out=r0);
        RAM8(in=in,load=x1,address=address[0..2],out=r1);
        RAM8(in=in,load=x2,address=address[0..2],out=r2);
        RAM8(in=in,load=x3,address=address[0..2],out=r3);
        RAM8(in=in,load=x4,address=address[0..2],out=r4);
        RAM8(in=in,load=x5,address=address[0..2],out=r5);
        RAM8(in=in,load=x6,address=address[0..2],out=r6);
        RAM8(in=in,load=x7,address=address[0..2],out=r7);
        Mux8Way16(a=r0,b=r1,c=r2,d=r3,e=r4,f=r5,g=r6,h=r7,sel=address[3..5],out=out);
    }
    ```
* RAM512
    * [RAM512.hdl](https://github.com/www-abcdefg/co109a/tree/master/03/b/RAM512.hdl)
    ```
    // This file is part of the materials accompanying the book 
    // "The Elements of Computing Systems" by Nisan and Schocken, 
    // MIT Press. Book site: www.idc.ac.il/tecs
    // File name: projects/03/b/RAM512.hdl

    /**
    * Memory of 512 registers, each 16 bit-wide. Out holds the value
    * stored at the memory location specified by address. If load==1, then 
    * the in value is loaded into the memory location specified by address 
    * (the loaded value will be emitted to out from the next time step onward).
    */

    CHIP RAM512 {
        IN in[16], load, address[9];
        OUT out[16];

        PARTS:
        // Put your code here:
        DMux8Way(in=load,sel=address[6..8],a=x0,b=x1,c=x2,d=x3,e=x4,f=x5,g=x6,h=x7);
        RAM64(in=in,load=x0,address=address[0..5],out=r0);
        RAM64(in=in,load=x1,address=address[0..5],out=r1);
        RAM64(in=in,load=x2,address=address[0..5],out=r2);
        RAM64(in=in,load=x3,address=address[0..5],out=r3);
        RAM64(in=in,load=x4,address=address[0..5],out=r4);
        RAM64(in=in,load=x5,address=address[0..5],out=r5);
        RAM64(in=in,load=x6,address=address[0..5],out=r6);
        RAM64(in=in,load=x7,address=address[0..5],out=r7);
        Mux8Way16(a=r0,b=r1,c=r2,d=r3,e=r4,f=r5,g=r6,h=r7,sel=address[6..8],out=out);
    }
    ```
* RAM4K
    * [RAM4K.hdl](https://github.com/www-abcdefg/co109a/tree/master/03/b/RAM4K.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/03/b/RAM4K.hdl

    /**
    * Memory of 4K registers, each 16 bit-wide. Out holds the value
    * stored at the memory location specified by address. If load==1, then 
    * the in value is loaded into the memory location specified by address 
    * (the loaded value will be emitted to out from the next time step onward).
    */

    CHIP RAM4K {
        IN in[16], load, address[12];
        OUT out[16];

        PARTS:
        // Put your code here:
        DMux8Way(in=load,sel=address[9..11],a=x0,b=x1,c=x2,d=x3,e=x4,f=x5,g=x6,h=x7);
        RAM512(in=in,load=x0,address=address[0..8],out=r0);
        RAM512(in=in,load=x1,address=address[0..8],out=r1);
        RAM512(in=in,load=x2,address=address[0..8],out=r2);
        RAM512(in=in,load=x3,address=address[0..8],out=r3);
        RAM512(in=in,load=x4,address=address[0..8],out=r4);
        RAM512(in=in,load=x5,address=address[0..8],out=r5);
        RAM512(in=in,load=x6,address=address[0..8],out=r6);
        RAM512(in=in,load=x7,address=address[0..8],out=r7);
        Mux8Way16(a=r0,b=r1,c=r2,d=r3,e=r4,f=r5,g=r6,h=r7,sel=address[9..11],out=out);
    }
    ```
* RAM16K
    * [RAM16K.hdl](https://github.com/www-abcdefg/co109a/tree/master/03/b/RAM16K.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/03/b/RAM16K.hdl

    /**
    * Memory of 16K registers, each 16 bit-wide. Out holds the value
    * stored at the memory location specified by address. If load==1, then 
    * the in value is loaded into the memory location specified by address 
    * (the loaded value will be emitted to out from the next time step onward).
    */

    CHIP RAM16K {
        IN in[16], load, address[14];
        OUT out[16];

        PARTS:
        // Put your code here:
        DMux4Way(in=load,sel=address[12..13],a=x0,b=x1,c=x2,d=x3);
        RAM4K(in=in,load=x0,address=address[0..11],out=r0);
        RAM4K(in=in,load=x1,address=address[0..11],out=r1);
        RAM4K(in=in,load=x2,address=address[0..11],out=r2);
        RAM4K(in=in,load=x3,address=address[0..11],out=r3);
        Mux4Way16(a=r0,b=r1,c=r2,d=r3,sel=address[12..13],out=out);
    }
    ```
![picture](https://github.com/www-abcdefg/co109a/blob/master/03/a/HW6.jpg)
![picture1](https://github.com/www-abcdefg/co109a/blob/master/03/a/HW6-1.jpg)
![picture2](https://github.com/www-abcdefg/co109a/blob/master/03/a/HW6-2.jpg)
![picture3](https://github.com/www-abcdefg/co109a/blob/master/03/a/HW6-3.jpg)
![picture4](https://github.com/www-abcdefg/co109a/blob/master/03/a/HW6-4.jpg)