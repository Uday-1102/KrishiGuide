<!DOCTYPE html>
<html lang="en">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>KrishiGuide</title>

<style>

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
    background: #f1f7f1;
    color: #243424;
}

header {
    background: linear-gradient(135deg, #176b37, #2e8b57);
    color: white;
    padding: 25px;
    text-align: center;
}

header h1 {
    margin: 0;
    font-size: 30px;
}

header p {
    margin: 10px auto 0;
    max-width: 900px;
    font-size: 13px;
    line-height: 1.5;
    opacity: 0.94;
}

.container {
    max-width: 1100px;
    margin: 25px auto;
    padding: 0 18px;
}

.card {
    background: white;
    border-radius: 14px;
    padding: 24px;
    margin-bottom: 20px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.07);
}

.card h2 {
    color: #176b37;
    margin-top: 0;
}

.grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 18px;
}

label {
    display: block;
    font-weight: bold;
    margin-bottom: 7px;
}

select,
input {
    width: 100%;
    padding: 12px;
    border: 1px solid #ccd8cc;
    border-radius: 8px;
    font-size: 15px;
    background: white;
}

select:focus,
input:focus {
    outline: 2px solid #72b889;
}

.button-area {
    text-align: center;
    margin-top: 25px;
}

button {
    background: #176b37;
    color: white;
    border: none;
    padding: 14px 32px;
    border-radius: 8px;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
}

button:hover {
    background: #0f542a;
}

.result {
    display: none;
}

.score-box {
    text-align: center;
    padding: 25px;
    border-radius: 14px;
    background: #eaf7ed;
    border: 2px solid #6bb77d;
    margin-bottom: 20px;
}

.score {
    font-size: 55px;
    font-weight: bold;
    color: #176b37;
}

.status {
    font-size: 20px;
    font-weight: bold;
    margin-top: 5px;
}

.prediction-subtitle {
    margin-top: 10px;
    color: #5d6d5d;
    font-size: 14px;
}

.result-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 18px;
}

.info-box {
    background: #f7faf7;
    padding: 18px;
    border-radius: 10px;
    border-left: 4px solid #2e8b57;
}

.info-box h3 {
    margin-top: 0;
    color: #176b37;
}

.crop-card {
    background: #f7faf7;
    border-radius: 10px;
    padding: 15px;
    margin: 10px 0;
    border: 1px solid #dbe8dc;
}

.crop-score {
    float: right;
    font-weight: bold;
    color: #176b37;
}

.bar {
    height: 10px;
    background: #dce7dd;
    border-radius: 10px;
    overflow: hidden;
    margin-top: 8px;
}

.bar-fill {
    height: 100%;
    background: #2e8b57;
    transition: width 0.6s ease;
}

.factor {
    margin: 12px 0;
}

.factor-top {
    display: flex;
    justify-content: space-between;
    font-size: 14px;
    font-weight: bold;
}

.factor-bar {
    height: 8px;
    background: #dce7dd;
    border-radius: 8px;
    overflow: hidden;
    margin-top: 5px;
}

.factor-fill {
    height: 100%;
    border-radius: 8px;
}

.factor-good {
    background: #2e8b57;
}

.factor-medium {
    background: #d5a900;
}

.factor-bad {
    background: #c84b4b;
}

.metric {
    display: inline-block;
    background: white;
    border: 1px solid #d7e3d8;
    border-radius: 9px;
    padding: 12px 16px;
    margin: 5px;
    min-width: 150px;
}

.metric strong {
    display: block;
    color: #176b37;
    font-size: 20px;
    margin-top: 4px;
}

.warning {
    background: #fff8d8;
    border-left: 5px solid #e0b400;
    padding: 14px;
    border-radius: 8px;
    margin-top: 18px;
    font-size: 13px;
    line-height: 1.6;
}

.success-box {
    background: #edf8ef;
    border-left: 5px solid #2e8b57;
    padding: 14px;
    border-radius: 8px;
    margin-top: 18px;
}

ul {
    line-height: 1.7;
}

@media(max-width: 700px) {

    .grid,
    .result-grid {
        grid-template-columns: 1fr;
    }

    header h1 {
        font-size: 24px;
    }

    .score {
        font-size: 45px;
    }

}

</style>

</head>

<body>


<header>

    <h1>🌾 KrishiGuide</h1>

    <p>
        This is a crop yield prediction website and prediction is provided on soil type, historical data, rainfall amount, etc. and might not be exact. For exact real-world prediction, please contact professionals.
    </p>

</header>


<div class="container">


<!-- =====================================================
     INPUT SECTION
===================================================== -->

<div class="card">

    <h2>👨‍🌾 Farmer Information</h2>

    <div class="grid">


        <div>

            <label for="farmerName">
                Farmer Name
            </label>

            <input
                type="text"
                id="farmerName"
                placeholder="Enter your name"
            >

        </div>


        <div>

            <label for="age">
                Age
            </label>

            <input
                type="number"
                id="age"
                min="1"
                max="120"
                placeholder="Enter your age"
            >

        </div>


        <div>

            <label for="state">
                State
            </label>

            <select id="state">

                <option value="">
                    Select State
                </option>

            </select>

        </div>


        <div>

            <label for="district">
                District
            </label>

            <input
                type="text"
                id="district"
                placeholder="Enter your district"
            >

        </div>


        <div>

            <label for="soil">
                Soil Type
            </label>

            <select id="soil">

                <option value="">
                    Select Soil Type
                </option>

                <option>Alluvial</option>
                <option>Black</option>
                <option>Red</option>
                <option>Laterite</option>
                <option>Sandy</option>
                <option>Loamy</option>
                <option>Clay</option>
                <option>Mountain</option>
                <option>Desert/Arid</option>

            </select>

        </div>


        <div>

            <label for="month">
                Growing / Sowing Month
            </label>

            <select id="month">

                <option value="">
                    Select Month
                </option>

                <option>January</option>
                <option>February</option>
                <option>March</option>
                <option>April</option>
                <option>May</option>
                <option>June</option>
                <option>July</option>
                <option>August</option>
                <option>September</option>
                <option>October</option>
                <option>November</option>
                <option>December</option>

            </select>

        </div>


        <div>

            <label for="previousCrop">
                Previous Crop
            </label>

            <select id="previousCrop">

                <option value="">
                    Select Previous Crop
                </option>

            </select>

        </div>


        <div>

            <label for="crop">
                Crop You Want To Grow
            </label>

            <select id="crop">

                <option value="">
                    Select Crop
                </option>

            </select>

        </div>


        <div>

            <label for="irrigation">
                Irrigation Availability
            </label>

            <select id="irrigation">

                <option value="">
                    Select
                </option>

                <option>Good</option>
                <option>Moderate</option>
                <option>Limited</option>
                <option>Rainfed</option>

            </select>

        </div>


        <div>

            <label for="rainfall">
                Expected Rainfall Condition
            </label>

            <select id="rainfall">

                <option value="">
                    Select
                </option>

                <option>High</option>
                <option>Moderate</option>
                <option>Low</option>
                <option>Very Low</option>

            </select>

        </div>


    </div>


    <div class="button-area">

        <button onclick="calculatePrediction()">
            🔍 Predict Crop Suitability
        </button>

    </div>

