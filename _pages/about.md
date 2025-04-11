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
        margin: 40px auto 20px auto;
        overflow: hidden;
        position: relative;
        border-radius: 10px;
        box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
    }

    .video-slider {
        display: flex;
        transition: transform 0.5s ease-in-out;
        width: 200%; /* 100% per video */
    }

    .video {
        width: 100%;
        position: relative;
        padding-top: 56.25%; /* 16:9 aspect ratio */
        flex-shrink: 0;
    }

    .video-frame {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 50%;
        border: none;
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
        z-index: 1;
    }

    .prev { left: 5px; }
    .next { right: 5px; }

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
    const totalVideos = document.querySelectorAll('.video').length;

    function updateSlider() {
        slider.style.transform = `translateX(-${index * 100}%)`;
    }

    function moveSlider(direction) {
        index = (index + direction + totalVideos) % totalVideos;
        updateSlider();
    }

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

    // Initialize slider
    document.addEventListener('DOMContentLoaded', () => {
        updateSlider();
    });
</script>
