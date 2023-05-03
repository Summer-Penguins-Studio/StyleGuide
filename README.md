# Summer Penguins Style Guide

## Índice
* [Guía de Estilo de Proyectos](#guía-de-estilo-de-proyectos)
* [Guía de Estilo de Código](#guía-de-estilo-de-código)

---

## Guía de Estilo de Proyectos
* [Nombrado](#convenciones-de-nombres)
* [Archivos](#archivos)
* [Git](#git)

### Convenciones de Nombres
- **Proyectos:** `PascalCase`
- **Carpetas:** `PascalCase`
- **Assets:** `PascalCase`

Los proyectos que comiencen su desarrollo y aún no tengan un nombre definido se nombrarán bajo el siguiente estándar:
- Su nombre estará compuesto de 2 palabras.
- La primera siempre será Project.
- La segunda será un nombre relacionado con la idea, ya sea un evento del juego, un personaje, un lugar o un concepto.
- Nunca se usará como segunda palabra el nombre de otro juego que sirva como inspiración.

### Archivos
- El repositorio del proyecto estará alojado en [Github](https://github.com), bajo la propiedad de la organización [Summer Penguins](https://github.com/Summer-Penguins-Studio). 
- Dentro del repositorio habrá siempre un archivo Licencia, un README, un gitginore, un GDD y una carpeta game donde se encontrará el proyecto en Unity.
- Opcionalmente podrán existir otras carpetas con información o subproyectos relacionados al proyecto general.
- Dentro del proyecto en Unity se organizarán los Assets siguiendo los estándares propuestos por Unity, tanto de jerarquía como de nombrado. Siempre y cuando no se viole aquí establecido.
- Dentro de la carpeta Scripts el código del proyecto se almacenará en subcarpetas que coincidan con la jerarquía de los namespaces del proyecto.

### Git
**Ramas:** El repositorio remoto, así como los locales, tendrán en todo momento 2 ramas. La rama `main` y la rama `dev` o `develop`. A medida que sea necesario se incluirá la rama `release`. Cada desarrollador debe tener su propia rama, con prefijo `dev-` seguido de un identificador propio del desarrollador.
**Commits:** El estándar de nombrado de los commits será, por el momento, Conventional Commits. Los siguientes tipos de commits son permitidos:
- init: Commit o commits iniciales, para la configuración inicial del proyecto.
- docs: Actualización de la documentación del proyecto, ya sea código o no.
- feat: Implementación de una nueva funcionalidad o trabajo sobre una ya existente.
- fix: Correción de errores.
- style: Cambio en el código puramente estético.
- assets(type): Inclusión o modificación de assets donde type refiere el tipo de asset (sprite, sound, texture, shader, model, etc).
- move: Actualización de repo remoto para hacer un cambio en el lugar de trabajo.

---

## Guía de Estilo de Código
* [Nombrado](#convenciones-de-nombres-1)
* [Formato del Código](#formato-del-código)
* [Comentarios](#comentarios)
* [Documentación](#documentación)

### Convenciones de Nombres

#### Nombres
- **Clases:** deben ser sustantivos en singular.
- **Interfaces:** deben ser adjetivos precedidos por una I mayúscula.
- **Métodos:** deben comenzar con una forma verbal que indique la acción y continuar con el contexto si fuera necesario.
- **Atributos, parámetros y variables:** deben ser sustantivos.
- **Métodos o Atributos Booleanos:** deben comenzar con un verbo con intención de pregunta, que pueda ser contestado con SI o NO (true o false).
- **Enums:** deben ser sustantivos, en singular si son enums regulares o en plurar si son enums bit a bit.
- **Namespaces:** Regularmente deben ser sustantivos e indicar su jerarquía mediante el operador punto (.).

#### Mayúsculas o minúsculas
- **Clases:** `PascalCase`
- **Interfaces:** `PascalCase`
- **Métodos y Atributos Públicos:** `PascalCase`
- **Métodos y Atributos Privados:** `camelCase`
- **Parámetros y variables locales:** `camelCase`
- **Nombres de Enums:** `PascalCase`
- **Valores de Enums:** `SCREAM_SNAKE_CASE`
- **Namespaces:** `PascalCase`

### Formato del Código

#### Propiedades
- **Campo de Respalo:** Siempre debe ser declarado.
- **Solo Lectura:** Colocar solo la instrucción get.
- **Solo Escritura:** Colocar solo la instrucción set.
- **Lectura y Escritura:** Colocar ambos, get y set.

``` C#
public class PlayerHealth
{
    // the private backing field
    private int maxHealth;

    // DON'T USE: read-only, returns backing field, modern syntax
    public int MaxHealth => maxHealth;
    // DON'T USE: private properties
    public int MaxHealth { get; private set; }

    // USE: only get properties, read-only
    public int MaxHealth { get; }
    // USE: only set properties, write-only
    public int MaxHealth { set; }
    // USE: read and write properties
    public int MaxHealth { get; set; }
}
```

#### Llaves y Estilo de Indentación
- **Indentación:** [Allman Style](https://en.wikipedia.org/wiki/Indentation_style#Allman_style), colocar la llave de apertura en una nueva línea.
- **Llaves:** No omitir las llaves bajo ningún concepto, ya sea en instrucciones de una sola línea o en instrucciones multilínea anidadas.

``` C#
// Allman Style
void DisplayMouseCursor(bool showMouse)
{
    if (!showMouse)
    {
        Cursor.lockState = CursorLockMode.Locked;
        Cursor.visible = false;
    }
}
```

``` C#
// Bracers
// DON'T USE: Single line statement
for (int i = 0; i < 100; i++) { DoSomething(i); }
// DON'T USE: Single line statement without bracers
for (int i = 0; i < 100; i++) 
    DoSomething(i);
// USE: always maintain the bracers
for (int i = 0; i < 100; i++)
{
    DoSomething(i);
}
```

#### Switch
- **Consistencia:** No violar nada de lo antes establecido.
- **Líneas**: Usar una línea para cada instrucción, una para el case, otra para las instrucciones necesarias y una final para el break.
- **Indentación:** Cada case y el default deberá ser indentado 4 espacios por delante del switch.
``` C#
switch (someExpression)
{
    case 0:
        DoSomething();
        break;
    case 1:
        DoSomethingElse();
        break;
    case 2:
        int n = 1;
        DoAnotherThing(n);
        break;
}
```
#### Espacios Horizontales
- Añadir espacios para disminuir la densidad del código.
``` C#
// USE: required spaces
for (int i = 0; i < 100; i++) { DoSomething(i); }
// DON'T USE: no spaces
for(inti=0;i<100;i++){DoSomething(i);}
```
- Usar un solo espacio después de la coma entre cada argumento o parámetro en una función.
- No usar espacios entre una función y sus paréntesis.
``` C#
// USE: single space after comma between arguments
CollectItem(myObject, 0, 1);
// DON'T USE: no spaces
CollectItem(myObject,0,1);
//DON'T USE: spaces before or after a method parenthesis
CollectItem( myObject,0,1);
CollectItem (myObject,0,1);
```
- No usar espacios dentro de corchetes.
``` C#
// USE: omit spaces inside brackets
x = dataArray[index];
// DON'T USE:
x = dataArray[ index ];
```
- Usar espacios antes de la condiciones de flujo de control
- Usar espacios antes y después de cada operador de comparación o asignación.
``` C#
// USE: space before condition; separate parentheses with a space.
while (x == y)
// DON'T USE:
while(x==y)
```

#### Saltos de Línea
- Agrupa secciones de código dependientes o similares.
- Separa cada método por un salto de línea.
- Separa distintas partes del código con 2 saltos de línea (Después de las directivas `using`).
- Separa distintas partes del código con 1 salto de línea.
- Usa 1 salto de línea dentro de métodos para mejorar la legibilidad del código.

#### Orden del Archivo
1. Directivas using del sistema
2. Directivas using custom
2. Declaración de los namespaces
3. Declaración de la Clase, Interfaz, Enum, etc
4. Atributos Públicos
5. Atributos Privados
6. Propiedades
7. Métodos Monobehaviour
8. Métodos Públicos
9. Métodos Privados

### Comentarios
- Coloca los comentarios en su propia línea, no al final de una línea de código.
- Una variable o método bien nombrada no requiere un comentario que la explique.
- Para los SerializedFields usa Tooltips en lugar de comentarios. Esto no solo aclara el código, sino que permite visualizar la descripción en el inspector.
``` C#
[Tooltip(“The amount of side-to-side friction.”)]
[SerializedField] public float Grip;
```
- Usa un espacio entre el inicio del comentario (//) y el texto.
- Comienza todos los comentarios con mayúscula a menos que la primera palabra refiera a una variable o método que esté declarada con minúscula.

### Documentación