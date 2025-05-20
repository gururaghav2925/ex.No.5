# Ex05 Image Carousel
## Date:09-05-2025

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
# main.jsx
```jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import App from './App.jsx'

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
  </StrictMode>,
)


```
 # Image.jsx
 ```jsx
// src/ImageCarousel.js
import React from 'react';
import Slider from 'react-slick';
import 'slick-carousel/slick/slick.css'; 
import 'slick-carousel/slick/slick-theme.css';

const ImageCarousel = () => {
  const images = [
    './src/img/car1.jpeg',
    './src/img/car2.jpeg',
    './src/img/car3.jpeg',
  ];

  const settings = {
    dots: true,
    infinite: true,
    speed: 500,
    slidesToShow: 1,
    slidesToScroll: 1,
    autoplay: true,
    autoplaySpeed: 3000,
  };

  return (
    <div style={{ width: '800px', margin: '0 auto' }}>
      <Slider {...settings}>
        {images.map((url, index) => (
          <div key={index}>
            <img src={url} alt={`Slide ${index + 1}`} style={{ width: '100%', height: 'auto' }} />
          </div>
        ))}
      </Slider>
    </div>
  );
};

export default ImageCarousel;

```

# App.jsx
```jsx

// src/App.js
import React from 'react';
import './css/App.css';
import ImageCarousel from './Image';

function App() {
  return (
    <div className="App">
      <h1>React Image Carousel</h1>
      <ImageCarousel />
    </div>
  );
}

export default App;

```

## OUTPUT

![image](https://github.com/user-attachments/assets/def773f8-36db-4113-954c-987da37da1ab)


![Screenshot 2025-05-20 170817](https://github.com/user-attachments/assets/378063a5-acff-4cc5-bdb5-d2abd2612a05)



![image](https://github.com/user-attachments/assets/6000e36f-e017-4eb1-9246-597fd8a386c6)


## RESULT
The program for creating Image Carousel using React is executed successfully.
