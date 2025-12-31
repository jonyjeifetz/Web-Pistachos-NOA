<script>
  import { onMount } from "svelte";

  let recetasContainer;
  let frameId;

  // FUNCIÓN DE ANIMACIÓN SUAVE
  const animar = () => {
    if (recetasContainer) {
      recetasContainer.scrollLeft += 1; // Misma velocidad que la galería

      // Reinicio para loop infinito
      if (recetasContainer.scrollLeft >= recetasContainer.scrollWidth / 2) {
        recetasContainer.scrollLeft = 0;
      }
    }
    frameId = requestAnimationFrame(animar);
  };

  onMount(() => {
    // Iniciar animación
    frameId = requestAnimationFrame(animar);

    // Lógica para móviles: activar efectos en la receta central
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

    // PAUSAS (Solo en Desktop para evitar trabas en móvil)
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

<h1>De La Rioja al mundo: nuestro alcance</h1>
<div id="flourish-container">
  <div class="flourish-embed flourish-map" data-src="visualisation/20858873"></div>
</div>

<h1>De La Rioja a Tu Mesa: Recetas Creativas con Pistacho</h1>
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

<style>
  /* Mantenemos tus estilos y aseguramos compatibilidad */
  h1 {
    font-family: 'Montserrat', sans-serif;
    color: #FFFFFF;
    text-align: center;
    margin-top: 40px;
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
    scroll-behavior: auto; /* IMPORTANTE para evitar conflictos con JS */
  }

  .recetas-container::-webkit-scrollbar {
    display: none;
  }

  .recetas {
    display: flex;
    gap: 20px;
    width: max-content;
    flex-wrap: nowrap;
    padding: 0 20px;
  }

  .receta {
    position: relative;
    width: 300px;
    height: 400px;
    text-align: center;
    flex-shrink: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: transform 0.4s ease;
    overflow: hidden;
    border-radius: 10px;
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
      filter: brightness(0.6);
    }
    .receta:hover .hover-text,
    .receta:hover .btn-ver-receta {
      opacity: 1;
    }
  }

  .hover-text {
    position: absolute;
    top: 40%;
    color: white;
    font-size: 24px;
    font-weight: bold;
    padding: 10px;
    opacity: 0;
    transition: opacity 0.4s ease;
    z-index: 2;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.8);
    pointer-events: none;
  }

  .btn-ver-receta {
    position: absolute;
    bottom: 20%;
    background-color: black;
    color: white;
    padding: 10px 20px;
    border-radius: 20px;
    text-decoration: none;
    font-weight: bold;
    opacity: 0;
    transition: all 0.4s ease;
    z-index: 2;
  }

  :global(.receta.active-center img) {
    transform: scale(1.1);
    filter: brightness(0.6);
  }
  :global(.receta.active-center .hover-text),
  :global(.receta.active-center .btn-ver-receta) {
    opacity: 1;
  }

  @media (max-width: 768px) {
    .receta {
      width: 250px;
      height: 350px;
    }
    .hover-text {
      font-size: 18px;
    }
  }

  .flourish-embed {
    width: 100%;
    max-width: 100%;
    overflow-x: hidden;
  }

  * {
    box-sizing: border-box;
  }
</style>