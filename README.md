# Ex.08 Design of Interactive Image Gallery
## Date:13.11.2024

## AIM:
To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS:

### Step 1:
Clone the github repository and create Django admin interface.

### Step 2:
Change settings.py file to allow request from all hosts.

### Step 3:
Use CSS for positioning and styling.

### Step 4:
Write JavaScript program for implementing interactivity.

### Step 5:
Validate the HTML and CSS code.

### Step 6:
Publish the website in the given URL.

## PROGRM :index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Photo Gallery</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <div class="gallery-container">
        <div class="gallery-item">
            <img src="11.jpeg" alt="Image 1">
        </div>
        <div class="gallery-item">
            <img src="12.jpeg" alt="Image 2">
        </div>
        <div class="gallery-item">
            <img src="13.jpeg" alt="Image 3">
        </div>
        <div class="gallery-item">
            <img src="14.jpeg" alt="Image 3">
        </div>
        <div class="gallery-item">
            <img src="15.jpeg" alt="Image 3">
        </div>
    </div>

    <div class="modal" id="modal">
        <span class="close" id="close">&times;</span>
        <img class="modal-content" id="modal-img">
    </div>

    <script src="script.js"></script>
</body>
</html>
```
style.css
```
body {
    background-color: gray;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    overflow: hidden;
}

.gallery-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 10px;
    padding: 20px;
    max-width: 1200px;
    width: 100%;
}

.gallery-item img {
    width: 100%;
    height: auto;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
}

.gallery-item img:hover {
    transform: scale(1.30);
    cursor: pointer;
}

.modal {
    display: none;
    position: fixed;
    z-index: 1;
    padding-top: 100px;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgba(0, 0, 0, 0.7);
}

.modal-content {
    margin: auto;
    display: block;
    width: 80%;
    max-width: 700px;
    border-radius: 10px;
}

.close {
    position: absolute;
    top: 10px;
    right: 25px;
    color: #fff;
    font-size: 36px;
    font-weight: bold;
    cursor: pointer;
}

.close:hover,
.close:focus {
    color: #ccc;
    text-decoration: none;
    cursor: pointer;
}

```
```
models.py
from django.db import models

class Image(models.Model):
    title = models.CharField(max_length=100)
    image = models.ImageField(upload_to='images/')

    def __str__(self):
        return self.title
views.py
from django.shortcuts import render
from .models import Image

def gallery_view(request):
    images = Image.objects.all()
    return render(request, 'gallery.html', {'images': images})
urls.py
from django.urls import path
from yuviapp.views import gallery_view

urlpatterns = [
    path('', gallery_view, name='gallery'),
]
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/342e686b-fad2-4a3f-a3bc-281b69754a63)


## RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
