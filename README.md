<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>Fagner ❤️ Ilka</title>

<style>

body{
margin:0;
font-family:Arial;
background:black;
color:white;
text-align:center;
overflow:hidden;
}

h1{
color:#ff4da6;
}

.tela{
display:none;
padding-top:80px;
}

.ativa{
display:block;
}

button{
background:#ff4da6;
border:none;
padding:15px 30px;
border-radius:30px;
font-size:18px;
color:white;
cursor:pointer;
}

.coracao{
position:absolute;
font-size:40px;
cursor:pointer;
}

.barra{
width:300px;
height:25px;
background:#333;
margin:20px auto;
border-radius:20px;
overflow:hidden;
}

.progresso{
height:100%;
width:0%;
background:#ff4da6;
transition:0.3s;
}

.galeria{
display:flex;
justify-content:center;
flex-wrap:wrap;
gap:20px;
margin-top:30px;
}

.polaroid{
background:white;
padding:10px;
border-radius:10px;
}

.polaroid img{
width:220px;
height:220px;
object-fit:cover;
border-radius:5px;
}

.envelope{
width:220px;
height:140px;
background:#ff4da6;
margin:40px auto;
position:relative;
cursor:pointer;
}

.tampa{
width:220px;
height:70px;
background:#ff80bf;
position:absolute;
top:0;
left:0;
transform-origin:top;
transition:1s;
}

.aberto{
transform:rotateX(180deg);
}

.carta{
display:none;
background:white;
color:black;
width:340px;
margin:20px auto;
padding:25px;
border-radius:10px;
line-height:1.6;
}

.nome{
position:fixed;
top:20px;
width:100%;
font-size:22px;
color:#ff4da6;
}

canvas{
position:fixed;
top:0;
left:0;
z-index:-1;
}

</style>
</head>

<body>

<canvas id="stars"></canvas>

<div class="nome">Fagner ❤️ Ilka</div>

<div id="tela1" class="tela ativa">

<h1>Ilka Maria ❤️</h1>

<p>Eu fiz um joguinho para você.</p>

<button onclick="iniciarJogo()">Começar</button>

</div>

<div id="tela2" class="tela">

<h1>Colete os corações 💘</h1>

<div class="barra">
<div id="progresso" class="progresso"></div>
</div>

</div>

<div id="tela3" class="tela">

<h1>Nossas Memórias 📸</h1>

<div class="galeria">

<div class="polaroid">
<img src="foto1.jpg">
</div>

<div class="polaroid">
<img src="foto2.jpg">
</div>

<div class="polaroid">
<img src="foto3.jpg">
</div>

</div>

<br>

<button onclick="proxima(4)">Continuar</button>

</div>

<div id="tela4" class="tela">

<h1>Uma carta para você 💌</h1>

<div class="envelope" onclick="abrirCarta()">
<div id="tampa" class="tampa"></div>
</div>

<div id="carta" class="carta">

<p><b>Ilka Maria,</b></p>

<p>
Eu errei com você, e isso me deixou muito magoado.  
Eu fiz tudo aquilo para te proteger, mas acabei fazendo o contrário.
</p>

<p>
Eu te amo tanto, Ilka Maria.  
Eu vou ser um namorado melhor.  
Eu mudei bastante desde o começo, estou melhor por você, amor.
</p>

<p>
Eu vi esse texto no TikTok e lembrei de você:
</p>

<p>
“Não vou desistir de você, porque desde que você chegou eu me sinto mais feliz.  
Eu nunca quis tanto algo como eu quero você.
</p>

<p>
Eu quero dividir momentos, sair por aí na madrugada, ver o pôr do sol ao seu lado, dançar na chuva, ver as estrelas, olhar nos seus olhos enquanto você ri pra mim.
</p>

<p>
Te dizer o quanto eu te amo e o quanto você é importante pra mim.
</p>

<p>
Você despertou as coisas mais bonitas que existiam em mim, que nem eu sabia que tinha.
</p>

<p>
Você me fez saber o que realmente é o amor, a simplicidade e o respeito.
</p>

<p>
Você é a única pessoa que sabe decifrar o meu olhar, e só você consegue fazer isso.
</p>

<p>
Só você consegue me deixar sem palavras, sem forças.
</p>

<p>
Só você consegue me deixar horas acordado com uma vontade incontrolável de entrelaçar os meus dedos aos teus e te encher de beijos.
</p>

<p>
Estar com você é tudo que eu quero.
</p>

<p>
É você quem eu quero que esteja ao meu lado, mais ninguém.
</p>

<p>
É você quem eu quero pra vida toda.
</p>

<p>
É só você. 🤍
</p>

<p><b>Com amor, Fagner.</b></p>

</div>

</div>

<audio id="musica">
<source src="olha.mp3" type="audio/mpeg">
</audio>

<script>

function proxima(n){
document.querySelectorAll(".tela").forEach(t=>t.classList.remove("ativa"))
document.getElementById("tela"+n).classList.add("ativa")
}

let pontos=0

function iniciarJogo(){

proxima(2)

for(let i=0;i<6;i++){

let c=document.createElement("div")

c.className="coracao"
c.innerHTML="❤️"

c.style.left=Math.random()*90+"vw"
c.style.top=Math.random()*80+"vh"

c.onclick=()=>{

c.remove()

pontos++

document.getElementById("progresso").style.width=(pontos*16.6)+"%"

if(pontos==6){

setTimeout(()=>{
proxima(3)
},500)

}

}

document.body.appendChild(c)

}

}

function abrirCarta(){

document.getElementById("tampa").classList.add("aberto")

setTimeout(()=>{

document.getElementById("carta").style.display="block"

document.getElementById("musica").play()

},800)

}

let canvas=document.getElementById("stars")
let ctx=canvas.getContext("2d")

canvas.width=window.innerWidth
canvas.height=window.innerHeight

let estrelas=[]

for(let i=0;i<150;i++){

estrelas.push({
x:Math.random()*canvas.width,
y:Math.random()*canvas.height,
r:Math.random()*2
})

}

function animar(){

ctx.clearRect(0,0,canvas.width,canvas.height)

ctx.fillStyle="white"

estrelas.forEach(e=>{

ctx.beginPath()
ctx.arc(e.x,e.y,e.r,0,Math.PI*2)
ctx.fill()

})

requestAnimationFrame(animar)

}

animar()

</script>

</body>
</html>
