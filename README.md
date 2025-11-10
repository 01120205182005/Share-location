<!doctype html>

<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Share Your Location</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; background-color: #f0f2f5; }
    h2 { color: #333; }
    button { padding: 12px 25px; font-size: 16px; background-color: #4CAF50; color: white; border: none; border-radius: 5px; cursor: pointer; }
    button:hover { background-color: #45a049; }
    pre { background-color: #e8e8e8; padding: 10px; border-radius: 5px; white-space: pre-wrap; }
  </style>
</head>
<body>
  <h2>Hello! This page was prepared for you by Dumbo</h2>
  <p>Click the button below and allow your browser to access your location. The location will only be shared if you approve.</p>
  <button id="getLoc">Share my location</button>
  <pre id="status"></pre><script>
const status = document.getElementById('status');

document.getElementById('getLoc').addEventListener('click', () => {
  if (!navigator.geolocation) {
    status.textContent = 'Geolocation is not supported by your browser.';
    return;
  }

  status.textContent = 'Requesting permission...';

  navigator.geolocation.getCurrentPosition(async (pos) => {
    const coords = {
      latitude: pos.coords.latitude,
      longitude: pos.coords.longitude,
      accuracy: pos.coords.accuracy,
      timestamp: pos.timestamp
    };
