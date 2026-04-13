# GreenTech-MVP-Sostenible
**Autor:** *Jorge Espejo Martínez*

## Informe Ejecutivo: De la "Grasa Digital" al Ecodiseño
Este proyecto contiene la refactorización del MVP de GreenTech Solutions. El objetivo principal era transformar una landing page (página web diseñada para convertir visitantes en clientes o contactos) ineficiente y pesada en un producto digital ligero, rápido y sostenible.

## Problemas encontrados en el codigo original
1. **Frameworks CSS innecesarios (Bootstrap):** se importa Bootstrap entero, pesa cientos de KB, solo para usar un botón. Esto es "grasa digital" porque estamos haciendo que el usuario descargue un montón de código que no se usa.
2. **Librerías JavaScript innecesarias (jQuery, Moment.js):** se importa jQuery para usar $(document).ready() y Moment.js para formatear una fecha. Moment.js es un "anti-patrón de sostenibilidad" porque pesa mucho y el Date nativo de JavaScript puede hacer lo mismo sin librerías externas.
3. **Imagen de fondo gigante:** la imagen de fondo es enorme. Esto hace que la web "tarde horrores en cargar, devora la tarifa de datos de los usuarios y sobrecalienta los procesadores".
4. **Forma de añadir el footer:** se usa JavaScript para poner el footer. Esto es ineficiente y rompe el principio de que el contenido estructural (HTML) debe estar separado del comportamiento (JS).
5. **Uso de fuentes externas:** esto no es el mayor problema, importar una fuente de Google Fonts (Montserrat) con 5 tipos ditintas (100, 300, 400, 700, 900) también añade peso. Se podría optimizar para usar solo los estilos que realmente se necesitan.
6. **No hay lazy loading:** la imagen se carga inmediatamente, aunque el usuario no la vea.

## Refactorización
1. **Eliminar Bootstrap y FontAwesome:** se sustituyen por el estilo visual con CSS nativo.
2. **Optimizar las fuentes:** se sigue utilizando Montserrat, pero solo cargando los estilos que necesitemos (normalmente 400 y 700). Además usaré font-display: swap para que el texto sea visible mientras se carga la fuente, mejorando de esta forma la percepción de velocidad.
3. **Eliminar jQuery y Moment.js:** se usará JavaScript puro (document.addEventListener, Date nativo con Intl.DateTimeFormat).
4. **Optimización de la imagen:** se redimenciona la imagen porque la mayoría de pantallas, posee entre 1920px o 1200px. Por otro lado, se comprime la imagen en un formato mejor como WebP. Finalmente se implementar Lazy Loading para que la imagen carge cuando el usuario se vaya acercando a la imagen.
5. **Mejorar la accesibilidad y estructura:** se usa HTML semántico para el footer, de esta forma se evita utilizar JavaScript.
6. **
Añadir un Meta tag de Cache: Podemos añadir un meta tag para que el navegador cachee los recursos estáticos.
