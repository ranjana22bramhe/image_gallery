```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Gallery</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Jost:wght@400;700&family=Raleway+Dots&display=swap" rel="stylesheet">
    <style>
       /* Common Styles for all pages */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Jost', sans-serif; /* Consistent font across pages */
        }

        a { /* Style all links to remove underlines */
            text-decoration: none;
        }

       /* index.html styles */
        body.front-page {
            background-image: url('https://img.freepik.com/premium-photo/realistic-navy-blue-glitter-background-36294593ht-6f20b8-background-generative-ai_913266-47502.jpg');
            /* ... other styles ... */
        }


        /* index1.html Styles */
        body.gallery-page {
            font-family: "Jost", sans-serif;
            /* ... (Existing styles) ... */
        }

        /* index2.html - index8.html Styles */
        body.subgallery-page {
            font-family: 'Poppins', sans-serif; /* Or keep Poppins if preferred */
            /* ... other styles ... */
        }

        /* Lightbox Styles (Common) */
        .lightbox {
            /* ... (Existing Lightbox styles) ... */
        }
        /* Add loading indicator to lightbox */
        .lightbox.loading::before {
            content: "";
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 50px;
            height: 50px;
            border: 5px solid #fff;
            border-radius: 50%;
            border-top-color: transparent;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: translate(-50%, -50%) rotate(0deg); }
            100% { transform: translate(-50%, -50%) rotate(360deg); }
        }



    </style>
</head>
<body class="front-page">
   </body>
</html>

```


index1.html (updated):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- ... existing head content ... -->
<body class="gallery-page">
     <!-- ... existing body content ... -->

</body>
</html>
```

index2.html - index8.html:
Add the body class to each of these files:

```html
<body class="subgallery-page">
    <!-- ... rest of the body content ... -->
    <script>
        // ... (Other JavaScript)

        function showLightbox(src, index) {
            lightbox.classList.add('loading'); // Add loading class
            const img = new Image();
            img.onload = function() {
                lightboxImg.src = src;
                lightboxHeading.textContent = imageDetails[index].heading;
                lightboxDescription.textContent = imageDetails[index].description;
                lightbox.style.display = 'flex';
                lightbox.classList.remove('loading'); // Remove loading class
            };
            img.src = src; // Trigger image load

        }
    </script>
</body>
```


Key changes and explanations:

1. **Consistent Font:**  The `font-family` is now set consistently using the  `body`  selector or a more specific selector if needed. This improves visual consistency.
2. **Body Classes:** Added classes  `front-page`,  `gallery-page`, and  `subgallery-page`  to the  `body`  tag in your HTML files. This allows you to apply specific styles to each page type without conflicts.
3. **Link Styling:**  Added a global style for  `a`  elements to remove underlines from all links.
4. **Loading Indicator:** Added a loading indicator to the lightbox.  The spinning animation appears while the larger image loads. This improves the user experience.  The key is to trigger the image load *after* setting the  `src`  so the  `onload`  event works correctly.


With these changes, your image gallery should have a cleaner, more consistent look and feel, and the lightbox will provide better feedback to the user during image loading.