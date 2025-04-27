---
title: "Designing an Adaptive ML Module for Social Behavior Acquisition of Service Robots"
collection: publications
category: manuscripts
permalink: /publication/2009-10-01-paper-title-number-1
excerpt: 'This paper introduces an adaptive ML module for service robots in complex hospital environments.'
date: 2024-08-01
venue: 'University of Twente (Human Media Interaction Group)'
paperurl: 'http://arjfaber.github.io/files/HARMONY_UT_ML_MODULE_Report.pdf'
slidesurl: 'https://github.com/ArjFaber/Bayesian_Neural_Network/wiki/Post-%5BUpdated-10-November-2024%5D-A-hard-coded-BNN-solution-implemented-for-a-Seattle-weather-dataset'
citation: 'Faber A. et al. (2024)'
---
This research focuses on developing socially aware robotics using reinforcement learning (RL) and artificial neural networks (ANNs). Our goal is to enable robots to understand and respond to social cues, such as gestures, speech, and facial expressions, in a context-sensitive manner.

We implemented Deep Q-Learning (DQN) to optimize decision-making in human-robot interactions. Additionally, we developed a predictive model for sound classification, addressing class imbalance with random oversampling, label simplification, and confidence interval adjustments. These improvements enhanced the model’s accuracy and generalization.

Future work includes exploring Bayesian neural networks, SMOTE for data balancing, and real-time learning, aiming to refine socially intelligent robotic behavior.

### 🚀 Featured Footage
<div class="video-wall">
   <div class="video-tile tall-fit" data-src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4" tabindex="0">
    <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4"></video>
    <div class="video-meta">
      <h4>Unofficial final demo</h4>
    </div>
      <span class="badge">NEW</span>
    <button class="play-btn">&#9658;</button>
  </div>
  
  <div class="video-tile featured" data-src="https://arjfaber.github.io/files/Harmony_Data_Collection.mp4" tabindex="0">
    <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/Harmony_Data_Collection.mp4"></video>
    <div class="video-meta">
      <h4>Data gathering</h4>
      <p>Leveraging Kuka's camera's and sensor input</p>
    </div>
    <button class="play-btn">&#9658;</button>
  </div>
</div>

<div class="slider-container">
    <div class="video-slider"> 
    <div class="video_slide" data-src="https://arjfaber.github.io/files/kuka1_.mp4" tabindex="0">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka1_.mp4"></video>
      <div class="video-meta">
        <h4>Finetuning Kuka controls (i)</h4>
        <p>Initial experiments for remote control</p>
      </div>
    <div class="video_slide" data-src="https://arjfaber.github.io/files/kuka2_.mp4" tabindex="0">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka2_.mp4"></video>
      <div class="video-meta">
        <h4>Finetuning Kuka controls (ii)</h4>
        <p>Trajectory smoothing improvements</p>
      </div>
    </div>
    <div class="video_slide" data-src="https://arjfaber.github.io/files/kuka3_.mp4" tabindex="0">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka3_.mp4"></video>
      <div class="video-meta">
        <h4>Finetuning Kuka controls (iii)</h4>
        <p>Velocity and responsiveness test</p>
      </div>
    </div>
       </div>
       <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
    <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
 
 </div>
  <!-- Slider to move between videos -->
  <div class="slider">
    <input type="range" min="0" max="2" value="0" id="video-slider" step="1">
  </div>
</div>

<!-- Modal -->
<div class="video-modal" id="videoModal">
  <div class="modal-content">
    <video controls autoplay id="modalVideo"></video>
    <h4>Press Esc to close</h4>
    <span class="close-btn">&times;</span>
  </div>
</div>

