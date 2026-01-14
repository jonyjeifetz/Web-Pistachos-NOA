<script>
  import { onMount } from "svelte";

  let recetasContainer;
  let frameId;

  // FUNCIÓN DE ANIMACIÓN SUAVE
  const animar = () => {
    if (recetasContainer) {
      recetasContainer.scrollLeft += 1; 

      if (recetasContainer.scrollLeft >= recetasContainer.scrollWidth / 2) {
        recetasContainer.scrollLeft = 0;
      }
    }
    frameId = requestAnimationFrame(animar);
  };

  onMount(() => {
    frameId = requestAnimationFrame(animar);

    const handleMobileScroll = () => {
      const items = document.querySelectorAll('.receta');
      const centerX = window.innerWidth / 2;

      items.forEach(item => {
        const rect = item.getBoundingClientRect();
        if (rect.left < centerX && rect.right > centerX) {
          item.classList.add('active-center');
        } else {
          item.classList.remove('active-center');
        }
      });
    };

    recetasContainer.addEventListener('scroll', handleMobileScroll);

    const esMovil = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
    
    if (!esMovil) {
      recetasContainer.addEventListener('mouseenter', () => cancelAnimationFrame(frameId));
      recetasContainer.addEventListener('mouseleave', () => {
        frameId = requestAnimationFrame(animar);
      });
    }

    return () => cancelAnimationFrame(frameId);
  });
</script>

<div class="seccion-principal">
  <h1>De La Rioja al mundo: Nuestro alcance</h1>
  <div id="flourish-container">
    <div class="flourish-embed flourish-map" data-src="visualisation/20858873"></div>
  </div>

  <h1 class="titulo-recetas">De La Rioja a Tu Mesa: Recetas Creativas con Pistacho</h1>
  <div class="recetas-container" bind:this={recetasContainer}>
    <div class="recetas">
      {#each [1, 2] as loop}
        <div class="receta">
          <img src="./images/Brownie de Pistacho.jpeg" alt="Brownie de Pistacho" />
          <div class="hover-text">Brownie de Pistacho</div>
          <a href="./Recetas/Receta Brownie de Pistacho.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
        </div>
        <div class="receta">
          <img src="./images/Baklava.jpeg" alt="Baklava" />
          <div class="hover-text">Baklava de Pistacho</div>
          <a href="./Recetas/Receta Baklava de Pistacho.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
        </div>
        <div class="receta">
          <img src="./images/Queso.jpeg" alt="Queso" />
          <div class="hover-text">Queso con Pistacho</div>
          <a href="./Recetas/Receta Queso de Pistacho.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
        </div>
        <div class="receta">
          <img src="./images/Crema de Pistacho.jpeg" alt="Crema de Pistacho" />
          <div class="hover-text">Crema de Pistacho</div>
          <a href="./Recetas/Receta Crema Pistacho.pdf" target="_blank" class="btn-ver-receta" >Ver receta</a>
        </div>
        <div class="receta">
          <img src="./images/Trufas.jpeg" alt="Trufas de Pistacho" />
          <div class="hover-text">Trufas de Pistacho, Palta y Chocolate</div>
          <a href="./Recetas/Receta Trufas de Pistacho, Palta y Chocolate.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
        </div>
      {/each}
    </div>
  </div>
</div>

<style>
  /* --- VARIABLES --- */
  :root {
    --oro-pistacho: #D4AF37;
    --verde-oliva: #6B8E23;
    --marron-tierra: #4B3621;
    --crema-arena: #FDFBF7;
  }

  .seccion-principal {
    background-color: var(--crema-arena);
    padding-bottom: 50px;
  }

  h1 {
    font-family: 'Montserrat', sans-serif;
    color: var(--marron-tierra);
    text-align: center;
    padding-top: 60px;
    margin: 0;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-size: 2rem;
  }

  .titulo-recetas {
    color: var(--verde-oliva);
    margin-top: 80px;
  }

  .recetas-container {
    display: flex;
    justify-content: flex-start;
    width: 100%;
    padding: 40px 0;
    margin-bottom: 20px;
    overflow-x: auto;
    scrollbar-width: none;
    -webkit-overflow-scrolling: touch;
    scroll-behavior: auto;
  }

  .recetas-container::-webkit-scrollbar {
    display: none;
  }

  .recetas {
    display: flex;
    gap: 30px;
    width: max-content;
    flex-wrap: nowrap;
    padding: 0 40px;
  }

  .receta {
    position: relative;
    width: 320px;
    height: 450px;
    text-align: center;
    flex-shrink: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: transform 0.4s ease;
    overflow: hidden;
    border-radius: 15px;
    box-shadow: 0 8px 15px rgba(75, 54, 33, 0.2);
    border: 1px solid rgba(212, 175, 55, 0.3); /* Borde sutil oro */
  }

  .receta img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: all 0.4s ease;
  }

  @media (min-width: 769px) {
    .receta:hover img {
      transform: scale(1.1);
      filter: brightness(0.5);
    }
    .receta:hover .hover-text,
    .receta:hover .btn-ver-receta {
      opacity: 1;
    }
  }

  .hover-text {
    position: absolute;
    top: 40%;
    color: var(--crema-arena);
    font-family: 'Montserrat', sans-serif;
    font-size: 22px;
    font-weight: bold;
    padding: 0 20px;
    opacity: 0;
    transition: opacity 0.4s ease;
    z-index: 2;
    text-shadow: 2px 2px 8px rgba(0,0,0,0.9);
    pointer-events: none;
    text-transform: uppercase;
  }

  .btn-ver-receta {
    position: absolute;
    bottom: 15%;
    background-color: var(--oro-pistacho);
    color: var(--marron-tierra);
    padding: 12px 25px;
    border-radius: 25px;
    text-decoration: none;
    font-weight: bold;
    font-size: 0.9rem;
    text-transform: uppercase;
    opacity: 0;
    transition: all 0.4s ease;
    z-index: 2;
    box-shadow: 0 4px 10px rgba(0,0,0,0.3);
  }

  .btn-ver-receta:hover {
    background-color: white;
    transform: translateY(-2px);
  }

  /* Animación para móvil */
  :global(.receta.active-center img) {
    transform: scale(1.1);
    filter: brightness(0.5);
  }
  :global(.receta.active-center .hover-text),
  :global(.receta.active-center .btn-ver-receta) {
    opacity: 1;
  }

  @media (max-width: 768px) {
    .receta {
      width: 280px;
      height: 380px;
    }
    h1 {
      font-size: 1.5rem;
      padding: 40px 15px 0;
    }
    .hover-text {
      font-size: 18px;
    }
  }

  .flourish-embed {
    width: 100%;
    margin-top: 20px;
  }

  * {
    box-sizing: border-box;
  }
</style>