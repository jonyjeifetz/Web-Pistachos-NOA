<!-- Codigo J-S -->
<script>
  import { onMount } from "svelte";
  import { Router, Route, Link } from 'svelte-routing';
  import { slide } from 'svelte/transition'; // Para una animación suave
  import Inicio from './components/Inicio.svelte';
  import AcercaDeNosotros from './components/AcercaDeNosotros.svelte';
  import AcercaDelPistacho from './components/AcercaDelPistacho.svelte';
  import UltimasNoticiasDelPistacho from './components/UltimasNoticiasDelPistacho.svelte';
  import ResposabilidadSocialEmpresarial from './components/ResposabilidadSocialEmpresarial.svelte';
  import NuestraGente from './components/NuestraGente.svelte';

  let menuAbierto = false; // Estado para el menú móvil

  function toggleMenu() {
    menuAbierto = !menuAbierto;
  }

  function cerrarMenu() {
    menuAbierto = false;
  }

  onMount(() => {
    // Redirige a la página de inicio si no es la página principal (Opcional según tu lógica)
    if (window.location.pathname !== "/") {
      // window.location.href = "/"; // Ten cuidado: esto anula el router de svelte si entran por link directo
    }

    const phoneNumber = "+5491127161950"; 
    const prewrittenMessage = encodeURIComponent("¡Hola! Estoy interesado en saber más sobre los pistachos de La Rioja.");
    const emailAddress = "info@pistachosriojanos.com"; 
    const isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
    
    document.getElementById("whatsapp-link").href = isMobile ? 
      `https://wa.me/${phoneNumber}?text=${prewrittenMessage}` : 
      `https://web.whatsapp.com/send?phone=${phoneNumber}&text=${prewrittenMessage}`;

    document.getElementById("instagram-link").href = isMobile ? 
      "instagram://user?username=pistachosriojanos" : 
      "https://www.instagram.com/pistachosriojanos";

    document.getElementById("gmail-link").href = isMobile ? 
      `mailto:${emailAddress}?subject=Mas Informacion&body=${prewrittenMessage}` : 
      `https://mail.google.com/mail/?view=cm&fs=1&to=${emailAddress}&su=Mas%20Informacion&body=${prewrittenMessage}`;
  });
</script>

<!-- Codigo HTML -->
<main>
  <div class="header"> 
    <img src="./images/Logo-Pistachos.png" alt="Logo-Pistachos-Riojanos" />
  </div>  

  <Router>
    <nav class="nav-container">
      
      <button class="menu-button" on:click={toggleMenu}>
        {menuAbierto ? '✕ Cerrar' : '☰ Menú'}
      </button>

      {#if menuAbierto}
        <div class="menu-mobile" transition:slide>
          <ul class="menu-list-vertical">
            <li><Link to="/" on:click={cerrarMenu}>Inicio</Link></li>
            <li><Link to="/acerca-de-nosotros" on:click={cerrarMenu}>Acerca de Nosotros</Link></li>
            <li><Link to="/acerca-del-pistacho" on:click={cerrarMenu}>Acerca del Pistacho</Link></li>
            <li><Link to="/ultimas-noticias-del-pistacho" on:click={cerrarMenu}>Últimas Noticias</Link></li>
            <li><Link to="/responsabilidad-social-empresarial" on:click={cerrarMenu}>RSE</Link></li>
            <li><Link to="/nuestra-gente" on:click={cerrarMenu}>Nuestra Gente</Link></li>
          </ul>
        </div>
      {/if}

      <div class="menu-horizontal">
        <ul class="menu-list-horizontal">
          <li><Link to="/">Inicio</Link></li>
          <li><Link to="/acerca-de-nosotros">Acerca de Nosotros</Link></li>
          <li><Link to="/acerca-del-pistacho">Acerca del Pistacho</Link></li>
          <li><Link to="/ultimas-noticias-del-pistacho">Noticias</Link></li>
          <li><Link to="/responsabilidad-social-empresarial">RSE</Link></li>
          <li><Link to="/nuestra-gente">Nuestra Gente</Link></li>
        </ul>
      </div>
    </nav>

    <div class="content">
      <Route path="/" component={Inicio} />
      <Route path="/acerca-de-nosotros" component={AcercaDeNosotros} />
      <Route path="/acerca-del-pistacho" component={AcercaDelPistacho} />
      <Route path="/ultimas-noticias-del-pistacho" component={UltimasNoticiasDelPistacho} />
      <Route path="/responsabilidad-social-empresarial" component={ResposabilidadSocialEmpresarial} />
      <Route path="/nuestra-gente" component={NuestraGente} />
    </div>
  </Router>

  <div class="footer">
    <h4>¿Preguntas? ¡Estamos a un clic de distancia!</h4>
    <div class="social-icons">
      <a id="instagram-link" href="/" target="_blank"><img src="./images/Instagram.png" alt="Instagram" /></a>
      <a id="whatsapp-link" href="/" target="_blank"><img src="./images/What's App.png" alt="Whats App" /></a>
      <a id="gmail-link" href="/" target="_blank"><img src="./images/Gmail.png" alt="Gmail" /></a>
    </div>
    <div class="footer-copy">
      <p>© 2024 por Jonathan Jeifetz</p>
    </div>
  </div>
</main>

<!-- Codigo CSS -->
<style>
  /* --- BASE --- */
  :global(body) {
    background-color: #80A54D;
    font-family: Arial, sans-serif;
    margin: 0;
    overflow-x: hidden;
  }

  .header {
    background-color: #FFFFFF;
    padding: 20px 0;
    text-align: center;
  }
  
  .nav-container {
    background-color: #000;
    position: relative;
    z-index: 1000;
  }

  /* --- MENU DESKTOP --- */
  .menu-horizontal {
    display: none; /* Oculto por defecto */
    justify-content: center;
    padding: 15px;
  }

  .menu-list-horizontal {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
    gap: 20px;
  }

  :global(.menu-list-horizontal a) {
    color: white;
    text-decoration: none;
    font-size: 16px;
  }

  /* --- MENU MÓVIL --- */
  .menu-button {
    display: block;
    width: 100%;
    background: #000;
    color: white;
    border: none;
    padding: 15px;
    font-size: 1.2rem;
    cursor: pointer;
    text-align: left;
  }

  .menu-mobile {
    background-color: #1a1a1a;
    width: 100%;
    border-top: 1px solid #333;
  }

  .menu-list-vertical {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .menu-list-vertical li {
    border-bottom: 1px solid #333;
  }

  :global(.menu-list-vertical a) {
    display: block;
    color: white;
    padding: 15px 20px;
    text-decoration: none;
    font-size: 18px;
  }

  /* --- RESPONSIVE --- */
  @media (min-width: 800px) {
    .menu-button {
      display: none; /* Esconde botón en PC */
    }
    .menu-horizontal {
      display: flex; /* Muestra menú horizontal en PC */
    }
    .menu-mobile {
      display: none;
    }
  }

  /* Footer estilos (se mantienen de tu código) */
  .footer { background-color: #FFFFFF; display: flex; flex-direction: column; align-items: center; padding: 20px 0; margin-top: 50px;}
  .footer .social-icons { display: flex; gap: 50px; padding: 1rem; }
  .footer img { max-width: 40px; }
</style>