</div>


<!-- =====================================================
     RESULT
===================================================== -->

<div class="card result" id="result">


    <h2>📊 Crop Prediction Result</h2>


    <div class="score-box">


        <div
            id="cropName"
            style="font-size:25px;font-weight:bold;"
        >
            Crop
        </div>


        <div
            class="score"
            id="score"
        >
            0%
        </div>


        <div
            class="status"
            id="status"
        >
            -
        </div>


        <div
            class="prediction-subtitle"
            id="predictionSubtitle"
        >
            Estimated crop suitability
        </div>


        <div style="margin-top:15px;">

            <span class="metric">

                Confidence

                <strong id="confidence">
                    -
                </strong>

            </span>


            <span class="metric">

                Yield Potential

                <strong id="yieldPotential">
                    -
                </strong>

            </span>

        </div>


    </div>


    <div class="result-grid">


        <div class="info-box">

            <h3>
                👨‍🌾 Farmer Information
            </h3>

            <p id="farmerInfo">
                -
            </p>

        </div>


        <div class="info-box">

            <h3>
                📍 Location
            </h3>

            <p id="locationInfo">
                -
            </p>

        </div>


        <div class="info-box">

            <h3>
                🌍 Agro-Climatic Information
            </h3>

            <p id="climateInfo">
                -
            </p>

        </div>


        <div class="info-box">

            <h3>
                🌱 Soil Information
            </h3>

            <p id="soilInfo">
                -
            </p>

        </div>


        <div class="info-box">

            <h3>
                🌾 Sowing Window
            </h3>

            <p id="sowingInfo">
                -
            </p>

        </div>


        <div class="info-box">

            <h3>
                📈 Yield Estimate
            </h3>

            <p id="yieldInfo">
                -
            </p>

        </div>


    </div>


    <!-- FACTOR ANALYSIS -->

    <div
        class="info-box"
        style="margin-top:18px;"
    >

        <h3>
            🧠 Prediction Factor Analysis
        </h3>

        <div id="factorAnalysis"></div>

    </div>


    <!-- NUTRIENT -->

    <div
        class="info-box"
        style="margin-top:18px;"
    >

        <h3>
            🧪 Nutrient / Manure Advice
        </h3>

        <div id="nutrientAdvice"></div>

    </div>


    <!-- WHY -->

    <div
        class="info-box"
        style="margin-top:18px;"
    >

        <h3>
            🌱 Why This Prediction?
        </h3>

        <ul id="reasonList"></ul>

    </div>


    <!-- ALTERNATIVES -->

    <div
        class="info-box"
        style="margin-top:18px;"
    >

        <h3>
            🔄 Alternative Crops
        </h3>

        <div id="alternatives"></div>

    </div>


    <div class="warning">

        <strong>Prediction limitation:</strong>
        This result is generated entirely inside this webpage using
        an embedded agricultural suitability model and synthetic
        reference information. It is not trained on live farm data
        and should not be interpreted as a guaranteed crop yield or
        scientifically validated probability.

    </div>


</div>

</div>


<script>


/* =========================================================
   STATE DATA

   The "historicalIndex" represents a synthetic historical
   stability proxy used by the offline model.

   It is NOT a real government dataset.
========================================================= */

