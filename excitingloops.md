---
layout: page
title: Some next destinations to explore...
---

A few recommended spots on the internet!

<style>
.departure-board {
  background: #ffffff;
  border-radius: 10px;
  overflow: hidden;
  max-width: 680px;
  margin: 2rem auto;
  box-shadow: 0 4px 20px rgba(0,0,0,0.1);
  font-family: 'Courier New', Courier, monospace;
  border: 1px solid #ddd;
}

.board-header {
  background: #1c3f6e;
  color: #ffffff;
  text-align: center;
  padding: 1rem 1.5rem;
  font-size: 1.2rem;
  letter-spacing: 0.35em;
  text-transform: uppercase;
  border-bottom: 3px solid #f5a623;
}

.board-col-headers {
  display: grid;
  grid-template-columns: 2fr 3fr;
  padding: 0.45rem 1.5rem;
  background: #f0f4f8;
  color: #888;
  font-size: 0.68rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  border-bottom: 1px solid #dde3ea;
}

.board-row {
  display: grid;
  grid-template-columns: 2fr 3fr;
  padding: 1rem 1.5rem;
  border-bottom: 1px solid #eef0f2;
  align-items: center;
  transition: background 0.15s;
}

.board-row:last-child {
  border-bottom: none;
}

.board-row:hover {
  background: #f7f9fb;
}

.dest a {
  color: #1c3f6e;
  text-decoration: none;
  font-size: 0.98rem;
  letter-spacing: 0.06em;
}

.dest a:hover {
  color: #f5a623;
}

.about {
  color: #555;
  font-size: 0.82rem;
  letter-spacing: 0.03em;
  line-height: 1.4;
}
</style>

<div class="departure-board">
  <div class="board-header">✈ &nbsp; DEPARTURES</div>
  <div class="board-col-headers">
    <span>DESTINATION</span>
    <span>ABOUT</span>
  </div>

  <div class="board-row">
    <div class="dest">
      <a href="https://tim-churchill.github.io/index.html" target="_blank">TIM'S BLOG</a>
    </div>
    <div class="about">My brother Tim's website hosting his creative and technical projects</div>
  </div>

  <div class="board-row">
    <div class="dest">
      <a href="https://byjtew.github.io/" target="_blank">BENJAMIN'S BLOG</a>
    </div>
    <div class="about">Visualizations, etc.</div>
  </div>



</div>
