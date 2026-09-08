# Ex05 Image Carousel
## Date:

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
### APP.jsx
```
import { useState, useEffect } from "react";
import "./App.css";

function App() {
  const images = [
    "https://image.api.playstation.com/vulcan/ap/rnd/202312/2115/3ac50f394d24bd8d5af5650eef32fcc1654166d30e3a3216.jpg",
    "https://m.media-amazon.com/images/S/pv-target-images/a0cb3885c44b8305ac89ba7ce98e8cd978bf3ebba6a151a00dbf2d528e98bf3b.jpg",
    "https://images5.alphacoders.com/746/746050.jpg",
    "https://cmsapi-frontend.naruto-official.com/site/api/naruto/Image/get?path=/naruto/jp/news/2023/07/19/PxlL2EIbfVfxfsXI/%E5%90%8D%E7%A7%B0%E6%9C%AA%E8%A8%AD%E5%AE%9A%201.jpg?_=103416c600291dfec2db98bb8f73254f"
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  function nextImage() {
    setCurrentIndex((currentIndex + 1) % images.length);
  }

  function previousImage() {
    setCurrentIndex(
      (currentIndex - 1 + images.length) % images.length
    );
  }

  useEffect(() => {
    const timer = setInterval(nextImage, 3000);

    return () => clearInterval(timer);
  }, [currentIndex]);

  return (
    <div className="carousel">
      <h1>Image Carousel</h1>

      <img
        src={images[currentIndex]}
        alt="carousel"
      />

      <br />

      <button onClick={previousImage}>Previous</button>
      <button onClick={nextImage}>Next</button>

      <p>Image {currentIndex + 1}</p>
    </div>
  );
}

export default App;
```
### APP.css
```
.carousel {
  width: 700px;
  margin: 50px auto;
  text-align: center;
  padding: 20px;
  background: white;
  border-radius: 10px;
}

.carousel h1 {
  margin-bottom: 20px;
}

.carousel img {
  width: 600px;
  height: 400px;
  object-fit: cover;
  border-radius: 8px;
}

button {
  margin: 20px 10px;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  background: #333;
  color: white;
  cursor: pointer;
}

button:hover {
  background: #555;
}
```
### INDEX.jsx
```
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #222;
}

#root {
  width: 100%;
  min-height: 100vh;
}
```
## OUTPUT
![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)
![alt text](image-3.png)
## RESULT
The program for creating Image Carousel using React is executed successfully.
