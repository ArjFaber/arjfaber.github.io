---
permalink: /
title: ""
author_profile: true
description: "Specializing in Reinforcement Learning, High-Performance Computing, and Robotics."
redirect_from: 
  - /about/
  - /about.html
---
<div id="funFact" class="fun-fact">🤔 Fun fact loading...</div>
<div class="project-card">
<h3> Welcome to my website!</h3>
<p style="text-align:center; margin-top: 20px;">
Hi, welcome to my website! Here you'll find most of my academic work to date. Jump to the CV below for a summary of my experience, and scroll down further for recent projects and previews of upcoming projects. Cheers, Arjan!
</p>
</div>
<div class="cv-toggle-container">
    <button class="cv-toggle-btn" onclick="toggleCV()">View CV</button>
</div>

<!-- Hidden PDF Viewer -->
<div class="cv-container" id="cvContainer" style="display: none;">
    <h2>My CV</h2>
    <iframe src="https://arjfaber.github.io/files/Arjan_Faber_CV_Recent.pdf" width="100%" height="600px">
        This browser does not support PDFs. Please download the PDF to view it:
        <a href="https://arjfaber.github.io/files/Arjan_Faber_CV_Recent.pdf">Download PDF</a>.
    </iframe>
</div>
<!-- Load YouTube IFrame API -->
<script src="https://www.youtube.com/iframe_api"></script>

## Featured Activity👇
<!-- Video Slider -->
<div class="slider-container">
    <div class="video-slider">
        <div class="video active">
                <iframe class="video-frame" id="player1" src="https://www.youtube.com/embed/k-XBWFp1FAQ?enablejsapi=1" allowfullscreen></iframe>
        </div>
        <div class="video">
                <iframe class="video-frame" id="player2" src="https://www.youtube.com/embed/X8vEKe2i508?enablejsapi=1" allowfullscreen></iframe>
        </div>
    </div>
    <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
    <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
</div>

<!-- Fun Fact Section -->

<!-- Intro Text -->

<!-- CV Toggle Button -->

## Upcoming Projects👇

<!-- Project Cards -->
<div class="project-card">
    <h3> Verifying the Upper Confidence Bound in Isabelle/HOL</h3>
    <p>This project formally verifies the Upper Confidence Bound (UCB) algorithm in Isabelle/HOL, focusing on its probabilistic guarantees and regret bounds. By leveraging advanced stochastic tools—such as martingales, concentration inequalities, and stopping times—it develops machine-checked proofs of UCB’s correctness. The work extends Isabelle/HOL’s probabilistic framework and explores verification of continuous-time bandit models via stochastic differential equations and Itô calculus. This research advances the formal verification of probabilistic algorithms in reinforcement learning.</p>
    <img src="https://arjfaber.github.io/files/UoE_Logo.png" alt="University of Edinburgh Logo">
  <button onclick="alert('Coming soon: A Project Towards Formal Verification of Continuous-Time Bandit Algorithms Using Stochastic Calculus!')">Learn More</button>
</div>

## My Strava Activities 🚴
<div class="slider-container">
    <div class="activity-slider">
        <!-- Activity Slides will be dynamically inserted here -->
    </div>
    <button class="btn prev" onclick="moveSlider(-1)">&#10094;</button>
    <button class="btn next" onclick="moveSlider(1)">&#10095;</button>
</div>

<!-- Leaflet.js CSS for map styling -->
<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />

<!-- Leaflet.js JS for map functionality -->
<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

<script>
fetch('/assets/strava-activities.json') // Adjust if path is different
  .then(response => response.json())
  .then(activities => {
    const container = document.querySelector('.activity-slider');
    activities.slice(0, 5).forEach((activity, index) => {
      const distanceKm = (activity.distance / 1000).toFixed(2);
      const timeMin = (activity.moving_time / 60).toFixed(1);
      const type = activity.type;
      const maxSpeed = (activity.max_speed * 3.6).toFixed(2); // Max speed in km/h

      const slide = document.createElement('div');
      slide.className = 'activity-slide';
      slide.innerHTML = `
        <div class="activity-card">
          <h3>${activity.name}</h3>
          <p>${distanceKm} km • ${timeMin} mins • ${type} • Max Speed: ${maxSpeed} km/h</p>
          <button onclick="window.open('https://www.strava.com/activities/${activity.id}', '_blank')">
            View on Strava
          </button>
          <div id="map-${activity.id}" class="map" style="height: 300px;"></div>
        </div>
      `;
      container.appendChild(slide);

      // Initialize map for this activity
      initializeMap(activity);
    });
  })
  .catch(error => {
    document.getElementById('strava-activities').innerHTML = '<p>Could not load activities.</p>';
    console.error('Strava load error:', error);
  });

