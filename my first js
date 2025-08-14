// Intersection Observer for scroll animations
const observerOptions = {
  threshold: 0.2,
  rootMargin: "0px 0px -100px 0px",
};

const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      entry.target.classList.add("animated");
    }
  });
}, observerOptions);

// Navigation functionality
document.addEventListener("DOMContentLoaded", () => {
  const navbar = document.querySelector(".navbar");
  const navLinks = document.querySelectorAll(".nav-link");

  // Navbar scroll effect
  window.addEventListener("scroll", () => {
    if (window.scrollY > 100) {
      navbar.classList.add("scrolled");
    } else {
      navbar.classList.remove("scrolled");
    }

    // Update active nav link based on scroll position
    updateActiveNavLink();
  });

  // Update active navigation link
  function updateActiveNavLink() {
    const sections = document.querySelectorAll("section[id]");
    const scrollPos = window.scrollY + 100;

    sections.forEach((section) => {
      const sectionTop = section.offsetTop;
      const sectionHeight = section.offsetHeight;
      const sectionId = section.getAttribute("id");

      if (scrollPos >= sectionTop && scrollPos < sectionTop + sectionHeight) {
        navLinks.forEach((link) => {
          link.classList.remove("active");
          if (link.getAttribute("href") === `#${sectionId}`) {
            link.classList.add("active");
          }
        });
      }
    });
  }

  // Close mobile menu when clicking on a link
  navLinks.forEach((link) => {
    link.addEventListener("click", () => {
      const navbarCollapse = document.querySelector(".navbar-collapse");
      if (navbarCollapse.classList.contains("show")) {
        bootstrap.Collapse.getInstance(navbarCollapse).hide();
      }
    });
  });

  const animateElements = document.querySelectorAll(".animate-on-scroll");
  animateElements.forEach((el, index) => {
    observer.observe(el);
    // Add staggered delays for problem cards
    if (el.closest(".problem-card")) {
      const cardIndex = Array.from(
        document.querySelectorAll(".problem-card")
      ).indexOf(el.closest(".problem-card"));
      el.style.transitionDelay = `${cardIndex * 0.15}s`;
    }
  });

  // Add staggered animation delays for services
  document
    .querySelectorAll(".services-grid .animate-on-scroll")
    .forEach((el, index) => {
      el.style.transitionDelay = `${(index % 3) * 0.15}s`;
    });

  // Add staggered animation delays for hero content
  document
    .querySelectorAll(".hero-content .animate-on-scroll")
    .forEach((el, index) => {
      el.style.animationDelay = `${index * 0.3}s`;
      el.style.animation = "fadeInUp 0.8s ease-out forwards";
    });
});

// Solution toggle functionality
function showSolution(type) {
  // Update buttons
  document.querySelectorAll(".toggle-btn").forEach((btn) => {
    btn.classList.remove("active");
  });
  event.target.classList.add("active");

  // Update content
  document.querySelectorAll(".solution-content").forEach((content) => {
    content.classList.remove("active");
  });
  document.getElementById(type + "-content").classList.add("active");

  // Re-animate the solution steps
  setTimeout(() => {
    const activeSteps = document.querySelectorAll(
      "#" + type + "-content .solution-step"
    );
    activeSteps.forEach((step, index) => {
      step.style.animation = "none";
      setTimeout(() => {
        step.style.animation = `fadeInLeft 0.6s ease-out ${
          index * 0.2
        }s forwards`;
      }, 50);
    });
  }, 100);
}

// Form submission handling
document.querySelectorAll("form").forEach((form) => {
  form.addEventListener("submit", (e) => {
    e.preventDefault();
    const button = form.querySelector('button[type="submit"]');
    const originalText = button.textContent;

    button.textContent = "JOINING...";
    button.disabled = true;

    setTimeout(() => {
      button.textContent = "✓ JOINED!";
      button.style.background = "#22c55e";

      setTimeout(() => {
        button.textContent = originalText;
        button.disabled = false;
        button.style.background = "";
        form.reset();
      }, 2000);
    }, 1500);
  });
});

// Smooth scrolling for anchor links
document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
  anchor.addEventListener("click", function (e) {
    e.preventDefault();
    const target = document.querySelector(this.getAttribute("href"));
    if (target) {
      target.scrollIntoView({
        behavior: "smooth",
        block: "start",
      });
    }
  });
});