const stateData = {


"West Bengal": {

    zone:
        "Lower Gangetic Plains and Eastern Coastal Region",

    climate:
        "Humid subtropical with high monsoon rainfall",

    soils:
        ["Alluvial","Clay","Loamy"],

    crops:
        ["Rice","Jute","Potato","Mustard","Vegetables"],

    rainfall:
        "High",

    historicalIndex: 0.84

},


"Punjab": {

    zone:
        "Trans-Gangetic Plains",

    climate:
        "Semi-arid to sub-humid",

    soils:
        ["Alluvial","Loamy"],

    crops:
        ["Wheat","Rice","Maize","Cotton","Mustard"],

    rainfall:
        "Moderate",

    historicalIndex: 0.86

},


"Haryana": {

    zone:
        "Trans-Gangetic Plains and Western Dry Region",

    climate:
        "Semi-arid to sub-humid",

    soils:
        ["Alluvial","Loamy","Sandy"],

    crops:
        ["Wheat","Rice","Mustard","Cotton","Bajra"],

    rainfall:
        "Low",

    historicalIndex: 0.80

},


"Uttar Pradesh": {

    zone:
        "Upper and Middle Gangetic Plains",

    climate:
        "Subtropical with variable rainfall",

    soils:
        ["Alluvial","Loamy","Sandy"],

    crops:
        ["Rice","Wheat","Potato","Sugarcane","Pulses"],

    rainfall:
        "Moderate",

    historicalIndex: 0.82

},


"Bihar": {

    zone:
        "Middle Gangetic Plains",

    climate:
        "Subtropical with humid monsoon conditions",

    soils:
        ["Alluvial","Loamy"],

    crops:
        ["Rice","Wheat","Maize","Pulses","Vegetables"],

    rainfall:
        "Moderate",

    historicalIndex: 0.78

},


"Rajasthan": {

    zone:
        "Western Dry Region and Aravalli Zone",

    climate:
        "Arid to semi-arid",

    soils:
        ["Sandy","Desert/Arid","Loamy"],

    crops:
        ["Bajra","Mustard","Wheat","Pulses"],

    rainfall:
        "Low",

    historicalIndex: 0.73

},


"Madhya Pradesh": {

    zone:
        "Central Plateau and Hills",

    climate:
        "Semi-arid to sub-humid tropical",

    soils:
        ["Black","Loamy","Red"],

    crops:
        ["Soybean","Wheat","Chickpea","Maize","Sorghum"],

    rainfall:
        "Moderate",

    historicalIndex: 0.83

},


"Maharashtra": {

    zone:
        "Western Plateau and Hills / Deccan Plateau",

    climate:
        "Tropical wet-dry to semi-arid",

    soils:
        ["Black","Red","Loamy"],

    crops:
        ["Sugarcane","Sorghum","Wheat","Groundnut","Cotton"],

    rainfall:
        "Moderate",

    historicalIndex: 0.79

},


"Gujarat": {

    zone:
        "Gujarat Plains and Hills",

    climate:
        "Semi-arid to dry tropical",

    soils:
        ["Black","Alluvial","Sandy"],

    crops:
        ["Cotton","Groundnut","Wheat","Bajra"],

    rainfall:
        "Low",

    historicalIndex: 0.77

},


"Karnataka": {

    zone:
        "Deccan Plateau and Southern Plateau",

    climate:
        "Tropical semi-arid to savanna",

    soils:
        ["Red","Black","Loamy"],

    crops:
        ["Ragi","Maize","Groundnut","Cotton","Sorghum"],

    rainfall:
        "Moderate",

    historicalIndex: 0.78

},


"Tamil Nadu": {

    zone:
        "Tamil Nadu Plains and Eastern Coastal Region",

    climate:
        "Tropical semi-arid to humid",

    soils:
        ["Red","Black","Alluvial","Loamy"],

    crops:
        ["Rice","Sugarcane","Groundnut","Maize","Vegetables"],

    rainfall:
        "Moderate",

    historicalIndex: 0.80

},


"Kerala": {

    zone:
        "West Coast Plains and Western Ghats",

    climate:
        "Humid tropical",

    soils:
        ["Laterite","Alluvial","Loamy"],

    crops:
        ["Rice","Coconut","Banana","Pepper","Vegetables"],

    rainfall:
        "High",

    historicalIndex: 0.82

},


"Odisha": {

    zone:
        "Eastern Plateau and Coastal Plains",

    climate:
        "Humid tropical with strong monsoon influence",

    soils:
        ["Alluvial","Red","Clay","Laterite"],

    crops:
        ["Rice","Pulses","Groundnut","Maize","Vegetables"],

    rainfall:
        "High",

    historicalIndex: 0.79

},


"Jharkhand": {

    zone:
        "Chota Nagpur Plateau",

    climate:
        "Sub-humid tropical",

    soils:
        ["Red","Laterite","Loamy"],

    crops:
        ["Rice","Maize","Pulses","Vegetables"],

    rainfall:
        "High",

    historicalIndex: 0.75

},


"Chhattisgarh": {

    zone:
        "Chhattisgarh Plains and Eastern Plateau",

    climate:
        "Sub-humid tropical",

    soils:
        ["Red","Alluvial","Clay"],

    crops:
        ["Rice","Maize","Pulses","Sorghum"],

    rainfall:
        "High",

    historicalIndex: 0.78

},


"Telangana": {

    zone:
        "Deccan Plateau",

    climate:
        "Semi-arid tropical",

    soils:
        ["Red","Black","Loamy"],

    crops:
        ["Rice","Cotton","Maize","Chickpea","Sorghum"],

    rainfall:
        "Moderate",

    historicalIndex: 0.77

},


"Andhra Pradesh": {

    zone:
        "East Coast Plains and Deccan Plateau",

    climate:
        "Tropical semi-arid to humid",

    soils:
        ["Black","Red","Alluvial"],

    crops:
        ["Rice","Chilli","Cotton","Groundnut","Sugarcane"],

    rainfall:
        "Moderate",

    historicalIndex: 0.81

},


"Assam": {

    zone:
        "Brahmaputra Valley and North Eastern Plains",

    climate:
        "Humid subtropical with very high rainfall",

    soils:
        ["Alluvial","Loamy"],

    crops:
        ["Rice","Tea","Jute","Mustard","Vegetables"],

    rainfall:
        "Very High",

    historicalIndex:
        0.76

},


"Himachal Pradesh": {

    zone:
        "Western Himalayas",

    climate:
        "Temperate mountain",

    soils:
        ["Mountain","Loamy"],

    crops:
        ["Apple","Wheat","Maize","Potato","Vegetables"],

    rainfall:
        "High",

    historicalIndex:
        0.79

},


"Uttarakhand": {

    zone:
        "Western Himalayan Foothills and Mountains",

    climate:
        "Subtropical to temperate mountain",

    soils:
        ["Mountain","Loamy","Alluvial"],

    crops:
        ["Rice","Wheat","Maize","Potato","Vegetables"],

    rainfall:
        "High",

    historicalIndex:
        0.76

},


"Jammu and Kashmir": {

    zone:
        "Western Himalayas",

    climate:
        "Subtropical foothills to temperate mountain",

    soils:
        ["Alluvial","Mountain","Loamy"],

    crops:
        ["Rice","Wheat","Maize","Apple","Pulses"],

    rainfall:
        "Moderate",

    historicalIndex:
        0.78

},


"Sikkim": {

    zone:
        "Eastern Himalayas",

    climate:
        "Humid mountain",

    soils:
        ["Mountain","Loamy"],

    crops:
        ["Maize","Rice","Cardamom","Ginger","Vegetables"],

    rainfall:
        "Very High",

    historicalIndex:
        0.74

}

};


/* =========================================================
   CROP DATABASE

   baseYield = approximate synthetic baseline in tonnes/ha.
   These values are used ONLY by the offline model.
========================================================= */

