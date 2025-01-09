<!-- Codigo J-S -->

<script>

  import { onMount } from "svelte";

  onMount(() => {
    if (window.location.pathname !== "/") {
      window.location.href = "/";
    }
  });

  window.onload = function() {
  // Número de teléfono para WhatsApp
  var phoneNumber = "+5491127161950"; 
  var prewrittenMessage = "¡Hola! Estoy interesado en saber más sobre los pistachos de La Rioja.";
  var encodedMessage = encodeURIComponent(prewrittenMessage);
  var emailAddress = "info@pistachosriojanos.com"; 
  
  var instagramLink = document.getElementById("instagram-link");
  var whatsappLink = document.getElementById("whatsapp-link");
  var gmailLink = document.getElementById("gmail-link");
  
  var isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
  
  if (isMobile && !/iPad/i.test(navigator.userAgent)) {
    whatsappLink.href = "https://wa.me/" + phoneNumber + "?text=" + encodedMessage;
    instagramLink.href = "instagram://user?username=pistachosriojanos";
    gmailLink.href = "mailto:" + emailAddress + "?subject=Mas Informacion&body=" + encodedMessage;
  } else {
    whatsappLink.href = "https://web.whatsapp.com/send?phone=" + phoneNumber + "&text=" + encodedMessage;
    instagramLink.href = "https://www.instagram.com/pistachosriojanos";
    gmailLink.href = "https://mail.google.com/mail/?view=cm&fs=1&to=" + emailAddress + "&su=Mas%20Informacion&body=" + encodedMessage;
  }
};

import { Router, Route, Link } from 'svelte-routing';
import Inicio from './components/Inicio.svelte';
import AcercaDeNosotros from './components/AcercaDeNosotros.svelte';
import AcercaDelPistacho from './components/AcercaDelPistacho.svelte';
import UltimasNoticiasDelPistacho from './components/UltimasNoticiasDelPistacho.svelte';
import ResposabilidadSocialEmpresarial from './components/ResposabilidadSocialEmpresarial.svelte';
import NuestraGente from './components/NuestraGente.svelte';

let menuVisible = false;

  function toggleMenu() {
    menuVisible = !menuVisible;
  }
</script>

<!-- Codigo HTML -->

<body>
  <main>
    <!-- Header -->
    <div class="header"> 
      <img
        src="./images/Logo-Pistachos.png"
        alt="Logo-Pistachos-Riojanos" 
      />
    </div> 
    
     <!-- Botón de menú en dispositivos pequeños -->
     <button class="menu-btn" on:click={toggleMenu}>
        ☰
      </button>

    <Router>
      <!-- Menú de navegación -->
      <nav class={menuVisible ? 'menu visible' : 'menu'}>
        <ul>
          <li><a href="#" on:click="{() => window.location.reload()}">Inicio</a></li>
          <li><Link to="/acerca-de-nosotros"><a href="/acerca-de-nosotros">Acerca de Nosotros</a></Link></li>
          <li><Link to="/acerca-del-pistacho"><a href="/acerca-del-pistacho">Acerca del Pistacho</a></Link></li>
          <li><Link to="/ultimas-noticias-del-pistacho"><a href="/ultimas-noticias-del-pistacho">Ultimas Noticias del Pistacho</a></Link></li>
          <li><Link to="/responsabilidad-social-empresarial"><a href="/responsabilidad-social-empresarial">Responsabilidad Social Empresarial</a></Link></li>
          <li><Link to="/nuestra-gente"><a href="/nuestra-gente">Nuestra Gente</a></Link></li>
        </ul>
      </nav>
    
      <!-- Las rutas definidas -->
      <Route path="/" component={Inicio} />
      <Route path="/acerca-de-nosotros" component={AcercaDeNosotros} />
      <Route path="/acerca-del-pistacho" component={AcercaDelPistacho} />
      <Route path="/ultimas-noticias-del-pistacho" component={UltimasNoticiasDelPistacho} />
      <Route path="/responsabilidad-social-empresarial" component={ResposabilidadSocialEmpresarial} />
      <Route path="/nuestra-gente" component={NuestraGente} />
    </Router>

    <div class="footer">
      <h4>¿Preguntas? ¡Estamos a un clic de distancia!</h4>
    
      <div class="social-icons">
        <a id="instagram-link" href="#" target="_blank">
          <img src="./images/Instagram.png" alt="Instagram" />
        </a>
        <a id="whatsapp-link" href="#" target="_blank">
          <img src="./images/What's App.png" alt="What's App" />
        </a>
        <a id="gmail-link" href="#" target="_blank">
          <img src="./images/Gmail.png" alt="Gmail" />
        </a>
      </div>
    
      <div class="footer-copy">
        <p>© 2024 por Jonathan Jeifetz</p>
      </div>
    </div> 
  </main>
</body>

<!-- Codigo CSS -->

<style>

/* Menú horizontal */
nav {
  background-color: rgb(0, 0, 0); /* Fondo negro */
  padding: 10px; /* Espaciado interno */
  display: flex; /* Hacemos el contenedor un flexbox */
  justify-content: center; /* Centra los elementos de la lista horizontalmente */
  width: 100%; /* Asegura que el nav ocupe todo el ancho disponible */
}

