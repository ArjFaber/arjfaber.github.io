---
permalink: /
title: ""
author_profile: true
description: "Specializing in Reinforcement Learning, High-Performance Computing, and Robotics."
redirect_from: 
  - /about/
  - /about.html
---

<!-- Video Slider -->
<div class="slider-container">
  <div class="video-slider">
    <div class="video active">
      <iframe class="video-frame" src="https://www.youtube.com/embed/k-XBWFp1FAQ?autoplay=0&mute=0" allowfullscreen></iframe>
    </div>
    <div class="video">
      <iframe class="video-frame" src="https://www.youtube.com/embed/X8vEKe2i508?autoplay=0&mute=0" allowfullscreen></iframe>
    </div>
  </div>
  <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
  <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
</div>

<!-- Intro Text -->
<p style="text-align:center; margin-top: 20px;">
  Hi, welcome to my website! It contains most of my academic related work to date.<br>
  See my CV below for a concise summary!
</p>

<!-- CV Toggle Button -->
<div class="cv-toggle-container">
  <button class="cv-toggle-btn" onclick="toggleCV()">View CV</button>
</div>

<!-- Hidden PDF Viewer -->
<div class="cv-container" id="cvContainer" style="display: none;">
  <h2>My CV</h2>
  <iframe src="https://arjfaber.github.io/files/Arjan_Faber_CV_Recent.pdf" width="100%" height="600px">
    This browser does not support PDFs. Please download the PDF to view it:
    <a href="https://arjfaber.github.io/files/Arjan_Faber_CV_Recent.pdf">Download PDF</a>.
  </iframe>
</div>

<style>
  .slider-container {
    max-width: 90%;
    width: auto;
    overflow: hidden;
    position: relative;
    margin: 40px auto 20px auto;
    border-radius: 10px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .video-slider {
    display: flex;
    transition: transform 0.5s ease-in-out;
  }

  .video {
    flex: 0 0 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    transform: scale(0.9);
    opacity: 0.6;
    transition: transform 0.4s ease, opacity 0.4s ease;
    padding: 10px;
    box-sizing: border-box;
  }

  .video.active {
    transform: scale(1.1);
    opacity: 1;
    z-index: 2;
  }

  .video-frame {
    width: 90%;
    max-width: 720px;
    height: 405px;
    border-radius: 10px;
    transition: all 0.3s ease-in-out;
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
    z-index: 3;
  }

  .prev {
    left: 5px;
  }

  .next {
    right: 5px;
  }

  .btn:hover {
    background-color: rgba(0, 0, 0, 0.8);
  }

  .cv-toggle-container {
    text-align: center;
    margin-top: 30px;
  }

  .cv-toggle-btn {
    padding: 10px 20px;
    font-size: 16px;
    border-radius: 8px;
    background-color: #007bff;
    color: white;
    border: none;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .cv-toggle-btn:hover {
    background-color: #0056b3;
  }

  .cv-container {
    max-width: 90%;
    margin: 20px auto;
    padding: 20px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
    border-radius: 10px;
    background: #fff;
    display: none;
  }

  .cv-container h2 {
    text-align: center;
    margin-bottom: 15px;
  }
</style>

<script>
  let index = 0;
  const slider = document.querySelector('.video-slider');
  const videos = document.querySelectorAll('.video');
  const totalVideos = videos.length;

  let autoSlideInterval;
  let isVideoPlaying = false;

  function updateSlider() {
    // Slide track
    slider.style.transform = `translateX(-${index * 100}%)`;

    // Handle active scaling
    videos.forEach((video, i) => {
      video.classList.toggle('active', i === index);
    });
  }

  function moveSlider(direction) {
    if (isVideoPlaying) return;

    // Scale down current before moving
    videos[index].classList.remove('active');

    setTimeout(() => {
      index = (index + direction + totalVideos) % totalVideos;
      updateSlider();
    }, 200); // delay to let the scale-down animate
  }

  function autoSlide() {
    if (!isVideoPlaying) {
      moveSlider(1);
    }
  }

  function startAutoSlide() {
    if (!autoSlideInterval && !isVideoPlaying) {
      autoSlideInterval = setInterval(autoSlide, 6000);
    }
  }

  function stopAutoSlide() {
    clearInterval(autoSlideInterval);
    autoSlideInterval = null;
  }

  document.addEventListener('DOMContentLoaded', function () {
    updateSlider();
    startAutoSlide();
  });

  function toggleCV() {
    const cvContainer = document.getElementById('cvContainer');
    const button = document.querySelector('.cv-toggle-btn');
    if (cvContainer.style.display === 'none') {
      cvContainer.style.display = 'block';
      button.textContent = 'Hide CV';
    } else {
      cvContainer.style.display = 'none';
      button.textContent = 'View CV';
    }
  }
</script>
