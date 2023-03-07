## JavaScript esencial para usar en VUE

Para utilizar Vue3 con Composition API y ```<script setup>```, es necesario tener una comprensión básica de JavaScript y la sintaxis de Vue. A continuación se detallan los principales conceptos de JavaScript que se necesitan para utilizar Vue3 con Composition API y ```<script setup>```:

**Declaración de variables y constantes**: Se utilizan para almacenar datos. En Vue3, se recomienda utilizar constantes para las variables reactivas.

**Funciones**: Se utilizan para ejecutar acciones y realizar cálculos. Las funciones son necesarias para definir los hooks de Vue, como onMounted y watchEffect.

**Arrow functions**: Son una forma abreviada de definir funciones en JavaScript. Son especialmente útiles para definir funciones en línea, como en los hooks de Vue.

**Objetos**: Son estructuras de datos que se utilizan para almacenar información. En Vue3, se utilizan objetos para definir el estado del componente.

**Spread operator**: Es una sintaxis que se utiliza para expandir un objeto o una matriz en un nuevo objeto o matriz. En Vue3, se utiliza el spread operator para combinar múltiples objetos y proporcionar propiedades a los componentes.

**Destructuring**: Es una sintaxis que se utiliza para extraer propiedades de un objeto o elementos de una matriz en variables separadas. En Vue3, se utiliza la destructuración para acceder a las propiedades del estado del componente.

**Importación y exportación de módulos**: Es una sintaxis que se utiliza para importar y exportar código de otros archivos. En Vue3, se utilizan las importaciones y exportaciones para modularizar el código y facilitar su reutilización.

**Template literals**: Es una sintaxis que se utiliza para definir cadenas de texto con interpolación de variables. En Vue3, se utilizan los template literals para definir los templates de los componentes.

Con estos conceptos básicos de JavaScript en mente, podemos empezar a utilizar Vue3 con Composition API y ```<script setup>```. Para ello, se debe escribir el código en un archivo .vue y utilizar la siguiente sintaxis:

```js
<template>
  <!-- El template del componente -->
</template>

<script setup>
  // Aquí se define el estado del componente y los hooks
</script>
````

Dentro de la sección ```<script setup>```, se pueden definir las variables reactivas, los hooks de Vue y las funciones del componente. Por ejemplo:

```js
<template>
  <button @click="increment">
    +
  </button>
  <div>{{ count }}</div>
</template>

<script setup>
  import { ref, onMounted, watchEffect } from 'vue'

  const count = ref(0)

  function increment() {
    count.value++
  }

  onMounted(() => {
    console.log('El componente se ha montado')
  })

  watchEffect(() => {
    console.log(`El contador tiene el valor ${count.value}`)
  })

</script>
````

En este ejemplo, se importa la función ref de Vue y se utiliza para definir la variable count como una variable reactiva con valor inicial 0. Luego, se define la función increment que incrementa el valor de count. Además, se utilizan los hooks de Vue onMounted y watchEffect para imprimir mensajes en la consola cuando el componente se monta y cuando count cambia de valor.

## Sitios de interés

### [Documentación Oficial](https://vuejs.org/guide/introduction.html)
### [Playgound SFC](https://sfc.vuejs.org/)
### [Vue DevTools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd?hl=es) 

## Explicación básica de la diferencia entre Composition API y Options API(Seguiremos incidiendo en esto)

Vue.js es un framework de JavaScript que ofrece varias opciones para la definición de componentes. En particular, existen dos formas principales de definir componentes en Vue: mediante la Options API y mediante la Composition API con script setup.

La Options API es la forma "tradicional" de definir componentes en Vue. En este enfoque, se define un objeto de opciones que especifica las propiedades, métodos, hooks de ciclo de vida y otros detalles del componente. Por ejemplo, aquí hay un ejemplo de un componente de Vue definido utilizando la Options API:

```js
<template>
  <div>{{ message }}</div>
</template>

<script>
export default {
  data() {
    return {
      message: '¡Hola, mundo!'
    }
  }
}
</script>
```

Por otro lado, la Composition API con script setup es una forma más moderna y flexible de definir componentes en Vue. En lugar de definir un objeto de opciones, el componente se define como una función que utiliza una serie de "hooks" para especificar las propiedades, métodos, hooks de ciclo de vida y otros detalles del componente. Aquí hay un ejemplo de cómo se define un componente utilizando la Composition API con script setup:

```js
<template>
  <div>{{ message }}</div>
</template>

<script setup>
import { ref } from 'vue';

const message = ref('¡Hola, mundo!');

</script>
```

En este ejemplo, la sintaxis ```<script setup>``` se utiliza para definir el estado del componente mediante la creación de un objeto reactivo utilizando la función ```ref()```


