<template>
    <div>
        <ThreeLogo />
        <div class="logo-container">
            <img src="/assets/media/Underthehood03.png" alt="Logo" class="logo" />
        </div>
        <div class="button-group">
            <button class="btn">Join Now</button>
            <button class="btn">Explore</button>
        </div>
    </div>
</template>

<script setup>
import ThreeLogo from '~/components/ThreeLogo.vue'

useHead({
  title: 'UNDERTHEHOOD® - Innovations in Aerospace, Automobiles, Construction & Development',
  meta: [
    { name: 'description', content: 'UNDERTHEHOOD® is a global leader in aerospace, automobiles, construction, and development with diverse sub-brands driving innovation and progress.' },
    { name: 'keywords', content: 'aerospace, automobiles, construction, development, innovations, sub-brands, technology, engineering, sustainability' },
    { name: 'author', content: 'UNDERTHEHOOD®' },

    // Open Graph / Social Sharing tags
    { property: 'og:title', content: 'UNDERTHEHOOD® - Leading the Future of Aerospace, Automobiles, and More' },
    { property: 'og:description', content: 'Explore how UNDERTHEHOOD® drives innovation in aerospace, automotive, construction, and more through its diverse sub-brands and companies.' },
    { property: 'og:image', content: '/assets/media/Underthehood.png' }, // Key image for sharing
    { property: 'og:url', content: 'https://underthehood.in' },
    { property: 'og:type', content: 'website' },

    // Twitter Card tags
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'twitter:title', content: 'UNDERTHEHOOD® - Global Leaders in Innovation' },
    { name: 'twitter:description', content: 'Aerospace, Automobiles, Construction, and Development – discover how UNDERTHEHOOD® pushes boundaries.' },
    { name: 'twitter:image', content: '/assets/media/Underthehood.png' },

    // Structured Data / JSON-LD
    {
      type: 'application/ld+json',
      json: {
        "@context": "https://schema.org",
        "@type": "Organization",
        "name": "UNDERTHEHOOD®",
        "url": "https://underthehood.in",
        "logo": "/assets/media/Underthehood.png",
        "description": "UNDERTHEHOOD® leads innovations in aerospace, automobiles, construction, and development with a vast range of sub-brands.",
        "address": {
          "@type": "PostalAddress",
          "addressLocality": "Bangalore",
          "addressCountry": "IN"
        }
      }
    }
  ],
  link: [
    { rel: 'canonical', href: 'https://underthehood.in' },
    { rel: 'icon', href: '/assets/media/Underthehood02.png' }, // Favicon
  ]
});
</script>

<style scoped>
.logo-container {
    position: absolute;
    top: 50%;
    /* Adjust this to position the logo above the buttons */
    left: 50%;
    transform: translateX(-50%);
    z-index: 2;
    /* Make sure it stays on top */
}

.logo {
    width: 200px;
    /* Adjust size as needed */
}

.button-group {
    font-family: "Inter", system-ui;
    position: absolute;
    bottom: 50px;
    left: 50%;
    transform: translateX(-50%);
}

.btn {
    margin: 0 10px;
    padding: 10px 20px;
    font-size: 14px;
    background-color: #111;
    color: #fefae0;
    font-weight: 600;
    border: none;
    cursor: pointer;
}
</style>