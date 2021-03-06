# 第一週
## code
* Not
    * [Not.hdl](https://github.com/www-abcdefg/co109a/blob/master/01/Not.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/01/Not.hdl

    /**
    * Not gate:
    * out = not in
    */

    CHIP Not {
        IN in;
        OUT out;

        PARTS:
        // Put your code here:
        Nand(a=in, b=in, out=out);
    }
    ```
* And
    * [And.hdl](https://github.com/www-abcdefg/co109a/blob/master/01/And.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/01/And.hdl

    /**
    * And gate: 
    * out = 1 if (a == 1 and b == 1)
    *       0 otherwise
    */

    CHIP And {
        IN a, b;
        OUT out;

        PARTS:
        // Put your code here:
        Nand(a=a, b=b, out= AnandB);
        Not(in=AnandB, out=out);
    }

    ```
* Or
    * [Or.hdl](https://github.com/www-abcdefg/co109a/blob/master/01/Or.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/01/Or.hdl

    /**
    * Or gate:
    * out = 1 if (a == 1 or b == 1)
    *       0 otherwise
    */

    CHIP Or {
        IN a, b;
        OUT out;

        PARTS:
        // Put your code here:
        Not(in=a, out=na);
        Not(in=b, out=nb);
        Nand(a=na, b=nb, out=out);
    }
    ```
* Xor
    * [Xor.hdl](https://github.com/www-abcdefg/co109a/blob/master/01/Xor.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/01/Xor.hdl

    /**
    * Exclusive-or gate:
    * out = not (a == b)
    */

    CHIP Xor {
        IN a, b;
        OUT out;

        PARTS:
        // Put your code here:
        Nand (a=a, b=b, out= AnandB);
        Or   (a=a, b=b, out= AorB);
        And  (a=AnandB, b=AorB, out=out);

    }
    ```
* Mux
    * [Mux.hdl](https://github.com/www-abcdefg/co109a/blob/master/01/Mux.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/01/Mux.hdl

    /** 
    * Multiplexor:
    * out = a if sel == 0
    *       b otherwise
    */

    CHIP Mux {
        IN a, b, sel;
        OUT out;

        PARTS:
        // Put your code here:
            Not(in=sel, out=nsel);
            And(a=a, b=nsel, out=x);
            And(a=b, b=sel, out=y);
            Or(a=x, b=y, out=out);
    }
    ```
* DMux
    * [DMux.hdl](https://github.com/www-abcdefg/co109a/blob/master/01/DMux.hdl)
    ```
    // This file is part of www.nand2tetris.org
    // and the book "The Elements of Computing Systems"
    // by Nisan and Schocken, MIT Press.
    // File name: projects/01/DMux.hdl

    /**
    * Demultiplexor:
    * {a, b} = {in, 0} if sel == 0
    *          {0, in} if sel == 1
    */

    CHIP DMux {
        IN in, sel;
        OUT a, b;

        PARTS:
        // Put your code here:
        Not(in=sel, out=nsel);
        And(a=in, b=nsel, out=a);
        And(a=in,  b=sel, out=b);

    }
    ```
    ## 圖片
    * ![picture](https://github.com/www-abcdefg/co109a/blob/master/01/hw1.jpg)
    * ![picture1](https://github.com/www-abcdefg/co109a/blob/master/01/hw1(1).jpg)