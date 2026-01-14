<div class="cuerpo">
    <h1>Acerca del Pistacho</h1>

    <div class="historia-del-pistacho">
      <h3>Historia del Pistacho</h3>
      <p>El pistacho nace del árbol pistachero o alfóncigo, denominado Pistacia Vera, perteneciente a la misma familia que el del anacardo. Sus orígenes se remontan a Asia occidental y Asia menor, donde comenzaron a cultivarse por primera vez en las zonas más secas de Irán, Turkmenistán, Turquía y Afganistán. 
          De hecho, uno de los requisitos para que el alfóndigo dé sus frutos es que haya sido cultivado en zonas con mucho calor y con ambientes con índices de humedad bajos.
      <br><br>
      Ya conocido por los egipcios, griegos y romanos, el pistacho atravesó Siria para aterrizar en Italia en el siglo I, extendiéndose más tarde por el mediterráneo.
      Hoy en día, este fruto seco ya se cultiva en todo el sur de Europa y el norte de África, además de otras zonas como California, Nuevo México o Austria. Sin embargo, Oriente Medio sigue siendo la cuna del pistacho por excelencia.
      <br><br>
      Y aunque comer pistachos hoy en día es de lo más habitual, no siempre ha sido así. En sus orígenes estaba considerado como un producto exclusivo de las clases sociales más elevadas. Tanto, que una de las leyendas cuenta que hace más de 3.000 años la reina de Saba quedó prendada de este fruto seco, elevándolo a alimento exclusivo de la realeza, 
      y prohibiéndolo al pueblo.
      </p>
    </div>

    <div class="propiedades-del-pistacho">
      <h3>Propiedades del Pistacho</h3>
      <p>La cáscara que recubre el pistacho alberga en su interior un fruto verde enormemente nutritivo, alargado y de un tamaño parecido al de una avellana. Frito, tostado o con un toque extra de sal, el pistacho es igualmente delicioso. Sin embargo, consumirlo crudo sigue siendo la opción más saludable.
      Entre la larga lista de propiedades del pistacho, la Fundación Española de la Nutrición (FEN) destaca los siguientes:</p>
      <ul>
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
      <ul>
          <li>Mejora la salud cardiovascular y el colesterol.</li>
          <li>Rico en antioxidantes.</li>
          <li>Posee un alto valor nutritivo.</li>
          <li>Reduce el estrés y la anemia.</li>
          <li>Ayuda a prevenir la obesidad y la diabetes.</li>
      </ul>            
    </div>         
</div>

<style>
    /* --- VARIABLES REUTILIZABLES --- */
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
        background-color: var(--crema-arena); /* Fondo suave para lectura */
        min-height: 100vh;
    }

    /* --- TÍTULOS --- */
    .cuerpo h1 {
        font-family: 'Montserrat', sans-serif;
        color: var(--marron-tierra);
        font-size: 36px;
        margin-bottom: 40px;
        text-transform: uppercase;
        letter-spacing: 2px;
    }

    .cuerpo h3 {
        font-family: 'Montserrat', sans-serif;
        color: var(--verde-oliva); /* Verde del logo para subsecciones */
        font-size: 28px;
        border-bottom: 2px solid var(--oro-pistacho); /* Subrayado dorado elegante */
        display: inline-block;
        margin-bottom: 20px;
        padding-bottom: 5px;
    }

    /* --- TEXTO Y LISTAS --- */
    .cuerpo p {
        font-family: 'Roboto', sans-serif;
        color: var(--marron-tierra);
        line-height: 1.6;
        text-align: left; /* Mejor legibilidad para textos largos */
        margin-bottom: 30px;
    }

    .cuerpo ul {
        text-align: left;
        color: var(--marron-tierra);
        font-family: 'Roboto', sans-serif;
        line-height: 1.8;
        list-style-position: inside;
        padding: 0;
        margin-bottom: 40px;
    }

    .cuerpo li::marker {
        color: var(--oro-pistacho); /* Viñetas doradas */
        font-weight: bold;
    }

    /* --- CONTENEDORES --- */
    .historia-del-pistacho,
    .propiedades-del-pistacho,
    .beneficios-del-pistacho {
        margin: 0 auto 50px auto;
        max-width: 800px; /* Un poco más ancho para mejor flujo */
    }

    /* --- RESPONSIVE --- */
    @media (max-width: 768px) {
        .cuerpo h1 { font-size: 28px; }
        .cuerpo h3 { font-size: 22px; }
        .cuerpo p { text-align: justify; } /* En móvil el justificado suele verse ordenado */
    }
</style>