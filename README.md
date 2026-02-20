# PARTE-2-EXAMEN-PMDM

# Examen Final: 

## 1. Configuración del Escenario y Objetos
 Se han creado los siguientes elementos básicos:
* **Plano:** Actúa como la base del escenario con colisiones estáticas.
* **Player:** Una esfera configurada con un componente **Rigidbody** para permitir interacciones físicas.
* **Enemigo:** Un cubo que contiene la lógica de perseguir y detección de colisiones.


## 2. Movimiento por Fuerza Aplicada
El control de la bola se ha realizado mediante el script `PlayerController`.
* **Lógica:** Se utiliza `Input.GetAxis` para capturar la entrada del teclado (flechas o WASD).
* **Física:** En lugar de mover la posición directamente, se aplica una fuerza física al Rigidbody usando `rb.AddForce`. Esto permite que la bola tenga inercia y responda a la gravedad.


## 3. IA del Enemigo: Estados "Lejos" y "Cerca"
Se ha programado una máquina de estados simple dentro del script `EnemigoIA` que funciona de la siguiente manera:
* **Cálculo de Distancia:** Mediante la función `Vector3.Distance`, el cubo mide constantemente la posición de la bola respecto a la suya.
* **Estado LEJOS:** Si la distancia es > 5 unidades, el cubo imprime en consola "Estado: LEJOS" y permanece estático.
* **Estado CERCA:** Si la distancia es < 5 unidades, el cubo cambia su estado a "CERCA" y utiliza `Vector3.MoveTowards` para perseguir al jugador a una velocidad constante.


## 4. Detección de Contacto y Variantes (Debug)
Para el punto de detección de contacto, se ha implementado el método `OnCollisionEnter`:
* **Funcionamiento:** Cuando se detecta que los Colliders de la bola y el cubo se tocan, se lanza un mensaje de **Debug.Log** confirmando el contacto.
* **Variantes de detección:**
     **OnCollisionEnter:** Para choques físicos donde los objetos no se atraviesan.

## 5. Requisitos de Configuración:
Para que todo el sistema funcione correctamente, se han configurado los siguientes detalles en el Inspector:
* **Tags:** La bola tiene asignado el Tag **"Player"** para que el cubo pueda identificarla en el código de colisión.
* **Colliders:** Tanto el cubo como la bola tienen sus Colliders con la opción **Is Trigger desactivada**, permitiendo el choque físico.
* **Asignación de quien persigue a quien:** Se arrastra el scrip del enemigo al cubo y en el insperctor se le añade el objeto Player para que el enemigo persiga a la bola en este caso.

* <img width="1516" height="840" alt="Captura desde 2026-02-20 11-44-32" src="https://github.com/user-attachments/assets/8244ca32-6c2b-4835-ba87-b3700194f1bd" />

