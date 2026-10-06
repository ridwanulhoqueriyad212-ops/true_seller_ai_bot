# True Seller AI Bot — Fixed Version

This version keeps the original project structure and features, with these fixes:

1. Website data refreshes automatically when the Render service starts.
2. Website data refreshes again every 60 minutes.
3. `/refresh` works from a normal browser (GET) as well as POST.
4. `/test-chat` can now be tested from a normal browser:
   `https://YOUR-SERVICE.onrender.com/test-chat?q=hello`
5. Gemini configuration is read from Render Environment Variables.
6. WhatsApp Cloud API remains optional until you create/connect it.
7. Orders use SQLite; no Google Sheet is required.

## Render

Build:
`pip install -r requirements.txt`

Start:
`gunicorn app:app`

Environment variables:
- GEMINI_API_KEY
- GEMINI_MODEL
- WEBSITE_URL
- FACEBOOK_PAGE_URL
- FACEBOOK_PAGE_ID
- FACEBOOK_PAGE_ACCESS_TOKEN (optional for now)
- WHATSAPP_TOKEN (later)
- PHONE_NUMBER_ID (later)
- WHATSAPP_VERIFY_TOKEN
- REFRESH_MINUTES
- DB_PATH
- PORT

## Important

Do not put API keys into GitHub. Put them only in Render Environment Variables.

After deploying, check:
`/health`

You want:
`"gemini_configured": true`
and, after the startup refresh finishes:
`"products_loaded":` greater than 0.