function initializeMap(activity) {
  const mapElement = document.getElementById(`map-${activity.id}`);

  // Initialize the map and set the view to the start of the activity
  const map = L.map(mapElement).setView([activity.start_latlng[0], activity.start_latlng[1]], 13);

  // Add OpenStreetMap tile layer
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
  }).addTo(map);

  // Decode the polyline and plot the route
  const latlngs = decodePolyline(activity.map.summary_polyline);
  
  // Add polyline to the map
  L.polyline(latlngs, {color: 'blue'}).addTo(map);

  // Optionally, add a marker at the start
  L.marker([activity.start_latlng[0], activity.start_latlng[1]])
    .addTo(map)
    .bindPopup("Start of Activity");
}

function decodePolyline(encoded) {
  let points = [];
  let index = 0, lat = 0, lng = 0;
  while (index < encoded.length) {
    let shift = 0, result = 0;
    let byte;
    do {
      byte = encoded.charCodeAt(index++) - 63;
      result |= (byte & 0x1f) << shift;
      shift += 5;
    } while (byte >= 0x20);
    let dlat = ((result & 1) ? ~(result >> 1) : (result >> 1));
    lat += dlat;

    shift = 0;
    result = 0;
    do {
      byte = encoded.charCodeAt(index++) - 63;
      result |= (byte & 0x1f) << shift;
      shift += 5;
    } while (byte >= 0x20);
    let dlng = ((result & 1) ? ~(result >> 1) : (result >> 1));
    lng += dlng;

    points.push([lat / 1E5, lng / 1E5]);
  }
  return points;
}

let currentSlide = 0;

function moveSlider(direction) {
  const slides = document.querySelectorAll('.activity-slide');
  const totalSlides = slides.length;

  currentSlide = (currentSlide + direction + totalSlides) % totalSlides;
  slides.forEach((slide, index) => {
    slide.style.display = index === currentSlide ? 'block' : 'none';
  });
}

// Initially hide all slides except the first one
document.addEventListener('DOMContentLoaded', () => {
  const slides = document.querySelectorAll('.activity-slide');
  slides.forEach((slide, index) => {
    slide.style.display = index === 0 ? 'block' : 'none';
  });
});
</script>




