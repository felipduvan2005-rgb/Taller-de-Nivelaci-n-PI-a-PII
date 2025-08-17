# Taller-de-Nivelaci-n-PI-a-PII

# Objetivos del Taller 

# Introducción a Markdown.

Markdown es un lenguaje de marcado ligero que permite dar formato a texto plano de manera sencilla.

Se utiliza principalmente para crear documentos de texto estructurados, como archivos README en GitHub, blogs, foros y 

documentación técnica.

# Introduccion a Git. 
Git es un sistema de control de versiones distribuido que permite registrar y administrar los cambios en archivos y 

proyectos a lo largo del tiempo. 

Fue creado por Linus Torvalds en 2005, principalmente para el desarrollo del núcleo de Linux, y hoy es una de las 

herramientas más usadas en el mundo de la programación.

# Parte Teorica 

# ¿Que es markdown?

Markdown es un lenguaje de marcado ligero que permite dar formato a texto plano usando una sintaxis simple. 

Es usado principalmente en documentación, README de GitHub y foros.

# GIT:

## 1. ¿Qué es un repositorio en Git y diferencia con un proyecto “normal”?

Un repositorio en Git es una carpeta que guarda todos los archivos de un proyecto junto con el historial de cambios.  

La diferencia con un proyecto normal es que el repositorio guarda versiones, ramas, commits y permite colaboración.

## 2. Tres áreas principales de Git

1. **Working Directory:** Carpeta de trabajo donde editas los archivos.

2. **Staging Area (Index):** Zona temporal donde agregas cambios con `git add`.

3. **Repository:** Base de datos interna de Git donde se guardan los commits.

## 3. Representación interna en Git

1. **Blob:** Contenido de archivos.

2. **Tree:** Estructura de carpetas.

3. **Commit:** Registro de cambios con mensaje, autor y fecha.

4. **Tag**: Marca especial para versiones.

## ¿Cómo se crea un commit y qué información almacena un objeto commit?

Un commit en Git es como una “foto” del estado de tu proyecto en un momento específico.

Se utiliza para guardar los cambios confirmados en el repositorio y forma parte del historial del proyecto.

Cómo se crea un commit

1. Agregar cambios al área de staging (índice):

**git add nombre_del_archivo**

 o para agregar todos los archivos modificados:

**git add .**

2. Confirmar los cambios con un mensaje descriptivo:

**git commit -m "Descripción clara de los cambios"**

## Información que almacena un objeto commit ##

1. Cada commit contiene:

2. Hash único (SHA-1): Identificador irrepetible del commit.

3. Autor: Nombre y correo electrónico del autor del cambio.

4. Fecha y hora: Momento exacto en que se creó el commit.

5. Mensaje: Descripción breve de lo que se cambió.

6. Referencias al commit padre: Para saber en qué estado se basó.

7. Snapshot (instantánea): Puntero a los objetos tree y blob que representan el contenido de los archivos en ese momento.

## 5. Diferencia entre git pull y git fetch

**git fetch:** Descarga cambios pero no los fusiona.

**git pull:** Descarga y fusiona automáticamente.

## 6. Rama (branch) en Git

Es una línea de desarrollo independiente. 

Git gestiona punteros a commits para permitir cambios sin afectar la rama principal.

## 7. Como se realiza un merge

git checkout rama-principal   # Cambiar a la rama de destino

git merge rama-secundaria     # Unir cambios de la rama secundaria

## Que conflictos pueden surgir

Ocurren cuando dos ramas modifican la misma línea de un archivo o cambian un archivo de forma incompatible.

## Cómo se resuelven:

Git marca los archivos en conflicto **(<<<<<<<, =======, >>>>>>>)**.

Editas el archivo para dejar la versión correcta.

Guardas los cambios, agregas al staging **(git add archivo)**, y confirmas **(git commit)**.

## 8. ¿Cómo funciona el área de staging (git add) y qué pasa si se omite este paso?

El área de staging o index en Git es como una "sala de espera" para los cambios que quieres guardar en tu próximo commit.

Cuando editas un archivo en tu proyecto, esos cambios primero ocurren en tu working directory (carpeta de trabajo).

Con el comando:

**git add archivo.txt**

mueves ese archivo al área de staging, indicándole a Git que esos cambios específicos se incluirán en el próximo commit.

Si omites este paso y haces directamente:

