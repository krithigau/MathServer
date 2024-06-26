# Ex.05 Design a Website for Server Side Processing
## Date:06.04.2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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

```
math.html

<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Surface Area of Right Cylinder</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <style>
        body {
            background-color: rgb(11, 11, 11);
        }
        .edge {
            width: 100%;
            padding-top: 250px;
            text-align: center;
        }
        .box {
            display: inline-block;
            border: thick dashed rgb(247, 251, 251);
            width: 1000px;
            min-height: 500px;
            font-size: 30px;
            background-color: rgb(9, 9, 9);
            box-sizing: border-box;
        }
        .formelt {
            color: white;
            text-align: center;
            margin-top: 8px;
            margin-bottom: 7px;
        }
        h1 {
            color: white;
            text-align: center;
            padding-top: 20px;
        }
        h3 {
            color: white;
            text-align: center;
            padding-top: 10px;
        }
    </style>
</head>
<body>
    <center>    
    <div class="edge">
        <div class="box">
           
            <h1>Surface Area of Right Cylinder</h1>
            <h3>KRITHIGA U (212223240076)</h3>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    Enter Radius value: <input type="text" name="radius" value="{{r}}"> m<br/>
                </div>
                <div class="formelt">
                    Enter Height value: <input type="text" name="height" value="{{h}}"> m<br/>
                </div>
                <br>
                <div class="formelt">
                    <input type="submit" value="Calculate"><br/>
                </div>
                <div class="formelt">
                    Area of the Right Cylinder <input type="text" name="area" value="{{area}}"> m<sup>2</sup><br/>
                </div>
            </form>
        </div>
    </div>
</center>
</body>
</html>

views.py

from django.shortcuts import render
def surfacearea(request):
    context = {}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        print('request.POST:', request.POST)
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        area = 2 * 3.14 * int(r) * int(h) + 2*3.14*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('SurfaceArea =', area)
    
    return render(request, 'myapp/math.html',context)

    urls.py

    from django.contrib import admin
    from django.urls import path
    from myapp import views
    urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.surfacearea,name="surfacearea"),
    path('',views.surfacearea,name="surfacearea")
    ]
```

## SERVER SIDE PROCESSING:

![alt text](<myproj/Screenshot (95).png>)

## HOMEPAGE:

![alt text](<myproj/Screenshot (94).png>)

## RESULT:
The program for performing server side processing is completed successfully.
