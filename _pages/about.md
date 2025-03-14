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

## 🎥 Video Slider

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
    <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
    <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
</div>

<style>
    .slider-container {
        width: 560px; /* Reduced size for better fit */
        overflow: hidden;
        position: relative;
        margin: auto; /* Centers the slider */
        border-radius: 10px;
        box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
        display: flex;
        justify-content: center;
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
        width: 560px; /* Slightly smaller width */
        height: 315px; /* Maintains 16:9 aspect ratio */
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
    function moveSlider(direction) {
        const slider = document.querySelector('.video-slider');
        const totalVideos = document.querySelectorAll('.video').length;
        index = (index + direction + totalVideos) % totalVideos;
        slider.style.transform = `translateX(-${index * 100}%)`;
    }
</script>
