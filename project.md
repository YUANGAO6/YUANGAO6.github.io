---
layout: landing
title: Panoramic Treadmill + AI Metabolism Precision Intervention System
header: false
full_width: true
article_header:
  type: overlay
  theme: dark
  align: center
  height: 100vh
  background_image:
    src: /assets/images/01hero_banner.png
  actions:
    - text: "Explore the Innovation"
      type: info
      url: "/project.html#hero-3"  # Points to "The Innovation Model" section
    - text: "Watch Our Story"
      type: success
      url: "/project.html#hero-2"  # Points to "Our Story" section

data:
  sections:
    - title: "Why HexTech?"
      excerpt: "Addressing the Global Teen Obesity Crisis with Technology & Care."
      theme: light
      background_image:
        src: /assets/images/01hero_banner.png
      children:
        - title: "Panoramic Immersion"
          excerpt: "5G + 3D Holography recreates snowfields & plateaus for engaging workouts."
          image:
            src: /assets/images/07connection.png
        - title: "AI Metabolism"
          excerpt: "Real-time breath acetone analysis for precision fat/sugar metabolism monitoring."
          image:
            src: /assets/images/05AI_detect.png
        - title: "Knee Protection"
          excerpt: "Water-surrounded design reduces knee impact by 40% via buoyancy."
          image:
            src: /assets/images/04water.png

    - title: "Our Story (Brand & Mission)"
      excerpt: "Driven by love, guided by science. The journey of Team HexTech."
      theme: dark
      background_color: "#2c3e50"
      background_image:
        src: /assets/images/06Prototype.jpg
      children:
        - title: "The Origin: A Promise to Family"
          excerpt: "It started with a family check-up. The doctor warned that my sister's weight was affecting her bone development. We realized traditional treadmills were boring and unsafe for her. Inspired by the Prader-Willi Syndrome charity project, we decided to build a 'warm' machine that understands the body."
          image:
            src: /assets/images/02origin.png
        - title: "Team HexTech"
          excerpt: "We are 'HexTech' - implying that technology (Tech) can be as magical as a spell (Hex). Composed of 3 high school students and 1 advisor, we combine mechanical design, coding, and marketing to make health accessible."
          image:
            src: /assets/images/03team.jpg
        - title: "Our Mission"
          excerpt: "To transform teen obesity intervention from a 'painful task' into an 'engaging journey'. We aim to build a closed-loop system connecting Exercise, Diet, and Metabolism."
          image:
            src: /assets/images/03team.jpg

    - title: "The Innovation Model"
      excerpt: "A fusion of mechanical engineering, AI algorithms, and immersive tech."
      theme: light
      background_image:
        src: /assets/images/01hero_banner.png
      children:
        - title: "Water-Surrounded<br>Structure"
          excerpt: "Safety First: Our unique water base utilizes buoyancy to reduce knee pressure by 40% and uses water resistance for efficient muscle training. A game-changer for obese teens."
          image:
            src: /assets/images/04water.png
        - title: "AI Metabolic<br>Monitoring"
          excerpt: "Precision Data: Integrating breath acetone spectral analysis to distinguish between sugar and lipid metabolism types, generating personalized training plans."
          image:
            src: /assets/images/05AI_detect.png
        - title: "5G Holographic<br>Interaction"
          excerpt: "Social Motivation: 5G enables real-time projection of friends or competitors into the cabin. No more lonely running—compete and encourage each other."
          image:
            src: /assets/images/07connection.png
        - title: "Prototype<br>Validation"
          excerpt: "Feasibility Proven: We built a functional LEGO EV3 prototype to verify the deformable cabin structure, motor control, and safety sensor logic. It works!"
          image:
            src: /assets/images/06Prototype.jpg

    - title: "Future & Impact"
      excerpt: "From a high school project to a global health solution."
      theme: dark
      background_image:
        src: /assets/images/01hero_banner.png
      children:
        - title: "Market Potential"
          excerpt: "Targeting the $28.7B home fitness market. Core users: Middle-to-high income parents & semi-professional runners. Business model includes hardware sales + $15/mo subscription."
        - title: "Social Impact"
          excerpt: "Helping the 30M obese teens in China (and globally) reduce chronic disease risks (diabetes, fatty liver) and regain confidence. Reducing long-term healthcare burdens."
        - title: "Next Steps"
          excerpt: "Seeking $1.5M seed funding for product mass production (molds), marketing (pilot programs), and R&D (algorithm optimization)."

    - title: "Connect with HexTech"
      excerpt: "Join us in building a healthier future."
      theme: light
      background_image:
        src: /assets/images/01hero_banner.png
      actions:
        - text: "Watch Demo Video"
          type: outline-primary
          url: "https://www.bilibili.com/video/BV1GJ411x7h7/?share_source=copy_web&vd_source=88426f80852072222a96e4e076dc3967"
        - text: "Download Whitepaper"
          type: outline-info
          url: "/intro/HexTech_Whitepaper.pdf"
