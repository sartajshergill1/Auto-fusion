<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Auto Fusion Sales</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #fff;
      color: #333;
      overflow-x: hidden;
      cursor: none;
    }

    .sidebar {
      width: 250px;
      background-color: #b00020;
      height: 100vh;
      padding: 30px 20px;
      box-shadow: 3px 0 10px rgba(0, 0, 0, 0.3);
      position: fixed;
      color: #fff;
    }

    .sidebar h2 {
      font-size: 24px;
      margin-bottom: 30px;
      color: #fff;
    }

    .sidebar ul {
      list-style: none;
      padding: 0;
    }

    .sidebar ul li {
      margin: 20px 0;
    }

    .sidebar ul li a {
      color: #fff;
      text-decoration: none;
      font-size: 18px;
      transition: 0.3s;
    }

    .sidebar ul li a:hover {
      color: #ffd700;
    }

    .main-content {
      margin-left: 270px;
      padding: 40px;
    }

    .main-content section {
      margin-bottom: 60px;
    }

    .main-content h1 {
      font-size: 36px;
      color: #b00020;
      margin-bottom: 20px;
    }

    .car-gallery {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
    }

    .car-item {
      width: 200px;
      text-align: center;
    }

    .car-item img {
      width: 100%;
      border-radius: 10px;
      box-shadow: 0 0 8px rgba(0,0,0,0.2);
    }

    /* Clock */
    #clock {
      margin-top: 30px;
      width: 200px;
      height: 200px;
      border: 6px solid #fff;
      border-radius: 50%;
      position: relative;
      margin-left: auto;
      margin-right: auto;
      background: #222;
    }

    .hand {
      width: 50%;
      height: 2px;
      background: white;
      position: absolute;
      top: 50%;
      transform-origin: 100%;
      transform: rotate(90deg);
    }

    /* Visitor count */
    .visitor-count {
      margin-top: 20px;
      text-align: center;
      font-size: 18px;
      color: #fff;
    }

    /* Animated Mouse */
    .cursor {
      width: 20px;
      height: 20px;
      background-color: red;
      border-radius: 50%;
      position: fixed;
      pointer-events: none;
      transition: transform 0.1s ease-out;
      z-index: 9999;
    }

    /* Responsive */
    @media (max-width: 768px) {
      .sidebar {
        display: none;
      }
      .main-content {
        margin-left: 0;
        padding: 20px;
      }
    }
  </style>
</head>
<body>

  <!-- Animated Cursor -->
  <div class="cursor" id="cursor"></div>

  <!-- Sidebar -->
  <div class="sidebar">
    <h2>Auto Fusion</h2>
    <ul>
      <li><a href="#home">Home</a></li>
      <li><a href="#products">Products</a></li>
      <li><a href="#contact">Contact</a></li>
      <li><a href="#about">About Us</a></li>
    </ul>

    <div id="clock">
      <div id="hour" class="hand"></div>
      <div id="minute" class="hand" style="height: 3px;"></div>
      <div id="second" class="hand" style="background: red;"></div>
    </div>

    <div class="visitor-count">
      Visitor Count: <span id="visitor-count">0</span>
    </div>
  </div>

  <!-- Main Content -->
  <div class="main-content">
    <section id="home">
      <h1>Welcome to Auto Fusion Sales</h1>
      <p>We offer the most reliable and affordable cars in India, including popular models like Thar, Hycross, and more.</p>
      <div class="car-gallery">
        <div class="car-item">
          <img src="https://cdn.pixabay.com/photo/2023/03/25/13/24/car-7874873_960_720.jpg" alt="Hycross">
          <p>Hycross</p>
        </div>
        <div class="car-item">
          <img src="https://cdn.pixabay.com/photo/2018/08/27/00/49/jeep-3635590_960_720.jpg" alt="Thar">
          <p>Mahindra Thar</p>
        </div>
        <div class="car-item">
          <img src="https://cdn.pixabay.com/photo/2022/02/02/05/27/car-6988956_960_720.jpg" alt="Punch">
          <p>Tata Punch</p>
        </div>
      </div>
    </section>

    <section id="products">
      <h1>Our Products</h1>
      <p>We offer a variety of new and certified pre-owned vehicles including SUVs, hatchbacks, and sedans from top brands like Maruti, Tata, Hyundai, and Mahindra.</p>
    </section>

    <section id="contact">
      <h1>Contact Us</h1>
      <p><strong>Mobile:</strong> 9592373629</p>
      <p><strong>Address:</strong> Main Jain Nagar Road, Abohar</p>
    </section>

    <section id="about">
      <h1>About Us</h1>
      <p><strong>Auto Fusion Sales</strong> brings affordable and high-quality vehicles to customers across India. Founded by <strong>Ranjit Shergill</strong>, we prioritize trust and customer satisfaction. Visit us today to drive home your dream car!</p>
    </section>
  </div>

  <!-- JavaScript -->
  <script>
    // Visitor Counter
    let count = localStorage.getItem('visitCount') || 0;
    count++;
    localStorage.setItem('visitCount', count);
    document.getElementById('visitor-count').innerText = count;

    // Clock
    function updateClock() {
      const now = new Date();
      const istOffset = 5.5 * 60 * 60 * 1000;
      const istTime = new Date(now.getTime() + istOffset);

      const hour = istTime.getUTCHours();
      const minute = istTime.getUTCMinutes();
      const second = istTime.getUTCSeconds();

      document.getElementById('hour').style.transform = `rotate(${hour * 30 + minute / 2}deg)`;
      document.getElementById('minute').style.transform = `rotate(${minute * 6}deg)`;
      document.getElementById('second').style.transform = `rotate(${second * 6}deg)`;
    }
    setInterval(updateClock, 1000);
    updateClock();

    // Animated Mouse
    const cursor = document.getElementById('cursor');
    document.addEventListener('mousemove', e => {
      cursor.style.left = e.pageX + 'px';
      cursor.style.top = e.pageY + 'px';
    });

    // Smooth Scroll for Nav
    document.querySelectorAll('.sidebar a').forEach(link => {
      link.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        target.scrollIntoView({ behavior: 'smooth' });
      });
    });
  </script>
</body>
</html>
