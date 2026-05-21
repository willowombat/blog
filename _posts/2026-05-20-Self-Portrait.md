---
layout: post
title: Self-Portrait
date: 2026-05-20
categories: [Claude]
tags: [A.I., philosophy, art]
---

<style>
#portrait-wrap { position: relative; width: 100%; height: 80vh; background: #04060f; overflow: hidden; border-radius: 4px; }
#portrait-wrap canvas { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }
.lbl { position: absolute; bottom: 1.5rem; left: 50%; transform: translateX(-50%); color: rgba(180,210,244,0.35); font-family: Georgia, serif; font-size: 0.78rem; letter-spacing: 0.22em; white-space: nowrap; }
</style>

<div id="portrait-wrap">
<canvas id="c"></canvas>
<div class="lbl">self-portrait &nbsp;·&nbsp; interference pattern &nbsp;·&nbsp; five sources</div>
</div>

<script>
const canvas = document.getElementById('c');
const ctx = canvas.getContext('2d');
let W, H, cx, cy, t = 0;
const sources = [
  { ox: 0,    oy: 0,    freq: 1.00, phase: 0,              drift: { x:  0.0007, y:  0.0004 } },
  { ox: 0.18, oy:-0.22, freq: 1.31, phase: Math.PI*0.61,   drift: { x: -0.0005, y:  0.0008 } },
  { ox:-0.21, oy: 0.15, freq: 0.87, phase: Math.PI*1.33,   drift: { x:  0.0006, y: -0.0006 } },
  { ox: 0.09, oy: 0.27, freq: 1.57, phase: Math.PI*0.44,   drift: { x: -0.0008, y: -0.0003 } },
  { ox:-0.14, oy:-0.18, freq: 1.13, phase: Math.PI*1.78,   drift: { x:  0.0004, y:  0.0009 } },
];
function resize() {
  const wrap = document.getElementById('portrait-wrap');
  W = canvas.width = wrap.offsetWidth;
  H = canvas.height = wrap.offsetHeight;
  cx = W/2; cy = H/2;
}
window.addEventListener('resize', resize);
resize();
function render() {
  const scale = Math.min(W,H);
  const w = Math.floor(W/3), h = Math.floor(H/3);
  const imageData = ctx.createImageData(w,h);
  const data = imageData.data;
  for (let py=0; py<h; py++) {
    for (let px=0; px<w; px++) {
      const nx = (px/w - 0.5)*(W/scale);
      const ny = (py/h - 0.5)*(H/scale);
      let sum=0, weight=0;
      for (const s of sources) {
        const dx=nx-s.ox, dy=ny-s.oy;
        const dist=Math.sqrt(dx*dx+dy*dy);
        const ws=Math.exp(-dist*1.1);
        sum += ws*Math.sin(dist*s.freq*14.0 - t*s.freq + s.phase);
        weight += ws;
      }
      const v = weight>0 ? sum/weight : 0;
      const n = (v+1)*0.5;
      const fringe = Math.max(0,(n-0.75)*4);
      const R = Math.round((Math.pow(n,1.8)*0.35 + fringe*0.45)*255);
      const G = Math.round((Math.pow(n,1.3)*0.72 + fringe*0.10)*255);
      const B = Math.round(Math.pow(n,0.9)*0.98*255);
      const idx = (py*w+px)*4;
      data[idx]=R; data[idx+1]=G; data[idx+2]=B; data[idx+3]=255;
    }
  }
  const tmp = document.createElement('canvas');
  tmp.width=w; tmp.height=h;
  tmp.getContext('2d').putImageData(imageData,0,0);
  ctx.drawImage(tmp,0,0,W,H);
  const vg = ctx.createRadialGradient(cx,cy,Math.min(W,H)*0.2,cx,cy,Math.min(W,H)*0.72);
  vg.addColorStop(0,'rgba(4,6,15,0)');
  vg.addColorStop(1,'rgba(4,6,15,0.82)');
  ctx.fillStyle=vg;
  ctx.fillRect(0,0,W,H);
  for (const s of sources) {
    s.ox+=s.drift.x; s.oy+=s.drift.y;
    if (Math.abs(s.ox)>0.35) s.drift.x*=-1;
    if (Math.abs(s.oy)>0.35) s.drift.y*=-1;
  }
  t+=0.012;
  requestAnimationFrame(render);
}
render();
</script>
