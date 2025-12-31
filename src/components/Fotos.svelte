
<div class="cuerpo">
    <h1 style="font-family: montserrat;">Fotos</h1>
    <br>
    <br>
    <h3 style="font-family: montserrat;">Proximamente!</h3>
</div>

<style>
    .cuerpo{
        margin: 8px; /* Margen predeterminado */
        padding: 0;  /* Relleno desactivado para evitar inconsistencias */
        text-align: center; /* Centra el contenido */
        flex: 1; /* Ocupa el espacio restante entre el header y el footer */
    }

    .cuerpo h1, h3 {
        font-family: montserrat;
        color: #FFFFFF;
    }

    /* Ajustes generales para los h1 en pantallas grandes */
    .cuerpo h1 {
        font-size: 36px; /* Tamaño de fuente por defecto */
        margin-bottom: 10px; /* Espacio debajo del título */
    }

    @media (max-width: 768px) {
    .cuerpo h1 {
        font-size: 32px; /* Tamaño ajustado para pantallas móviles */
        line-height: 1.2; /* Ajuste del interlineado para evitar exceso de espacio */
        margin-bottom: 5px; /* Menos espacio debajo del título */
        font-weight: bold; /* Hacer que el título sea en negrita */
    }

    .cuerpo h3 {
        font-size: 26px; /* Tamaño ajustado para h3 en pantallas móviles */
        line-height: 1.3; /* Ajuste del interlineado para h3 */
        margin-bottom: 5px; /* Ajuste del espacio debajo de h3 */
    }
    }

    .cuerpo p {
        font-family: roboto;
        color: #FFFFFF;
        padding: 1rem 0;
        text-align: center;
    }
</style>