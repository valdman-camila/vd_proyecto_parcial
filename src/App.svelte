<script>
  /* Importamos d3 para tenerlo disponible */
  import * as d3 from "d3"

  let dataLepidopteraRegion = [
    {anio: 2015, destruccion: 24, diversidad: 23},
    {anio: 2016, destruccion: 33, diversidad: 35},
    {anio: 2017, destruccion: 42, diversidad: 45},
    {anio: 2018, destruccion: 54, diversidad: 56},
    {anio: 2019, destruccion: 63, diversidad: 50},
    {anio: 2020, destruccion: 71, diversidad: 43},
    {anio: 2021, destruccion: 77, diversidad: 38},
    {anio: 2022, destruccion: 87, diversidad: 32},
    {anio: 2023, destruccion: 92, diversidad: 28},
    {anio: 2024, destruccion: 98, diversidad: 25}
  ]

  // Calcular valores mínimos y máximos
  let minDestruccion = d3.min(dataLepidopteraRegion, d => d.destruccion) * 0.22;
  let minDiversidad = d3.min(dataLepidopteraRegion, d => d.diversidad) * 0.22;
  let cantidadMinima = Math.min(minDestruccion, minDiversidad);

  // Encontrar el valor máximo entre ambas variables
  let maxValor = d3.max(dataLepidopteraRegion, d => Math.max(d.destruccion, d.diversidad));

  let altura = d3
    .scaleLinear()
    .domain([0, maxValor])
    .range([0, 500])
</script>

