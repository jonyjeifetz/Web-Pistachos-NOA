<script>
  import { onMount } from 'svelte';

  const recetas = [
    { url: './images/Brownie de Pistacho.jpeg', titulo: 'Brownie de Pistacho', pdf: './Recetas/Receta Brownie de Pistacho.pdf' },
    { url: './images/Baklava.jpeg', titulo: 'Baklava de Pistacho', pdf: './Recetas/Receta Baklava de Pistacho.pdf' },
    { url: './images/Queso.jpeg', titulo: 'Queso con Pistacho', pdf: './Recetas/Receta Queso de Pistacho.pdf' },
    { url: './images/Crema de Pistacho.jpeg', titulo: 'Crema de Pistacho', pdf: './Recetas/Receta Crema Pistacho.pdf' },
    { url: './images/Trufas.jpeg', titulo: 'Trufas de Pistacho, Palta y Chocolate', pdf: './Recetas/Receta Trufas de Pistacho, Palta y Chocolate.pdf' }
  ];

  let galeriaContainer;
  let frameId; 

  const animar = () => {
    if (galeriaContainer) {
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

  onMount(() => {
    frameId = requestAnimationFrame(animar);
    const esMovil = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
    
    if (!esMovil) {
      galeriaContainer.addEventListener('mouseenter', () => cancelAnimationFrame(frameId));
      galeriaContainer.addEventListener('mouseleave', () => {
        frameId = requestAnimationFrame(animar);
      });
    }
    return () => cancelAnimationFrame(frameId);
  });
</script>

<div class="seccion-recetas-nueva">
  <div class="titulos">
    <h1>Recetas Creativas</h1>
    <p class="subtitulo-destacado">De Catamarca a Tu Mesa</p>
  </div>

  <div class="galeria-wrapper" bind:this={galeriaContainer}>
    <div class="galeria-track">
      {#each [1, 2] as loop}
        {#each recetas as receta}
          <a href={receta.pdf} target="_blank" class="item-galeria">
            <img src={receta.url} alt={receta.titulo} loading="lazy" />
            <div class="zoom-overlay">
              <div class="info-receta">
                <span class="titulo-item">{receta.titulo}</span>
                <span class="btn-fake">📖 VER RECETA</span>
              </div>
            </div>
          </a>
        {/each}
      {/each}
    </div>
  </div>
</div>

<style>
  :root {
    --oro-pistacho: #D4AF37;
    --verde-oliva: #6B8E23;
    --marron-tierra: #4B3621;
    --crema-arena: #FDFBF7;
  }

  .seccion-recetas-nueva {
    background-color: var(--crema-arena);
    /* Ajustado el padding superior para que se vea bien pegado al menú */
    padding: 60px 0 80px 0; 
    overflow: hidden;
    /* SE ELIMINÓ EL border-top PARA QUITAR LA LÍNEA DEBAJO DEL MENÚ */
    border-top: none; 
  }

  .titulos {
    text-align: center;
    color: var(--marron-tierra);
    margin-bottom: 50px;
    font-family: 'Montserrat', sans-serif;
  }

  .titulos h1 { 
    font-size: 2.5rem;
    margin: 0; 
    text-transform: uppercase; 
    letter-spacing: 3px;
  }

  .subtitulo-destacado {
    font-size: 1.8rem;
    color: var(--verde-oliva);
    font-weight: bold;
    margin-top: 15px;
    letter-spacing: 1px;
    text-transform: none;
  }

  .galeria-wrapper {
    width: 100%;
    height: 450px;
    overflow-x: auto;
    scrollbar-width: none;
    cursor: pointer;
  }

  .galeria-wrapper::-webkit-scrollbar { display: none; }

  .galeria-track {
    display: flex;
    width: max-content;
    align-items: center;
    height: 100%;
  }

  .item-galeria {
    position: relative;
    flex: 0 0 500px;
    height: 400px;
    margin: 0 15px;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 10px 25px rgba(75, 54, 33, 0.2);
    background-color: var(--marron-tierra);
    transition: transform 0.4s ease;
    border: 2px solid transparent;
    text-decoration: none;
    display: block;
  }

  :global(.item-galeria.active-center) {
    border-color: var(--oro-pistacho);
    transform: scale(1.02);
  }

  .item-galeria img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.4s ease, filter 0.4s ease;
  }

  .zoom-overlay {
    position: absolute;
    top: 0; left: 0; width: 100%; height: 100%;
    background: rgba(45, 30, 18, 0.75);
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0;
    transition: opacity 0.4s ease;
    color: var(--crema-arena);
    z-index: 5; 
  }

  .info-receta {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    padding: 0 30px;
    text-align: center;
  }

  .titulo-item {
    font-family: 'Montserrat', sans-serif;
    font-size: 1.5rem;
    font-weight: bold;
    text-transform: uppercase;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
    white-space: normal;
  }

  .btn-fake {
    border: 2px solid var(--oro-pistacho);
    padding: 10px 25px;
    border-radius: 25px;
    font-weight: 600;
    background: var(--oro-pistacho);
    color: var(--marron-tierra);
  }

  .item-galeria:hover .zoom-overlay,
  :global(.item-galeria.active-center .zoom-overlay) {
    opacity: 1;
  }

  .item-galeria:hover img,
  :global(.item-galeria.active-center img) {
    filter: brightness(0.4);
  }

  @media (max-width: 768px) {
    .item-galeria { flex: 0 0 320px; height: 350px; }
    .galeria-wrapper { height: 400px; }
    .titulos h1 { font-size: 1.8rem; }
    .subtitulo-destacado { font-size: 1.3rem; }
    .titulo-item { font-size: 1.1rem; }
    .seccion-recetas-nueva { padding: 40px 0 60px 0; }
  }
</style>