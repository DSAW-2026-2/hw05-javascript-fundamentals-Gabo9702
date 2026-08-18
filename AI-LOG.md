# ¿Cómo puedo hacer un menú hamburguesa en mi página web?

Paso 1: Crear el botón de la hamburguesa
Primero, necesitas un botón con el icono de las tres rayitas que solo sea visible en pantallas de teléfonos. En Tailwind CSS, logramos esto con la clase md:hidden (que lo oculta en pantallas medianas y grandes).

Agrega este código dentro de tu <header>, justo donde quieres que aparezca el botón:

<!-- Botón Hamburguesa -->
<button id="mobile-menu-btn" type="button" class="md:hidden text-gray-500 hover:text-gray-700 p-2 focus:outline-none">
    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
    </svg>
</button>

Paso 2: Crear el menú desplegable oculto
Ahora necesitamos la lista de enlaces que se va a desplegar hacia abajo. Este contenedor debe estar oculto por defecto usando la clase hidden de Tailwind, y también debe tener md:hidden para asegurar que nunca se vea en la versión de escritorio.

Coloca este código justo debajo de la barra de navegación principal, pero todavía dentro de tu <header>:

<!-- Menú Desplegable Móvil -->
<div id="mobile-menu" class="hidden md:hidden pb-4 px-4">
    <div class="flex flex-col space-y-2 mt-2">
        <a href="#inicio" class="text-gray-600 hover:bg-gray-100 px-3 py-2 rounded-md font-medium">Inicio</a>
        <a href="#caracteristicas" class="text-gray-600 hover:bg-gray-100 px-3 py-2 rounded-md font-medium">Características</a>
        <a href="#equipo" class="text-gray-600 hover:bg-gray-100 px-3 py-2 rounded-md font-medium">Equipo</a>
    </div>
</div>

Paso 3: Darle vida con JavaScript
Finalmente, vamos a usar Vanilla JavaScript para hacer que el botón funcione. La lógica es muy sencilla: cuando el usuario haga clic en el botón de la hamburguesa, le quitaremos o le pondremos la clase hidden al contenedor del menú.

Agrega este código dentro de tu etiqueta <script> al final de tu documento (o en tu archivo .js externo):

JavaScript
// 1. Seleccionamos el botón y el menú usando su ID
const mobileMenuBtn = document.getElementById('mobile-menu-btn');
const mobileMenu = document.getElementById('mobile-menu');

// 2. Le agregamos un "escuchador de eventos" al botón
mobileMenuBtn.addEventListener('click', () => {
    // 3. toggle() alterna la clase 'hidden': 
    // Si el menú la tiene (está oculto), se la quita. Si no la tiene (está visible), se la pone.
    mobileMenu.classList.toggle('hidden');
});
¿Cómo funciona?
Al usar el método classList.toggle('hidden'), nos ahorramos tener que escribir bloques if/else largos. JavaScript se encarga automáticamente de evaluar el estado actual del menú y cambiarlo, haciendo que se despliegue y se contraiga con cada clic.