<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Test Vahan</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      padding: 20px;
      /* Add significant top padding to account for external GitHub header and our fixed app header */
      padding-top: 120px; /* Increased padding to give more space for both fixed headers */
      background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%);
      text-align: center;
      margin: 0;
      min-height: 100vh;
      position: relative;
    }
    .app-main-header {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      background: #1a237e; /* Dark blue background for strong visibility */
      color: white;
      padding: 10px 0;
      font-size: 2.2em;
      font-weight: 700;
      letter-spacing: 2px;
      z-index: 1002; /* Highest z-index to ensure it's always on top */
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
      text-transform: uppercase;
    }

    h2, h3 {
      color: #1a237e;
      font-weight: 600;
      margin-top: 20px;
    }
    h2 {
      font-size: 2em;
      letter-spacing: 1px;
    }
    h3 {
      font-size: 1.5em;
    }
    .upload-section {
      margin-bottom: 20px;
      background: rgba(255, 255, 255, 0.9);
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }
    input[type="file"], input[type="text"] {
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
      padding: 15px 25px;
      margin: 8px;
      font-size: 18px;
      border-radius: 8px;
      border: none;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
      color: white;
    }

    .upload-main-btn {
      background-color: #64b5f6;
      padding: 18px 30px;
      font-size: 20px;
      font-weight: 600;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
      border: 2px solid #2196f3;
    }
    .upload-main-btn:hover {
      background-color: #42a5f5;
      box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
      transform: translateY(-3px) scale(1.02);
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
      z-index: 1001; /* Higher z-index for modals */
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
      background-color: #3f51b5;
      color: white;
      border: none;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }
    .modal-content .upload-btn:hover {
      background-color: #303f9f;
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
      z-index: 1001; /* Higher z-index for modals */
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
      transform: scale(0.9);
      opacity: 0;
      transition: transform 0.3s ease, opacity 0.3s ease;
    }
    .csat-modal-content.active {
      transform: scale(1);
      opacity: 1;
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
    .csat-modal-content .button-group {
      display: flex;
      justify-content: center;
      gap: 10px; /* Space between buttons */
      margin-top: 15px;
    }
    .csat-modal-content .close-btn,
    .csat-modal-content .calculate-btn {
      flex: 1; /* Make buttons take equal width within the group */
      padding: 10px 20px;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
      border: none; /* Remove default button border */
    }
    .csat-modal-content .close-btn {
      background-color: #f44336;
      color: white;
    }
    .csat-modal-content .close-btn:hover {
      background-color: #d32f2f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    .csat-modal-content .calculate-btn {
      background-color: #3f51b5;
      color: white;
    }
    .csat-modal-content .calculate-btn:hover {
      background-color: #303f9f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    /* Fixed Buttons on Main Page */
    .fixed-buttons-container {
        position: fixed;
        top: 60px; /* Positioned below the new app header */
        left: 0;
        right: 0;
        width: 100%;
        display: flex;
        justify-content: center;
        gap: 20px;
        z-index: 1000; /* Between app header and modals */
        padding: 5px 0;
        background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%); /* Match body background */
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }

    .csat-btn,
    .vi-claim-btn,
    .endorsement-btn,
    .manual-vi-btn {
      background-color: #1b5e20;
      color: white;
      border: none;
      padding: 15px 25px;
      font-size: 18px;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
      white-space: nowrap;
    }
    .csat-btn:hover,
    .vi-claim-btn:hover,
    .endorsement-btn:hover,
    .manual-vi-btn:hover {
      background-color: #2e7d32;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateY(-2px);
    }

    /* Full-Page Widget Styles (for all modes) */
    .endorsement-page, .vi-claim-page, .manual-vi-page, .csat-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%);
      z-index: 1003; /* Highest z-index for full-page modals */
      padding: 0;
      margin: 0;
      box-sizing: border-box;
      font-family: 'Roboto', sans-serif;
      overflow-y: auto;
      justify-content: center;
      align-items: center;
    }
    .endorsement-container, .vi-claim-container, .manual-vi-container, .csat-modal-content {
      width: 100%;
      max-width: 800px;
      margin: 20px auto;
      background: #ffffff;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
      transition: transform 0.3s ease, opacity 0.3s ease;
      transform: scale(0.9);
      opacity: 0;
      position: relative;
    }
    .endorsement-container.active, .vi-claim-container.active, .manual-vi-container.active, .csat-modal-content.active {
      transform: scale(1);
      opacity: 1;
    }
    .endorsement-container h1, .vi-claim-container h1, .manual-vi-container h1, .csat-modal-content h4 {
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
      font-family: Arial, Helvetica, sans-serif;
      background: #fafafa;
      transition: border-color 0.3s ease, box-shadow 0.3s ease;
      cursor: pointer;
      height: 40px;
      appearance: none;
      -webkit-appearance: none;
      -moz-appearance: none;
      background-image: url('data:image/svg+xml;utf8,<svg fill="black" height="24" viewBox="0 0 24 24" width="24" xmlns="http://www.w3.org/2000/svg"><path d="M7 10l5 5 5-5z"/></svg>');
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

    /* Styles from ZD.html */
    .table-header {
        cursor: pointer;
        transition: background-color 0.3s, transform 0.2s;
    }
    .table-header:hover {
        background-color: #facc15;
        transform: scale(1.05);
    }
    .sort-icon::after {
        content: '↕';
        margin-left: 5px;
        display: inline-block;
    }
    .sort-asc::after {
        content: '↑';
    }
    .sort-desc::after {
        content: '↓';
    }
    .table-row {
        transition: background-color 0.3s;
    }
    .table-row:hover {
        background-color: #fefcbf;
    }
    .search-input {
        transition: all 0.3s;
    }
    .search-input:focus {
        border-color: #db2777;
        box-shadow: 0 0 10px rgba(219, 39, 119, 0.5);
    }
    td, th {
        white-space: normal !important;
        word-break: break-words !important;
    }
    .table-row:nth-child(odd) {
        background-color: #e0f7fa;
    }
    .table-row:nth-child(even) {
        background-color: #fce4ec;
    }
    .table-row:hover {
        background-color: #fff9c4 !important;
    }

    .horizontal-scroll-buttons {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin-bottom: 15px;
    }

    .horizontal-scroll-buttons button {
      background-color: #3f51b5;
      color: white;
      padding: 8px 15px;
      border-radius: 8px;
      font-size: 1em;
      cursor: pointer;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      transition: all 0.3s ease;
    }

    .horizontal-scroll-buttons button:hover {
      background-color: #303f9f;
      transform: translateY(-2px);
    }

    /* Hide main content when a modal/full-page section is open */
    body.modal-open > .app-main-header,
    body.modal-open > .fixed-buttons-container,
    body.modal-open > .upload-section,
    body.modal-open > h3,
    body.modal-open > #gallery {
      display: none !important;
    }

    @media (max-width: 600px) {
      body {
        padding-top: 50px; /* Adjust padding for mobile view to account for fixed app header */
      }
      .app-main-header {
        font-size: 1.5em; /* Smaller font size for mobile header */
        padding: 8px 0;
      }
      input[type="file"], input[type="text"] {
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
      /* Hide fixed buttons container on mobile for main page view */
      body:not(.modal-open) .fixed-buttons-container {
        display: none !important;
      }
      /* Show main upload section by default on mobile when no modal is open */
      body:not(.modal-open) .upload-section,
      body:not(.modal-open) h3,
      body:not(.modal-open) #gallery {
        display: block !important;
      }

      .modal-content, .csat-modal-content {
        width: 80%;
        padding: 15px;
      }
      .csat-modal-content .close-btn,
      .csat-modal-content .calculate-btn {
          padding: 8px 15px;
          font-size: 16px;
      }

      .endorsement-container, .vi-claim-container, .manual-vi-container {
        width: 90vw;
        padding: 15px;
        margin-top: 10px;
      }
      .endorsement-container h1, .vi-claim-container h1, .manual-vi-container h1 {
        font-size: 1.5em;
      }
      .PB_DROPDOWN {
        font-size: 0.9em;
        height: 36px;
      }
      .output {
        font-size: 0.95em;
      }
      .created-by {
        font-size: 0.7em;
      }
    }
  </style>
