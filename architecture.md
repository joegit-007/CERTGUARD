# CertGuard — Technical Architecture

## System Overview

```
User uploads document image
        │
        ▼
  Frontend (index.html)
        │
        ├── ELA Canvas Visualization (local, real-time)
        │
        └── Anthropic Claude API (claude-sonnet-4-20250514)
                │
                ├── Error Level Analysis signal
                ├── Copy-Move Detection signal
                ├── Signature Verification signal
                ├── OCR Text Consistency signal
                └── Wavelet Analysis signal
                        │
                        ▼
              JSON Structured Verdict
                        │
                        ▼
              UI renders: verdict banner
                          confidence meters
                          pipeline cards
                          typewriter AI report
```

## API Call Structure

```json
POST https://api.anthropic.com/v1/messages
{
  "model": "claude-sonnet-4-20250514",
  "max_tokens": 1000,
  "system": "<forensics system prompt with language instruction>",
  "messages": [{
    "role": "user",
    "content": [
      { "type": "image", "source": { "type": "base64", ... } },
      { "type": "text", "text": "Run full forensic analysis..." }
    ]
  }]
}
```

## Response Schema

```json
{
  "verdict": "AUTHENTIC | SUSPICIOUS | FORGED",
  "forgery_probability": 0-100,
  "ela": { "score": 0-100, "status": "clean|suspicious|tampered", "finding": "..." },
  "copy_move": { "score": 0-100, "status": "clean|suspicious|tampered", "finding": "..." },
  "signature": { "score": 0-100, "status": "genuine|uncertain|forged", "finding": "..." },
  "ocr": { "score": 0-100, "status": "consistent|inconsistent", "finding": "..." },
  "wavelet": { "score": 0-100, "status": "normal|anomalous", "finding": "..." },
  "summary": "Human-readable forensic summary in target language",
  "evidence": ["Point 1", "Point 2", "Point 3"]
}
```

## Multilingual Implementation

Language selection changes:
1. All UI text via JavaScript translation object (8 languages)
2. System prompt instructs Claude to respond in chosen language
3. `document.body.style.direction` toggled for Arabic RTL

## ELA Visualization Algorithm

```javascript
// Per-pixel transform:
brightness = (R + G + B) / 3
ela_value = |brightness - 128| * 3
output_R = min(255, ela_value * 2)
output_G = min(255, ela_value * 0.4)
output_B = min(255, ela_value * 1.6)
```

This highlights compression anomalies as red/purple hot spots.
