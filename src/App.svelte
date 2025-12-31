<!-- Codigo J-S -->
<script>
  import { onMount } from "svelte";
  import { Router, Route, Link } from 'svelte-routing';
  import { slide } from 'svelte/transition';
  import Inicio from './components/Inicio.svelte';
  import AcercaDeNosotros from './components/AcercaDeNosotros.svelte';
  import AcercaDelPistacho from './components/AcercaDelPistacho.svelte';
  import UltimasNoticiasDelPistacho from './components/UltimasNoticiasDelPistacho.svelte';
  import ResposabilidadSocialEmpresarial from './components/ResposabilidadSocialEmpresarial.svelte';
  import NuestraGente from './components/NuestraGente.svelte';

  let menuAbierto = false;

  function toggleMenu() {
    menuAbierto = !menuAbierto;
  }

  function cerrarMenu() {
    menuAbierto = false;
    window.scrollTo(0, 0); 
  }

  onMount(() => {
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
      
      <button 
        class="menu-button {menuAbierto ? 'menu-abierto-negro' : ''}" 
        on:click={toggleMenu}
      >
        {menuAbierto ? '✕ Cerrar' : '☰ Menú'}
      </button>

      {#if menuAbierto}
        <div class="menu-mobile" transition:slide>
          <ul class="menu-list-vertical">
            <li><Link to="/" on:click={cerrarMenu}>Inicio</Link></li>
            <li><Link to="/acerca-de-nosotros" on:click={cerrarMenu}>Acerca de Nosotros</Link></li>
            <li><Link to="/acerca-del-pistacho" on:click={cerrarMenu}>Acerca del Pistacho</Link></li>
            <li><Link to="/ultimas-noticias-del-pistacho" on:click={cerrarMenu}>Últimas Noticias</Link></li>
            <li><Link to="/responsabilidad-social-empresarial" on:click={cerrarMenu}>Responsabilidad Social Empresarial</Link></li>
            <li><Link to="/nuestra-gente" on:click={cerrarMenu}>Nuestra Gente</Link></li>
          </ul>
        </div>
      {/if}

      <div class="menu-horizontal">
        <ul class="menu-list-horizontal">
          <li><Link to="/" on:click={() => window.scrollTo(0,0)}>INICIO</Link></li>
          <li><Link to="/acerca-de-nosotros" on:click={() => window.scrollTo(0,0)}>ACERCA DE NOSOTROS</Link></li>
          <li><Link to="/acerca-del-pistacho" on:click={() => window.scrollTo(0,0)}>ACERCA DEL PISTACHO</Link></li>
          <li><Link to="/ultimas-noticias-del-pistacho" on:click={() => window.scrollTo(0,0)}>NOTICIAS</Link></li>
          <li><Link to="/responsabilidad-social-empresarial" on:click={() => window.scrollTo(0,0)}>RESPONSABILIDAD SOCIAL EMPRESARIAL</Link></li>
          <li><Link to="/nuestra-gente" on:click={() => window.scrollTo(0,0)}>NUESTRA GENTE</Link></li>
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
    position: relative;
    z-index: 1000;
  }

  /* --- MENU DESKTOP OPTIMIZADO PARA PANTALLAS GRANDES --- */
  .menu-horizontal {
    display: none;
    background-color: #000; 
    padding: 25px 0; /* Más altura para dar presencia */
  }

  .menu-list-horizontal {
    display: flex;
    list-style: none;
    margin: 0 auto;
    padding: 0 20px;
    justify-content: space-between; /* Distribuye a lo largo de todo el ancho */
    align-items: center;
    width: 95%; /* Ocupa casi todo el ancho de la pantalla */
    max-width: 1500px; /* Aumentado para que no se vea chico en el centro */
  }

  :global(.menu-list-horizontal a) {
    color: white;
    text-decoration: none;
    font-size: 18px; /* Letra más grande y visible */
    font-weight: bold;
    text-transform: uppercase;
    transition: all 0.3s ease;
    white-space: nowrap; 
    padding: 5px 10px;
  }

  :global(.menu-list-horizontal a:hover) {
    color: #80A54D;
    transform: scale(1.05); /* Efecto visual de resaltado */
  }

  /* --- MENU MÓVIL --- */
  .menu-button {
    display: block;
    width: 100%;
    background: transparent; 
    color: white;
    border: none;
    padding: 20px;
    font-size: 1.5rem;
    font-weight: bold;
    cursor: pointer;
    text-align: left;
    text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
  }

  .menu-mobile {
    background-color: #000;
    width: 100%;
  }

  :global(.menu-list-vertical a) {
    display: block;
    color: white;
    padding: 20px;
    text-decoration: none;
    font-size: 1.1rem;
    border-bottom: 1px solid #222;
  }

  /* --- RESPONSIVE / BREAKPOINT --- */
  @media (min-width: 1150px) { /* Ajustado para que el texto largo no choque */
    .menu-button {
      display: none;
    }
    .menu-horizontal {
      display: flex;
    }
    .menu-mobile {
      display: none;
    }
  }

  /* --- FOOTER --- */
  .footer { 
    background-color: #FFFFFF; 
    display: flex; 
    flex-direction: column; 
    align-items: center; 
    padding: 40px 0; 
  }
  .footer .social-icons { display: flex; gap: 40px; padding: 1rem; }
  .footer img { max-width: 45px; }
</style>
