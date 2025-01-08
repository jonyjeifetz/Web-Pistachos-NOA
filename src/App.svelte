<!-- Codigo J-S -->

<script>
  window.onload = function() {
    // Número de teléfono para WhatsApp
    var phoneNumber = "+5491127161950"; 
    var prewrittenMessage = "¡Hola! Estoy interesado en saber más sobre los pistachos de La Rioja.";
    var encodedMessage = encodeURIComponent(prewrittenMessage);
    var emailAddress = "info@pistachosriojanos.com"; 
    
    var instagramLink = document.getElementById("instagram-link");
    var whatsappLink = document.getElementById("whatsapp-link");
    var gmailLink = document.getElementById("gmail-link");
    
    var isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
    
    if (isMobile && !/iPad/i.test(navigator.userAgent)) {
      whatsappLink.href = "https://wa.me/" + phoneNumber + "?text=" + encodedMessage;
      instagramLink.href = "instagram://user?username=pistachosriojanos";
      gmailLink.href = "mailto:" + emailAddress + "?subject=Mas Informacion&body=" + encodedMessage;
    } else {
      whatsappLink.href = "https://web.whatsapp.com/send?phone=" + phoneNumber + "&text=" + encodedMessage;
      instagramLink.href = "https://www.instagram.com/pistachosriojanos";
      gmailLink.href = "https://mail.google.com/mail/?view=cm&fs=1&to=" + emailAddress + "&su=Mas%20Informacion&body=" + encodedMessage;
    }

    // Activar la clase .show-hover cuando las recetas son completamente visibles
    const recetas = document.querySelectorAll(".receta");

    // Observador de intersección
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting && entry.intersectionRatio >= 0.7) {
            // Agrega la clase .show-hover si el 70% del elemento es visible
            entry.target.classList.add("show-hover");
          } else {
            // Elimina la clase .show-hover si menos del 70% es visible
            entry.target.classList.remove("show-hover");
          }
        });
      },
      {
        threshold: [0.7] // Detecta cuando al menos el 70% del elemento es visible
      }
    );

    // Observar cada receta
    recetas.forEach((receta) => observer.observe(receta));

    // Alternar manualmente fullscreen en click
    recetas.forEach((receta) => {
      receta.addEventListener("click", () => {
        const isFullscreen = receta.classList.contains("fullscreen");
        // Alternar entre fullscreen y posición original
        receta.classList.toggle("fullscreen");

        // Deshabilitar scroll en el fondo cuando una receta esté en fullscreen
        document.body.style.overflow = isFullscreen ? "auto" : "hidden";
      });
    });

    // Activar automáticamente los hovers en dispositivos táctiles
    if (isMobile) {
      recetas.forEach((receta) => {
        receta.classList.add("show-hover");
      });
    }
  };
</script>

<!-- Codigo HTML -->

