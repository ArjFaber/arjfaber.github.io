---
title: "Verification of the Upper Confidence Bound Algorithm in Isabelle/HOL"
collection: publications
category: manuscripts
permalink: /publication/masterdissertation
excerpt: 'This paper formally verifies the upper confidence bound algorithm in Isabelle/HOL.'
date: 2025-01-10
venue: 'University of Edinburgh (School of Informatics)'
paperurl: 'https://arjfaber.github.io/files/Faber, Arjan S2619954.pdf'
slidesurl: ''
citation: 'Faber A. (2025)'
---
This project formally verifies the Upper Confidence Bound (UCB) algorithm in
Isabelle/Higher-order Logic (HOL), focusing on its probabilistic guarantees and regret
bounds. By leveraging advanced stochastic tools such as martingales, concentration in-
equalities, and stopping times. This project develops machine-checked proofs of UCB’s
correctness. The work extends Isabelle/HOL’s probabilistic framework and explores
verification of continuous-time bandit models via stochastic differential equations and
Itˆo calculus. This research advances the formal verification of probabilistic algorithms
in reinforcement learning.

<style>
  b<style>
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
    background: linear-gradient(145deg, #00ffcc, #000);  /* Dark futuristic gradient */
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
    }
   .video-slide video {
  width: 100%;
  height: 100%;
  object-fit: contain; /* or 'cover' if you want full filling */
}
.video-slide {
  flex: 0 0 100%; /* Take up 100% of the slider container */
  max-width: 100%;
  height: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}
   .video-slide.active {
    transform: scale(1.05);
    opacity: 1;
    box-shadow: 0px 0px 25px rgba(0, 255, 0, 0.7); /* Neon green active glow */
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

/* Styling for the glowing dots */
.dot-indicator-container {
  display: flex;
  justify-content: center;
  gap: 15px;
  margin-top: 10px;
}

.dot-indicator {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background-color: #00ffcc; /* Default color */
  opacity: 0.5;
  transition: opacity 0.3s ease, transform 0.3s ease;
}

/* Each dot gets a different active glow */
.dot-indicator:nth-child(1).active {
  opacity: 1;
  transform: scale(1.3);
  box-shadow: 0 0 8px rgba(255, 0, 0, 0.7); /* Red glow for the first video */
}

.dot-indicator:nth-child(2).active {
  opacity: 1;
  transform: scale(1.3);
  box-shadow: 0 0 8px rgba(0, 255, 0, 0.7); /* Green glow for the second video */
}

.dot-indicator:nth-child(3).active {
  opacity: 1;
  transform: scale(1.3);
  box-shadow: 0 0 8px rgba(0, 0, 255, 0.7); /* Blue glow for the third video */
}

/* Default active dot glow (if needed for any other use) */
.dot-indicator.active {
  box-shadow: 0 0 8px rgba(0, 255, 200, 0.7); /* Default glow */
}


</style>

<script>
  let index = 0;
const slider = document.querySelector('.video-slider');
const videoElements = document.querySelectorAll('.video-slide');
const totalVideos = videoElements.length;
const dots = document.querySelectorAll('.dot-indicator'); // Glowing dots

let autoSlideInterval;
let isVideoPlaying = false; // Flag to check if video is playing

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
    isVideoPlaying = true; // Set flag when video is playing
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
  isVideoPlaying = false; // Reset flag when modal is closed
});

document.addEventListener("keydown", (e) => {
  if (e.key === "Escape" && modal.style.display === "flex") {
    modal.style.display = "none";
    modalVideo.pause();
    modalVideo.src = "";
    isVideoPlaying = false; // Reset flag when modal is closed
  }
});

function updateSlider() {
  slider.style.transform = `translateX(-${index * 100}%)`;
  videoElements.forEach((vid, i) => {
    vid.classList.toggle('active', i === index);
  });
  // Update dot indicators
  dots.forEach((dot, i) => {
    dot.classList.toggle('active', i === index);
  });
  rangeInput.value = index;
}

function moveSlider(direction) {
  if (isVideoPlaying) return; // Prevent sliding when a video is playing

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
  if (isVideoPlaying) return; // Prevent auto-sliding when a video is playing

  const currentVideo = videoElements[index];
  currentVideo.classList.add('pop-animate');

  setTimeout(() => {
    currentVideo.classList.remove('pop-animate');
    index = (index + 1) % totalVideos;
    updateSlider();
  }, 1600);
}

const rangeInput = document.getElementById('video-slider');

rangeInput.addEventListener('input', (e) => {
  index = parseInt(e.target.value);
  updateSlider();
  stopAutoSlide(); // Stop auto-slide when user interacts
});

rangeInput.addEventListener('input', (e) => {
  index = parseInt(e.target.value);
  updateSlider();
  stopAutoSlide(); // Stop immediately when user interacts

  // Restart auto-slide after 6 seconds of inactivity
  setTimeout(() => {
    startAutoSlide();
  }, 6000);
});

document.addEventListener('DOMContentLoaded', function () {
  updateSlider();
  startAutoSlide();
});

document.querySelectorAll('.video-slide').forEach(slide => {
  const video = slide.querySelector('video');
  const playBtn = slide.querySelector('.play-btn');

  playBtn.addEventListener('click', (e) => {
    e.stopPropagation(); // Prevent triggering the slide click
    if (video.paused) {
      video.play();
      playBtn.innerHTML = "&#10074;&#10074;"; // Pause icon
      isVideoPlaying = true; // Set flag when video is playing
    } else {
      video.pause();
      playBtn.innerHTML = "&#9658;"; // Play icon
      isVideoPlaying = false; // Set flag when video is paused
    }
  });

  slide.addEventListener('click', () => {
    let src = video.getAttribute('src') || video.currentSrc;
    if (src) {
      modalVideo.src = src;
      modal.style.display = "flex";
      modalVideo.play();
      isVideoPlaying = true; // Set flag when video is playing in modal
    } else {
      console.warn('No video source found for modal');
    }
  });

  slide.addEventListener('keypress', (e) => {
    if (e.key === "Enter") {
      slide.click();
    }
  });

  // Video ended event to reset flag
  video.addEventListener('ended', () => {
    isVideoPlaying = false; // Reset flag when video ends
    startAutoSlide(); // Restart auto-slide after video ends
  });
});
</script>
