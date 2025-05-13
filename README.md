<!DOCTYPE html>
<html>
<head>
  <title>Amazon Fulfillment Centers Map</title>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- Leaflet CSS -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />

  <!-- Leaflet JS -->
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #f4f7fa;
    }
    header {
      background-color: #2c3e50;
      color: #ecf0f1;
      padding: 1rem;
      text-align: center;
      font-size: 1.5rem;
    }
    #map {
      height: calc(100vh - 60px); /* adjust height based on header */
    }
    .leaflet-popup-content {
      font-size: 14px;
      color: #2c3e50;
    }
  </style>
</head>
<body>

<header>Amazon Fulfillment Centers - Live Pings Map</header>

<div id="map"></div>

<script>
  // Initialize map centered on continental USA
  var map = L.map('map').setView([39.8283, -98.5795], 4); // Geographic center of US

  // Add tile layer
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(map);

  // Amazon Fulfillment Sites
  var amazonSites = [
    {
      name: "SCO2",
      lat: 39.7392,
      lon: -104.9903,
      address: "SCO2 - Denver, CO"
    },
    {
      name: "SAX7",
      lat: 34.0606,
      lon: -117.3955,
      address: "SAX7 - 19150 Orange St, Bloomington, CA 92316"
    },
    {
      name: "GEG5",
      lat: 47.6733,
      lon: -117.2264,
      address: "GEG5 - Spokane, WA"
    },
    {
      name: "ORF5",
      lat: 36.8485,
      lon: -76.2913,
      address: "ORF5 - 201 Technology Blvd, Suffolk, VA 23434"
    },
    {
      name: "CNO8",
      lat: 35.1692,
      lon: -80.8103,
      address: "CNO8 - Charlotte, NC"
    },
    {
      name: "SAT9",
      lat: 29.4210,
      lon: -98.5280,
      address: "SAT9 - San Antonio, TX"
    },
    {
      name: "MTN6",
      lat: 39.2700,
      lon: -76.5450,
      address: "MTN6 - 2010 Broening Hwy, Baltimore, MD 21224"
    },
    {
      name: "RIC4",
      lat: 37.5787,
      lon: -77.4892,
      address: "RIC4 - 5000 Commerce Rd, Richmond, VA 23234"
    },
    {
      name: "YXX1",
      lat: 49.0351,
      lon: -122.6470,
      address: "YXX1 - 2933 Mount Lehman Rd, Abbotsford, BC, Canada"
    },
    {
      name: "SFL9",
      lat: 27.9956,
      lon: -82.0239,
      address: "SFL9 - 1760 County Line Rd, Lakeland, FL 33811"
    }
  ];

  // Add markers
  amazonSites.forEach(function(site) {
    L.marker([site.lat, site.lon])
      .addTo(map)
      .bindPopup(`<b>${site.name}</b><br>${site.address}`);
  });
</script>

</body>
</html>