---



<script>
document.addEventListener("DOMContentLoaded", function() {
  const targets = document.querySelectorAll('.layout--landing .hero__content > *, .layout--landing .grid--container .cell');

  // Configuration
  const fadeStart = 0.95; // Start fading in almost immediately
  const fadeEnd = 0.75;   // Fully visible quickly (at 75% viewport height)
  const fadeOutStart = -0.1; // Start fading out ONLY after it passes the top edge
  
  function updateScroll() {
    const windowHeight = window.innerHeight;
    
    targets.forEach(el => {
      const rect = el.getBoundingClientRect();
      const elementTop = rect.top;
      const elementHeight = rect.height;
      const elementCenter = elementTop + elementHeight / 2;
      
      // Calculate progress based on viewport position
      // 1.0 = bottom of screen, 0.0 = top of screen
      let progress = elementTop / windowHeight;
      
      let opacity = 0;
      let translateY = 0;
      let scale = 0.95;
      let blur = 0;

      if (progress > fadeStart) {
        // Below fade start point: Invisible
        opacity = 0;
        translateY = 60;
        scale = 0.95;
        blur = 10;
      } else if (progress <= fadeStart && progress >= fadeEnd) {
        // Entering phase: Fade In + Slide Up
        // Map progress (fadeStart -> fadeEnd) to (0 -> 1)
        const t = (fadeStart - progress) / (fadeStart - fadeEnd);
        opacity = t;
        translateY = 60 * (1 - t);
        scale = 0.95 + (0.05 * t);
        blur = 10 * (1 - t);
      } else if (progress < fadeEnd && progress > fadeOutStart) {
        // Center phase: Fully visible
        opacity = 1;
        translateY = 0;
        scale = 1;
        blur = 0;
      } else if (progress <= fadeOutStart) {
        // Leaving phase: Fade Out + Slide Up (Apple Style)
        // Map progress (fadeOutStart -> -0.5) to (1 -> 0)
        // This means it will fade out completely when the element is 50% above the viewport top.
        const fadeOutEnd = -0.5;
        const t = (progress - fadeOutEnd) / (fadeOutStart - fadeOutEnd);
        // Clamp t between 0 and 1
        const safeT = Math.max(0, Math.min(1, t));
        
        opacity = safeT;
        translateY = -60 * (1 - safeT); // Continue moving up a bit more
        scale = 1 - (0.1 * (1 - safeT)); // Scale down slightly more
        blur = 10 * (1 - safeT);
      }

      // Apply styles
      el.style.opacity = opacity;
      el.style.transform = `translate3d(0, ${translateY}px, 0) scale(${scale})`;
      el.style.filter = `blur(${blur}px)`;
    });
    
    requestAnimationFrame(updateScroll);
  }

  // Start loop
  updateScroll();
});
</script>

<style>
  /* Base styles for scroll targets */
  .layout--landing .hero__content > *, 
  .layout--landing .grid--container .cell {
    /* Transitions are handled by JS frame-by-frame for scroll-bound effect */
    /* We add a tiny transition to smooth out JS jitter if any */
    transition: opacity 0.1s linear, transform 0.1s linear, filter 0.1s linear;
    will-change: opacity, transform, filter;
  }
</style>

<style>
  /* Force the first section to be full screen */
  #hero-1 {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-top: 0 !important; /* Remove default padding if any */
    margin-top: -60px; /* Counteract default header margin if needed, tune this */
  }
  
  /* Remove any default margin from the page content container */
  .layout--landing {
    margin-top: 0 !important;
  }
</style>

