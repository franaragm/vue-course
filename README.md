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
```

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
  
# Reactividad  

## Declarando el Estado Reactivo
Podemos crear un objeto o array reactivo con la función reactive():

```js
import { reactive } from 'vue
const state = reactive({ count: 0 })
```


Los objetos reactivos son proxies de JavaScript y se comportan igual que los objetos normales. La diferencia es que Vue es capaz de rastrear el acceso a las propiedades y las mutaciones de un objeto reactivo.


```js
<script setup>
import { reactive } from 'vue'

const state = reactive({ count: 0 })

function increment() {
  state.count++
}
</script>

<template>
  <button @click="increment">
    {{ state.count }}
  </button>
</template>
```  

## Tiempo de actualización del DOM
Cuando se muta el estado reactivo, el DOM se actualiza automáticamente. Sin embargo, debe tenerse en cuenta que las actualizaciones del DOM no se aplican de forma sincrónica. En su lugar, Vue las almacena hasta el "siguiente tick" en el ciclo de actualización para asegurar que cada componente se actualiza sólo una vez sin importar cuántos cambios de estado hayas hecho.

Para esperar a que se complete la actualización del DOM después de un cambio de estado, puedes utilizar la API global nextTick():

```js
<script setup>
import { reactive, nextTick } from 'vue'

const state = reactive({ count: 0 })

function increment() {
  state.count++
  nextTick(() => {
    console.log(state.count)
  })
}

</script>

<template>
  <button @click="increment">
    {{ state.count }}
  </button>
</template>
```
  
  
## Reactividad Profunda
En Vue, el estado es “profundamente" reactivo por defecto. Esto significa que puedes esperar que los cambios sean detectados incluso cuando mutes objetos anidados o arrays:

```js
<script setup>
import { reactive } from 'vue'

const obj = reactive({
  nested: { count: 0 },
  arr: ['foo', 'bar']
})

function mutateDeeply() {
  obj.nested.count++
  obj.arr.push('baz')
}

</script>

<template>
  <button @click="mutateDeeply">
    Cambiar
  </button>
  <div>
    {{obj.nested.count}}
  </div>
  <div>
    {{obj.arr}}
  </div>
</template>
```
  
También es posible crear explícitamente objetos reactivos superficiales en los que la reactividad sólo se rastrea en el nivel raíz, pero normalmente sólo se necesitan en casos de uso avanzados.

### Reactive Proxy vs. Original
Es importante tener en cuenta que el valor devuelto por reactive() es un Proxy del objeto original, que no es igual al objeto original:

```js
const raw = {}
const proxy = reactive(raw)

// proxy NO es igual al original.
console.log(proxy === raw) // false
```

Sólo el proxy es reactivo - mutar el objeto original no desencadenará actualizaciones. Por lo tanto, la mejor práctica cuando se trabaja con el sistema de reactividad de Vue es utilizar exclusivamente las versiones proxy de su estado.

Para asegurar un acceso consistente al proxy, llamar a reactive() sobre el mismo objeto siempre devuelve el mismo proxy, y llamar a reactive() sobre un proxy existente también devuelve ese mismo proxy:

```js
// calling reactive() on the same object returns the same proxy
console.log(reactive(raw) === proxy) // true

// calling reactive() on a proxy returns itself
console.log(reactive(proxy) === proxy) // true
```

Esta regla se aplica también a los objetos anidados. Debido a la reactividad profunda, los objetos anidados dentro de un objeto reactivo también son proxies:

```js
const proxy = reactive({})

const raw = {}
proxy.nested = raw

console.log(proxy.nested === raw) // false
```  
  
### Limitaciones de reactive()
La API reactive() tiene dos limitaciones:

Sólo funciona para tipos de objeto (objetos, matrices y tipos de colección como Map y Set). No puede manejar tipos primitivos como string, number o boolean.

Dado que el seguimiento de la reactividad de Vue funciona sobre el acceso a propiedades, debemos mantener siempre la misma referencia al objeto reactivo. Esto significa que no podemos "reemplazar" fácilmente un objeto reactivo porque se pierde la conexión de reactividad con la primera referencia:
Since Vue's reactivity tracking works over property access, we must always keep the same reference to the reactive object. This means we can't easily "replace" a reactive object because the reactivity connection to the first reference is lost:

```js
let state = reactive({ count: 0 })

// la referencia anterior ({ count: 0 }) ya no se rastrea (¡se ha perdido la conexión de reactividad!)
state = reactive({ count: 1 })
```  

También significa que cuando asignemos o desestructuremos una propiedad de un objeto reactivo en variables locales, o cuando pasemos esa propiedad a una función, perderemos la conexión de reactividad:

```js
const state = reactive({ count: 0 })

