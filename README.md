# Ex05 Image Carousel
## Date: 01.06.2026
## NAME: SHIV SUJAN S R
## REG NO: 212223040194
## DEPT: B.E.CSE

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
## APP.JS
```
import React, { useState } from 'react';
import './App.css';

const images = [
  'lion.jpg',
  'cat.jpg',
  '3.jpg',
  '4.avif',
  '5.webp'
];

function App() {
  const [currentIndex, setCurrentIndex] = useState(2);

  const handlePrev = () => {
    setCurrentIndex(
      (prevIndex) => (prevIndex - 1 + images.length) % images.length
    );
  };

  const handleNext = () => {
    setCurrentIndex(
      (prevIndex) => (prevIndex + 1) % images.length
    );
  };

  const getClass = (index) => {
    const diff = index - currentIndex;

    if (diff === 0) return 'active';
    if (diff === -1 || diff === images.length - 1) return 'prev';
    if (diff === 1 || diff === -(images.length - 1)) return 'next';

    return 'hidden';
  };

  return (
    <div className="carousel-container">
      <div className="carousel">
        {images.map((img, index) => (
          <img
            key={index}
            src={img}
            className={`carousel-img ${getClass(index)}`}
            alt="space"
          />
        ))}
      </div>

      <div className="buttons">
        <button onClick={handlePrev}>Previous</button>
        <button onClick={handleNext}>Next</button>
      </div>

      <footer>
        Done By: SHIV SUJAN S R 212223040194
      </footer>
    </div>
  );
}

export default App;
```

## APP.CSS
```
body {
  margin: 0;
  font-family: sans-serif;
  background: linear-gradient(to right, #a1c4fd, #c2e9fb);
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.carousel-container {
  text-align: center;
}

.carousel {
  position: relative;
  width: 800px;
  height: 400px;
  margin: auto;
  perspective: 1000px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.carousel-img {
  position: absolute;
  width: 300px;
  height: 200px;
  object-fit: cover;
  border-radius: 15px;
  box-shadow: 0 15px 25px rgba(0,0,0,0.3);
  opacity: 0;
  transition: all 0.5s ease;
  transform: scale(0.7);
  z-index: 0;
}

.carousel-img.active {
  opacity: 1;
  transform: scale(1);
  z-index: 3;
}

.carousel-img.prev {
  transform: translateX(-220px) scale(0.8);
  opacity: 0.7;
  z-index: 2;
}

.carousel-img.next {
  transform: translateX(220px) scale(0.8);
  opacity: 0.7;
  z-index: 2;
}

.buttons {
  margin-top: 20px;
}

button {
  background-color: #f50057;
  border: none;
  color: white;
  padding: 12px 24px;
  font-size: 16px;
  margin: 0 10px;
  border-radius: 10px;
  cursor: pointer;
  box-shadow: 0 5px 10px rgba(0,0,0,0.2);
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #c51162;
}
```
## OUTPUT

<img width="1919" height="1076" alt="Screenshot 2026-06-01 133504" src="https://github.com/user-attachments/assets/ebb7e431-2560-4bd4-a72e-33d71fde0192" />
<img width="1918" height="1076" alt="Screenshot 2026-06-01 133524" src="https://github.com/user-attachments/assets/4c340f34-0e9b-4f8f-af35-38eebe00726a" />

## RESULT
The program for creating Image Carousel using React is executed successfully.
