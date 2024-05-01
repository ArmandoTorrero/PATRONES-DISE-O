# ¿QUE ES UN PATRON DE DISEÑO?

 >>Un patrón de diseño es una solución general y reutilizable a un problema común que se presenta durante el desarrollo de software. Estos patrones proporcionan un enfoque probado y estructurado para resolver problemas de diseño de software de manera eficiente, promoviendo la reutilización de código, la modularidad y la mantenibilidad.

 >> Existen varios patrones de diseño con muchas soluciones pero existen tres principales: 
  - **Patrones de creacion**: Estos patrones se centran en la creación de objetos de manera eficiente, abstrayendo el proceso de creación para que el cliente no necesite conocer los detalles específicos de la implementación.
 - **Patrones de estructura**: Estos patrones se ocupan de la composición de clases y objetos para formar estructuras más grandes y complejas. 
 - **Patrones de comportamiento**: Estos patrones se centran en la comunicación entre objetos y cómo se comportan entre sí para lograr un comportamiento más flexible y eficiente del software. 
  
# ¿EN QUE CONSISTE?
 
 >> El propósito principal de los patrones de diseño en el desarrollo de software es proporcionar soluciones probadas y efectivas a problemas comunes que surgen durante el proceso de diseño y desarrollo. Estos patrones están diseñados para mejorar la eficiencia, la reutilización del código y la mantenibilidad del software.

 >> Los patrones de diseño consisten en descripciones formales de las mejores prácticas y soluciones para problemas específicos. Proporcionan un conjunto de reglas y pautas para la creación de software de alta calidad que sea fácil de entender, modificar y mantener. 

# ¿POR QUE APRENDER SOBRE PATRONES?

 - **Eficiencia en el desarrollo:**Los patrones de diseño proporcionan soluciones probadas y eficientes a problemas comunes en el diseño de software. Al aplicar estos patrones, los desarrolladores pueden evitar la necesidad de reinventar la rueda cada vez que se enfrentan a un problema similar, lo que ahorra tiempo y esfuerzo durante el desarrollo.
 - **Reutilizacion de codigo:**Al utilizar patrones de diseño, los desarrolladores pueden reutilizar componentes de software existentes que implementan esos patrones. Esto promueve la modularidad y la reutilización del código, lo que a su vez conduce a un desarrollo más rápido y una mayor consistencia en el código base.
 - **Mantenibilidad y escalabilidad:**Los patrones de diseño están diseñados para crear software que sea fácil de entender, mantener y extender. Al seguir las mejores prácticas y principios establecidos por los patrones de diseño, se reduce la complejidad del código y se facilita la incorporación de nuevas características y la realización de cambios en el software con un menor riesgo de introducir errores.
 - **Comunicacion efectiva:**Los patrones de diseño proporcionan un lenguaje común y una forma de comunicarse sobre el diseño de software dentro de un equipo de desarrollo. Esto facilita la colaboración entre los miembros del equipo y ayuda a garantizar un entendimiento compartido de la arquitectura y el diseño del sistema.
 - **Mejora de la calidad del software:**Al aplicar patrones de diseño, los desarrolladores pueden crear software que cumpla con los principios de diseño sólidos y las mejores prácticas de la industria. Esto conduce a un código más limpio, modular y mantenible, que es menos propenso a errores y más fácil de depurar y mantener a largo plazo.

## EJEMPLO DE PATRON DE DISEÑO CON PHP
>> En mi caso he elegido el patron de diseño llamado "bridge", el cual te permite dividir una clase muy grande en varias clases pequeñas pero que esten relacionadas con la principal gracias al uso de "extends", gracias a este patron podremos crear una clase que generalice los atributos y metodos que tendran las demas clases hijas para que estas mismas pueden usar esos metodos en todo momento. En mi ejemplo he imaginado un partido del ceuta el cual ira mucha gente la cual puede ser "abonado" o "junta directiva" y ambos tendran atributos y metodos en comun, para ello he creado una clase padre llamada "Persona" el cual tendra los atributos tipicos que tendria una persona normal para despues crear las otras dos clases que van a heredar sus atributos y metodos. 

```php

  <?php 
    class Persona 
    {
        public $dni; 
        public $nombre;  
        public $edad; 

        public function __construct($dni, $nombre, $edad) {
            $this->dni = $dni;
            $this->nombre = $nombre;
            $this->edad = $edad;
        }

        public function setDNI($dni) {
            $this->dni = $dni;         
        }

        public function setNombre($nombre) {
            $this->nombre = $nombre;
        }

        public function setEdad($edad) {
            $this->edad = $edad; 
        }

        public function getDNI() {
            return $this->dni;
        }

        public function getNombre() {
            return $this->nombre;
        }

        public function getEdad() {
            return $this->edad;
        }
    }

    class abonado extends Persona
    {
        public $numero_abonado; 
        public $asiento_abonado; 
        public $fechaPrimerAbono; 

        public function __construct($numero_abonado,$asiento_abonado,$fechaPrimerAbono) {
            $this->numero_abonado = $numero_abonado;
            $this->asiento_abonado = $asiento_abonado;
            $this->fechaPrimerAbono = $fechaPrimerAbono;
        }

        public function setNumeroAbonado($numero_abonado) {
            $this->numero_abonado = $numero_abonado;
        }

        public function setAsiento($asiento_abonado) {
            $this->asiento_abonado = $asiento_abonado;
        }

        public function setFechaPrimerAbono($fechaPrimerAbono) {
            $this->fechaPrimerAbono = $fechaPrimerAbono;
        }
    }

    class juntaDirectiva extends Persona
    {
        public $numero_junta_directiva; 
        public $sector; 

        public function __construct($numero_junta_directiva, $sector) {
            $this->numero_junta_directiva = $numero_junta_directiva;
            $this->sector = $sector;
        }

        public function setNumeroJunta($numero_junta_directiva){       
            $this->numero_junta_directiva = $numero_junta_directiva;
        }

        public function setSeccion($sector) {
            $this->sector = $sector;
        }
    }

    $objPersona = new Persona("12345678M","Juan",17);
    
    $objAbonado = new abonado("22334455n","Carlos",27);
    
    $objAbonado->getEdad(); 
    $objAbonado->getNombre()
?>

```
