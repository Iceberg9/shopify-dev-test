# Prueba de Desarrollo para Shopify
## Documentación
- Shopify Theme Kit - [Shopify Theme Kit](https://shopify.github.io/themekit/)
- Liquid Reference - [Liquid reference · Shopify Help Center](https://help.shopify.com/en/themes/liquid)
- Shopify Theme Layouts Reference - [Theme layouts · Shopify Help Center](https://help.shopify.com/en/themes/development/layouts)
- Shopify Theme Templates - [Theme templates · Shopify Help Center](https://help.shopify.com/en/themes/development/templates)
- Shopify Theme Sections - [Theme sections · Shopify Help Center](https://help.shopify.com/en/themes/development/sections)

## Tips
- Se recomienda leer detalladamente la documentación para el entendimiento de la estructura de diseño de plantillas de Shopify.
- Se provee documentación de Theme Kit, la herramienta para poder trabajar de forma local que se conecta al servidor de Shopify. 
- Para lograr esta prueba prestar especial atención a: **Shopify Theme Templates, Shopify Theme Sections, Liquid Reference.**


## Brief
Se provee un template en blanco, sin diseño de ningún tipo, pero si con la estructura básica detallada en [Building themes · Shopify Help Center](https://help.shopify.com/en/themes/development). **La prueba consiste en el desarrollo de la parte visual y algunas características técnicas de la página de inicio de una tienda Shopify** considerando solo lo siguiente:

- Static Section - Header
- Dynamic Section - Collection List
- Dynamic Section - Featured Product
- Static Section - Footer

> Importante: solo se hará la página principal, las otras secciones deben permanecer sin diseño. Considera que el Header y el Footer conservan su estilo a lo largo del sitio.

Se provee la referencia visual pero queda libre a interpretación el ajuste de espacios para las distintas resoluciones, no buscamos pixel perfect, buscamos diseño responsivo.

La maqueta a seguir para versión desktop y movil es la siguiente:
[Sketch Cloud - Maqueta](https://sketch.cloud/s/D84ne)

Los assets los encuentras en este mismo repositorio.

## Requerimientos
La siguiente lista de requerimientos deben cumplirse para que consideremos la prueba terminada y lista para revisión:

### Github y ambiente de desarrollo
Necesitas hacer un fork de este repositorio para que lo tengas en tu cuenta GitHub y ahí trabajar en branches cada requerimiento.

El ambiente que vas a trabajar es el de desarrollo, por lo tanto necesitas correr en tu consola el comando correspondiente de theme kit:
`theme watch --env=dev`

### Fuente
El sitio entero debe tener https://fonts.google.com/specimen/Raleway 

### Iconos
Todos los iconos deben usarse en formato SVG. El template trae precargado una librería en la carpeta *snippets*.

Para hacer uso de los iconos es necesario usar la etiqueta *include*, por ejemplo:
`{% include 'icon-cart' %}`


### Static Section - Header

- La hamburguesa debe funcionar de la misma forma en desktop como en mobile, ademas de mostrar el menu seleccionado en la configuración del  *Section Header*.
- El logotipo debe poderse cambiar con el *image-picker* disponible en la configuración del *Section Header*.


### Dynamic Section - Collection list
- El titulo, así como las colecciones deben responder a los bloques dinamicos del section.
- Mediante el uso del grid del template, si existen 5 bloques, que la distribución sea: Primera Fila de 3 columnas | Segunda Fila de 2 columnas.


### Dynamic Section - Featured product
- El titulo, así como el producto completo, debe responder al control del section.
- Mostrar la imagen destacada `{{ product.featured_image }}` del producto.
- Crear un componente que permita incrementar / decrementar la cantidad del input tomando en cuenta lo siguiente:
	- No debe poderse escribir 0
	- El numero máximo a escribir debe ser el la cantidad de inventario disponible `{{ variant.inventory_quantity }}`
	- En caso de llegar al máximo arrojar un mensaje con alert.
- Al dar click en *Add to cart* debe agregarlo al carrito y llevarme a la página de /cart.


### Static Section - Footer
- Seguir lineamientos de diseño de la maqueta.


### Entrega
Una vez tengas listo los ajustes, debes realizar deploy completo de tu versión del theme a el ambiente de desarrollo.

`theme deploy --env=dev`

Posterior a esto, hacer un pull request a nuestro repositorio original sobre la rama `test`.

Finalmente enviar un email para confirmar que finalizaste la prueba y esta lista para revisión a alan@iceberg9.mx
