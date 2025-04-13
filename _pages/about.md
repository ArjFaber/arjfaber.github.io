---
permalink: /
title: "Arjan Faber – MSc student"
author_profile: true
description: "Specializing in Reinforcement Learning, High-Performance Computing, and Robotics."
redirect_from: 
  - /about/
  - /about.html
---

<!-- Load YouTube IFrame API -->
<script src="https://www.youtube.com/iframe_api"></script>

<!-- Video Slider -->
<div class="slider-container">
    <div class="video-slider">
        <div class="video active">
            <iframe class="video-frame" id="player1" src="https://www.youtube.com/embed/k-XBWFp1FAQ?enablejsapi=1" allowfullscreen></iframe>
        </div>
        <div class="video">
            <iframe class="video-frame" id="player2" src="https://www.youtube.com/embed/X8vEKe2i508?enablejsapi=1" allowfullscreen></iframe>
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
        width: 300%;
        transition: transform 0.5s ease-in-out;
    }

    .video {
        min-width: 100%;
        box-sizing: border-box;
        display: flex;
        justify-content: center;
        align-items: center;
        transform: scale(0.9);
        opacity: 0.6;
        transition: transform 0.4s ease, opacity 0.4s ease;
    }

    .video.active {
        transform: scale(1.05);
        opacity: 1;
        z-index: 2;
    }

    @keyframes popOutIn {
        0% { transform: scale(1.05); }
        50% { transform: scale(1.15); }
        100% { transform: scale(1.05); }
    }

    .video.pop-animate {
        animation: popOutIn 1.5s ease;
        z-index: 2;
    }

    .video-frame {
        width: 100%;
        max-width: 100%;
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
        z-index: 3;
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
    const videoElements = document.querySelectorAll('.video');
    const totalVideos = videoElements.length;

    let autoSlideInterval;
    let isVideoPlaying = false;
    let ytPlayers = [];

    function updateSlider() {
        slider.style.transform = `translateX(-${index * 100}%)`;

        videoElements.forEach((vid, i) => {
            vid.classList.toggle('active', i === index);
        });
    }

    function moveSlider(direction) {
        if (isVideoPlaying) return;

        const currentVideo = videoElements[index];
        currentVideo.classList.add('pop-animate');

        setTimeout(() => {
            currentVideo.classList.remove('pop-animate');
            index = (index + direction + totalVideos) % totalVideos;
            updateSlider();
        }, 1600);
    }

    function autoSlide() {
        if (isVideoPlaying) return;

        const currentVideo = videoElements[index];
        currentVideo.classList.add('pop-animate');

        setTimeout(() => {
            currentVideo.classList.remove('pop-animate');
            index = (index + 1) % totalVideos;
            updateSlider();
        }, 1600);
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

    // YouTube IFrame API callback
    function onYouTubeIframeAPIReady() {
        const iframes = document.querySelectorAll('.video-frame');
        iframes.forEach((iframe, i) => {
            ytPlayers[i] = new YT.Player(iframe, {
                events: {
                    'onStateChange': function (event) {
                        if (event.data === YT.PlayerState.PLAYING) {
                            isVideoPlaying = true;
                            stopAutoSlide();
                        } else if (
                            event.data === YT.PlayerState.PAUSED ||
                            event.data === YT.PlayerState.ENDED
                        ) {
                            isVideoPlaying = false;
                            startAutoSlide();
                        }
                    }
                }
            });
        });
    }

    document.addEventListener('DOMContentLoaded', function () {
        updateSlider();
        startAutoSlide();
    });
</script>