const cropData = {


"Rice": {

    soils:["Alluvial","Clay","Loamy"],

    months:["June","July","August"],

    rainfall:["High","Moderate"],

    irrigation:["Good","Moderate","Rainfed"],

    baseYield:3.8,

    yieldMin:2.4,

    yieldMax:5.8,

    waterDemand:0.85,

    climate:["humid","subtropical","tropical"],

    advice:[
        "Maintain adequate soil moisture.",
        "Use balanced nitrogen, phosphorus and potassium according to soil-test recommendations.",
        "Organic manure or compost can help improve soil structure."
    ]

},


"Wheat": {

    soils:["Alluvial","Loamy","Black"],

    months:["October","November","December"],

    rainfall:["Low","Moderate"],

    irrigation:["Good","Moderate"],

    baseYield:3.2,

    yieldMin:2.0,

    yieldMax:5.0,

    waterDemand:0.60,

    climate:["subtropical","semi-arid","temperate"],

    advice:[
        "Maintain adequate irrigation during critical growth stages.",
        "Nitrogen management is important.",
        "Apply phosphorus and potassium based on soil testing."
    ]

},


"Maize": {

    soils:["Loamy","Alluvial","Red","Black"],

    months:["June","July","August","January","February"],

    rainfall:["Moderate","High"],

    irrigation:["Good","Moderate","Rainfed"],

    baseYield:3.6,

    yieldMin:2.2,

    yieldMax:6.0,

    waterDemand:0.65,

    climate:["subtropical","tropical","semi-arid"],

    advice:[
        "Ensure good drainage.",
        "Use organic manure to improve soil condition.",
        "Balanced NPK application is recommended based on soil testing."
    ]

},


"Potato": {

    soils:["Alluvial","Loamy","Sandy"],

    months:["October","November","December","January"],

    rainfall:["Low","Moderate"],

    irrigation:["Good","Moderate"],

    baseYield:18,

    yieldMin:10,

    yieldMax:28,

    waterDemand:0.70,

    climate:["subtropical","temperate"],

    advice:[
        "Potato prefers loose, well-drained soil.",
        "Use well-decomposed organic manure.",
        "Potassium and phosphorus are important for tuber development."
    ]

},


"Mustard": {

    soils:["Alluvial","Loamy","Sandy"],

    months:["October","November"],

    rainfall:["Low","Moderate"],

    irrigation:["Good","Moderate","Rainfed"],

    baseYield:1.4,

    yieldMin:0.8,

    yieldMax:2.4,

    waterDemand:0.35,

    climate:["semi-arid","subtropical"],

    advice:[
        "Avoid excessive waterlogging.",
        "Sulphur can be important for oilseed crops.",
        "Use balanced nitrogen and phosphorus according to soil-test recommendations."
    ]

},


"Cotton": {

    soils:["Black","Loamy","Alluvial"],

    months:["June","July"],

    rainfall:["Moderate","High"],

    irrigation:["Good","Moderate","Rainfed"],

    baseYield:1.8,

    yieldMin:1.0,

    yieldMax:3.0,

    waterDemand:0.65,

    climate:["semi-arid","tropical"],

    advice:[
        "Black soils can provide good moisture retention.",
        "Maintain balanced nutrition.",
        "Monitor water stress and drainage."
    ]

},


"Soybean": {

    soils:["Black","Loamy"],

    months:["June","July"],

    rainfall:["Moderate","High"],

    irrigation:["Rainfed","Moderate"],

    baseYield:1.6,

    yieldMin:0.9,

    yieldMax:2.7,

    waterDemand:0.55,

    climate:["semi-arid","sub-humid","tropical"],

    advice:[
        "Avoid prolonged waterlogging.",
        "Use appropriate phosphorus and potassium based on soil testing.",
        "Maintain good soil drainage."
    ]

},


"Groundnut": {

    soils:["Sandy","Loamy","Red"],

    months:["June","July","October"],

    rainfall:["Moderate","Low"],

    irrigation:["Good","Moderate","Rainfed"],

    baseYield:1.8,

    yieldMin:1.0,

    yieldMax:3.0,

    waterDemand:0.50,

    climate:["semi-arid","tropical"],

    advice:[
        "Well-drained soil is important.",
        "Calcium and sulphur may be important depending on soil condition.",
        "Avoid excessive waterlogging."
    ]

},


"Bajra": {

    soils:["Sandy","Loamy","Black"],

    months:["June","July"],

    rainfall:["Low","Moderate"],

    irrigation:["Rainfed","Limited","Moderate"],

    baseYield:1.7,

    yieldMin:0.9,

    yieldMax:2.8,

    waterDemand:0.25,

    climate:["arid","semi-arid","tropical"],

    advice:[
        "Suitable for relatively dry conditions.",
        "Use balanced nutrients according to soil testing.",
        "Avoid excessive irrigation."
    ]

},


"Ragi": {

    soils:["Red","Loamy"],

    months:["June","July","August"],

    rainfall:["Moderate","High"],

    irrigation:["Rainfed","Moderate"],

    baseYield:1.8,

    yieldMin:1.0,

    yieldMax:3.0,

    waterDemand:0.40,

    climate:["semi-arid","tropical"],

    advice:[
        "Red and well-drained soils are commonly suitable.",
        "Use organic matter where soil fertility is low.",
        "Balanced nitrogen and phosphorus management is recommended."
    ]

},


"Sugarcane": {

    soils:["Alluvial","Black","Loamy"],

    months:["January","February","September","October"],

    rainfall:["Moderate","High"],

    irrigation:["Good"],

    baseYield:70,

    yieldMin:40,

    yieldMax:110,

    waterDemand:0.95,

    climate:["tropical","subtropical","humid"],

    advice:[
        "Sugarcane requires substantial water availability.",
        "Use organic manure to improve soil condition.",
        "NPK management should be based on soil testing."
    ]

},


"Pulses": {

    soils:["Loamy","Black","Red","Alluvial"],

    months:["June","July","October","November"],

    rainfall:["Low","Moderate"],

    irrigation:["Rainfed","Limited","Moderate"],

    baseYield:1.2,

    yieldMin:0.6,

    yieldMax:2.0,

    waterDemand:0.30,

    climate:["semi-arid","subtropical","tropical"],

    advice:[
        "Avoid prolonged waterlogging.",
        "Use appropriate phosphorus based on soil testing.",
        "Maintain soil organic matter."
    ]

},


"Chickpea": {

    soils:["Black","Loamy","Alluvial"],

    months:["October","November"],

    rainfall:["Low","Moderate"],

    irrigation:["Rainfed","Moderate"],

    baseYield:1.3,

    yieldMin:0.7,

    yieldMax:2.2,

    waterDemand:0.30,

    climate:["semi-arid","subtropical"],

    advice:[
        "Cool and relatively dry conditions are generally preferred.",
        "Avoid excessive irrigation.",
        "Phosphorus management can be important."
    ]

},


"Sorghum": {

    soils:["Black","Red","Loamy"],

    months:["June","July","September"],

    rainfall:["Low","Moderate"],

    irrigation:["Rainfed","Limited","Moderate"],

    baseYield:1.5,

    yieldMin:0.8,

    yieldMax:2.6,

    waterDemand:0.30,

    climate:["semi-arid","tropical"],

    advice:[
        "Suitable for relatively dry regions.",
        "Maintain adequate soil fertility.",
        "Avoid waterlogging."
    ]

},


"Vegetables": {

    soils:["Loamy","Alluvial","Red","Sandy"],

    months:["January","February","March","June","July","October","November"],

    rainfall:["Moderate","High"],

    irrigation:["Good","Moderate"],

    baseYield:15,

    yieldMin:8,

    yieldMax:25,

    waterDemand:0.65,

    climate:["tropical","subtropical","humid"],

    advice:[
        "Well-drained fertile soil is preferred.",
        "Organic manure can improve soil structure.",
        "Use crop-specific nutrient recommendations."
    ]

},


"Jute": {

    soils:["Alluvial","Loamy"],

    months:["March","April","May"],

    rainfall:["High","Moderate"],

    irrigation:["Rainfed","Moderate"],

    baseYield:2.4,

    yieldMin:1.5,

    yieldMax:3.5,

    waterDemand:0.70,

    climate:["humid","subtropical","tropical"],

    advice:[
        "Warm and humid conditions are generally suitable.",
        "Maintain adequate moisture.",
        "Organic matter can improve soil condition."
    ]

},


"Chilli": {

    soils:["Black","Red","Loamy","Alluvial"],

    months:["June","July","September","October"],

    rainfall:["Moderate"],

    irrigation:["Good","Moderate"],

    baseYield:2.0,

    yieldMin:1.0,

    yieldMax:3.5,

    waterDemand:0.55,

    climate:["tropical","semi-arid"],

    advice:[
        "Avoid prolonged waterlogging.",
        "Use organic manure and balanced nutrients.",
        "Potassium management can be important for fruit development."
    ]

},


"Apple": {

    soils:["Mountain","Loamy"],

    months:["January","February","December"],

    rainfall:["Moderate","High"],

    irrigation:["Good","Moderate"],

    baseYield:10,

    yieldMin:5,

    yieldMax:18,

    waterDemand:0.55,

    climate:["temperate","mountain"],

    advice:[
        "Requires suitable cool and temperate conditions.",
        "Well-drained soil is preferred.",
        "Nutrient management should be based on soil and orchard testing."
    ]

},


"Tea": {

    soils:["Loamy","Laterite"],

    months:["March","April","May","June"],

    rainfall:["High","Very High"],

    irrigation:["Good","Moderate"],

    baseYield:2.0,

    yieldMin:1.0,

    yieldMax:3.5,

    waterDemand:0.75,

    climate:["humid","mountain","subtropical"],

    advice:[
        "Acidic, well-drained soils can be suitable.",
        "Organic matter management is important.",
        "Maintain adequate moisture without prolonged waterlogging."
    ]

},


"Coconut": {

    soils:["Sandy","Alluvial","Loamy"],

    months:["June","July","August"],

    rainfall:["High","Moderate"],

    irrigation:["Good","Moderate"],

    baseYield:8,

    yieldMin:4,

    yieldMax:14,

    waterDemand:0.80,

    climate:["humid","tropical"],

    advice:[
        "Adequate moisture is important.",
        "Well-drained soils are preferred.",
        "Organic manure can help maintain soil fertility."
    ]

},


"Banana": {

    soils:["Alluvial","Loamy","Red"],

    months:["June","July","August","September"],

    rainfall:["High","Moderate"],

    irrigation:["Good"],

    baseYield:35,

    yieldMin:20,

    yieldMax:50,

    waterDemand:0.85,

    climate:["humid","tropical"],

    advice:[
        "Banana requires adequate moisture and nutrients.",
        "Good drainage is important.",
        "Organic manure can improve soil fertility."
    ]

},


"Pepper": {

    soils:["Laterite","Loamy","Red"],

    months:["June","July"],

    rainfall:["High","Very High"],

    irrigation:["Good","Moderate"],

    baseYield:0.7,

    yieldMin:0.3,

    yieldMax:1.3,

    waterDemand:0.80,

    climate:["humid","tropical","mountain"],

    advice:[
        "Warm and humid conditions are generally suitable.",
        "Good drainage is important.",
        "Organic matter management can support plant growth."
    ]

},


"Cardamom": {

    soils:["Mountain","Loamy","Laterite"],

    months:["June","July","August"],

    rainfall:["High","Very High"],

    irrigation:["Good","Moderate"],

    baseYield:0.4,

    yieldMin:0.15,

    yieldMax:0.8,

    waterDemand:0.85,

    climate:["humid","mountain"],

    advice:[
        "Humid mountain conditions are generally preferred.",
        "Maintain soil organic matter.",
        "Avoid prolonged waterlogging."
    ]

},


"Ginger": {

    soils:["Loamy","Red","Laterite"],

    months:["April","May","June"],

    rainfall:["High","Moderate"],

    irrigation:["Good","Moderate"],

    baseYield:8,

    yieldMin:4,

    yieldMax:14,

    waterDemand:0.70,

    climate:["humid","tropical","subtropical"],

    advice:[
        "Loose and well-drained soil is preferred.",
        "Organic manure can improve soil structure.",
        "Avoid prolonged waterlogging."
    ]

}

};