<main>
  <div class="header">
    <img
      src="./images/moth-clipart-original.png"
      width="200"
      alt="Polilla"
    />
    <h3 class="headline">
      <b>Lepidoptera</b>
      Como la diversidad de esta orden esta siendo afectada
    </h3>
  </div>   

  <div class="graph_container">
    <!-- Grafico con polillas -->
    <div class="container">
      {#each dataLepidopteraRegion as item}
        <div class="item_wrapper">
          <div class="labels-wrapper">
            <p class="value-h">{item.destruccion} (H)</p>
            <p class="value-d">{item.diversidad} (D)</p>
          </div>
            <img class="bigMoth" src="./images/moth-illustration-by-Vexels.svg" alt="silkmoth" style="height: {(altura(item.diversidad - cantidadMinima) * 1.5)}px"/>
            <img class="LeafB" src="./images/double_leaf.svg" alt="big leaf" style="height:{altura(item.diversidad - cantidadMinima) *1.5}px" />
            <img class="smallMoth" src="./images/grey-moth-illustration-by-Vexels.svg" alt="common moth" style="height:{altura(item.destruccion - cantidadMinima) * 1.5}px"/>
            <img class="LeafA" src="./images/double_leaf.svg" alt="small leaf" style="height:{altura(item.destruccion - cantidadMinima) * 1.5}px"/>
          <div class="column2" style="height: {altura(item.destruccion)}px"></div>
        </div>
      {/each}
    </div>
  
    <div class="region-labels">
      {#each dataLepidopteraRegion as item}
        <div class="region-label">
          <p class="counMoth" style="margin-right: 0px; margin-left: 18px">{item.anio}</p>
        </div> 
      {/each}
    </div>
  </div>
  
  <!-- Índices -->
  <div class="legend-container">
    <div class="legend-item">
      <img src="./images/moth-illustration-by-Vexels.svg" style="height: 150px" alt="polilla grande"/>
      <p>Índice de diversidad (D)</p>
    </div>
    <div class="legend-item">
      <img src="./images/grey-moth-illustration-by-Vexels.svg" style="height: 150px" alt="polilla chica"/>
      <p>Índice de destrucción del hábitat (H)</p>
    </div>
  </div>

  <p>
    De las aproximadamente 174,250 especies de lepidópteros descritas hasta 2007, se estima que las mariposas y los hespéridos comprenden alrededor de 17,950, mientras que el resto son polillas. Los lepidópteros están distribuidos en todas las regiones faunísticas excepto la Antártida, pero en áreas como el Neotrópico y la región Indo-australiana, la riqueza de especies es particularmente alta, con mariposas y polillas adaptadas a ecosistemas muy específicos. 
  </p>

  <h3 class="headline" style="margin-top: 130px">
    El paso de los años: menos diversidad y más deterioro
  </h3>
  <div class="chart-wrapper" style="margin-top: 10px">
    <div 
      class="flourish-embed flourish-chart" 
      data-src="visualisation/22688790">
      <script src="https://public.flourish.studio/resources/embed.js"></script>
      <noscript>
        <img src="https://public.flourish.studio/visualisation/22688790/thumbnail" 
        width="100%" 
        alt="chart visualization" />
      </noscript>
    </div>
  </div>

  <p>
    A lo largo del tiempo, el aumento constante en la destrucción del hábitat (H) se correlaciona directamente con una disminución del índice de diversidad (D). Se podría plantear, entonces, que mientras más se alteran y degradan los ecosistemas, menos especies logran sobrevivir o coexistir, provocando un colapso en la riqueza biológica. La trayectoria ascendente de la destrucción contrasta con el declive constante de la diversidad, evidenciando una relación inversamente proporcional entre ambos fenómenos.
  </p>

  <h3 class="headline" style="margin-top: 130px">
    Cambios porcentuales anuales
  </h3>
  <div class="chart-wrapper" style="margin-top: 10px">
    <div 
      class="flourish-embed flourish-chart" 
      data-src="visualisation/22687681">
      <script src="https://public.flourish.studio/resources/embed.js"></script>
      <noscript>
        <img src="https://public.flourish.studio/visualisation/22687681/thumbnail" 
        width="100%" 
        alt="chart visualization" />
      </noscript>
    </div>
  </div>

  <p>
    Año tras año, la proporción de destrucción del hábitat (en violeta) ha ido suplantando el espacio que anteriormente ocupaba la diversidad de lepidópteros (en amarillo). A medida que aumenta el porcentaje de ecosistemas alterados o eliminados, la biodiversidad de esta orden disminuye de manera correspondiente. Esta tendencia evidencia una relación inversa clara: por cada avance en la destrucción del entorno, se pierde biodiversidad, una pérdida que, en muchos casos, resulta irreversible.
  </p>
 
  <br />
  <footer class="footer">
    <div class="footer-left">
      <p class="text">Desarrollado por <strong>Camila Nicole Valdman</strong></p>
      <p class="text">Visualización de Datos – 2025</p>
    </div>
    <div class="footer-right">
      <a href="https://www.linkedin.com/in/camila-valdman-3241542a2/" target="_blank" class="footer-link">
        <img src="./images/LinkedIn_icon.svg" alt="LinkedIn" />
        LinkedIn
      </a>
      <a href="https://github.com/valdman-camila" target="_blank" class="footer-link">
        <img src="./images/github-icon.svg" alt="GitHub" />
        GitHub
      </a>
    </div>
  </footer>
  
  <br />
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,100..1000;1,9..40,100..1000&display=swap");

  .footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    padding: 40px 60px;
    background-color: #ffc21c3a;
    border-top: 2px solid #ffc21c;
    font-size: 18px;
    gap: 20px;
    margin-top: 100px;
    margin-bottom: 0%;
  }

  .footer-left {
    display: flex;
    flex-direction: column;
    gap: 5px;
  }

  .footer-right {
    display: flex;
    gap: 20px;
  }

  .footer-link {
    display: flex;
    align-items: center;
    gap: 8px;
    text-decoration: none;
    color: #333;
    font-weight: bold;
    transition: color 0.2s ease;
  }

  .footer-link:hover {
    color: #ffc21c;
  }

  .footer-link img {
    width: 24px;
    height: 24px;
  }

  .header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-top: 50px;
    margin-bottom: 60px;
  }

  .headline {
    font-size: 30px;
    line-height: 1.2;
    font-weight: normal;
    text-align: center;
    margin: 20px;
  }

  .headline b {
    display: block;
    font-size: 35px;
    margin-bottom: 5px;
  }

  .chart-wrapper {
    max-width: 1100px;
    margin: auto;
    margin-bottom: 100px;
    margin-top: 130px;
  }

  .graph_container {
    position: relative;
    margin-bottom: 60px; 
    overflow-x: auto;
    overflow-y:hidden;
    width: 100%;
  }

  .container {
    display: flex;
    height: 550px;
    position: relative;
    padding-left: 70px;
    padding-right: 70px;
    width: max-content;
    min-width: 100%;
    gap: 140px; 
  }

  .region-labels {
    display: flex;
    width: max-content;
    min-width: 100%;
    padding-left: 60px;
    padding-right: 60px;
    gap: 140px; 
    margin-top: 20px;
  }

  .labels-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    gap: 5px;
    flex: 1;
  }

  .value-h, .value-d {
    font-size: 24px;
    font-weight: bold;
    white-space: nowrap;
    padding: 2px 5px;
    border-radius: 3px;
  }

  .value-h {
    color: #80510c;
  }

  .value-d {
    color: #454459;
  }

  .region-label {
    text-align: center;
    width: 80px;
    flex-shrink: 0;
  }

  .item_wrapper {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
    gap: 10px;
    width: 80px;
    position: relative;
    height: 100%;
    flex-shrink: 0;
  }

  .column2 {
    width: 20px;
    height: 100%;
    border-radius: 30px;
    background-color: rgb(70, 126, 2);
  }

  .counMoth {
    font-size: 24px;
    font-weight: bold;
    color: #000000;
    text-align: center;
    margin-top: 15px;
  }

  .bigMoth{
    position: absolute;
    z-index: 1;
    width: 200px;
    height: 100%;
    transform: scale(1.8) rotate(40deg);
    margin-right: -100px;
  }

  .smallMoth{
    position: absolute;
    z-index: 1;
    width: 150px;
    height: 100%;
    transform: scale(1.8) rotate(-40deg);
    margin-left: -100px;
  }

  .LeafA{
    position: absolute;
    z-index: 0;
    width: 200px;
    height: 100%;
    transform: scale(1.5) rotate(40deg);
    margin-left: -80px;
  }

  .LeafB{
    position: absolute;
    z-index: 0;
    width: 200px;
    height: 100%;
    transform: scale(1.5) rotate(-40deg);
    margin-right: -80px;
  }

  p {
    font-size: 20px;
    margin-left: 15px;
    margin-right: 15px;
  }

  .legend-container {
    display: flex;
    justify-content: center;
    gap: 40px;
    margin-top: 40px;
    margin-bottom: 100px;
  }

  .legend-item {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .legend-item p {
    margin: 0;
    font-size: 22px;
  }

  .graph_container::-webkit-scrollbar {
    height: 8px;
  }

  .graph_container::-webkit-scrollbar-thumb {
    background: #ffc21c;
    border-radius: 4px;
  }
  
  .graph_container::-webkit-scrollbar-track {
    background: #f1f1f1;
  }

  main {
    margin-left: 30px;
    margin-right: 30px;
    font-family: "DM Sans", sans-serif;
    transform: scale(0.7);
    margin-top: 0;
    margin-bottom: 0;
  }
</style>