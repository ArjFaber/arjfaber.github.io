---
permalink: /
title: ""
author_profile: true
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

## 🎥 Most recent work

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
    </div>
    <div class="dots">
        <span class="dot active" onclick="selectSlide(0)"></span>
        <span class="dot" onclick="selectSlide(1)"></span>
    </div>
</div>

<style>
    .slider-container {
        width: 560px;
        overflow: hidden;
        position: relative;
        margin: auto;
        border-radius: 10px;
        box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .video-slider {
        display: flex;
        width: 200%;
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

    .dots {
        display: flex;
        justify-content: center;
        margin-top: 10px;
    }

    .dot {
        width: 12px;
        height: 12px;
        margin: 0 5px;
        background-color: #bbb;
        border-radius: 50%;
        display: inline-block;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }

    .dot.active {
        background-color: #555;
    }

</style>

<script>
    let index = 0;
    const totalVideos = document.querySelectorAll('.video').length;
    const slider = document.querySelector('.video-slider');
    const dots = document.querySelectorAll('.dot');

    function updateSlider() {
        slider.style.transform = `translateX(-${index * 100}%)`;
        dots.forEach(dot => dot.classList.remove('active'));
        dots[index].classList.add('active');
    }

    function selectSlide(newIndex) {
        index = newIndex;
        updateSlider();
        resetAutoSlide();
    }

    function autoSlide() {
        index = (index + 1) % totalVideos;
        updateSlider();
    }

    let autoSlideInterval = setInterval(autoSlide, 5000);

    function resetAutoSlide() {
        clearInterval(autoSlideInterval);
        autoSlideInterval = setInterval(autoSlide, 5000);
    }
</script>
