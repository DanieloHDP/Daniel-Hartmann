Meine Lebenslauf



<img src="Bilder/Discord-Bild.png" width= "300" align="right" > 
<img src="Bilder/Discord-Bild.png" height= "150" align="left"> 
<p align="center">
<img src="Bilder/Discord-Bild.png" width= "300" > 
</p>
<button class="btn-primary" type="button">Mail</button>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="manifest" href="/manifest.webmanifest">
</head>
<body>
    <button id="install" style="display: none;">Installieren</button>
    <script>
        const installButton = document.getElementById('install');
        let deferredPrompt;
        window.addEventListener('beforeinstallprompt', evt => {
            event.preventDefault();
            deferredPrompt = evt;
            installButton.style.display = 'block';
        });

        window.addEventListener('appinstalled', () => {
            installButton.style.display = 'none';
        });

        installButton.addEventListener('click', async () => {
            await deferredPrompt.prompt();
            const choiceResult = await deferredPrompt.userChoice;
            console.log(choiceResult.outcome);
        });
        navigator.serviceWorker.register('./sw.js');
    </script>
</body>
</html>


