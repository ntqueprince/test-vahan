<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SHIVANG</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      padding: 20px;
      background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%); /* हल्का नीला ग्रेडिएंट */
      text-align: center;
      margin: 0;
      min-height: 100vh;
    }
    h2, h3 {
      color: #1a237e;
      font-weight: 600;
    }
    h2 {
      font-size: 3em; /* फॉन्ट साइज़ को 3em कर दिया गया है */
      letter-spacing: 1px;
    }
    h3 {
      font-size: 1.5em;
    }
    .upload-section {
      margin-top: 100px; /* Adjusted margin-top to push it further down */
      margin-bottom: 20px;
      background: rgba(255, 255, 255, 0.9);
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }
    input[type="file"], input[type="text"], button {
      padding: 12px;
      margin: 8px;
      font-size: 16px;
      border-radius: 8px;
      border: 1px solid #b0bec5;
      width: 80%;
      max-width: 300px;
      box-sizing: border-box;
      transition: all 0.3s ease;
    }
    input[type="text"]:focus, input[type="file"]:focus {
      border-color: #3f51b5;
      box-shadow: 0 0 8px rgba(63, 81, 181, 0.3);
      outline: none;
    }
    button {
      background-color: #ADD8E6 !important; /* हल्का नीला बैकग्राउंड कलर */
      color: white;
      border: none;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
    }
    button:hover {
      background-color: #87CEEB !important; /* गहरा नीला ऑन होवर */
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateY(-2px);
    }
    .progress-container {
      width: 80%;
      max-width: 300px;
      margin: 10px auto;
    }
    .progress-bar {
      width: 100%;
      background-color: #eceff1;
      border-radius: 8px;
      overflow: hidden;
    }
    .progress {
      width: 0%;
      height: 20px;
      background: linear-gradient(90deg, #3f51b5, #5c6bc0);
      text-align: center;
      line-height: 20px;
      color: white;
      font-weight: 400;
      transition: width 0.3s ease;
    }
    .status {
      margin-top: 5px;
      font-size: 14px;
      color: #455a64;
      font-weight: 400;
    }
    #gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
      justify-items: center;
      padding: 10px;
    }
    .image-container {
      background: white;
      padding: 10px;
      border-radius: 12px;
      box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
      text-align: center;
      transition: all 0.3s ease;
      max-width: 200px;
    }
    .image-container:hover {
      transform: translateY(-5px);
      box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
    }
    #gallery img {
      max-width: 100%;
      height: 150px;
      object-fit: cover;
      border-radius: 8px;
      border: 2px solid #e0e0e0;
    }
    .tag {
      margin: 5px 0;
      font-size: 16px;
      font-weight: 500;
      color: #37474f;
    }
    .download-btn {
      background-color: #ff5722;
      color: white;
      padding: 8px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 5px;
      font-size: 14px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
    }
    .download-btn:hover {
      background-color: #e64a19;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateY(-2px);
    }
    /* Popup Styles for Tag Modal */
    .modal {
      display: none;
      position: fixed;
      z-index: 1;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.6);
      justify-content: center;
      align-items: center;
    }
    .modal-content {
      background-color: white;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
      width: 90%;
      max-width: 400px;
      text-align: center;
      border: 2px solid #3f51b5;
    }
    .modal-content h4 {
      margin: 0 0 15px;
      color: #d32f2f;
      font-weight: 500;
    }
    .modal-content input[type="text"] {
      width: 100%;
      padding: 10px;
      margin-bottom: 15px;
      border: 1px solid #b0bec5;
      border-radius: 8px;
      transition: all 0.3s ease;
    }
    .modal-content input[type="text"]:focus {
      border-color: #3f51b5;
      box-shadow: 0 0 8px rgba(63, 81, 181, 0.3);
      outline: none;
    }
    .modal-content button {
      padding: 10px 20px;
      margin: 5px;
      border-radius: 8px;
      cursor: pointer;
    }
    .modal-content .upload-btn {
      background-color: #ADD8E6 !important; /* हल्का नीला बैकग्राउंड कलर */
      color: white;
      border: none;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }
    .modal-content .upload-btn:hover {
      background-color: #87CEEB !important; /* गहरा नीला ऑन होवर */
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    .modal-content .cancel-btn {
      background-color: #f44336;
      color: white;
      border: none;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }
    .modal-content .cancel-btn:hover {
      background-color: #d32f2f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    .modal-progress-container {
      width: 100%;
      margin: 10px 0;
      display: none;
    }
    .modal-progress-bar {
      width: 100%;
      background-color: #eceff1;
      border-radius: 8px;
      overflow: hidden;
    }
    .modal-progress {
      width: 0%;
      height: 20px;
      background: linear-gradient(90deg, #3f51b5, #5c6bc0);
      text-align: center;
      line-height: 20px;
      color: white;
      font-weight: 400;
      transition: width 0.3s ease;
    }
    /* CSAT Calculator Modal Styles */
    .csat-modal {
      display: none;
      position: fixed;
      z-index: 2;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.6);
      justify-content: center;
      align-items: center;
    }
    .csat-modal-content {
      background-color: white;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
      width: 90%;
      max-width: 400px;
      text-align: center;
      border: 2px solid #3f51b5;
    }
    .csat-modal-content h4 {
      color: #1a237e;
      font-weight: 600;
      margin-bottom: 15px;
    }
    .csat-modal-content .input-section {
      margin-bottom: 15px;
    }
    .csat-modal-content label {
      display: block;
      font-size: 1em;
      color: #37474f;
      margin-bottom: 5px;
    }
    .csat-modal-content input, .csat-modal-content select {
      padding: 10px;
      font-size: 1em;
      border-radius: 8px;
      border: 1px solid #b0bec5;
      width: 100%;
      max-width: 200px;
      box-sizing: border-box;
      transition: all 0.3s ease;
    }
    .csat-modal-content input:focus, .csat-modal-content select:focus {
      border-color: #3f51b5;
      box-shadow: 0 0 8px rgba(63, 81, 181, 0.3);
      outline: none;
    }
    .csat-modal-content .good-section {
      background: #c8e6c9;
      padding: 10px;
      border-radius: 8px;
    }
    .csat-modal-content .bad-section {
      background: #ffcdd2;
      padding: 10px;
      border-radius: 8px;
    }
    .csat-modal-content .result-section {
      margin-top: 15px;
      padding: 10px;
      background: #eceff1;
      border-radius: 8px;
    }
    .csat-modal-content .result-section p {
      margin: 5px 0;
      font-size: 0.9em;
      color: #455a64;
    }
    .csat-modal-content .success {
      color: #2e7d32;
      font-weight: 500;
      padding: 5px;
      border-radius: 4px;
      background: rgba(200, 230, 201, 0.3);
    }
    .csat-modal-content .error {
      color: #c62828;
      font-weight: 600;
      font-size: 1em;
      padding: 5px;
      border-radius: 4px;
      background: rgba(255, 205, 210, 0.3);
      display: inline-block;
    }
    .csat-modal-content .button-group { /* Added for button alignment */
      display: flex;
      justify-content: center;
      gap: 10px; /* Space between buttons */
      margin-top: 15px;
    }
    .csat-modal-content .close-btn, .csat-modal-content .calculate-btn {
      flex: 1; /* Make buttons take equal width */
      max-width: 150px; /* Limit max width for larger screens */
      padding: 10px 20px;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
      margin: 0 !important; /* Remove individual margins */
    }
    .csat-modal-content .close-btn {
      background-color: #f44336;
      color: white;
      border: none;
    }
    .csat-modal-content .close-btn:hover {
      background-color: #d32f2f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    .csat-modal-content .calculate-btn {
      background-color: #3f51b5;
      color: white;
      border: none;
    }
    .csat-modal-content .calculate-btn:hover {
      background-color: #303f9f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    /* Fixed Buttons */
    .csat-btn, .endorsement-btn, .manual-vi-btn-fixed, .claim-nstp-btn-fixed {
      position: fixed;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
      font-size: 0.9em;
      background-color: #FF4500; /* OrangeRed */
    }

    .csat-btn:hover, .endorsement-btn:hover, .manual-vi-btn-fixed:hover, .claim-nstp-btn-fixed:hover {
      background-color: #E63900; /* Darker OrangeRed on hover */
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateY(-2px);
    }

    /* CSAT and Claim Count buttons */
    .csat-btn {
      top: 10px;
      left: 10px;
    }
    .claim-nstp-btn-fixed {
      top: 60px; /* Positioned below CSAT button */
      left: 10px;
    }

    /* Endorsement and Manual VI buttons */
    .endorsement-btn {
      top: 10px;
      right: 10px;
    }
    .manual-vi-btn-fixed {
        top: 60px; /* Positioned below endorsement button */
        right: 10px; /* Aligned with endorsement button */
    }

    /* ENDORSEMENT Full-Page Widget Styles */
    .endorsement-page {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%); /* हल्का नीला ग्रेडिएंट */
      z-index: 1000;
      padding: 0; /* Removed padding to make it truly full-page */
      margin: 0; /* Ensure no margins */
      box-sizing: border-box;
      font-family: 'Roboto', sans-serif;
    }
    .endorsement-container {
      width: 100%;
      max-width: 600px;
      margin: 0 auto;
      background: #ffffff;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
      transition: transform 0.3s ease, opacity 0.3s ease;
      transform: scale(0.9);
      opacity: 0;
      position: relative;
      top: 50%;
      transform: translateY(-50%); /* Center vertically */
    }
    .endorsement-container.active {
      transform: scale(1) translateY(-50%); /* Adjust transform to include centering */
      opacity: 1;
    }
    .endorsement-container h1 {
      text-align: center;
      color: #1a237e;
      font-size: 1.8em;
      font-weight: 700;
      margin-bottom: 8px;
    }
    .created-by {
      text-align: center;
      font-size: 0.8em;
      margin-bottom: 15px;
      background: linear-gradient(90deg, #3f51b5, #e91e63);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      animation: fadeIn 1.5s ease-in-out;
    }
    @keyframes fadeIn {
      0% { opacity: 0; transform: translateY(10px); }
      100% { opacity: 1; transform: translateY(0); }
    }
    .endorsement-container label {
      display: block;
      color: #263238;
      font-size: 1em;
      font-weight: 500;
      margin: 10px 0 6px;
    }
    .PB_DROPDOWN {
      width: 100%;
      padding: 10px;
      border: 2px solid #b0bec5;
      border-radius: 8px;
      font-size: 0.95em;
      font-family: Arial, Helvetica, sans-serif; /* Changed to fix BAJAJ rendering */
      background: #fafafa;
      transition: border-color 0.3s ease, box-shadow 0.3s ease;
      cursor: pointer;
      height: 40px; /* Fixed height to prevent extra space */
      appearance: none; /* Remove default browser styling */
      -webkit-appearance: none;
      -moz-appearance: none;
      background-image: url('data:image/svg+xml;utf8,<svg fill="black" height="24" viewBox="0 0 24 24" width="24" xmlns="http://www.w3.org/2000/svg"><path d="M7 10l5 5 5-5z"/></svg>'); /* Custom dropdown arrow */
      background-repeat: no-repeat;
      background-position: right 10px center;
    }
    .PB_DROPDOWN:focus {
      outline: none;
      border-color: #3f51b5;
      box-shadow: 0 0 8px rgba(63, 81, 181, 0.3);
    }
    .PB_DROPDOWN:hover {
      border-color: #3f51b5;
    }
    .output {
      background: #e3f2fd;
      padding: 15px;
      border-radius: 10px;
      margin-top: 15px;
      font-size: 1em;
      font-weight: 500;
      line-height: 1.6;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
      border: 1px solid #bbdefb;
      transform: scale(0.95);
      opacity: 0;
      transition: transform 0.3s ease, opacity 0.3s ease;
    }
    .output.show {
      transform: scale(1);
      opacity: 1;
    }
    .output.output-red {
      background: #f8d7da;
      border: 1px solid #f5c6cb;
    }
    .output div {
      margin-bottom: 8px;
    }
    .label {
      color: #1565c0;
      font-weight: 700;
      margin-right: 8px;
    }
    .output-red .label {
      color: #721c24;
    }
    .value {
      color: #263238;
    }
    .back-btn {
      background-color: #f44336;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
      margin-top: 15px;
      display: block;
      margin-left: auto;
      margin-right: auto;
    }
    .back-btn:hover {
      background-color: #d32f2f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateY(-2px);
    }
    /* Styles for Manual VI Page */
    .manual-vi-page {
      display: none; /* Hidden by default */
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%); /* हल्का नीला ग्रेडिएंट */
      z-index: 1000;
      padding: 20px;
      box-sizing: border-box;
      text-align: center;
      overflow-y: auto; /* Make content scrollable */
    }
    .manual-vi-page .card {
        margin-top: 10px; /* Consistent margin */
    }
    .manual-vi-page .card-header {
      background-color: #343a40 !important; /* Dark background for header */
      color: white !important; /* White text for header */
      padding: 10px 15px;
      border-top-left-radius: 15px;
      border-top-right-radius: 15px;
      font-weight: 600;
    }
    .manual-vi-page .card-body {
      padding: 20px;
    }
    .manual-vi-page ul {
      list-style-type: disc; /* Ensure bullet points are visible */
      padding-left: 20px;
      text-align: left; /* Align text to the left within the lists */
    }

    /* Styles for Claim Count & NSTP Page */
    .claim-nstp-page {
      display: none; /* Hidden by default */
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%); /* हल्का नीला ग्रेडिएंट */
      z-index: 1000;
      padding: 20px;
      padding-top: 20px; /* Adjusted padding-top as no fixed button at top now */
      box-sizing: border-box;
      text-align: center;
      overflow-y: auto; /* Make content scrollable */
    }
    /* Removed .claim-nstp-page .back-to-home-btn styles as the button is removed */
    
    /* Table styles for claim-nstp-page */
    .claim-nstp-page table {
        width: 100%;
        margin-top: 20px;
        border-collapse: collapse;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        border-radius: 12px;
        overflow: hidden; /* Ensures rounded corners are applied to table content */
    }
    .claim-nstp-page th, .claim-nstp-page td {
        padding: 12px 15px;
        text-align: left;
        border-bottom: 1px solid #ddd;
    }
    .claim-nstp-page th {
        background-color: #3f51b5;
        color: white;
        font-weight: 600;
        text-transform: uppercase;
        letter-spacing: 0.05em;
        white-space: nowrap; /* Prevent wrapping for headers */
    }
    .claim-nstp-page td {
      white-space: nowrap; /* Prevent wrapping for cell content */
    }
    .claim-nstp-page tr:nth-child(odd) {
        background-color: #f8faff;
    }
    .claim-nstp-page tr:nth-child(even) {
        background-color: #eef2ff;
    }
    .claim-nstp-page tr:hover {
        background-color: #dbe0ff;
        transform: translateY(-2px);
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
        transition: all 0.2s ease-in-out;
    }
    .claim-nstp-page .positive {
        color: #2e7d32;
        font-weight: 500;
    }
    .claim-nstp-page .negative {
        color: #c62828;
        font-weight: 500;
    }
    .claim-nstp-page .neutral {
        color: #455a64;
    }

    @media (max-width: 600px) {
      input[type="file"], input[type="text"], button {
        width: 90%;
        font-size: 14px;
        padding: 10px;
      }
      .progress-container {
        width: 90%;
      }
      #gallery {
        grid-template-columns: 1fr;
      }
      .image-container {
        padding: 8px;
        max-width: 100%;
      }
      h2, h3 {
        font-size: 1.2em;
      }
      .modal-content, .csat-modal-content {
        width: 80%;
        padding: 15px;
      }
      /* Hide all fixed buttons on mobile */
      .csat-btn,
      .endorsement-btn,
      .manual-vi-btn-fixed,
      .claim-nstp-btn-fixed {
        display: none;
      }
      .csat-modal-content .error {
        font-size: 0.85em;
        padding: 4px;
      }
      .csat-modal-content .success {
        font-size: 0.85em;
        padding: 4px;
      }
      .csat-modal-content .result-section p {
        font-size: 0.8em;
      }
      .endorsement-container {
        width: 90vw;
        padding: 15px;
      }
      .endorsement-container h1 {
        font-size: 1.5em;
      }
      .PB_DROPDOWN {
        font-size: 0.9em;
        height: 36px; /* Adjusted for mobile */
      }
      .output {
        font-size: 0.95em;
      }
      .created-by {
        font-size: 0.7em;
      }
      .manual-vi-page {
        padding-top: 20px; /* Consistent padding for mobile */
      }
      .manual-vi-page .card {
        margin-top: 10px; /* Consistent margin for mobile */
      }
      .claim-nstp-page {
        padding-top: 20px; /* Adjusted padding-top for mobile - removed space for fixed button */
      }
      /* Removed .claim-nstp-page .back-to-home-btn styles for mobile as button is removed */
      .claim-nstp-page table {
        margin-top: 10px;
      }
    }
  </style>
