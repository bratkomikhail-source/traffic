<?php
// Омское время
date_default_timezone_set('Asia/Omsk');

$time = date('H:i');

function getBridgeDirection($time)
{
    if ($time >= "00:00" && $time < "12:00") {
        return [
            "text"  => "ДВИЖЕНИЕ С ЛЕВОГО БЕРЕГА",
            "arrow" => "➡️",
            "color" => "#1e7e34" // зелёный
        ];
    } else {
        return [
            "text"  => "ДВИЖЕНИЕ С ПРАВОГО БЕРЕГА",
            "arrow" => "⬅️",
            "color" => "#004085" // синий
        ];
    }
}

$direction = getBridgeDirection($time);
?>
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>Направление движения по мосту</title>

<!-- Обновление раз в минуту -->
<meta http-equiv="refresh" content="60">

<style>
body {
    margin: 0;
    background: #000;
    color: #fff;
    font-family: Arial, sans-serif;
}
.container {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.arrow {
    font-size: 160px;
}
.text {
    font-size: 48px;
    font-weight: bold;
    margin-top: 30px;
    color: <?= $direction['color'] ?>;
    text-align: center;
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
    <div class="arrow"><?= $direction['arrow'] ?></div>
    <div class="text"><?= $direction['text'] ?></div>
    <div class="time">
        Омское время: <?= date('d.m.Y H:i') ?>
    </div>
</div>

</body>
</html>
