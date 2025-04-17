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

### Featured Footage

<div class="slider-container">
  <div class="video-slider" id="videoSlider">
    <div class="video active">
      <video width="640" height="360" muted loop playsinline>
        <source src="https://arjfaber.github.io/files/Harmony_Data_Collection.mp4" type="video/mp4">
        Your browser does not support the video tag.
      </video>
    </div>
    <div class="video">
      <video width="640" height="360" muted loop playsinline>
        <source src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4" type="video/mp4">
        Your browser does not support the video tag.
      </video>
    </div>
  </div>
  <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
  <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
</div>

![KUKA Robot Image](https://arjfaber.github.io/files/UT.png)

<style>
  .slider-container {
    max-width: 100%;
    overflow: hidden;
    aspect-ratio: 16 / 9;
    position: relative;
    margin: 40px auto 20px auto;
    border-radius: 15px;
    background-color: #f8f8f8; /* Ibis white */
    box-shadow: 0px 0px 20px rgba(0, 255, 0, 0.3);
    border: 2px solid #00ff00; /* Green LED border */
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
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0.6;
    transition: transform 0.4s ease, opacity 0.4s ease;
  }

  .video.active {
    opacity: 1;
  }

  .video.paused {
    animation: zoomPulse 2s infinite ease-in-out;
    z-index: 2;
  }

  @keyframes zoomPulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.04); }
    100% { transform: scale(1); }
  }

  .btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba(0, 0, 0, 0.6);
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
</style>

<script>
  let index = 0;
  const slider = document.querySelector('.video-slider');
  const videos = document.querySelectorAll('.video video');
  const wrappers = document.querySelectorAll('.video');
  const total = wrappers.length;

  function updateSlider() {
    slider.style.transform = `translateX(-${index * 100}%)`;
    wrappers.forEach((wrapper, i) => {
      wrapper.classList.toggle('active', i === index);
    });
    applyPausedAnimation();
  }

  function moveSlider(dir) {
    index = (index + dir + total) % total;
    updateSlider();
  }

  function applyPausedAnimation() {
    wrappers.forEach((wrapper, i) => {
      const vid = wrapper.querySelector('video');
      if (i === index && vid.paused) {
        wrapper.classList.add('paused');
      } else {
        wrapper.classList.remove('paused');
      }
    });
  }

  videos.forEach((video, i) => {
    video.addEventListener('play', () => {
      wrappers[i].classList.remove('paused');
    });
    video.addEventListener('pause', () => {
      if (i === index) {
        wrappers[i].classList.add('paused');
      }
    });
  });

  // Auto-slide if current video is paused
  let autoSlideInterval = setInterval(() => {
    const currentVideo = wrappers[index].querySelector('video');
    if (currentVideo.paused) {
      moveSlider(1);
    }
  }, 3000); // Slide every 7s when paused

  document.addEventListener('DOMContentLoaded', updateSlider);
</script>
