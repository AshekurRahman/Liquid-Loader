# Liquid Loader

A simple and visually appealing liquid loader animation using HTML and CSS.

![Preview](https://raw.githubusercontent.com/AshekurRahman/Liquid-Loader/main/preview.gif)

## Description

This project demonstrates a liquid loader animation, which can be used as a preloader for websites or applications. The loader uses CSS animations and SVG filters to create a dynamic and engaging effect.

## Features

- **Liquid effect:** Utilizes SVG filters to create a gooey, liquid-like animation.
- **Responsive design:** The loader is designed to be responsive and adapt to different screen sizes.
- **Customizable:** Easy to customize colors, sizes, and animation timings through CSS variables.

## Getting Started

### Prerequisites

No special prerequisites are required to use this loader. Simply include the HTML and CSS in your project.

### Usage

1. **Include the HTML**: Copy and paste the HTML structure into your project.
2. **Include the CSS**: Copy and paste the CSS styles into your project's stylesheet.
3. **Customize**: Adjust the CSS variables to fit your design needs.

### Example

Here's a quick example of how to integrate the liquid loader:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* Resetting margins and paddings for all elements, setting box-sizing to border-box */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* Styling for the preloader section */
        .preloader {
            position: fixed; /* Fixed positioning to cover the entire screen */
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: white; /* White background color */
            z-index: 9999; /* Ensuring it's on top of other elements */
            display: flex;
            align-items: center; /* Centering content vertically */
            justify-content: center; /* Centering content horizontally */
        }

        /* Dummy SVG element used to define the filter */
        .liquid {
            width: 0;
            height: 0;
        }

        /* Styling for the loader container */
        .loader {
            position: relative;
            width: 250px;
            height: 250px;
            filter: url(#gooey); /* Applying the gooey filter */
        }

        /* Styling for each loader span element */
        .loader span {
            position: absolute;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            display: inline-block;
            transform: rotate(calc(45deg * var(--i))); /* Rotating each span based on the --i variable */
        }

        /* Styling for the before pseudo-element of each span */
        .loader span::before {
            content: "";
            position: absolute;
            top: 0;
            left: calc(50% - 20px); /* Centering the circle horizontally */
            width: 40px;
            height: 40px;
            background-color: blue; /* Blue color for the circle */
            border-radius: 99px; /* Making the circle round */
            box-shadow: 0 0 30px blue; /* Adding a blue glow */
        }

        /* Additional styling and animation for rotating spans */
        .loader span.rotate {
            animation: rounded 4s ease-in-out infinite; /* Infinite rotation animation */
            animation-delay: calc(-0.2s * var(--j)); /* Staggering the animation delays */
        }

        /* Keyframes for the rotation animation */
        @keyframes rounded {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }
    </style>
</head>
<body>
    <!-- Preloader section -->
    <section class="preloader">
        <!-- SVG used to define the gooey filter -->
        <svg class="liquid"> 
            <filter id="gooey"> 
                <feGaussianBlur in="SourceGraphic" stdDeviation="10" /> <!-- Blurring the source graphic -->
                <feColorMatrix values="
                    1 0 0 0 0
                    0 1 0 0 0
                    0 0 1 0 0
                    0 0 0 20 -10" /> <!-- Adjusting the color matrix for the gooey effect -->
            </filter> 
        </svg>
        <!-- Loader container -->
        <div class="loader">
            <!-- Loader span elements with custom properties -->
            <span style="--i: 1;"></span>
            <span style="--i: 2;"></span>
            <span style="--i: 3;"></span>
            <span style="--i: 4;"></span>
            <span style="--i: 5;"></span>
            <span style="--i: 6;"></span>
            <span style="--i: 7;"></span>
            <span style="--i: 8;"></span>
            <span class="rotate" style="--j: 0;"></span>
            <span class="rotate" style="--j: 1;"></span>
            <span class="rotate" style="--j: 2;"></span>
            <span class="rotate" style="--j: 3;"></span>
            <span class="rotate" style="--j: 4;"></span>
        </div>
    </section>
</body>
</html>
