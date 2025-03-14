let index = 0;
const slider = document.querySelector('.video-slider');
const totalVideos = document.querySelectorAll('.video').length;

function updateSlider() {
    slider.style.transform = `translateX(-${index * 100}%)`;
}

function moveSlider(direction) {
    index = (index + direction + totalVideos) % totalVideos;
    updateSlider();
}

function autoSlide() {
    // Check if the current slide contains a video element
    const currentSlide = document.querySelectorAll('.video')[index];
    const videoElement = currentSlide.querySelector('video');
    
    // If the video is playing, do not auto slide
    if (videoElement && !videoElement.paused) {
        return; // Do not auto slide while the video is playing
    }

    // If the video is not playing, slide to the next one
    index = (index + 1) % totalVideos;
    updateSlider();
}

// Start auto-sliding immediately (on page load)
let autoSlideInterval = setInterval(autoSlide, 5000);

// Optional: Stop auto-slide when a video is playing
const videos = document.querySelectorAll('video');
videos.forEach(video => {
    video.addEventListener('play', () => clearInterval(autoSlideInterval));
    video.addEventListener('pause', () => {
        clearInterval(autoSlideInterval);
        autoSlideInterval = setInterval(autoSlide, 5000);
    });
    video.addEventListener('ended', () => {
        clearInterval(autoSlideInterval);
        autoSlideInterval = setInterval(autoSlide, 5000);
    });
});
