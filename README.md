# True Seller AI Bot 1

Bot 1 is for WhatsApp number:

+8801620922977

## What is already included

- Flask app
- Gemini AI brain
- Bangla / English / Banglish replies
- True Seller website scraping
- Product/image/price text extraction
- 60-minute knowledge refresh
- Optional Facebook Graph API knowledge
- Order database (SQLite)
- Order fields: name, phone, full address, product
- 3-day review-job worker
- WhatsApp webhook skeleton
- `/test-chat` endpoint for testing the AI before WhatsApp API is connected

## Important

The WhatsApp Cloud API is NOT connected yet. That is intentional because the WhatsApp
API credentials have not been created yet.

The Facebook Page may require a Meta Graph API Page access token for reliable post/caption
reading. Public Facebook HTML is often limited, so the app safely falls back instead of
inventing information.

## Run locally

1. Install Python.
2. Copy `.env.example` to `.env`.
3. Put your Gemini API key in `GEMINI_API_KEY`.
4. Install packages:

   pip install -r requirements.txt

5. Start:

   python app.py

6. Open:

   http://127.0.0.1:10000/

## Test the AI without WhatsApp

Send POST JSON to:

POST /test-chat

Example:

{
  "message": "এই থ্রি পিসের দাম কত?"
}

## Render deployment

1. Create a new Web Service.
2. Connect this project/repository.
3. Build Command:

   pip install -r requirements.txt

4. Start Command:

   gunicorn app:app

5. Add Environment Variables from `.env.example`.
6. Put your Gemini API key into `GEMINI_API_KEY`.
7. Keep WHATSAPP_TOKEN and PHONE_NUMBER_ID empty for now.
8. Deploy.

## Later: WhatsApp

When the WhatsApp Cloud API is ready, we will fill:

- WHATSAPP_TOKEN
- PHONE_NUMBER_ID
- WHATSAPP_VERIFY_TOKEN

Then the webhook URL will be:

https://YOUR-RENDER-DOMAIN/webhook

The actual WhatsApp send/receive adapter should be enabled only after the Cloud API
credentials and Meta webhook configuration are ready.

## Later: Bot 2

Bot 2 will use the same code. Only these environment values change:

WHATSAPP_TOKEN
PHONE_NUMBER_ID

