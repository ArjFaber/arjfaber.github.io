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

<!-- SLIDER SECTION -->
<div class="slider-container tech-bg" id="sliderContainer">
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
  <button class="btn prev slide-in">&#10094;</button>
  <button class="btn next slide-in">&#10095;</button>
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

<!-- STYLES -->
<style>
  /* Matrix-style animated background */
  .tech-bg::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: radial-gradient(ellipse at center, #001100 0%, #000000 100%);
    opacity: 0.7;
    z-index: 0;
    pointer-events: none;
  }

  /* Slider Container */
  .slider-container {
    max-width: 100%;
    height: 500px; /* Set height for proper display */
    position: relative;
    margin: 40px auto;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: 0 0 30px rgba(0, 255, 100, 0.3);
    border: 2px solid #00ff9e;
    background-color: #000; /* For better visibility */
  }

  /* Slider Content */
  .video-slider {
    display: flex;
    transition: transform 0.5s ease-in-out;
    z-index: 1;
  }

  /* Video Styling for Each Slider Video */
  .video {
    min-width: 100%;
    width: 100%;
    height: 100%; /* Make sure the video fills the height */
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0.7;
    transition: all 0.4s ease;
    filter: grayscale(20%);
    will-change: transform; /* Optimize for smooth animations */
  }

  /* Active Video Styling with Zoom and Glow */
  .video.active {
    opacity: 1;
    transform: scale(1.08); /* Zoom effect */
    filter: grayscale(0%);
    box-shadow: 0px 0px 35px rgba(0, 255, 100, 0.6); /* Glow effect */
    animation: glow 1.5s infinite alternate; /* Glowing effect */
  }

  /* Keyframes for Glow Animation */
  @keyframes glow {
    0% {
      box-shadow: 0px 0px 15px rgba(0, 255, 255, 0.5); /* Faint glow */
    }
    100% {
      box-shadow: 0px 0px 40px rgba(0, 255, 255, 1); /* Stronger glow */
    }
  }

  /* Hover Zoom Effect for Static Video Cards */
  .video-card:hover {
    transform: scale(1.05); /* Zoom effect on hover */
    box-shadow: 0 20px 40px rgba(0, 255, 180, 0.4), 0 0 30px #00ffcc; /* Glow effect */
  }

  /* Hover Zoom Effect on Videos in Slider */
  .video:hover video,
  .video-card:hover video {
    transform: scale(1.1) rotateX(1deg); /* Slight zoom and rotation */
    box-shadow: 0 12px 35px rgba(0, 255, 180, 0.4); /* Glow effect */
  }

  .play-btn {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(1);
    font-size: 48px;
    color: #00ffcc;
    background: rgba(0, 0, 0, 0.6);
    border: 2px solid #00ffcc;
    border-radius: 50%;
    padding: 10px 16px;
    cursor: pointer;
    z-index: 2;
    opacity: 0;
    transition: all 0.4s ease;
    box-shadow: 0 0 15px #00ffd5;
  }

  .video:hover .play-btn,
  .video-card:hover .play-btn {
    opacity: 1;
    animation: pulseGlow 1.2s infinite ease-in-out;
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

  .btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(0, 0, 0, 0.5);
    border: 2px solid #00ffcc;
    color: #00ffe1;
    font-size: 24px;
    border-radius: 50%;
    padding: 10px 14px;
    cursor: pointer;
    z-index: 10;
    opacity: 0.8;
    transition: all 0.3s ease;
  }

  .btn:hover {
    background-color: #00ffcc;
    color: black;
    transform: scale(1.1) translateY(-50%);
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
</style>

<!-- SCRIPT -->
<script>
  document.addEventListener("DOMContentLoaded", () => {
    const slider = document.querySelector(".video-slider");
    const wrappers = document.querySelectorAll(".video");
    const videos = document.querySelectorAll(".video video");
    const buttons = document.querySelectorAll(".video .play-btn");
    const total = wrappers.length;
    let index = 0;
    let autoSlideInterval;

    // Initially set the first video as active
    wrappers[0].classList.add("active");

    function updateSlider() {
      slider.style.transform = `translateX(-${index * 100}%)`;
      wrappers.forEach((wrapper, i) => {
        wrapper.classList.toggle("active", i === index);
      });
    }

    function moveSlider(dir) {
      index = (index + dir + total) % total;
      updateSlider();
    }

    function toggleVideo(btn, video) {
      if (video.paused) {
        video.play();
        btn.innerHTML = "&#10074;&#10074;";
      } else {
        video.pause();
        btn.innerHTML = "&#9658;";
      }
    }

    // Toggle video play/pause on slider
    buttons.forEach((btn, i) => {
      const video = videos[i];
      btn.addEventListener("click", () => toggleVideo(btn, video));
      video.addEventListener("play", () => (btn.innerHTML = "&#10074;&#10074;"));
      video.addEventListener("pause", () => (btn.innerHTML = "&#9658;"));
    });

    function startAutoSlideCheck() {
      clearInterval(autoSlideInterval);
      autoSlideInterval = setInterval(() => {
        const currentVideo = wrappers[index].querySelector("video");
        if (currentVideo.paused) {
          moveSlider(1);
        }
      }, 7000);
    }

    updateSlider();
    startAutoSlideCheck();

    // Fade-in animations for static video grid
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("show");
          }
        });
      },
      { threshold: 0.2 }
    );

    document.querySelectorAll(".video-card").forEach((card) => {
      observer.observe(card);
    });

    // Static video controls
    document.querySelectorAll(".video-card").forEach((card) => {
      const video = card.querySelector("video");
      const btn = card.querySelector(".play-btn");

      btn.addEventListener("click", () => toggleVideo(btn, video));
      video.addEventListener("play", () => (btn.innerHTML = "&#10074;&#10074;"));
      video.addEventListener("pause", () => (btn.innerHTML = "&#9658;"));
    });

    // Slider controls
    document.querySelector(".prev").addEventListener("click", () => moveSlider(-1));
    document.querySelector(".next").addEventListener("click", () => moveSlider(1));
  });
</script>