</head>
<body>
  <!-- Fixed buttons are hidden on mobile using CSS in media query -->
  <button class="csat-btn" onclick="openCSATModal()">CSAT Calculator</button>

  <button class="claim-nstp-btn-fixed" onclick="openClaimNSTPPage()">Claim_Count & NSTP</button>

  <button class="endorsement-btn" onclick="openEndorsementPage()">ENDORSEMENT</button>

  <button class="manual-vi-btn-fixed" onclick="openManualVIPage()">MANUAL-VI</button>

  <h2 id="mainHeader"></h2> <!-- 📷SHIVANG टेक्स्ट को हटा दिया गया है -->
  <div class="upload-section">
    <input type="file" id="fileUpload" accept="image/*">
    <input type="text" id="tagInput" placeholder="Enter tag (e.g., SHIVANG)">
    <button onclick="uploadImage()">Upload</button>
    <div class="progress-container">
      <div class="progress-bar">
        <div class="progress" id="progress">0%</div>
      </div>
      <div class="status" id="status">Ready</div>
    </div>
  </div>

  <h3>Uploaded Images</h3>
  <div id="gallery"></div>

  <div id="tagModal" class="modal">
    <div class="modal-content">
      <h4>Error: Tag is required!</h4>
      <input type="text" id="modalTagInput" placeholder="Enter tag (e.g., SHIVANG)">
      <button class="upload-btn" onclick="submitTag()">Upload</button>
      <button class="cancel-btn" onclick="closeModal()">Cancel</button>
      <div class="modal-progress-container" id="modalProgressContainer">
        <div class="modal-progress-bar">
          <div class="modal-progress" id="modalProgress">0%</div>
        </div>
      </div>
    </div>
  </div>

  <div id="csatModal" class="csat-modal">
    <div class="csat-modal-content">
      <h4>CSAT Calculator</h4>
      <div class="input-section good-section">
        <label>Good Count:</label>
        <input type="number" id="goodCount" min="0" value="0">
      </div>
      <div class="input-section bad-section">
        <label>Bad Count:</label>
        <input type="number" id="badCount" min="0" value="0">
      </div>
      <div class="input-section">
        <label>Required CSAT (%):</label>
        <select id="requiredCSAT">
          <option value="70">70%+</option>
          <option value="71">71%+</option>
          <option value="72">72%+</option>
          <option value="73">73%+</option>
          <option value="74">74%+</option>
          <option value="75">75%+</option>
          <option value="76">76%+</option>
          <option value="77">77%+</option>
          <option value="78">78%+</option>
          <option value="79">79%+</option>
          <option value="80">80%+</option>
          <option value="81">81%+</option>
          <option value="82">82%+</option>
          <option value="83">83%+</option>
          <option value="84">84%+</option>
          <option value="85">85%+</option>
          <option value="86">86%+</option>
          <option value="87">87%+</option>
          <option value="88">88%+</option>
          <option value="89">89%+</option>
          <option value="90">90%+</option>
          <option value="91">91%+</option>
          <option value="92">92%+</option>
          <option value="93">93%+</option>
          <option value="94">94%+</option>
          <option value="95">95%+</option>
          <option value="96">96%+</option>
          <option value="97">97%+</option>
          <option value="98">98%+</option>
          <option value="99">99%+</option>
          <option value="100">100%+</option>
        </select>
      </div>
      <div class="result-section" id="csatResult">
        <p>Total: 0</p>
        <p>CSAT: 0%</p>
        <p id="csatStatus">Enter counts to see status</p>
      </div>
      <div class="button-group"> <!-- Added button-group div -->
        <button class="close-btn" onclick="closeCSATModal()">Close</button>
        <button class="calculate-btn" id="calculateButton" onclick="calculateCSAT()">Calculate</button>
      </div>
    </div>
  </div>

  <div class="endorsement-page" id="endorsementPage">
    <div class="endorsement-container">
      <h1>ENDORSEMENT</h1>
      <div class="created-by">Created by Shivang</div>
      <button class="back-btn" onclick="closeEndorsementPage()">Back to Main Page</button>
      <label for="insurer">Select Insurance Company:</label>
      <select id="insurer" class="PB_DROPDOWN">
        <option disabled selected>Select Insurer</option>
      </select>
      <label for="requirement">Select Requirement:</label>
      <select id="requirement" class="PB_DROPDOWN" disabled>
        <option disabled selected>Select Requirement</option>
      </select>
      <div id="output" class="output"></div>
    </div>
  </div>

  <div class="manual-vi-page" id="manualVIPage">
    <div class="card mt-4">
      <div class="card-header bg-dark text-white d-flex justify-content-between align-items-center">
        </div>
      <div class="card-body">
        <div class="mb-3 p-3 rounded" style="background-color: #e3f2fd;">
          <strong>ADP Home Visit Cities: 42</strong>
          <ul class="mb-0" style="columns: 2;">
            <li>Aligarh</li><li>Alwar</li><li>Ambala</li><li>Amritsar</li><li>Belgaum</li>
            <li>Bhiwani</li><li>Bhubaneshwar</li><li>Bilaspur</li><li>Coimbatore</li><li>Dhanbad</li>
            <li>Guwahati</li><li>Haldwani</li><li>Haridwar</li><li>Indore</li><li>Jalandhar</li>
            <li>Jamshedpur</li><li>Jhajjar</li><li>Jhansi</li><li>Jind</li><li>Jodhpur</li>
            <li>Kangra</li><li>Madurai</li><li>Mathura</li><li>Moradabad</li><li>Muzaffarnagar</li>
            <li>Mysore</li><li>Nagpur</li><li>Panipat</li><li>Pondicherry</li><li>Raipur</li>
            <li>Rajkot</li><li>Rewa</li><li>Rewari</li><li>Rohtak</li><li>Satara</li>
            <li>Shimla</li><li>Surat</li><li>Thiruvananthapuram</li><li>Thrissar</li><li>Udaipur</li>
            <li>Varanasi</li><li>Yamuna Nagar</li>
          </ul>
        </div>
        <div class="mb-3 p-3 rounded" style="background-color: #d0f0c0;">
          <strong>Manual Home Visit Cities: 14</strong>
          <ul class="mb-0" style="columns: 2;">
            <li>Ahmedabad</li><li>Bangalore</li><li>Chennai</li><li>Delhi</li><li>Faridabad</li>
            <li>Ghaziabad</li><li>Gurgaon</li><li>Hyderabad</li><li>Kolkata</li><li>Mumbai</li>
            <li>Noida & Greater Noida</li><li>Patna</li><li>Pune</li><li>Thane & Navi Mumbai</li>
          </ul>
        </div>
      </div>
    </div>
  </div>

  <div class="claim-nstp-page" id="claimNSTPPage">
    <h2 class="text-4xl font-bold text-center mb-6 text-indigo-800 tracking-tight">Claim Count & NSTP Details</h2>
    <div class="created-by">Created by Shivang</div>
    <div class="container mx-auto p-4 bg-white rounded-2xl shadow-2xl max-w-7xl w-full border-4 border-transparent bg-clip-border bg-gradient-to-r from-blue-500 via-purple-500 to-pink-500">
        <div class="mb-4">
            <input type="text" id="claimNstpSearchInput" placeholder="Search by Insurer Name..." class="search-input w-full p-3 text-lg border-2 border-blue-500 rounded-lg shadow-md focus:outline-none focus:ring-4 focus:ring-pink-500 bg-blue-50 text-gray-800 placeholder-gray-500">
        </div>
        <div class="overflow-x-auto rounded-lg" id="claimNstpTableContainer">
            <table id="claimNstpTable" class="w-full bg-white border border-gray-300">
                <thead class="bg-gradient-to-r from-blue-600 via-purple-600 to-pink-600 text-white text-lg font-semibold">
                    <tr>
                        <th class="table-header p-2 text-left" data-column="insurer_name">Insurer Name</th>
                        <th class="table-header p-2 text-left" data-column="zd_claims_year">ZD Claims/Year</th>
                        <th class="table-header p-2 text-left" data-column="non_zd_claims_year">Non-ZD Claims/Year</th>
                        <th class="table-header p-2 text-left" data-column="commercial">Commercial</th>
                        <th class="table-header p-2 text-left" data-column="video_approval">Video Approval</th>
                        <th class="table-header p-2 text-left" data-column="video_tat">Video TAT</th>
                        <th class="table-header p-2 text-left" data-column="short_partial">Short Partial</th>
                        <th class="table-header p-2 text-left" data-column="artificial_low_lighting">Artificial Low Lighting</th>
                        <th class="table-header p-2 text-left" data-column="scar_declaration">Scar Declaration</th>
                        <th class="table-header p-2 text-left" data-column="brand_new_3_3">Brand New 3+3</th>
                        <th class="table-header p-2 text-left" data-column="old_3_3">Old 3+3</th>
                    </tr>
                </thead>
                <tbody id="claimNstpTableBody" class="text-gray-800 text-base">
                    <!-- Data will be populated by JavaScript -->
                </tbody>
            </table>
        </div>
    </div>
  </div>

  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.14.1/firebase-app.js";
    import { getDatabase, ref, push, onValue, remove, serverTimestamp } from "https://www.gstatic.com/firebasejs/10.14.1/firebase-database.js";

    const firebaseConfig = {
      apiKey: "AIzaSyCIfleywEbd1rcjymkfEfFYxPpvYdZHGhk",
      authDomain: "cvang-vahan.firebaseapp.com",
      databaseURL: "https://cvang-vahan-default-rtdb.firebaseio.com",
      projectId: "cvang-vahan",
      storageBucket: "cvang-vahan.appspot.com",
      messagingSenderId: "117318825099",
      appId: "1:117318825099:web:afc0e2f863117cb14bfc"
    };

    const app = initializeApp(firebaseConfig);
    const db = getDatabase(app);
    const imagesRef = ref(db, 'images');

    const cloudName = 'di83mshki';
    const uploadPreset = 'anonymous_upload';

    let selectedFile = null;
    let hasCalculated = false;

    window.uploadImage = function() {
      const file = document.getElementById('fileUpload').files[0];
      const tag = document.getElementById('tagInput').value.trim();
      const progressBar = document.getElementById('progress');
      const status = document.getElementById('status');

      if (!file) {
        alert("कृपया एक फोटो चुनें।");
        return;
      }

      if (!tag) {
        selectedFile = file;
        document.getElementById('tagModal').style.display = 'flex';
        return;
      }

      uploadFile(file, tag, progressBar, status);
    };

    window.submitTag = function() {
      const modalTag = document.getElementById('modalTagInput').value.trim();
      const progressBar = document.getElementById('progress');
      const status = document.getElementById('status');
      const modalProgress = document.getElementById('modalProgress');
      const modalProgressContainer = document.getElementById('modalProgressContainer');

      if (!modalTag) {
        alert(" कृपया एक टैग डालें।");
        return;
      }

      modalProgressContainer.style.display = 'block';
      document.querySelector('.upload-btn').style.display = 'none';
      document.querySelector('.cancel-btn').style.display = 'none';

      uploadFile(selectedFile, modalTag, progressBar, status, modalProgress);
    };

    window.closeModal = function() {
      document.getElementById('tagModal').style.display = 'none';
      document.getElementById('modalTagInput').value = '';
      document.getElementById('modalProgressContainer').style.display = 'none';
      document.getElementById('modalProgress').style.width = '0%';
      document.getElementById('modalProgress').textContent = '0%';
      document.querySelector('.upload-btn').style.display = 'inline-block';
      document.querySelector('.cancel-btn').style.display = 'inline-block';
      selectedFile = null;
    };

    function uploadFile(file, tag, progressBar, status, modalProgress = null) {
      const url = `https://api.cloudinary.com/v1_1/${cloudName}/image/upload`;
      const formData = new FormData();
      formData.append('file', file);
      formData.append('upload_preset', uploadPreset);
      formData.append('tags', tag);

      const xhr = new XMLHttpRequest();

      xhr.upload.onprogress = function(event) {
        if (event.lengthComputable) {
          const percentComplete = Math.round((event.loaded / event.total) * 100);
          progressBar.style.width = percentComplete + '%';
          progressBar.textContent = percentComplete + '%';
          if (modalProgress) {
            modalProgress.style.width = percentComplete + '%';
            modalProgress.textContent = percentComplete + '%';
          }
          status.textContent = 'Uploading...';
        }
      };

      xhr.onload = function() {
        if (xhr.status === 200) {
          const data = JSON.parse(xhr.responseText);
          console.log("Cloudinary Response:", data);
          if (!data.secure_url) {
            status.textContent = 'Upload failed: No secure URL received';
            alert('Upload failed: No secure URL received');
            closeModal();
            return;
          }
          const imgObj = {
            url: data.secure_url,
            tag: tag,
            timestamp: serverTimestamp()
          };
          push(imagesRef, imgObj)
            .then(() => {
              console.log("Firebase Push Successful:", imgObj);
              progressBar.style.width = '100%';
              progressBar.textContent = '100%';
              if (modalProgress) {
                modalProgress.style.width = '100%';
                modalProgress.textContent = '100%';
              }
              status.textContent = 'Complete';
              alert('Uploaded Successfully!');
              closeModal();
            })
            .catch((error) => {
              console.error("Firebase Push Error:", error);
              status.textContent = 'Upload failed: Firebase error';
              alert('Upload failed: Firebase error');
              closeModal();
            });
        } else {
          console.error("Cloudinary Upload Failed:", xhr.status, xhr.responseText);
          status.textContent = 'Upload failed!';
          alert('Upload failed!');
          closeModal();
        }
      };

      xhr.onerror = function() {
        status.textContent = 'Upload error occurred!';
        alert('Upload failed due to an error!');
        closeModal();
      };

      xhr.open('POST', url, true);
      xhr.send(formData);
    }

    window.downloadImage = async function(url, tag) {
      try {
        const response = await fetch(url);
        const blob = await response.blob();
        const blobUrl = window.URL.createObjectURL(blob);
        const link = document.createElement('a');
        link.href = blobUrl;
        link.download = `${tag || 'image'}.jpg`;
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
        window.URL.revokeObjectURL(blobUrl);
      } catch (err) {
        console.error('Download failed:', err);
        alert('Failed to download the image.');
      }
    };

    onValue(imagesRef, (snapshot) => {
      const gallery = document.getElementById('gallery');
      gallery.innerHTML = '';
      const images = snapshot.val();
      const now = Date.now();

      console.log("Firebase Data:", images);

      if (images) {
        const sortedImages = Object.entries(images)
          .map(([key, img]) => ({ key, ...img }))
          .sort((a, b) => (b.timestamp || 0) - (a.timestamp || 0));

        sortedImages.forEach(({ key, url, tag, timestamp }) => {
          const imgTimestamp = timestamp || 0;
          if (now - imgTimestamp < 300000) {
            const container = document.createElement('div');
            container.className = 'image-container';
            container.innerHTML = `
              <p class="tag">Tag: ${tag}</p>
              <img src="${url}" alt="uploaded image" onload="console.log('Image loaded:', '${url}')">
              <button class="download-btn" onclick="downloadImage('${url}', '${tag}')">Download</button>
            `;
            gallery.appendChild(container);
          } else {
            remove(ref(db, `images/${key}`))
              .then(() => console.log(`Image ${key} deleted from Firebase`))
              .catch((error) => console.error("Delete Error:", error));
          }
        });
      } else {
        console.log("No images in Firebase");
      }
    });

    // CSAT Calculator Functions
    window.openCSATModal = function() {
      document.getElementById('csatModal').style.display = 'flex';
      calculateCSAT();
    };

    window.closeCSATModal = function() {
      document.getElementById('csatModal').style.display = 'none';
      document.getElementById('goodCount').value = '0';
      document.getElementById('badCount').value = '0';
      document.getElementById('requiredCSAT').value = '70';
      document.getElementById('calculateButton').textContent = 'Calculate';
      hasCalculated = false;
      calculateCSAT();
    };

    window.calculateCSAT = function() {
      const goodCount = parseInt(document.getElementById('goodCount').value) || 0;
      const badCount = parseInt(document.getElementById('badCount').value) || 0;
      const requiredCSAT = parseInt(document.getElementById('requiredCSAT').value);
      const resultSection = document.getElementById('csatResult');
      const status = document.getElementById('csatStatus');
      const calculateButton = document.getElementById('calculateButton');

      const total = goodCount + badCount;
      const csat = total === 0 ? 0 : (goodCount / total) * 100;
      const formattedCSAT = csat.toFixed(2);

      resultSection.querySelector('p:nth-child(1)').textContent = `Total: ${total}`;
      resultSection.querySelector('p:nth-child(2)').textContent = `CSAT: ${formattedCSAT}%`;

      if (total === 0) {
        status.textContent = 'Enter counts to see status';
        status.className = '';
        return;
      }

      let additionalGoodNeeded = 0;
      let newCSAT = csat;
      let newGoodCount = goodCount;
      let newTotal = total;

      if (csat <= requiredCSAT) {
        while (newCSAT <= requiredCSAT) {
          additionalGoodNeeded++;
          newGoodCount = goodCount + additionalGoodNeeded;
          newTotal = total + additionalGoodNeeded;
          newCSAT = (newGoodCount / newTotal) * 100;
        }
      }

      const exactCSAT = newCSAT;

      const isAboveRequired = csat > requiredCSAT;

      if (isAboveRequired) {
        status.textContent = `Success! CSAT (${formattedCSAT}%) is above required (${requiredCSAT}%+).`;
        status.className = 'success';
      } else {
        status.textContent = `Need ${additionalGoodNeeded} more good count(s) to achieve ${requiredCSAT}%+ (exact: ${exactCSAT.toFixed(2)}%).`;
        status.className = 'error';
      }

      if (!hasCalculated) {
        hasCalculated = true;
        calculateButton.textContent = 'Recalculate';
      }
    };

    // Close CSAT Modal on Outside Click
    document.getElementById('csatModal').addEventListener('click', function(event) {
      if (event.target === this) {
        closeCSATModal();
      }
    });

    // ENDORSEMENT Full-Page Functionality
    window.openEndorsementPage = function() {
      document.getElementById('endorsementPage').style.display = 'block';
      setTimeout(() => {
        document.querySelector('.endorsement-container').classList.add('active');
      }, 10);
      document.getElementById('mainHeader').style.display = 'none';
      document.querySelector('.upload-section').style.display = 'none';
      document.querySelector('h3').style.display = 'none';
      document.getElementById('gallery').style.display = 'none';
      document.querySelector('.csat-btn').style.display = 'none';
      document.querySelector('.endorsement-btn').style.display = 'none';
      document.querySelector('.manual-vi-btn-fixed').style.display = 'none';
      document.querySelector('.claim-nstp-btn-fixed').style.display = 'none'; /* Added to hide new button */
    };

    window.closeEndorsementPage = function() {
      document.getElementById('endorsementPage').style.display = 'none';
      document.querySelector('.endorsement-container').classList.remove('active');
      document.getElementById('mainHeader').style.display = 'block';
      document.querySelector('.upload-section').style.display = 'block';
      document.querySelector('h3').style.display = 'block';
      document.getElementById('gallery').style.display = 'grid';
      // These buttons will be hidden on mobile by CSS
      document.querySelector('.csat-btn').style.display = 'block';
      document.querySelector('.endorsement-btn').style.display = 'block';
      document.querySelector('.manual-vi-btn-fixed').style.display = 'block';
      document.querySelector('.claim-nstp-btn-fixed').style.display = 'block'; /* Added to show new button */
    };

    // Close ENDORSEMENT Page on Outside Click
    document.getElementById('endorsementPage').addEventListener('click', function(event) {
      if (event.target === this) {
        closeEndorsementPage();
      }
    });

    // MANUAL-VI Full-Page Functionality
    window.openManualVIPage = function() {
      document.getElementById('manualVIPage').style.display = 'block'; /* Show the manual VI page */
      document.getElementById('mainHeader').style.display = 'none'; /* Hide main header */
      document.querySelector('.upload-section').style.display = 'none'; /* Hide upload section */
      document.querySelector('h3').style.display = 'none'; /* Hide "Uploaded Images" header */
      document.getElementById('gallery').style.display = 'none'; /* Hide gallery */
      document.querySelector('.csat-btn').style.display = 'none'; /* Hide CSAT button */
      document.querySelector('.endorsement-btn').style.display = 'none'; /* Hide ENDORSEMENT button */
      document.querySelector('.manual-vi-btn-fixed').style.display = 'none'; /* Hide the MANUAL-VI button itself */
      document.querySelector('.claim-nstp-btn-fixed').style.display = 'none'; /* Added to hide new button */
    };

    window.closeManualVIPage = function() {
      document.getElementById('manualVIPage').style.display = 'none'; /* Hide the manual VI page */
      document.getElementById('mainHeader').style.display = 'block'; /* Show main header */
      document.querySelector('.upload-section').style.display = 'block'; /* Show upload section */
      document.querySelector('h3').style.display = 'block'; /* Show "Uploaded Images" header */
      document.getElementById('gallery').style.display = 'grid'; /* Show gallery */
      document.querySelector('.csat-btn').style.display = 'block'; /* Show CSAT button */
      document.querySelector('.endorsement-btn').style.display = 'block'; /* Show ENDORSEMENT button */
      document.querySelector('.manual-vi-btn-fixed').style.display = 'block'; /* Show the MANUAL-VI button itself */
      document.querySelector('.claim-nstp-btn-fixed').style.display = 'block'; /* Added to show new button */
    };

    // Close Manual VI Page on Outside Click (optional, but good for consistency)
    document.getElementById('manualVIPage').addEventListener('click', function(event) {
      if (event.target === this) {
        closeManualVIPage();
      }
    });

    // Data for the Claim Count & NSTP table
    const insuranceData = [
      {
          "insurer_name": "National",
          "commercial": "Yes",
          "video_approval": "At PB end",
          "video_tat": "24 Hours",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "ZD Plan: 2, ZD+: Unlimited",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "New India Assurance",
          "commercial": "Yes",
          "video_approval": "At PB end",
          "video_tat": "24 Hours",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "Yes",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Oriental",
          "commercial": "No",
          "video_approval": "At PB end",
          "video_tat": "24 Hours",
          "short_partial": "No",
          "artificial_low_lighting": "Yes",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "United India",
          "commercial": "Yes",
          "video_approval": "At PB end",
          "video_tat": "48 Hours",
          "short_partial": "Yes",
          "artificial_low_lighting": "Yes",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "Unlimited",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Tata AIG",
          "commercial": "Yes",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required (with vehicle number) within Video TAT",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "Yes",
          "old_3_3": "Yes"
      },
      {
          "insurer_name": "ICICI Lombard",
          "commercial": "Yes",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "Yes",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "Yes",
          "old_3_3": "Yes"
      },
      {
          "insurer_name": "Zuno General",
          "commercial": "No",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Cholamandalam MS",
          "commercial": "No",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Will Not Accept Scar on WS/change insurer",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Future Generali",
          "commercial": "No",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "MAGMA",
          "commercial": "No",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required (Scar on Driver Side not accepted) within Video TAT",
          "zd_claims_year": "Unlimited",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Raheja QBE",
          "commercial": "No",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Kotak",
          "commercial": "No",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "SBI General",
          "commercial": "Yes",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "Unlimited",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Shriram",
          "commercial": "Yes",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required (Shriram format) + Address ID proof within Video TAT",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited till IDV",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Iffco Tokio",
          "commercial": "No",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "Unlimited",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Liberty Videocon",
          "commercial": "No",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "No",
          "artificial_low_lighting": "No",
          "scar_declaration": "Will Not Accept Scar on WS/change insurer",
          "zd_claims_year": "Unlimited",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "HDFC Ergo",
          "commercial": "No",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Will Not Accept Scar on WS/change insurer",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Reliance",
          "commercial": "Yes",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required (with vehicle number) within Video TAT",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited till IDV",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Bajaj Allianz",
          "commercial": "Yes",
          "video_approval": "At U/W end",
          "video_tat": "2 days",
          "short_partial": "Yes",
          "artificial_low_lighting": "No",
          "scar_declaration": "Will Refer to Under Writer",
          "zd_claims_year": "2",
          "non_zd_claims_year": "Unlimited",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Royal Sundaram",
          "commercial": "No",
          "video_approval": "At U/W end",
          "video_tat": "2 days",
          "short_partial": "No",
          "artificial_low_lighting": "No",
          "scar_declaration": "Will Refer to Under Writer",
          "zd_claims_year": "Unlimited till IDV",
          "non_zd_claims_year": "Unlimited till IDV",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Universal Sompo",
          "commercial": "No",
          "video_approval": "At U/W end",
          "video_tat": "2 days",
          "short_partial": "No",
          "artificial_low_lighting": "No",
          "scar_declaration": "Will Refer to Under Writer",
          "zd_claims_year": "Unlimited till IDV",
          "non_zd_claims_year": "Unlimited till IDV",
          "brand_new_3_3": "No",
          "old_3_3": "No"
      },
      {
          "insurer_name": "Digit",
          "commercial": "Yes",
          "video_approval": "At PB end",
          "video_tat": "2 days",
          "short_partial": "No",
          "artificial_low_lighting": "No",
          "scar_declaration": "Declaration Required within Video TAT",
          "zd_claims_year": "1 or 2 claims (as per selected plan)",
          "non_zd_claims_year": "Unlimited till IDV",
          "brand_new_3_3": "Yes",
          "old_3_3": "Yes"
      }
    ];

    // Function to populate the Claim Count & NSTP table
    function populateClaimNSTPTable(data) {
        const tableBody = document.getElementById('claimNstpTableBody');
        tableBody.innerHTML = ''; // Clear existing rows
        data.forEach(item => {
            const row = document.createElement('tr');
            row.className = 'table-row';
            row.innerHTML = `
                <td class="p-2 font-medium text-indigo-900">${item.insurer_name}</td>
                <td class="p-2 neutral">${item.zd_claims_year}</td>
                <td class="p-2 neutral">${item.non_zd_claims_year}</td>
                <td class="p-2 ${item.commercial === 'Yes' ? 'positive' : 'negative'}">${item.commercial}</td>
                <td class="p-2 neutral">${item.video_approval}</td>
                <td class="p-2 neutral">${item.video_tat}</td>
                <td class="p-2 ${item.short_partial === 'Yes' ? 'positive' : 'negative'}">${item.short_partial}</td>
                <td class="p-2 ${item.artificial_low_lighting === 'Yes' ? 'positive' : 'negative'}">${item.artificial_low_lighting}</td>
                <td class="p-2 neutral">${item.scar_declaration}</td>
                <td class="p-2 ${item.brand_new_3_3 === 'Yes' ? 'positive' : 'negative'}">${item.brand_new_3_3}</td>
                <td class="p-2 ${item.old_3_3 === 'Yes' ? 'positive' : 'negative'}">${item.old_3_3}</td>
            `;
            tableBody.appendChild(row);
        });
    }

    // Claim Count & NSTP Full-Page Functionality (नया जोड़ा गया)
    window.openClaimNSTPPage = function() {
      document.getElementById('claimNSTPPage').style.display = 'block'; /* Show the new page */
      populateClaimNSTPTable(insuranceData); // Populate the table when the page opens

      // Set up search and sort for Claim NSTP page
      document.getElementById('claimNstpSearchInput').addEventListener('input', (e) => {
            const searchTerm = e.target.value.toLowerCase();
            const filteredData = insuranceData.filter(item =>
                item.insurer_name.toLowerCase().includes(searchTerm)
            );
            populateClaimNSTPTable(filteredData);
        });

      document.querySelectorAll('#claimNstpTable .table-header').forEach(header => {
            header.addEventListener('click', () => {
                const column = header.dataset.column;
                const currentOrder = header.classList.contains('sort-asc') ? 'desc' : 'asc';

                document.querySelectorAll('#claimNstpTable .table-header').forEach(h => {
                    h.classList.remove('sort-asc', 'sort-desc');
                    // h.classList.add('sort-icon'); // You might want to add a default sort icon if needed
                });

                header.classList.remove('sort-icon');
                header.classList.add(currentOrder === 'asc' ? 'sort-asc' : 'sort-desc');

                // Sort the data based on the full insuranceData, then populate
                const sortedData = [...insuranceData].sort((a, b) => {
                    const aValue = String(a[column]).toLowerCase(); // Ensure string conversion
                    const bValue = String(b[column]).toLowerCase(); // Ensure string conversion
                    if (currentOrder === 'asc') {
                        return aValue > bValue ? 1 : -1;
                    } else {
                        return aValue < bValue ? 1 : -1;
                    }
                });
                populateClaimNSTPTable(sortedData);
            });
        });

      document.getElementById('mainHeader').style.display = 'none'; /* Hide main header */
      document.querySelector('.upload-section').style.display = 'none'; /* Hide upload section */
      document.querySelector('h3').style.display = 'none'; /* Hide "Uploaded Images" header */
      document.getElementById('gallery').style.display = 'none'; /* Hide gallery */
      document.querySelector('.csat-btn').style.display = 'none'; /* Hide CSAT button */
      document.querySelector('.endorsement-btn').style.display = 'none'; /* Hide ENDORSEMENT button */
      document.querySelector('.manual-vi-btn-fixed').style.display = 'none'; /* Hide Manual VI button */
      document.querySelector('.claim-nstp-btn-fixed').style.display = 'none'; /* Hide itself */
    };

    window.closeClaimNSTPPage = function() {
      document.getElementById('claimNSTPPage').style.display = 'none'; /* Hide the new page */
      document.getElementById('mainHeader').style.display = 'block'; /* Show main header */
      document.querySelector('.upload-section').style.display = 'block'; /* Show upload section */
      document.querySelector('h3').style.display = 'block'; /* Show "Uploaded Images" header */
      document.getElementById('gallery').style.display = 'grid'; /* Show gallery */
      document.querySelector('.csat-btn').style.display = 'block'; /* Show CSAT button */
      document.querySelector('.endorsement-btn').style.display = 'block'; /* Show ENDORSEMENT button */
      document.querySelector('.manual-vi-btn-fixed').style.display = 'block'; /* Show Manual VI button */
      document.querySelector('.claim-nstp-btn-fixed').style.display = 'block'; /* Show itself */
    };

    // नया लॉजिक: सेक्शन के बाहर क्लिक करने पर मुख्य पेज पर वापसी
    document.getElementById('claimNSTPPage').addEventListener('click', function(event) {
      const container = document.querySelector('#claimNSTPPage .container');
      if (container && !container.contains(event.target)) {
        closeClaimNSTPPage();
      }
    });

    // नया लॉजिक: कीबोर्ड ऐरो की (arrow keys) से साइड स्क्रॉल
    document.addEventListener('keydown', function(event) {
      const claimNstpPage = document.getElementById('claimNSTPPage');
      if (claimNstpPage.style.display === 'block') { // Only scroll if claimNstpPage is visible
        const tableContainer = document.getElementById('claimNstpTableContainer');
        if (event.key === 'ArrowRight') {
          tableContainer.scrollLeft += 100; // Scroll 100px to the right
        } else if (event.key === 'ArrowLeft') {
          tableContainer.scrollLeft -= 100; // Scroll 100px to the left
        }
      }
    });


    const insurerDropdown = document.querySelector('.endorsement-page #insurer');
    const requirementDropdown = document.querySelector('.endorsement-page #requirement');
    const outputBox = document.querySelector('.endorsement-page #output');

    // Empty array for you to manually add JSON data
    const data = [];

    // Populate insurer dropdown
    try {
      const insurers = [...new Set(data.map(d => d["Insurer"]))].sort();
      insurers.forEach(ins => {
        const opt = document.createElement("option");
        opt.value = opt.textContent = ins;
        insurerDropdown.appendChild(opt);
      });
    } catch (error) {
      console.error("Error populating insurers:", error);
      alert("Error in JSON data. Please check the syntax and paste valid JSON.");
    }

    // Handle insurer selection
    insurerDropdown.addEventListener("change", () => {
      requirementDropdown.innerHTML = "<option disabled selected>Select Requirement</option>";
      outputBox.style.display = "none";
      outputBox.classList.remove("show", "output-red");
      const selectedInsurer = insurerDropdown.value;
      const requirements = [...new Set(
        data.filter(d => d["Insurer"] === selectedInsurer)
            .map(d => d["Requirement"])
      )].sort();
      requirements.forEach(req => {
        const opt = document.createElement("option");
        opt.value = opt.textContent = req;
        requirementDropdown.appendChild(opt);
      });
      requirementDropdown.disabled = false;
    });

    // Handle requirement selection
    requirementDropdown.addEventListener("change", () => {
      const ins = insurerDropdown.value;
      const req = requirementDropdown.value;
      const record = data.find(
        d => d["Insurer"] === ins && d["Requirement"] === req
      );
      if (record) {
        outputBox.innerHTML = `
          <div><span class="label">Endorsement Type:</span><span class="value">${record["Endorsement type"]}</span></div>
          <div><span class="label">Documents Required:</span><span class="value">${record["Documents or any other requirement"]}</span></div>
          <div><span class="label">TAT:</span><span class="value">${record["TAT"]}</span></div>
          <div><span class="label">Charges/Deduction:</span><span class="value">${record["Charges / Deduction"]}</span></div>
          <div><span class="label">Inspection:</span><span class="value">${record["Inspection"]}</span></div>
          <div><span class="label">Exception:</span><span class="value">${record["Any Exception"]}</span></div>
          <div><span class="label">Declaration Format:</span><span class="value">${record["Declaration format (if declaration required)"]}</span></div>
        `;
        if (record["Endorsement type"].toLowerCase() === "not possible") {
          outputBox.classList.add("output-red");
        } else {
          outputBox.classList.remove("output-red");
        }
        outputBox.style.display = "block";
        setTimeout(() => outputBox.classList.add("show"), 10);
      }
    });

  </script>
</body>
</html>
