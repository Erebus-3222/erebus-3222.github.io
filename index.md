---
layout: default
title: Home
---

# Home
{: .no_toc }

Welcome to Erebus Scripts Documentation.
{: .fs-6 .fw-300 }

<button class="btn js-toggle-dark-mode">Toggle Day/Night Modes</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = 'Night Mode';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = 'Day Mode';
  }
});
</script>