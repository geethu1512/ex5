# Ex.05 Design a Website for Server Side Processing
## Name: GEETHU R
## Register No. :212224040089
## Date: 26-04-2025
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
math.html
~~~
<html>

<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>POWER OF LAMP IN INCANDESCENT BULB</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <style type="text/css">
        body {
            background-color: #f8f9fa;
        }

        .edge {
            display: flex;
            height: 100vh;
            width: 100%;
            justify-content: center;
            align-items: center;
        }

        .box {
            display: block;
            width: 500px;
            min-height: 300px;
            font-size: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 10px;
            box-shadow: 0px 8px 20px rgba(0, 0, 0, 0.3);
        }

        .formelt {
            color: #f1f1f1;
            text-align: center;
            margin-top: 7px;
            margin-bottom: 6px;
        }

        h1 {
            color: #ffffff;
            text-align: center;
            padding-top: 20px;
        }

        input {
            margin: 5px;
            padding: 8px;
            border-radius: 5px;
            border: none;
            font-size: 16px;
        }

        input[type="submit"] {
            background-color: #ff9800;
            color: white;
            font-weight: bold;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: #e68900;
        }
    </style>
</head>

<body>
    <div class="edge">
        <div class="box">
            <h1>POWER OF LAMP IN INCANDESCENT BULB</h1>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    INTENSITY : <input type="text" name="Intensity" value="{{I}}">(in A)<br />
                </div>
                <div class="formelt">
                    RESISTANCE : <input type="text" name="Resistence" value="{{R}}">(in Ω)<br />
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"><br />
                </div>
                <div class="formelt">
                    POWER : <input type="text" name="Power" value="{{Power}}">W<br />
                </div>
            </form>
        </div>
    </div>
</body>

</html>
~~~
views.py
~~~
from django.shortcuts import render

def powerlamp(request):
    context={}
    context['Power'] = ""
    context['I'] = ""
    context['R'] = ""
    if request.method == 'POST':
        print("POST method is used")
        I = request.POST.get('Intensity','')
        R = request.POST.get('Resistence','')
        print('request=',request)
        print('Intensity=',I)
        print('Resistence=',R)
        Power = int(I) * int(I) * int(R)
        context['Power'] = Power
        context['I'] = I
        context['R'] = R
        print('Power=',Power)
    return render(request,'mathapp/math.html',context)
~~~
urls.py
~~~
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('PowerOfLampFilamentInAnIncandescentBulb/',views.powerlamp,name="PowerOfLampFilamentInAnIncandescentBulb"),
    path('',views.powerlamp,name="PowerOfLampFilamentInAnIncandescentBulb"),
]
~~~

## SERVER SIDE PROCESSING:

![new terminal window](https://github.com/user-attachments/assets/317eda32-8fe5-4d94-a893-cf476c11f636)

## HOMEPAGE:

![new output](https://github.com/user-attachments/assets/b63e856d-894b-4040-aa40-0e615ca7a0a8)

## RESULT:
The program for performing server side processing is completed successfully.
