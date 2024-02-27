---
layout: post
title: Google Analytics
subtitle: Free analytics for your website.
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

Here are couple screenshots for this blog data:  
![GA4 screen #1](https://github.com/vvzhukov/vvzhukov.github.io/blob/master/assets/img/GA_screenshot1.PNG?raw=true))    
![GA4 screen #2](https://github.com/vvzhukov/vvzhukov.github.io/blob/master/assets/img/GA_screenshot2.PNG?raw=true))   

## Setting up the Google Analytics Account  

### Create an Analytics account  
First thign you need to register and create the Analytics account.  
1. Go to https://analytics.google.com.  
2. Navigate to 'Admin', click Create, then select Account.
3. Configure the data-sharing settings to control which data you share.
4. Click Next to add the first property to the account.  

### Create a new Google Analytics 4 property  
1. Enter a name for the property ("My website") and select the reporting time zone and currency.  
2. Click Next. Select your industry category and business size.  
3. Click Next. Select how you intend to use Google Analytics.  
It will impact the set of default reports that are tailored based on the information you provide about how you intend to use Analytics.
4. Click Create and (if you are setting up a new account) accept the Analytics Terms of Service and the Data Processing Amendment.  
5. Continue to Add a data stream to start collecting data.  

### Add a data stream
1. Enter the URL of your primary website, e.g., "example.com", and a Stream name, e.g. "Example, Inc. (web stream)".  
2. You have the option to enable or disable enhanced measurement. Enhanced measurement automatically collects page views and other events. Once the data stream has been created, you can always go back and individually disable the enhanced measurement events you don’t want to collect.  
3. Click Create stream.  
   
## Setting up the web  
Here you have options. Either your CMS / site generator natively supports google analytics or you need to add some code directly to each page of your web.
In my case Beautiful Jecyll supports Google Analytics 4 so I have just modifyed the config *_config.yml*:  
```yml
# --- Web Analytics Section --- #

# Fill in your Google Analytics gtag.js ID to track your website using gtag
gtag: "ID1"

# Fill in your Google Analytics ID to track your website using Google Analytics
google_analytics: "ID2"

# Google Tag Manager ID
gtm: "ID3"
```
More details may be found at the Google instruction (1).
Here are some extra code blocks that will appear in your web source code.  
These scripts are used to collect the data described above.
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
Where ID1, ID2 and ID3 are gtag, Google Analytics ID, and Google Tag Manager ID.  

Lastly please give some time once you will setup everything. For me it took around 40 hours + to get first data.
Thank you for reading my blog, all the 100+ unique visitors!  

Topics to cover later:  
- Security / injections  
- Digital fingerprint / anonymisation (hello cookies :)  
- Data insights and conclusions  
- Search engine optimisation  

## References
This post is written under
1. [GA instructions](https://learn.deeplearning.ai/llmops/lesson/1/introduction)
2. [GA review](https://developers.google.com/analytics/learn/beginners#:~:text=Google%20Analytics%20collects%20data%20from,for%20your%20specific%20use%20cases.)  
P.S. Written with a help of GPT-3.5