// n is a local variable that is disconnected
// from state.count.
let n = state.count
// does not affect original state
n++

// count is also disconnected from state.count.
let { count } = state
// does not affect original state
count++

// the function receives a plain number and
// won't be able to track changes to state.count
callSomeFunction(state.count)
```  

### Reactive Variables with ref()
Para hacer frente a las limitaciones de reactive(), Vue también proporciona una función ref() que nos permite crear "refs" reactivas que pueden contener cualquier tipo de valor:

```js
import { ref } from 'vue'

const count = ref(0)
```  

ref() toma el argumento y lo devuelve envuelto dentro de un objeto ref con una propiedad .value:

```js
const count = ref(0)

console.log(count) // { value: 0 }
console.log(count.value) // 0

count.value++
console.log(count.value) // 1
```

Al igual que las propiedades de un objeto reactivo, la propiedad .value de una ref es reactiva. Además, cuando contiene tipos de objeto, ref convierte automáticamente su .value con reactive().

Una ref que contenga un valor de objeto puede sustituir reactivamente al objeto completo:

```js
const objectRef = ref({ count: 0 })

// esto funciona de forma reactiva
objectRef.value = { count: 1 }
```
  
Las referencias también pueden pasarse a funciones o desestructurarse a partir de objetos planos sin perder reactividad:

```js
const obj = {
  foo: ref(1),
  bar: ref(2)
}

// la función recibe una ref
// necesita acceder al valor a través de .value pero
// conservará la conexión de reactividad
callSomeFunction(obj.foo)

// todavía reactivo
const { foo, bar } = obj
```  

En otras palabras, ref() nos permite crear una "referencia" a cualquier valor y pasarla sin perder reactividad. Esta capacidad es bastante importante, ya que se utiliza con frecuencia cuando se extrae la lógica en Composable Functions.

## Ref Unwrapping en plantillas
Cuando se accede a las refs como propiedades de nivel superior en la plantilla, se "desenvuelven" automáticamente, por lo que no es necesario utilizar .value. Aquí está el ejemplo del contador anterior, utilizando ref() en su lugar:

```vue
<script setup>
import { ref } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}
</script>

<template>
  <button @click="increment">
    {{ count }} <!-- no .value needed -->
  </button>
</template>
```

Ten en cuenta que el "desenvolvimiento" sólo se aplica si la referencia es una propiedad de nivel superior en el contexto de representación de la plantilla. Por ejemplo, object es una propiedad de nivel superior, pero object.foo no lo es.

Por lo tanto, dado el siguiente objeto:

```js
const object = { foo: ref(1) }
```  

The following expression will NOT work as expected:

```js
{{ object.foo + 1 }}
```
 
El resultado renderizado será [objet Object] porque object.foo es un objeto ref. Podemos solucionarlo haciendo que foo sea una propiedad de nivel superior:

```js
const { foo } = object

{{ foo + 1 }}
``` 
  
Ahora el resultado del renderizado será 2.

Una cosa a tener en cuenta es que una referencia también se desenvolverá si es el valor final evaluado de una interpolación de texto (es decir, una etiqueta {{ }}), por lo que lo siguiente se representará 1:

```js
{{ object.foo }}
```  

Esto es sólo una característica de conveniencia de la interpolación de texto y es equivalente a {{ object.foo.value }}.

## Ref Unwrapping en Objetos Reactivos
Cuando se accede a una referencia o se muta como una propiedad de un objeto reactivo, también se desenvuelve automáticamente para que se comporte como una propiedad normal:

```js
const count = ref(0)
const state = reactive({
  count
})

console.log(state.count) // 0

state.count = 1
console.log(count.value) // 1
``` 
  
Si se asigna una nueva referencia a una propiedad vinculada a una referencia existente, ésta sustituirá a la anterior:

```js
const otherCount = ref(2)

state.count = otherCount
console.log(state.count) // 2
// original ref is now disconnected from state.count
console.log(count.value) // 1
```  
  
Ref unwrapping only happens when nested inside a deep reactive object. It does not apply when it is accessed as a property of a shallow reactive object.

## Ref Unwrapping en Arrays y Colecciones
A diferencia de los objetos reactivos, no se realiza ningún desenvolvimiento cuando se accede a la referencia como elemento de una matriz reactiva o de un tipo de colección nativa como Map:

```js
const books = reactive([ref('Vue 3 Guide')])
// necesita .value aquí
console.log(books[0].value)

const map = reactive(new Map([['count', ref(0)]]))
necesita .value aquí
console.log(map.get('count').value)
```
