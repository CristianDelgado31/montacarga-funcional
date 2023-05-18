# Documentación montacarga funcional

![portada](https://i.gyazo.com/dc9a24c2f549c103147ae4d401b4fedb.png "portada")
## Integrantes
* Delgado Cristian



## Proyecto: Montacarga funcional
![montacarga](https://i.gyazo.com/61a03131984bb5e6dc862351ecb67425.png "montacarga funcional")

## Diagrama esquematico del circuito
![diagrama esquematico](https://i.gyazo.com/b0f6a23c64aab6f55a764a66272290d5.png "montacarga funcional")

## Descripción
Montacarga funcional cuyo objetivo es mostrar mediante un display 7 segmentos el piso donde esta ubicado y prende un LED de un color en especifico dependiendo si está en movimiento o no. Tiene un pulsador de emergencia quitandole la funcionalidad de subir y bajar de los pulsadores correspondientes.

## Función principal

Su función principal mostrar el piso donde estan ubicados los usuarios.  

El codigo esta conformado por LEDS, un display 7 segmentos, contadores, banderas, funciones, condicionales y uso de switch.
Muestra de como se conforma el codigo:
```c++
//Variables y puertos usados
int ContadorPiso9 = 0;
int FlagPlantaBaja = 0;
int contador = 0;
int contadorEmergencia = 0;

#define LED_MOVIMIENTO 13
#define LED_PAUSA 10

#define A 7
#define B 8
#define C 6
#define D 5
#define E A1
#define F A2
#define G A3

pinMode(9,INPUT_PULLUP);
pinMode(11,INPUT_PULLUP);
pinMode(12,INPUT_PULLUP);

//funciones
void Mostrar7Segmentos(int letra1,int letra2,int letra3,int letra4,int letra5,int letra6,int letra7, int tiempo)
{
  	digitalWrite(LED_MOVIMIENTO, HIGH);
	delay(tiempo);  
    digitalWrite(letra1, HIGH);
    digitalWrite(letra2, HIGH);
    digitalWrite(letra3, HIGH);
    digitalWrite(letra4, HIGH);
    digitalWrite(letra5, HIGH);
    digitalWrite(letra6, HIGH);
    digitalWrite(letra7, HIGH);
}
void Apagar7Segmentos(int letra1,int letra2,int letra3,int letra4,int letra5,int letra6,int letra7)
{
 	digitalWrite(LED_MOVIMIENTO, LOW);
    digitalWrite(letra1, LOW);
    digitalWrite(letra2, LOW);
    digitalWrite(letra3, LOW);
    digitalWrite(letra4, LOW);
    digitalWrite(letra5, LOW);
    digitalWrite(letra6, LOW);
    digitalWrite(letra7, LOW);
}

//condicionales uso de if y switch
switch(contador){
        case 0:
          if (lecturaBajar == 0)
          {
             MostrarYAvisar(A,B,C,E,F,G,A,0);
          } 
          if (lecturaMovimiento == 0)
          {
           Mostrar7Segmentos(A,B,C,E,F,G,A,3000);
           Serial.println("Planta Baja");
          }
           break;
        case 1:
          if (lecturaBajar == 0)
          {
             Apagar7Segmentos(A,B,D,F,G,A,B);   
          } 
          Apagar7Segmentos(A,B,C,E,F,G,A);
          Mostrar7Segmentos(A,E,A,E,A,E,A,3000);
          Serial.println("Piso 1");
          break;
        case 2:
          if (lecturaBajar == 0)
          {
             Apagar7Segmentos(A,B,D,E,F,A,B);   
          } 
          Apagar7Segmentos(A,E,A,E,A,E,A);
          Mostrar7Segmentos(A,B,D,F,G,A,B,3000);
          Serial.println("Piso 2");
          break;
}
if (lecturaBajar == 0)
{
    contador--; 
}
else
{
    contador++;
}
//Uso de bandera
  if (FlagPlantaBaja == 0)
  {
     Serial.println("Planta Baja");
      digitalWrite(A, HIGH);
      digitalWrite(B, HIGH);
      digitalWrite(C, HIGH);
      digitalWrite(E, HIGH);
      digitalWrite(F, HIGH);
      digitalWrite(G, HIGH);
      FlagPlantaBaja = 1;
  }


```

## Link del proyecto
* [proyecto](https://www.tinkercad.com/things/bKFRt3FmXNC)


## Fuentes
* [tutorial markdown](https://www.youtube.com/watch?v=oxaH9CFpeEE)



