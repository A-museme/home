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
    <div class="collapsible-content" style="display: none;">
        <p>
        Sure! Let's break down the provided JavaScript code step by step in an educational manner, ideal for someone new to programming. We'll highlight the key concepts and functionalities.

### 1. **Regular Expression for Phone Numbers**
```javascript
const phoneRegex = /(\+?1[-.\s]?)?\(?\d{3}\)?[-.\s]\d{3}[-.\s]\d{4}/g;
```
- **What It Does**: This line defines a **regular expression (regex)** to identify phone numbers in various common formats. 
- **Explanation**:
  - `\+?`: Matches an optional plus sign (for international codes).
  - `1[-.\s]?`: Matches the country code for the U.S. (optional) followed by a separator (dash, dot, or space).
  - `\(?\d{3}\)?`: Matches an area code (3 digits), which can be enclosed in parentheses.
  - `[-.\s]`: Matches a separator (dash, dot, or space).
  - `\d{3}`: Matches the next 3 digits.
  - `[-.\s]`: Matches another separator.
  - `\d{4}`: Matches the final 4 digits of the phone number.
- **Result**: The regex can match numbers like `123-456-7890`, `(123) 456-7890`, and `+1 123 456 7890`.

### 2. **Set to Track Processed Elements**
```javascript
let processedElements = new Set();
```
- **What It Does**: This line initializes a **Set** to keep track of elements that have already been processed.
- **Why It Matters**: It prevents duplicate buttons from being added next to phone numbers that have already been tagged.

### 3. **Parsing Visible Text Content**
```javascript
function parseVisibleTextContent() {
    let textNodes = [];
    const walker = document.createTreeWalker(document.body, NodeFilter.SHOW_TEXT, {
        acceptNode(node) {
            return node.parentNode.offsetParent !== null ? NodeFilter.FILTER_ACCEPT : NodeFilter.FILTER_REJECT;
        }
    });

    let node;
    while ((node = walker.nextNode())) {
        textNodes.push(node);
    }
    return textNodes;
}
```
- **What It Does**: This function uses a **TreeWalker** to find all visible text nodes in the document.
- **Key Concepts**:
  - `document.createTreeWalker`: Creates a walker to traverse nodes in the DOM.
  - `NodeFilter.SHOW_TEXT`: Filters to show only text nodes.
  - `acceptNode`: Checks if the parent of the node is visible (i.e., `offsetParent !== null`).
- **Outcome**: The function returns an array of text nodes that are currently visible on the page.

### 4. **Check for Existing Phone Buttons**
```javascript
function phoneNumberAlreadyTagged(node, phoneNumber) {
    const nextSibling = node.nextSibling;
    return nextSibling && nextSibling.nodeName === "BUTTON" && nextSibling.title.includes(phoneNumber);
}
```
- **What It Does**: This function checks if there is already a button next to the detected phone number.
- **Why It Matters**: It ensures we don’t add multiple buttons next to the same phone number.

### 5. **Creating the Phone Button**
```javascript
function createPhoneButtonInline(phoneNumber, node) {
    if (!node || processedElements.has(node)) return;

    const span = document.createElement("span");
    // ... [Styling code]
    
    const svgButton = document.createElement("img");
    svgButton.src = chrome.runtime.getURL("icon.svg");
    // ... [Button event listeners and styling]
    
    processedElements.add(node);
    console.log(`[PhoneDetection] Injected button for: ${phoneNumber}`);
}
```
- **What It Does**: This function creates and injects a button next to the detected phone number in the DOM.
- **Key Concepts**:
  - **Create Elements**: Uses `document.createElement` to create a `span` and an `img` for the button.
  - **Styling**: Applies CSS styles to position the button relative to the phone number.
  - **Event Listeners**: Sets up `mouseover` and `mouseout` events to change the button’s appearance.
  - **Functionality**: On clicking the button, it sends a message to the Chrome extension to handle a phone lead.

### 6. **Detecting Phone Numbers**
```javascript
function detectPhoneNumbers() {
    console.log("[PhoneDetection] Scanning for phone numbers...");
    const textNodes = parseVisibleTextContent();
    textNodes.forEach(node => {
        const matches = node.nodeValue.match(phoneRegex);
        if (matches) {
            matches.forEach(phoneNumber => {
                createPhoneButtonInline(phoneNumber.trim(), node);
            });
        }
    });
    console.log("[PhoneDetection] Phone number scan complete.");
}
```
- **What It Does**: This function scans for phone numbers in the text nodes and creates buttons for them.
- **Key Concepts**:
  - **Logging**: Uses `console.log` to indicate the start and end of the scanning process.
  - **Match Phone Numbers**: Uses the regex to find and process detected phone numbers.

### 7. **Initial Scan and Mutation Observer**
```javascript
detectPhoneNumbers();

const observer = new MutationObserver(mutations => {
    detectPhoneNumbers();
});
observer.observe(document.body, { childList: true, subtree: true });
```
- **What It Does**: The initial call to `detectPhoneNumbers()` scans the page for phone numbers when the extension is loaded. 
- **MutationObserver**: This observes changes in the DOM (e.g., when new content is loaded) and triggers a re-scan to find newly added phone numbers.
- **Why It Matters**: This ensures that dynamically loaded content (like AJAX calls) is also checked for phone numbers.

### Summary
- This code allows a Chrome extension to detect phone numbers on a webpage, injects clickable buttons next to them, and manages interactions with those buttons. 
- The use of regex, DOM manipulation, and event handling demonstrates core JavaScript concepts and the power of browser extensions in enhancing user interactions.
        </p>
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
</style>

<script>
    // Script to handle the collapsible functionality
    document.querySelectorAll('.collapsible-header').forEach(header => {
        header.addEventListener('click', function() {
            const content = this.nextElementSibling;
            content.style.display = content.style.display === "block" ? "none" : "block";
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