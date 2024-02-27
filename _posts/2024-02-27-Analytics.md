---
layout: post
title: Google Analytics
subtitle: Free analytics for your web site.
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [Web, Analytics, JavaScript, Statistics]
comments: true
---

{: .box-note}

# Whys & Hows
Do you want to know:  
- who (device type, operating system, and browser type) is visiting your web site?  
- what pages are they visiting and how long (session statistics)?  
- where are they from (approximate geolocation)?  
  
Do you want it for free? Google Analytics is a good solution for that.  
What can you do with the data you will get?  
- Improve search engine optimization  
- Get marketing insights
- Play around with the analytics and research how does it work (my case)  
'Hi' to my single reader from Georgia :)  

## Setting up the web

  
```javascript

<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=[ID1]"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', '[ID1]');
</script>


  
  <!-- Google Tag Manager -->
  <script>
    (function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
      new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
      j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
      'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
    })(window,document,'script','dataLayer','[ID2]');
  </script>
  <!-- End Google Tag Manager -->


  
<!-- Google Analytics -->
<script>
  (function (i, s, o, g, r, a, m) {
    i['GoogleAnalyticsObject'] = r; i[r] = i[r] || function () {
      (i[r].q = i[r].q || []).push(arguments)
    }, i[r].l = 1 * new Date(); a = s.createElement(o),
      m = s.getElementsByTagName(o)[0]; a.async = 1; a.src = g; m.parentNode.insertBefore(a, m)
  })(window, document, 'script', 'https://www.google-analytics.com/analytics.js', 'ga');
  ga('create', '[ID3]', 'auto');
  ga('send', 'pageview');
</script>
<!-- End Google Analytics -->
```
Where ID1, ID2 and ID3 are 

## References
This post is written as an open notebook after the completion of the OpenAI Course 'LLMOps':
[GA instructions]([https://learn.deeplearning.ai/llmops/lesson/1/introduction](https://support.google.com/analytics/answer/9304153)

P.S. Written with a help of GPT-3.5
