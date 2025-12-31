<script>
  /* --- (Mantenemos tu lógica de script intacta) --- */
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
        class="menu-button {menuAbierto ? 'btn-negro' : 'btn-verde'}" 
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
    background-color: #FFFFFF;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    overflow-x: hidden;
  }

  main { display: flex; flex-direction: column; }

  .header {
    background-color: #FFFFFF;
    padding: 20px 0;
    text-align: center;
  }

  /* --- MENU DESKTOP (IMAGEN 2) --- */
  .menu-horizontal {
    display: none; /* Se activa en el media query */
    background-color: #000; /* Siempre negro en PC */
    padding: 25px 0;
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
    color: white;
    text-decoration: none;
    font-size: 18px;
    font-weight: bold;
    text-transform: uppercase;
  }

  /* --- MENU MÓVIL DINÁMICO --- */
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

  .btn-verde { background-color: #80A54D; } /* Estado cerrado: Verde */
  .btn-negro { background-color: #000; }   /* Estado abierto: Negro */

  .menu-mobile {
    background-color: #000;
    width: 100%;
  }

  :global(.menu-list-vertical a), .menu-list-vertical li a {
    display: block;
    color: white;
    padding: 20px;
    text-decoration: none;
    border-bottom: 1px solid #222;
  }

  /* --- CONTENT --- */
  .content {
    background-color: #80A54D;
    margin: 0;
    display: flow-root; /* Evita el espacio blanco */
    min-height: 50vh;
  }

  /* --- RESPONSIVE --- */
  @media (min-width: 1150px) {
    .menu-button { display: none; }
    .menu-horizontal { display: flex; } /* Aparece el menú negro de PC */
    .menu-mobile { display: none; }
  }

 /* --- FOOTER --- */
  .footer { 
    background-color: #FFFFFF; 
    display: flex; 
    flex-direction: column; 
    align-items: center; 
    padding: 60px 20px; /* Añadimos padding lateral para que el texto no toque los bordes en el celular */
    margin: 0;
    text-align: center; /* Centra el texto por defecto */
  }

  .footer h4 {
    margin: 0 0 30px 0;
    font-size: 1.5rem;
    line-height: 1.3;
    max-width: 800px; /* Evita que el texto se estire demasiado en PC */
  }
  
  /* Mantenemos tus logos exactamente como están ahora */
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
  }

  /* --- AJUSTE ESPECÍFICO PARA CELULARES --- */
  @media (max-width: 768px) {
    .footer h4 {
      font-size: 1.2rem; /* Achicamos un poco la letra para que entre mejor */
      width: 100%;       /* Asegura que ocupe el ancho disponible */
      margin-bottom: 20px;
      padding: 0 10px;   /* Aire extra a los costados del texto */
    }

    .footer .social-icons {
      gap: 50px; /* Mantenemos una separación cómoda para dedos en móvil */
    }
    
    .footer img {
      width: 45px; /* Mantenemos tu tamaño de móvil */
    }
  }
</style>