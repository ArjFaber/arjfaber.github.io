---
permalink: /
title: "Arjan Faber – About Me"
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
            <div>
                <iframe class="video-frame" id="player1" src="https://www.youtube.com/embed/k-XBWFp1FAQ?enablejsapi=1" allowfullscreen></iframe>
            </div>
        </div>
        <div class="video">
            <div>
                <iframe class="video-frame" id="player2" src="https://www.youtube.com/embed/X8vEKe2i508?enablejsapi=1" allowfullscreen></iframe>
            </div>
        </div>
    </div>
    <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
    <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
</div>

<!-- Fun Fact Section -->
<div id="funFact" class="fun-fact">🤔 Fun fact loading...</div>

<!-- Intro Text -->
<p style="text-align:center; margin-top: 20px;">
  Hi, welcome to my website! It contains most of my academic related work to date.<br>
  <a href="#cvContainer">Jump to CV</a> or check below for project previews!
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

<!-- Project Cards -->
<div class="project-card">
    <h3>🤖 Robotic Grasping with RL</h3>
    <p>Used deep reinforcement learning to teach a robotic arm to pick up objects with precision and efficiency.</p>
    <button onclick="alert('Coming soon: Detailed project breakdown!')">Learn More</button>
</div>

<div class="project-card">
    <h3>💻 HPC-Based Climate Modeling</h3>
    <p>Simulated large-scale weather systems using high-performance clusters to improve forecast accuracy.</p>
    <button onclick="alert('Coming soon: Interactive simulation link!')">Learn More</button>
</div>

<style>
    body.dark-mode {
        background-color: #121212;
        color: white;
    }

    .dark-mode .cv-container {
        background: #1e1e1e;
    }

    .slider-container {
        max-width: 100%;
        overflow: hidden;
        aspect-ratio: 16 /9;  
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
        height: 100%;
        width: 100%;
        transition: transform 0.5s ease-in-out;
    }

    .video {
        min-width: 100%;
        height: 100%;
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
        border: none;
        border-radius: 10px;
        
    }

    .video-caption {
        text-align: center;
        font-size: 14px;
        margin-top: 10px;
        color: #555;
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

    .fun-fact {
        text-align: center;
        margin-top: 25px;
        font-style: italic;
        color: #666;
    }

    .project-card {
        max-width: 600px;
        margin: 20px auto;
        padding: 20px;
        border-radius: 12px;
        background: #f7f7f7;
        box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        transition: transform 0.2s;
        text-align: center;
    }

    .project-card:hover {
        transform: scale(1.02);
    }

    .project-card h3 {
        margin-bottom: 10px;
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

    const facts = [
        "Reinforcement Learning mimics how humans learn by reward!",
        "The first neural network was proposed in 1943!",
        "HPC clusters can simulate entire galaxies 🌌",
        "Robots don’t get tired — just overheating CPUs 🧠🔥",
    ];

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

    function toggleDarkMode() {
        document.body.classList.toggle('dark-mode');
    }

    function showRandomFact() {
        document.getElementById('funFact').textContent = "💡 " + facts[Math.floor(Math.random() * facts.length)];
    }

    setInterval(showRandomFact, 6000);

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
        showRandomFact();
    });
</script>
