# Satyata (सत्यता) 🛡️
**Automated Multi-Signal Forensic Image Analysis Pipeline**

Satyata is an n8n-based forensic pipeline that detects deepfakes, AI-generated images, and misclaimed media. It cross-references metadata, computer vision models, and multi-modal AI (Gemini) to provide a "Trust Score" for any image.

## ✨ Features
- **EXIF Analysis:** Detects AI software signatures, modified dates, and camera metadata.
- **Deepfake Detection:** Utilizes `Wvolf/ViT_Deepfake_Detection` (98%+ accuracy).
- **AI-Gen Detection:** Utilizes `dima806/ai_vs_real_image_detection`.
- **Reverse Image OSINT:** Powered by SerpAPI to find the earliest web appearances.
- **Gemini Forensics:** Uses Gemini 2.5 Flash to act as an expert forensic analyst.
- **HTML Reporting:** Beautiful email reports sent via Resend.

---

## 🛠️ Setup
1. **Import:** Import `fakey2.json` into your n8n instance.
2. **API Keys:** Add your keys to the following nodes:
   - Hugging Face (Wvolf & dima806)
   - ImgBB (For public image hosting)
   - SerpAPI (For Google Reverse Search)
   - Gemini API
   - Resend API (For email reporting)

---

## 📮 Postman Walkthrough
Use this to test the workflow once it's active.

### 1. Request Details
- **Method:** `POST`
- **URL:** `[Your-n8n-Webhook-URL]`
- **Body Type:** `form-data`

### 2. Body Parameters
| Key | Type | Value | Description |
| :--- | :--- | :--- | :--- |
| **`data`** | **File** | `[Select Image]` | The image you want to analyze. |
| **`caption`** | Text | "Staged photo on Mars" | (Optional) The user claim about the image. |
| **`claimDate`** | Text | "2024-05-10" | (Optional) The date the image is claimed to be from. |

### 3. Execution
Hit **Send**. You will receive a JSON response containing the **Trust Score** and a detailed breakdown, followed by a beautiful HTML email in your inbox.

