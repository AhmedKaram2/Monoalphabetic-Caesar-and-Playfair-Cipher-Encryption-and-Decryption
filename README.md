# Monoalphabetic-Caesar-and-Playfair-Cipher-Encryption-and-Decryption
Monoalphabetic, Caesar and Playfair Cipher Encryption and Decryption in Java GUI

Methods of Monoalphabetic, Caesar and Playfair Cipher Encryption and Decryption

![alt tag] (http://s30.postimg.org/45jt4qr01/Screen_Shot_2016_04_03_at_1_27_36_AM.png)

             private static char MonoAlphabeticEncrypt(char a) {
            int pos = (int)a;
            pos = (pos % 91)- 65;
            a = key.charAt(pos);
            return a;
        }
    private static char MonoAlphabeticdecrypt(char a) {
            int ascii = 0;
            for(int i=0;i< key.length(); i++){
                if(key.charAt(i) == a)
                    ascii = i + 65;
            }
            return (char)ascii;
        } 
 
![alt tag] (http://s22.postimg.org/6v1kl4y0x/Screen_Shot_2016_04_03_at_1_27_10_AM.png)

    private static char Caesarencrypt(char a, int i, int f) {
        int ascii = (int)a;
        ascii = ((ascii + f ) % 90);
        if(ascii < 65){//adjustment for characters bigger than Z
            ascii = ascii + 65;
        }
            //moving using 3 characters
        a = (char) ascii;
        return a;
    }
    private static char Caesardecrypt(char a, int i, int f) {
        int ascii = (int)a;
        ascii = ((ascii - f ) % 90);
        if(ascii < 65){//adjustment for characters smaller than a
            ascii = ascii + 25;
        }          
        //moving using 3 characters
        a = (char) ascii;
        return a;
    }
 

 ![alt tag] (http://s17.postimg.org/hyw9hd2y7/Screen_Shot_2016_04_03_at_1_27_55_AM.png)
 

        private static String PlayFairencrypt(char c1, char c2) {
        int[] posa = new int[2];
        int[] posb = new int[2];
        String frag = "";
        posa = search(c1);
        posb = search(c2);
        if(posa[0] == posb[0]){//same row
            c1 = keymatPlayfair[posa[0]][(posa[1]+1)%5];
            c2 = keymatPlayfair[posb[0]][(posb[1]+1)%5];
            frag = (""+c1+c2+"");
        }
        else if(posa[1] == posb[1]){ //same column
            c1 = keymatPlayfair[(posa[0]+1)%5][posa[1]];
            c2 = keymatPlayfair[(posb[0]+1)%5][posb[1]];
            frag = (""+c1+c2+"");
        }
        else{
            c1 = keymatPlayfair[posb[0]][posa[1]];
            c2 = keymatPlayfair[posa[0]][posb[1]];
            frag = (""+c1+c2+"");
        }
        return frag;
    }
    private static String PlayFairdecrypt(char c1, char c2) {
        int[] posa = new int[2];
        int[] posb = new int[2];
        String frag = "";
        posa = search(c1);
        posb = search(c2);
        if(posa[0] == posb[0]){//same row
            c1 = keymatPlayfair[posa[0]][(posa[1]-1)%5];
            c2 = keymatPlayfair[posb[0]][(posb[1]-1)%5];
            frag = (""+c1+c2+"");
        }
        else if(posa[1] == posb[1]){ //same column
            c1 = keymatPlayfair[(posa[0]-1)%5][posa[1]];
            c2 = keymatPlayfair[(posb[0]-1)%5][posb[1]];
            frag = (""+c1+c2+"");
        }
        else{
            c1 = keymatPlayfair[posb[0]][posa[1]];
            c2 = keymatPlayfair[posa[0]][posb[1]];
            frag = (""+c1+c2+"");
        }
        return frag;
    }
    private static int[] search(char c) {
        int i,j;
        int[] pos = new int[2];
        for (i = 0; i < 5; i++) {
            for (j = 0; j < 5; j++) {
                if (keymatPlayfair[i][j] == c){
                    pos[0] = i;
                    pos[1] = j;
                    break;
                }
            }
        }
        return pos;
    }
