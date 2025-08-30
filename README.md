
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ঘুম সাইকেল ক্যালকুলেটর</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
            background: #5b8bd4;
        }
        
        h1 {
            color: #000000;
        }
        
        input,
        button {
            padding: 10px;
            font-size: 16px;
            margin: 10px;
            border-radius: 8px;
            border: 1px solid #ccc;
        }
        
        button {
            background: #15881f;
            color: white;
            cursor: pointer;
        }
        
        button:hover {
            background: #6eb172;
        }
        
        .result {
            margin-top: 20px;
            font-size: 18px;
            color: #000000;
        }
        
        .time-box {
            background: rgb(238, 240, 235);
            display: inline-block;
            padding: 10px 20px;
            margin: 5px;
            border-radius: 10px;
            box-shadow: 0 2px 6px rgba(180, 83, 83, 0.2);
        }
    </style>
</head>

<body>
    <h1>😴 ঘুম সাইকেল ক্যালকুলেটর</h1>
    <p>তুমি কখন উঠবে সেটা সময় দাও (যেমন: 04:00):</p>
    <input type="time" id="wakeTime">
    <button onclick="calculateBedtime()">হিসাব কর</button>

    <div id="results" class="result"></div>

    <script>
        function calculateBedtime() {
            let wakeTime = document.getElementById("wakeTime").value;
            if (!wakeTime) {
                alert("দয়া করে সময় লিখ।");
                return;
            }

            let [hours, minutes] = wakeTime.split(":").map(Number);
            let resultsDiv = document.getElementById("results");
            resultsDiv.innerHTML = "<h3>তোর ঘুমানোর সঠিক সময়:</h3>";

            let sleepCycles = [6, 7.5, 9]; // hours

            sleepCycles.forEach(cycle => {
                let date = new Date();
                date.setHours(hours);
                date.setMinutes(minutes);
                date.setSeconds(0);

                date.setMinutes(date.getMinutes() - cycle * 60);

                let timeStr = date.toLocaleTimeString([], {
                    hour: '2-digit',
                    minute: '2-digit'
                });
                resultsDiv.innerHTML += `<div class='time-box'>${timeStr}</div>`;
            });
        }
    </script>
</body>

</html>
