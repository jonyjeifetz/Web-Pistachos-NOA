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

let menuAbierto = false;

  const toggleMenu = () => {
    menuAbierto = !menuAbierto;
  };

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
    
    <Router>
      <!-- Botón para menú desplegable (móviles) -->
      <button class="menu-button" on:click={toggleMenu}>
        ☰ Menú
      </button>

      <!-- Menú desplegable (solo móviles) -->
      {#if menuAbierto}
        <nav class="menu">
          <ul class="menu-list">
            <li class="menu-item"><a href="#" on:click="{() => window.location.reload()}">Inicio</a></li>
            <li class="menu-item"><Link class="menu-link" to="/acerca-de-nosotros"><a href="/acerca-de-nosotros">Acerca de Nosotros</a></Link></li>
            <li class="menu-item"><Link class="menu-link" to="/acerca-del-pistacho"><a href="/acerca-del-pistacho">Acerca del Pistacho</a></Link></li>
            <li class="menu-item"><Link class="menu-link" to="/ultimas-noticias-del-pistacho"><a href="/ultimas-noticias-del-pistacho">Ultimas Noticias del Pistacho</a></Link></li>
            <li class="menu-item"><Link class="menu-link" to="/responsabilidad-social-empresarial"><a href="/responsabilidad-social-empresarial">Responsabilidad Social Empresarial</a></Link></li>
            <li class="menu-item"><Link class="menu-link" to="/nuestra-gente"><a href="/nuestra-gente">Nuestra Gente</a></Link></li>
          </ul>
        </nav>
      {/if}
      <!-- Menú horizontal (solo escritorio) -->
      <nav class="menu-horizontal">
        <ul class="menu-list1">
          <li class="menu-item"><a href="#" on:click="{() => window.location.reload()}">Inicio</a></li>
          <li class="menu-item"><Link class="menu-link" to="/acerca-de-nosotros"><a href="/acerca-de-nosotros">Acerca de Nosotros</a></Link></li>
          <li class="menu-item"><Link class="menu-link" to="/acerca-del-pistacho"><a href="/acerca-del-pistacho">Acerca del Pistacho</a></Link></li>
          <li class="menu-item"><Link class="menu-link" to="/ultimas-noticias-del-pistacho"><a href="/ultimas-noticias-del-pistacho">Ultimas Noticias del Pistacho</a></Link></li>
          <li class="menu-item"><Link class="menu-link" to="/responsabilidad-social-empresarial"><a href="/responsabilidad-social-empresarial">Responsabilidad Social Empresarial</a></Link></li>
          <li class="menu-item"><Link class="menu-link" to="/nuestra-gente"><a href="/nuestra-gente">Nuestra Gente</a></Link></li>
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

  /* Estilos para el menú */
  nav {
    background-color: rgb(0, 0, 0); /* Fondo negro */
    padding: 10px; /* Espaciado interno */
  }

  nav ul {
    list-style-type: none; /* Eliminar los puntos de la lista */
    padding: 0;
    margin: 0;
    display: flex; /* Esto pone los elementos de la lista en una fila */
    justify-content: center; /* Centra los elementos del menú */
  }

  nav li {
    position: relative; /* Necesario para el pseudo-elemento */
    margin-right: 20px; /* Espaciado entre los elementos del menú */
  }

  nav li::after {
    content: '|'; /* Agrega el separador */
    position: absolute;
    right: -10px; /* Ajusta la posición del separador */
    color: white; /* Color del separador */
    font-weight: bold;
  }

  nav li:last-child::after {
    content: ''; /* Elimina el separador del último elemento */
  }

  nav ul li a {
    color: white; /* Texto en blanco */
    text-decoration: none; /* Sin subrayado */
    font-size: 19px; /* Aumenta el tamaño de la fuente */
  }

  nav ul li a:hover {
    text-decoration: underline; /* Subrayado al pasar el ratón */
  }

 /* Body */
  body{
    background-color:#80A54D; /* Color Pistacho */
    font-family: Arial, sans-serif; /* Fuente básica */
    margin: 0; /* Elimina el margen por defecto del body */
    padding: 0; /* Elimina el relleno por defecto del body */
    overflow-x: hidden; /* Evita el scroll horizontal */
    width: 100%; /* Ajusta el ancho al 100% */
  }

  /* Header */
  .header{
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

  /* PRUEBAS DE MENU CON BOTON */

/* Menú Horizontal: Centrado */
.menu-horizontal .menu-list1 {
  display: flex;             /* Establece un contenedor flexible */
  justify-content: center;   /* Centra los elementos horizontalmente */
  align-items: center;       /* Centra los elementos verticalmente (si es necesario) */
  padding: 0;                /* Elimina el relleno predeterminado */
  margin: 0;                 /* Elimina el margen predeterminado */
  list-style: none;          /* Elimina los puntos de lista predeterminados */
  position: relative;
  left: 0;                   /* Se eliminó el -80% */
}

.menu-horizontal .menu-list1 .menu-item {
  margin: 0 15px;            /* Espacio entre los elementos del menú */
}

/* Corregir el color de la sección "Inicio" */
.menu-horizontal .menu-list1 .menu-item:first-child a {
  color: #FFFFFF; /* Blanco para la sección "Inicio" */
  font-weight: normal;
  text-decoration: none;
}

.menu-horizontal .menu-list1 .menu-item:first-child a:hover {
  font-weight: bold; /* Poner en negrita al pasar el mouse */
}

/* Corregir el color de los enlaces en el resto del menú */
.menu-horizontal .menu-list1 .menu-item a {
  color: #FFFFFF; /* Color blanco para todos los enlaces */
  font-weight: normal;
  text-decoration: none;
}

.menu-horizontal .menu-list1 .menu-item a:hover {
  font-weight: bold; /* Poner en negrita al pasar el mouse */
}

/* Menú Vertical: Alineado a la izquierda */
.menu .menu-list {
  list-style: none;           /* Elimina los puntos de lista */
  padding: 0;                 /* Elimina el relleno predeterminado */
  margin: 0;                  /* Elimina márgenes predeterminados */
  display: block;             /* Asegura que la lista sea bloque */
  position: absolute;         /* Alineado de manera absoluta */
  left: 0;                    /* Lo coloca a la izquierda */
  top: 0;                     /* Lo coloca en la parte superior */
  background-color: #222222;  /* Fondo oscuro para el menú */
  padding: 20px;              /* Espaciado interior */
}

.menu .menu-item {
  text-align: left;           /* Alineación a la izquierda de los elementos */
  margin: 10px 0;             /* Espaciado entre los ítems */
}

.menu .menu-item a {
  color: #FFFFFF;             /* Color blanco para los enlaces */
  font-weight: normal;        /* No negrita por defecto */
  text-decoration: none;      /* Sin subrayado */
  display: block;             /* Hace que los enlaces ocupen todo el ancho */
  padding: 10px 20px;         /* Padding para que los ítems sean más grandes */
}

.menu .menu-item a:hover {
  font-weight: bold;          /* Poner en negrita al pasar el mouse */
  background-color: #333333;  /* Fondo gris oscuro al pasar el mouse */
}




  /* Media query: dispositivos móviles (≤ 768px) */
  @media screen and (max-width: 768px) {
  .menu-button {
    display: block; /* Mostrar el botón para menú desplegable */
  }

  .menu {
    display: block; /* Mostrar el menú desplegable */
  }

  .menu-horizontal {
    display: none; /* Ocultar el menú horizontal */
  }
}

/* Media query: dispositivos grandes (> 768px) */
@media screen and (min-width: 769px) {
  .menu-button {
    display: none; /* Ocultar el botón para menú desplegable */
  }

  .menu {
    display: none; /* Ocultar el menú desplegable */
  }

  .menu-horizontal {
    display: flex; /* Mostrar el menú horizontal */
  }
}



</style>
