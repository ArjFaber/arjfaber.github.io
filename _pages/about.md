---
permalink: /
title: ""
author_profile: true
description: "Specializing in Reinforcement Learning, High-Performance Computing, and Robotics."
redirect_from: 
  - /about/
  - /about.html
---
<div class="slider-container">
    <div class="video-slider">
        <div class="video">
            <iframe class="video-frame" src="https://www.youtube.com/embed/k-XBWFp1FAQ?autoplay=0&mute=0" allowfullscreen></iframe>
        </div>
        <div class="video">
         <iframe class="video-frame" src="https://www.youtube.com/embed/X8vEKe2i508?autoplay=0&mute=0" allowfullscreen></iframe>
        </div>
    </div>
    <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
    <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
</div>

# About Me



<style>
    .slider-container {
        max-width: 100%;
        width: auto;
        overflow: hidden;
        position: relative;
        margin: auto;
        border-radius: 10px;
        box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .video-slider {
        display: flex;
        width: 300%;
        transition: transform 0.5s ease-in-out;
    }

    .video {
        min-width: 100%;
        box-sizing: border-box;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .video-frame {
        width: 560px;
        height: 315px;
        border-radius: 10px;
    }

    .btn {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        background-color: rgba(0, 0, 0, 0.5);
        color: white;
        border: none;
        padding: 10px;
        cursor: pointer;
        font-size: 18px;
        border-radius: 50%;
    }

    .prev { left: 5px; }
    .next { right: 5px; }

    .btn:hover {
        background-color: rgba(0, 0, 0, 0.8);
    }
</style>

<script>
    let index = 0;
  const slider = document.querySelector('.video-slider');
const totalVideos = document.querySelectorAll('.video').length;

let autoSlideInterval;
let isVideoPlaying = false;

function updateSlider() {
    slider.style.transform = `translateX(-${index * 100}%)`;  // Added backticks to create a valid string
}

function moveSlider(direction) {
    if (!isVideoPlaying) {
        index = (index + direction + totalVideos) % totalVideos;
        updateSlider();
    }
}

function autoSlide() {
    if (!isVideoPlaying) {
        index = (index + 1) % totalVideos;
        updateSlider();
    }
}

function startAutoSlide() {
    if (!autoSlideInterval && !isVideoPlaying) {
        autoSlideInterval = setInterval(autoSlide, 5000);
    }
}

function stopAutoSlide() {
    clearInterval(autoSlideInterval);
    autoSlideInterval = null;
}

// Ensure the auto-slide functionality works even without interaction
document.addEventListener('DOMContentLoaded', function () {
    startAutoSlide();
});

// Pause auto-slide when a video starts playing
const videos = document.querySelectorAll('video');
videos.forEach(video => {
    video.addEventListener('play', () => {
        isVideoPlaying = true;
        stopAutoSlide();
    });
    video.addEventListener('pause', () => {
        isVideoPlaying = false;
        startAutoSlide();
    });
    video.addEventListener('ended', () => {
        isVideoPlaying = false;
        startAutoSlide();
    });
});

// Initialize the slider position
updateSlider();

</script>

