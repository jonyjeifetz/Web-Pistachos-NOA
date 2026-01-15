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
  import Recetas from './components/Recetas.svelte'; 

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
      <img 
        src="./images/Logo-Pistachos.png" 
        alt="Logo-Pistachos-NOA" 
        width="400" 
        height="177" 
      />
    </a>
  </div> 

  <Router>
    <nav class="nav-container">
      <button 
        class="menu-button {menuAbierto ? 'btn-tierra' : 'btn-oro'}" 
        on:click={toggleMenu}
      >
        {menuAbierto ? '✕ Cerrar' : '☰ Menú'}
      </button>

      {#if menuAbierto}
        <div class="menu-mobile" transition:slide>
          <ul class="menu-list-vertical">
            <li><a href="/" on:click={cerrarMenu}>Inicio</a></li>
            <li><Link to="/recetas" on:click={cerrarMenu}>Recetas</Link></li>
            <li><Link to="/nuestra-gente" on:click={cerrarMenu}>Nuestra Gente</Link></li>
            <li><Link to="/responsabilidad-social-empresarial" on:click={cerrarMenu}>Responsabilidad Social Empresarial</Link></li>
            <li><Link to="/acerca-de-nosotros" on:click={cerrarMenu}>Acerca de Nosotros</Link></li>
            <li><Link to="/acerca-del-pistacho" on:click={cerrarMenu}>Acerca del Pistacho</Link></li>
            <li><Link to="/ultimas-noticias-del-pistacho" on:click={cerrarMenu}>Noticias</Link></li>
          </ul>
        </div>
      {/if}

      <div class="menu-horizontal">
        <ul class="menu-list-horizontal">
          <li><a href="/">INICIO</a></li>
          <li><Link to="/recetas" on:click={() => window.scrollTo(0,0)}>RECETAS</Link></li>
          <li><Link to="/nuestra-gente" on:click={() => window.scrollTo(0,0)}>NUESTRA GENTE</Link></li>
          <li><Link to="/responsabilidad-social-empresarial" on:click={() => window.scrollTo(0,0)}>RESPONSABILIDAD SOCIAL EMPRESARIAL</Link></li>
          <li><Link to="/acerca-de-nosotros" on:click={() => window.scrollTo(0,0)}>ACERCA DE NOSOTROS</Link></li>
          <li><Link to="/acerca-del-pistacho" on:click={() => window.scrollTo(0,0)}>ACERCA DEL PISTACHO</Link></li>
          <li><Link to="/ultimas-noticias-del-pistacho" on:click={() => window.scrollTo(0,0)}>NOTICIAS</Link></li>
        </ul>
      </div>
    </nav>

    <div class="content">
      <Route path="/" component={Inicio} />
      <Route path="/recetas" component={Recetas} />
      <Route path="/nuestra-gente" component={NuestraGente} />
      <Route path="/responsabilidad-social-empresarial" component={ResposabilidadSocialEmpresarial} />
      <Route path="/acerca-de-nosotros" component={AcercaDeNosotros} />
      <Route path="/acerca-del-pistacho" component={AcercaDelPistacho} />
      <Route path="/ultimas-noticias-del-pistacho" component={UltimasNoticiasDelPistacho} />
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
      <p>© 2025 por Jonathan Jeifetz</p>
    </div>
  </div>
</main>

<style>
  :root {
    --oro-pistacho: #D4AF37;
    --verde-oliva: #6B8E23;
    --marron-tierra: #4B3621;
    --crema-arena: #FDFBF7;
    --texto-oscuro: #2D1E12;
  }

  :global(body) {
    background-color: var(--crema-arena);
    color: var(--texto-oscuro);
    font-family: 'Segoe UI', Roboto, Arial, sans-serif;
    margin: 0;
    padding: 0;
    overflow-x: hidden;
  }

  main { display: flex; flex-direction: column; }

  .header {
    background-color: #FFFFFF;
    padding: 20px 0;
    text-align: center;
    border-bottom: 3px solid var(--oro-pistacho);
  }

  .menu-horizontal {
    display: none;
    background-color: var(--marron-tierra);
    padding: 20px 0;
    margin: 0;
  }

  .menu-list-horizontal {
    display: flex;
    list-style: none;
    margin: 0 auto;
    width: 95%;
    max-width: 1500px;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
  }

  :global(.menu-list-horizontal a), .menu-list-horizontal li a {
    color: var(--crema-arena);
    text-decoration: none;
    font-size: 13px; /* SE MANTIENE EL ORIGINAL */
    font-weight: bold;
    text-transform: uppercase;
    white-space: nowrap;
    transition: color 0.3s ease;
  }

  :global(.menu-list-horizontal a:hover) {
    color: var(--oro-pistacho);
  }

  .menu-button {
    display: block;
    width: 100%;
    color: white;
    border: none;
    padding: 20px;
    font-size: 1.5rem;
    font-weight: bold;
    cursor: pointer;
    text-align: left;
  }

  .btn-oro { background-color: var(--oro-pistacho); color: var(--marron-tierra); } 
  .btn-tierra { background-color: var(--marron-tierra); }   

  .menu-mobile {
    background-color: var(--marron-tierra);
    width: 100%;
  }

  :global(.menu-list-vertical a), .menu-list-vertical li a {
    display: block;
    color: var(--crema-arena);
    padding: 20px;
    text-decoration: none;
    border-bottom: 1px solid #5a4128;
  }

  .content {
    background-color: var(--verde-oliva);
    color: white;
    margin: 0;
    display: flow-root; 
    min-height: 50vh;
  }

  @media (min-width: 1150px) {
    .menu-button { display: none; }
    .menu-horizontal { display: flex; } 
    .menu-mobile { display: none; }
  }

  .footer { 
    background-color: #FFFFFF; 
    color: var(--marron-tierra);
    display: flex; 
    flex-direction: column; 
    align-items: center; 
    padding: 60px 20px; 
    margin: 0;
    text-align: center;
    border-top: 1px solid #eee;
  }

  .footer h4 {
    margin: 0 0 30px 0;
    font-size: 1.5rem;
    color: var(--marron-tierra);
  }
  
  .footer .social-icons { 
    display: flex; 
    gap: 80px; 
    padding: 20px; 
    justify-content: center;
    align-items: center;
  }
  
  .footer img { 
    width: 50px; 
    height: auto;
    filter: sepia(0.5) contrast(1.2);
  }

  .footer-copy {
    margin-top: 20px;
    font-size: 0.9rem;
    opacity: 0.8;
  }

  @media (max-width: 768px) {
    .footer h4 { font-size: 1.2rem; }
    .footer .social-icons { gap: 50px; }
  }
</style>