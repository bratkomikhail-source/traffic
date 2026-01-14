<?php
date_default_timezone_set('Asia/Omsk');
$currentMinutes = (int)date('H') * 60 + (int)date('i');

function getBridgeStatus($m) {
    $schedule = [
        [300, 509,  "С ЛЕВОГО БЕРЕГА",  "➡️", "#1e7e34", "05:00 – 08:29"],
        [510, 569,  "С ПРАВОГО БЕРЕГА", "⬅️", "#004085", "08:30 – 09:29"],
        [570, 659,  "С ЛЕВОГО БЕРЕГА",  "➡️", "#1e7e34", "09:30 – 10:59"],
        [660, 734,  "С ПРАВОГО БЕРЕГА", "⬅️", "#004085", "11:00 – 12:14"],
        [735, 824,  "С ЛЕВОГО БЕРЕГА",  "➡️", "#1e7e34", "12:15 – 13:44"],
        [825, 899,  "С ПРАВОГО БЕРЕГА", "⬅️", "#004085", "13:45 – 14:59"],
        [900, 989,  "С ЛЕВОГО БЕРЕГА",  "➡️", "#1e7e34", "15:00 – 16:29"],
        [990, 1184, "С ПРАВОГО БЕРЕГА", "⬅️", "#004085", "16:30 – 19:44"],
        [1185,1229, "С ЛЕВОГО БЕРЕГА",  "➡️", "#1e7e34", "19:45 – 20:29"],
        [1230,1274, "С ПРАВОГО БЕРЕГА", "⬅️", "#004085", "20:30 – 21:14"],
        [1275,1379, "С ЛЕВОГО БЕРЕГА",  "➡️", "#1e7e34", "21:15 – 22:59"],
    ];

    foreach ($schedule as $s) {
        if ($m >= $s[0] && $m <= $s[1]) {
            return ["text" => "ДВИЖЕНИЕ " . $s[2], "arrow" => $s[3], "color" => $s[4], "interval" => $s[5]];
        }
    }

    return ["text" => "ДВИЖЕНИЕ С ПРАВОГО БЕРЕГА", "arrow" => "⬅️", "color" => "#004085", "interval" => "23:00 – 04:59"];
}

$dir = getBridgeStatus($currentMinutes);
?>
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>Направление движения по мосту</title>
<meta http-equiv="refresh" content="60">
<style>
body { margin:0; font-family:Arial,sans-serif; background:#000; color:#fff; display:flex; justify-content:space-between; align-items:center; height:100vh; padding:0 80px; }
.main { text-align:center; }
.arrow { font-size:160px; }
.text { font-size:48px; font-weight:bold; margin-top:30px; color:<?php echo $dir['color']; ?>; }
.info { text-align:right; color:#ccc; font-size:36px; }
.time { font-size:28px; margin-top:20px; }
</style>
</head>
<body>
<div class="main">
    <div class="arrow"><?php echo $dir['arrow']; ?></div>
    <div class="text"><?php echo $dir['text']; ?></div>
</div>
<div class="info">
    <div>Интервал:</div>
    <div><?php echo $dir['interval']; ?></div>
    <div class="time">Омское время:<br><?php echo date('H:i'); ?></div>
</div>
</body>
</html>
