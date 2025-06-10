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

My research interests lie at the intersection of computer science, economics, and sociology, focusing on fairness in AI- and human-involved systems—including data markets, federated learning, and human–AI collaboration. I investigate fairness-related issues arising from human factors such as heterogeneous data resources, behaviors, cognitive capacities, and demographic characteristics. My academic goal is to empower AI systems to be trustworthy, efficient, and fair in practice. Please refer to my research statement details in the PDF available at ({{site.url}}/assets/pdf/Jiashi_GAO_Research_statement.pdf).

<hr class="divider" />
I expect to graduate in July 2025 and am currently seeking postdoctoral positions to continue my research. You can find my CV [here]({{site.url}}/assets/pdf/Jiashi_GAO_CV.pdf).


<hr class="divider" />
<!-- PDF Viewer Section -->
<div id="pdf-viewer-container">
    <button class="pdf-nav-btn" id="prev" onclick="goToPreviousPage()">Prev</button>
    <canvas id="pdf-canvas"></canvas>
    <button class="pdf-nav-btn" id="next" onclick="goToNextPage()">Next</button>
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
    max-width: 600px; /* Match the width of the content above */
    width: 80%;
    margin-left: auto;
    margin-right: auto;
  }
  #pdf-canvas {
    border: 1px solid #ccc;
  }
  /* Styling for the Prev and Next buttons */
  .pdf-nav-btn {
      background-color: rgba(155, 41, 184, 0.8);  /* Magenta color with 80% opacity */
      color: white;                               /* White text */
      padding: 12px 24px;                         /* Padding for the buttons */
      font-size: 16px;                            /* Larger font size */
      font-weight: bold;                          /* Bold text */
      border-radius: 25px;                        /* Rounded corners */
      border: none;                               /* Remove border */
      cursor: pointer;                           /* Pointer cursor on hover */
      transition: all 0.3s ease;                  /* Smooth transition for hover effect */
      margin: 0 10px;                             /* Spacing between the buttons */
  }
  
  .pdf-nav-btn:hover {
      background-color: rgba(155, 41, 184, 1);    /* Magenta color without transparency on hover */
      transform: scale(1.05);                      /* Slightly increases the size on hover */
  }
  
  .pdf-nav-btn:focus {
      outline: none;                               /* Removes the default focus outline */
      box-shadow: 0 0 5px rgba(155, 41, 184, 0.5);  /* Soft magenta glow when focused */
  }
</style>
