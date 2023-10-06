# Tp-SPD
![alt text](https://github.com/KevinRivarola2/Tp-SPD/blob/main/TP1/Imagenes/9b8084d5-b1b7-4b05-be03-3ce359a2cd41.jpg)
## Integrantes
* Kevin Rivarola
* Tomás Sandoval
## Proyecto: Contador de 0 a 99 con Display 7 Segmentos y Multiplexación
![alt text](https://github.com/KevinRivarola2/Tp-SPD/blob/main/TP1/Imagenes/d3ab24f5-09f7-40dc-a2bc-bea4cfb72552.jpg)
## Descripción
Placa arduino que permite al usuario contar numeros del 0 al 99 haciendo uso de tres botones mostrandole los numeros en dos displays de 7 segmentos.
los botones son:
- sumar 1
- restar 1
- reiniciar conteo
## Codigo
### Función principal
Llama a 'determinar_boton_presionado' y guarda el numero del pin asociado al boton presionado en 'boton_presionado'.    
Luego Aumenta, decrementa o reinicia el contador segun el boton presionado. 
Finalmente llama a 'mostrar_contador' pasandole la variable 'contador' como argumento.   
~~~
void loop(){
  int boton_presionado = determinar_boton_presionado();
  if (boton_presionado == BOTON_SUMAR){
    contador++;
    if (contador > 99){
      contador = 0;
    }
  }
  else if(boton_presionado == BOTON_RESTAR){
    contador--;
    if (contador < 0){
      contador = 99;
    }
  }
  else if(boton_presionado == BOTON_RESET){
    contador = 0;
  }
  mostrar_contador(contador);  
}
~~~
### mostrar_contador
Función que se encarga de la multiplexacion, toma un int como argumento y no retorna nada.  
Primero usa el contador para calcular los digitos que iran en los display.
luego llama a 'prender_display' con argumento 0 para 

~~~
void mostrar_contador(int contador) {
  int decena = contador / 10;
  int unidad = contador -  decena * 10;
  prender_display(0);
  mostrar_digito(decena);
  prender_display(DISPLAY_DECENA);
  prender_display(0);
  mostrar_digito(unidad);
  prender_display(DISPLAY_UNIDAD); 
}
~~~