<style>
  /* --- Style Tweaks --- */

  /* 1. Add Scroll Indicator to the Article Header */
  /* Ensure wrapper is relative so indicator is positioned correctly */
  .article__header--overlay {
    position: relative;
  }

  .article__header--overlay::after {
    content: "Scroll Down";
    position: absolute;
    bottom: 30px;
    left: 50%;
    transform: translateX(-50%);
    color: #fff;
    font-size: 0.8rem;
    opacity: 0.8;
    animation: bounce 2s infinite;
    z-index: 10;
  }

  @keyframes bounce {
    0%, 20%, 50%, 80%, 100% { transform: translateX(-50%) translateY(0); }
    40% { transform: translateX(-50%) translateY(-10px); }
    60% { transform: translateX(-50%) translateY(-5px); }
  }

  /* 2. Remove default background from light sections and DISABLE mask */
  .hero--light {
    background-image: none !important;
    background-color: #ffffff !important;
  }
  
  /* Explicitly prevent any mask on light sections */
  .hero--light::before {
    content: none !important;
    display: none !important;
  }

  /* 3. Dark Overlay for Dark Sections (including Article Header) */
  /* Mask applied to the .hero--dark element, NOT the wrapper */
  .hero--dark {
    position: relative; /* Ensure ::before is contained */
  }

  .hero--dark::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.4); /* Reduced opacity per user feedback */
    z-index: 1;
  }

  /* Ensure content is above the mask */
  .article__header--overlay .hero__content,
  .hero--dark .hero__content, 
  .hero--dark .grid--container {
    position: relative;
    z-index: 2;
  }
  
  /* Ensure text is white and readable on dark sections */
  .article__header--overlay h1,
  .article__header--overlay p,
  .hero--dark h3, 
  .hero--dark p, 
  .hero--dark .hero__content {
    color: #ffffff !important;
    text-shadow: 0 2px 10px rgba(0,0,0,0.5);
  }

  /* Base styles for scroll targets */
  .layout--landing .hero__content > *, 
  .layout--landing .grid--container .cell {
    transition: opacity 0.1s linear, transform 0.1s linear, filter 0.1s linear;
    will-change: opacity, transform, filter;
  }
  
  /* Justify text for paragraphs */
   .hero__content p,
   .grid--container p {
     text-align: justify;
     /* Enable hyphenation to fix large gaps (Rivers of White) */
     -webkit-hyphens: auto;
     -ms-hyphens: auto;
     hyphens: auto;
   }

   /* 4. Enforce uniform image size and cropping */
    .layout--landing .grid--container .cell img {
      width: 100%;
      height: 250px; /* Fixed height for uniformity */
      object-fit: cover; /* Crop to fill without distortion */
      border-radius: 4px; /* Optional: Slight rounding for polish */
    }

    /* 5. Align images horizontally (bottom alignment) */
    /* Force Grid to use Flexbox with stretch alignment */
    .layout--landing .grid {
      display: flex !important;
      flex-wrap: wrap !important;
      align-items: stretch !important;
    }

    /* Make the cell a flex container */
    .layout--landing .grid .cell {
      display: flex !important;
      flex-direction: column !important;
      height: auto !important; /* Let flex stretch height */
      float: none !important; /* Disable floats if any */
    }
    
    /* Push the image to the bottom using auto margin */
    .layout--landing .grid .cell > .mx-auto {
      margin-top: auto !important;
      width: 100%;
    }
    
    /* Ensure text container doesn't have excess margin interfering */
    .layout--landing .grid .cell > .mb-5 {
      margin-bottom: 1rem !important; /* Standardize gap */
    }
    
    /* 6. Style for Section Subtitles (Excerpts) */
    /* Target the excerpt paragraph specifically to center and enlarge it */
    .hero__content > .mb-5 > p {
      text-align: center !important; /* Override the justify set above */
      font-size: 1.5rem; /* Make it larger */
      line-height: 1.4;
      max-width: 900px; /* Prevent it from getting too wide on large screens */
      margin-left: auto;
      margin-right: auto;
    }

    /* 7. Enable Smooth Scrolling for Anchor Links */
    html {
      scroll-behavior: smooth;
    }
  </style>

<script>
  // Inject Logo into the Article Header
  document.addEventListener("DOMContentLoaded", function() {
    const headerOverlay = document.querySelector('.article__header--overlay');
    if (headerOverlay) {
      const logoContainer = document.createElement('div');
      logoContainer.className = 'custom-logo';
      logoContainer.innerHTML = `
        <a href="/project.html" style="display: block;">
          <img src="/assets/images/08logo.png" alt="HexTech Logo" style="width: 120px; height: auto; display: block;">
        </a>
      `;
      
      // Style the container
      logoContainer.style.position = 'absolute';
      logoContainer.style.top = '30px';
      logoContainer.style.left = '30px';
      logoContainer.style.zIndex = '100';
      
      headerOverlay.appendChild(logoContainer);
    }
  });
</script>