**git commit**

Git no guardará esos cambios, porque no fueron agregados al área de staging.

Este sistema te permite decidir qué cambios quieres confirmar y cuáles no, incluso dentro del mismo archivo.

## 9. ¿Qué es el archivo .gitignore y cómo influye en el seguimiento de archivos?

El archivo .gitignore es un listado de rutas, nombres o patrones de archivos que Git debe ignorar.

Se usa para evitar que se rastreen archivos que no son relevantes para el repositorio, como:

1. Archivos temporales ***(*.tmp, *.log)*** 

2. Configuraciones locales **(.vscode/, .idea/)**

3. Archivos binarios generados ***(*.class, *.exe)***

4. Dependencias que se pueden volver a descargar **(node_modules/, vendor/)**

Ejemplo de **.gitignore** para un proyecto Java:

**.class**

**.idea/**

**.vscode/**

**out/**

Esto ayuda a mantener el repositorio limpio y evita subir información innecesaria o sensible.

## 10. ¿Cuál es la diferencia entre un commit --amend y un nuevo commit?

**Nuevo commit**: Cada vez que ejecutas **git commit -m "mensaje"**, Git crea un nuevo registro en el historial con un ID 

único **(hash)**, incluso si el cambio fue pequeño.

**git commit --amend**: Permite modificar el último commit sin crear uno nuevo.

**Se usa para**:

Corregir el mensaje del último commit.

Agregar archivos que olvidaste incluir.

**Ejemplo**:

**git add archivo_olvidado.java**

**git commit --amend -m "Mensaje corregido"**

## 11. ¿Cómo se utiliza git stash y en qué escenarios es útil?

git stash guarda temporalmente tus cambios no confirmados para que puedas trabajar en otra cosa sin perder tu progreso.

Escenario típico:

1. Estás trabajando en una nueva funcionalidad.

2. Necesitas cambiar de rama para resolver un error urgente.

3. Usas:

**git stash**

y Git guarda esos cambios en una pila interna y deja tu carpeta limpia.

4. Luego, para recuperarlos:

**git stash pop**

Es útil para cambiar de contexto rápido sin tener que hacer un commit incompleto.

## 12.¿Qué mecanismos ofrece Git para deshacer cambios?

Git tiene varios métodos, cada uno con un propósito distinto:

**git reset**: Mueve la rama a un commit anterior, borrando commits recientes de forma local.

**git revert**: Crea un nuevo commit que revierte los cambios de uno anterior (seguro en repositorios compartidos).

**git checkout**: Restaura un archivo a su estado en un commit específico o en HEAD (último commit).

**git restore**: (versión moderna de checkout para restaurar archivos).

Ejemplo para restaurar un archivo:

**git checkout -- archivo.txt**

## 13. ¿Cómo funciona la configuración de remotos (origin, upstream) y qué comandos uso para gestión de forks?

En Git, un remoto es una referencia a un repositorio que está alojado en otra ubicación **(como GitHub)**.

Los más comunes son:

**origin**: Es el repositorio principal donde trabajas.

**upstream**: Es el repositorio original del cual hiciste un fork.

Comandos útiles:

**git remote add origin URL_REPO   # Agrega un remoto principal**

**git remote add upstream URL_REPO # Agrega el remoto del que hiciste fork**

**git remote -v                    # Lista remotos**

**git fetch upstream               # Trae cambios del remoto original**

**git merge upstream/main          # Fusiona esos cambios en tu rama local**

## 14. ¿Cómo puedo inspeccionar el historial de commits?

Git ofrece varios comandos para revisar el historial:

git log: Lista los commits con autor, fecha y mensaje.

git diff: Muestra los cambios línea por línea entre commits.

git show <hash>: Muestra el contenido y cambios de un commit específico.

Ejemplo:

**git log --oneline --graph --decorate --all**

## 15. ¿Cuáles son los tipos de datos primitivos en Java?

Java tiene 8 tipos de datos primitivos, que son los más básicos y no son objetos:

1. byte → Entero pequeño (-128 a 127).

2. short → Entero más amplio (-32,768 a 32,767).

3. int → Entero estándar.

4. long → Entero muy grande.

5. float → Decimal de precisión simple.

6. double → Decimal de precisión doble.

7. char → Un solo carácter Unicode.

8. boolean → true o false.

## 16. ¿Cómo funcionan las estructuras de control de flujo en Java?

Las estructuras de control permiten tomar decisiones y repetir instrucciones:

1. **if / else**: Ejecuta un bloque si la condición es verdadera; de lo contrario, otro bloque.

2. **switch**: Selección múltiple basada en el valor de una variable.

3. **for**: Repite un bloque un número fijo de veces.

4. **while**: Repite mientras la condición sea verdadera.

5. **do-while**: Igual que while, pero se ejecuta al menos una vez.

## 17. ¿Por qué es importante usar nombres significativos para variables y métodos?

Usar nombres descriptivos mejora:

1. **Legibilidad**: Facilita entender el código.

2. **Mantenimiento**: Más fácil corregir o ampliar funciones.

3. **Colaboración**: Otros desarrolladores entienden el propósito rápidamente.

## 18. ¿Qué es la Programación Orientada a Objetos (POO)?

Es un paradigma que organiza el código en objetos, los cuales agrupan datos (atributos) y comportamientos (métodos).

Su objetivo es modelar problemas del mundo real y facilitar la reutilización de código.

**Ventajas**:

Reutilización de código.

Mayor modularidad.

Facilidad para escalar proyectos.

## 19. ¿Cuáles son los cuatro pilares de la POO?

1. **Abstracción**: Ocultar la complejidad y mostrar solo lo necesario.

2. **Encapsulamiento**: Proteger los datos internos usando modificadores de acceso.

3. **Herencia**: Permitir que una clase use atributos/métodos de otra.

4. **Polimorfismo**: Usar una misma interfaz para diferentes comportamientos.

## 20.¿Qué es la herencia en POO y cómo se utiliza en Java?

La herencia permite crear nuevas clases basadas en clases existentes, reutilizando código y facilitando modificaciones.

En Java, se implementa con **extends.** 

## 21. ¿Qué son los modificadores de acceso y cuáles son los más comunes en Java?

Controlan quién puede acceder a un atributo o método:

1. **public**: Accesible desde cualquier lugar.

2. **private**: Solo dentro de la clase.

3. **protected**: Desde la misma clase, subclases y mismo paquete.

4. **default (sin palabra clave)**: Solo dentro del mismo paquete.

## 22. ¿Qué es una variable de entorno y por qué son importantes?

Una variable de entorno es un valor definido en el sistema operativo que influye en la ejecución de programas.

En Java, se usan para:

1. Definir la ubicación del compilador **(JAVA_HOME)**.

2. Configurar rutas de librerías.

3. Establecer configuraciones sin modificar el código.

# Calculadora basica

print("=== Calculadora Básica ===")
print("Operaciones disponibles: ")
print("1. Suma")
print("2. Resta")
print("3. Multiplicación")
print("4. División")

opcion = int(input("Seleccione una operación (1-4): "))
num1 = float(input("Ingrese el primer número: "))
num2 = float(input("Ingrese el segundo número: "))

if opcion == 1:
    print("Resultado:", num1 + num2)
elif opcion == 2:
    print("Resultado:", num1 - num2)
elif opcion == 3:
    print("Resultado:", num1 * num2)
elif opcion == 4:
    if num2 != 0:
        print("Resultado:", num1 / num2)
    else:
        print("Error: No se puede dividir entre cero.")
else:
    print("Opción inválida.")
# Contar vocales y consonantes

palabra = input("Ingrese una palabra en minúsculas: ")

vocales = "aeiou"
contador_vocales = 0
contador_consonantes = 0

for letra in palabra:
    if letra in vocales:
        contador_vocales += 1
    else:
        contador_consonantes += 1

print("Número de vocales:", contador_vocales)
print("Número de consonantes:", contador_consonantes)

# Pograma para invertir una cadena de texto

print("=== Inversor de Cadenas ===")

texto = input("Ingrese una cadena de texto: ")

texto_invertido = texto[::-1]

print("\n--- Resultados ---")
print("Texto original :", texto)
print("Texto invertido:", texto_invertido)

print("\nCadena invertida carácter por carácter:")
for letra in texto_invertido:
    print(letra, end=" ")
print("\n")

if texto == texto_invertido:
    print("La cadena es un PALÍNDROMO (se lee igual al derecho y al revés).")
else:
    print("La cadena NO es un palíndromo.")

print("Número de caracteres en el texto:", len(texto))






- 
