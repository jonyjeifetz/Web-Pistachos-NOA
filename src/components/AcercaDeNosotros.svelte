<div class="cuerpo">
    <h1>Acerca de Nosotros</h1>

    <div class="nuestros-valores">
        <h3>Nuestros valores</h3>
        <div style="display: flex; align-items: center; justify-content: space-between;">
            <!-- Imagen -->
            <img
              src="./images/Compromiso.jpeg"
              alt="Compromiso"
              style="width: 40%; height: auto;" 
            />
            <!-- Texto -->
            <p style="flex: 1; text-align: left; margin-top: 0; padding-left: 10px;">
              <strong style="text-decoration: underline;">Compromiso:</strong> Construimos relaciones de largo plazo con nuestros colaboradores, clientes, proveedores y todas las partes interesadas.
            </p>
          </div>
        <br>
        <div style="display: flex; align-items: center; justify-content: space-between; flex-direction: row-reverse;">
            <!-- Imagen -->
            <img
              src="./images/Creatividad.jpeg"
              alt="Innovación"
              style="width: 40%; height: auto;"  
            />
            <!-- Texto -->
            <p style="flex: 1; text-align: left; margin-top: 0; padding-right: 10px;">
              <strong style="text-decoration: underline;">Creatividad:</strong> Pensar, repensar, co-crear buscando mejores soluciones que nos permitan dar lo mejor de nosotros.
            </p>
          </div>
        <br>
        <div style="display: flex; align-items: center; justify-content: space-between;">
            <!-- Imagen -->
            <img
              src="./images/Transparencia.jpeg"
              alt="Transparencia"
              style="width: 40%; height: auto;" 
            />
            <!-- Texto -->
            <p style="flex: 1; text-align: left; margin-top: 0; padding-left: 10px;">
              <strong style="text-decoration: underline;">Transparencia:</strong> Comunicamos internamente las razones de nuestras acciones con el objetivo de crear conocimiento de manera colectiva y poder delegar la toma de decisiones. Recibimos positivamente toda retroalimentación de nuestros colaboradores.
            </p>
          </div>
        <br>
        <div style="display: flex; align-items: center; justify-content: space-between;">
            <!-- Texto -->
            <p style="flex: 1; text-align: left; margin-top: 0; padding-right: 10px;">
              <strong style="text-decoration: underline;">Sinergia:</strong> Contribuimos con el otro para la concreción de los objetivos y obtener resultados más positivos.
            </p>
            <!-- Imagen -->
            <img
              src="./images/Sinergia.jpeg"
              alt="Sinergia"
              style="width: 40%; height: auto;"  
            />
          </div>
        <br>
        <div style="display: flex; align-items: center; justify-content: space-between;">
            <!-- Imagen -->
            <img
              src="./images/Convivencia Positiva.jpeg"
              alt="Convivencia Positiva"
              style="width: 40%; height: auto;"  
            />
            <!-- Texto -->
            <p style="flex: 1; text-align: left; margin-top: 0; padding-left: 10px;">
              <strong style="text-decoration: underline;">Convivencia Positiva:</strong> Mantenemos vínculos saludables y propiciamos la felicidad y el disfrute durante el desarrollo de la actividad laboral.
            </p>
          </div>
          
        <br>
        <div style="display: flex; align-items: center; justify-content: space-between;">
            <!-- Texto -->
            <p style="flex: 1; text-align: left; margin-top: 0; padding-right: 10px;">
                <strong style="text-decoration: underline;">Crecimiento y Desarrollo:</strong> Alentamos el crecimiento y desarrollo de todos nuestros colaboradores y clientes.
            </p>
            <!-- Imagen -->
            <img 
                src="./images/Crecimiento y Desarrollo.jpeg" 
                alt="Crecimiento y Desarrollo"
                style="width: 40%; height: auto;" 
            />
        </div>
    </div>
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

    .acerca-de-nosotros {
    text-align: center; /* Centra el contenido */
    margin: 20px 0; /* Espacio arriba y abajo */
    }

    .nuestros-valores {
        text-align: center; /* Centra el contenido */
        margin: 0 auto; /* Centra el contenido */
        max-width: 650px; /* Ancho máximo del contenido */
    }

    .acerca-de-nosotros h1 {
        margin-bottom: 10px; /* Reduce la distancia entre el título principal y el siguiente contenido */
    }

    .nuestros-valores h3 {
        margin-top: 20px; /* Espaciado uniforme antes del subtítulo */
        margin-bottom: 15px; /* Espaciado uniforme después del subtítulo */
    }

    .nuestros-valores p {
        text-align: left; /* Alinea el texto a la izquierda */
        margin-top: 0; /* Evita espacio adicional antes del contenido */
        margin-bottom: 20px; /* Espaciado uniforme después del contenido */
    }

    .nuestros-valores strong {
        text-decoration: underline; /* Mantiene el subrayado para destacar los valores */
        font-weight: bold; /* Asegura que el texto sea negrita */
    }
</style>