nav ul {
  list-style-type: none; /* Eliminar puntos de la lista */
  padding: 0;
  margin: 0;
  display: flex; /* Muestra los elementos en una fila */
  justify-content: center; /* Centra los elementos dentro de la lista */
}

nav li {
  position: relative; /* Necesario para el pseudo-elemento */
  margin-right: 20px; /* Espaciado entre los elementos */
}

nav li::after {
  content: '|'; /* Separador entre elementos */
  position: absolute;
  right: -10px;
  color: white;
  font-weight: bold;
}

nav li:last-child::after {
  content: ''; /* Elimina el separador del último elemento */
}

nav ul li a {
  color: white; /* Texto en blanco */
  text-decoration: none; /* Sin subrayado */
  font-size: 19px; /* Tamaño de la fuente */
}

nav ul li a:hover {
  text-decoration: underline; /* Subrayado al pasar el ratón */
}

/* Estilos del botón de menú */
.menu-btn {
  display: none; /* Ocultar el botón en tamaños mayores a 600px */
  background: none;
  border: none;
  color: white;
  font-size: 30px;
  cursor: pointer;
  position: absolute;
  top: 20px;
  right: 20px;
  z-index: 9999; /* Asegura que el botón esté por encima de otros elementos */
}

/* Menú visible cuando se activa */
.menu {
  display: flex; /* Mostrar el menú como un flexbox */
  justify-content: center; /* Centrar los elementos dentro del menú */
}

.menu.visible ul {
  display: block; /* Muestra el menú cuando se activa */
}

/* Estilos para dispositivos móviles */
@media (max-width: 600px) {
  nav ul {
    display: none; /* Oculta el menú horizontal en móviles */
    flex-direction: column; /* El menú se muestra en columna */
  }

  .menu-btn {
    display: block; /* Muestra el botón de menú en dispositivos móviles */
  }

  .menu.visible ul {
    display: block; /* Muestra el menú cuando se activa */
  }

  /* Asegura que el texto y los íconos estén alineados y con suficiente espacio */
  nav ul li {
    margin-right: 0; /* Elimina el margen derecho para los elementos de la lista */
    padding: 10px 0; /* Añade un poco de espacio arriba y abajo de los elementos */
  }

  nav ul li a {
    font-size: 18px; /* Ajusta el tamaño de la fuente para que se vea bien en móviles */
  }
}

/* Body */
body {
  background-color: #80A54D; /* Color Pistacho */
  font-family: Arial, sans-serif; /* Fuente básica */
  margin: 0; /* Elimina el margen por defecto del body */
  padding: 0; /* Elimina el relleno por defecto del body */
  overflow-x: hidden; /* Evita el scroll horizontal */
  width: 100%; /* Ajusta el ancho al 100% */
}

/* Header */
.header {
  background-color: #FFFFFF; /* Color de fondo */
  text-align: center; /* Centra el contenido */
  position: relative;
}

.header img {
  max-width: 100%; /* Hace que la imagen no se salga del contenedor */
  height: auto; /* Mantiene la relación de aspecto */
  margin: 0 auto; /* Centra la imagen horizontalmente */
  display: block; /* Evita espacios extra en línea */
}

/* Footer */
.footer {
  background-color: #FFFFFF; /* Color de fondo */
  display: flex; /* Alinea los elementos en columna */
  flex-direction: column; /* Coloca los elementos en columna (título, imágenes, copyright) */
  align-items: center; /* Centra los elementos horizontalmente */
  padding: 20px 0; /* Añade espacio arriba y abajo */
}

.footer h4 {
  font-family: montserrat; /* Fuente del título */
  text-align: center; /* Centra el texto */
  margin-top: 0; /* Elimina el margen superior innecesario */
  margin-bottom: 20px; /* Espacio entre el título y las imágenes */
}

.footer .social-icons {
  display: flex; /* Alinea las imágenes en una fila */
  justify-content: center; /* Centra las imágenes */
  align-items: center; /* Asegura la alineación vertical */
  gap: 150px; /* Espacio entre las imágenes */
  flex-wrap: wrap; /* Permite que las imágenes pasen a la siguiente línea si no caben */
  margin: 0 auto; /* Centrado horizontal */
  padding: 1rem; /* Espaciado interno opcional */
}

.footer img {
  max-width: 50px; /* Ajusta el tamaño de las imágenes */
  height: auto; /* Mantiene la relación de aspecto */
  display: block; /* Evita espacios extra en línea */
  margin: 0; /* Asegura que no haya márgenes adicionales */
}

/* Estilos para dispositivos móviles */
@media (max-width: 600px) {
  .footer .social-icons {
    gap: 7rem; /* Reduce el espacio entre las imágenes */
  }

  .footer img {
    max-width: 30px; /* Reduce el tamaño de las imágenes */
  }
}

/* Estilo del texto de copyright */
.footer-copy {
  margin-top: 20px; /* Espacio entre las imágenes y el copyright */
  font-size: 14px; /* Tamaño de fuente */
  color: #666; /* Color del texto */
  text-align: center; /* Centra el texto */
}

</style>