/* =========================================================
   MONTH NUMBER
========================================================= */

const monthNumber = {

    January:1,
    February:2,
    March:3,
    April:4,
    May:5,
    June:6,
    July:7,
    August:8,
    September:9,
    October:10,
    November:11,
    December:12

};


/* =========================================================
   SELECT POPULATION
========================================================= */

const stateSelect =
    document.getElementById("state");


Object.keys(stateData).forEach(state => {

    const option =
        document.createElement("option");

    option.value = state;
    option.textContent = state;

    stateSelect.appendChild(option);

});


function loadCropOptions(preferred = []) {

    const cropSelect =
        document.getElementById("crop");

    const previousSelect =
        document.getElementById("previousCrop");


    cropSelect.innerHTML =
        '<option value="">Select Crop</option>';

    previousSelect.innerHTML =
        '<option value="">Select Previous Crop</option>';


    let crops =
        Object.keys(cropData);


    crops.sort((a,b) => {

        return preferred.includes(b) -
               preferred.includes(a);

    });


    crops.forEach(crop => {

        const option1 =
            document.createElement("option");

        option1.value = crop;
        option1.textContent = crop;

        cropSelect.appendChild(option1);


        const option2 =
            document.createElement("option");

        option2.value = crop;
        option2.textContent = crop;

        previousSelect.appendChild(option2);

    });

}


loadCropOptions();


stateSelect.addEventListener(
    "change",
    function() {

        const state = this.value;

        if (!state) {

            loadCropOptions();

            return;

        }

        loadCropOptions(
            stateData[state].crops
        );

    }
);


/* =========================================================
   UTILITY FUNCTIONS
========================================================= */

function clamp(value,min,max) {

    return Math.max(
        min,
        Math.min(max,value)
    );

}


function sigmoid(x) {

    return 1 / (1 + Math.exp(-x));

}


function gaussianDistance(value,ideal,tolerance) {

    return Math.exp(
        -Math.pow(
            (value - ideal) / tolerance,
            2
        )
    );

}


/* =========================================================
   FACTOR SCORE FUNCTIONS
========================================================= */

function soilScore(crop,soil) {

    if (
        crop.soils.includes(soil)
    ) {

        return 0.96;

    }

    return 0.30;

}


function monthScore(crop,month) {

    const selected =
        monthNumber[month];

    const valid =
        crop.months.map(
            m => monthNumber[m]
        );


    if (valid.includes(selected)) {

        return 1.0;

    }


    let nearest =
        Math.min(
            ...valid.map(
                x => Math.abs(x-selected)
            )
        );


    if (nearest === 1)
        return 0.72;

    if (nearest === 2)
        return 0.48;

    return 0.22;

}


function rainfallScore(crop,rainfall) {

    const level = {

        "Very Low":0.05,
        "Low":0.30,
        "Moderate":0.65,
        "High":0.88

    }[rainfall];


    const target = {

        "Very Low":0.05,
        "Low":0.30,
        "Moderate":0.65,
        "High":0.88

    };


    if (
        crop.rainfall.includes(rainfall)
    ) {

        return 0.96;

    }


    let best = 0;

    crop.rainfall.forEach(
        item => {

            best =
                Math.max(
                    best,
                    1 -
                    Math.abs(
                        level-target[item]
                    )
                );

        }
    );


    return clamp(best,0.15,0.72);

}


function irrigationScore(crop,irrigation) {

    if (
        crop.irrigation.includes(
            irrigation
        )
    ) {

        return 0.96;

    }


    const severity = {

        "Good":1,
        "Moderate":0.75,
        "Limited":0.45,
        "Rainfed":0.25

    }[irrigation];


    if (
        crop.waterDemand < 0.40
    ) {

        return clamp(
            0.55 + severity * 0.25,
            0.20,
            0.90
        );

    }


    if (
        crop.waterDemand > 0.80
    ) {

        return clamp(
            severity,
            0.15,
            0.90
        );

    }


    return clamp(
        0.40 + severity * 0.45,
        0.20,
        0.92
    );

}


function stateCropScore(state,cropName) {

    if (
        state.crops.includes(cropName)
    ) {

        return 0.96;

    }

    return 0.42;

}


function historicalScore(state) {

    return clamp(
        state.historicalIndex,
        0.55,
        0.95
    );

}


