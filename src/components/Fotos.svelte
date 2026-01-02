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
      // En PC frenamos si el mouse entra (opcional, si querés que no frene nunca podés quitar esto)
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
  .seccion-galeria {
    background-color: #80A54D;
    padding: 60px 0;
    overflow: hidden;
  }

  .titulos {
    text-align: center;
    color: white;
    margin-bottom: 30px;
    font-family: 'Montserrat', sans-serif;
  }

  .titulos h1 { font-size: 2.2rem; margin: 0; text-transform: uppercase; }

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
    margin: 0 10px;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: 0 10px 20px rgba(0,0,0,0.2);
    background-color: #709143;
    transition: transform 0.4s ease;
    user-select: none;
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
    background: rgba(0,0,0,0.45);
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0;
    transition: opacity 0.4s ease;
    color: white;
    font-weight: 600;
    letter-spacing: 1px;
    font-family: 'Montserrat', sans-serif;
    z-index: 5; 
  }

  /* ACTIVACIÓN POR HOVER O CENTRO */
  .item-galeria:hover .zoom-overlay,
  :global(.item-galeria.active-center .zoom-overlay) {
    opacity: 1;
  }

  .item-galeria:hover img,
  :global(.item-galeria.active-center img) {
    filter: brightness(0.7);
    transform: scale(1.05);
  }

  /* MODAL */
  .modal-overlay {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(0,0,0,0.95);
    z-index: 10000;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
    touch-action: none;
  }

  .modal-contenido {
    max-width: 95%;
    max-height: 90vh;
  }

  .modal-contenido img, .video-full {
    max-width: 100%;
    max-height: 85vh;
    border-radius: 8px;
    object-fit: contain;
  }

  .boton-cerrar {
    position: absolute;
    top: 20px; right: 20px;
    background: white;
    border: none;
    width: 45px; height: 45px;
    border-radius: 50%;
    font-size: 1.5rem;
    cursor: pointer;
    z-index: 10001;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  @media (max-width: 768px) {
    .item-galeria { flex: 0 0 300px; height: 280px; }
    .galeria-wrapper { height: 320px; }
  }
</style>