<body>
  <main>
    <!-- Header -->
    <div class="header">
      <img
        src="./images/Logo-Pistachos.png"
        alt="Logo-Pistachos-Riojanos"
      />
    </div> 

    <div class="cuerpo">
      <!-- Acerca de Nosotros -->
      <div class="acerca-de-nosotros">
        <h1>Acerca de Nosotros</h1>
        <div class="nuestros-valores">
          <h3>Nuestros valores</h3>
          <p style="text-align: left; margin-top: -3%"><strong style="text-decoration: underline;">Compromiso:</strong> Construimos relaciones de largo plazo con nuestros colaboradores, clientes, proveedores y todas las partes interesadas.
          <br>
          <strong style="text-decoration: underline;">Creatividad:</strong> Pensar, re pensar, co crear buscando mejores soluciones que nos permitan dar lo mejor de nosotros.
          <br>
          <strong style="text-decoration: underline;">Transparencia:</strong> Comunicamos internamente las razones de nuestras acciones con el objetivo de crear conocimiento de manera colectiva y poder delegar la toma de decisiones. Recibimos positivamente toda retroalimentación de nuestros colaboradores.
          <br>
          <strong style="text-decoration: underline;">Sinergia:</strong> Contribuimos con el otro para la concreción de los objetivos y obtener resultados más positivos.
          <br>
          <strong style="text-decoration: underline;">Convivencia Positiva:</strong> Mantenemos vínculos saludables y propiciamos la felicidad y el disfrute durante el desarrollo de la actividad laboral.
          <br>
          <strong style="text-decoration: underline;">Crecimiento y Desarrollo:</strong> Alentamos el crecimiento y desarrollo de todos nuestros colaboradores y clientes.</p>
        </div>
      </div>

      <!-- Acerca del Pistacho -->
      <div class="acerca-del-pistacho">
          <h1>Acerca del Pistacho</h1>
          <div class="historia-del-pistacho">
            <h3>Historia del Pistacho</h3>
            <p style="text-align: left; margin-top: -3%">El pistacho nace del árbol pistachero o alfóncigo, denominado Pistacia Vera, perteneciente a la misma familia que el del anacardo. Sus orígenes se remontan a Asia occidental y Asia menor, donde comenzaron a cultivarse por primera vez en las zonas más secas de Irán, Turkmenistán, Turquía y Afganistán. 
              De hecho, uno de los requisitos para que el alfóndigo dé sus frutos es que haya sido cultivado en zonas con mucho calor y con ambientes con índices de humedad bajos.
            <br>
            Ya conocido por los egipcios, griegos y romanos, el pistacho atravesó Siria para aterrizar en Italia en el siglo I, extendiéndose más tarde por el mediterráneo.
            Hoy en día, este fruto seco ya se cultiva en todo el sur de Europa y el norte de África, además de otras zonas como California, Nuevo México o Austria. Sin embargo, Oriente Medio sigue siendo la cuna del pistacho por excelencia.
            <br>
            Y aunque comer pistachos hoy en día es de lo más habitual, no siempre ha sido así. En sus orígenes estaba considerado como un producto exclusivo de las clases sociales más elevadas. Tanto, que una de las leyendas cuenta que hace más de 3.000 años la reina de Saba quedó prendada de este fruto seco, elevándolo a alimento exclusivo de la realeza, 
            y prohibiéndolo al pueblo.
            </p>
          </div>
          <div class="propiedades-del-pistacho">
            <h3>Propiedades del Pistacho</h3>
            <p style="text-align: left; margin-top: -3%">La cáscara que recubre el pistacho alberga en su interior un fruto verde enormemente nutritivo, alargado y de un tamaño parecido al de una avellana. Frito, tostado o con un toque extra de sal, el pistacho es igualmente delicioso. Sin embargo, consumirlo crudo sigue siendo la opción más saludable.
            Entre la larga lista de propiedades del pistacho, la Fundación Española de la Nutrición (FEN) destaca los siguientes:</p>
            <ul style="text-align: left; margin-top: -3%; list-style-position: inside; padding-left: 0; color: #FFFFFF; display: inline-block;">
              <li>Alto contenido en grasas insaturadas (grasas buenas).</li>
              <li>Gran aporte de hidratos de carbono.</li>
              <li>Buena fuente de proteínas vegetales.</li>
              <li>Elevado poder antioxidante.</li>
              <li>Abundante contenido de vitaminas B6 y E, zinc, potasio y fósforo.</li>
              <li>Muy ricos en magnesio, hierro y calcio.</li>
            </ul> 
          </div>
          <div class="beneficios-del-pistacho">
            <h3>Beneficios del Pistacho</h3>
            <ul style="text-align: left; margin-top: -1%; list-style-position: inside; padding-left: 0; color: #FFFFFF; display: inline-block;">
              <li>Mejora la salud cardiovascular y el colesterol.</li>
              <li>Rico en antioxidantes.</li>
              <li>Posee un alto valor nutritivo.</li>
              <li>Reduce el estrés y la anemia.</li>
              <li>Ayuda a prevenir la obesidad y la diabetes.</li>
            </ul>            
          </div>         
      </div>
      <!-- Mapa -->
      <h1>De La Rioja al mundo: nuestro alcance</h1>
      <div class="flourish-embed flourish-map" data-src="visualisation/20858873"><script src="https://public.flourish.studio/resources/embed.js"></script><noscript><img src="https://public.flourish.studio/visualisation/20858873/thumbnail" width="100%" alt="map visualization" /></noscript></div>
      <br>

      <!-- Recetas -->
      <h1>De La Rioja a Tu Mesa: Recetas Creativas con Pistacho</h1>
      <div class="recetas-container">
        <div class="recetas">
          <!-- Receta 1 -->
          <div class="receta">
            <img src="./images/Brownie de Pistacho.jpeg" alt="Brownie de Pistacho" />
            <div class="hover-text">Brownie de Pistacho</div>
            <a href="https://drive.google.com/file/d/1ASjwHNIaNYszFCMRZSmtb848PJkgLRZg/view?usp=sharing" target="_blank" class="btn-ver-receta">Ver receta</a>
          </div>
          <!-- Receta 2 -->
          <div class="receta">
            <img src="./images/Baklava.jpeg" alt="Baklava" />
            <div class="hover-text">Baklava de Pistacho</div>
            <a href="https://drive.google.com/file/d/1r3VQnVpUyxmnwXWGs8SemCGaLiBKmScE/view?usp=sharing" target="_blank" class="btn-ver-receta">Ver receta</a>
          </div>
          <!-- Receta 3 -->
          <div class="receta">
            <img src="./images/Queso.jpeg" alt="Queso" />
            <div class="hover-text">Queso con Pistacho</div>
            <a href="https://drive.google.com/file/d/1qWyoHTN51e4i0o8e8_FapCsSJhkCUc9t/view?usp=sharing" target="_blank" class="btn-ver-receta">Ver receta</a>
          </div>
          <!-- Receta 4 -->
          <div class="receta">
            <img src="./images/Crema de Pistacho.jpeg" alt="Crema de Pistacho" />
            <div class="hover-text">Crema de Pistacho</div>
            <a href="https://drive.google.com/file/d/1EaWcLLZRK1M0UEYfJ9T_Xm8azDYD8pAA/view?usp=sharing" target="_blank" class="btn-ver-receta" >Ver receta</a>
          </div>
          <!-- Receta 5 -->
          <div class="receta">
            <img src="./images/Trufas.jpeg" alt="Trufas de Pistacho" />
            <div class="hover-text">Trufas de Pistacho, Palta y Chocolate</div>
            <a href="https://drive.google.com/file/d/166AyeBcA_4nVvagtlAALTjaTE_pYXHzF/view?usp=sharing" target="_blank" class="btn-ver-receta">Ver receta</a>
          </div> 
        </div>
      </div>

      <!-- Ultimas noticias del pistacho -->
      <h1 style="font-family: montserrat;">Ultimas Noticias del Pistacho</h1>

      <!-- Responsabilidad Social Empresarial -->
      <h1 style="font-family: montserrat;">Responsabilidad Social Empresarial</h1>

      <!-- Nuestra Gente -->
      <h1 style="font-family: montserrat;">Nuestra Gente</h1>
    </div>

    <div class="footer">
      <h4>¿Preguntas? ¡Estamos a un clic de distancia!</h4>
    
      <div class="social-icons">
        <a id="instagram-link" href="#" target="_blank">
          <img src="./images/Instagram.png" alt="Instagram" />
        </a>
        <a id="whatsapp-link" href="#" target="_blank">
          <img src="./images/What's App.png" alt="What's App" />
        </a>
        <a id="gmail-link" href="#" target="_blank">
          <img src="./images/Gmail.png" alt="Gmail" />
        </a>
      </div>
    
      <div class="footer-copy">
        <p>© 2024 por Jonathan Jeifetz</p>
      </div>
    </div> 
  </main>
