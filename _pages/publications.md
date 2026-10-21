---
layout: page
permalink: /publications/
title: publications
nav: true
nav_order: 1
---

<!-- _pages/publications.md -->

<div class="publications">

{% bibliography %}

</div>

<script>
  // Award buttons: link straight to the first link in the award text (bib `award` field),
  // or show as a plain label when there is none, and sit after the paper's link buttons.
  // Cloning drops the theme's expand-on-click handler; runs on `load` so the theme's
  // DOMContentLoaded setup has already happened.
  window.addEventListener("load", () => {
    document.querySelectorAll(".publications a.award.btn").forEach((button) => {
      const panel = button.closest("li")?.querySelector(".award.hidden");
      const awardLink = panel?.querySelector("a[href]");
      const replacement = button.cloneNode(true);
      if (awardLink) {
        replacement.href = awardLink.href;
        replacement.target = "_blank";
        replacement.rel = "external nofollow noopener";
      } else {
        replacement.removeAttribute("role");
        replacement.classList.add("award-label");
      }
      button.parentElement.append(replacement);
      button.remove();
    });
  });
</script>
