<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>Направление движения по мосту</title>

<style>
    body {
        margin: 0;
        background: black;
        color: white;
        font-family: Arial, sans-serif;
    }
    .container {
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
    }
    .arrow {
        font-size: 160px;
    }
    .text {
        font-size: 48px;
        font-weight: bold;
        margin-top: 30px;
    }
    .time {
        margin-top: 40px;
        font-size: 28px;
        color: #ccc;
    }
</style>
</head>
<body>

<div class="container">
    <div id="arrow" class="arrow"></div>
    <div id="text" class="text"></div>
    <div id="time" class="time"></div>
</div>

<script>
function updateDirection() {
    // Получаем текущее время по Омску
    const now = new Date(
        new Date().toLocaleString("en-US", { timeZone: "Asia/Omsk" })
    );

    const hours = now.getHours();
    cons
