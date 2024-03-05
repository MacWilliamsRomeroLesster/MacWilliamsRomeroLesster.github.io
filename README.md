<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inicio</title>
    <style>
        body {
            background-color: #FFEDD9;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .header {
            text-align: center;
            padding: 5px;
            margin-top: 10px;
            background-color: #FFDAB9;
            width: 70%;
            border-radius: 30px;
            font-family: 'Helvetica';
            box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
            transition: 0.3s;
        }
        h1 {
            font-weight: 1000;
            font-size: 3em;
            color: #FFA07A;
        }
        .survey {
            display: none;
            margin: auto;
            width: 70%;
            padding: 10px;
            text-align: center;
        }
        .button-container {
            text-align: center;
            margin-top: 20px;
        }
        button {
            padding: 15px 25px;
            font-size: 24px;
            text-align: center;
            cursor: pointer;
            outline: none;
            color: #fff;
            background-color: #FFA07A;
            border: none;
            border-radius: 15px;
            box-shadow: 0 9px #999;
        }
        button:hover {background-color: #ec8c69}
        button:active {
            background-color: #ec8c69;
            box-shadow: 0 5px #666;
            transform: translateY(4px);
        }
        .text-box {
            background-color: #FFFAF0;
            color: #FFA07A;
            width: 70%;
            padding: 10px;
            margin-top: 20px;
            text-align: center;
            border-radius: 15px;
            overflow: hidden;
            white-space: normal;
            border-right: .15em solid orange;
        }
        #video {
            margin-top: 20px;
        }
    </style>
    <script>
        function showSurvey() {
            document.querySelector('.survey').style.display = 'block';
            document.querySelector('#show-survey').style.display = 'none';
            document.querySelector('#next').style.display = 'inline-block';
            document.querySelector('#video').style.display = 'none';
            document.querySelector('.text-box').style.display = 'none';
        }

        function typeWriter(text, i, fnCallback) {
            if (i < (text.length)) {
                document.querySelector(".text-box").innerHTML = text.substring(0, i+1) +'<span aria-hidden="true"></span>';

                setTimeout(function() {
                    typeWriter(text, i + 1, fnCallback)
                }, 100);
            }
            else if (typeof fnCallback == 'function') {
                setTimeout(fnCallback, 700);
            }
        }

        function StartTextAnimation(i) {
            if (typeof dataText[i] == 'undefined'){
                setTimeout(function() {
                    StartTextAnimation(0);
                }, 20000);
            }
            if (i < dataText[i].length) {
                typeWriter(dataText[i], 0, function(){
                    StartTextAnimation(i + 1);
                });
            }
        }

        function showNextScreen() {
            document.querySelector('.survey').style.display = 'none';
            document.querySelector('#next').style.display = 'none';
            document.querySelector('#video').src = 'dancing-monkey-__.gif'; // Cambia 'URL_del_segundo_video.mp4' por la URL correcta de tu video IdleSentado
            document.querySelector('.text-box').innerText = ''; 
            document.querySelector('#video').style.display = 'block';
            document.querySelector('.text-box').style.display = 'none';
        }


        document.addEventListener('DOMContentLoaded', function(event) {
            document.querySelector('#next').addEventListener('click', showNextScreen);
            dataText = [document.querySelector(".text-box").innerText];
            StartTextAnimation(0);

            // Obtén el elemento del primer video
            var video = document.getElementById('video');

            // Agrega un evento para detectar cuando termina el primer video
            video.addEventListener('ended', function() {
                // Cambia la fuente del primer video por la del segundo video
                video.src = 'dancing-monkey-__.gif'; // Reemplaza 'URL_del_segundo_video.mp4' con la URL de tu segundo video
                video.play(); // Reproduce el segundo video
            });
            
            // Reproduce el primer video en bucle
            video.play();
            video.loop = true;
        })
    </script>

</head>
<body>
    <div class="header">
        <h1>UCFESTIVAL</h1>
    </div>
    <div class="button-container">
        <button id="show-survey" onclick="showSurvey()">Mostrar encuesta</button>
        <button id="next" style="display: none;">Siguiente</button>
    </div>
    <img id="video" width="560" height="315" src="dancing-cat-33-title.gif" alt="videito">
    <div class="text-box">
        <p>Bienvenido a la encuesta del patrón.
        </p>
    </div>
    <div class="survey">
        <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSc7xOutx2jk2BC19zNJWG9vCTmNxkqO9tjVI0_CPQDzPsHteQ/viewform?usp=sf_link" width="640" height="600" frameborder="0" marginheight="0" marginwidth="0">Cargando…</iframe>
    </div>
</body>
</html>


""" usó three.js para crear el modelo 3d """