/* =========================================================
   CLIMATE COMPATIBILITY
========================================================= */

function climateScore(
    state,
    crop
) {

    const climate =
        state.climate.toLowerCase();


    let score = 0.55;


    crop.climate.forEach(
        type => {

            if (
                climate.includes(type)
            ) {

                score =
                    Math.max(
                        score,
                        0.93
                    );

            }

        }
    );


    if (
        climate.includes("humid") &&
        crop.waterDemand < 0.30
    ) {

        score -= 0.10;

    }


    if (
        climate.includes("arid") &&
        crop.waterDemand > 0.70
    ) {

        score -= 0.22;

    }


    if (
        climate.includes("mountain") &&
        crop.climate.includes("mountain")
    ) {

        score = 0.97;

    }


    return clamp(
        score,
        0.15,
        0.98
    );

}


/* =========================================================
   ROTATION SCORE
========================================================= */

function rotationScore(
    previous,
    selected
) {

    if (
        previous === selected
    ) {

        return 0.62;

    }


    const previousCrop =
        cropData[previous];

    const currentCrop =
        cropData[selected];


    if (
        !previousCrop ||
        !currentCrop
    ) {

        return 0.80;

    }


    /*
       Generic rotation diversity model.
       Different crop categories receive
       a positive diversification benefit.
    */

    const sameWaterProfile =
        Math.abs(
            previousCrop.waterDemand -
            currentCrop.waterDemand
        ) < 0.12;


    if (sameWaterProfile) {

        return 0.78;

    }


    return 0.91;

}


/* =========================================================
   INTERACTION EFFECTS

   This is what makes the model more sophisticated
   than simply adding independent points.
========================================================= */

function interactionAdjustment(
    state,
    crop,
    soil,
    rainfall,
    irrigation,
    month
) {

    let adjustment = 0;


    /* Good soil + suitable rainfall */

    if (
        crop.soils.includes(soil) &&
        crop.rainfall.includes(rainfall)
    ) {

        adjustment += 0.055;

    }


    /* Good soil + irrigation */

    if (
        crop.soils.includes(soil) &&
        crop.irrigation.includes(irrigation)
    ) {

        adjustment += 0.035;

    }


    /* High rainfall + poor drainage sensitive crops */

    if (
        rainfall === "High" &&
        crop.waterDemand < 0.30
    ) {

        adjustment -= 0.045;

    }


    /* Low rainfall + high water demand */

    if (
        rainfall === "Low" &&
        crop.waterDemand > 0.70
    ) {

        adjustment -= 0.085;

    }


    /* Very low rainfall */

    if (
        rainfall === "Very Low" &&
        crop.waterDemand > 0.40
    ) {

        adjustment -= 0.15;

    }


    /* Good irrigation can compensate partially */

    if (
        irrigation === "Good" &&
        crop.waterDemand > 0.70
    ) {

        adjustment += 0.055;

    }


    /* Rainfed crops under excessive irrigation */

    if (
        irrigation === "Good" &&
        crop.waterDemand < 0.35
    ) {

        adjustment -= 0.015;

    }


    /* State + crop relationship */

    if (
        state.crops.includes(
            Object.keys(cropData)
                .find(
                    key =>
                        cropData[key] === crop
                )
        )
    ) {

        adjustment += 0.035;

    }


    return clamp(
        adjustment,
        -0.25,
        0.15
    );

}


/* =========================================================
   MAIN PREDICTION MODEL
========================================================= */

function runPrediction(
    stateName,
    soil,
    month,
    previousCrop,
    cropName,
    irrigation,
    rainfall
) {


    const state =
        stateData[stateName];

    const crop =
        cropData[cropName];


    const factors = {


        soil:
            soilScore(
                crop,
                soil
            ),


        season:
            monthScore(
                crop,
                month
            ),


        rainfall:
            rainfallScore(
                crop,
                rainfall
            ),


        irrigation:
            irrigationScore(
                crop,
                irrigation
            ),


        state:
            stateCropScore(
                state,
                cropName
            ),


        climate:
            climateScore(
                state,
                crop
            ),


        rotation:
            rotationScore(
                previousCrop,
                cropName
            ),


        historical:
            historicalScore(
                state
            )

    };


    /*
       Weighted model.

       These weights sum to 1.
    */

    const weights = {

        soil:0.18,

        season:0.15,

        rainfall:0.16,

        irrigation:0.14,

        state:0.13,

        climate:0.10,

        rotation:0.06,

        historical:0.08

    };


    let weighted = 0;


    Object.keys(weights)
        .forEach(key => {

            weighted +=
                factors[key] *
                weights[key];

        });


    const interaction =
        interactionAdjustment(
            state,
            crop,
            soil,
            rainfall,
            irrigation,
            month
        );


    weighted += interaction;


    /*
       Logistic calibration.

       Converts the combined factor score
       into a probability-like suitability
       estimate rather than a simple sum.
    */

    const logit =
        (weighted - 0.56) * 8;


    let probability =
        sigmoid(logit);


    /*
       Historical stability affects
       the upper/lower confidence boundary.
    */

    const dataQuality =
        (
            factors.historical +
            factors.state +
            factors.climate
        ) / 3;


    const uncertainty =
        clamp(
            0.24 -
            dataQuality * 0.12 +
            Math.abs(
                0.65-weighted
            ) * 0.08,
            0.08,
            0.24
        );


    /*
       Keep output realistic.
    */

    probability =
        clamp(
            probability,
            0.18,
            0.95
        );


    const lower =
        clamp(
            probability - uncertainty,
            0.05,
            0.95
        );


    const upper =
        clamp(
            probability + uncertainty,
            0.05,
            0.98
        );


    /*
       Yield calculation.

       The base yield is adjusted using
       suitability and factor interactions.
    */

    let yieldMultiplier =
        0.58 +
        probability * 0.55;


    /*
       Strong irrigation can increase
       potential for high-water crops.
    */

    if (
        irrigation === "Good" &&
        crop.waterDemand > 0.65
    ) {

        yieldMultiplier += 0.08;

    }


    /*
       Rainfall mismatch reduces potential.
    */

    if (
        !crop.rainfall.includes(
            rainfall
        )
    ) {

        yieldMultiplier -= 0.10;

    }


    /*
       Soil mismatch reduces potential.
    */

    if (
        !crop.soils.includes(
            soil
        )
    ) {

        yieldMultiplier -= 0.10;

    }


    yieldMultiplier =
        clamp(
            yieldMultiplier,
            0.45,
            1.25
        );


    const predictedYield =
        crop.baseYield *
        yieldMultiplier;


    const yieldLow =
        Math.max(
            crop.yieldMin,
            predictedYield *
            (1 - uncertainty)
        );


    const yieldHigh =
        Math.min(
            crop.yieldMax,
            predictedYield *
            (1 + uncertainty)
        );


    return {

        probability,

        lower,

        upper,

        uncertainty,

        predictedYield,

        yieldLow,

        yieldHigh,

        factors,

        interaction

    };

}


