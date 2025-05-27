<html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Scenic Time Clock</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
      text-align: center;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      transition: background-image 1s ease-in-out;
      height: 100vh;
      color: white;
    }

    .clock {
      font-size: 4em;
      margin-top: 25vh;
      text-shadow: 2px 2px 8px black;
    }

    .label {
      font-size: 2em;
      margin-top: 10px;
      text-shadow: 1px 1px 6px black;
    }
  </style>
</head>
<body>

  <div class="clock" id="clock"></div>
  <div class="label" id="label"></div>

  <script>
    function getLabelAndBackground(hours, minutes) {
      const totalMinutes = hours * 60 + minutes;

      if (totalMinutes >= 660 && totalMinutes < 780) 
  return [
    "Dawn",
    "url('https://images.unsplash.com/photo-1503424160383-57de83bd6fb2?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D')"
  ];
      if (totalMinutes >= 780 && totalMinutes < 900) 
  return [
    "Morning",
    "url('https://images.unsplash.com/photo-1571080648416-3fda23702c51?q=80&w=987&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D')"
  ];
     if (totalMinutes >= 900 && totalMinutes < 1020) 
  return [
    "Noon",
    "url('https://images.unsplash.com/photo-1671555443135-0e625aaa08e6?q=80&w=1035&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D')"
  ];
      if (totalMinutes >= 1020 && totalMinutes < 1140) 
  return [
    "Afternoon",
    "url('https://images.unsplash.com/photo-1593143998138-422382462e01?q=80&w=988&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D')"
  ];
      if (totalMinutes >= 1140 && totalMinutes < 1200) 
  return [
    "Dusk",
    "url('https://images.unsplash.com/photo-1579037440434-eaf51bade044?q=80&w=1064&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D')"
  ];
      if (totalMinutes >= 1200 && totalMinutes < 1320) 
  return [
    "Evening",
    "url('https://images.unsplash.com/photo-1554315025-0f10196df289?w=1200&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8ZXZlbmluZ3xlbnwwfHwwfHx8MA%3D%3D')"
  ];
      if (totalMinutes >= 1320 || totalMinutes < 300) 
      return [
  "Night",
  "url('https://images.unsplash.com/photo-1477840539360-4a1d23071046?w=1200&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTB8fG5pZ2h0JTIwc2t5fGVufDB8fDB8fHww')"
];  
        ;
      return [
  "midNight",
  "url('https://images.unsplash.com/photo-1590418606746-018840f9cd0f?q=80&w=987&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D')"
];
    }

    function updateClock() {
      const now = new Date();
      let h = now.getHours();
      const m = now.getMinutes();
      const s = now.getSeconds();
      const ampm = h >= 12 ? 'PM' : 'AM';
      let h12 = h % 12 || 12;

      const timeStr = `${h12.toString().padStart(2, '0')}:${m.toString().padStart(2, '0')}:${s.toString().padStart(2, '0')} ${ampm}`;
      document.getElementById('clock').textContent = timeStr;

      const [label, bgImage] = getLabelAndBackground(h, m);
      document.getElementById('label').textContent = label;
      document.body.style.backgroundImage = bgImage;
    }

    setInterval(updateClock, 1000);
    updateClock();
  </script>

</body>
</html>
