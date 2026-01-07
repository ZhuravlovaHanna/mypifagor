<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Numerology Table</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        .input-header {
            background-color: #e74c3c;
            margin-bottom: 20px;
        }

        .input-header input {
            background-color: #ecf0f1;
            /*background-color: black;*/
            color: #000000;
            width: 100%;
            border: none;
            padding: 20px;
            text-align: center;
            font-size: 2em;
            outline: none;
            caret-color: black; /* To ensure the caret is visible */
        }

        .input-header input::placeholder {
            color: #757373;
        }

        body {
            font-family: Arial, sans-serif;
            /*background-color: #f4f4f4;*/
            background-color: transparent;
            padding: 20px;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
            /*background-color: #fff;*/
            background-color: transparent;
            padding: 20px 30px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0);
        }

        .calculate-btn {
            background-color: #e82828;
            color: white;
            padding: 15px 30px;
            text-align: center;
            display: block;
            margin: 20px auto;
            cursor: pointer;
            text-transform: uppercase;
            border: none;
            outline: none;
        }

        .table {
            display: grid;
            grid-template-columns: repeat(4, 1fr); /* Now has 4 columns */
            gap: 10px;
            margin-top: 20px;
        }

        .cell {
            background-color: #ecf0f1;
            padding: 20px;
            text-align: center;
        }

        .cell span {
            font-size: 1.5em;
            display: block;
            margin: 20px 0;
        }

        .cell label {
            display: block;
            text-transform: uppercase;
            font-size: 0.9em;
            color: #34495e;
        }

        .cell.wide {
            grid-column: span 2;
        }

        .cell.large {
            grid-column: span 3;
        }

        @media (max-width: 500px) {
            .input-header input::placeholder {
                color: #55555569;
            }

            body {
                padding: 0px;
            }

            .container {
                padding: 2px;
            }

            .cell span {
                font-size: 1em;
            }

            .cell label {
                font-size: 0.7em;
            }

            .cell {
                padding: 10px;
            }

            .cell span {
                margin: 10px 0;
            }

            .table {
                gap: 1px;
            }
        }

        @media (max-width: 320px) {
            .input-header input {
                padding: 10px 20px;
            }

            .calculate-btn {
                margin: 10px auto;
            }

            .input-header {
                margin-bottom: 10px;
            }

            .table {
                margin-top: 10px;
            }

            .padding_top_tm {
                padding-top: 11px;
            }

            .calculate-btn {
                padding: 12px 30px;
            }

            .cell label {
                font-size: 0.4em;
            }

        }
    </style>
</head>
<body>

<div class="container">
    <div class="input-header">
        <input inputmode="numeric" type="text" id="dateInput" placeholder="08.03.1998" oninput="applyDateMask(this)">
    </div>
    <button class="calculate-btn" onclick="changeSpan()">Розрахувати</button>

    <div class="table">
        <div class="cell wide">
            <div class="cell-content">
                <label>Додаткові числа</label>
                <span id="extra_numbers">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Число долі</label>
                <span id="destination_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Темперамент</label>
                <span id="temperament_number" class="padding_top_tm">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Характер</label>
                <span id="character_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Здоровʼя</label>
                <span id="health_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Удача</label>
                <span id="luck_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Ціль</label>
                <span id="goal_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Енергія</label>
                <span id="energy_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Логіка</label>
                <span id="logic_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>обовʼязок</label>
                <span id="duty_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Сімʼя</label>
                <span id="family_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Інтерес</label>
                <span id="interest_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Труд</label>
                <span id="labor_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Памʼять</label>
                <span id="memory_number">-</span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Звички</label>
                <span id="habit_number">-</span>
            </div>
        </div>
        <div class="cell" style="background-color: transparent;">
            <div class="cell-content">
                <label></label>
                <span></span>
            </div>
        </div>
        <div class="cell">
            <div class="cell-content">
                <label>Побут</label>
                <span id="beat_number">-</span>
            </div>
        </div>
    </div>
</div>

