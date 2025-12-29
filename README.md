# Scaminator — E-Commerce Fraud Detector

**Demo Video:** https://youtu.be/qQHVDAPuuI4?si=Otpt7rtn-2VJ8Pj6

## Project Overview

Scaminator is a Chrome Extension–based E-Commerce Fraud Detection System developed as the final term project for SENG472. It helps users determine whether an online product listing is safe, suspicious, or likely a scam using LLM grounding techniques, multi-agent reasoning, and real-time web scraping.

Instead of relying on a single black-box model, Scaminator mimics how a careful human shopper evaluates products — by checking reviews, seller credibility, pricing anomalies, and social sentiment from multiple independent sources.

## Key Features

### Smart Product Evaluation

- Analyzes product listings from Trendyol and external e-commerce websites
- Examines multiple aspects:
  - Product descriptions
  - Seller profiles
  - User reviews
  - Price consistency
  - Social sentiment

### Multi-Agent LLM Architecture

- Specialized investigator agents, each responsible for a single signal:
  - Product description analysis
  - Review authenticity
  - Seller reliability
  - Social sentiment
  - Price anomaly detection
- Controller agents verify quality and trigger re-analysis if needed
- A Final Judge agent synthesizes all evidence into a single verdict

### Clear Risk Verdicts

Each product is labeled as:
- **Green (Safe)** — Product appears legitimate
- **Orange (Suspicious)** — Proceed with caution
- **Red (Likely Scam)** — High risk of fraud

Every verdict includes explainable reasoning, not just a label.

### Chrome Extension Integration

- Works directly on the product page
- Automatically evaluates the current browser tab
- Displays instant results in the popup

### External Site Support

For non-Trendyol websites:
- **Akakçe** price comparison to detect inflated or unrealistic pricing
- **Ekşi Sözlük** sentiment analysis to capture real user opinions

## System Architecture

```
User Input (URL)
        ↓
 Scraper Layer
        ↓
 Investigation Agents
        ↓
 Controller Agents
        ↓
 Final Judge Agent
        ↓
 Verdict Output (Green / Orange / Red)
```

The system is fully modular, making it easy to extend with new agents (e.g., image analysis, logistics tracking).

## Technologies Used

### Frontend
- Chrome Extension (HTML, CSS, JavaScript)
- Streamlit (Web interface)

### Backend
- Python
- FastAPI

### LLM & Grounding
- Google Gemini API
- Multi-agent architecture
- Function calling
- Structured JSON outputs

### Scraping & Data
- Selenium
- BeautifulSoup4
- Crawl4AI

### Validation
- Pydantic for strict schema enforcement

## Grounding Techniques Applied

### Multi-Agent Reasoning
Each agent focuses on a single, well-defined task.

### Retrieval-Augmented Generation (RAG)
All LLM responses are grounded in fresh, product-specific scraped data.

### Structured Output Enforcement
All agents return deterministic JSON outputs, ensuring:
- Explainability
- Reliability
- Easy frontend rendering

## Team Members

- **Ahmet Alp Malkoç** — Chrome Extension development, scrapers and backend, multi-agent communication, external fraud pipeline, Akakçe & Ekşi scrapers
- **Berk Belhan** — Backend architecture, multi-agent pipeline, final judge logic
- **Kutay Becerir** — UI/UX design, Streamlit frontend, Chrome extension interface
- **Utku Erdoğanaras** — Prompt engineering, controller-agent calibration, Trendyol scraping

**Supervisor:** Dr. Murat Karakaya

## Evaluation Highlights

- Target accuracy: ≥ 90% on mixed real/fraudulent listings
- False positive rate: ≤ 10%
- Average response time: < 20 seconds
- Structured output compliance: 100%

## Future Improvements

- Vision-based fraud detection (image mismatch analysis)
- Logistics and delivery anomaly tracking
- Faster inference via parallel agent execution
- Alternative product recommendations

## Course Information

- **Course:** SENG472 – Term Project, under the supervision of Dr. Murat Karakaya
- **Project Title:** E-Commerce Fraud Detector (Scaminator)
- **Submission Date:** June 10, 2025
