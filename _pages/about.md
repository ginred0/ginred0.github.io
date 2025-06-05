---
layout: about
title: About
permalink: /
subtitle: SUSTech, Shenzhen, China

profile:
  align: right
  image: g&gary.jpg
  image_circular: false # crops the image to make it circular
  more_info: >

selected_papers: false # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: false # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false
  scrollable: true # adds a vertical scroll bar if there are more than 3 blog posts
  limit: 3 # leave blank to include all the blog posts
---

I am a PhD candidate in the Department of Computer Science and Engineering at <a href="https://www.sustech.edu.cn/">Southern University of Science and Technology</a> in Shenzhen, China, under the supervision of Associate Professor <a href="https://cse.sustech.edu.cn/faculty/~weixt/">Xuetao Wei</a>. Before my PhD, I worked as a research assistant,  under the supervision of Professor <a href="https://jqyu.me/en/index.html">James Jianqiao Yu</a>. Both mentors have provided invaluable guidance and support throughout my academic journey.

<hr class="divider" />

My research interests lie at the intersection of computer science, economics, and sociology, focusing on fairness in AI- and human-involved systems—including data markets, federated learning, and human–AI collaboration. I investigate fairness-related issues arising from human factors such as heterogeneous data resources, behaviors, cognitive capacities, and demographic characteristics. My academic goal is to empower AI systems to be trustworthy, efficient, and fair in practice.

<hr class="divider" />

Artificial Intelligence (AI) has become an integral part of our daily lives, providing efficient, large-scale support for decision-making across various domains such as medical diagnoses, financial risk assessments, and sentencing judgments. Given its close relation to human well-being, it is imperative to examine whether AI acts as an ethical assistant. For example, will AI assistance exacerbate information inequality among diverse human demographics—particularly those with varying expertise due to unequal access to advanced knowledge? Could AI systems propagate subtle biases and mislead humans into making unfair decisions?



During my PhD studies, I actively engaged in examining and solving fairness-related issues in systems involving both humans and AI. These issues include:



- **Data Markets:** Budget-constrained participants seek to purchase datasets that most effectively enhance fairness in AI model training, yet the capacity of marketplace datasets to improve fairness before purchase remains unknown.

- **Collaborative Model Training:**
  - There is a trade-off between allocating model performance fairly among participants and achieving optimal overall performance.
  - Fair performance allocation may sacrifice the benefits of advantaged participants, prompting them to withdraw and potentially causing the system to be unstable.
  - Multi-fairness-aware local model aggregation mechanisms can be stealthily bypassed by malicious participants, undermining the collaboratively trained global model's fairness without reducing accuracy.

- **Human–AI Collaboration:** Experts' utility gains from AI assistance are sensitive to individual factors such as cognitive capacity, resulting in unequal benefits among heterogeneous experts.


I expect to graduate in July 2025 and am currently seeking postdoctoral positions to continue my research. You can find my CV [here]({{site.url}}/assets/pdf/Jiashi_GAO_CV.pdf).
<hr class="divider" />
<!-- PDF Viewer Section -->
<div id="pdf-viewer-container">
    <button id="prev" onclick="goToPreviousPage()">Prev</button>
    <canvas id="pdf-canvas"></canvas>
    <button id="next" onclick="goToNextPage()">Next</button>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.10.377/pdf.min.js"></script>
<script>
  const url = '{{site.url}}/assets/pdf/rs.pdf';  // Replace with your PDF file's URL
  let currentPage = 1;
  let pdfDoc = null;

  const canvas = document.getElementById('pdf-canvas');
  const ctx = canvas.getContext('2d');

  // Load PDF
  function renderPage(pageNum) {
    pdfDoc.getPage(pageNum).then(function(page) {
      const viewport = page.getViewport({ scale: 1 });
      canvas.height = viewport.height;
      canvas.width = viewport.width;

      page.render({ canvasContext: ctx, viewport: viewport });
    });
  }

  function loadPDF() {
    pdfjsLib.getDocument(url).promise.then(function(pdf) {
      pdfDoc = pdf;
      renderPage(currentPage);
    });
  }

  function goToNextPage() {
    if (currentPage < pdfDoc.numPages) {
      currentPage++;
      renderPage(currentPage);
    }
  }

  function goToPreviousPage() {
    if (currentPage > 1) {
      currentPage--;
      renderPage(currentPage);
    }
  }

  loadPDF();
</script>

<style>
  #pdf-viewer-container {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 20px;
    max-width: 800px; /* Match the width of the content above */
    width: 100%;
    margin-left: auto;
    margin-right: auto;
  }
  #pdf-canvas {
    border: 1px solid #ccc;
  }
  button {
      background: linear-gradient(145deg, #6c7ae0, #4b58c9);  /* Gradient background */
      border: none;                                      /* Remove border */
      color: white;                                      /* White text for contrast */
      padding: 12px 24px;                                /* Larger padding for better click area */
      font-size: 16px;                                   /* Slightly larger font for visibility */
      font-weight: bold;                                 /* Bold text for emphasis */
      border-radius: 25px;                               /* Rounded corners */
      cursor: pointer;                                  /* Pointer cursor on hover */
      transition: all 0.3s ease;                         /* Smooth transition for hover effects */
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);          /* Subtle shadow for depth */
      margin: 0 10px;
  }
  
  button:hover {
      background: linear-gradient(145deg, #4b58c9, #6c7ae0);  /* Inverted gradient on hover */
      box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);              /* Darker shadow on hover */
      transform: translateY(-2px);                           /* Slight lift effect on hover */
  }
  
  button:focus {
      outline: none;                                        /* Remove focus outline */
      box-shadow: 0 0 5px rgba(110, 128, 255, 0.5);           /* Soft focus glow */
  }
</style>
