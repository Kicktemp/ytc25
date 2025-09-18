<p align="center">
  <a href="https://revealjs.com">
  <img src="https://hakim-static.s3.amazonaws.com/reveal-js/logo/v1/reveal-black-text-sticker.png" alt="reveal.js" width="500">
  </a>
  <br><br>
  <a href="https://github.com/hakimel/reveal.js/actions"><img src="https://github.com/hakimel/reveal.js/workflows/tests/badge.svg"></a>
  <a href="https://slides.com/"><img src="https://s3.amazonaws.com/static.slid.es/images/slides-github-banner-320x40.png?1" alt="Slides" width="160" height="20"></a>
</p>

Dieses Repository enthält eine Reveal.js-Präsentation, die ohne Gulp auskommt und sich direkt auf GitHub Pages betreiben lässt. Die Präsentation folgt dem Standard-Markup von reveal.js – alle Slides/Sections stehen direkt in der index.html (kein Markdown).

The framework comes with a powerful feature set including [nested slides](https://revealjs.com/vertical-slides/), [Markdown support](https://revealjs.com/markdown/), [Auto-Animate](https://revealjs.com/auto-animate/), [PDF export](https://revealjs.com/pdf-export/), [speaker notes](https://revealjs.com/speaker-view/), [LaTeX typesetting](https://revealjs.com/math/), [syntax highlighted code](https://revealjs.com/code/) and an [extensive API](https://revealjs.com/api/).

---

Want to create reveal.js presentation in a graphical editor? Try <https://slides.com>. It's made by the same people behind reveal.js.

---

### Sponsors
Hakim's open source work is supported by <a href="https://github.com/sponsors/hakimel">GitHub sponsors</a>. Special thanks to:
<div align="center">
  <table>
    <td align="center">
      <a href="https://workos.com/?utm_campaign=github_repo&utm_medium=referral&utm_content=revealjs&utm_source=github">
        <div>
          <img src="https://user-images.githubusercontent.com/629429/151508669-efb4c3b3-8fe3-45eb-8e47-e9510b5f0af1.svg" width="290" alt="WorkOS">
        </div>
        <b>Your app, enterprise-ready.</b>
        <div>
          <sub>Start selling to enterprise customers with just a few lines of code. Add Single Sign-On (and more) in minutes instead of months.</sub>
        </div>
      </a>
    </td>
  </table>
</div>

---

### Nutzung ohne Gulp
- Installation: npm install
- Entwicklung (mit Live-Reload): npm run dev (startet BrowserSync unter http://localhost:3000 und kompiliert SCSS im Watch-Modus)
- Nur Styles beobachten: npm run watch (kompiliert SCSS nach dist/)
- Lokaler Server ohne Live-Reload: npm start (baut CSS und startet http://localhost:8000)
- Deployment auf GitHub Pages: Push auf den Branch, den du bei Pages konfiguriert hast (z. B. main). CNAME liegt bereits bei.

Slides bearbeiten: Öffne index.html und editiere die <section>-Blöcke innerhalb von <div class="slides">. Drücke während der Präsentation die Taste "s", um die Sprecheransicht zu öffnen. Dort siehst du die aktuellen Folien, die nächste Folie, einen Timer und deine Notizen (via <aside class="notes"> in jeder Section).

Videos pro Folie:
- Klick zum Abspielen: In HTML ein Video-Tag mit data-clickplay einfügen.
  Beispiel:
  <video data-clickplay data-src="dist/assets/example.mp4" poster="dist/assets/poster.jpg" playsinline style="max-height:60vh"></video>
- Vollbild & Autoplay beim Betreten der Folie: Nutze eine eigene Section mit data-video-fullscreen und setze am Video data-autoplay. Autoplay funktioniert zuverlässig, wenn das Video muted ist (Browser-Policy). Optional kannst du data-state="video-fullscreen" setzen, um die Reveal-UI (Controls/Progress) auszublenden.
  Beispiel:
  <section data-video-fullscreen data-state="video-fullscreen">
    <video data-autoplay data-src="dist/assets/example.mp4" poster="dist/assets/poster.jpg" muted playsinline></video>
  </section>
- Verhalten:
  - Videos werden erst bei Bedarf geladen (lazy via data-src).
  - data-clickplay: Klick toggelt Play/Pause und blendet Controls ein/aus.
  - data-autoplay: Startet automatisch beim Folienwechsel, pausiert/setzt zurück beim Verlassen.
- Tipp: Lege deine MP4-Dateien unter dist/assets/ ab und nutze poster-Bilder für schnelle Voransicht.

Weitere Doku zu Reveal.js:
- 🚀 Installation: https://revealjs.com/installation
- 👀 Demo: https://revealjs.com/demo
- 📖 Markup/Markdown: https://revealjs.com/markup/
- 🖌 Editor: https://slides.com/
- 🎬 Videokurs (paid): https://revealjs.com/course

--- 
<div align="center">
  MIT licensed | Copyright © 2011-2024 Hakim El Hattab, https://hakim.se
</div>



#### Hintergrundvideo (echtes Fullscreen mit Reveal)
- Nutze eine Section mit data-background-video. Reveal rendert das Video als Slide-Hintergrund (fullscreen), ideal für randloses 16:9.
- Empfohlene Attribute:
  - data-background-video: URL zur Videodatei
  - data-background-color="#000": Hintergrundfarbe als Fallback
  - data-background-size="cover": skaliert auf ganzen Viewport
  - data-background-video-muted: für zuverlässiges Autoplay
  - data-background-video-loop: optional
  - data-state="video-fullscreen": optional zum Ausblenden der UI (Controls/Progress)
- Beispiel:
  <section 
    data-background-video="http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4"
    data-background-color="#000"
    data-background-size="cover"
    data-background-video-muted
    data-background-video-loop
    data-state="video-fullscreen"
  >
    <h2 style="color:#fff">Fullscreen Hintergrund‑Video</h2>
  </section>

#### Iframe als Folien‑Hintergrund (Fullscreen)
- Nutze data-background-iframe, um eine externe Seite als Hintergrund zu laden.
- Mit data-background-interactive erlaubst du Interaktionen (Scrollen, Klicken) im Iframe.
- Empfohlene Attribute:
  - data-background-iframe: URL zur Seite
  - data-background-color="#000": Fallback‑Hintergrund
  - data-background-interactive: erlaubt Interaktion (optional)
  - data-state="iframe-fullscreen": optional zum Setzen eines speziellen Slide‑Zustands
- Beispiel:
  <section 
    data-background-iframe="https://kickyoocasts.com/yoomasterclass/einfuehrung/intro-yoomasterclass"
    data-background-interactive
    data-background-color="#000"
    data-state="iframe-fullscreen"
  >
    <h2 style="color:#fff">Iframe</h2>
  </section>
- Hinweise:
  - Manche Seiten erlauben kein Einbetten (X-Frame-Options/CSP). In diesem Fall funktioniert der Iframe nicht.
  - Verwende nach Möglichkeit HTTPS‑URLs, besonders für GitHub Pages.
