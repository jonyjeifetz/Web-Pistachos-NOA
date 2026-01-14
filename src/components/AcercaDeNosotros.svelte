<div class="cuerpo">
    <h1>Acerca de Nosotros</h1>

    <div class="nuestros-valores">
        <h3>Nuestros valores</h3>
        
        <div class="valor-item">
            <img src="./images/Compromiso.jpeg" alt="Compromiso" />
            <p>
              <strong>Compromiso:</strong> Construimos relaciones de largo plazo con nuestros colaboradores, clientes, proveedores y todas las partes interesadas.
            </p>
        </div>

        <div class="valor-item reverse">
            <img src="./images/Creatividad.jpeg" alt="Innovación" />
            <p>
              <strong>Creatividad:</strong> Pensar, repensar, co-crear buscando mejores soluciones que nos permitan dar lo mejor de nosotros.
            </p>
        </div>

        <div class="valor-item">
            <img src="./images/Transparencia.jpeg" alt="Transparencia" />
            <p>
              <strong>Transparencia:</strong> Comunicamos internamente las razones de nuestras acciones con el objetivo de crear conocimiento de manera colectiva y poder delegar la toma de decisiones. Recibimos positivamente toda retroalimentación de nuestros colaboradores.
            </p>
        </div>

        <div class="valor-item reverse">
            <img src="./images/Sinergia.jpeg" alt="Sinergia" />
            <p>
              <strong>Sinergia:</strong> Contribuimos con el otro para la concreción de los objetivos y obtener resultados más positivos.
            </p>
        </div>

        <div class="valor-item">
            <img src="./images/Convivencia Positiva.jpeg" alt="Convivencia Positiva" />
            <p>
              <strong>Convivencia Positiva:</strong> Mantenemos vínculos saludables y propiciamos la felicidad y el disfrute durante el desarrollo de la actividad laboral.
            </p>
        </div>
          
        <div class="valor-item reverse">
            <img src="./images/Crecimiento y Desarrollo.jpeg" alt="Crecimiento y Desarrollo" />
            <p>
                <strong>Crecimiento y Desarrollo:</strong> Alentamos el crecimiento y desarrollo de todos nuestros colaboradores y clientes.
            </p>
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

    .cuerpo {
        margin: 0;
        padding: 40px 20px;
        text-align: center;
        background-color: var(--crema-arena);
        min-height: 100vh;
    }

    /* --- TÍTULOS --- */
    .cuerpo h1 {
        font-family: 'Montserrat', sans-serif;
        color: var(--marron-tierra);
        font-size: 36px;
        margin-bottom: 20px;
        text-transform: uppercase;
    }

    .cuerpo h3 {
        font-family: 'Montserrat', sans-serif;
        color: var(--verde-oliva);
        font-size: 28px;
        margin-bottom: 40px;
    }

    /* --- ESTRUCTURA DE VALORES --- */
    .nuestros-valores {
        margin: 0 auto;
        max-width: 900px; /* Un poco más ancho para las imágenes */
    }

    .valor-item {
        display: flex;
        align-items: center;
        gap: 20px;
        margin-bottom: 40px;
        background: white; /* Tarjeta blanca para resaltar sobre el fondo crema */
        padding: 15px;
        border-radius: 8px;
        box-shadow: 0 4px 6px rgba(0,0,0,0.05);
        border-left: 5px solid var(--oro-pistacho); /* Detalle de marca */
    }

    .valor-item.reverse {
        flex-direction: row-reverse;
        border-left: none;
        border-right: 5px solid var(--oro-pistacho);
    }

    .valor-item img {
        width: 35%;
        height: auto;
        border-radius: 4px;
        object-fit: cover;
    }

    .valor-item p {
        flex: 1;
        font-family: 'Roboto', sans-serif;
        color: var(--marron-tierra);
        text-align: left;
        line-height: 1.6;
        margin: 0;
    }

    .valor-item strong {
        color: var(--verde-oliva);
        font-size: 1.1rem;
        display: block;
        margin-bottom: 5px;
        text-decoration: none; /* Quitamos subrayado para un look más moderno */
    }

    /* --- RESPONSIVE --- */
    @media (max-width: 768px) {
        .valor-item, .valor-item.reverse {
            flex-direction: column;
            text-align: center;
            border-left: none;
            border-right: none;
            border-top: 5px solid var(--oro-pistacho);
        }

        .valor-item img {
            width: 100%;
        }

        .valor-item p {
            text-align: center;
            padding: 10px 0;
        }

        .cuerpo h1 { font-size: 28px; }
        .cuerpo h3 { font-size: 22px; }
    }
</style>