---
permalink: /
title: "About"
author_profile: true
description: "MSc Data Science at the University of Edinburgh, specializing in RL and Formal Proofs in AI."
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
            <iframe class="video-frame lazy-load" data-src="https://www.youtube.com/embed/k-XBWFp1FAQ?autoplay=1&mute=1" allowfullscreen></iframe>
        </div>
        <div class="video">
            <video class="video-frame lazy-load" controls>
                <source data-src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
        </div>
        <div class="video">
            <iframe class="video-frame lazy-load" data-src="https://www.youtube.com/embed/X8vEKe2i508?autoplay=1&mute=1" allowfullscreen></iframe>
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
        width: 100%;
        max-width: 560px;
        height: auto;
        border-radius: 10px;
    }

    .btn {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        background-color: rgba(0, 0, 0, 0.7);
        color: white;
        border: none;
        padding: 15px;
        cursor: pointer;
        font-size: 20px;
        border-radius: 5px;
    }

    .prev { left: 5px; }
    .next { right: 5px; }

    .btn:hover {
        background-color: rgba(0, 0, 0, 0.9);
        transform: scale(1.1);
    }
</style>

<script>
    let index = 0;
    const slider = document.querySelector('.video-slider');
    const totalVideos = document.querySelectorAll('.video').length;

    let autoSlideInterval;
    let isVideoPlaying = false;

    function updateSlider() {
        slider.style.transform = `translateX(-${index * 100}%)`;
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

    // Start slider immediately without waiting for videos
    startAutoSlide();

    // Lazy load videos when they come into view
    function lazyLoad() {
        const lazyVideos = document.querySelectorAll('.lazy-load');
        lazyVideos.forEach((video) => {
            const rect = video.getBoundingClientRect();
            if (rect.top < window.innerHeight && rect.bottom > 0) {
                if (video.tagName === 'IFRAME') {
                    video.src = video.dataset.src;
                } else if (video.tagName === 'VIDEO') {
                    const source = video.querySelector('source');
                    source.src = source.dataset.src;
                    video.load();
                }
                video.classList.remove('lazy-load');
            }
        });
    }

    // Listen for scroll and resize events to trigger lazy loading
    window.addEventListener('scroll', lazyLoad);
    window.addEventListener('resize', lazyLoad);
    window.addEventListener('load', lazyLoad);

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
            startAutoSlide();  // Resume auto-sliding after video ends
        });
    });

    // Initialize the slider position
    updateSlider();
</script>
