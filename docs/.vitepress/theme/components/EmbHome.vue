<script setup lang="ts">
import { ArrowRight, ScanSearch, ClipboardCheck, Workflow, House, ChartNoAxesCombined, ShieldCheck, Bug, Sparkles } from '@lucide/vue'
import { withBase } from 'vitepress'

const topics = [
  { number: '01', icon: ClipboardCheck, title: '夯实软硬件基础', en: 'CORE FOUNDATION', description: '从 C/C++、数据结构到数字电路与计算机组成，建立理解硬件与代码协作方式的底层视角。', tags: ['C/C++', '数据结构', '计算机组成'], color: 'copper' },
  { number: '02', icon: Workflow, title: '连接芯片与系统', en: 'SYSTEM BUILDING', description: '围绕单片机、ARM、RTOS 与嵌入式 Linux，记录从外设驱动到系统调试的完整实践。', tags: ['单片机', 'ARM', 'RTOS'], color: 'stone' },
  { number: '03', icon: ChartNoAxesCombined, title: '让设备稳定运行', en: 'RELIABLE DEVICES', description: '沉淀接口通信、性能分析与问题定位方法，把每次实验与项目迭代变成可复用的工程经验。', tags: ['驱动开发', '通信协议', '系统调试'], color: 'gold' },
]

const nodes = [
  { icon: ClipboardCheck, title: '硬件基础', detail: 'MCU · Digital', position: 'markup' },
  { icon: Bug, title: '驱动调试', detail: 'Driver · Debug', position: 'styles' },
  { icon: ScanSearch, title: '接口通信', detail: 'UART · SPI · I2C', position: 'logic' },
  { icon: Workflow, title: '系统构建', detail: 'RTOS · Linux', position: 'frameworks' },
]

const flowPaths = [
  'M110 96 H174 Q198 96 198 120 V161 Q198 175 218 175 H250',
  'M110 256 H174 Q198 256 198 232 V203 Q198 189 218 189 H250',
  'M310 175 H345 Q370 175 370 151 V120 Q370 96 394 96 H450',
  'M310 189 H345 Q370 189 370 213 V232 Q370 256 394 256 H450',
]
</script>

<template>
  <div class="web-home">
    <section class="web-hero" aria-labelledby="web-title">
      <div class="web-intro">
        <p class="web-eyebrow"><i /> 在这里，让代码靠近真实世界</p>
        <h1 id="web-title">走进嵌入式的世界<br><span>让每一行代码，点亮设备。</span></h1>
        <p class="web-description">从一个寄存器，到一套稳定运行的系统。<br>记录嵌入式开发的原理、工具与实践，让学习路径清晰可循。</p>
        <div class="web-actions">
          <a class="web-secondary" :href="withBase('/')"><House :size="17" />首页</a>
          <a class="web-primary" :href="withBase('/00.计算机背景知识/01.计算机软件常识')">开启学习之旅<ArrowRight :size="17" /></a>
        </div>
        <div class="web-notes"><span>覆盖有章</span><span>验证有据</span><span>交付有底</span></div>
      </div>

      <div class="web-visual" role="img" aria-label="嵌入式知识体系：以系统开发为核心，连接硬件基础、驱动调试、接口通信与系统构建。">
        <div class="visual-label"><span><i /> THE EMBEDDED JOURNEY</span><span>从原理到设备</span></div>
        <div class="web-orbit orbit-one" /><div class="web-orbit orbit-two" />
        <svg class="web-connectors" viewBox="0 0 560 350" fill="none" aria-hidden="true">
          <g v-for="(path, index) in flowPaths" :key="path">
            <path :d="path" />
            <path class="web-flow" :d="path" pathLength="100" :style="{ animationDelay: `${index * -0.8}s` }" />
          </g>
        </svg>
        <div v-for="node in nodes" :key="node.position" class="web-node" :class="node.position">
          <component :is="node.icon" :size="24" :stroke-width="1.6" />
          <strong>{{ node.title }}</strong><small>{{ node.detail }}</small>
        </div>
        <div class="web-core"><ShieldCheck :size="40" :stroke-width="1.4" /><strong>EMB</strong><small>硬件 · 软件 · 系统</small></div>
        <div class="visual-caption"><Sparkles :size="14" /> 让每一次实验，都更接近可靠</div>
      </div>
    </section>

    <div class="web-stack"><span>构建你的嵌入式视野</span><div><b>C/C++</b><i /><b>MCU</b><i /><b>ARM</b><i /><b>RTOS</b><i /><b>Linux</b></div><span>从原理出发 · 持续实践</span></div>

    <section class="web-learning" aria-labelledby="learning-title">
      <div class="learning-heading"><div><p>LEARN · BUILD · DEBUG</p><h2 id="learning-title">每一次实践，都让系统更进一步</h2></div><span>循序渐进，构建你的嵌入式知识体系</span></div>
      <div class="web-topics">
        <article v-for="topic in topics" :key="topic.number" class="web-topic" :class="topic.color">
          <div class="topic-top"><div class="topic-icon"><component :is="topic.icon" :size="23" :stroke-width="1.7" /></div><span>{{ topic.number }} / {{ topic.en }}</span></div>
          <h3>{{ topic.title }}</h3><p>{{ topic.description }}</p><div class="topic-tags"><span v-for="tag in topic.tags" :key="tag">{{ tag }}</span></div>
        </article>
      </div>
    </section>
    <p class="web-closing"><span />保持好奇，让每一次点亮都有收获<span /></p>
  </div>
