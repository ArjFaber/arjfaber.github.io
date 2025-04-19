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

<!-- SLIDER SECTION -->
<div class="slider-container" id="sliderContainer">
  <div class="video-slider" id="videoSlider">
    <div class="video active">
      <video muted loop playsinline preload="auto" id="video1">
        <source src="https://arjfaber.github.io/files/Harmony_Data_Collection.mp4" type="video/mp4">
        Your browser does not support the video tag.
      </video>
      <button class="play-btn">&#9658;</button>
    </div>
    <div class="video">
      <video muted loop playsinline preload="auto" id="video2">
        <source src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4" type="video/mp4">
        Your browser does not support the video tag.
      </video>
      <button class="play-btn">&#9658;</button>
    </div>
  </div>
  <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
  <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
</div>

<!-- STATIC VIDEO GRID SECTION -->
<h2>Kuka Robot Recovery Documentation</h2>
<div class="video-grid">
  <div class="video-card">
    <video preload="auto">
      <source src="https://arjfaber.github.io/files/kuka1_.mp4" type="video/mp4">
    </video>
    <button class="play-btn">&#9658;</button>
  </div>
  <div class="video-card">
    <video preload="auto">
      <source src="https://arjfaber.github.io/files/kuka2_.mp4" type="video/mp4">
    </video>
    <button class="play-btn">&#9658;</button>
  </div>
  <div class="video-card">
    <video preload="auto">
      <source src="https://arjfaber.github.io/files/kuka3_.mp4" type="video/mp4">
    </video>
    <button class="play-btn">&#9658;</button>
  </div>
</div>

<!-- SHARED STYLES FOR ALL -->
<style>
  .slider-container {
    max-width: 100%;
    aspect-ratio: 16 / 9;
    position: relative;
    margin: 40px auto;
    border-radius: 15px;
    background-color: black;
    box-shadow: 0px 0px 20px rgba(0, 255, 0, 0.3);
    border: 2px solid #00ff00;
    overflow: hidden;
  }

  .video-slider {
    display: flex;
    transition: transform 0.5s ease-in-out;
  }

  .video {
    min-width: 100%;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0.6;
    transition: all 0.4s ease;
  }

  .video.active {
    opacity: 1;
    transform: scale(1.03);
    box-shadow: 0px 0px 25px rgba(0, 255, 0, 0.6);
  }

  .video video, .video-card video {
    width: 100%;
    height: auto;
    border-radius: 12px;
    pointer-events: none;
  }

  .play-btn {
    position: absolute;
    font-size: 48px;
    color: white;
    background: rgba(0, 0, 0, 0.5);
    border: none;
    border-radius: 50%;
    padding: 10px 16px;
    cursor: pointer;
    z-index: 2;
    transition: opacity 0.3s ease;
    opacity: 0;
  }

  .video:hover .play-btn,
  .video-card:hover .play-btn {
    opacity: 1;
  }

  .btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(0, 0, 0, 0.6);
    border: none;
    color: white;
    font-size: 24px;
    border-radius: 50%;
    padding: 8px 12px;
    cursor: pointer;
    z-index: 10;
  }

  .prev { left: 10px; }
  .next { right: 10px; }

  .video-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 20px;
    padding: 20px;
  }

  .video-card {
    position: relative;
    opacity: 0;
    transform: translateY(40px);
    transition: all 0.8s ease-out;
  }

  .video-card.show {
    opacity: 1;
    transform: translateY(0);
  }

  .video-card video:hover {
    transform: scale(1.05);
    box-shadow: 0 12px 32px rgba(0, 0, 0, 0.4);
    transition: all 0.3s ease;
  }
</style>

<!-- SCRIPTS -->
<script>
document.addEventListener("DOMContentLoaded", () => {
  const slider = document.querySelector('.video-slider');
  const wrappers = document.querySelectorAll('.video');
  const videos = document.querySelectorAll('.video video');
  const buttons = document.querySelectorAll('.video .play-btn');
  const total = wrappers.length;
  let index = 0;
  let autoSlideInterval;

  function updateSlider() {
    slider.style.transform = `translateX(-${index * 100}%)`;
    wrappers.forEach((wrapper, i) => {
      wrapper.classList.toggle('active', i === index);
    });
  }

  function moveSlider(dir) {
    index = (index + dir + total) % total;
    updateSlider();
  }

  function toggleVideo(btn, video) {
    if (video.paused) {
      video.play();
      btn.innerHTML = '&#10074;&#10074;';
    } else {
      video.pause();
      btn.innerHTML = '&#9658;';
    }
  }

  // Attach play button toggle to slider videos
  buttons.forEach((btn, i) => {
    const video = videos[i];
    btn.addEventListener('click', () => toggleVideo(btn, video));
    video.addEventListener('play', () => btn.innerHTML = '&#10074;&#10074;');
    video.addEventListener('pause', () => btn.innerHTML = '&#9658;');
  });

  function startAutoSlideCheck() {
    clearInterval(autoSlideInterval);
    autoSlideInterval = setInterval(() => {
      const currentVideo = wrappers[index].querySelector('video');
      if (currentVideo.paused) {
        moveSlider(1);
      }
    }, 7000);
  }

  updateSlider();
  startAutoSlideCheck();

  // Fade-in animations for static video grid
  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('show');
      }
    });
  }, { threshold: 0.2 });

  document.querySelectorAll('.video-card').forEach(card => {
    observer.observe(card);
  });

  // Static KUKA video play buttons
  document.querySelectorAll('.video-card').forEach(card => {
    const video = card.querySelector('video');
    const btn = card.querySelector('.play-btn');

    btn.addEventListener('click', () => toggleVideo(btn, video));

    video.addEventListener('play', () => btn.innerHTML = '&#10074;&#10074;');
    video.addEventListener('pause', () => btn.innerHTML = '&#9658;');
  });
});
</script>
