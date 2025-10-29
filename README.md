# single-page-application-2
&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;

  &lt;meta charset=&quot;UTF-8&quot; /&gt;
  &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1&quot; /&gt;
  &lt;title&gt;Naan Mudhalvan Info SPA&lt;/title&gt;
  &lt;style&gt;
    @import
url(&#39;https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&amp;display
=swap&#39;);

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: &#39;Poppins&#39;, sans-serif;
      background: url(&#39;https://images.unsplash.com/photo-1499673610122-
01c7122c5dcb?auto=format&amp;fit=crop&amp;w=1350&amp;q=80&#39;) no-repeat center center
fixed;
      background-size: cover;
      color: #fff;
      height: 100vh;
      overflow: hidden;
    }

    /* Transparent overlay moving background */
    .overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 200%;

      height: 200%;
      background: rgba(0, 0, 0, 0.4);
      animation: moveOverlay 20s linear infinite;
      pointer-events: none;
    }

    @keyframes moveOverlay {
      0% { transform: translate(0, 0); }
      50% { transform: translate(-25%, -25%); }
      100% { transform: translate(0, 0); }
    }

    header {
      position: relative;
      z-index: 10;
      padding: 20px 40px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: rgba(0, 0, 0, 0.6);
      backdrop-filter: blur(5px);
    }
    header h1 {
      font-size: 2rem;
    }

    nav a {
      color: #ffffffcc;
      margin-left: 20px;

      text-decoration: none;
      font-weight: 600;
      transition: color 0.3s;
      font-size: 1.1rem;
    }
    nav a:hover, nav a.active {
      color:palevioletred
    }

    main {
      position: relative;
      z-index: 10;
      max-width: 800px;
      margin: 40px auto;
      background: rgba(0,0,0,0.5);
      border: 3px solid pink;
      border-radius: 12px;
      padding: 30px;
      backdrop-filter: blur(10px);
      min-height: 300px;
      transition: opacity 0.4s ease;
    }

    img {
      width: 100%;
      border-radius: 8px;
      margin: 20px 0;
      border: 2px solid #fff;
    }

    h2 {
      margin-top: 0;
      color: #ffd700;
    }

    p, li {
      line-height: 1.6;
    }

    ul {
      list-style: disc inside;
      margin-top: 10px;
    }
  &lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
  &lt;div class=&quot;overlay&quot;&gt;&lt;/div&gt;

  &lt;header&gt;
    &lt;h1&gt;Naan Mudhalvan&lt;/h1&gt;
    &lt;nav&gt;
      &lt;a href=&quot;#home&quot; id=&quot;nav-home&quot; class=&quot;active&quot;&gt;Home&lt;/a&gt;
      &lt;a href=&quot;#about&quot; id=&quot;nav-about&quot;&gt;About&lt;/a&gt;
      &lt;a href=&quot;#gallery&quot; id=&quot;nav-gallery&quot;&gt;Gallery&lt;/a&gt;
    &lt;/nav&gt;
  &lt;/header&gt;

  &lt;main id=&quot;content&quot;&gt;

    &lt;!-- Dynamic content loads here --&gt;
  &lt;/main&gt;

  &lt;script&gt;
    const routes = {
      home: `
        &lt;h2&gt;Welcome to Naan Mudhalvan&lt;/h2&gt;
        &lt;p&gt;The &lt;strong&gt;Naan Mudhalvan&lt;/strong&gt; scheme is a flagship initiative
launched by the Tamil Nadu government to empower youth by identifying and
nurturing their talents, offering skill training, career guidance, and supporting
them to face competitive exams and opportunities.&lt;/p&gt;
        &lt;img src=&quot;${&quot;C:\Users\ADMIN\Pictures\image 2.png&quot;}
      `,
      about: `
        &lt;h2&gt;About the Scheme&lt;/h2&gt;
        &lt;p&gt;Under &lt;strong&gt;Naan Mudhalvan&lt;/strong&gt;, students receive:&lt;/p&gt;
        &lt;ul&gt;
          &lt;li&gt;Skill development training (soft skills, technical skills)&lt;/li&gt;
          &lt;li&gt;Guidance on higher education and career pathways&lt;/li&gt;
          &lt;li&gt;Support for competitive exams (coaching, study materials)&lt;/li&gt;
          &lt;li&gt;Language training (English, regional, etc.)&lt;/li&gt;
        &lt;/ul&gt;
        &lt;img src=&quot;${&quot;C:\Users\ADMIN\Pictures\images.jpg&quot;}
      `,
      gallery: `
        &lt;h2&gt;Gallery&lt;/h2&gt;
        &lt;p&gt;Here are some images related to Naan Mudhalvan:&lt;/p&gt;
        &lt;img src=&quot;${&quot;https://i.ytimg.com/vi/Zs4xCWHvD3U/maxresdefault.jpg&quot;}&quot;
alt=&quot;Event Image 1&quot;&gt;
        &lt;img src=&quot;${&quot;https://i.ytimg.com/vi/9wCvJXGjnNY/maxresdefault.jpg&quot;}&quot;
alt=&quot;Event Image 2&quot;&gt;

        &lt;img src=&quot;${&quot;https://i.ytimg.com/vi/vOuCs5r1G3A/maxresdefault.jpg&quot;}&quot;
alt=&quot;Event Image 3&quot;&gt;
        &lt;img src=&quot;${&quot;https://i.ytimg.com/vi/1015/600/350.jpg&quot;}&quot; alt=&quot;Related
Image&quot;&gt;
      `
    };

    const contentDiv = document.getElementById(&#39;content&#39;);
    const navLinks = document.querySelectorAll(&#39;nav a&#39;);

    function setActiveLink(hash) {
      navLinks.forEach(link =&gt; {
        if (link.getAttribute(&#39;href&#39;) === hash) {
          link.classList.add(&#39;active&#39;);
        } else {
          link.classList.remove(&#39;active&#39;);
        }
      });
    }

    function loadContent() {
      const hash = window.location.hash || &#39;#home&#39;;
      const routeName = hash.substring(1);

      contentDiv.style.opacity = 0;
      setTimeout(() =&gt; {
        if (routes[routeName]) {
          contentDiv.innerHTML = routes[routeName];
        } else {

          contentDiv.innerHTML = `&lt;h2&gt;404 - Page Not Found&lt;/h2&gt;&lt;p&gt;Sorry, no
content found.&lt;/p&gt;`;
        }
        setActiveLink(hash);
        contentDiv.style.opacity = 1;
      }, 300);
    }

    window.addEventListener(&#39;hashchange&#39;, loadContent);
    loadContent(); // initial load
  &lt;/script&gt;

&lt;/body&gt;
&lt;/html&gt;