</template>

<style scoped>
.web-home { --web-text: #18352a; --web-muted: #66766d; --web-accent: var(--web-primary); --web-line: #dce6df; --web-surface: rgb(255 255 255 / 82%); max-width: 1200px; margin: 0 auto; padding: clamp(24px, 4vh, 40px) 32px 16px; color: var(--web-text); line-height: 1.5; }
.web-hero { display: grid; grid-template-columns: 1fr 1fr; align-items: center; gap: 48px; padding: 8px 0 clamp(20px, 3vh, 28px); }
.web-eyebrow { display: flex; align-items: center; gap: 10px; margin: 0 0 10px; color: var(--web-accent); font-size: 12px; letter-spacing: 2px; }
.web-eyebrow i, .visual-label i { display: inline-block; width: 6px; height: 6px; border-radius: 50%; background: var(--web-primary); box-shadow: 0 0 0 4px rgb(22 101 52 / 13%); }
.web-intro h1 { margin: 0; padding: 0; text-align: left; font-size: clamp(30px, 3vw, 40px); line-height: 1.3; letter-spacing: 0; font-weight: 750; }
.web-intro h1::after { display: none; }
.web-intro h1 span { color: var(--web-accent); background: linear-gradient(105deg, #166534, #65a30d 56%, #4d7c0f); background-clip: text; -webkit-text-fill-color: transparent; }
.web-description { margin: 10px 0 14px; color: var(--web-muted); font-size: 15px; line-height: 1.6; }
.web-actions { display: flex; flex-wrap: wrap; gap: 12px; }
.web-actions a { display: inline-flex; align-items: center; justify-content: center; gap: 14px; padding: 10px 18px; border-radius: 8px; font-size: 13px; line-height: 24px; font-weight: 600; transition: transform .2s, box-shadow .2s; }
.web-actions a:hover { transform: translateY(-2px); box-shadow: 0 6px 16px rgb(22 101 52 / 18%); }
.web-actions a:focus-visible { outline: 3px solid var(--web-accent); outline-offset: 4px; }
.web-primary { background: linear-gradient(110deg, #166534, #4d7c0f); color: #fff; }
.web-secondary { border: 1px solid #b9cdbd; background: rgb(22 101 52 / 6%); color: var(--web-accent); }
.web-notes { display: flex; gap: 22px; margin-top: 12px; color: var(--web-muted); font-size: 11px; }
.web-notes span::before { content: '•'; margin-right: 7px; color: #8aaa74; }
.web-visual { position: relative; width: 100%; aspect-ratio: 560 / 350; background-image: radial-gradient(rgb(22 101 52 / 16%) .8px, transparent .8px); background-size: 18px 18px; }
.visual-label { position: absolute; inset: 0 0 auto; display: flex; justify-content: space-between; color: var(--web-muted); font-size: 9px; letter-spacing: 1.8px; }
.visual-label i { margin-right: 9px; }.visual-label > span:last-child { letter-spacing: 0; }
.web-connectors { position: absolute; inset: 0; width: 100%; height: 100%; stroke: #abc4ad; stroke-width: 1.2; }
.web-orbit { position: absolute; top: 52%; left: 50%; aspect-ratio: 1; transform: translate(-50%, -50%); border: 1px solid rgb(22 101 52 / 13%); border-radius: 50%; }
.orbit-one { width: 44%; }.orbit-two { width: 60%; }
.web-node { position: absolute; display: flex; width: 23%; height: 25%; flex-direction: column; align-items: center; justify-content: center; gap: 6px; border: 1px solid #b9cdbd; border-radius: 8px; background: var(--web-surface); color: #357a49; }
.web-node strong { color: var(--web-text); font-size: 12px; }.web-node small { color: var(--web-muted); font-size: 9px; }
.markup { left: 2%; top: 15%; }.styles { left: 2%; bottom: 14%; border-color: #c5d5c8; color: #4d7657; }.logic { right: 2%; top: 15%; border-color: #b9cdbd; color: #166534; }.frameworks { right: 2%; bottom: 14%; border-color: #b4c9ad; color: #4d7c0f; }
.web-core { position: absolute; top: 52%; left: 50%; display: flex; width: 24%; height: 37%; transform: translate(-50%, -50%); flex-direction: column; align-items: center; justify-content: center; gap: 10px; border: 1px solid #9fbe9f; border-radius: 8px; background: linear-gradient(140deg, #f5faf4, #eaf3e8); box-shadow: 0 0 0 7px rgb(255 255 255 / 50%), 0 12px 35px rgb(22 101 52 / 13%); color: #166534; }
.web-core strong { font-size: 20px; letter-spacing: 4px; font-weight: 500; }.web-core small { font-size: 9px; letter-spacing: 1px; }
.visual-caption { position: absolute; bottom: 0; display: flex; width: 100%; align-items: center; justify-content: center; gap: 7px; color: var(--web-muted); font-size: 10px; }
.web-stack { display: flex; align-items: center; justify-content: space-between; gap: 20px; padding: 12px 0; border-block: 1px solid var(--web-line); color: var(--web-muted); font-size: 11px; }
.web-stack > div { display: flex; align-items: center; gap: 25px; }.web-stack b { font-size: 16px; font-weight: 600; line-height: 24px; letter-spacing: 0; }.web-stack i { width: 3px; height: 3px; border-radius: 50%; background: #9ab991; }
.web-learning { padding-top: clamp(20px, 3vh, 28px); }.learning-heading { display: flex; align-items: flex-end; justify-content: space-between; gap: 16px; margin-bottom: 18px; }.learning-heading p { margin: 0 0 8px; color: var(--web-accent); font-size: 9px; letter-spacing: 2px; }.learning-heading h2 { margin: 0; padding: 0; border: 0; font-size: 20px; font-weight: 650; line-height: 1.5; letter-spacing: 0; }.learning-heading > span { color: var(--web-muted); font-size: 11px; }
.web-topics { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }.web-topic { --topic-color: #357a49; --topic-border: #b9cdbd; --topic-tint: rgb(22 101 52 / 8%); position: relative; overflow: hidden; padding: 20px; border: 1px solid var(--topic-border); border-radius: 8px; background: var(--web-surface); }.web-topic::before { position: absolute; top: 0; right: 18px; left: 18px; height: 2px; content: ''; background: linear-gradient(90deg, var(--topic-color), transparent); opacity: .65; }
.stone { --topic-color: #4d7657; --topic-border: #c5d5c8; --topic-tint: rgb(77 118 87 / 8%); }.gold { --topic-color: #4d7c0f; --topic-border: #b4c9ad; --topic-tint: rgb(77 124 15 / 9%); }
.topic-top { display: flex; align-items: center; gap: 12px; color: var(--topic-color); }.topic-top > span { font-size: 9px; line-height: 24px; letter-spacing: 1px; }.topic-icon { padding: 7px; border-radius: 8px; background: var(--topic-tint); }.web-topic h3 { margin: 8px 0 5px; font-size: 17px; font-weight: 650; }.web-topic p { margin: 0; color: var(--web-muted); font-size: 11px; line-height: 1.7; white-space: normal; }.topic-tags { display: flex; flex-wrap: wrap; gap: 7px; margin-top: 10px; }.topic-tags span { padding: 2px 8px; border-radius: 4px; background: var(--topic-tint); color: var(--topic-color); font-size: 10px; line-height: 16px; }
.web-closing { display: flex; align-items: center; justify-content: center; gap: 14px; margin: clamp(18px, 2.5vh, 24px) 0 0; color: var(--web-muted); font-size: 11px; }.web-closing span { width: 24px; height: 1px; background: var(--web-line); }
.web-flow { stroke: var(--web-accent); stroke-width: 2; stroke-linecap: round; stroke-dasharray: 5 95; animation: web-flow 4s linear infinite; }
.web-core::before { position: absolute; inset: -8px; content: ''; border: 1px solid rgb(22 101 52 / 34%); border-radius: 12px; animation: web-pulse 4s ease-out infinite; pointer-events: none; }
.web-core > svg { animation: web-float 5s ease-in-out infinite; }.visual-label i { animation: web-beacon 3s ease-in-out infinite; }
@keyframes web-flow { to { stroke-dashoffset: -100; } } @keyframes web-pulse { 0% { transform: scale(1); opacity: .65; } 85%, 100% { transform: scale(1.25); opacity: 0; } } @keyframes web-float { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-4px); } } @keyframes web-beacon { 0%, 100% { opacity: 1; } 50% { opacity: .4; } }
:global(.is-home-page .Layout:has(.web-home)) { background-image: radial-gradient(ellipse at 72% 18%, rgb(198 220 188 / 30%), transparent 46%), linear-gradient(150deg, rgb(244 248 240 / 86%), transparent 58%), linear-gradient(215deg, rgb(237 243 234 / 60%), transparent 58%); background-size: auto; }
:global(.VPHome:has(.web-home)) { margin-bottom: 0; }:global(.Layout:has(.web-home) .VPFooter) { padding: 16px 24px; }
:global(.dark .web-home) { --web-text: #e7f2e5; --web-muted: #b4c8ae; --web-accent: #a3d65c; --web-line: #3c543b; --web-surface: rgb(28 40 27 / 86%); }
:global(.dark .is-home-page .Layout:has(.web-home)), :global(.dark.is-home-page .Layout:has(.web-home)) { background-image: radial-gradient(ellipse at 70% 18%, rgb(77 124 15 / 25%), transparent 50%), linear-gradient(145deg, rgb(35 78 41 / 30%), transparent 65%); }
:global(.dark .web-home .web-intro h1 span) { background-image: linear-gradient(105deg, #a3d65c, #c2e88a 56%, #d8f2b5); }
:global(.dark .web-home .web-node) { color: #a3d65c; border-color: #6c9852; }
:global(.dark .web-home .web-core) { border-color: #6c9852; background: linear-gradient(140deg, #263d25, #1e321e); box-shadow: 0 0 0 7px rgb(163 214 92 / 9%); color: #c7ea91; }
:global(.dark .web-home .web-topic) { --topic-border: #4a6841; --topic-color: #b4df75; }:global(.dark .web-home .stone) { --topic-border: #52664d; --topic-color: #c2dbad; }:global(.dark .web-home .gold) { --topic-border: #50683e; --topic-color: #c7e58e; }
@media (max-width: 960px) { .web-hero { gap: 24px; }.web-stack > span:last-child, .learning-heading > span { display: none; }.web-stack > div { gap: 18px; }.web-core { gap: 5px; }.web-core svg { width: 32px; } }
@media (max-width: 700px) { .web-home { padding: 32px 24px 20px; }.web-hero { grid-template-columns: 1fr; gap: 36px; padding-bottom: 30px; }.web-intro { text-align: center; }.web-eyebrow, .web-actions, .web-notes { justify-content: center; }.web-intro h1 { text-align: center; font-size: clamp(27px, 6vw, 38px); line-height: 1.4; }.web-description { font-size: 13px; line-height: 1.8; }.web-visual { max-width: 520px; margin: auto; }.web-stack { flex-direction: column; gap: 12px; }.web-stack > div { gap: 12px; }.web-stack b { font-size: 12px; }.web-learning { padding-top: 30px; }.learning-heading h2 { font-size: 18px; }.web-topics { grid-template-columns: 1fr; gap: 14px; }.web-topic { padding: 20px; }.web-topic h3 { font-size: 15px; line-height: 22px; }.web-topic p { line-height: 1.6; }.web-closing { gap: 8px; font-size: 10px; }.web-closing span { width: 12px; }.web-node { gap: 4px; }.web-node > svg { width: 19px; height: 19px; flex-shrink: 0; }.web-node strong { font-size: 10px; line-height: 1.4; }.web-node small { font-size: 7px; line-height: 1.4; white-space: nowrap; }.web-core { gap: 4px; }.web-core > svg { width: 28px; height: 28px; }.web-core strong { font-size: 16px; letter-spacing: 2px; }.web-core small { font-size: 7px; letter-spacing: 0; } }
@media (min-width: 961px) and (max-height: 900px) { .web-home { padding-top: 16px; padding-bottom: 12px; }.web-hero { padding-bottom: 16px; }.web-visual { max-width: 408px; justify-self: end; }.web-intro h1 { font-size: 32px; }.web-eyebrow { margin-bottom: 8px; }.web-description { margin: 12px 0; line-height: 1.7; }.web-actions a { padding: 10px 16px; }.web-notes { margin-top: 8px; }.web-learning { padding-top: 16px; }.learning-heading { margin-bottom: 12px; }.learning-heading h2 { font-size: 18px; }.learning-heading p { margin-bottom: 5px; }.web-topic { padding: 16px; }.web-topic h3 { margin-top: 10px; margin-bottom: 6px; }.web-topic p { margin-bottom: 10px; }.web-closing { margin-top: 18px; }:global(.Layout:has(.web-home) .VPFooter) { padding: 12px 24px; } }
@media (prefers-reduced-motion: reduce) { .web-flow, .web-core::before, .web-core > svg, .visual-label i { animation: none; }.web-flow, .web-core::before { opacity: 0; }.web-actions a { transition: none; }.web-actions a:hover { transform: none; } }
@media (max-width: 700px) { .web-topic p { white-space: normal; } }
</style>
