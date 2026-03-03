//sensor funcionamiento con respecto a la distancia.
void setup() {
  Serial.begin(9600);
  pinMode(13, OUTPUT);
}

void loop() {
  long tiempo = millis(); 
  int D_cm = distancia(20); 
  tiempo = millis() - tiempo; 

  Serial.print("Tiempo de lectura: ");
  Serial.print(tiempo); 
  Serial.print("ms  Distancia: ");
  Serial.print(D_cm);
  Serial.println("  cm");
  
  delay(100);
}

float distancia(int n)
{
  long suma = 0;
  for(int i = 0; i < n; i++)
  {
    suma = suma + analogRead(A0);
  }  

  float adc = suma / n;

  // 🔵 ECUACIÓN AJUSTADA
  float distancia_cm = 147000 * pow(adc, -1.47);

  return(distancia_cm);
}