/* =========================================================
   STATUS
========================================================= */

function getStatus(probability) {

    if (probability >= 0.80) {

        return {
            text:"✓ Highly Suitable",
            color:"#176b37"
        };

    }


    if (probability >= 0.65) {

        return {
            text:"✓ Suitable",
            color:"#2e8b57"
        };

    }


    if (probability >= 0.50) {

        return {
            text:"⚠ Moderately Suitable",
            color:"#b88600"
        };

    }


    return {
        text:"✕ Low Suitability",
        color:"#b23a3a"
    };

}


/* =========================================================
   YIELD POTENTIAL
========================================================= */

function getYieldPotential(
    probability
) {

    if (probability >= 0.82)
        return "High";

    if (probability >= 0.65)
        return "Moderate-High";

    if (probability >= 0.50)
        return "Moderate";

    if (probability >= 0.35)
        return "Low-Moderate";

    return "Low";

}


/* =========================================================
   CONFIDENCE
========================================================= */

function getConfidence(
    prediction
) {

    const spread =
        prediction.upper -
        prediction.lower;


    if (
        spread <= 0.22
    ) {

        return "High";

    }


    if (
        spread <= 0.32
    ) {

        return "Moderate";

    }


    return "Low";

}


/* =========================================================
   FACTOR LABELS
========================================================= */

const factorLabels = {

    soil:"Soil compatibility",

    season:"Sowing season",

    rainfall:"Rainfall compatibility",

    irrigation:"Irrigation availability",

    state:"State crop suitability",

    climate:"Climate compatibility",

    rotation:"Crop rotation",

    historical:"Historical stability proxy"

};


/* =========================================================
   FACTOR DISPLAY
========================================================= */

function displayFactors(
    prediction
) {

    const container =
        document.getElementById(
            "factorAnalysis"
        );


    container.innerHTML = "";


    const sorted =
        Object.entries(
            prediction.factors
        )
        .sort(
            (a,b) => b[1]-a[1]
        );


    sorted.forEach(
        ([key,value]) => {


            const percentage =
                Math.round(
                    value * 100
                );


            let cls =
                "factor-good";


            if (
                value < 0.55
            ) {

                cls =
                    "factor-bad";

            } else if (
                value < 0.72
            ) {

                cls =
                    "factor-medium";

            }


            const div =
                document.createElement(
                    "div"
                );


            div.className =
                "factor";


            div.innerHTML = `

                <div class="factor-top">

                    <span>
                        ${factorLabels[key]}
                    </span>

                    <span>
                        ${percentage}%
                    </span>

                </div>

                <div class="factor-bar">

                    <div
                        class="factor-fill ${cls}"
                        style="width:${percentage}%"
                    ></div>

                </div>

            `;


            container.appendChild(div);

        }
    );


    if (
        prediction.interaction !== 0
    ) {

        const interaction =
            document.createElement(
                "p"
            );


        interaction.className =
            "small";


        interaction.innerHTML =

            "<strong>Combined-condition adjustment:</strong> " +

            (
                prediction.interaction >= 0
                ? "+"
                : ""
            ) +

            Math.round(
                prediction.interaction * 100
            ) +

            "%";


        container.appendChild(
            interaction
        );

    }

}


/* =========================================================
   REASON GENERATOR
========================================================= */

function generateReasons(
    stateName,
    soil,
    month,
    previousCrop,
    cropName,
    irrigation,
    rainfall,
    prediction
) {

    const state =
        stateData[stateName];

    const crop =
        cropData[cropName];


    const reasons = [];


    if (
        crop.soils.includes(soil)
    ) {

        reasons.push(
            "The selected soil type matches the crop's preferred soil profile."
        );

    } else {

        reasons.push(
            "The selected soil is outside the crop's strongest soil profile."
        );

    }


    if (
        crop.months.includes(month)
    ) {

        reasons.push(
            "The selected month falls inside the crop's preferred sowing window."
        );

    } else {

        reasons.push(
            "The selected month is outside the crop's main sowing window."
        );

    }


    if (
        crop.rainfall.includes(
            rainfall
        )
    ) {

        reasons.push(
            "The expected rainfall category is compatible with the crop."
        );

    } else {

        reasons.push(
            "The expected rainfall differs from the crop's preferred rainfall conditions."
        );

    }


    if (
        crop.irrigation.includes(
            irrigation
        )
    ) {

        reasons.push(
            "The available irrigation level is compatible with the crop."
        );

    } else {

        reasons.push(
            "The available irrigation may limit the crop under these conditions."
        );

    }


    if (
        state.crops.includes(
            cropName
        )
    ) {

        reasons.push(
            cropName +
            " is represented as a major crop in the selected state's embedded agro-climatic profile."
        );

    } else {

        reasons.push(
            cropName +
            " is not represented among the major crops in the selected state's embedded profile."
        );

    }


    if (
        previousCrop === cropName
    ) {

        reasons.push(
            "The same crop was grown previously, so the model applies a crop-rotation penalty."
        );

    } else {

        reasons.push(
            "The proposed crop differs from the previous crop, reducing the rotation penalty."
        );

    }


    if (
        prediction.probability >= 0.80
    ) {

        reasons.push(
            "Multiple major factors align positively, resulting in a high suitability estimate."
        );

    } else if (
        prediction.probability >= 0.60
    ) {

        reasons.push(
            "Most major conditions are reasonably aligned, but some uncertainty remains."
        );

    } else {

        reasons.push(
            "Several important conditions are not fully aligned, reducing the estimated suitability."
        );

    }


    return reasons;

}


/* =========================================================
   MAIN CALCULATION
========================================================= */