</body>

<!-- Codigo CSS -->

<style>
 /* Body */
 body{
    background-color:#80A54D; /* Color Pistacho */
    font-family: Arial, sans-serif; /* Fuente básica */
    margin: 0; /* Elimina el margen por defecto del body */
    padding: 0; /* Elimina el relleno por defecto del body */
    overflow-x: hidden; /* Evita el scroll horizontal */
    width: 100%; /* Ajusta el ancho al 100% */
  }

 /* Cuerpo */
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
          font-size: 24px; /* Tamaño más pequeño para pantallas móviles */
          line-height: 1.2; /* Ajuste del interlineado para evitar exceso de espacio */
          margin-bottom: 5px; /* Menos espacio debajo del título */
      }
  }

  .cuerpo p {
    font-family: roboto;
    color: #FFFFFF;
    padding: 1rem 0;
    text-align: center;
  }

  /* Header */
 .header{
    background-color: #FFFFFF; /* Color de fondo */
    text-align: center; /* Centra el contenido */
  }

 .header img {
    max-width: 100%; /* Hace que la imagen no se salga del contenedor */
    height: auto; /* Mantiene la relación de aspecto */
  }

  /* Acerca de Nosotros */
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

  /* Acerca del Pistacho */
  .acerca-del-pistacho {
    text-align: center; /* Centra el contenido */
    margin: 20px 0; /* Espacio arriba y abajo */
  }

  .historia-del-pistacho,
  .propiedades-del-pistacho,
  .beneficios-del-pistacho {
      text-align: center; /* Centra el contenido */
      margin: 0 auto; /* Centra el contenido */
      max-width: 650px; /* Ancho máximo del contenido */
  }

  .acerca-del-pistacho h1 {
      margin-bottom: 20px; /* Espaciado uniforme después del título principal */
  }

  .historia-del-pistacho h3,
  .propiedades-del-pistacho h3,
  .beneficios-del-pistacho h3 {
      margin-top: 30px; /* Espaciado uniforme antes de los subtítulos */
      margin-bottom: 15px; /* Espaciado uniforme después de los subtítulos */
  }

  .historia-del-pistacho p,
  .propiedades-del-pistacho p,
  .propiedades-del-pistacho ul,
  .beneficios-del-pistacho ul {
      margin-top: 0; /* Evita espacio adicional antes del contenido */
      margin-bottom: 20px; /* Espaciado uniforme después del contenido */
  }

    /* Recetas */
  .recetas-container {
      display: flex;
      justify-content: flex-start;
      width: 100%;
      padding: 20px;
      margin-bottom: 20px;
      overflow-x: auto;
      scrollbar-width: none;
  }

  .recetas-container::-webkit-scrollbar {
      display: none;
  }

  .recetas {
      display: flex;
      gap: 20px;
      width: max-content;
      flex-wrap: nowrap;
  }

  .receta {
      position: relative;
      width: 300px;  /* Tamaño base para pantallas grandes */
      height: 400px;
      text-align: center;
      flex-shrink: 0;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      transition: transform 0.3s ease;
  }

  /* Ajuste de tamaño de imagen */
  .receta img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.3s ease;
      border-radius: 10px;
  }

  /* Efecto hover para dispositivos con mouse */
  .receta:hover img {
      transform: scale(1.1);  /* Agranda la imagen cuando se hace hover */
  }

  /* Hover-text */
  .hover-text {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background-color: black;
      color: white;
      font-size: 24px;
      font-weight: bold;
      padding: 10px;
      border-radius: 10px;
      opacity: 0;
      transition: opacity 0.3s ease;
  }

  .receta:hover .hover-text {
      opacity: 1;  /* Muestra el texto cuando la receta tiene hover */
  }

  /* Botón */
  .btn-ver-receta {
      background-color: black;
      color: white;
      padding: 10px 20px;
      border-radius: 20px;
      text-decoration: none;
      font-weight: bold;
      opacity: 0;
      transition: opacity 0.3s ease, transform 0.3s ease;
      margin: 0 auto;
      width: fit-content;
      position: relative;
      z-index: 1;
  }

  .receta:hover .btn-ver-receta {
      opacity: 1;
      transform: translateY(-10px) scale(1.1);  /* Efecto en el botón */
  }

  /* Ajustes para dispositivos pequeños */
  @media (max-width: 768px) {
      .receta {
          width: 250px;  /* Reduce el tamaño de cada receta en pantallas pequeñas */
          height: 350px;
      }

      .receta img {
          width: 100%;
          height: auto;  /* Ajuste para que las imágenes se mantengan proporcionadas */
      }
  }

  @media (max-width: 480px) {
      .receta {
          width: 200px;  /* Ajuste para pantallas aún más pequeñas */
          height: 300px;
      }

      .receta img {
          width: 100%;
          height: auto;
      }

      .hover-text {
          font-size: 18px;  /* Ajusta el tamaño de la fuente para pantallas pequeñas */
          padding: 5px;
      }

      .btn-ver-receta {
          font-size: 14px;  /* Reduce el tamaño del texto en el botón */
          padding: 8px 16px;  /* Ajusta el tamaño del botón */
      }
  }
  
  /* Footer */
    .footer {
    background-color: #FFFFFF; /* Color de fondo */
    display: flex; /* Alinea los elementos en columna */
    flex-direction: column; /* Coloca los elementos en columna (título, imágenes, copyright) */
    align-items: center; /* Centra los elementos horizontalmente */
    padding: 20px 0; /* Añade espacio arriba y abajo */
  }

  .footer h4 {
    font-family: montserrat; /* Fuente del título */
    text-align: center; /* Centra el texto */
    margin-top: 0; /* Elimina el margen superior innecesario */
    margin-bottom: 20px; /* Espacio entre el título y las imágenes */
  }

  .footer .social-icons {
    display: flex; /* Alinea las imágenes en una fila */
    justify-content: center; /* Centra las imágenes */
    align-items: center; /* Asegura la alineación vertical */
    gap: 150px; /* Espacio entre las imágenes */
    flex-wrap: wrap; /* Permite que las imágenes pasen a la siguiente línea si no caben */
    margin: 0 auto; /* Centrado horizontal */
    padding: 1rem; /* Espaciado interno opcional */
  }

  .footer img {
      max-width: 50px; /* Ajusta el tamaño de las imágenes */
      height: auto; /* Mantiene la relación de aspecto */
      display: block; /* Evita espacios extra en línea */
      margin: 0; /* Asegura que no haya márgenes adicionales */
  }

  /* Estilos para dispositivos móviles */
  @media (max-width: 600px) {
      .footer .social-icons {
          gap: 7rem; /* Reduce el espacio entre las imágenes */
      }

      .footer img {
          max-width: 30px; /* Reduce el tamaño de las imágenes */
      }
  }


  /* Estilo del texto de copyright */
  .footer-copy {
    margin-top: 20px; /* Espacio entre las imágenes y el copyright */
    font-size: 14px; /* Tamaño de fuente */
    color: #666; /* Color del texto */
    text-align: center; /* Centra el texto */
  }

  /* Borrado de marca de agua flourish */
  .flourish-embed {
    width: 100%;
    max-width: 100%; /* Impide que el mapa se salga de la pantalla */
    overflow-x: hidden; /* Evita el desplazamiento horizontal del mapa */
  }

  * {
    box-sizing: border-box; /* Asegura que los márgenes y rellenos no causen desbordes */
  }

</style>