La sintaxis ```<script setup>``` es una forma más concisa y legible de definir componentes en Vue. Permite definir el estado, las propiedades computadas, los métodos y los hooks de ciclo de vida en una sección de código separada, lo que hace que el código sea más fácil de leer y mantener. Además, la sintaxis ```<script setup>``` se integra bien con las herramientas de compilación modernas como Vite y permite la carga diferida de código para una mejor eficiencia del rendimiento.

Una de las principales ventajas de la Composition API con script setup es que permite una mejor organización del código y una reutilización más fácil de la lógica del componente. Además, la Composition API facilita la creación de componentes más pequeños y modulares, lo que puede mejorar el rendimiento y la capacidad de mantenimiento de la aplicación.

En resumen, la Options API es una forma más tradicional de definir componentes en Vue, mientras que la Composition API con script setup es una forma más moderna y flexible. La Composition API facilita la reutilización del código y la organización del mismo, lo que puede hacer que el desarrollo de componentes sea más fácil y rápido.

Vue3 admite las dos APIs, aunque es aconsejable usar la Composition API.

# Aspectos fundamentales en VUE

## Sintaxis de plantilla

### Text Interpolation

La forma más básica de vinculación de datos es la interpolación de texto utilizando la sintaxis "Mustache" (llaves dobles):

```js
<script setup>
import { ref } from 'vue'

const firtsName = "Lebron"
const lastName = "James"

</script>

<template>
<p>Name: {{ firtsName }}</p>
<p>Last: {{ lastName }}</p>


</template>

```js

La etiqueta mustache se sustituirá por el valor de las propiedades de la instancia del componente correspondiente. También se actualizará cada vez que cambie la propiedad msg (Reactividad)

### Attribute Bindings
Enlaces de atributos

La etiqueta mustache no pueden utilizarse dentro de atributos HTML. En su lugar, usamos una **directiva v-bind**:

```js
<script setup>
import { ref } from 'vue'
const dynamicId = ref('my_id')

</script>

<template>
<div :id="dynamicId"></div>
</template>
``` 

La **directiva** v-bind indica a Vue que mantenga el atributo id del elemento sincronizado con la propiedad dynamicId del componente. Si el valor vinculado es nulo o indefinido, el atributo se eliminará del elemento renderizado.

### Atributos booleanos
Los atributos booleanos son atributos que pueden indicar valores verdadero / falso mediante su presencia en un elemento. Por ejemplo, disabled es uno de los atributos booleanos más utilizados.

v-bind funciona de forma un poco diferente en este caso:

```js
<script setup>
import { ref } from 'vue'
const isButtonDisabled = ref(true)

</script>

<template>
<button :disabled="isButtonDisabled">Button</button>
</template>
```

El atributo disabled se incluirá si isButtonDisabled tiene un valor verdadero. También se incluirá si el valor es una cadena vacía, manteniendo la coherencia con <button disabled="">. Para otros valores falsos, el atributo se omitirá.

### Uso de expresiones JavaScript

Hasta ahora sólo hemos estado vinculando a simples claves de propiedad en nuestras plantillas. Pero Vue realmente soporta todo el poder de las expresiones JavaScript dentro de todos los enlaces de datos:

```js
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div :id="`list-${id}`"></div>
```

Estas expresiones se evaluarán como JavaScript en el ámbito de datos de la instancia actual del componente.

En las plantillas Vue, las expresiones JavaScript pueden utilizarse en las siguientes posiciones:

1) Dentro de interpolaciones de texto (moustaches)
2)En el valor de atributo de cualquier directiva Vue (atributos especiales que empiezan por v-)

### Sólo expresiones
Cada enlace sólo puede contener una única expresión. Una expresión es un fragmento de código que puede evaluarse para obtener un valor. Una simple comprobación es si se puede utilizar después del retorno.

Por lo tanto, lo siguiente NO funcionará:

```js
<!-- esto es un stament(afirmación), no una expresión: -->
{{ var a = 1 }}

<!-- el control de flujo tampoco funcionará, debemos usar expresiones ternarias -->
{{ if (ok) { return message } }}
```

## Directivas
Las directivas son atributos especiales con el prefijo v-. Vue proporciona una serie de directivas incorporadas, incluyendo v-html y v-bind que hemos visto antes.

Se espera que los valores de los atributos de las directivas sean expresiones JavaScript simples (con la excepción de v-for, v-on y v-slot, que veremos más adelante). El trabajo de una directiva es aplicar reactivamente actualizaciones al DOM cuando cambia el valor de su expresión. Tomemos v-if como ejemplo:

```js
<script setup>
import { ref } from 'vue'
const seen = ref(true)

</script>

<template>
<p v-if="seen">Me ves</p>
<p >{{ seen ? 'Me ves' : 'No me ves'}}</p>

</template>
```



