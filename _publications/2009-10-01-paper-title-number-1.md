---
title: 'A Universal Translator for Social Behavior in Healthcare Robotics via Reinforcement Learning'
collection: publications
category: manuscripts
permalink: /publication/2009-10-01-paper-title-number-1
excerpt: 'This paper is about the implementation of a machine learning module for service robots in hospitals.'
date: 2024-07-28
venue: 'University of Twente'
slidesurl: 'https://arjfaber.github.io/teaching/'
paperurl: 'https://arjfaber.github.io/files/HARMONY_UT_ML_Module_Report.pdf'
citation: 'Faber, A. et al.(2024)'
---

This research focuses on developing socially aware robotics using reinforcement learning (RL) and artificial neural networks (ANNs). Our goal is to enable robots to understand and respond to social cues, such as gestures, speech, and facial expressions, in a context-sensitive manner.

We implemented Deep Q-Learning (DQN) to optimize decision-making in human-robot interactions. Additionally, we developed a predictive model for sound classification, addressing class imbalance with random oversampling, label simplification, and confidence interval adjustments. These improvements enhanced the model's accuracy and generalization.

Future work includes exploring Bayesian neural networks, SMOTE for data balancing, and real-time learning, aiming to refine socially intelligent robotic behavior.

---

### 🚀 Featured Footage
<div class="video-wall">
    <div class="video-tile featured" data-src="https://arjfaber.github.io/files/Harmony_Data_Collection.mp4">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/Harmony_Data_Collection.mp4"></video>
      <button class="play-btn">&#9658;</button>
    </div>
    <div class="video-tile" data-src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4"></video>
      <button class="play-btn">&#9658;</button>
    </div>
    <div class="video-tile" data-src="https://arjfaber.github.io/files/kuka1_.mp4">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka1_.mp4"></video>
      <button class="play-btn">&#9658;</button>
    </div>
    <div class="video-tile" data-src="https://arjfaber.github.io/files/kuka2_.mp4">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka2_.mp4"></video>
      <button class="play-btn">&#9658;</button>
    </div>
    <div class="video-tile" data-src="https://arjfaber.github.io/files/kuka3_.mp4">
      <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka3_.mp4"></video>
      <button class="play-btn">&#9658;</button>
    </div>
  </div>

  <!-- Modal -->
  <div class="video-modal" id="videoModal">
    <div class="modal-content">
      <video controls autoplay id="modalVideo"></video>
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

    .video-tile {
        width: 50%;
        height: 50%
      position: relative;
      border-radius: 15px;
      overflow: hidden;
      box-shadow: 0 0 20px rgba(0, 255, 200, 0.2);
      transition: transform 0.4s ease, box-shadow 0.4s ease;
      cursor: pointer;
    }

    .video-tile video {
      width: 80%;
      height: 80%;
      object-fit: cover;
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

    /* Modal styles */
    .video-modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(10, 10, 10, 0.95);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }

    .modal-content {
      position: relative;
      max-width: 90%;
      width: 800px;
    }

    .modal-content video {
      width: 100%;
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
    document.querySelectorAll(".video-tile").forEach(tile => {
      const btn = tile.querySelector(".play-btn");
      const video = tile.querySelector("video");
      const src = tile.dataset.src;

      btn.addEventListener("click", (e) => {
        e.stopPropagation();
        if (video.paused) {
          video.play();
          btn.innerHTML = "&#10074;&#10074;";
        } else {
          video.pause();
          btn.innerHTML = "&#9658;";
        }
      });

      tile.addEventListener("click", () => {
        const modal = document.getElementById("videoModal");
        const modalVideo = document.getElementById("modalVideo");
        modalVideo.src = src;
        modal.style.display = "flex";
      });
    });

    document.querySelector(".close-btn").addEventListener("click", () => {
      const modal = document.getElementById("videoModal");
      const modalVideo = document.getElementById("modalVideo");
      modal.style.display = "none";
      modalVideo.pause();
      modalVideo.src = "";
    });
  </script>
