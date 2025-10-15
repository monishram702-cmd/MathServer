# Ex.05 Design a Website for Server Side Processing
## Date:14/10/2025

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
# Ex.05 Design a Website for Server Side Processing
## Date:14/10/2025

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :

```html


home.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>MONISHRAM</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background-color: #121212;
      font-family: 'Segoe UI', sans-serif;
      color: #e0e0e0;
    }

    .hero {
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      background: radial-gradient(circle at center, #1f1f1f 0%, #121212 100%);
    }

    .heading-group {
      text-align: center;
      line-height: 1.1;
      margin-bottom: 10px;
    }

    .heading {
      font-size: 4em;
      letter-spacing: 8px;
      font-weight: bold;
      color: #ffffff;
      text-shadow: 0 0 20px #00ffe0;
      margin: 0;
    }

    .subheading {
      font-size: 2em;
      letter-spacing: 4px;
      font-weight: bold;
      color: #ffffff;
      text-shadow: 0 0 20px #00ffe0;
      margin: 0;
    }

    .tagline {
      font-size: 1.2em;
      color: #bbbbbb;
      font-style: italic;
      margin-bottom: 30px;
    }

    .enter-btn {
      padding: 15px 40px;
      background-color: #00ffe0;
      color: #121212;
      text-decoration: none;
      font-weight: bold;
      border-radius: 30px;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      cursor: pointer;
    }

    .enter-btn:hover {
      transform: scale(1.05);
      box-shadow: 0 0 15px #00ffe0;
    }
  </style>
</head>
<body>
  <div class="hero">
    <div class="heading-group">
      <h1 class="heading">MONISH R</h1>
      <h2 class="subheading">25017815</h2>
    </div>
    <p class="tagline">Unveil the power within the filament</p>
    <a href="calculator.html" class="enter-btn">Enter</a>
  </div>
</body>
</html>

calculator.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Filament Power Calculator</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background-color: #121212;
      font-family: 'Segoe UI', sans-serif;
      color: #e0e0e0;
    }

    .container {
      background-color: #1f1f1f;
      padding: 30px;
      border-radius: 10px;
      max-width: 400px;
      margin: 80px auto;
      box-shadow: 0 0 10px rgba(0,0,0,0.3);
      text-align: center;
    }

    h1 {
      font-size: 2em;
      color: #00ffe0;
      margin-bottom: 20px;
    }

    label {
      display: block;
      margin-top: 15px;
      font-weight: bold;
      text-align: left;
    }

    input {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      box-sizing: border-box;
      background-color: #2c2c2c;
      color: #fff;
      border: none;
      border-radius: 5px;
    }

    button {
      margin-top: 20px;
      padding: 10px 20px;
      background-color: #00ffe0;
      color: #121212;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-weight: bold;
    }

    button:hover {
      box-shadow: 0 0 10px #00ffe0;
    }

    #result {
      margin-top: 20px;
      font-size: 1.2em;
      color: #00ffe0;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Filament Power Calculator</h1>
    <form id="powerForm">
      <label for="intensity">Current Intensity (I) in Amperes:</label>
      <input type="number" id="intensity" name="intensity" step="any" required>

      <label for="resistance">Resistance (R) in Ohms:</label>
      <input type="number" id="resistance" name="resistance" step="any" required>

      <button type="submit">Calculate Power</button>
    </form>

    <div id="result"></div>
  </div>

  <script>
    document.getElementById('powerForm').addEventListener('submit', function(e) {
      e.preventDefault();

      const I = parseFloat(document.getElementById('intensity').value);
      const R = parseFloat(document.getElementById('resistance').value);

      if (isNaN(I) || isNaN(R)) {
        document.getElementById('result').textContent = "Please enter valid numbers.";
        return;
      }

      const P = I * I * R;
      document.getElementById('result').textContent = Power (P) = ${P.toFixed(2)} watts;
    });
  </script>
</body>
</html>

views.py

from django.shortcuts import render

def home(request):
    return render(request, 'powerapp/home.html')

def calculator(request):
    power = None
    if request.method == 'POST':
        intensity = float(request.POST.get('intensity', 0))
        resistance = float(request.POST.get('resistance', 0))
        power = round(intensity ** 2 * resistance, 2)
    return render(request, 'powerapp/calculator.html', {'power': power})

urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
    path('calculator.html/', views.calculator, name='calculator'),
]

```



## SERVER SIDE PROCESSING:

![screenshot 25](https://github.com/user-attachments/assets/6d1e18f9-b3e6-4772-9355-889c82f09f86)


## HOMEPAGE:

<img width="1920" height="1080" alt="Screenshot (27)" src="https://github.com/user-attachments/assets/d22ed9e0-86d2-40bf-8cf8-fb38d2c0ba01" />

<img width="1920" height="1080" alt="Screenshot (28)" src="https://github.com/user-attachments/assets/d68e290d-86b1-472c-a6f4-f362c4b18910" />

## RESULT:
The program for performing server side processing is completed successfully.