<style>
    body.dark-mode {
        background-color: #121212;
        color: white;
    }

    .dark-mode .cv-container {
        background: #1e1e1e;
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

   .video.active {
    transform: scale(1.05);
    opacity: 1;
    box-shadow: 0px 0px 25px rgba(0, 255, 0, 0.7); /* Neon green active glow */
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

   .video-frame {
    width: 100%;
    height: 100%;
    border: none;
    border-radius: 10px;
    background-color: #222;  /* Dark background for iframe */
}

    .video-caption {
        text-align: center;
        font-size: 14px;
        margin-top: 10px;
        color: #555;
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

    .btn:hover {
        background-color: rgba(0, 0, 0, 0.8);
    }

    .cv-toggle-container {
        text-align: center;
        margin-top: 30px;
    }

    .cv-toggle-btn {
        padding: 10px 20px;
        font-size: 16px;
        border-radius: 8px;
        background-color: #007bff;
        color: white;
        border: none;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }

    .cv-toggle-btn:hover {
        background-color: #0056b3;
    }

    .cv-container {
        max-width: 90%;
        margin: 20px auto;
        padding: 20px;
        box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
        border-radius: 10px;
        background: #fff;
        display: none;
    }

    .cv-container h2 {
        text-align: center;
        margin-bottom: 15px;
    }

    .fun-fact {
        text-align: center;
        margin-top: 25px;
        font-style: italic;
        color: #666;
    }

    .project-card {
        max-width: 600px;
        margin: 20px auto;
        padding: 20px;
        border-radius: 12px;
        background: rgba(247, 247, 247, 0.85);;
        box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        transition: transform 0.2s;
        text-align: center;
    }

    .project-card:hover {
        transform: scale(1.02);
    }

    .project-card h3 {
        margin-bottom: 10px;
    }
</style>

<script>
    let index = 0;
    const slider = document.querySelector('.video-slider');
    const videoElements = document.querySelectorAll('.video');
    const totalVideos = videoElements.length;

    let autoSlideInterval;
    let isVideoPlaying = false;
    let ytPlayers = [];

    const references = [
    {
        title: "\"Why should I trust you?\" Explaining the predictions of any classifier",
        authors: "Ribeiro, Marco Tulio and Singh, Sameer and Guestrin, Carlos",
        year: 2016,
        journal: "Proceedings of the ACM SIGKDD International Conference on Knowledge Discovery and Data Mining",
        doi: "10.1145/2939672.2939778"
    },
    {
        title: "A cross-section across CVA",
        authors: "Chourdakis, Kyriakos and Epperlein, Eduardo and Jeannin, Marc and Mcewen, James",
        year: 2013,
        journal: "February"
    },
    {
        title: "A cross-section for CVA",
        authors: "Chourdakis, Kyriakos and Epperlin, Eduardo and Jeannin, Marc and Mcewen, James",
        year: 2013,
        journal: "Risk",
        pages: "20--21"
    },
    {
        title: "A deep learning approach for credit scoring using credit default swaps",
        authors: "Luo, Cuicui and Wu, Desheng and Wu, Dexiang",
        year: 2017,
        journal: "Engineering Applications of Artificial Intelligence",
        volume: 65,
        pages: "465--470",
        doi: "10.1016/j.engappai.2016.12.002",
        url: "https://doi.org/10.1016/j.engappai.2016.12.002"
    },
    {
        title: "A neural network approach for credit risk evaluation",
        authors: "Angelini, Eliana and di Tollo, Giacomo and Roli, Andrea",
        year: 2008,
        journal: "Quarterly Review of Economics and Finance",
        volume: 48,
        pages: "733--755",
        doi: "10.1016/j.qref.2007.04.001"
    },
    {
        title: "Advanced Introduction to Machine Learning, Vapnik-Chervonenkis Theory",
        authors: "Poczos, Barnabas",
        year: 2015,
        booktitle: "ML department Carnegie Mellon School of CS",
        doi: "10.1080/13602381.2017.1382264"
    },
    {
        title: "Bagging predictors",
        authors: "Breiman, Leo",
        year: 1994,
        journal: "Department of Statistics University of California",
        url: "https://www.stat.berkeley.edu/%7B~%7Dbreiman/bagging.pdf"
    },
    {
        title: "Bayesian Neural Networks and Tensorflow 2.0",
        authors: "Hasz, Brendan",
        year: 2019,
        url: "https://brendanhasz.github.io/2019/07/23/bayesian-density-net.html"
    },
    {
        title: "Binary code reranking method with weighted hamming distance",
        authors: "Fu, Haiyan and Kong, Xiangwei and Wang, Zhenfan",
        year: 2016,
        journal: "Multimedia Tools and Applications",
        pages: "1391--1408",
        volume: 75,
        doi: "10.1007/s11042-014-2087-y"
    },
    {
        title: "CDS Market Structure and Risk Flows: The Dutch Case",
        authors: "Levels, Anouk and van Stralen, Rene and Kroon Petrescu, Sinziana and van Lelyveld, Iman",
        year: 2018,
        journal: "SSRN Electronic Journal",
        doi: "10.2139/ssrn.3184307"
    },
    {
        title: "CDS spreads as an independent measure of credit risk",
        authors: "Kiesel, Florian and Spohnholtz, Jonathan",
        year: 2017,
        journal: "Journal of Risk Finance",
        volume: 18,
        pages: "122--144",
        doi: "10.1108/JRF-09-2016-0119"
    },
    {
        title: "Classification Algorithms and Regression Trees",
        authors: "Breiman, Leo and H. Friedman, Jerome and A. Olshen, Richard and J. Stone, Charles",
        year: 1984,
        booktitle: "Classification and Regression Trees",
        publisher: "Wadsworth International Group",
        address: "Belmont, CA",
        isbn: "978-0412048418"
    },
    {
        title: "Completing the Market: Generating Shadow CDS Spreads by Machine Learning",
        authors: "Hu, Nan and Li, Jian and Meyer-Cirkel, Alexis",
        year: 2019,
        journal: "IMF Working Papers",
        number: 292,
        volume: 19,
        doi: "10.5089/9781513524085.001"
    },
    {
        title: "Credit Default Swap spreads as viable substitutes for credit ratings",
        authors: "Flannery, Mark J and Houston, Joel F and Partnoy, Frank",
        year: 2010,
        booktitle: "The University of Pennsylvania Law Review",
        number: 7,
        pages: "2085--2123",
        volume: 158
    },
    {
        title: "Deep Sparse Rectifier Neural Networks",
        authors: "Glorot, Xavier and Bordes, Antoine and Bengio, Yoshua",
        year: 2011,
        journal: "AISTATS",
        doi: "10.1002/ecs2.1832"
    },
    {
        title: "Forecasting Credit Spreads: A Machine Learning Approach",
        authors: "Yuankang, Rick and Xiong, and Cai, Hui and Diego-Guerra, Israel and Lu, Yifei and Xu, Xinye and Yin, Yuan",
        year: 2019,
        keywords: "BART, LSTM, Random Forest, credit spread, prediction"
    },
    {
        title: "Hands-on Bayesian Neural Networks - a Tutorial for Deep Learning Users",
        authors: "Valentin Jospin, Laurent and Buntine, Wray and Boussaid, Farid and Laga, Hamid and Bennamoun, Mohammed",
        year: 2020,
        journal: "ACM Comput. Surv.",
        number: 1,
        pages: "1--35",
        volume: 1,
        arxivId: "2007.06823",
        keywords: "Approximate Bayesian methods, Bayesian Deep Learning, Bayesian methods"
    },
    {
        title: "How Neural Networks Learn from Experience",
        authors: "Hinton, Geoffrey",
        year: 1992,
        journal: "Scientific American",
        number: 3,
        pages: "144--151",
        volume: 267
    },
    {
        title: "Keeping neural networks simple by minimizing the description length of the weights",
        authors: "Hinton, Geoffrey E. and van Camp, Drew",
        year: 1993,
        pages: "5--13",
        isbn: "0897916115",
        doi: "10.1145/168304.168306"
    },
    {
        title: "Liquidity in Credit Default Swap Markets",
        authors: "Arakelyan, Armen and Serrano, Pedro",
        year: 2016,
        journal: "Journal of Multinational Financial Management",
        volume: "37-38",
        pages: "139--157",
        doi: "10.1016/j.mulfin.2016.09.001"
    },
    {
        title: "Liquidity risk in derivatives valuation: an improved credit proxy method",
        authors: "Sourabh, Sumit and Hofer, Markus and Kandhai, Drona",
        year: 2018,
        journal: "Quantitative Finance",
        volume: 18,
        pages: "467--481",
        doi: "10.1080/14697688.2017.1315166"
    },
    {
        title: "Neural Networks and Learning Machines",
        authors: "Haykin, Simon",
        year: 2009,
        edition: "3rd",
        publisher: "Prentice Hall International, Inc",
        address: "Hamilton, Ontario, Canada"
    },
    {
        title: "Random Decision Forests",
        authors: "Ho, Tin Kam",
        year: 1995,
        journal: "Proceedings of 3rd International Conference on Document Analysis and Recognition",
        pages: "278--282",
        isbn: "0818671289"
    },
    {
        title: "Random forests",
        authors: "Breiman, Leo",
        year: 2001,
        journal: "Machine Learning",
        pages: "5--32",
        volume: 45,
        isbn: "9783110941975",
        doi: "10.1201/9780367816377-11"
    },
    {
        title: "Random Search for Hyper-Parameter Optimization",
        authors: "James, Bergstra and Yoshua, Bengio",
        year: 2012,
        journal: "Journal of Machine Learning Research",
        volume: 13,
        number: 1,
        pages: "281--305"
    },
    {
        title: "Survey of Machine Learning in Credit Risk",
        authors: "Breeden, Joseph L",
        year: 2020,
        journal: "SSRN Electronic Journal",
        number: "May",
        doi: "10.2139/ssrn.3616342"
    },
    {
        title: "The Elements of Statistical Learning",
        authors: "Hastie, Trevor and Tibshirani, Robert and Friedman, Jerome",
        year: 2009,
        booktitle: "The Mathematical Intelligencer",
        volume: 27,
        number: 2,
        url: "http://www.springerlink.com/index/D7X7KX6772HQ2135.pdf",
        isbn: "9780387848570"
    },
    {
        title: "The Role of Neural Network Activation Functions",
        authors: "Parveen, Shahrukh and Qureshi, Mohsin",
        year: 2020,
        journal: "Machine Learning Research",
        pages: "47--52",
        volume: 35,
        doi: "10.1007/978-3-319-32008-1_7"
    },
    {
        title: "Using Machine Learning Models in Risk Management: Lessons from Basel III",
        authors: "Widdowson, David and Dombrowski, Alexandra",
        year: 2018,
        journal: "Financial Times",
        volume: 2
    },
    {
        title: "Understanding Deep Learning",
        authors: "LeCun, Yann and Bengio, Yoshua and Hinton, Geoffrey",
        year: 2015,
        journal: "Nature",
        volume: 521,
        pages: "436--444",
        doi: "10.1038/nature14539"
    },
    {
        title: "Understanding Machine Learning: From Theory to Algorithms",
        authors: "Shai Shalev-Shwartz and Shai Ben-David",
        year: 2014,
        publisher: "Cambridge University Press",
        isbn: "9781107057135"
    },
    {
        title: "A Guide to Convolutional Neural Networks for Computer Vision",
        authors: "Gupta, Laxmidhar and Agarwal, Amit and Gupta, M.",
        year: 2020,
        publisher: "Sage Publications"
    }
];

  

    function updateSlider() {
        slider.style.transform = `translateX(-${index * 100}%)`;

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
        }, 1600);
    }

    function autoSlide() {
        if (isVideoPlaying) return;

        const currentVideo = videoElements[index];
        currentVideo.classList.add('pop-animate');

        setTimeout(() => {
            currentVideo.classList.remove('pop-animate');
            index = (index + 1) % totalVideos;
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

    function toggleCV() {
        const cvContainer = document.getElementById('cvContainer');
        const button = document.querySelector('.cv-toggle-btn');
        if (cvContainer.style.display === 'none') {
            cvContainer.style.display = 'block';
            button.textContent = 'Hide CV';
        } else {
            cvContainer.style.display = 'none';
            button.textContent = 'View CV';
        }
    }

    function toggleDarkMode() {
        document.body.classList.toggle('dark-mode');
    }

   function showRandomFact() {
    let fact = references[Math.floor(Math.random() * references.length)];
    let factText = `${fact.title} (${fact.year}) - ${fact.authors}`;
    document.getElementById('funFact').textContent = "💡 " + factText;
  }

  setInterval(showRandomFact, 6000);

   

    // YouTube IFrame API callback
    function onYouTubeIframeAPIReady() {
        const iframes = document.querySelectorAll('.video-frame');
        iframes.forEach((iframe, i) => {
            ytPlayers[i] = new YT.Player(iframe, {
                events: {
                    'onStateChange': function (event) {
                        if (event.data === YT.PlayerState.PLAYING) {
                            isVideoPlaying = true;
                            stopAutoSlide();
                        } else if (
                            event.data === YT.PlayerState.PAUSED ||
                            event.data === YT.PlayerState.ENDED
                        ) {
                            isVideoPlaying = false;
                            startAutoSlide();
                        }
                    }
                }
            });
        });
    }

    document.addEventListener('DOMContentLoaded', function () {
        updateSlider();
        startAutoSlide();
        showRandomFact();
    });


</script>
