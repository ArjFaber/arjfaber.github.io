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

<!-- Video Wall Section -->
<div class="video-wall">
  <div class="video-tile tall-fit" data-src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4" tabindex="0">
    <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4"></video>
    <div class="video-meta">
      <h4>Unofficial final demo</h4>
    </div>
    <span class="badge">NEW</span>
    <p class="esc-text">Press ESC to close</p>
    <button class="play-btn">&#9658;</button>
  </div>

  <div class="video-tile featured" data-src="https://arjfaber.github.io/files/Harmony_Data_Collection.mp4" tabindex="0">
    <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/Harmony_Data_Collection.mp4"></video>
    <div class="video-meta">
      <h4>Data gathering</h4>
      <p>Leveraging Kuka's cameras and sensor input</p>
    </div>
    <p class="esc-text">Press ESC to close</p>
    <button class="play-btn">&#9658;</button>
  </div>

 <div class="slider-container">
  <div class="video-slider">
    <div class="video-tile" data-src="https://arjfaber.github.io/files/kuka1_.mp4" tabindex="0">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka1_.mp4"></video>
      <div class="video-meta">
        <h4>Finetuning Kuka controls (i)</h4>
        <p>Initial experiments for remote control</p>
      </div>
      <p class="esc-text">Press ESC to close</p>
      <button class="play-btn">&#9658;</button>
    </div>
    <div class="video-tile " data-src="https://arjfaber.github.io/files/kuka2_.mp4" tabindex="0">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka2_.mp4"></video>
      <div class="video-meta">
        <h4>Finetuning Kuka controls (ii)</h4>
        <p>Trajectory smoothing improvements</p>
      </div>
      <p class="esc-text">Press ESC to close</p>
      <button class="play-btn">&#9658;</button>
    </div>
    <div class="video-tile" data-src="https://arjfaber.github.io/files/kuka3_.mp4" tabindex="0">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka3_.mp4"></video>
      <div class="video-meta">
        <h4>Finetuning Kuka controls (iii)</h4>
        <p>Velocity and responsiveness test</p>
      </div>
      <p class="esc-text">Press ESC to close</p>
      <button class="play-btn">&#9658;</button>
    </div>
  </div>

  <!-- Buttons must be inside slider-container -->
  <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
  <button class="btn next" onclick="moveSlider(1)">&#10095;</button>

</div> 

<!-- Modal -->
<div class="video-modal" id="videoModal">
  <div class="modal-content">
    <video controls autoplay id="modalVideo"></video>
     <p class="esc-text">Press ESC to close</p>
    <span class="close-btn">&times;</span>
  </div>
</div>

<!-- Styles -->
<style>
  .esc-text {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 16px;
  color: #00ffcc;
  background-color: rgba(0, 0, 0, 0.7);
  padding: 8px 12px;
  border-radius: 5px;
  display: none;
  cursor: pointer;
  z-index: 2;
  transition: all 0.3s ease;
}

.video-tile:hover .esc-text {
  display: block;
}

.esc-text:hover {
  background-color: rgba(0, 0, 0, 0.9);
  box-shadow: 0 0 8px rgba(0, 255, 255, 0.8);
}
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
    overflow: hidden;
    aspect-ratio: 16 / 9;
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
  }
      }

    .slider-container {
    max-width: 100%;
    overflow: hidden;
    aspect-ratio: 16 / 9;
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
        transform: scale(1);
        opacity: 0.6;
        transition: transform 0.4s ease, opacity 0.4s ease;
    }


    .video-slider {
        display: flex;
        height: 100%;
        width: 100%;
        transition: transform 0.5s ease-in-out;
    }
 .video.active {
    transform: scale(1.05);
    opacity: 1;
    box-shadow: 0px 0px 25px rgba(0, 255, 0, 0.7); /* Neon green active glow */
}.prev { left: 5px; }
    .next { right: 5px; }

    .btn:hover {
        background-color: rgba(0, 0, 0, 0.8);
    }
  .video-tile {
    width: 100%;
    height: 100%;
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

  .featured {
    animation: pulseFeature 4s infinite alternate ease-in-out;
  }

  @keyframes pulseFeature {
    0% {
      transform: scale(1);
      box-shadow: 0 0 25px rgba(0, 255, 150, 0.4);
    }
    100% {
      transform: scale(1.05);
      box-shadow: 0 0 40px rgba(0, 255, 255, 0.6);
    }
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

  .video-meta {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 12px 15px;
    background: linear-gradient(to top, rgba(0,0,0,0.7), rgba(0,0,0,0));
    z-index: 2;
  }

  .video-meta h4,
  .video-meta p {
    margin: 0;
    color: #00ffcc;
    text-shadow: 0 0 6px rgba(0,0,0,0.6);
  }

  .video-meta h4 {
    font-size: 18px;
    font-weight: bold;
  }

  .video-meta p {
    font-size: 14px;
    margin-top: 4px;
  }

  .badge {
    position: absolute;
    top: 10px;
    left: 10px;
    background-color: #ff4081;
    color: white;
    padding: 4px 8px;
    border-radius: 4px;
    font-size: 12px;
    font-weight: bold;
    z-index: 3;
  }

  @media (max-width: 600px) {
    .video-meta h4 {
      font-size: 16px;
    }
    .video-meta p {
      font-size: 12px;
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
  .video-slider .video {
  flex: 0 0 100%;
  max-width: 100%;
}
</style>
<!-- Scripts -->
<script>
let index = 0;
const slider = document.querySelector(".video-slider");
const videoElements = document.querySelectorAll(".video-slider .video");
const totalVideos = videoElements.length;
let isVideoPlaying = false;

// Open modal
document.querySelectorAll(".video-tile").forEach(tile => {
  const btn = tile.querySelector(".play-btn");
  const video = tile.querySelector("video");
  const src = tile.dataset.src;

  btn.addEventListener("click", (e) => {
    e.stopPropagation();
    if (video.paused) {
      video.play();
      btn.innerHTML = "&#10074;&#10074;"; // Pause icon
    } else {
      video.pause();
      btn.innerHTML = "&#9658;"; // Play icon
    }
  });

  tile.addEventListener("click", () => {
    const modal = document.getElementById("videoModal");
    const modalVideo = document.getElementById("modalVideo");

    modalVideo.src = src;
    modalVideo.load();
    modalVideo.play();
    modal.style.display = "flex";
  });

  tile.addEventListener("keypress", (e) => {
    if (e.key === "Enter") {
      tile.click();
    }
  });
});

// Close modal
document.querySelector(".close-btn").addEventListener("click", () => {
  const modal = document.getElementById("videoModal");
  const modalVideo = document.getElementById("modalVideo");
  modal.style.display = "none";
  modalVideo.pause();
  modalVideo.src = "";
});

// Close modal with ESC
document.addEventListener('keydown', function(e) {
  if (e.key === 'Escape') {
    const modal = document.getElementById("videoModal");
    const modalVideo = document.getElementById("modalVideo");
    if (modal.style.display === "flex") {
      modal.style.display = "none";
      modalVideo.pause();
      modalVideo.src = "";
    }
  }
});

// Move slider manually
function updateSlider() {
  slider.style.transform = translateX(-${index * 100}%);

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
  }, 400);
}

document.addEventListener('DOMContentLoaded', function () {
  updateSlider();
});
</script> 
