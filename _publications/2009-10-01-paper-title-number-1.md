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

---

### 🚀 Featured Footage
<!-- your first video wall (unchanged) -->
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

---

<!-- horizontal slider with arrows + auto-scroll -->
<div class="slider-wrapper">
  <button class="arrow left">&#10094;</button>

  <div class="slider-horizontal" id="videoSlider">
    <div class="slider-track">
      <div class="video-tile" data-src="https://arjfaber.github.io/files/kuka1_.mp4">
        <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka1_.mp4"></video>
        <div class="video-meta">
          <h4>Finetuning Kuka controls (i)</h4>
          <p>Initial experiments for remote control</p>
        </div>
      </div>
      <div class="video-tile" data-src="https://arjfaber.github.io/files/kuka2_.mp4">
        <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka2_.mp4"></video>
        <div class="video-meta">
          <h4>Finetuning Kuka controls (ii)</h4>
          <p>Trajectory smoothing improvements</p>
        </div>
      </div>
      <div class="video-tile" data-src="https://arjfaber.github.io/files/kuka3_.mp4">
        <video muted loop playsinline preload="auto" src="https://arjfaber.github.io/files/kuka3_.mp4"></video>
        <div class="video-meta">
          <h4>Finetuning Kuka controls (iii)</h4>
          <p>Velocity and responsiveness test</p>
        </div>
      </div>
    </div>
  </div>

  <button class="arrow right">&#10095;</button>
</div>

<!-- Modal -->
<div class="video-modal" id="videoModal">
  <div class="modal-content">
    <video controls autoplay id="modalVideo"></video>
    <span class="close-btn">&times;</span>
  </div>
</div>

<!-- CSS & JS -->
<style>
/* --(same styles as before: .video-wall, .video-tile, .featured, .play-btn, .slider-wrapper, .arrow buttons, etc.)-- */
/* copy everything from previous message */
</style>

<script>
// Video Modal Logic
document.querySelectorAll(".video-tile").forEach(tile => {
  const btn = tile.querySelector(".play-btn");
  const video = tile.querySelector("video");
  const src = tile.dataset.src;

  if (btn) {
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
  }

  tile.addEventListener("click", () => {
    const modal = document.getElementById("videoModal");
    const modalVideo = document.getElementById("modalVideo");

    modalVideo.src = src;
    modal.style.display = "flex";
  });

  tile.addEventListener("keypress", (e) => {
    if (e.key === "Enter") {
      tile.click();
    }
  });
});

document.querySelector(".close-btn").addEventListener("click", () => {
  const modal = document.getElementById("videoModal");
  const modalVideo = document.getElementById("modalVideo");
  modal.style.display = "none";
  modalVideo.pause();
  modalVideo.src = "";
});

// Arrow Button Manual Scroll
const slider = document.getElementById('videoSlider');
document.querySelector('.left').addEventListener('click', () => {
  slider.scrollBy({ left: -300, behavior: 'smooth' });
});
document.querySelector('.right').addEventListener('click', () => {
  slider.scrollBy({ left: 300, behavior: 'smooth' });
});

// 🚀 Auto-Sliding Logic
let autoScroll;
function startAutoScroll() {
  autoScroll = setInterval(() => {
    if ((slider.scrollLeft + slider.offsetWidth) >= slider.scrollWidth) {
      slider.scrollTo({ left: 0, behavior: 'smooth' });
    } else {
      slider.scrollBy({ left: 2, behavior: 'smooth' });
    }
  }, 30); // speed of auto-slide (lower = faster)
}

function stopAutoScroll() {
  clearInterval(autoScroll);
}

slider.addEventListener('mouseenter', stopAutoScroll);
slider.addEventListener('mouseleave', startAutoScroll);

// Start auto-scrolling immediately
startAutoScroll();
</script>
