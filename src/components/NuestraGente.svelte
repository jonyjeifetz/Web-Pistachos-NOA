<div class="cuerpo">
    <div class="contenedor-texto">
        <h1>Nuestra Gente</h1>
        <div class="divisor-oro"></div>
        <h3>¡Próximamente!</h3>
        <p>Estamos preparando un espacio para presentar al equipo humano que hace posible la excelencia de nuestros pistachos.</p>
    </div>
</div>

<style>
    :root {
      --oro-pistacho: #D4AF37;
      --verde-oliva: #6B8E23;
      --marron-tierra: #4B3621;
      --crema-arena: #FDFBF7;
    }

    .cuerpo {
        margin: 0;
        padding: 80px 20px;
        text-align: center;
        background-color: var(--crema-arena);
        min-height: 70vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .contenedor-texto {
        max-width: 700px;
        background: white;
        padding: 50px;
        border-radius: 20px;
        box-shadow: 0 10px 30px rgba(75, 54, 33, 0.05);
        border: 1px solid rgba(212, 175, 55, 0.2);
    }

    .cuerpo h1 {
        font-family: 'Montserrat', sans-serif;
        color: var(--verde-oliva);
        font-size: 32px;
        text-transform: uppercase;
        margin: 0;
        letter-spacing: 1px;
    }

    .divisor-oro {
        width: 100px;
        height: 3px;
        background-color: var(--oro-pistacho);
        margin: 25px auto;
    }

    .cuerpo h3 {
        font-family: 'Montserrat', sans-serif;
        color: var(--marron-tierra);
        font-size: 24px;
        margin-bottom: 15px;
    }

    .cuerpo p {
        font-family: 'Montserrat', sans-serif;
        color: var(--marron-tierra);
        opacity: 0.8;
        line-height: 1.5;
        font-style: italic;
    }

    @media (max-width: 768px) {
        .contenedor-texto { padding: 30px 20px; }
        .cuerpo h1 { font-size: 24px; }
        .cuerpo h3 { font-size: 20px; }
    }
</style>