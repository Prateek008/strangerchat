# StrangerChat (free random chat)

React + Tailwind + Node + Socket.io. Ek hi service frontend aur backend dono serve karti hai.

## Local chalane ke liye
```bash
npm install
npm --prefix client install
npm run dev        # client: http://localhost:5173, server: :3000
```
Do browser tabs kholo, dono me "Start chat" dabao, match ho jayenge.

## Deploy (Render, free)
1. Folder ko GitHub repo me push karo
2. render.com -> New -> **Web Service** -> repo select karo (render.yaml auto-detect hota hai)
   - Build: `npm install && npm run build`
   - Start: `npm start`
   - Plan: Free
3. Deploy hone ke baad `https://yourapp.onrender.com` pe site live

### Sleep problem
Free plan 15 min inactivity ke baad sleep ho jata hai. UptimeRobot (free) se `https://yourapp.onrender.com/health` ko har 5 min ping karo.

### Optional: reports MongoDB me save karna
MongoDB Atlas M0 (free) me cluster banao, connection string Render me env var `MONGO_URI` me daalo. Na daalo to bhi sab chalta hai (reports sirf server logs me aayenge).

## Features
- Random 1-on-1 matching, typing indicator, emoji, dark mode, online count
- New chat / Stop / Report (3 alag users ke report pe 24h IP ban)
- Rate limit (5 sec me max 6 messages), 500 char limit
- Links auto-remove, basic gaali filter (`BAD_WORDS` in `server/index.js` me aur words add kar sakte ho)
- Text only. Image sharing jaan-bujh ke nahi hai

## Dhyan rakhne wali baatein
- Bans/reports in-memory hain, server restart pe reset ho jayenge (MongoDB me sirf report log save hota hai)
- Ek hi server instance ke liye bana hai. Zyada traffic pe Redis adapter chahiye
- 18+ gate sirf self-declaration hai. Public launch se pehle Terms/Privacy page aur apne desh ke rules check kar lena
