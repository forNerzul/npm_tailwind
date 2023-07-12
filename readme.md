# Pasos para crear un proyecto con tailwind y npm:

1. `mkdir <carpeta_proyecto>`
2. `cd <carpeta_proyecto>`
3. `npm init` Para inicializar el paquete node.
4. Crear una carpeta `public` en la raíz del proyecto.
5. Dentro de la carpeta `public` crear una carpeta `css`. Esta carpeta va a servir para que nuestro POSTCSS compile css de tailwind ahí.
6. En la raíz del proyecto crear la carpeta `src`.
7. Dentro de la carpeta `src` crear una carpeta `css`.
8. Estando en la raíz del proyecto ejecutar estos comandos en la terminal:
   `npm install -D tailwindcss postcss-cli autoprefixer`
   `npx tailwindcss init`

Esto va a crear un archivo `tailwind.config.js` en el directorio raíz del proyecto.

9. El archivo tailwind.config.js debe quedar asi:

```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./public/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

La linea `content: ["./public/**/*.{html,js}"],` contiene la ruta de nuestros templates o codigo en donde escribamos una clase de tailwind esto es necesario para que tailwind sepa donde estan las clases que tiene que compilar posteriormente.
En nuestro caso como ubicamos nuestros archivos `.html` en la carpeta `./public/`.

10. Agregamos el archivo `main.css` con las siguientes directivas de tailwind:

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

11. En el `package.json` añadimos la siguiente linea en la sección de scripts para indicar el commando para ejecutar postcss con un archivo de entrada (en nuestro caso `./src/css/main.css` y un archivo de salida con todos nuestros estilos a importar en el html `./public/app.css`)

`"watch": "postcss ./src/css/main.css -o ./public/css/app.css --watch"`

12. Creamos un archivo llamado `postcss.config.js` en el directorio raíz del proyecto el cual debe quedar así:

```
module.exports = {
    plugins: {
        tailwindcss: {},
        autoprefixer: {},
    },
};
```

13. Con esto ya podemos ejecutar `npm run watch` en la terminal para compilar los estilos y empezar a usar.
