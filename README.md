obstacle-avoiding-bot
=====================

Basic bot based on arduino that aoids obstacles using IR sensor.

int IR = 3;
int left1 = 10;
int left2 = 9;
int right1 = 5;
int right2 = 6;
int leftir;
int rightir;
int rightspd;
int leftspd;
int turn;
void readsensor();
void motorspeed();
void setup()
{
  Serial.begin(9600);
  pinMode(LeftIR,INPUT);
  pinMode(RightIR,INPUT);
  pinMode(left1,OUTPUT);
  pinMode(left2,OUTPUT);
  pinMode(right1,OUTPUT);
  pinMode(right2,OUTPUT); 
  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
  digitalWrite(13,HIGH);
}

void loop()
{
  readsensor();
  motorspeed();
}

// FUNCTIONS //

void readsensor()
{
  IR = digitalRead(LeftIR);
  if(leftir > 0)
  {
    turn = 0;  
  }
  else
  {
    turn = 1;
  }
}
void motorspeed()
{
  if(turn == 1)
  {
  analogWrite(right1, 120);
  digitalWrite(right2, LOW);
  analogWrite(left1, 120);
  digitalWrite(left2, LOW);
  }
  else if(turn == 0)
  {
  analogWrite(right1, LOW);
  digitalWrite(right2, LOW);
  analogWrite(left1, 160);
  digitalWrite(left2, LOW);
  }
}
