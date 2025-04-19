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

<div class="slider-container" id="sliderContainer" style="visibility: hidden;">
  <div class="video-slider" id="videoSlider">
    <div class="video active">
      <video width="640" height="360" muted loop playsinline preload="auto" id="video1">
        <source src="https://arjfaber.github.io/files/Harmony_Data_Collection.mp4" type="video/mp4">
        Your browser does not support the video tag.
      </video>
      <button class="play-btn" onclick="toggleVideo(this)">&#9658;</button> <!-- play icon -->
    </div>
    <div class="video">
      <video width="640" height="360" muted loop playsinline preload="auto" id="video2">
        <source src="https://arjfaber.github.io/files/Harmony_ML_Module_Final-2.mp4" type="video/mp4">
        Your browser does not support the video tag.
      </video>
    <button class="play-btn" onclick="toggleVideo(this)">&#9658;</button> <!-- play icon -->
    </div>
  </div>
  <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
  <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
</div>


## Kuka Robot Recovery Documentation
<div class="video-grid">
  <div class="video-card">
    <video preload="auto">
      <source src="https://arjfaber.github.io/files/kuka1_.mp4" type="video/mp4">
    </video>
  </div>
  <div class="video-card">
    <video preload="auto">
      <source src="https://arjfaber.github.io/files/kuka2_.mp4" type="video/mp4">
    </video>
  </div>
  <div class="video-card">
    <video preload="auto">
      <source src="https://arjfaber.github.io/files/kuka3_.mp4" type="video/mp4">
    </video>
  </div>
</div>



[Kuka setup tutorial](https://github.com/ArjFaber/Harmony_UT/wiki)

![KUKA Robot Image](https://arjfaber.github.io/files/UT.png)
<style>
  .video-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 20px;
    padding: 20px;
  }

  .video-card {
    opacity: 0;
    transform: translateY(40px);
    transition: all 0.8s ease-out;
  }

  .video-card.show {
    opacity: 1;
    transform: translateY(0);
  }

  .video-card video {
    width: 100%;
    border-radius: 12px;
    box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .video-card video:hover {
    transform: scale(1.05);
    box-shadow: 0 12px 32px rgba(0, 0, 0, 0.4);
  }
  .slider-container {
    max-width: 100%;
    overflow: hidden;
    aspect-ratio: 16 / 9;
    position: relative;
    margin: 40px auto 20px auto;
    border-radius: 15px;
    background-color: rgba(0, 0, 0, 0); /* Ibis white */
    box-shadow: 0px 0px 20px rgba(0, 255, 0, 0.3);
    border: 2px solid #00ff00; /* Green LED border */
    display: flex;
    justify-content: center;
    align-items: center;
    visibility: hidden; /* Hide initially */
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
  .video.active {
    transform: scale(1.05);
    opacity: 1;
    box-shadow: 0px 0px 25px rgba(0, 255, 0, 0.7); /* Neon green active glow */
  }
.play-btn {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 36px;
  color: white;
  background-color: rgba(0, 0, 0, 0.6);
  border-radius: 50%;
  padding: 20px;
  cursor: pointer;
  z-index: 2;
  opacity: 0; /* Hidden by default */
  pointer-events: none;
  transition: opacity 0.5s ease;
}
  .play-btn:hover {
    background-color: rgba(0, 0, 0, 0.9);
  }
  .video.playing .play-btn {
    display: block; /* Hide button when video is playing */
  }
  @keyframes popOutIn {
        0% { transform: scale(1.05); }
        50% { transform: scale(1.15); }
        100% { transform: scale(1.05); }
    }
    .video.pop-animate {
        animation: popOutIn 1.5s ease;
        z-index: 2;
    }
  .video.paused {
    animation: popOutIn 2s ease;
    z-index: 2;
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
    z-index: 3;
  }
  .prev { left: 5px; }
  .next { right: 5px; }
</style>

<script>
let index = 0;
const slider = document.querySelector('.video-slider');
const wrappers = document.querySelectorAll('.video');
const videos = document.querySelectorAll('.video video');
const total = wrappers.length;

let autoSlideInterval; // Declare a global variable for the auto slide interval

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

function startAutoSlideCheck() {
  clearInterval(autoSlideInterval); // Clear any existing interval

  // Start the auto-slide interval
  autoSlideInterval = setInterval(() => {
    const currentVideo = wrappers[index].querySelector('video');
    const currentWrapper = wrappers[index];

    if (currentVideo.paused && !currentWrapper.classList.contains('paused')) {
      currentWrapper.classList.add('paused');

      setTimeout(() => {
        // If still paused after 1.6 seconds, auto-slide to next video
        if (currentVideo.paused) {
          currentWrapper.classList.remove('paused');
          moveSlider(1);
        } else {
          currentWrapper.classList.remove('paused');
        }
      }, 1600); // 1.6 second grace period
    }
  }, 5000); // Check every 5 seconds
}

// Toggle play/pause from button
function toggleVideo(button) {
  const wrapper = button.closest('.video');
  const video = wrapper.querySelector('video');

  if (video.paused) {
    video.play();
    wrapper.classList.add('playing');
    button.innerHTML = '&#10074;&#10074;'; // Pause icon
    startAutoSlideCheck(); // Restart auto slide check when video is played
  } else {
    video.pause();
    wrapper.classList.remove('playing');
    button.innerHTML = '&#9658;'; // Play icon
    startAutoSlideCheck(); // Restart auto slide check when video is paused
  }
}

// Auto-hide play/pause button after 5 seconds of inactivity
function setupAutoHideControls() {
  wrappers.forEach((wrapper) => {
    const button = wrapper.querySelector('.play-btn');
    let hideTimeout;

    const showControls = () => {
      button.style.opacity = '1';
      button.style.pointerEvents = 'auto';

      clearTimeout(hideTimeout);
      hideTimeout = setTimeout(() => {
        button.style.opacity = '0';
        button.style.pointerEvents = 'none';
      }, 5000); // 5 seconds
    };

    wrapper.addEventListener('mousemove', showControls);
    wrapper.addEventListener('mouseenter', showControls);
    wrapper.addEventListener('mouseleave', () => {
      button.style.opacity = '0';
      button.style.pointerEvents = 'none';
    });

    // Initialize controls hidden
    button.style.opacity = '0';
    button.style.pointerEvents = 'none';
  });
}

window.onload = () => {
  document.getElementById('sliderContainer').style.visibility = 'visible';
  updateSlider();
  startAutoSlideCheck();
  setupAutoHideControls(); // 🧩 Add this call
};

// Ensure buttons update with video state
videos.forEach((video, i) => {
  const btn = wrappers[i].querySelector('.play-btn');

  video.addEventListener('play', () => {
    wrappers[i].classList.add('playing');
    wrappers[i].classList.remove('paused');
    btn.innerHTML = '&#10074;&#10074;';
  });

  video.addEventListener('pause', () => {
    wrappers[i].classList.remove('playing');
    wrappers[i].classList.add('paused');
    btn.innerHTML = '&#9658;';
    startAutoSlideCheck(); // Restart auto slide check when paused
  });
});

  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('show');
      }
    });
  }, {
    threshold: 0.2
  });

  window.addEventListener('DOMContentLoaded', () => {
  document.querySelectorAll('.video-card').forEach(card => {
    observer.observe(card);
  });
});
</script>


