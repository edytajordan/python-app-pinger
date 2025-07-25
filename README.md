# 🕒 Render Ping Keeper

This repo uses **GitHub Actions** to keep a Flask app hosted on **Render.com** awake during specific hours (5 AM – 11 PM EST).  
It does this by:

- Running every 15 minutes
- Waiting a random 2-5 minutes
- Sending a `GET` request to your app’s `/healthz` endpoint

---

## ✅ Why?

Render's free tier sleeps apps after 15 minutes of inactivity. This workflow simulates natural traffic to prevent cold starts — without breaking Render’s usage policy.

---

## 🔧 How It Works

- **GitHub Actions Workflow**: `.github/workflows/ping.yml`
- **Random delay**: 300–600 seconds (5–10 min)
- **Time restriction**: Only active between 5:00 AM and 11:00 PM Eastern Time

---

## 🔁 Customization

- Change your Flask app URL in `.github/workflows/ping.yml`:
  ```bash
  curl -s https://your-flask-app.onrender.com/healthz
  ```

- Update hours by modifying:
  ```bash
  if [ $NOW -ge 5 ] && [ $NOW -lt 23 ]; then
  ```

---

## 🛠 Setup Instructions

1. Fork or clone this repository
2. Edit the `curl` URL to match your own Flask app
3. Push to GitHub
4. Go to the **Actions tab** to monitor workflow runs

> ⚠️ **For unlimited GitHub Actions minutes**, use a public repo (private repos are limited to 500 minutes/month on free plans)

---

## 📄 License

MIT — free to use, modify, and share.
