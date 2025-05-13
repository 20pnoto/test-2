<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>BEUMER Projects Map</title>

  <!-- Leaflet CSS & JS -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      background-color: #E6F0FA;
    }

    #map {
      width: 100vw;
      height: 100vh;
      z-index: 0;
    }

    /* Custom circle marker icons */
    .custom-ping {
      width: 20px;
      height: 20px;
      border-radius: 50%;
      border: 2px solid white;
      box-shadow: 0 0 6px rgba(0,0,0,0.3);
    }

    .ping-green {
      background-color: #3CB371; /* mediumseagreen */
    }

    .ping-yellow {
      background-color: #FFD700; /* gold */
    }

    .ping-red {
      background-color: #DC143C; /* crimson */
    }

    /* Popup styling */
    .leaflet-popup-content-wrapper {
      background: white !important;
      border-radius: 8px !important;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3) !important;
      border: none !important;
    }

    .leaflet-popup-tip {
      background: white !important;
    }

    .leaflet-popup-content {
      color: #003b6f;
      font-size: 14px;
      font-weight: bold;
      margin: 8px 12px;
    }

    /* Legend */
    #legend {
      position: fixed;
      bottom: 15px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(255, 255, 255, 0.95);
      border-radius: 10px;
      padding: 10px 20px;
      font-size: 14px;
      font-weight: 600;
      color: #003b6f;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.25);
      display: flex;
      gap: 20px;
      align-items: center;
      z-index: 1000;
      pointer-events: none;
    }

    .legend-item {
      display: flex;
      align-items: center;
      gap: 6px;
      pointer-events: auto;
    }

    .legend-icon {
      width: 14px;
      height: 14px;
      border-radius: 50%;
      border: 2px solid white;
      box-shadow: 0 0 3px rgba(0,0,0,0.3);
    }

    .green-marker { background-color: #3CB371; }
    .yellow-marker { background-color: #FFD700; }
    .red-marker { background-color: #DC143C; }
  </style>
</head>
<body>

  <div id="map"></div>

  <!-- Legend -->
  <div id="legend">
    <div class="legend-item">
      <div class="legend-icon green-marker"></div>
      Active
    </div>
    <div class="legend-item">
      <div class="legend-icon yellow-marker"></div>
      Change Orders
    </div>
    <div class="legend-item">
      <div class="legend-icon red-marker"></div>
      Inactive
    </div>
  </div>

  <script>
    const map = L.map('map').setView([39.8283, -98.5795], 4);

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; OpenStreetMap contributors'
    }).addTo(map);

    // Create CSS-based markers
    function createPingMarker(colorClass) {
      return L.divIcon({
        className: `custom-ping ${colorClass}`,
        iconSize: [20, 20],
        iconAnchor: [10, 10],
        popupAnchor: [0, -10]
      });
    }

    const greenIcon = createPingMarker("ping-green");
    const yellowIcon = createPingMarker("ping-yellow");
    const redIcon = createPingMarker("ping-red");

    const amazonSites = [
      { name: "SCO2", lat: 39.7392, lon: -104.9903, address: "Denver, CO" },
      { name: "SAX7", lat: 34.0606, lon: -117.3955, address: "Bloomington, CA", icon: redIcon },
      { name: "GEG5", lat: 47.6733, lon: -117.2264, address: "Spokane, WA", icon: yellowIcon },
      { name: "ORF5", lat: 36.8485, lon: -76.2913, address: "Suffolk, VA" },
      { name: "CNO8", lat: 34.3917, lon: -118.5373, address: "Santa Clarita, CA" },
      { name: "SAT9", lat: 29.4210, lon: -98.5280, address: "San Antonio, TX" },
      { name: "MTN6", lat: 39.2700, lon: -76.5450, address: "Baltimore, MD" },
      { name: "RIC4", lat: 37.5787, lon: -77.4892, address: "Richmond, VA" },
      { name: "YXX1", lat: 49.2333, lon: -122.6833, address: "Pitt Meadows, BC, Canada" },
      { name: "SFL9", lat: 27.9956, lon: -82.0239, address: "Lakeland, FL" }
    ];

    amazonSites.forEach(site => {
      const markerIcon = site.icon || greenIcon;
      L.marker([site.lat, site.lon], { icon: markerIcon })
        .addTo(map)
        .bindPopup(`<strong>${site.name}</strong><br>${site.address}`);
    });
  </script>
</body>
</html>


</html>

</body>
</html>
