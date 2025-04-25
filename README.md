<!NAVIN SEHRAWAT>
<html lang="hi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>फसल सलाह बॉट</title>
  <style>
    body {
      font-family: 'Noto Sans Devanagari', sans-serif;
      background-color: #f6fff3;
      color: #333;
      text-align: center;
      padding: 30px;
    }
    h1 {
      color: #2e7d32;
    }
    select, button {
      padding: 10px;
      font-size: 18px;
      margin: 10px;
      width: 80%;
      max-width: 300px;
    }
    #result {
      margin-top: 30px;
      padding: 20px;
      background-color: #e8f5e9;
      border-radius: 10px;
      border: 1px solid #a5d6a7;
      font-size: 18px;
      text-align: left;
      max-width: 800px;
      margin-left: auto;
      margin-right: auto;
    }
  </style>
</head>
<body>

  <h1>फसल सलाह बॉट</h1>

  <label for="crop">फसल चुनें:</label><br>
  <select id="crop">
    <option value="wheat">गेहूं</option>
    <option value="rice">धान</option>
    <option value="mustard">सरसों</option>
    <option value="gram">चना</option>
    <option value="sugarcane">गन्ना</option>
    <option value="maize">मक्का</option>
    <option value="bottle gourd">लौकी</option>
    <option value="bitter gourd">करेला</option>
    <option value="ladyfinger">भिंडी</option>
    <option value="beans">सेम</option>
    <option value="fenugreek">मेथी</option>
    <option value="green chili">हरी मिर्च</option>
    <option value="turmeric">हल्दी</option>
    <option value="ginger">अदरक</option>
    <option value="coriander">धनिया</option>
    <option value="potato">आलू</option>
    <option value="onion">प्याज</option>
    <option value="garlic">लहसुन</option>
    <option value="carrot">गाजर</option>
    <option value="peas">मटर</option>
    <option value="tomato">टमाटर</option>
    <option value="brinjal">बैंगन</option>
    <option value="spinach">पालक</option>
    <option value="cabbage">पत्ता गोभी</option>
    <option value="cauliflower">फूल गोभी</option>
    <option value="capsicum">शिमला मिर्च</option>
    <option value="radish">मूली</option>
    <option value="pumpkin">कद्दू</option>
    <option value="cucumber">खीरा</option>
    <option value="groundnut">मूंगफली</option>
    <option value="soybean">सोयाबीन</option>
    <option value="black gram">उड़द</option>
    <option value="green gram">मूंग</option>
  </select><br><br>

  <label for="season">मौसम चुनें:</label><br>
  <select id="season">
    <option value="rabi">रबी</option>
    <option value="kharif">खरीफ</option>
    <option value="summer">गर्मी</option>
  </select><br><br>

  <button onclick="showTip()">सलाह दिखाओ</button>

  <div id="result"></div>

  <script>
    const tips = {
      "wheat": {
        "rabi": "बुवाई: अक्तूबर-दिसंबर | पानी: 4-5 बार (20-25 दिन में) | खाद: 60kg N, 40kg P, 40kg K प्रति किला | उत्पादन: ~18-22 क्विंटल/किला"
      },
      "rice": {
        "kharif": "बुवाई: जून-जुलाई | पानी: खेत में भरपूर पानी | खाद: 80kg N, 60kg P, 40kg K प्रति किला | उत्पादन: ~25-30 क्विंटल/किला"
      },
      "mustard": {
        "rabi": "बुवाई: अक्टूबर-नवंबर | पानी: 2-3 बार | खाद: 50kg N, 40kg P, 20kg K प्रति किला | उत्पादन: ~6-8 क्विंटल/किला"
      },
      "gram": {
        "rabi": "बुवाई: अक्टूबर-नवंबर | पानी: 1-2 बार | खाद: 20kg N, 40kg P प्रति किला | उत्पादन: ~8-10 क्विंटल/किला"
      },
      "sugarcane": {
        "kharif": "बुवाई: जून-जुलाई | पानी: हर 10-12 दिन | खाद: 150kg N, 75kg P, 75kg K | उत्पादन: ~300-400 क्विंटल/किला"
      },
      "maize": {
        "kharif": "बुवाई: जून | पानी: हर 15 दिन | खाद: 100kg N, 60kg P, 40kg K | उत्पादन: ~18-20 क्विंटल/किला"
      },
      "bottle gourd": {
        "summer": "बुवाई: फरवरी-मार्च | पानी: हर 5-7 दिन | खाद: गोबर खाद + 50kg N | उत्पादन: ~120-150 क्विंटल/किला"
      },
      "bitter gourd": {
        "kharif": "बुवाई: जून | पानी: हर 4-5 दिन | खाद: गोबर खाद + 60kg N | उत्पादन: ~80-100 क्विंटल/किला"
      },
      "ladyfinger": {
        "summer": "बुवाई: मार्च | पानी: 4-6 दिन के अंतर | खाद: 60kg N, 30kg P | उत्पादन: ~80-90 क्विंटल/किला"
      },
      "beans": {
        "rabi": "बुवाई: अक्तूबर | पानी: 8-10 दिन पर | खाद: जैविक खाद + 30kg N | उत्पादन: ~50-60 क्विंटल/किला"
      },
      "fenugreek": {
        "rabi": "बुवाई: अक्तूबर-नवंबर | पानी: 2-3 बार | खाद: जैविक खाद | उत्पादन: ~30-40 क्विंटल/किला"
      },
      "green chili": {
        "kharif": "नर्सरी: मई | पानी: 5-6 दिन में | खाद: 60kg N, 50kg P | उत्पादन: ~60-80 क्विंटल/किला"
      },
      "turmeric": {
        "kharif": "बुवाई: मई-जून | पानी: हर 7 दिन | खाद: गोबर + 100kg N | उत्पादन: ~100-150 क्विंटल/किला"
      },
      "ginger": {
        "kharif": "बुवाई: अप्रैल-मई | पानी: नमी बनाए रखें | खाद: जैविक खाद + 75kg N | उत्पादन: ~80-120 क्विंटल/किला"
      },
      "coriander": {
        "rabi": "बुवाई: अक्तूबर-नवंबर | पानी: 2-3 बार | खाद: जैविक खाद | उत्पादन: ~10-12 क्विंटल/किला"
      },
      "potato": {
        "rabi": "बुवाई: अक्टूबर-नवंबर | पानी: हर 12-15 दिन | खाद: 150kg N, 100kg P | उत्पादन: ~90-120 क्विंटल/किला"
      },
      "onion": {
        "rabi": "बुवाई: नवम्बर | पानी: हर 7-10 दिन | खाद: 100kg N, 50kg P | उत्पादन: ~120-150 क्विंटल/किला"
      },
      "garlic": {
        "rabi": "बुवाई: अक्टूबर-नवंबर | पानी: 15 दिन में | खाद: 60kg N, 40kg P | उत्पादन: ~60-80 क्विंटल/किला"
      },
      "carrot": {
        "rabi": "बुवाई: अक्टूबर | पानी: हर 10 दिन | खाद: जैविक खाद | उत्पादन: ~70-90 क्विंटल/किला"
      },
      "peas": {
        "rabi": "बुवाई: नवम्बर | पानी: 10 दिन में | खाद: 20kg N, 40kg P | उत्पादन: ~40-50 क्विंटल/किला"
      },
      "tomato": {
        "summer": "बुवाई: फरवरी | पानी: हर 4 दिन | खाद: 100kg N, 50kg P | उत्पादन: ~150-200 क्विंटल/किला"
      },
      "brinjal": {
        "summer": "बुवाई: मार्च | पानी: हर 5-6 दिन | खाद: गोबर + 60kg N | उत्पादन: ~100-150 क्विंटल/किला"
      },
      "spinach": {
        "rabi": "बुवाई: अक्तूबर | पानी: 7-10 दिन पर | खाद: जैविक खाद | उत्पादन: ~40-50 क्विंटल/किला"
      },
      "cabbage": {
        "rabi": "बुवाई: नवम्बर | पानी: 10 दिन में | खाद: 100kg N | उत्पादन: ~150 क्विंटल/किला"
      },
      "cauliflower": {
        "rabi": "बुवाई: अक्तूबर-नवंबर | पानी: हर 7 दिन | खाद: 100kg N | उत्पादन: ~100 क्विंटल/किला"
      },
      "capsicum": {
        "summer": "बुवाई: मार्च | पानी: हर 4-5 दिन | खाद: 80kg N, 50kg P | उत्पादन: ~80-100 क्विंटल/किला"
      },
      "radish": {
        "rabi": "बुवाई: अक्तूबर-नवंबर | पानी: 10-15 दिन पर | खाद: गोबर खाद | उत्पादन: ~60-70 क्विंटल/किला"
      },
      "pumpkin": {
        "kharif": "बुवाई: जून | पानी: हर 6-7 दिन | खाद: जैविक खाद | उत्पादन: ~80-100 क्विंटल/किला"
      },
      "cucumber": {
        "summer": "बुवाई: फरवरी | पानी: हर 4 दिन | खाद: 60kg N | उत्पादन: ~90-110 क्विंटल/किला"
      },
      "groundnut": {
        "kharif": "बुवाई: जून | पानी: 15-20 दिन पर | खाद: 40kg N, 60kg P | उत्पादन: ~15-18 क्विंटल/किला"
      },
      "soybean": {
        "kharif": "बुवाई: जून-जुलाई | पानी: 12-15 दिन | खाद: 60kg N, 60kg P | उत्पादन: ~12-15 क्विंटल/किला"
      },
      "black gram": {
        "kharif": "बुवाई: जून | पानी: 15-20 दिन पर | खाद: 20kg N, 40kg P | उत्पादन: ~10-12 क्विंटल/किला"
      },
      "green gram": {
        "summer": "बुवाई: मार्च | पानी: 10-12 दिन पर | खाद: 20kg N, 40kg P | उत्पादन: ~10-12 क्विंटल/किला"
      }
    };

    function showTip() {
      const crop = document.getElementById("crop").value;
      const season = document.getElementById("season").value;
      const result = document.getElementById("result");

      if (tips[crop] && tips[crop][season]) {
        result.innerHTML = `<strong>${crop.charAt(0).toUpperCase() + crop.slice(1)}</strong><br>${tips[crop][season]}`;
      } else {
        result.innerHTML = "इस मौसम के लिए जानकारी उपलब्ध नहीं है।";
      }
    }
  </script>

</body>
</html>
