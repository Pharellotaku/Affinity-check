index.html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Affinity Check Pro</title>
    <style>
        :root {
            --primary: #ff4d6d;
            --bg: #121212;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg);
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
        }
        .container {
            text-align: center;
            background: #1e1e1e;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            width: 90%;
            max-width: 400px;
            border: 1px solid #333;
        }
        h1 { color: var(--primary); font-size: 24px; }
        input {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border-radius: 10px;
            border: none;
            background: #333;
            color: white;
            text-align: center;
            box-sizing: border-box;
        }
        button {
            background: var(--primary);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            margin-top: 10px;
            transition: 0.3s;
        }
        #result-box {
            margin-top: 20px;
            padding: 15px;
            border-radius: 10px;
            display: none;
            animation: fadeIn 0.5s;
        }
        .vane { color: #ffcc00; font-style: italic; }
        .match { color: #00ffcc; font-size: 1.2em; font-weight: bold; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body>

<div class="container">
    <h1>💖 Affinity Scanner</h1>
    <p>Calcule ton destin amoureux...</p>
    
    <input type="text" id="name1" placeholder="Ton prénom">
    <input type="text" id="name2" placeholder="Le prénom du crush">
    
    <button onclick="checkAffinity()">CALCULER LE MATCH</button>
    
    <div id="result-box">
        <p id="percentage" style="font-size: 2em; margin: 0;"></p>
        <p id="message"></p>
    </div>
</div>

<script>
    function checkAffinity() {
        const n1 = document.getElementById('name1').value.trim().toLowerCase();
        const n2 = document.getElementById('name2').value.trim().toLowerCase();
        const resBox = document.getElementById('result-box');
        const percentText = document.getElementById('percentage');
        const msgText = document.getElementById('message');

        if(n1 === "" || n2 === "") {
            alert("Remplis les noms pour voir !");
            return;
        }

        resBox.style.display = "block";
        
        // LE MATCH SECRET : PHARELL & ARIANA
        if ((n1 === "pharell" && n2 === "ariana") || (n1 === "ariana" && n2 === "pharell")) {
            document.body.style.backgroundColor = "#2d0a1a";
            percentText.innerHTML = "99.9%";
            percentText.style.color = "#ff4d6d";
            msgText.innerHTML = "<span class='match'>Incroyable ! Vous allez super bien ensemble. Ariana & Pharell, c'est écrit dans les étoiles. ✨❤️</span>";
        } 
        // LES VANNES POUR LES POTES
        else {
            document.body.style.backgroundColor = "#121212";
            percentText.innerHTML = Math.floor(Math.random() * 5) + "%";
            percentText.style.color = "#ffcc00";
            
            const vannes = [
                "Ouch... Même l'intelligence artificielle dit non.",
                "Espoir fait vivre, mais là c'est mort.",
                "Même en rêve, ça ne passe pas.",
                "Erreur 404 : Charisme non trouvé.",
                "Franchement ? Change de cible, Jay ou Josué ont plus de chances que toi !",
                "Hissenne, Aaron... même combat : 0 affinité détectée.",
                "Maëva a déjà vu le résultat, elle a dit : 'MDR'."
            ];
            
            msgText.innerHTML = "<span class='vane'>" + vannes[Math.floor(Math.random() * vannes.length)] + "</span>";
        }
    }
</script>

</body>
</html>
