# Bienes raíces

Proyecto para visualizar la lista de propieades guardadas.
https://real-estates-project.herokuapp.com/

## Configuración

```bash
# Instalar dependencias
$ npm install

# Ejecutar el servidor en modo desarrollador
$ npm run dev

# Crear un paquete para publicar en producción
$ npm run build
$ npm run start
```

Para obtener mas detalle, consulte la [documentación](https://nuxtjs.org).

## Consideraciones especiales

Dada la estructura de las especificaciones de [diseño](https://www.figma.com/file/sW5Z8Y3pHim5OYIAAvRtd9/Prueba-T%C3%A9cnica?node-id=5%3A17) se requiero crear las siguientes adiciones a los estilos de Tailwind:

- Se adiciona los colores **jungle (_#012D26_)**, **jungle-gray (_#5B6866_)**, **caribbean (_#3ECFAF_)**, **md-blue (_#EBEDFF_)**, **blue-sky (_#3948FF_)** y **gray-light (_#E5F0EE_)**, ya que los mismo no se encuentran disponibles en las paletas de colores
- Se adiciona los tamaños ancho porcentuales **5/4 (_125%_)** y **6/4 (_150%_)**, igualmente los espacios de margenes porcetuales y negativos **-1/4 (_-25%_)** y **-3/10 (_-30%_)** para poder manejar las ubicaciones de las imagenes en las tarjetas de imagenes, dado que dichos valores no se incluyen.
- Se adiciona el tamaño de relleno porcentual \**15/100 (*15%\*) para ordenar la ubicación del numeral que indica las propiedades restantes en las tarjetas de imagenes, aplicando solo en las tarjetas que incluyen 3 o más imagenes, dado que valor no se incluye.
- Se adiciona el tamaño máxiomo de ancho **18.25 (_18.25rem_)** para controlar el tamaño máximo de las tarjetas de imagenes, dado que dicho tamaño no se incluye.
