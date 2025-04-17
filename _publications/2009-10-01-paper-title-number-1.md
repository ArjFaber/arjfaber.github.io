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
    margin: 40px auto;
    border-radius: 15px;
    background: linear-gradient(145deg, #1f1f1f, #333);
    box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.6), 0px 0px 10px rgba(0, 255, 0, 0.3);
    border: 2px solid #00ff00;
  }

  .video-slider {
    display: flex;
    transition: transform 0.5s ease-in-out;
    width: 100%;
  }

  .video {
    min-width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0.6;
    transition: transform 0.4s ease, opacity 0.4s ease;
  }

  .video.active {
    transform: scale(1.05);
    opacity: 1;
    box-shadow: 0px 0px 25px rgba(0, 255, 0, 0.7);
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
    z-index: 2;
  }

  .prev { left: 10px; }
  .next { right: 10px; }

  .btn:hover {
    background-color: rgba(0, 0, 0, 0.8);
  }
</style>

<script>
  let index = 0;
  const slider = document.querySelector('.video-slider');
  const videos = document.querySelectorAll('.video');
  const totalVideos = videos.length;
  const videoTags = document.querySelectorAll('video');
  let autoSlideTimer;

  function updateSlider() {
    slider.style.transform = `translateX(-${index * 100}%)`;
    videos.forEach((v, i) => {
      v.classList.toggle('active', i === index);
    });
  }

  function moveSlider(direction) {
    index = (index + direction + totalVideos) % totalVideos;
    updateSlider();
    resetAutoSlide();
  }

  function autoSlide() {
    if (![...videoTags].some(video => !video.paused)) {
      index = (index + 1) % totalVideos;
      updateSlider();
    }
    autoSlideTimer = setTimeout(autoSlide, 6000);
  }

  function resetAutoSlide() {
    clearTimeout(autoSlideTimer);
    autoSlideTimer = setTimeout(autoSlide, 6000);
  }

  function attachPlayPauseListeners() {
    videoTags.forEach(video => {
      video.addEventListener('play', () => {
        clearTimeout(autoSlideTimer);
      });
      video.addEventListener('pause', () => {
        resetAutoSlide();
      });
      video.addEventListener('ended', () => {
        resetAutoSlide();
      });
    });
  }

  document.addEventListener('DOMContentLoaded', () => {
    updateSlider();
    attachPlayPauseListeners();
    resetAutoSlide();
  });
</script>
