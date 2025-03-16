Ejemplo para Multiversiones:

1. Crear proyectos de Angular normales. Ejemplo: mf-root, mf-seguridad, etc.

2. Instalar en cada proyecto el siguiente paquete como dependencia de desarrollo: https://www.npmjs.com/package/@angular-architects/module-federation (npm i @angular-architects/module-federation -D)

3. Configurar en cada proyecto los puertos y el tipo de proyecto que son. Ejemplo:
	ng g @angular-architects/module-federation --project mf-root --port 4200 --type dynamic-host
	ng add @angular-architects/module-federation --project mf-seguridad --port 4201 --type remote

4. En cada proyecto, por recomendación del Moi, en el archivo webpack.config.js, cambiar los valores de los atributos singleton y strictVersion en false, para que cada uno maneje sus propias versiones de dependencias.

5. En el archivo mf.manifest.json configurar los nombres de las aplicaciones y sus respectivos puertos. Validar estos valores en angular.json y en webpack.config.js.

6. Instalar en los micros (no en el root) el siguiente paquete npm i @angular/elements.

---

Configuraciones personalizadas:

https://www.angulararchitects.io/blog/multi-framework-and-version-micro-frontends-with-module-federation-your-4-steps-guide/

7. Aplicar arquitectura limpia para el encarpetado (presentation, domain, infraestructure, application).

8. Crear un módulo de angular en la carpeta presentation, quitar los atributos standalone y el import del decorador del AppComponent y pasarlos al nuevo módulo creado, donde los providers serán los del app.config.ts.

9. Implementar el DoBoostrap en el módulo, ver ejemplo en el enlace.

10. Hacer esto con todos los micros.

11. Instalar en todos los micros, incluido el root, el siguiente paquete: https://www.npmjs.com/package/@angular-architects/module-federation-tools (npm i @angular-architects/module-federation-tools)

12. Crear los environments.

13. En el archivo boobstrap.ts implementar el método boobstrap de module-federation-tools. Que llama el respectivo módulo {production, appType}. 

14. En el archivo webpack.config.ts en el exposes colocar "./web-components" : "./src/boobstrap.ts". Menos en el root.

15. Configurar las rutas con WebComponetWrapper en el root y que contenga las rutas principales de cada microfrontend.



