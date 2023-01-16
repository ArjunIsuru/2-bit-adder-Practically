# 2-bit-adder-Practically


A1  A0   B1  B0   X2  X1  X0
0     0     0     0      0     0     0
0     0     0     1      0     0     1
0     0     1     0      0     1     0
0     0     1     1      0     1     1
0     1     0     0      0     0     1
0     1     0     1      0     1     0
0     1     1     0      0     1     1
0     1     1     1      1     0     0
1     0     0     0      0     1     0
1     0     0     1      0     1     1
1     0     1     0      1     0     0
1     0     1     1      1     0     1
1     1     0     0      0     1     1
1     1     0     1      1     0     0
1     1     1     0      1     0     1
1     1     1     1      1     1     0


X0 =      A1'.A0'.B0   +    A1'.A0.B0'    +     A1.A0'.B0   +    A1.A0.B0'    

X0 = A1'.(A0  xor  B0)    +    A1.(A0   xor   B0)   =  A0   xor   B0


X1  =  A1'.A0'.B1    +     A1.A0'.B1'   +   A1'.A0. ( B1   xor   B0)   +   A1.A0.(B1   xor   B0)'

X1 =  A0.( A1   xor   B1   xor   B0)   +   A0'.(A1   xor   B1)


X2 =  A1.A0'.B1   +    A1.A0.B1   +  A0.B0.(A1  xor  B1)  

X2 =  A1.B1   +    A0.B0.(A1  xor  B1)

*Decoder with Arduino*

void setup()
{
  for (int i = 2;  i <=8;  i++){
    pinMode(i,OUTPUT);
  }
  for (int j = 10;  j <=12;  j++){
    pinMode(j,INPUT);
  }
}

void loop()
{
  bool A = digitalRead(10);
  bool B = digitalRead(11);
  bool C = digitalRead(12);
  
  bool a = ((!(A or C)) or (A and B) or (C and (A xor B)));
  bool b = ((!(A or C)) or (B and C) or (A and (!(B or C))));
  bool c = (((!A) and (!(B xor C))) or A);
  bool d = (!(A xor B xor C)) or ((!A)and B and (!C));
  bool e = (!(A or B)) or ( B and (!C));
  bool f = (((!B) or (A and B and (!C))));
  bool g = ((A xor B) or (A and B) and (!C));
  
  if (a == 1){
    digitalWrite(2,HIGH);
  }
  else{
    digitalWrite(2,LOW);
  }
  
  if (b == 1){
    digitalWrite(3,HIGH);
  }
  else{
    digitalWrite(3,LOW);
  }
   
  if (c == 1){
    digitalWrite(4,HIGH);
  }
  else{
    digitalWrite(4,LOW);
  }   
  
  if (d == 1){
    digitalWrite(5,HIGH);
  }
  else{
    digitalWrite(5,LOW);
  }   
  
   if (e == 1){
    digitalWrite(6,HIGH);
  }
  else{
    digitalWrite(6,LOW);
  }     
            
  
  if (f == 1){
    digitalWrite(7,HIGH);
  }
  else{
    digitalWrite(7,LOW);
  }               
     
  if (g == 1){
    digitalWrite(8,HIGH);
  }
  else{
    digitalWrite(8,LOW);
  }                    
}

*Arjun ( Isuru ) 🍁✨️*