<style>
  body {
    background: #000;
    color: #00ffcc;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 40px 20px;
  }

  .video-wall {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    margin-top: 40px;
    z-index: 1;
  }

   .slider-container {
    max-width: 100%;
    aspect-ratio: 16/9;
    overflow: hidden;
    position: relative;
    margin: 40px auto 20px auto;
    border-radius: 15px;
    background: linear-gradient(145deg, #1f1f1f, #333);  /* Dark futuristic gradient */
    box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.6), 0px 0px 10px rgba(0, 255, 0, 0.3);  /* Subtle glowing neon effect */
    display: flex;
    justify-content: center;
    align-items: center;
    border: 2px solid #00ff00;  /* Neon green border */
    position: relative;
    transition: opacity 0.3s ease;
  }
  .video-slider {
    display: flex;
    height: 100%;
    width: 100%;
    transition: transform 0.5s ease-in-out;
    object-fit: contain;
  }

  .video-slide {
    position: relative;
    box-sizing: border-box;
    display: flex;
    justify-content: center;
    align-items: center;
    object-fit: contain;
  }

  .video-slide video {
    width: 100%;
    height: 100%;
    
  }

  .video-tile {
    position: relative;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: 0 0 20px rgba(0, 255, 200, 0.2);
    transition: transform 0.4s ease, box-shadow 0.4s ease;
    cursor: pointer;
    outline: none;
  }

  .video-tile video {
    width: 100%;
    height: 100%;
    object-fit: contain;
    display: block;
    filter: grayscale(20%);
    transition: all 0.4s ease;
  }

  .video-tile:hover {
    transform: scale(1.03);
    box-shadow: 0 0 30px rgba(0, 255, 150, 0.5);
  }

  .video-tile:hover video {
    filter: grayscale(0%);
  }

  .play-btn {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 42px;
    color: #00ffcc;
    background: rgba(0, 0, 0, 0.6);
    border: 2px solid #00ffcc;
    border-radius: 50%;
    padding: 12px 16px;
    cursor: pointer;
    z-index: 2;
    opacity: 0;
    transition: all 0.3s ease;
    animation: none;
  }

  .video-tile:hover .play-btn {
    opacity: 1;
    animation: pulseGlow 1.5s infinite ease-in-out;
  }

  @keyframes pulseGlow {
    0%, 100% {
      transform: translate(-50%, -50%) scale(1);
      box-shadow: 0 0 15px #00ffd5;
    }
    50% {
      transform: translate(-50%, -50%) scale(1.1);
      box-shadow: 0 0 25px #00ffcc;
    }
  }

  .video-modal {
    position: fixed;
    top: 0;
    left: 0;
    background: rgba(10, 10, 10, 0.95);
    display: none;
    justify-content: center;
    align-items: center;
    z-index: 1000;
    width: 100%;
    height: 100%;
  }

  .video-modal h4 {
    color: #00ffcc;
    font-size: 16px;
    margin-top: 10px;
    text-align: center;
  }

  .modal-content {
    position: relative;
    max-width: 90%;
    max-height: 80%;
  }

  .modal-content video {
    width: 100%;
    height: auto;
    border-radius: 10px;
  }

  .close-btn {
    position: absolute;
    top: -40px;
    right: 0;
    font-size: 36px;
    color: #00ffcc;
    cursor: pointer;
  }
</style>

<script>
  let index = 0;
  const slider = document.querySelector('.video-slider');
  const videoElements = document.querySelectorAll('.video');
  const totalVideos = videoElements.length;

  let autoSlideInterval;
  let isVideoPlaying = false;

  const modal = document.getElementById("videoModal");
  const modalVideo = document.getElementById("modalVideo");
  const closeBtn = document.querySelector(".close-btn");

  document.querySelectorAll(".video-tile").forEach(tile => {
    const btn = tile.querySelector(".play-btn");
    const video = tile.querySelector("video");
    const src = tile.dataset.src;

    btn.addEventListener("click", (e) => {
      e.stopPropagation();
      if (video.paused) {
        video.play();
        btn.innerHTML = "&#10074;&#10074;"; // Pause symbol
      } else {
        video.pause();
        btn.innerHTML = "&#9658;"; // Play symbol
      }
    });

    tile.addEventListener("click", () => {
      modalVideo.src = src;
      modal.style.display = "flex";
      modalVideo.play();
    });

    tile.addEventListener("keypress", (e) => {
      if (e.key === "Enter") {
        tile.click();
      }
    });
  });

  closeBtn.addEventListener("click", () => {
    modal.style.display = "none";
    modalVideo.pause();
    modalVideo.src = "";
  });

  document.addEventListener("keydown", (e) => {
    if (e.key === "Escape" && modal.style.display === "flex") {
      modal.style.display = "none";
      modalVideo.pause();
      modalVideo.src = "";
    }
  });

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

  function startAutoSlide() {
    if (!autoSlideInterval && !isVideoPlaying) {
      autoSlideInterval = setInterval(autoSlide, 5000);
    }
  }

  function stopAutoSlide() {
    clearInterval(autoSlideInterval);
    autoSlideInterval = null;
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

  document.addEventListener('DOMContentLoaded', function () {
    updateSlider();
    startAutoSlide();
  });
</script>

