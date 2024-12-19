<!-- Codigo J-S -->

<script>
  import { onMount } from 'svelte';

  onMount(() => {
    // Número de teléfono para WhatsApp
    const phoneNumber = "+5491127161950";
    const prewrittenMessage = "¡Hola! Estoy interesado en saber más sobre los pistachos de La Rioja.";
    const encodedMessage = encodeURIComponent(prewrittenMessage);
    const emailAddress = "info@pistachosriojanos.com";

    const instagramLink = document.getElementById("instagram-link");
    const whatsappLink = document.getElementById("whatsapp-link");
    const gmailLink = document.getElementById("gmail-link");

    const isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);

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
          if (entry.isIntersecting && entry.intersectionRatio === 1) {
            // Agrega la clase .show-hover si el elemento está completamente visible
            entry.target.classList.add("show-hover");
          } else {
            // Elimina la clase .show-hover si deja de estar completamente visible
            entry.target.classList.remove("show-hover");
          }
        });
      },
      {
        threshold: [1.0] // Detecta solo cuando el 100% del elemento es visible
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
  });
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
    <!-- Cuerpo -->
    <div class="cuerpo">

      <!-- Mapa de lugares a donde llegamos -->
      <h1>Des La Rioja al mundo: nuestro alcance</h1>
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
            <a href="https://drive.google.com/file/d/1Zbw5SykhiiRfSp2-pC5lcwBqAvM51w4r/view?usp=sharing" target="_blank" class="btn-ver-receta">Ver receta</a>
          </div>
          <!-- Receta 2 -->
          <div class="receta">
            <img src="./images/Baklava.jpeg" alt="Baklava" />
            <div class="hover-text">Baklava de Pistacho</div>
            <a href="https://drive.google.com/file/d/1V6sNBDheU02jBE7tzeNJjLJNlpkNbT8y/view?usp=sharing" target="_blank" class="btn-ver-receta">Ver receta</a>
          </div>
          <!-- Receta 3 -->
          <div class="receta">
            <img src="./images/Queso.jpeg" alt="Queso" />
            <div class="hover-text">Queso con Pistacho</div>
            <a href="https://drive.google.com/file/d/1hwa1G7DXF9gmWTH-C3S8fcfvd9gKICJP/view?usp=sharing" target="_blank" class="btn-ver-receta">Ver receta</a>
          </div>
          <!-- Receta 4 -->
          <div class="receta">
            <img src="./images/Crema de Pistacho.jpeg" alt="Brownie de Pistacho" />
            <div class="hover-text">Crema de Pistacho</div>
            <a href="https://drive.google.com/file/d/1Gv9wytTSmbYasBnLOxM8PZKojaWBYxqJ/view?usp=sharing" target="_blank" class="btn-ver-receta" >Ver receta</a>
          </div>
          <!-- Receta 5 -->
          <div class="receta">
            <img src="./images/Trufas.jpeg" alt="Baklava" />
            <div class="hover-text">Trufas de Pistacho, Palta y Chocolate</div>
            <a href="https://drive.google.com/file/d/1loEPgKMhqq6IPenL4eDia_CM901GDa6R/view?usp=sharing" target="_blank" class="btn-ver-receta">Ver receta</a>
          </div> 
        </div>
      </div>

      <!-- Link a la pagina para vender -->
      <h1 class="PaginaVenta">¡Atrévete a probar el snack que te conquistará! Pistachos frescos y deliciosos te esperan</h1>
      <div class="button-container">
        <a href="https://www.pistachosriojanos.com/" target="_blank">
          <button class="order-button">Haz tu pedido</button>
        </a>
      </div>
      
      <p>¡Esperamos que te guste!</p>
      <!-- Enters para que el Footer quede al final de la Pantalla. Es provisorio hasta que tenga toda la info -->
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <!-- Aca terminan los enters Provisorios -->
    </div>
    <!-- Footer -->
    <div class="footer">
      <!-- Titulo del Footer -->
      <h4>¿Preguntas? ¡Estamos a un clic de distancia!</h4>
    
      <!-- Contenedor de las imágenes (Instagram, WhatsApp, Gmail) -->
      <div class="social-icons">
        <!-- Instagram -->
        <a id="instagram-link" href="#" target="_blank">
          <img src="./images/Instagram.png" alt="Instagram" />
        </a>
        <!-- WhatsApp -->
        <a id="whatsapp-link" href="#" target="_blank">
          <img src="./images/What's App.png" alt="What's App" />
        </a>
        <!-- Gmail -->
        <a id="gmail-link" href="#" target="_blank">
          <img src="./images/Gmail.png" alt="Gmail" />
        </a>
      </div>
    
      <!-- Texto de copyright -->
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

 .cuerpo h1 {
    font-family: montserrat;
    color: #FFFFFF;
  }

  .cuerpo p {
    font-family: roboto;
    color: #FFFFFF;
    padding: 1rem 0;
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
}

/* Ajuste de tamaño de imagen */
.receta img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
    border-radius: 10px;
}

/* Efecto hover */
.receta:hover img {
    transform: scale(1.1);
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
    opacity: 1;
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
    transform: translateY(-10px) scale(1.1);
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





    /* Pagina de Venta */
    .PaginaVenta {
      text-align: center; /* Centra el texto */
      font-size: 2rem; /* Ajusta el tamaño del título */
      margin-bottom: 20px; /* Espacio debajo del título */
    }

  .button-container {
    text-align: center; /* Centra el botón */
  }

  .order-button {
    background-color: black; /* Fondo negro */
    color: white; /* Texto blanco */
    font-size: 1.2rem; /* Tamaño del texto */
    padding: 10px 20px; /* Espaciado dentro del botón */
    border: none; /* Sin bordes */
    border-radius: 5px; /* Bordes redondeados */
    cursor: pointer; /* Cambia el cursor al pasar por encima */
    transition: transform 0.3s ease, background-color 0.3s ease; /* Animación suave */
  }

  .order-button:hover {
    transform: scale(1.1); /* Zoom al pasar el mouse */
    background-color: #333; /* Fondo gris oscuro al hacer hover */
  }

  .receta.hover img {
    transform: scale(1.1); /* Zoom de la imagen */
  }

  .receta.hover .hover-text {
    opacity: 1; /* Muestra el texto al hacer hover */
  }

  .receta.hover .btn-ver-receta {
    opacity: 1; /* Muestra el botón */
    transform: translateY(-10px); /* Pequeño movimiento hacia arriba */
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
    gap: 20px; /* Espacio entre las imágenes */
  }

  .footer img {
    max-width: 50px; /* Ajusta el tamaño de las imágenes */
    height: auto; /* Mantiene la relación de aspecto */
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
