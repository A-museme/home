---
layout: post
title: "VoIP Chrome Extension with CRM Integration"
date: 2024-09-27
categories: projects
---

<div class="collapsible-section">
    <h2 class="collapsible-header" style="color: red; font-weight: bold; text-shadow: 0 0 5px rgba(255, 0, 0, 0.7);">
        Code Deep Dive & Insights
    </h2>
    <button class="expand-button" style="background-color: #ccc; color: green; border: none; cursor: pointer; padding: 8px 12px; border-radius: 4px;">
        Open Code Review
    </button>
    <div class="collapsible-content" style="display: none; overflow: hidden; transition: max-height 0.3s ease; max-height: 0;">
        <p>Sure! Let's break down the provided JavaScript code step by step in an educational manner, ideal for someone new to programming. We'll highlight the key concepts and functionalities.</p>

        <h3>1. <strong>Regular Expression for Phone Numbers</strong></h3>
        <pre><code>const phoneRegex = /(\+?1[-.\s]?)?\(?\d{3}\)?[-.\s]\d{3}[-.\s]\d{4}/g;</code></pre>
        <p><strong>What It Does</strong>: This line defines a <strong>regular expression (regex)</strong> to identify phone numbers in various common formats.</p>
        <p><strong>Explanation</strong>:</p>
        <ul>
            <li><code>\+?</code>: Matches an optional plus sign (for international codes).</li>
            <li><code>1[-.\s]?</code>: Matches the country code for the U.S. (optional) followed by a separator (dash, dot, or space).</li>
            <li><code>\(?\d{3}\)?</code>: Matches an area code (3 digits), which can be enclosed in parentheses.</li>
            <li><code>[-.\s]</code>: Matches a separator (dash, dot, or space).</li>
            <li><code>\d{3}</code>: Matches the next 3 digits.</li>
            <li><code>[-.\s]</code>: Matches another separator.</li>
            <li><code>\d{4}</code>: Matches the final 4 digits of the phone number.</li>
        </ul>
        <p><strong>Result</strong>: The regex can match numbers like <code>123-456-7890</code>, <code>(123) 456-7890</code>, and <code>+1 123 456 7890</code>.</p>

        <h3>2. <strong>Set to Track Processed Elements</strong></h3>
        <pre><code>let processedElements = new Set();</code></pre>
        <p><strong>What It Does</strong>: This line initializes a <strong>Set</strong> to keep track of elements that have already been processed.</p>
        <p><strong>Why It Matters</strong>: It prevents duplicate buttons from being added next to phone numbers that have already been tagged.</p>

        <h3>3. <strong>Parsing Visible Text Content</strong></h3>
        <pre><code>function parseVisibleTextContent() { ... }</code></pre>
        <p><strong>What It Does</strong>: This function uses a <strong>TreeWalker</strong> to find all visible text nodes in the document.</p>
        <p><strong>Key Concepts</strong>:</p>
        <ul>
            <li><code>document.createTreeWalker</code>: Creates a walker to traverse nodes in the DOM.</li>
            <li><code>NodeFilter.SHOW_TEXT</code>: Filters to show only text nodes.</li>
            <li><code>acceptNode</code>: Checks if the parent of the node is visible (i.e., <code>offsetParent !== null</code>).</li>
        </ul>
        <p><strong>Outcome</strong>: The function returns an array of text nodes that are currently visible on the page.</p>

        <h3>4. <strong>Check for Existing Phone Buttons</strong></h3>
        <pre><code>function phoneNumberAlreadyTagged(node, phoneNumber) { ... }</code></pre>
        <p><strong>What It Does</strong>: This function checks if there is already a button next to the detected phone number.</p>
        <p><strong>Why It Matters</strong>: It ensures we don’t add multiple buttons next to the same phone number.</p>

        <h3>5. <strong>Creating the Phone Button</strong></h3>
        <pre><code>function createPhoneButtonInline(phoneNumber, node) { ... }</code></pre>
        <p><strong>What It Does</strong>: This function creates and injects a button next to the detected phone number in the DOM.</p>
        <p><strong>Key Concepts</strong>:</p>
        <ul>
            <li><strong>Create Elements</strong>: Uses <code>document.createElement</code> to create a <code>span</code> and an <code>img</code> for the button.</li>
            <li><strong>Styling</strong>: Applies CSS styles to position the button relative to the phone number.</li>
            <li><strong>Event Listeners</strong>: Sets up <code>mouseover</code> and <code>mouseout</code> events to change the button’s appearance.</li>
            <li><strong>Functionality</strong>: On clicking the button, it sends a message to the Chrome extension to handle a phone lead.</li>
        </ul>

        <h3>6. <strong>Detecting Phone Numbers</strong></h3>
        <pre><code>function detectPhoneNumbers() { ... }</code></pre>
        <p><strong>What It Does</strong>: This function scans for phone numbers in the text nodes and creates buttons for them.</p>
        <p><strong>Key Concepts</strong>:</p>
        <ul>
            <li><strong>Logging</strong>: Uses <code>console.log</code> to indicate the start and end of the scanning process.</li>
            <li><strong>Match Phone Numbers</strong>: Uses the regex to find and process detected phone numbers.</li>
        </ul>

        <h3>7. <strong>Initial Scan and Mutation Observer</strong></h3>
        <pre><code>detectPhoneNumbers(); ...</code></pre>
        <p><strong>What It Does</strong>: The initial call to <code>detectPhoneNumbers()</code> scans the page for phone numbers when the extension is loaded.</p>
        <p><strong>MutationObserver</strong>: This observes changes in the DOM (e.g., when new content is loaded) and triggers a re-scan to find newly added phone numbers.</p>
        <p><strong>Why It Matters</strong>: This ensures that dynamically loaded content (like AJAX calls) is also checked for phone numbers.</p>

        <h3>Summary</h3>
        <p>This code allows a Chrome extension to detect phone numbers on a webpage, injects clickable buttons next to them, and manages interactions with those buttons.</p>
        <p>The use of regex, DOM manipulation, and event handling demonstrates core JavaScript concepts and the power of browser extensions in enhancing user interactions.</p>
    </div>
</div>

<style>
.collapsible-section .collapsible-header {
    cursor: pointer;
    padding: 10px;
    background-color: #f0f0f0; /* Light gray background */
    border: 1px solid #ccc; /* Light gray border */
    border-radius: 5px; /* Rounded corners */
    margin: 5px 0; /* Space between sections */
}

.collapsible-section .collapsible-content {
    padding: 10px;
    border-top: 1px solid #ccc; /* Border on top of content */
}

/* Animation for expanding/collapsing */
.collapsible-content.open {
    max-height: 500px; /* Arbitrary high value to allow smooth animation */
    transition: max-height 0.5s ease-in-out;
}

.collapsible-content.closed {
    max-height: 0;
    transition: max-height 0.5s ease-in-out;
}
</style>

<script>
    // Script to handle the collapsible functionality
    document.querySelector('.expand-button').addEventListener('click', function() {
        const content = this.parentNode.querySelector('.collapsible-content');
        if (content.style.display === "block") {
            content.style.display = "none";
            content.classList.remove('open');
            content.classList.add('closed');
            this.innerHTML = 'Open Code Review'; // Change text to Open Code Review
        } else {
            content.style.display = "block";
            content.classList.remove('closed');
            content.classList.add('open');
            this.innerHTML = 'Close Code Review'; // Change text to Close Code Review
        }
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