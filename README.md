
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Amazon Fulfillment Centers - BEUMER Styled Map</title>

  <!-- Leaflet CSS -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />

  <!-- Leaflet JS -->
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      font-family: 'Segoe UI', sans-serif;
      background-color: #E6F0FA;
    }

    header {
      position: absolute;
      top: 0;
      width: 100%;
      background-color: #005BAC;
      color: white;
      text-align: center;
      padding: 1rem;
      font-size: 1.8rem;
      z-index: 1000;
      box-shadow: 0 2px 5px rgba(0,0,0,0.2);
    }

    #map {
      position: absolute;
      top: 60px;
      bottom: 0;
      left: 0;
      right: 0;
    }

    /* Custom popup styling */
    .leaflet-popup-content-wrapper {
      background-color: rgba(0, 91, 172, 0.9);
      color: white;
      border-radius: 8px;
      padding: 10px;
    }

    .leaflet-popup-tip {
      background-color: rgba(0, 91, 172, 0.9);
    }

    .leaflet-popup-content {
      margin: 0;
      font-size: 14px;
      line-height: 1.4;
    }

    .leaflet-container a {
      color: #FFD700;
    }
  </style>
</head>
<body>

  <header>Amazon Fulfillment Centers - BEUMER Corp Styled</header>
  <div id="map"></div>

  <script>
    const map = L.map('map').setView([39.8283, -98.5795], 4); // Center of continental US

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; OpenStreetMap contributors'
    }).addTo(map);

    const amazonSites = [
      { name: "SCO2", lat: 39.7392, lon: -104.9903, address: "SCO2 - Denver, CO" },
      { name: "SAX7", lat: 34.0606, lon: -117.3955, address: "SAX7 - 19150 Orange St, Bloomington, CA 92316" },
      { name: "GEG5", lat: 47.6733, lon: -117.2264, address: "GEG5 - Spokane, WA" },
      { name: "ORF5", lat: 36.8485, lon: -76.2913, address: "ORF5 - 201 Technology Blvd, Suffolk, VA 23434" },
      { name: "CNO8", lat: 35.1692, lon: -80.8103, address: "CNO8 - Charlotte, NC" },
      { name: "SAT9", lat: 29.4210, lon: -98.5280, address: "SAT9 - San Antonio, TX" },
      { name: "MTN6", lat: 39.2700, lon: -76.5450, address: "MTN6 - 2010 Broening Hwy, Baltimore, MD 21224" },
      { name: "RIC4", lat: 37.5787, lon: -77.4892, address: "RIC4 - 5000 Commerce Rd, Richmond, VA 23234" },
      { name: "YXX1", lat: 49.0351, lon: -122.6470, address: "YXX1 - 2933 Mount Lehman Rd, Abbotsford, BC, Canada" },
      { name: "SFL9", lat: 27.9956, lon: -82.0239, address: "SFL9 - 1760 County Line Rd, Lakeland, FL 33811" }
    ];

    amazonSites.forEach(site => {
      L.marker([site.lat, site.lon])
        .addTo(map)
        .bindPopup(`<strong>${site.name}</strong><br>${site.address}`);
    });
  </script>

</body>
</html>