function calculatePrediction() {


    const farmerName =
        document
        .getElementById("farmerName")
        .value
        .trim();


    const age =
        document
        .getElementById("age")
        .value;


    const state =
        document
        .getElementById("state")
        .value;


    const district =
        document
        .getElementById("district")
        .value
        .trim();


    const soil =
        document
        .getElementById("soil")
        .value;


    const month =
        document
        .getElementById("month")
        .value;


    const previousCrop =
        document
        .getElementById("previousCrop")
        .value;


    const crop =
        document
        .getElementById("crop")
        .value;


    const irrigation =
        document
        .getElementById("irrigation")
        .value;


    const rainfall =
        document
        .getElementById("rainfall")
        .value;


    if (
        !farmerName ||
        !age ||
        !state ||
        !district ||
        !soil ||
        !month ||
        !previousCrop ||
        !crop ||
        !irrigation ||
        !rainfall
    ) {

        alert(
            "Please complete all fields before checking the prediction."
        );

        return;

    }


    const prediction =
        runPrediction(
            state,
            soil,
            month,
            previousCrop,
            crop,
            irrigation,
            rainfall
        );


    const percentage =
        Math.round(
            prediction.probability *
            100
        );


    const lower =
        Math.round(
            prediction.lower *
            100
        );


    const upper =
        Math.round(
            prediction.upper *
            100
        );


    const status =
        getStatus(
            prediction.probability
        );


    const potential =
        getYieldPotential(
            prediction.probability
        );


    const confidence =
        getConfidence(
            prediction
        );


    /* SHOW RESULT */

    document
        .getElementById("result")
        .style.display = "block";


    document
        .getElementById("cropName")
        .textContent = crop;


    document
        .getElementById("score")
        .textContent =
            percentage + "%";


    document
        .getElementById("status")
        .textContent =
            status.text;


    document
        .getElementById("status")
        .style.color =
            status.color;


    document
        .getElementById("predictionSubtitle")
        .textContent =

        "Estimated suitability range: " +
        lower +
        "% – " +
        upper +
        "%";


    document
        .getElementById("confidence")
        .textContent =
            confidence;


    document
        .getElementById("yieldPotential")
        .textContent =
            potential;


    /* FARMER */

    document
        .getElementById("farmerInfo")
        .innerHTML =

        "<strong>Name:</strong> " +
        escapeHTML(farmerName) +

        "<br><strong>Age:</strong> " +
        escapeHTML(age);


    /* LOCATION */

    const stateInfo =
        stateData[state];


    document
        .getElementById("locationInfo")
        .innerHTML =

        "<strong>State:</strong> " +
        escapeHTML(state) +

        "<br><strong>District:</strong> " +
        escapeHTML(district) +

        "<br><strong>Agro-climatic zone:</strong> " +
        escapeHTML(
            stateInfo.zone
        );


    /* CLIMATE */

    document
        .getElementById("climateInfo")
        .innerHTML =

        escapeHTML(
            stateInfo.climate
        ) +

        "<br><br>" +

        "<strong>Typical rainfall:</strong> " +

        escapeHTML(
            stateInfo.rainfall
        );


    /* SOIL */

    document
        .getElementById("soilInfo")
        .innerHTML =

        "<strong>Selected:</strong> " +

        escapeHTML(soil) +

        "<br><strong>Common regional soils:</strong> " +

        stateInfo.soils
        .map(
            s => escapeHTML(s)
        )
        .join(", ");


    /* SOWING */

    const cropInfo =
        cropData[crop];


    document
        .getElementById("sowingInfo")
        .innerHTML =

        "<strong>" +
        escapeHTML(crop) +
        ":</strong> " +

        cropInfo.months
        .map(
            m => escapeHTML(m)
        )
        .join(", ");


    /* YIELD */

    const unit =
        (
            crop === "Potato" ||
            crop === "Sugarcane" ||
            crop === "Vegetables" ||
            crop === "Banana" ||
            crop === "Coconut" ||
            crop === "Ginger" ||
            crop === "Apple"
        )
        ? "tonnes/ha"
        : "tonnes/ha";


    document
        .getElementById("yieldInfo")
        .innerHTML =

        "<strong>Estimated:</strong> " +

        prediction
        .predictedYield
        .toFixed(2) +

        " " + unit +

        "<br><strong>Estimated range:</strong> " +

        prediction
        .yieldLow
        .toFixed(2) +

        " – " +

        prediction
        .yieldHigh
        .toFixed(2) +

        " " + unit;


    /* FACTORS */

    displayFactors(
        prediction
    );


    /* ADVICE */

    let adviceHTML =
        "<ul>";


    cropInfo.advice.forEach(
        advice => {

            adviceHTML +=

                "<li>" +
                escapeHTML(advice) +
                "</li>";

        }
    );


    adviceHTML +=
        "</ul>";


    document
        .getElementById(
            "nutrientAdvice"
        )
        .innerHTML =
            adviceHTML;


    /* REASONS */

    const reasons =
        generateReasons(
            state,
            soil,
            month,
            previousCrop,
            crop,
            irrigation,
            rainfall,
            prediction
        );


    const reasonList =
        document
        .getElementById(
            "reasonList"
        );


    reasonList.innerHTML = "";


    reasons.forEach(
        reason => {

            const li =
                document.createElement(
                    "li"
                );

            li.textContent =
                reason;

            reasonList.appendChild(
                li
            );

        }
    );


    /* ALTERNATIVES */

    generateAlternatives(
        state,
        soil,
        month,
        rainfall,
        irrigation,
        crop
    );


    /* SCROLL */

    document
        .getElementById("result")
        .scrollIntoView({
            behavior:"smooth"
        });

}


/* =========================================================
   ALTERNATIVE CROPS

   Uses the same prediction engine instead of
   the old simple 50-point formula.
========================================================= */

function generateAlternatives(
    stateName,
    soil,
    month,
    rainfall,
    irrigation,
    selectedCrop
) {


    const state =
        stateData[stateName];


    const container =
        document.getElementById(
            "alternatives"
        );


    let alternatives = [];


    state.crops.forEach(
        cropName => {


            if (
                !cropData[cropName] ||
                cropName === selectedCrop
            ) {

                return;

            }


            const prediction =
                runPrediction(
                    stateName,
                    soil,
                    month,
                    selectedCrop,
                    cropName,
                    irrigation,
                    rainfall
                );


            alternatives.push({

                crop:cropName,

                score:
                    Math.round(
                        prediction.probability *
                        100
                    )

            });

        }
    );


    /*
       If the state's own crops are insufficient,
       evaluate all crops as additional alternatives.
    */

    if (
        alternatives.length < 3
    ) {

        Object.keys(cropData)
        .forEach(
            cropName => {

                if (
                    cropName ===
                    selectedCrop
                ) {

                    return;

                }


                if (
                    alternatives
                    .some(
                        x =>
                            x.crop ===
                            cropName
                    )
                ) {

                    return;

                }


                const prediction =
                    runPrediction(
                        stateName,
                        soil,
                        month,
                        selectedCrop,
                        cropName,
                        irrigation,
                        rainfall
                    );


                alternatives.push({

                    crop:cropName,

                    score:
                        Math.round(
                            prediction.probability *
                            100
                        )

                });

            }
        );

    }


    alternatives.sort(
        (a,b) =>
            b.score -
            a.score
    );


    container.innerHTML = "";


    alternatives
        .slice(0,5)
        .forEach(
            item => {


                const div =
                    document.createElement(
                        "div"
                    );


                div.className =
                    "crop-card";


                div.innerHTML = `

                    <strong>
                        ${escapeHTML(item.crop)}
                    </strong>

                    <span class="crop-score">
                        ${item.score}%
                    </span>

                    <div class="bar">

                        <div
                            class="bar-fill"
                            style="width:${item.score}%"
                        ></div>

                    </div>

                `;


                container.appendChild(
                    div
                );

            }
        );

}


/* =========================================================
   HTML ESCAPING
========================================================= */

function escapeHTML(value) {

    return String(value)

        .replace(
            /&/g,
            "&amp;"
        )

        .replace(
            /</g,
            "&lt;"
        )

        .replace(
            />/g,
            "&gt;"
        )

        .replace(
            /"/g,
            "&quot;"
        )

        .replace(
            /'/g,
            "&#039;"
        );

}

</script>

</body>

</html>
