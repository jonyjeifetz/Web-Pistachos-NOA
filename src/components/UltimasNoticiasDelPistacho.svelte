<div class="cuerpo">
    <div class="noticias-header">
        <h1>Últimas Noticias del Pistacho</h1>
        <div class="linea-decorativa"></div>
    </div>
    
    <div class="noticias-placeholder">
        <div class="icono-noticia">📰</div>
        <h3>¡Próximamente!</h3>
        <p>Estamos preparando las novedades más relevantes sobre la cosecha, el mercado y la cultura del pistacho en La Rioja.</p>
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

    .cuerpo {
        margin: 0;
        padding: 60px 20px;
        text-align: center;
        background-color: var(--crema-arena);
        min-height: 75vh;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .noticias-header {
        margin-bottom: 50px;
    }

    .cuerpo h1 {
        font-family: 'Montserrat', sans-serif;
        color: var(--marron-tierra);
        font-size: 36px;
        text-transform: uppercase;
        margin-bottom: 15px;
        letter-spacing: 1px;
    }

    .linea-decorativa {
        width: 80px;
        height: 4px;
        background-color: var(--oro-pistacho);
        margin: 0 auto;
        border-radius: 2px;
    }

    .noticias-placeholder {
        max-width: 600px;
        padding: 40px;
        border: 2px dashed var(--oro-pistacho); /* Estilo "en construcción" elegante */
        border-radius: 15px;
        background-color: rgba(255, 255, 255, 0.5);
    }

    .icono-noticia {
        font-size: 3rem;
        margin-bottom: 10px;
    }

    .cuerpo h3 {
        font-family: 'Montserrat', sans-serif;
        color: var(--verde-oliva);
        font-size: 28px;
        margin: 10px 0;
    }

    .cuerpo p {
        font-family: 'Roboto', sans-serif;
        color: var(--marron-tierra);
        line-height: 1.6;
        font-size: 1.1rem;
        margin-top: 15px;
    }

    /* --- RESPONSIVE --- */
    @media (max-width: 768px) {
        .cuerpo h1 {
            font-size: 28px;
        }
        .noticias-placeholder {
            padding: 30px 15px;
            margin: 0 10px;
        }
        .cuerpo h3 {
            font-size: 22px;
        }
    }
</style>