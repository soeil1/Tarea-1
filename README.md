#include <stdio.h>
#include <stdlib.h>
#include<string.h>
#include<stdbool.h>
#include <math.h>
int main(){

    int op;//Datos de entrada
    printf("\t----------------------------------------------------------------------\n");
    printf("\t---------------BIENVENIDO ESPERO QUE TE ENCUENTRES BIEN---------------\n");
    printf("\t----------------------------------------------------------------------\n");

    printf("\n\tSeleccione un programa a correr\n\n\t1)De sistema binario a octal, decimal y hexadecimal\n\t2)De sistema octal a binario, decimal y hexadecimal\n\t3)De sistema decimal a binario, octal y hexadecimal\n\t4)De sistema hexadecimal a binario, octal y decimal\n\t5)De sistema base n a binario, octal, decimal y hexadecimal y viseversa\n\t6)SALIR\n\t") ;
    scanf("%d", &op);

    while(op<6 && op>0){//utilice un ciclo do while para realizar el menu
            fflush(stdin);
        while(op<1 || op>6){

            printf("InserciOn no vAlida\nValores vAlidos: 1 - 6");
            printf("\n\tSeleccione un programa a correr\n\n\t1)De sistema binario a octal, decimal y hexadecimal\n\t2)De sistema octal a binario, decimal y hexadecimal\n\t3)De sistema decimal a binario, octal y hexadecimal\n\t4)De sistema hexadecimal a binario, octal y decimal\n\t5)De sistema base n a binario, octal, decimal y hexadecimal y viseversa\n\t6)SALIR\n\t") ;
            scanf("%d", &op);
        }

        while(op==1){//Esra es la ejecuciÛn del primer problema

            printf("\n\t------CONVERCIONES DE SISTEMA BINARIO----------\n");
            printf("\n\t1)De sistema binario a octal\n\t2)De sistema binario a decimal\n\t3)De sistema binario a hexadecimal\n\t");
            printf("\n\t---------------------------------------------\n\t");
            long exp=0,decimal=0,num,digito,aux;
            bool esBinario;
            int j;
            int i=0;

            do {
                printf("Ingresa un valor en sistema binario:\n\t");//Pedimos el numero binario
                scanf("%llu",&num);//leer
                printf("\n\t---------------------------------------------\n\t");
                esBinario = true;
                aux = num;
                while (aux != 0) {
                                  digito = aux % 10;//Separa digitos
                                  if (digito != 0 && digito != 1)
                                     { //If valida que no es binario
                                      esBinario = false;
                                     }
                                  aux = aux / 10;//elimina los digitos
                                 }
              } while (!esBinario);//si no es verdadero vuelve a solicitar el numero

                while(num !=0){
                                digito=num %10; //separando
                                num=num/10;//eliminando
                                decimal=decimal+digito*(pow(2,exp));//multiplica por la potencia correspondiente de acuerdo a la posicion
                                exp++;
                              }
                printf("\n\tLa conversion en decimal es:\n\t%i",decimal);
                printf("\n");
                printf("\n\t---------------------------------------------\n\t");
                int n=decimal;
                int octal[999]; //Declaramos nuestras variables a usar.

                while(n){
                        octal[i]=n%8; //separando digitos
                        n=n/8;//eliminando
                        i++;
                        }
                printf("La conversion en octal es:\n\t");
                for(j=i-1;j>=0;j--)//imprimir el arreglo como habia sido guardado de derecha a izquierda j disminuye y escribe de izquierda a derecha
                printf("%d",octal[j]);

                printf("\n");
                printf("\n\t---------------------------------------------\n\t");

               int h=decimal;
               char hexa[100],numH[17]={"0123456789ABCDEF"}; //creamos un arreglo con los numeros en hexadecimal y uno para guardar las variables

               while(h){
                       hexa[i]=numH[h%16];//separando digitos y guardando en el arreglo hexa
                       h=h/16;//eliminando
                       i++;
                      }
               printf("La conversion en hexadecimal es:\n\t");
               for(j=i-1;j>0;j--)
               printf("%c",hexa[j]);//imprimir el arreglo como habia sido guardado de derecha a izquierda j disminuye y escribe de izquierda a derecha
               printf("\n\t---------------------------------------------\n\t");


               printf("\n\tDesea Repetir la ejeciciOn de PROBLEMA1? (1 = Si || 2 = No)\n\tELECCION: ");
               scanf("%d", &op);
               if(op==1){
                //        //Repetimos la ejeciciOn del Programa Actual
               }else if(op==2){
                op=6;    //Salimos al MenU Inicial
            }

        }
        while(op==2){
            fflush(stdin);//Borrar memoria

            printf("\n\t------CONVERCIONES DE SISTEMA OCTAL----------\n\t");
            printf("\n\t1)De sistema octal a binario\n\t2)De sistema octal a decimal\n\t3)De sistema octal a hexadecimal\n\t");
            printf("\n\t---------------------------------------------\n\t");

            int n,b[50],d=0,h[50];
            int i=0;
            int s;
            inicio:
            //pedir y almacenar numero octal//
            printf("Ingresa un valor en sistema octal:\n\t");
            scanf("%i",&n);
          //separar el numero en sus cifras individuales
                while(n!=0){
                            b[i]=n%10;//se almacena el residuo de n/10
                            if(b[i]<0 || b[i]>7)//se comparan las cifras para verificar que esten en sistema octal
                                {
                                printf("El numero ingresado no esta en sistema octal,ingresa otro \n");
                                goto inicio;//regresa al inicio del programa
                                }
                             n=n/10;//se quita la ultima cifra de n
                             i++;
                            }//se guardan mis cifras empezando por la ultima
              printf("\n\t---------------------------------------------\n\t");
              printf("La conversion en binario es:\n\t");
              //convertir cada cifra a su binario equivalente
              if(i==0)
                {
                    printf("000");
                }
              for(s=i-1;s>=0;s--)//i-1 seria el valor de mi ultima cifra,se hace un decremento para que i disminuya en 1 y asi mostrar mis cifras anteriores
               {
                if(b[s]==0)
                {
                    printf("000");
                }
                if(b[s]==1)
                {
                    printf("001");
                }
                if(b[s]==2)
                {
                    printf("010");
                }
                if(b[s]==3)
                {
                    printf("011");
                }
                if(b[s]==4)
                {
                    printf("100");
                }
                if(b[s]==5)
                {
                    printf("101");
                }
                if(b[s]==6)
                {
                    printf("110");
                }
                if(b[s]==7)
                {
                    printf("111");
                }
            }
             printf("\n\t---------------------------------------------\n\t");
             printf("La conversion en decimal es:\n\t");
                 for(s=i-1;s>=0;s--)//i-1 seria el valor de mi ultima cifra,se hace un decremento para que i disminuya en 1 y asi mostrar mis cifras anteriores
                  {
                    d=d+(b[s]*pow(8,s));/*convertir octal a decimal,donde pow es 8 elevado a la potencia s,donde s es el indice que corresponde al numero multiplicado
                                por el valor de la cifra almacenada en ese indice*/
                 }
            printf("\n\t%i",d);//mostrar el valor decimal
            printf("\n\t---------------------------------------------\n\t");
            printf("La conversion en hexadecimal es:\n\t");
            i=0;
            while(d!=0)
                    {
                    h[i]=d%16;//se almacena el residuo de d/16 por ser base hexadecimal
                    d=d/16;//se quita la ultima cifra de d
                    i++;
                    }//se guardan mis cifras empezando por la ultima
            for(s=i-1;s>=0;s--)//i-1 seria el valor de mi ultima cifra,se hace un decremento para que i disminuya en 1 y asi mostrar mis cifras anteriores
            {
                if(h[s]==10)
                {
                    printf("A");
                }
                if(h[s]==11)
                {
                    printf("B");
                }
                if(h[s]==12)
                {
                    printf("C");
                }
                if(h[s]==13)
                {
                    printf("D");
                }
                if(h[s]==14)
                {
                    printf("E");
                }
                if(h[s]==15)
                {
                    printf("F");
                }
                if(h[s]>0 && h[s]<10)
                {
                    printf("%i",h[s]);
                }
            }
            printf("\n\t---------------------------------------------\n\t");

            printf("\n\tDesea Repetir la ejecicion de PROBLEMA2? (1 = Si || 2 = No)\n\tELECCION: ");
            scanf("%d", &op);
            if(op==1){
                op=2;    //Repetimos la ejeciciOn del Programa Actual
            }else if(op==2){
                op=6;    //Salimos al MenU Inicial
            }

        }
        while(op==3){
            fflush(stdin);//Borrar memoria

            printf("\n\t------CONVERCIONES DE SISTEMA DECIMAL----------\n\t");
            printf("\n\t1)De sistema decimal a binario\n\t2)De sistema decimal a octal\n\t3)De sistema decimal a hexadecimal\n\t");
            printf("\n\t---------------------------------------------\n\t");
            int n,i=0,h,oc, binario[999],hexadecimal[999],octal[999];//Datos de entrada
            printf("\n\tIngresa un valor en sistema decimal:\n\t");
            scanf("%i",&n);
            oc=n;
            h=n;
            printf("\n\t---------------------------------------------\n\t");

            binario[999];{ //Declaramos nuestras variables a usar.
            while (n!=0){
                        binario[i] = n%2; //Esta linea es para guardar el residuo del valor de n entre 2. En un arreglo.
                        n=n/2; // Esta division es para modificar en valor de n en la proxima repeticion del while.
                        i++; // Para moficicar el valor de i en el arreglo binario en la siguiente repeticion del while.
                        }
                   i--;
                   printf("\n\tLa conversion en binario es:\n\t ");

            while (i>=0){//Este while se usa para imprimir los valores guardados en el arreglo binario.
                    switch(binario[i]){/*Este switch sirve evaluar los diferentes casos posibles, si el numero guardado en el arreglo es 2,3, se imprimira la correspondiente letra para cada caso*/

                                        default:
                                                printf("%i",binario[i]); /*Si es un numero diferente del 2 al 3 solamente pone lo que hay en el arreglo osea uno que va del 0 al 1.*/
                                        break;}
                                   i--;}
                     printf("\n");}
                     printf("\n\t---------------------------------------------\n\t");
           octal[999];{ //Declaramos nuestras variables a usar.
                   i=0;
           while (oc!=0){
                         octal[i]=oc%8; //Esta linea es para guardar el residuo del valor de n entre 8. En un arreglo.
                         oc=oc/8; //Esta division es para modificar en valor de n en la proxima repeticion del while.
                         i++;} // Para moficicar el valor de i en el arreglo octal en la siguiente repeticion del while.
                         i--;
                         printf("\n\tLa conversion en octal es:\n\t ");

          while (i>=0){ //Este while se usa para imprimir los valores guardados en el arreglo octal.
                    switch(octal[i]){/*Este switch sirve evaluar los diferentes casos posibles, si el numero guardado en el arreglo es 8, se imprimira la correspondiente de un numero*/
                                    default:
                                            printf("%i",octal[i]); /*Si es un numero diferente del 10 al 15 solamente pone lo que hay en el arreglo osea uno que va del 0 al 9.*/
                                    break;}
                                    i--;}
                        printf("\n\t---------------------------------------------\n\t");
                        printf("\n");}

         hexadecimal[999];{ //Declaramos nuestras variables a usar.
                       i=0;
         while (h!=0){
                      hexadecimal[i] = h%16; //Esta linea es para guardar el residuo del valor de n entre 16. En un arreglo.
                      h=h/16; // Esta division es para modificar en valor de n en la proxima repeticion del while.
                      i++;}// Para moficicar el valor de i en el arreglo hexadecimal en la siguiente repeticion del while.
                      i--;
                      printf("\n\tLa conversion en hexadecimal es:\n\t ");

         while (i>=0){ //Este while se usa para imprimir los valores guardados en el arreglo hexadecimal.
                    switch(hexadecimal[i]){/*Este switch sirve evaluar los diferentes casos posibles, si el numero guardado en el arreglo es 10,11,12,13,14 0 15, se imprimira la correspondiente letra para cada caso*/
                                    case 10:
                                            printf("A");
                                    break;
                                    case 11:
                                            printf("B");
                                    break;
                                    case 12:
                                            printf("C");
                                    break;
                                    case 13:
                                            printf("D");
                                    break;
                                    case 14:
                                            printf("E");
                                    break;
                                    case 15:
                                            printf("F");
                                    break;
                                    default:
                                            printf("%i",hexadecimal[i]); /*Si es un numero diferente del 10 al 15 solamente pone lo que hay en el arreglo osea uno que va del 0 al 9.*/
                                    break;}
                                i--;}
                        printf("\n\t---------------------------------------------\n\t");
                    printf("\n");}
            printf("\n\tDesea Repetir la ejeciciOn de PROBLEMA3? (1 = Si || 2 = No)\n\tELECCION: ");
            scanf("%d", &op);
            if(op==1){
                op=3;    //Repetimos la ejeciciOn del Programa Actual
            }else if(op==2){
                op=6;    //Salimos al MenU Inicial
            }
        }

        while(op==4){
            fflush(stdin);//Borrar memoria

            printf("\n\t------CONVERCIONES DE SISTEMA HEXADECIMAL------\n\t");
            printf("\n\t1)De sistema hexadecimal a binario\n\t2)De sistema hexadecimal a octal\n\t3)De sistema hexadecimal a decimal\n\t");
            printf("\n\t---------------------------------------------\n\t");

            int i,l,j;
            int octal[999],potencia=1, decimal=0;
            char n[999];//El octal se rrecibbe como cadena

        do{//whhile que controla que se iongrese un numero en hexadecimmal
            fflush(stdin);//liemmpia la entrada
            printf("\n\tIngresa un valor en hexadecimal:\n\t");
            scanf("%s",n);//lee una cadena sin espacios
            l=strlen(n);//optiene la longitd de la cadena

           for(i=l-1;i>=0;i--)//fpr que recorre la cadena de izquierda a derecha
              {
           switch (n[i])//switch que recorre cada elemento del areglo
                 {
                    case '0':
                        j=0;
                          break;

                      case '1':
                          j=0;
                          break;

                    case '2':
                        j=0;
                          break;

                      case '3':
                          j=0;
                          break;

                    case '4':
                        j=0;
                          break;

                      case '5':
                          j=0;
                          break;
                      case '6':
                          j=0;
                          break;

                    case '7':
                        j=0;
                          break;

                      case '8':
                          j=0;
                          break;

                      case '9':
                          j=0;
                          break;

                      case 'A':
                          j=0;
                          break;
                      case'a':
                          j=0;
                          break;

                      case 'B':
                          j=0;
                          break;
                      case'b':
                          j=0;
                          break;

                      case 'C':
                          j=0;
                          break;
                      case 'c':
                          j=0;
                          break;

                    case 'D':
                        j=0;
                          break;
                      case 'd':
                          j=0;
                          break;

                      case 'E':
                          j=0;
                          break;
                      case'e':
                          j=0;
                          break;

                      case 'F':
                          j=0;
                          break;
                    case 'f':
                        j=0;
                        break;
                    default:
                        printf("Numero no valido\n ");
                        printf("\n\t---------------------------------------------\n\t");
                        j=1;// sirve para repetir el ciclo en caso de que ingren un digito invvalido
                    break;
                    }//cierre swtch que reconoce los digitos

            }//cierre for que recorre cada elemento del arreglo del meno

        }while(j==1);// while que repite el menu en caso de ingresar un digito invalido
              fflush(stdin);
              int b[l][4];//matriz para binario
            //codigo de Hexadecimal a binario//
            //***************************************
            //************************************
              for (i=l;i>=0;i--)//este for recorre de izquierda a deracha la cadena dada para conversion a codigo bbbinario
                 {
                  switch (n[i])//switch para cada caso del elemnto del areglo para binario
                        {
                        case '0':
                            b[i][0]=0;//se hace una matris de l filas y 4 columnas para
                            b[i][1]=0;//Se pone el valor que corresponde a cada valor del elemnto Hexadecimal
                            b[i][2]=0;
                            b[i][3]=0;
                         break;
                         case '1':

                            b[i][0]=0;
                            b[i][1]=0;
                            b[i][2]=0;
                            b[i][3]=1;

                         break;
                         case '2':

                            b[i][0]=0;
                            b[i][1]=0;
                            b[i][2]=1;
                            b[i][3]=0;

                         break;
                         case '3':

                            b[i][0]=0;
                            b[i][1]=0;
                            b[i][2]=1;
                            b[i][3]=1;

                         break;
                         case '4':
                            b[i][0]=0;
                            b[i][1]=1;
                            b[i][2]=0;
                            b[i][3]=0;

                         break;
                         case '5':
                            b[i][0]=0;
                            b[i][1]=1;
                            b[i][2]=0;
                            b[i][3]=1;

                         break;
                         case '6':

                            b[i][0]=0;
                            b[i][1]=1;
                            b[i][2]=1;
                            b[i][3]=0;

                         break;
                         case '7':

                            b[i][0]=0;
                            b[i][1]=1;
                            b[i][2]=1;
                            b[i][3]=1;

                         break;
                         case '8':
                            b[i][0]=1;
                            b[i][1]=0;
                            b[i][2]=0;
                            b[i][3]=0;

                         break;
                         case '9':
                            b[i][0]=1;
                            b[i][1]=0;
                            b[i][2]=0;
                            b[i][3]=1;

                         break;
                         case 'A':

                            b[i][0]=1;
                            b[i][1]=0;
                            b[i][2]=1;
                            b[i][3]=0;

                         break;
                         case 'a':

                            b[i][0]=1;
                            b[i][1]=0;
                            b[i][2]=1;
                            b[i][3]=0;

                         break;
                         case 'B':

                            b[i][0]=1;
                            b[i][1]=0;
                            b[i][2]=1;
                            b[i][3]=1;

                         break;
                         case 'b':

                            b[i][0]=1;
                            b[i][1]=0;
                            b[i][2]=1;
                            b[i][3]=1;

                         break;
                         case 'C':

                            b[i][0]=1;
                            b[i][1]=1;
                            b[i][2]=0;
                            b[i][3]=0;

                         break;
                         case 'c':

                            b[i][0]=1;
                            b[i][1]=1;
                            b[i][2]=0;
                            b[i][3]=0;


                         break;
                         case 'D':

                            b[i][0]=1;
                            b[i][1]=1;
                            b[i][2]=0;
                            b[i][3]=1;

                         break;
                         case 'd':

                            b[i][0]=1;
                            b[i][1]=1;
                            b[i][2]=0;
                            b[i][3]=1;

                         break;
                         case 'E':

                            b[i][0]=1;
                            b[i][1]=1;
                            b[i][2]=1;
                            b[i][3]=0;

                         break;
                         case 'e':

                            b[i][0]=1;
                            b[i][1]=1;
                            b[i][2]=1;
                            b[i][3]=0;

                         break;
                         case 'F':

                            b[i][0]=1;
                            b[i][1]=1;
                            b[i][2]=1;
                            b[i][3]=1;

                         break;
                         case 'f':

                            b[i][0]=1;
                            b[i][1]=1;
                            b[i][2]=1;
                            b[i][3]=1;

                         break;

                      }//cierre swich de binario

                    } //cierre for de binario
                    printf("\n\t---------------------------------------------\n\t");
                    printf("La conversion en binario es :\n\t");
                      for(i=0;i<l;i++)// for para impimir la matriz que solo controla las filas
                      {
                          printf("%i",b[i][0]);
                        printf("%i",b[i][1]);
                        printf("%i",b[i][2]);
                        printf("%i",b[i][3]);
                          printf("   ");// espacio para imprimir un espacio cada 4 digitos
                       }
                    //codigo para converison a octal
                    //************************
                    //************************
                    fflush(stdin);
                    //Dado que es una cadena no se pueden realizar operaciones asi que primero se converite en decimal y luego a octal
                for (i=l;i>=0;i--)//fpr que recorre la cadena de izquierda a derecha
                {

                switch (n[i])//switch que lee cada elemento del numero hexadecimal
                      {

                        case '0':
                        // decimal+=   ==   decimal=decimal+
                         decimal += 0*potencia;// Dado que el elemnto es base 16 se multiplica cada digito por 16
                         potencia *= 16;//la potencia en la primer vuelta vale 1 que despues de entrar en un caso se multiplica por 16
                                         // y asi sucesivvamente hasta reccorere todos los digitos de la cadena
                         break;
                         case '1':
                         decimal += 1*potencia;
                         potencia *= 16;

                         break;
                         case '2':
                         decimal += 2*potencia;
                         potencia *= 16;

                         break;
                         case '3':
                         decimal += 3*potencia;
                         potencia *= 16;

                         break;
                         case '4':
                         decimal += 4*potencia;
                         potencia *= 16;

                         break;
                         case '5':
                         decimal += 5*potencia;
                         potencia *= 16;

                         break;
                         case '6':
                         decimal += 6*potencia;
                         potencia *= 16;

                         break;
                         case '7':
                         decimal += 7*potencia;
                         potencia *= 16;

                         break;
                         case '8':
                         decimal += 8*potencia;
                         potencia *= 16;

                         break;
                         case '9':
                         decimal += 9*potencia;
                         potencia *= 16;

                         break;
                         case 'A':
                         decimal +=  10*potencia;
                         potencia *= 16;

                         break;
                         case 'a':
                         decimal +=  10*potencia;
                         potencia *= 16;

                         break;
                         case 'B':
                         decimal +=  11*potencia;
                         potencia *= 16;

                         break;
                         case 'b':
                         decimal +=  11*potencia;
                         potencia *= 16;

                         break;
                         case 'C':
                         decimal +=  12*potencia;
                         potencia *= 16;

                         break;
                         case 'c':
                         decimal +=  12*potencia;
                         potencia *= 16;

                         break;
                         case 'D':
                         decimal +=  13*potencia;
                         potencia *= 16;

                         break;
                         case 'd':
                         decimal +=  13*potencia;
                         potencia *= 16;

                         break;
                         case 'E':
                         decimal +=  14*potencia;
                         potencia *= 16;

                         break;
                         case 'e':
                         decimal +=  14*potencia;
                         potencia *= 16;

                         break;
                         case 'F':
                         decimal +=  15*potencia;
                         potencia *= 16;

                         break;
                         case 'f':
                         decimal +=  15*potencia;
                         potencia *= 16;

                         break;


                        }//cierre swich
                }    //cierre for
                i=0;

                 while (decimal!=0){
                            octal[i] = decimal%8; //Esta linea es para guardar el residuo del valor de n entre 8. En un arreglo.
                            decimal = decimal /8; //Esta division es para modificar en valor de n en la proxima repeticion del while.
                            i++;} // Para moficicar el valor de i en el arreglo hexadecimal en la siguiente repeticion del while.
                        i--;
                    printf("\n\t---------------------------------------------\n\t");
                    printf("La conversion en sistema octal es :\n\t");

                while (i>=0) //Este while se usa para imprimir los valores guardados en el arreglo octal.
                    {
                     switch(octal[i]){
                            /*Este switch sirve evaluar los diferentes casos posibles, si el numero guardado en el arreglo
                            es 8, se imprimira la correspondiente de un numero*/

                                case 8:
                                        printf("0");
                                break;
                                default:
                                        printf("%i",octal[i]); /*Si es un numero diferente del 10 al 15 solamente pone lo que hay en el arreglo osea uno que va del 0 al 9.*/
                                break;
                                                }
                                i--;}

                //codigo para convertir a sistema decimal
                //***************
                //*******************************************************
                fflush(stdin);
                potencia=1;//reestablece valores de variables utilizadas anteriormente
                decimal=0;// reestablece valores utilizados
                for (i=l;i>=0;i--)//for para recorrer cadena de izquirda a deracha para sistema decimal
                {

                switch (n[i])//swicht para leer el valor del elemento de la cadena para decimal
                    {
                         case '0':
                         decimal += 0*potencia;// dado que hexadecimal es base 16 se multiplica cada elemnto por 16
                         potencia *= 16;//cada vuelta la potencia se multiplica por 16

                         break;
                         case '1':
                         decimal += 1*potencia;
                         potencia *= 16;


                         break;
                         case '2':
                         decimal += 2*potencia;
                         potencia *= 16;

                         break;
                         case '3':
                         decimal += 3*potencia;
                         potencia *= 16;

                         break;
                         case '4':
                         decimal += 4*potencia;
                         potencia *= 16;

                         break;
                         case '5':
                         decimal += 5*potencia;
                         potencia *= 16;

                         break;
                         case '6':
                         decimal += 6*potencia;
                         potencia *= 16;

                         break;
                         case '7':
                         decimal += 7*potencia;
                         potencia *= 16;

                         break;
                         case '8':
                         decimal += 8*potencia;
                         potencia *= 16;

                         break;
                         case '9':
                         decimal += 9*potencia;
                         potencia *= 16;

                         break;

                         case 'A':
                         decimal +=  10*potencia;
                         potencia *= 16;

                         break;
                         case 'a':
                         decimal +=  10*potencia;
                         potencia *= 16;

                         break;
                         case 'B':
                         decimal +=  11*potencia;
                         potencia *= 16;

                         break;
                         case 'b':
                         decimal +=  11*potencia;
                         potencia *= 16;

                         break;
                         case 'C':
                         decimal +=  12*potencia;
                         potencia *= 16;

                         break;
                         case 'c':
                         decimal +=  12*potencia;
                         potencia *= 16;

                         break;
                         case 'D':
                         decimal +=  13*potencia;
                         potencia *= 16;
                         break;
                         case 'd':
                         decimal +=  13*potencia;
                         potencia *= 16;
                         break;
                         case 'E':
                         decimal +=  14*potencia;
                         potencia *= 16;
                         break;
                         case 'e':
                         decimal +=  14*potencia;
                         potencia *= 16;
                         break;
                         case 'F':
                         decimal +=  15*potencia;
                         potencia *= 16;
                         break;
                         case 'f':
                         decimal +=  15*potencia;
                         potencia *= 16;
                         break;
                    }//cierre swich

                }//cierre for
                printf("\n\t---------------------------------------------\n\t");
                printf("La conversion en decimal es:\n\t%d",decimal);
            printf("\n\tDesea Repetir la ejeciciOn de PROBLEMA4? (1 = Si || 2 = No)\n\tELECCION: ");
            scanf("%d", &op);
            if(op==1){
                op=4;    //Repetimos la ejeciciOn del Programa Actual
            }else if(op==2){
                op=6;    //Salimos al MenU Inicial
            }

        }
           while(op==5){
            fflush(stdin);//Borrar memoria

        int opc,n;
        printf("\n\t------CONVERCIONES DE SISTEMA BASE N------\n\t");
        printf("\n\t1)Base n a binario,octal,decimal y hexadecimal\n\t2)De Binario a Base n\n\t3)De octal a base n\n\t4)De decimal a base n\n\t5)De hexadecimal a base n\n\t");
        scanf("%i",&opc);
        printf("\n\t---------------------------------------------\n\t");
        switch (opc)
        {
        case 1:
            printf("Base n a binario,octal,decimal y hexadecimal");
            printf("\n\t---------------------------------------------\n\t");
        {
            int n,l,i,b,d[999],c=0,e=0,hexadecimal[99],oc[99],cp,binario[999];
            char num[999],numH[35]="0123456789ABCDEFGHIJKLMNOPQRSUWXYZ";

            printf("\n\t---------------------------------------------\n\t");
            printf("Que base desea utilizar?\n\t");
             printf("\n\t---------------------------------------------\n\t");
            scanf("%i",&n);
            inicio2:
             printf("\n\t---------------------------------------------\n\t");
            printf("Ingresa un valor en base %i\n\t",n);
             printf("\n\t---------------------------------------------\n\t");
            scanf("%s",num);
            l=strlen(num);

    switch(n)
    {
        case 1:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 2:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 3:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 4:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 5:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 6:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 7:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 8:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 9:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 10:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 11:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 12:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 13:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
            break;
            }
        case 14:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 15:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        case 16:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 17:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 18:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 19:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 20:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 21:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 22:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 23:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 24:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 25:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 26:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 27:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P'&& num[i]!='Q')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 28:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P'&& num[i]!='Q'&& num[i]!='R')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 29:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P'&& num[i]!='Q'&& num[i]!='R'&& num[i]!='S')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 30:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P'&& num[i]!='Q'&& num[i]!='R'&& num[i]!='S'&& num[i]!='T')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 31:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P'&& num[i]!='Q'&& num[i]!='R'&& num[i]!='S'&& num[i]!='T'&& num[i]!='U')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 32:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P'&& num[i]!='Q'&& num[i]!='R'&& num[i]!='S'&& num[i]!='T'&& num[i]!='U'&& num[i]!='V')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 33:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P'&& num[i]!='Q'&& num[i]!='R'&& num[i]!='S'&& num[i]!='T'&& num[i]!='U'&& num[i]!='V'&& num[i]!='W')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 34:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P'&& num[i]!='Q'&& num[i]!='R'&& num[i]!='S'&& num[i]!='T'&& num[i]!='U'&& num[i]!='V'&& num[i]!='W'&& num[i]!='X')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 35:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P'&& num[i]!='Q'&& num[i]!='R'&& num[i]!='S'&& num[i]!='T'&& num[i]!='U'&& num[i]!='V'&& num[i]!='W'&& num[i]!='X'&& num[i]!='Y')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
            case 36:
            {
                for(i=l-1;i>=0;i--)
                if (num[i]!='0'&& num[i]!='1'&& num[i]!='2'&& num[i]!='3'&& num[i]!='4'&& num[i]!='5'&& num[i]!='6'&& num[i]!='7'&& num[i]!='8'&& num[i]!='9'&& num[i]!='A'&& num[i]!='B'&& num[i]!='C'&& num[i]!='D'&& num[i]!='E'&& num[i]!='F'&& num[i]!='G'&& num[i]!='H'&& num[i]!='I'&& num[i]!='J'&& num[i]!='K'&& num[i]!='L'&& num[i]!='M'&& num[i]!='N'&& num[i]!='O'&& num[i]!='P'&& num[i]!='Q'&& num[i]!='R'&& num[i]!='S'&& num[i]!='T'&& num[i]!='U'&& num[i]!='V'&& num[i]!='W'&& num[i]!='X'&& num[i]!='Y'&& num[i]!='Z')
                {
                    printf("valor no valido,ingrese otro");
                    goto inicio2;
                }
                break;
            }
        }

        for(i=l-1;i>=0;i--)
        {
            if(num[i]=='0')
            {
                d[i]=0;
            }
            if(num[i]=='1')
            {
                d[i]=1;
            }
            if(num[i]=='2')
            {
                d[i]=2;
            }
            if(num[i]=='3')
            {
                d[i]=3;
            }
            if(num[i]=='4')
            {
                d[i]=4;
            }
            if(num[i]=='5')
            {
                d[i]=5;
            }
            if(num[i]=='6')
            {
                d[i]=6;
            }
            if(num[i]=='7')
            {
                d[i]=7;
            }
            if(num[i]=='8')
            {
                d[i]=8;
            }
            if(num[i]=='9')
            {
                d[i]=9;
            }
            if(num[i]=='A')
            {
                d[i]=10;
            }
             if(num[i]=='B')
            {
                d[i]=11;
            }
            if(num[i]=='C')
            {
                d[i]=12;
            }
            if(num[i]=='D')
            {
                d[i]=13;
            }
            if(num[i]=='E')
            {
                d[i]=14;
            }
            if(num[i]=='F')
            {
                d[i]=15;
            }
            if(num[i]=='G')
            {
                d[i]=16;
            }
            if(num[i]=='H')
            {
                d[i]=17;
            }
            if(num[i]=='I')
            {
                d[i]=18;
            }
            if(num[i]=='J')
            {
                d[i]=19;
            }
             if(num[i]=='K')
            {
                d[i]=20;
            }
             if(num[i]=='L')
            {
                d[i]=21;
            }
            if(num[i]=='M')
            {
                d[i]=22;
            }
            if(num[i]=='N')
            {
                d[i]=23;
            }
            if(num[i]=='O')
            {
                d[i]=24;
            }
            if(num[i]=='P')
            {
                d[i]=25;
            }
            if(num[i]=='Q')
            {
                d[i]=26;
            }
            if(num[i]=='R')
            {
                d[i]=27;
            }
            if(num[i]=='S')
            {
                d[i]=28;
            }
            if(num[i]=='T')
            {
                d[i]=29;
            }
            if(num[i]=='U')
            {
                d[i]=30;
            }
            if(num[i]=='V')
            {
                d[i]=31;
            }
            if(num[i]=='W')
            {
                d[i]=32;
            }
            if(num[i]=='X')
            {
                d[i]=33;
            }
            if(num[i]=='Y')
            {
                d[i]=34;
            }
            if(num[i]=='Z')
            {
                d[i]=35;
            }
        }
        printf("\n\t---------------------------------------------\n\t");
        printf("tu conversion a decimal es\n");
        printf("\n\t---------------------------------------------\n\t");
        for(i=l-1;i>=0;i--)
        {
            c=c+(d[i]*pow(n,e));
            e++;
        }
        printf("%i\n",c);
        cp=c;
        b=c;
        i=0;

        printf("\n\t---------------------------------------------\n\t");
        printf("tu conversion a Hexadecimal es\n");
        printf("\n\t---------------------------------------------\n\t");
        while (c!=0){
                    hexadecimal[i] = c%16; //Esta linea es para guardar el residuo del valor de n entre 16. En un arreglo.
                    c = c /16; // Esta division es para modificar en valor de n en la proxima repeticion del while.
                    i++; // Para moficicar el valor de i en el arreglo hexadecimal en la siguiente repeticion del while.
                    }
                i--;
        while (i>=0) //Este while se usa para imprimir los valores guardados en el arreglo hexadecimal.
            {
            switch(hexadecimal[i])/*Este switch sirve evaluar los diferentes casos posibles, si el numero guardado en el arreglo
                                        es 10,11,12,13,14 0 15, se imprimira la correspondiente letra para cada caso*/
                {
                case 10:
                    printf("A");
                 break;
                case 11:
                    printf("B");
                 break;
                case 12:
                     printf("C");
                  break;
                case 13:
                     printf("D");
                  break;
                case 14:
                    printf("E");
                   break;
                case 15:
                    printf("F");
                break;
                default:
                printf("%i",hexadecimal[i]); /*Si es un numero diferente del 10 al 15
                                                        solamente pone lo que hay en el arreglo osea uno que va del 0 al 9.*/
                 break;
                }
            i--;
            }
            printf("\n");
            i=0;
            printf("\n\t---------------------------------------------\n\t");
            printf("tu conversion a octal es\n");
            printf("\n\t---------------------------------------------\n\t");
            i=0;
        while (cp!=0){
                     oc[i]=cp%8; //Esta linea es para guardar el residuo del valor de n entre 8. En un arreglo.
                     cp=cp/8; //Esta division es para modificar en valor de n en la proxima repeticion del while.
                     i++;} // Para moficicar el valor de i en el arreglo hexadecimal en la siguiente repeticion del while.
                     i--;
        while (i>=0){ //Este while se usa para imprimir los valores guardados en el arreglo octal.
                    switch(oc[i]){/*Este switch sirve evaluar los diferentes casos posibles, si el numero guardado en el arreglo es 8, se imprimira la correspondiente de un numero*/
                                    default:
                                            printf("%i",oc[i]); /*Si es un numero diferente del 10 al 15 solamente pone lo que hay en el arreglo osea uno que va del 0 al 9.*/
                                    break;}
                                    i--;}
                        printf("\n");
                        i=0;
    while (b!=0){
        binario[i]=b%2;
        b=b/2;
        i++;
        }
        i--;
        printf("\n\t---------------------------------------------\n\t");
        printf("tu conversion a binario es \n\t");
        printf("\n\t---------------------------------------------\n\t");

        while (i>=0){
            switch(binario[i]){
            default:
            printf("%i",binario[i]); //Si es un numero diferente del 10 al 15 solamente pone lo que hay en el arreglo osea uno que va del 0 al 9./
            break;}
            i--;}
            printf("\n\t---------------------------------------------\n\t");
            break;
        }


    case 2:
        printf("De Binario a Base n");
        printf("\n\t---------------------------------------------\n\t");
        {
            int h=0;
            long num,digito,aux,exp=0;
            bool esBinario;
            int i=0,j;
            int base;
            char numH[35]="0123456789ABCDEFGHIJKLMNOPQRSUWXYZ";

            do {
            printf("Ingresa un valor en binario:\n\t");//Pedimos el numero binario
            scanf("%llu",&num);//leer

            esBinario = true;
            aux = num;
            while (aux != 0) {
                        digito = aux % 10;//Separa digitos
                        if (digito != 0 && digito != 1) { //If valida que no es binario
                            esBinario = false;
                        }
                    aux = aux / 10;//elimina los digitos
                    }
            } while (!esBinario);//si no es verdadero vuelve a solicitar el numero

            while(num !=0){
                 digito=num %10; //separando
                 num=num/10;//eliminando
                 h=h+digito*(pow(2,exp));//multiplica por la potencia correspondiente de acuerdo a la posicion
                 exp++;
                }
            printf("\tDame la base:\n\t");
            scanf("%i",&base);
            char hexa[base];

            while(h){
                  hexa[i]=numH[h%base];//separando digitos y guardando en el arreglo hexa
                  h=h/base;//eliminando
                  i++;
                }
            printf("\n\tEl numero en base %i es:\n\t ",base);
            for(j=i-1;j>=0;j--)
            printf("%c",hexa[j]);
            printf("\n\t---------------------------------------------\n\t");
          break;
        }


    case 3:
            printf("De octal a Base n");
            printf("\n\t---------------------------------------------\n\t");
            {
            int h=0,n,s,b[50];
            int i=0,j;
            int base;
            char numH[36]="0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
            inicio3:
            printf("Ingresa un valor en octal:\n\t");
            scanf("%i",&n);
                while(n!=0)
                    {
                        b[i]=n%10;//se almacena el residuo de n/10
                        if(b[i]<0 || b[i]>7)//se comparan las cifras para verificar que esten en sistema octal
                            {
                                printf("El numero ingresado no esta en sistema octal,ingresa otro \n");
                                goto inicio3;//regresa al inicio del programa
                            }
                        n=n/10;//se quita la ultima cifra de n
                        i++;
                    }//se guardan mis cifras empezando por la ultima
            for(s=i-1;s>=0;s--)//i-1 seria el valor de mi ultima cifra,se hace un decremento para que i disminuya en 1 y asi mostrar mis cifras anteriores
                {
                  h=h+(b[s]*pow(8,s));/*convertir octal a decimal,donde pow es 8 elevado a la potencia s,donde s es el indice que corresponde al numero multiplicado
                                por el valor de la cifra almacenada en ese indice*/
                }
                    i=0;
           printf("\n\tDame la base:\n\t");
           scanf("%i",&base);
           char hexa[base];

           while(h)
                {
                hexa[i]=numH[h%base];//separando digitos y guardando en el arreglo hexa
                h=h/base;//eliminando
                i++;
                }
          printf("\n\tEl numero en base %i es:\n\t",base);
          for(j=i-1;j>=0;j--)
              printf("%c",hexa[j]);
          printf("\n\t---------------------------------------------\n\t");
        break;
        }
    case 4:{

           printf("De decimal a Base n\n");
           printf("\n\t---------------------------------------------\n\t");
           int h;
           int i=0,j;
           int base;
           char numH[36]="0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";

           printf("Ingresa el valor en decimal:\n\t");
           scanf("%i",&h);

           printf("\tDame la base:\n\t ");
           scanf("%i",&base);
           char arre[base];

           while(h){
                arre[i]=numH[h%base];//separando digitos y guardando en el arreglo
                h=h/base;//eliminando
                i++;
                }
           printf("\tEl numero en base %i es:\n\t ",base);
           for(j=i-1;j>=0;j--)
           printf("%c",arre[j]);
           printf("\n\t---------------------------------------------\n\t");
      break;}

    case 5:

           printf("De hexadecimal a Base n");
           printf("\n\t---------------------------------------------\n\t");
           int i,j,potencia=1, decimal=0,l,base,h;
           char numH[35]="0123456789ABCDEFGHIJKLMNOPQRSUWXYZ",n[99];

           printf("Dame la base a la que quieres convertir :\n\t");
           scanf("%d",&base);
           char hexa[base];
           printf("\tDame el numero en hexadecimal:\n\t");
           scanf("%s",n);//lee una cadena sin espacios
           l=strlen(n);

           for (i=l;i>=0;i--)//for para recorrer cadena de izquirda a deracha para sistema decimal
             {

               switch (n[i])//swicht para leer el valor del elemento de la cadena para decimal
                    {

                    case '0':

                         decimal += 0*potencia;// dado que hexadecimal es base 16 se multiplica cada elemnto por 16
                         potencia *= 16;//cada vuelta la potencia se multiplica por 16

                         break;
                         case '1':
                         decimal += 1*potencia;
                         potencia *= 16;


                         break;
                         case '2':
                         decimal += 2*potencia;
                         potencia *= 16;

                         break;
                         case '3':
                         decimal += 3*potencia;
                         potencia *= 16;

                         break;
                         case '4':
                         decimal += 4*potencia;
                         potencia *= 16;

                         break;
                         case '5':
                         decimal += 5*potencia;
                         potencia *= 16;

                         break;
                         case '6':
                         decimal += 6*potencia;
                         potencia *= 16;

                         break;
                         case '7':
                         decimal += 7*potencia;
                         potencia *= 16;

                         break;
                         case '8':
                         decimal += 8*potencia;
                         potencia *= 16;

                         break;
                         case '9':
                         decimal += 9*potencia;
                         potencia *= 16;

                         break;
                         case 'A':
                         decimal +=  10*potencia;
                         potencia *= 16;

                         break;
                         case 'a':
                         decimal +=  10*potencia;
                         potencia *= 16;

                         break;
                         case 'B':
                         decimal +=  11*potencia;
                         potencia *= 16;

                         break;
                         case 'b':
                         decimal +=  11*potencia;
                         potencia *= 16;

                         break;
                         case 'C':
                         decimal +=  12*potencia;
                         potencia *= 16;

                         break;
                         case 'c':
                         decimal +=  12*potencia;
                         potencia *= 16;

                         break;
                         case 'D':
                         decimal +=  13*potencia;
                         potencia *= 16;

                         break;
                         case 'd':
                         decimal +=  13*potencia;
                         potencia *= 16;

                         break;
                         case 'E':
                         decimal +=  14*potencia;
                         potencia *= 16;

                         break;
                         case 'e':
                         decimal +=  14*potencia;
                         potencia *= 16;

                         break;
                         case 'F':
                         decimal +=  15*potencia;
                         potencia *= 16;

                         break;
                         case 'f':
                         decimal +=  15*potencia;
                         potencia *= 16;

                         break;

                    }//cierre swich

                }//cierre for

            i=0;
            while(decimal){
                hexa[i]=numH[decimal%base];//separando digitos y guardando en el arreglo hexa
                decimal=decimal/base;//eliminando
                i++;
                }
            printf("\tEl numero en base %i es:\n\t ",base);
            for(j=i-1;j>=0;j--)
            printf("%c",hexa[j]);
            printf("\n\t---------------------------------------------\n\t");
    break;

}

            printf("\n\tDesea Repetir la ejeciciOn de PROBLEMA4? (1 = Si || 2 = No)\n\tELECCION: ");
            scanf("%d", &op);
            if(op==1){
                op=5;    //Repetimos la ejeciciOn del Programa Actual
            }else if(op==2){
                op=6;    //Salimos al MenU Inicial
            }

        }
        printf("\n\tSeleccione un programa a correr\n\n\t1)De sistema binario a octal, decimal y hexadecimal\n\t2)De sistema octal a binario, decimal y hexadecimal\n\t3)De sistema decimal a binario, octal y hexadecimal\n\t4)De sistema hexadecimal a binario, octal y decimal\n\t5)De sistema base n a binario, octal, decimal y hexadecimal y viseversa\n\t6)SALIR\n\t") ;
        scanf("%d", &op);

    }
    printf("\n\t--------------HASTA LUEGO QUE TENGAS BUEN DIA---------------\n");//fin del ejecutable
}
