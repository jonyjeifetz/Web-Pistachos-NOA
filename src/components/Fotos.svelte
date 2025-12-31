<script>
  import { onMount } from 'svelte';
  import { fade, scale } from 'svelte/transition';

  // CONFIGURACIÓN
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
  let scrollInterval;
  let itemSeleccionado = null; // Controla qué imagen se ve en grande

  // Funciones para el Modal
  function abrirModal(item) {
    itemSeleccionado = item;
    pararScroll(); // Pausamos el movimiento mientras mira la foto
  }

  function cerrarModal() {
    itemSeleccionado = null;
    iniciarScroll(); // Reanudamos el movimiento
  }

  const iniciarScroll = () => {
    if (scrollInterval) pararScroll(); // Evita duplicar intervalos
    scrollInterval = setInterval(() => {
      if (galeriaContainer && !itemSeleccionado) {
        galeriaContainer.scrollLeft += 1;
        if (galeriaContainer.scrollLeft >= galeriaContainer.scrollWidth / 2) {
          galeriaContainer.scrollLeft = 0;
        }
      }
    }, 30);
  };

  const pararScroll = () => clearInterval(scrollInterval);

  onMount(() => {
    iniciarScroll();

    // Eventos de pausa manual (hover/touch)
    galeriaContainer.addEventListener('mouseenter', pararScroll);
    galeriaContainer.addEventListener('mouseleave', () => {
        if (!itemSeleccionado) iniciarScroll();
    });

    return () => pararScroll();
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
            <div class="zoom-overlay"><span>🔍 Ver más</span></div>
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
          <img 
            src={itemSeleccionado.url} 
            alt="Vista Completa" 
            transition:scale={{ duration: 300, start: 0.9 }} 
          />
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
    transition: transform 0.3s ease;
  }

  .item-galeria:hover { transform: translateY(-5px); }

  .item-galeria img, .item-galeria video {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }

  /* Capa de "ver más" al pasar el mouse */
  .zoom-overlay {
    position: absolute;
    top: 0; left: 0; width: 100%; height: 100%;
    background: rgba(0,0,0,0.3);
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0;
    transition: opacity 0.3s ease;
    color: white;
    font-weight: bold;
    font-family: 'Montserrat', sans-serif;
  }

  .item-galeria:hover .zoom-overlay { opacity: 1; }

  /* ESTILOS DEL MODAL */
  .modal-overlay {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(0,0,0,0.9);
    z-index: 1000;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
  }

  .modal-contenido {
    max-width: 90%;
    max-height: 90vh;
    display: flex;
    justify-content: center;
  }

  .modal-contenido img, .video-full {
    max-width: 100%;
    max-height: 85vh;
    border-radius: 8px;
    box-shadow: 0 0 30px rgba(0,0,0,0.5);
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
    z-index: 1001;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: background 0.3s;
  }

  .boton-cerrar:hover { background: #ccc; }

  @media (max-width: 768px) {
    .item-galeria { flex: 0 0 300px; height: 280px; }
    .galeria-wrapper { height: 300px; }
  }
</style>