</head>
<body>
  <!-- Main Application Header -->
  <div class="app-main-header">
    TEST VAHAN
  </div>

  <div class="fixed-buttons-container">
    <!-- CSAT Calculator Button -->
    <button class="csat-btn" onclick="openCSATModal()">CSAT Calculator</button>

    <!-- VI & Claim Count Button -->
    <button class="vi-claim-btn" onclick="openVIClaimPage()">VI & Claim_Count</button>

    <!-- ENDORSEMENT Button -->
    <button class="endorsement-btn" onclick="openEndorsementPage()">ENDORSEMENT</button>

    <!-- MANUAL-VI Button -->
    <button class="manual-vi-btn" onclick="openManualVIPage()">MANUAL-VI</button>
  </div>


<!-- MANUAL-VI Full-Page Widget -->
<div class="manual-vi-page" id="manualVIPage">
  <div class="manual-vi-container">
    <button class="back-btn" onclick="closeManualVIPage()">Back to Main Page</button>
    <h1>Manual VI Details</h1>
    <div class="created-by">Created by Shivang</div>
    <div class="mb-3 p-3 rounded" style="background-color: #e3f2fd;">
      <strong>ADP Home Visit Cities: 42</strong>
      <ul class="mb-0" style="columns: 2;">
        <li>Aligarh</li><li>Alwar</li><li>Ambala</li><li>Amritsar</li><li>Belgaum</li>
        <li>Bhiwani</li><li>Bhubaneshwar</li><li>Bilaspur</li><li>Coimbatore</li><li>Dhanbad</li>
        <li>Guwahati</li><li>Haldwani</li><li>Haridwar</li><li>Indore</li><li>Jalandhar</li>
        <li>Jamshedpur</li><li>Jhajjar</li><li>Jind</li><li>Jodhpur</li>
        <li>Kangra</li><li>Madurai</li><li>Mathura</li><li>Moradabad</li><li>Muzaffarnagar</li>
        <li>Mysore</li><li>Nagpur</li><li>Panipat</li><li>Pondicherry</li><li>Raipur</li>
        <li>Rajkot</li><li>Rewa</li><li>Rewari</li><li>Rohtak</li><li>Satara</li>
        <li>Shimla</li><li>Surat</li><li>Thiruvananthapuram</li><li>Thrissur</li><li>Udaipur</li>
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

  <!-- Removed h2#mainHeader as it's replaced by app-main-header -->
  <div class="upload-section">
    <input type="file" id="fileUpload" accept="image/*">
    <input type="text" id="tagInput" placeholder="Enter tag (e.g., Shivang)">
    <button class="upload-main-btn" onclick="uploadImage()">Upload</button>
    <div class="progress-container">
      <div class="progress-bar">
        <div class="progress" id="progress">0%</div>
      </div>
      <div class="status" id="status">Ready</div>
    </div>
  </div>

  <h3>Uploaded Images</h3>
  <div id="gallery"></div>

  <!-- Tag Modal -->
  <div id="tagModal" class="modal">
    <div class="modal-content">
      <h4>Error: Tag is required!</h4>
      <input type="text" id="modalTagInput" placeholder="Enter tag (e.g., Shivang)">
      <button class="upload-btn" onclick="submitTag()">Upload</button>
      <button class="cancel-btn" onclick="closeModal()">Cancel</button>
      <div class="modal-progress-container" id="modalProgressContainer">
        <div class="modal-progress-bar">
          <div class="modal-progress" id="modalProgress">0%</div>
        </div>
      </div>
    </div>
  </div>

  <!-- CSAT Calculator Modal -->
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
      <div class="button-group"> <!-- New button group for alignment -->
        <button class="close-btn" onclick="closeCSATModal()">Close</button>
        <button class="calculate-btn" id="calculateButton" onclick="calculateCSAT()">Calculate</button>
      </div>
    </div>
  </div>

  <!-- ENDORSEMENT Full-Page Widget -->
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

  <!-- VI & Claim Count Full-Page Widget -->
  <div class="vi-claim-page" id="viClaimPage">
    <div class="vi-claim-container">
      <!-- Content from ZD.html starts here -->
      <button class="back-btn" onclick="closeVIClaimPage()">Back to Main Page</button>
      <div class="container mx-auto p-4 bg-white rounded-2xl shadow-2xl max-w-7xl w-full border-4 border-transparent bg-clip-border bg-gradient-to-r from-blue-500 via-purple-500 to-pink-500">
        <!-- Horizontal Scroll Buttons -->
        <div class="horizontal-scroll-buttons">
          <button onclick="scrollTableHorizontally('left')">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-arrow-left">
              <path d="M19 12H5"/>
              <path d="m12 19-7-7 7-7"/>
            </svg>
          </button>
          <button onclick="scrollTableHorizontally('right')">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-arrow-right">
              <path d="M5 12h14"/>
              <path d="m12 5 7 7-7 7"/>
            </svg>
          </button>
        </div>
        <h1 class="text-4xl font-bold text-center mb-6 text-indigo-800 tracking-tight">Insurance Comparison Dashboard</h1>
        <p class="text-center text-lg text-gray-600 mb-4">Created by Shivang</p>
        <div class="mb-4">
            <input type="text" id="searchInput" placeholder="Search by Insurer Name..." class="search-input w-full p-3 text-lg border-2 border-blue-500 rounded-lg shadow-md focus:outline-none focus:ring-4 focus:ring-pink-500 bg-blue-50 text-gray-800 placeholder-gray-500">
        </div>
        <div class="overflow-x-auto rounded-lg" id="insuranceTableWrapper">
            <table id="insuranceTable" class="w-full bg-white border border-gray-300">
                <thead class="bg-gradient-to-r from-blue-600 via-purple-600 to-pink-600 text-white text-lg font-semibold">
                    <tr>
                        <th class="table-header p-2 text-left" data-column="insurer_name">Insurer Name</th>
                        <th class="table-header p-2 text-left" data-column="zd_claims_year">ZD Claims/Year</th>
                        <th class="table-header p-2 text-left" data-column="non_zd_claims_year">Non-ZD Claims/Year</th>
                        <th class="table-header p-2 text-left" data-column="video_tat">Video TAT</th>
                        <th class="table-header p-2 text-left" data-column="short_partial">Short Partial</th>
                        <th class="table-header p-2 text-left" data-column="artificial_low_lighting">Artificial Low Lighting</th>
                        <th class="table-header p-2 text-left" data-column="scar_declaration">Scar Declaration</th>
                        <th class="table-header p-2 text-left" data-column="commercial">Commercial</th>
                        <th class="table-header p-2 text-left" data-column="video_approval">Video Approval</th>
                        <th class="table-header p-2 text-left" data-column="brand_new_3_3">Brand New 3+3</th>
                        <th class="table-header p-2 text-left" data-column="old_3_3">Old 3+3</th>
                    </tr>
                </thead>
                <tbody id="tableBody" class="text-gray-800 text-base">
                    <!-- Data will be populated by JavaScript -->
                </tbody>
            </table>
        </div>
      </div>
      <!-- Content from ZD.html ends here -->
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
        // Use a message box instead of alert
        const modal = document.createElement('div');
        modal.innerHTML = `
          <div style="position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); display: flex; justify-content: center; align-items: center; z-index: 9999;">
            <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.3); text-align: center;">
              <p>कृपया एक फोटो चुनें।</p>
              <button onclick="this.parentElement.parentElement.remove()" style="margin-top: 10px; padding: 8px 15px; background-color: #3f51b5; color: white; border: none; border-radius: 5px; cursor: pointer;">Ok</button>
            </div>
          </div>
        `;
        document.body.appendChild(modal);
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
        // Use a message box instead of alert
        const modal = document.createElement('div');
        modal.innerHTML = `
          <div style="position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); display: flex; justify-content: center; align-items: center; z-index: 9999;">
            <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.3); text-align: center;">
              <p>कृपया एक टैग डालें।</p>
              <button onclick="this.parentElement.parentElement.remove()" style="margin-top: 10px; padding: 8px 15px; background-color: #3f51b5; color: white; border: none; border-radius: 5px; cursor: pointer;">Ok</button>
            </div>
          </div>
        `;
        document.body.appendChild(modal);
        return;
      }

      modalProgressContainer.style.display = 'block';
      document.querySelector('#tagModal .upload-btn').style.display = 'none';
      document.querySelector('#tagModal .cancel-btn').style.display = 'none';

      uploadFile(selectedFile, modalTag, progressBar, status, modalProgress);
    };

    window.closeModal = function() {
      document.getElementById('tagModal').style.display = 'none';
      document.getElementById('modalTagInput').value = '';
      document.getElementById('modalProgressContainer').style.display = 'none';
      document.getElementById('modalProgress').style.width = '0%';
      document.getElementById('modalProgress').textContent = '0%';
      document.querySelector('#tagModal .upload-btn').style.display = 'inline-block';
      document.querySelector('#tagModal .cancel-btn').style.display = 'inline-block';
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
            // Use a message box instead of alert
            const modal = document.createElement('div');
            modal.innerHTML = `
              <div style="position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); display: flex; justify-content: center; align-items: center; z-index: 9999;">
                <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.3); text-align: center;">
                  <p>Upload failed: No secure URL received</p>
                  <button onclick="this.parentElement.parentElement.remove()" style="margin-top: 10px; padding: 8px 15px; background-color: #3f51b5; color: white; border: none; border-radius: 5px; cursor: pointer;">Ok</button>
                </div>
              </div>
            `;
            document.body.appendChild(modal);
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
              // Use a message box instead of alert
              const modal = document.createElement('div');
              modal.innerHTML = `
                <div style="position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); display: flex; justify-content: center; align-items: center; z-index: 9999;">
                  <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.3); text-align: center;">
                    <p>Uploaded Successfully!</p>
                    <button onclick="this.parentElement.parentElement.remove()" style="margin-top: 10px; padding: 8px 15px; background-color: #3f51b5; color: white; border: none; border-radius: 5px; cursor: pointer;">Ok</button>
                  </div>
                </div>
              `;
              document.body.appendChild(modal);
              closeModal();
            })
            .catch((error) => {
              console.error("Firebase Push Error:", error);
              status.textContent = 'Upload failed: Firebase error';
              // Use a message box instead of alert
              const modal = document.createElement('div');
              modal.innerHTML = `
                <div style="position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); display: flex; justify-content: center; align-items: center; z-index: 9999;">
                  <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.3); text-align: center;">
                    <p>Upload failed: Firebase error</p>
                    <button onclick="this.parentElement.parentElement.remove()" style="margin-top: 10px; padding: 8px 15px; background-color: #3f51b5; color: white; border: none; border-radius: 5px; cursor: pointer;">Ok</button>
                  </div>
                </div>
              `;
              document.body.appendChild(modal);
              closeModal();
            });
        } else {
          console.error("Cloudinary Upload Failed:", xhr.status, xhr.responseText);
          status.textContent = 'Upload failed!';
          // Use a message box instead of alert
          const modal = document.createElement('div');
          modal.innerHTML = `
            <div style="position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); display: flex; justify-content: center; align-items: center; z-index: 9999;">
              <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.3); text-align: center;">
                <p>Upload failed!</p>
                <button onclick="this.parentElement.parentElement.remove()" style="margin-top: 10px; padding: 8px 15px; background-color: #3f51b5; color: white; border: none; border-radius: 5px; cursor: pointer;">Ok</button>
              </div>
            </div>
          `;
          document.body.appendChild(modal);
          closeModal();
        }
      };

      xhr.onerror = function() {
        status.textContent = 'Upload error occurred!';
        // Use a message box instead of alert
        const modal = document.createElement('div');
        modal.innerHTML = `
          <div style="position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); display: flex; justify-content: center; align-items: center; z-index: 9999;">
            <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.3); text-align: center;">
              <p>Upload failed due to an error!</p>
              <button onclick="this.parentElement.parentElement.remove()" style="margin-top: 10px; padding: 8px 15px; background-color: #3f51b5; color: white; border: none; border-radius: 5px; cursor: pointer;">Ok</button>
            </div>
          </div>
        `;
        document.body.appendChild(modal);
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
        // Use a message box instead of alert
        const modal = document.createElement('div');
        modal.innerHTML = `
          <div style="position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); display: flex; justify-content: center; align-items: center; z-index: 9999;">
            <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.3); text-align: center;">
              <p>Failed to download the image.</p>
              <button onclick="this.parentElement.parentElement.remove()" style="margin-top: 10px; padding: 8px 15px; background-color: #3f51b5; color: white; border: none; border-radius: 5px; cursor: pointer;">Ok</button>
            </div>
          </div>
        `;
        document.body.appendChild(modal);
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
          // Keep images for 5 minutes (300000 milliseconds)
          if (now - imgTimestamp < 300000) {
            const container = document.createElement('div');
            container.className = 'image-container';
            container.innerHTML = `
              <p class="tag">Tag: ${tag}</p>
              <img src="${url}" alt="uploaded image" onerror="this.onerror=null;this.src='https://placehold.co/150x150/FFF/000?text=Image+Error';" onload="console.log('Image loaded:', '${url}')">
              <button class="download-btn" onclick="downloadImage('${url}', '${tag}')">Download</button>
            `;
            gallery.appendChild(container);
          } else {
            // Delete image from Firebase if older than 5 minutes
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
      setTimeout(() => {
        document.querySelector('#csatModal .csat-modal-content').classList.add('active');
      }, 10);
      document.body.classList.add('modal-open');
      calculateCSAT();
    };

    window.closeCSATModal = function() {
      document.querySelector('#csatModal .csat-modal-content').classList.remove('active');
      setTimeout(() => {
        document.getElementById('csatModal').style.display = 'none';
        document.body.classList.remove('modal-open');
      }, 300);
      
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
      document.body.classList.add('modal-open');
    };

    window.closeEndorsementPage = function() {
      document.querySelector('.endorsement-container').classList.remove('active');
      setTimeout(() => {
        document.getElementById('endorsementPage').style.display = 'none';
        document.body.classList.remove('modal-open');
      }, 300);
    };

    document.getElementById('endorsementPage').addEventListener('click', function(event) {
      if (event.target === this) {
        closeEndorsementPage();
      }
    });

    // VI & Claim Count Full-Page Functionality
    window.openVIClaimPage = function() {
      document.getElementById('viClaimPage').style.display = 'block';
      setTimeout(() => {
        document.querySelector('.vi-claim-container').classList.add('active');
      }, 10);
      populateTable(insuranceData);
      document.body.classList.add('modal-open');
    };

    window.closeVIClaimPage = function() {
      document.querySelector('.vi-claim-container').classList.remove('active');
      setTimeout(() => {
        document.getElementById('viClaimPage').style.display = 'none';
        document.body.classList.remove('modal-open');
      }, 300);
    };

    document.getElementById('viClaimPage').addEventListener('click', function(event) {
      if (event.target === this) {
        closeVIClaimPage();
      }
    });

    // MANUAL-VI Full-Page Functionality
    window.openManualVIPage = function() {
      document.getElementById('manualVIPage').style.display = 'block';
      setTimeout(() => {
        document.querySelector('.manual-vi-container').classList.add('active');
      }, 10);
      document.body.classList.add('modal-open');
    };

    window.closeManualVIPage = function() {
      document.querySelector('.manual-vi-container').classList.remove('active');
      setTimeout(() => {
        document.getElementById('manualVIPage').style.display = 'none';
        document.body.classList.remove('modal-open');
      }, 300);
    };

    document.getElementById('manualVIPage').addEventListener('click', function(event) {
      if (event.target === this) {
        closeManualVIPage();
      }
    });


    const insurerDropdown = document.querySelector('.endorsement-page #insurer');
    const requirementDropdown = document.querySelector('.endorsement-page #requirement');
    const outputBox = document.querySelector('.endorsement-page #output');

    const data = [];

    try {
      const insurers = [...new Set(data.map(d => d["Insurer"]))].sort();
      insurers.forEach(ins => {
        const opt = document.createElement("option");
        opt.value = opt.textContent = ins;
        insurerDropdown.appendChild(opt);
      });
    } catch (error) {
      console.error("Error populating insurers:", error);
      const modal = document.createElement('div');
      modal.innerHTML = `
        <div style="position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); display: flex; justify-content: center; align-items: center; z-index: 9999;">
          <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.3); text-align: center;">
            <p>Error in JSON data. Please check the syntax and paste valid JSON.</p>
            <button onclick="this.parentElement.parentElement.remove()" style="margin-top: 10px; padding: 8px 15px; background-color: #3f51b5; color: white; border: none; border-radius: 5px; cursor: pointer;">Ok</button>
          </div>
        </div>
      `;
      document.body.appendChild(modal);
    }

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

    function populateTable(data) {
        const tableBody = document.getElementById('tableBody');
        tableBody.innerHTML = '';
        data.forEach(item => {
            const row = document.createElement('tr');
            row.className = 'table-row border-b';
            row.innerHTML = `
                <td class="p-2 font-medium text-indigo-900">${item.insurer_name}</td>
                <td class="p-2">${item.zd_claims_year}</td>
                <td class="p-2">${item.non_zd_claims_year}</td>
                <td class="p-2">${item.video_tat}</td>
                <td class="p-2 ${item.short_partial === 'Yes' ? 'text-green-700' : 'text-red-700'}">${item.short_partial}</td>
                <td class="p-2 ${item.artificial_low_lighting === 'Yes' ? 'text-green-700' : 'text-red-700'}">${item.artificial_low_lighting}</td>
                <td class="p-2">${item.scar_declaration}</td>
                <td class="p-2 ${item.commercial === 'Yes' ? 'text-green-700' : 'text-red-700'}">${item.commercial}</td>
                <td class="p-2">${item.video_approval}</td>
                <td class="p-2 ${item.brand_new_3_3 === 'Yes' ? 'text-green-700' : 'text-red-700'}">${item.brand_new_3_3}</td>
                <td class="p-2 ${item.old_3_3 === 'Yes' ? 'text-green-700' : 'text-red-700'}">${item.old_3_3}</td>
            `;
            tableBody.appendChild(row);
        });
    }

    function sortTable(column, order) {
        const sortedData = [...insuranceData].sort((a, b) => {
            const aValue = String(a[column]).toLowerCase();
            const bValue = String(b[column]).toLowerCase();
            if (order === 'asc') {
                return aValue > bValue ? 1 : -1;
            } else {
                return aValue < bValue ? 1 : -1;
            }
        });
        populateTable(sortedData);
    }

    document.querySelectorAll('.vi-claim-page .table-header').forEach(header => {
        header.addEventListener('click', () => {
            const column = header.dataset.column;
            const currentOrder = header.classList.contains('sort-asc') ? 'desc' : 'asc';
            
            document.querySelectorAll('.vi-claim-page .table-header').forEach(h => {
                h.classList.remove('sort-asc', 'sort-desc');
                h.classList.add('sort-icon');
            });
            
            header.classList.remove('sort-icon');
            header.classList.add(currentOrder === 'asc' ? 'sort-asc' : 'sort-desc');
            
            sortTable(column, currentOrder);
        });
    });

    document.getElementById('searchInput').addEventListener('input', (e) => {
        const searchTerm = e.target.value.toLowerCase();
        const filteredData = insuranceData.filter(item => 
            item.insurer_name.toLowerCase().includes(searchTerm)
        );
        populateTable(filteredData);
    });

    window.scrollTableHorizontally = function(direction) {
      const tableWrapper = document.getElementById('insuranceTableWrapper');
      const scrollAmount = 200;
      if (direction === 'left') {
        tableWrapper.scrollLeft -= scrollAmount;
      } else {
        tableWrapper.scrollLeft += scrollAmount;
      }
    };
  </script>
</body>
</html>
