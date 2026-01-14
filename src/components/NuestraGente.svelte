<div class="cuerpo">
    <h1>Nuestra Gente</h1>
    <h3>¡Próximamente!</h3>
    <div class="decoracion-oro"></div>
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
        padding: 100px 20px; /* Más espacio para que no se vea vacío */
        text-align: center;
        background-color: var(--crema-arena);
        min-height: 60vh; /* Para que ocupe gran parte de la pantalla */
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .cuerpo h1 {
        font-family: 'Montserrat', sans-serif;
        color: var(--marron-tierra);
        font-size: 42px;
        text-transform: uppercase;
        margin-bottom: 10px;
        letter-spacing: 2px;
    }

    .cuerpo h3 {
        font-family: 'Montserrat', sans-serif;
        color: var(--verde-oliva);
        font-size: 28px;
        font-weight: 300;
        margin-top: 0;
    }

    /* Una línea decorativa para que no se vea tan simple */
    .decoracion-oro {
        width: 60px;
        height: 4px;
        background-color: var(--oro-pistacho);
        margin-top: 20px;
        border-radius: 2px;
    }

    /* RESPONSIVE */
    @media (max-width: 768px) {
        .cuerpo h1 {
            font-size: 32px;
        }
        .cuerpo h3 {
            font-size: 24px;
        }
    }
</style>