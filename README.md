<!DOCTYPE html>
<html>
<head>
  <title>Pineapple-XDcreator</title>
  <!-- Agregamos el ícono del sitio web en la pestaña del navegador -->
  <link rel="icon" type="image/png" id="favicon">
  <style>
    .elemento {
      border: 1px solid #ccc;
      padding: 10px;
      margin: 10px;
    }
  </style>
</head>
<body>
  <!-- Inputs para insertar el nombre del sitio, el contenido y el icono -->
  <label for="sitio-nombre">Nombre del sitio:</label>
  <input type="text" id="sitio-nombre" placeholder="Ingrese el nombre del sitio">

  <label for="imagen">Imagen:</label>
  <input type="file" id="imagen">

  <label for="icono">Icono del sitio:</label>
  <input type="file" id="icono">

  <label for="video">Video:</label>
  <input type="file" id="video">

  <label for="texto">Texto:</label>
  <textarea id="texto" rows="4" cols="50"></textarea>

  <!-- Botones para agregar elementos y guardar el sitio -->
  <button onclick="agregarImagen()">Agregar Imagen</button>
  <button onclick="agregarIcono()">Agregar Icono</button>
  <button onclick="agregarVideo()">Agregar Video</button>
  <button onclick="agregarTexto()">Agregar Texto</button>
  <button onclick="guardarSitio()">Finalizar</button>

  <!-- Contenedor para mostrar los elementos agregados -->
  <div id="contenedor"></div>

<div id="creado-con">
    Creado con Pineapple-XD creator - <a href="path_a_tu_Pineapple-XD_creator" download>https://xdgamesofficial.itch.io/pineapple-xdcreator-p</a>
  </div>

  <!-- JavaScript para agregar elementos y guardar el sitio -->
  <script>
    function agregarImagen() {
      const imagenInput = document.getElementById('imagen');
      const contenedor = document.getElementById('contenedor');
      const imagen = document.createElement('img');
      imagen.className = 'elemento';
      const file = imagenInput.files[0];
      const reader = new FileReader();

      reader.onloadend = function() {
        imagen.src = reader.result;
        imagen.addEventListener('click', function() {
          contenedor.removeChild(imagen);
        });
      };

      if (file) {
        reader.readAsDataURL(file);
        contenedor.appendChild(imagen);
      }
    }

    function agregarIcono() {
      const iconoInput = document.getElementById('icono');
      const favicon = document.getElementById('favicon');
      const file = iconoInput.files[0];
      const reader = new FileReader();

      reader.onloadend = function() {
        favicon.href = reader.result;
      };

      if (file) {
        reader.readAsDataURL(file);
      }
    }

    function agregarVideo() {
      const videoInput = document.getElementById('video');
      const contenedor = document.getElementById('contenedor');
      const video = document.createElement('video');
      video.className = 'elemento';
      const file = videoInput.files[0];
      const reader = new FileReader();

      reader.onloadend = function() {
        video.src = reader.result;
        video.controls = true;
        video.addEventListener('click', function() {
          contenedor.removeChild(video);
        });
      };

      if (file) {
        reader.readAsDataURL(file);
        contenedor.appendChild(video);
      }
    }

    function agregarTexto() {
      const textoInput = document.getElementById('texto');
      const contenedor = document.getElementById('contenedor');
      const texto = document.createElement('p');
      texto.className = 'elemento';
      texto.innerText = textoInput.value;
      texto.addEventListener('click', function() {
        contenedor.removeChild(texto);
      });
      contenedor.appendChild(texto);
    }

    function guardarSitio() {
      const sitioNombre = document.getElementById('sitio-nombre').value;
      const contenedor = document.getElementById('contenedor').innerHTML;
      const contenidoHTML = `
        <!DOCTYPE html>
        <html>
        <head>
          <title>${sitioNombre}</title>
          <!-- Agregamos el ícono del sitio web en la pestaña del navegador -->
          <link rel="icon" type="image/png" href="${document.getElementById('favicon').href}">
        </head>
<div id="creado-con">
    Creado con Pineapple-XD creator - <a href="path_a_tu_Pineapple-XD_creator" download>https://xdgamesofficial.itch.io/pineapple-xdcreator-p</a>
  </div>
        <body>
          ${contenedor}
        </body>
        </html>
      `;
      const blob = new Blob([contenidoHTML], { type: 'text/html' });
      const a = document.createElement('a');
      a.href = URL.createObjectURL(blob);
      a.download = sitioNombre + 'Pineapple.html';
      a.click();
    }
  </script>
</body>
</html>
