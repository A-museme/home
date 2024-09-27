---
layout: post
title: "VoIP Chrome Extension with CRM Integration"
date: 2024-09-27
categories: projects
---

<div class="collapsible-section">
    <button class="collapsible-button" style="background-color: grey; color: green; border: none; padding: 10px; cursor: pointer; border-radius: 5px;">
        Open Code Review
    </button>
    <div class="collapsible-content" style="display: none; overflow: hidden; transition: max-height 0.3s ease-out;">
        <p>Sure! Let's break down the provided JavaScript code step by step in an educational manner, ideal for someone new to programming. We'll highlight the key concepts and functionalities.</p>

        <h3>1. <strong>Regular Expression for Phone Numbers</strong></h3>
        <pre><code>const phoneRegex = /(\+?1[-.\s]?)?\(?\d{3}\)?[-.\s]\d{3}[-.\s]\d{4}/g;</code></pre>
        <p><strong>What It Does</strong>: This line defines a <strong>regular expression (regex)</strong> to identify phone numbers in various common formats.</p>
        
        <!-- Continue adding your sections here -->
        
    </div>
</div>

<script>
    const collapsibleButtons = document.querySelectorAll('.collapsible-button');
    
    collapsibleButtons.forEach(button => {
        button.addEventListener('click', function() {
            const content = this.nextElementSibling;
            content.style.display = content.style.display === 'block' ? 'none' : 'block';
        });
    });
</script>

# VoIP Chrome Extension with CRM Integration

**Technologies Used:**  
![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?logo=javascript&logoColor=black) ![Chrome Extensions API](https://img.shields.io/badge/-Chrome_Extensions_API-4285F4?logo=google-chrome&logoColor=white) ![Twilio API](https://img.shields.io/badge/-Twilio_API-F22F46?logo=twilio&logoColor=white) ![HTML/CSS](https://img.shields.io/badge/-HTML/CSS-E34F26?logo=html5&logoColor=white) ![OAuth](https://img.shields.io/badge/-OAuth-4285F4?logo=oauth&logoColor=white) ![Web Scraping](https://img.shields.io/badge/-Web_Scraping-239120?logo=python&logoColor=white) ![Google APIs](https://img.shields.io/badge/-Google_APIs-4285F4?logo=google&logoColor=white)

## Overview

Developed a custom Google Chrome extension to streamline communication processes within the CRM by integrating VoIP functionality directly into the browser. The extension allowed users to make calls through their Twilio account using `tel:` links on web pages, adding leads to the CRM if they didn’t already exist, and automating data entry for call logging.

## Key Features

- **Click-to-Call Integration:** Detected phone numbers on any webpage and displayed an interactive button next to each number, allowing users to initiate VoIP calls directly from their browser using Twilio's API.
- **CRM Integration:** The extension automatically checked if a phone number existed in the CRM. If not, the user could create a new lead with basic details (name, number, address) using structured data extracted from the webpage.
- **Lead Importing & Data Scraping:** Integrated web scraping best practices to detect and extract relevant lead data (e.g., first name, last name, company) from the current webpage, ensuring accurate and efficient data entry.
- **Notes & Call Logs:** Allowed users to add notes to each call, which were saved directly to the CRM system, including timestamps and call details.

---

## Process

### Research & Planning

- Began by analyzing existing CRM workflows and understanding pain points in the sales process. Identified inefficiencies in manually dialing numbers and logging calls into the CRM.
- Planned the architecture for integrating VoIP services using Twilio's API and extending Chrome’s functionality to interact with web pages and phone numbers dynamically.

### Development

1. **Initial Setup:** Set up the Chrome Extension project, defining manifest files and core background/event scripts. Integrated the Twilio API to handle call initiation directly from the browser.
2. **Click-to-Call Feature:** Implemented logic to detect phone numbers (`tel:` links) on webpages using JavaScript and DOM manipulation. Added a clickable button next to each number to initiate a call.
3. **CRM Integration:** Leveraged APIs to check if the phone number already existed in the CRM and provided a popup for users to input lead details when the number was new. This data was then automatically added to the CRM via API calls.
4. **Data Scraping:** Developed web scraping logic to extract relevant details such as name, phone number, and company information directly from the page, improving the user’s ability to quickly generate new leads.
5. **Notes & Logging:** Created a call logging system that recorded the call details and any notes entered by the user. This information was linked to the CRM for future reference and reporting.

### Testing & QA

- Extensively tested the extension across multiple websites to ensure phone number detection worked consistently. Debugged issues related to DOM parsing and made adjustments for edge cases, such as different number formats.
- Verified Twilio call initiation and CRM integration workflows to ensure smooth user experiences and proper data flow.

### Deployment & Feedback

- Released the extension for internal sales team usage. Gathered feedback on the UI, functionality, and efficiency, which led to further optimization of call logs and lead creation processes.
- Ensured compliance with data security standards, particularly around handling customer data and CRM integration.

---

This project provided significant value by reducing manual data entry, improving workflow efficiency, and seamlessly integrating VoIP services within the sales process.
s