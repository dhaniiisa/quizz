<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Tebak-Tebakan Seru</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background: linear-gradient(135deg, #667eea, #764ba2);
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
        color: #fff;
    }

    .box {
        background: rgba(0,0,0,0.3);
        padding: 25px;
        border-radius: 15px;
        width: 350px;
        text-align: center;
    }

    input {
        width: 90%;
        padding: 10px;
        border-radius: 8px;
        border: none;
        margin-top: 10px;
        font-size: 16px;
    }

    button {
        margin-top: 15px;
        padding: 10px 20px;
        border: none;
        border-radius: 10px;
        background: #ffcc00;
        font-weight: bold;
        cursor: pointer;
    }

    button:hover {
        background: #ffd633;
    }

    .info {
        margin-top: 15px;
    }
</style>
</head>
<body>

<div class="box">
    <h2>Tebak-Tebakan 🤔</h2>
    <p id="question"></p>

    <input type="text" id="answer" placeholder="Jawablah...">
    <br>
    <button onclick="checkAnswer()">Jawab</button>

    <div class="info">
        <p id="result"></p>
        <p id="score"></p>
    </div>
</div>

<script>
const questions = [
    { q: "Kenapa Superman di bajunya ada tulisan S?", a: "yang xl habis" },
    { q: "Kebo apa yang cape?", a: "kebogor ngesot" },
    { q: "Tahu apa yang besar?", a: "tahu isi asia" },
    { q: "Punya gigi tapi tidak bisa makan?", a: "ga kenyang" },
    { q: "Kenapa air laut rasanya asin?", a: "takdir" },
    { q: "Ada 10 bebek di kali 2 jadi berapa?", a: "20 bebek" },
    { q: "Siapa nama orang paling pikmi sedunia?", a: "rima" },
    { q: "Sapi apa yang tidak makan rumput?", a: "sapi puasa" },
    { q: "Hewan apa yang matanya di kaki, mulutnya di kaki, hidungnya di kaki?", a: "kodok keinjek" },
    { q: "Pemain bola apa yang beratnya 3 kg?", a: "Bambang tabung gas" }
];

let index = 0;
let score = 0;

document.getElementById("question").innerText = questions[index].q;
document.getElementById("score").innerText = "Skor: 0";

function checkAnswer() {
    const userAnswer = document.getElementById("answer").value.toLowerCase();
    const correctAnswer = questions[index].a;

    if (userAnswer === correctAnswer) {
        score++;
        document.getElementById("result").innerText = "✅ Benar!";
    } else {
        document.getElementById("result").innerText = 
        "❌ Salah! Jawaban: " + correctAnswer;
    }

    index++;
    document.getElementById("answer").value = "";
    document.getElementById("score").innerText = "Skor: " + score;

    if (index < questions.length) {
        setTimeout(() => {
            document.getElementById("question").innerText = questions[index].q;
            document.getElementById("result").innerText = "";
        }, 1000);
    } else {
        setTimeout(() => {
            document.querySelector(".box").innerHTML = `
                <h2>🎉 Selesai!</h2>
                <p>Skor kamu: ${score} / ${questions.length}</p>
                <button onclick="location.reload()">Main Lagi</button>
            `;
        }, 1000);
    }
}
</script>

</body>
</html>
