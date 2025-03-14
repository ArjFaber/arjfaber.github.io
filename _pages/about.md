permalink: /
title: ""
author_profile: true
description: "Specializing in Reinforcement Learning, High-Performance Computing, and Robotics."
redirect_from: 
  - /about/
  - /about.html
---

# Arjan Faber  

🔬 MSc Data Science, University of Edinburgh - Researching Formal Proofs in RL  
💡 Passionate about Machine Learning, High-Performance Computing & Robotics  

---

## 🔍 About Me  

I'm a graduate researcher with a background in econometrics, AI, and reinforcement learning. My work spans deep learning, robotics, and formal verification of algorithms. Currently, I'm researching **formal proof methods for reinforcement learning** at the University of Edinburgh.  

When I'm not coding, you'll find me playing jazz guitar, following Formula 1, or traveling the world!  

---

## 🛠️ Skills & Expertise  

- **AI & Machine Learning** – Deep Learning, Reinforcement Learning, Bayesian Neural Networks  
- **High-Performance Computing (HPC)** – OpenMP, MPI, SLURM, ARCHER2  
- **Programming** – Python, C++, C#, MATLAB, R  
- **Robotics & AI** – ROS1/ROS2, OpenPose, SLAM  

---

## 🎥 Recent Activity

<div class="slider-container">
    <div class="video-slider">
        <div class="video">
            <iframe class="video-frame" src="https://www.youtube.com/embed/k-XBWFp1FAQ?autoplay=0&mute=0" allowfullscreen></iframe>
        </div>
        <div class="video">
            <video class="video-frame" controls>
                <source src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
        </div>
        <div class="video">
         <iframe class="video-frame" src="https://www.youtube.com/embed/X8vEKe2i508?autoplay=0&mute=0" allowfullscreen></iframe>
        </div>
    </div>
    <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
    <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
</div>

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
        slider.style.transform = translateX(-${index * 100}%);
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
    startAutoSlide();

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

