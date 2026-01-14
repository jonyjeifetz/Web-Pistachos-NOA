<script>
  import { onMount } from 'svelte';
  import { fade, scale } from 'svelte/transition';

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

  let galeriaContainer;
  let frameId; 
  let itemSeleccionado = null; 

  const animar = () => {
    if (galeriaContainer && !itemSeleccionado) {
      galeriaContainer.scrollLeft += 1;
      
      if (galeriaContainer.scrollLeft >= galeriaContainer.scrollWidth / 2) {
        galeriaContainer.scrollLeft = 0;
      }
      detectarCentro();
    }
    frameId = requestAnimationFrame(animar);
  };

  const detectarCentro = () => {
    const items = galeriaContainer.querySelectorAll('.item-galeria');
    const centroPantalla = window.innerWidth / 2;

    items.forEach(item => {
      const rect = item.getBoundingClientRect();
      if (rect.left < centroPantalla && rect.right > centroPantalla) {
        item.classList.add('active-center');
      } else {
        item.classList.remove('active-center');
      }
    });
  };

  function abrirModal(item) {
    itemSeleccionado = item;
  }

  function cerrarModal() {
    itemSeleccionado = null;
  }

  onMount(() => {
    frameId = requestAnimationFrame(animar);

    const esMovil = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
    
    if (!esMovil) {
      galeriaContainer.addEventListener('mouseenter', () => { if(!itemSeleccionado) itemSeleccionado = true });
      galeriaContainer.addEventListener('mouseleave', () => { if(itemSeleccionado === true) itemSeleccionado = null });
    }

    return () => cancelAnimationFrame(frameId);
  });

  function manejarError(e) {
    e.target.closest('.item-galeria').style.display = 'none';
  }
</script>

<div class="seccion-galeria">
  <div class="titulos">
    <h1>Nuestra Producción</h1>
    <p>La Rioja, Argentina</p>
  </div>

  <div class="galeria-wrapper" bind:this={galeriaContainer}>
    <div class="galeria-content">
      {#each [1, 2] as loop}
        {#each baseItems as item}
          <div class="item-galeria" on:click={() => abrirModal(item)}>
            {#if item.tipo === 'foto'}
              <img src={item.url} alt="Pistachos Riojanos" loading="lazy" on:error={manejarError} />
            {:else}
              <video src={item.url} autoplay muted loop playsinline on:error={manejarError}></video>
            {/if}
            <div class="zoom-overlay"><span>🔍 AMPLIAR</span></div>
          </div>
        {/each}
      {/each}
    </div>
  </div>

  {#if itemSeleccionado && typeof itemSeleccionado === 'object'}
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

<style>
  /* --- VARIABLES --- */
  :root {
    --oro-pistacho: #D4AF37;
    --verde-oliva: #6B8E23;
    --marron-tierra: #4B3621;
    --crema-arena: #FDFBF7;
  }

  .seccion-galeria {
    background-color: var(--verde-oliva); /* Verde institucional de fondo */
    padding: 60px 0;
    overflow: hidden;
    border-top: 4px solid var(--oro-pistacho); /* Separador dorado */
  }

  .titulos {
    text-align: center;
    color: var(--crema-arena); /* Texto claro para contraste sobre verde */
    margin-bottom: 30px;
    font-family: 'Montserrat', sans-serif;
  }

  .titulos h1 { 
    font-size: 2.2rem; 
    margin: 0; 
    text-transform: uppercase; 
    letter-spacing: 2px;
  }

  .titulos p {
    font-size: 1.1rem;
    opacity: 0.9;
    color: var(--oro-pistacho); /* Subtítulo en dorado */
    font-weight: bold;
  }

  .galeria-wrapper {
    width: 100%;
    height: 400px;
    overflow-x: auto;
    overflow-y: hidden;
    white-space: nowrap;
    scrollbar-width: none;
    cursor: pointer;
    -webkit-overflow-scrolling: touch;
    scroll-behavior: auto;
  }

  .galeria-wrapper::-webkit-scrollbar { display: none; }

  .galeria-content {
    display: flex;
    width: max-content;
    align-items: center;
  }

  .item-galeria {
    position: relative;
    flex: 0 0 500px;
    height: 380px;
    margin: 0 15px;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 10px 25px rgba(0,0,0,0.3);
    background-color: var(--marron-tierra);
    transition: transform 0.4s ease;
    user-select: none;
    border: 2px solid transparent;
  }

  /* Marco dorado para el item que pasa por el centro */
  :global(.item-galeria.active-center) {
    border-color: var(--oro-pistacho);
  }

  .item-galeria img, .item-galeria video {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    pointer-events: none;
    transition: transform 0.4s ease, filter 0.4s ease;
  }

  .zoom-overlay {
    position: absolute;
    top: 0; left: 0; width: 100%; height: 100%;
    background: rgba(75, 54, 33, 0.7); /* Marrón tierra con transparencia */
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0;
    transition: opacity 0.4s ease;
    color: var(--crema-arena);
    font-weight: 600;
    letter-spacing: 2px;
    font-family: 'Montserrat', sans-serif;
    z-index: 5; 
  }

  .zoom-overlay span {
    border: 2px solid var(--oro-pistacho);
    padding: 10px 20px;
    border-radius: 5px;
  }

  /* ACTIVACIÓN */
  .item-galeria:hover .zoom-overlay,
  :global(.item-galeria.active-center .zoom-overlay) {
    opacity: 1;
  }

  .item-galeria:hover img,
  :global(.item-galeria.active-center img) {
    filter: brightness(0.6);
    transform: scale(1.08);
  }

  /* MODAL */
  .modal-overlay {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(45, 30, 18, 0.97); /* Marrón muy oscuro casi negro */
    z-index: 10000;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
    touch-action: none;
  }

  .modal-contenido img, .video-full {
    max-width: 100%;
    max-height: 85vh;
    border-radius: 8px;
    object-fit: contain;
    border: 3px solid var(--oro-pistacho); /* Marco dorado en el modal */
  }

  .boton-cerrar {
    position: absolute;
    top: 20px; right: 20px;
    background: var(--oro-pistacho);
    color: var(--marron-tierra);
    border: none;
    width: 50px; height: 50px;
    border-radius: 50%;
    font-size: 1.8rem;
    font-weight: bold;
    cursor: pointer;
    z-index: 10001;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 0 4px 10px rgba(0,0,0,0.3);
  }

  @media (max-width: 768px) {
    .item-galeria { flex: 0 0 320px; height: 260px; }
    .galeria-wrapper { height: 300px; }
    .titulos h1 { font-size: 1.6rem; }
  }
</style>