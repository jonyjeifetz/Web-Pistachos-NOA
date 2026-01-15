<script>
  import { onMount } from "svelte";
  import { fade, scale } from 'svelte/transition';

  let galeriaContainer;
  let frameId;
  let itemSeleccionado = null;

  // Configuración de archivos de la galería
  const totalFotos = 160; 
  const totalVideos = 5; 

  let baseItems = [
    ...Array.from({ length: totalVideos }, (_, i) => ({
      tipo: 'video',
      url: `./images/galeria/videos/Video (${i + 1}).mp4`,
    })),
    ...Array.from({ length: totalFotos }, (_, i) => ({
      tipo: 'foto',
      url: `./images/galeria/Foto (${i + 1}).jpg`,
    }))
  ];

  // FUNCIÓN DE ANIMACIÓN SUAVE
  const animar = () => {
    if (galeriaContainer && !itemSeleccionado) {
      galeriaContainer.scrollLeft += 1; 

      if (galeriaContainer.scrollLeft >= galeriaContainer.scrollWidth / 2) {
        galeriaContainer.scrollLeft = 0;
      }
    }
    frameId = requestAnimationFrame(animar);
  };

  function abrirModal(item) {
    itemSeleccionado = item;
  }

  function cerrarModal() {
    itemSeleccionado = null;
  }

  onMount(() => {
    frameId = requestAnimationFrame(animar);

    const handleMobileScroll = () => {
      const items = document.querySelectorAll('.item-galeria');
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

    galeriaContainer.addEventListener('scroll', handleMobileScroll);

    const esMovil = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
    
    if (!esMovil) {
      galeriaContainer.addEventListener('mouseenter', () => cancelAnimationFrame(frameId));
      galeriaContainer.addEventListener('mouseleave', () => {
        if (!itemSeleccionado) frameId = requestAnimationFrame(animar);
      });
    }

    return () => cancelAnimationFrame(frameId);
  });

  function manejarError(e) {
    e.target.closest('.item-galeria').style.display = 'none';
  }
</script>

<!--
<div class="seccion-principal">
  <h1>De Catamarca al mundo: Nuestro alcance</h1>
  <div id="flourish-container">
    <div class="flourish-embed flourish-map" data-src="visualisation/27220153"></div>
  </div>  
  <h1 class="titulo-galeria">Nuestra Producción en Imágenes</h1>
  <div class="galeria-scroll-container" bind:this={galeriaContainer}>
    <div class="galeria-track">
      {#each [1, 2] as loop}
        {#each baseItems as item}
          <div class="item-galeria" on:click={() => abrirModal(item)}>
            {#if item.tipo === 'foto'}
              <img src={item.url} alt="Pistachos Riojanos" loading="lazy" on:error={manejarError} />
            {:else}
              <video src={item.url} autoplay muted loop playsinline on:error={manejarError}></video>
            {/if}
            <div class="hover-text">Pistachos Riojanos</div>
            <button class="btn-ampliar">🔍 AMPLIAR</button>
          </div>
        {/each}
      {/each}
    </div>
  </div>

  {#if itemSeleccionado}
    <div class="modal-overlay" transition:fade={{ duration: 200 }} on:click={cerrarModal}>
      <button class="boton-cerrar" on:click={cerrarModal}>✕</button>
      <div class="modal-contenido" on:click|stopPropagation>
        {#if itemSeleccionado.tipo === 'foto'}
          <img src={itemSeleccionado.url} alt="Vista Completa" transition:scale={{ duration: 300, start: 0.9 }} />
        {:else}
          <video src={itemSeleccionado.url} controls autoplay playsinline class="video-full"></video>
        {/if}
      </div>
    </div>
  {/if}
</div>
-->

<!-- Esta seccion se elimina cuando tengo la info posta -->
<div class="cuerpo-inicio">
    <div class="contenedor-tarjeta">
        <h1>Bienvenido a Pistachos del NOA</h1>
        <div class="divisor-oro"></div>
        <h3>Excelencia desde Catamarca</h3>
        <p>Estamos preparando una experiencia digital completa para mostrarte el corazón de nuestra producción y la calidad premium de nuestros pistachos.</p>
    </div>
</div>

<style>
  :root {
    --oro-pistacho: #D4AF37;
    --verde-oliva: #6B8E23;
    --marron-tierra: #4B3621;
    --crema-arena: #FDFBF7;
  }

  .cuerpo-inicio {
        margin: 0;
        padding: 60px 20px; /* Reducimos un poco el padding general del contenedor */
        text-align: center;
        background-color: var(--crema-arena);
        min-height: 70vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .contenedor-tarjeta {
        max-width: 700px;
        background: white;
        padding: 40px 50px 60px 50px; /* Ajustamos: menos arriba (40px) y más abajo (60px) para "subir" el contenido */
        border-radius: 20px;
        box-shadow: 0 10px 30px rgba(75, 54, 33, 0.05);
        border: 1px solid rgba(212, 175, 55, 0.2);
        display: flex;
        flex-direction: column;
        justify-content: flex-start; /* Cambiamos a start para controlar mejor la posición */
    }

    .cuerpo-inicio h1 {
        font-family: 'Montserrat', sans-serif;
        color: var(--verde-oliva);
        font-size: 32px;
        text-transform: uppercase;
        margin-top: 0; /* Aseguramos que no haya margen extra arriba */
        margin-bottom: 0;
        letter-spacing: 1px;
        line-height: 1.2;
    }

    .divisor-oro {
        width: 100px;
        height: 3px;
        background-color: var(--oro-pistacho);
        margin: 20px auto; /* Reducimos ligeramente el margen del divisor */
    }

  .cuerpo-inicio h3 {
      font-family: 'Montserrat', sans-serif;
      color: var(--marron-tierra);
      font-size: 24px;
      margin-bottom: 15px;
  }

  .cuerpo-inicio p {
      font-family: 'Montserrat', sans-serif;
      color: var(--marron-tierra);
      opacity: 0.8;
      line-height: 1.6;
      font-style: italic;
      font-size: 18px;
  }

  @media (max-width: 768px) {
      .contenedor-tarjeta { padding: 30px 20px; }
      .cuerpo-inicio h1 { font-size: 24px; }
      .cuerpo-inicio h3 { font-size: 20px; }
  }
  /* --------------------------------------------------------------------------------- */

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

  .titulo-galeria {
    color: var(--marron-tierra);
    margin-top: 80px;
  }

  .galeria-scroll-container {
    display: flex;
    width: 100%;
    padding: 40px 0;
    overflow-x: auto;
    scrollbar-width: none;
    -webkit-overflow-scrolling: touch;
  }

  .galeria-scroll-container::-webkit-scrollbar {
    display: none;
  }

  .galeria-track {
    display: flex;
    gap: 30px;
    width: max-content;
    padding: 0 40px;
  }

  .item-galeria {
    position: relative;
    width: 320px;
    height: 450px;
    flex-shrink: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: transform 0.4s ease;
    overflow: hidden;
    border-radius: 15px;
    box-shadow: 0 8px 15px rgba(75, 54, 33, 0.2);
    border: 1px solid rgba(212, 175, 55, 0.3);
    cursor: pointer;
  }

  .item-galeria img, .item-galeria video {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: all 0.4s ease;
  }

  @media (min-width: 769px) {
    .item-galeria:hover img, .item-galeria:hover video {
      transform: scale(1.1);
      filter: brightness(0.5);
    }
    .item-galeria:hover .hover-text,
    .item-galeria:hover .btn-ampliar {
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
    opacity: 0;
    transition: opacity 0.4s ease;
    z-index: 2;
    text-shadow: 2px 2px 8px rgba(0,0,0,0.9);
    pointer-events: none;
    text-transform: uppercase;
  }

  .btn-ampliar {
    position: absolute;
    bottom: 15%;
    background-color: var(--oro-pistacho);
    color: var(--marron-tierra);
    padding: 12px 25px;
    border-radius: 25px;
    border: none;
    font-weight: bold;
    font-size: 0.9rem;
    text-transform: uppercase;
    opacity: 0;
    transition: all 0.4s ease;
    z-index: 2;
    box-shadow: 0 4px 10px rgba(0,0,0,0.3);
    cursor: pointer;
  }

  /* Animación para móvil (cuando el item pasa por el centro) */
  :global(.item-galeria.active-center img), :global(.item-galeria.active-center video) {
    transform: scale(1.1);
    filter: brightness(0.5);
  }
  :global(.item-galeria.active-center .hover-text),
  :global(.item-galeria.active-center .btn-ampliar) {
    opacity: 1;
  }

  /* MODAL STYLES */
  .modal-overlay {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(45, 30, 18, 0.95);
    z-index: 10000;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
  }

  .modal-contenido img, .video-full {
    max-width: 100%;
    max-height: 85vh;
    border-radius: 8px;
    border: 3px solid var(--oro-pistacho);
  }

  .boton-cerrar {
    position: absolute;
    top: 20px; right: 20px;
    background: var(--oro-pistacho);
    color: var(--marron-tierra);
    border: none;
    width: 45px; height: 45px;
    border-radius: 50%;
    font-size: 1.5rem;
    font-weight: bold;
    cursor: pointer;
    z-index: 10001;
  }

  @media (max-width: 768px) {
    .item-galeria { width: 280px; height: 380px; }
    h1 { font-size: 1.5rem; }
  }

  .flourish-embed { width: 100%; margin-top: 20px; }
  * { box-sizing: border-box; }
</style>