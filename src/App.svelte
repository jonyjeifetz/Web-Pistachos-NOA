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
  }

  onMount(() => {
    const phoneNumber = "+5491127161950"; 
    const prewrittenMessage = encodeURIComponent("¡Hola! Estoy interesado en saber más sobre los pistachos de La Rioja.");
    const emailAddress = "info@pistachosriojanos.com"; 
    const isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
    
    document.getElementById("whatsapp-link").href = isMobile ? 
      `https://wa.me/${phoneNumber}?text=${prewrittenMessage}` : 
      `https://web.whatsapp.com/send?phone=${phoneNumber}?text=${prewrittenMessage}`;

    document.getElementById("instagram-link").href = isMobile ? 
      "instagram://user?username=pistachosriojanos" : 
      "https://www.instagram.com/pistachosriojanos";

    document.getElementById("gmail-link").href = isMobile ? 
      `mailto:${emailAddress}?subject=Mas Informacion&body=${prewrittenMessage}` : 
      `https://mail.google.com/mail/?view=cm&fs=1&to=${emailAddress}&su=Mas%20Informacion&body=${prewrittenMessage}`;
  });
</script>

<main>
  <div class="header"> 
    <a href="/">
      <img src="./images/Logo-Pistachos.png" alt="Logo-Pistachos-Riojanos" />
    </a>
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
            <li><a href="/" on:click={cerrarMenu}>Inicio</a></li>
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
          <li><a href="/">INICIO</a></li>
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

<style>
  /* --- BASE --- */
  :global(body) {
    background-color: #FFFFFF; /* Fondo global blanco para que lo que sobre abajo sea blanco */
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    overflow-x: hidden;
  }

  .header {
    background-color: #FFFFFF;
    padding: 20px 0;
    text-align: center;
    display: block;
  }

  .header a {
    display: inline-block;
    text-decoration: none;
  }
  
  .nav-container {
    position: relative;
    z-index: 1000;
  }

  /* --- CONTENIDO VERDE --- */
  .content {
    background-color: #80A54D; 
    min-height: 50vh; /* Ajustado para que el verde ocupe buen espacio */
    margin: 0; 
    padding: 1px 0 0 0; /* El pixel superior evita el espacio blanco entre negro y verde */
  }

  /* --- MENU DESKTOP --- */
  .menu-horizontal {
    display: none;
    background-color: #000; 
    padding: 25px 0;
    margin: 0; /* Elimina cualquier separación con el contenido verde */
  }

  .menu-list-horizontal {
    display: flex;
    list-style: none;
    margin: 0 auto;
    padding: 0 20px;
    justify-content: space-between;
    align-items: center;
    width: 95%;
    max-width: 1500px;
  }

  :global(.menu-list-horizontal a), .menu-list-horizontal li a {
    color: white;
    text-decoration: none;
    font-size: 18px;
    font-weight: bold;
    text-transform: uppercase;
    transition: all 0.3s ease;
    white-space: nowrap; 
    padding: 5px 10px;
  }

  :global(.menu-list-horizontal a:hover), .menu-list-horizontal li a:hover {
    color: #80A54D;
    transform: scale(1.05);
  }

  /* --- MENU MÓVIL --- */
  .menu-button {
    display: block;
    width: 100%;
    background: #000; /* Fondo negro para evitar saltos de color */
    color: white;
    border: none;
    padding: 20px;
    font-size: 1.5rem;
    font-weight: bold;
    cursor: pointer;
    text-align: left;
  }

  .menu-mobile {
    background-color: #000;
    width: 100%;
    margin: 0;
  }

  :global(.menu-list-vertical a), .menu-list-vertical li a {
    display: block;
    color: white;
    padding: 20px;
    text-decoration: none;
    font-size: 1.1rem;
    border-bottom: 1px solid #222;
  }

  /* --- RESPONSIVE / BREAKPOINT --- */
  @media (min-width: 1150px) {
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
    margin: 0;
  }
  
  .footer .social-icons { 
    display: flex; 
    gap: 40px; 
    padding: 1rem; 
  }
  
  .footer img { 
    max-width: 45px; 
  }

  @media (max-width: 768px) {
    .footer {
      padding: 40px 20px;
      text-align: center;
    }

    .footer h4 {
      margin: 0 0 25px 0;
      width: 100%;
      line-height: 1.2;
    }

    .footer .social-icons {
      gap: 60px;
      padding: 20px 0;
      justify-content: center;
    }

    .footer img {
      max-width: 55px;
    }
  }
</style>