<script>
    function applyDateMask(input) {
        const value = input.value;
        let output = value.replace(/[^0-9]/g, '').substring(0, 8);
        if (output.length > 4) {
            output = output.substring(0, 2) + '.' + output.substring(2, 4) + '.' + output.substring(4, 8);
        } else if (output.length > 2) {
            output = output.substring(0, 2) + '.' + output.substring(2);
        }
        input.value = output;
    }

    function changeSpan() {
        const inputValue = document.getElementById('dateInput').value;

        if (/^\d{2}\.\d{2}\.\d{4}$/.test(inputValue)) {
            const parts = inputValue.split('.');
            const day = parseInt(parts[0], 10);
            const month = parseInt(parts[1], 10);
            const year = parseInt(parts[2], 10);

            if (day >= 1 && day <= 31 && month >= 1 && month <= 12) {
                сalculateMatrix(inputValue)
            } else {
                alert("Невірний формат дати");
            }
        } else {
            alert("Введіть дату в форматі: dd.mm.yyyy");
        }
    }

    function сalculateMatrix(birthday) {
        const extra_numbers = document.getElementById('extra_numbers');
        const destination_number = document.getElementById('destination_number');
        const temperament_number = document.getElementById('temperament_number');
        const character_number = document.getElementById('character_number');
        const health_number = document.getElementById('health_number');
        const luck_number = document.getElementById('luck_number');
        const goal_number = document.getElementById('goal_number');
        const energy_number = document.getElementById('energy_number');
        const logic_number = document.getElementById('logic_number');
        const duty_number = document.getElementById('duty_number');
        const family_number = document.getElementById('family_number');
        const interest_number = document.getElementById('interest_number');
        const labor_number = document.getElementById('labor_number');
        const memory_number = document.getElementById('memory_number');
        const habit_number = document.getElementById('habit_number');
        const beat_number = document.getElementById('beat_number');

        const firstValuableNumber = getFirstValuableNumber(birthday)
        const secondValuableNumber = getSecondValuableNumber(firstValuableNumber)
        const thirdValuableNumber = getThirdValuableNumber(firstValuableNumber, birthday)
        const fourthValuableNumber = getFourthValuableNumber(thirdValuableNumber)
        const occurrences = getOccurrences([firstValuableNumber, secondValuableNumber, thirdValuableNumber, fourthValuableNumber], birthday)

        extra_numbers.textContent = `${firstValuableNumber}, ${secondValuableNumber}, ${thirdValuableNumber}, ${fourthValuableNumber}`
        destination_number.textContent = getDestiny(firstValuableNumber, secondValuableNumber)
        temperament_number.textContent = getRest(occurrences['3'], occurrences['5'], occurrences['7'])
        character_number.textContent = occurrences['1'] ? prepareResponse('1', occurrences['1']) : `-`
        health_number.textContent = occurrences['4'] ? prepareResponse('4', occurrences['4']) : '-'
        luck_number.textContent = occurrences['7'] ? prepareResponse('7', occurrences['7']) : '-'
        goal_number.textContent = getRest(occurrences['1'], occurrences['4'], occurrences['7'])
        energy_number.textContent = occurrences['2'] ? prepareResponse('2', occurrences['2']) : '-'
        logic_number.textContent = occurrences['5'] ? prepareResponse('5', occurrences['5']) : '-'
        duty_number.textContent = occurrences['8'] ? prepareResponse('8', occurrences['8']) : '-'
        family_number.textContent = getRest(occurrences['2'], occurrences['5'], occurrences['8'])
        interest_number.textContent = occurrences['3'] ? prepareResponse('3', occurrences['3']) : '-'
        labor_number.textContent = occurrences['6'] ? prepareResponse('6', occurrences['6']) : '-'
        memory_number.textContent = occurrences['9'] ? prepareResponse('9', occurrences['9']) : '-'
        habit_number.textContent = getRest(occurrences['3'], occurrences['6'], occurrences['9'])
        beat_number.textContent = getRest(occurrences['4'], occurrences['5'], occurrences['6'])
    }

    function getRest(num1, num2, num3) {
        let response = 0

        if (num1 > 0) {
            response += num1
        }

        if (num2 > 0) {
            response += num2
        }

        if (num3 > 0) {
            response += num3
        }

        return response > 0 ? response.toString() : `-`
    }

    function prepareResponse(value, occurrence) {
        let response = ''
        for (let i = 0; i < occurrence; i++) {
            response += value
        }

        return response
    }

        function getDestiny(firstValuableNumber, secondValuableNumber) {
        if (secondValuableNumber < 10 || secondValuableNumber === 11) {
            return secondValuableNumber
        }

        const destiny = getSecondValuableNumber(firstValuableNumber)

        if (destiny === 10) {
            return 1
        }
        
        if (destiny > 10) {
            return getSecondValuableNumber(destiny)
        }

        return destiny
    }

    function getFirstValuableNumber(birthday) {
        const sum = birthday.split('.').reduce((acc, cur) => {
            if (Number(cur)) {
                const numbers = cur.split('')

                numbers.forEach((number) => {
                    acc += Number(number)
                })
                return acc
            }
        }, 0)

        if (!sum) {
            throw new Error('Birthday is not valid')
        }

        return sum
    }

    function getSecondValuableNumber(firstValuableNumber) {
        const secondNumber = firstValuableNumber
            .toString()
            .split('')
            .reduce((acc, cur) => {
                return acc + Number(cur)
            }, 0)

        if (!secondNumber) {
            throw new Error('Birthday is not valid')
        }

        return secondNumber
    }

    function getThirdValuableNumber(firstValuableNumber, birthday) {
        const birthdayNumber = birthday.split('')
        const multiplyTo = Number(birthdayNumber[0]) === 0 ? Number(birthdayNumber[1]) : Number(birthdayNumber[0])

        return firstValuableNumber - 2 * multiplyTo
    }

    function getFourthValuableNumber(thirdValuableNumber) {
        const fourthNumber = thirdValuableNumber
            .toString()
            .split('')
            .reduce((acc, cur) => {
                return acc + Number(cur)
            }, 0)

        return Number(fourthNumber)
    }

    function getOccurrences(valuableNumbers, birthday) {
        const allNumbers = birthday.split('.').map((number) => number)

        valuableNumbers.forEach((valuableNumber) => {
            const numbers = valuableNumber
                .toString()
                .split('.')
                .map((number) => number)
            numbers.forEach((number) => {
                allNumbers.push(number)
            })
        })

        const row = allNumbers.join('')
        return row.split('').reduce((acc, curr) => {
            return acc[curr] ? ++acc[curr] : (acc[curr] = 1), acc
        }, {})
    }
</script>
</body>
</html>
