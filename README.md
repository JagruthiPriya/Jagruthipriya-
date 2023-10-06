<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <title>Temperature converter</title>
    <style>
      @import url("https://fonts.googleapis.com/css2?family=Raleway:ital,wght@0,300;0,500;0,600;0,700;1,300;1,400;1,500;1,600;1,700&family=Roboto:wght@100;300;400;700&family=Ubuntu:ital,wght@0,300;0,400;0,500;1,300;1,400;1,500;1,700&display=swap");

      * {
        box-sizing: border-box;
        padding: 0;
        margin: 0;
        font-family: "Poppins", sans-serif;
      }

      .container {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        text-align: center;
        background-color: rgb(99, 99, 209);
      }

      #calcTemp {
        padding: 29px 67px;
        min-height: 290px;
        background-color: #22926b;
        box-shadow: rgba(0, 0, 0, 0.12) 0px 1px 3px,
          rgba(0, 0, 0, 0.24) 0px 1px 2px;
      }

      label {
        font-size: 38px;
        font-style: italic;
        line-height: 80px;
      }

      #temp {
        width: 110px;
        height: 34px;
        border-radius: 5px;
        margin: 12px;
        padding: 8px;
        font-size: 20px;
        font-weight: 500;
        border: none;
        outline: none;
      }

      #temp_diff {
        width: 120px;
        height: 34px;
        border-radius: 5px;
        margin: 12px;
        font-size: 18px;
        font-weight: 500;
        border: none;
        outline: none;
      }

      #submit {
        width: 100px;
        border-radius: 5px;
        margin: 30px 0 20px 0;
        font-size: 18px;
        background-color: rgb(31, 222, 14);
        padding: 5px;
        transition: all 0.5s ease;
      }

      #submit:hover {
        background-color: antiquewhite;
        cursor: pointer;
      }

      #result {
        font-size: 27px;
      }
    </style>
  </head>

  <body>
    <div class="container">
      <form id="calcTemp" onsubmit="calculateTemp(); return false">
        <label for="temp">Enter the temperature to converter </label>
        <br />
        <input type="number" name="temp" id="temp" value="0" />
        <select name="temp_diff" id="temp_diff">
          <option value="cel">&#176;Celsius</option>
          <option value="fah">&#176;Fahrenheit</option>
        </select>
        <br />
        <input type="submit" name="temp" id="submit" />
        <br />
        <span id="result"></span>
      </form>
    </div>

    <script>
      const calculateTemp = () => {
        const inputTemp = document.getElementById("temp").value;

        const tempSelected = document.getElementById("temp_diff");
        const valueTemp = temp_diff.options[tempSelected.selectedIndex].value;

        // Celsius to Fahrenheit
        const celToFah = (cel) => {
          let fahrenheit = ((cel * 9) / 5 + 32).toFixed(1);
          return fahrenheit;
        };

        // Fahrenheit to Celsius
        const fahToCel = (fah) => {
          let celsius = (((fah - 32) * 5) / 9).toFixed(1);
          return celsius;
        };

        if (valueTemp == "cel") {
          document.getElementById("result").innerHTML =
            celToFah(inputTemp) + "&#176; Fahrenheit";
        } else {
          document.getElementById("result").innerHTML =
            fahToCel(inputTemp) + "&#176; Celsius";
        }
      };
    </script>
  </body>
</html>
