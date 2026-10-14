# Troubleshooting Guide

## File Upload Fails

If file uploads are failing with "Upload failed" error, check these:

### 1. Is MongoDB Running?
The app requires MongoDB to store file metadata.

**Check if MongoDB is installed:**
```powershell
mongod --version
```

**Start MongoDB (if installed):**
```powershell
# Start MongoDB service
net start MongoDB
```

**Or install MongoDB:**
- Download: https://www.mongodb.com/try/download/community
- Or use MongoDB Atlas (cloud): https://www.mongodb.com/cloud/atlas

### 2. Check Server Status
Visit: http://localhost:5000/api/health

Should show:
```json
{
  "status": "ok",
  "mongodb": "connected",
  "port": 5000
}
```

If `mongodb: "disconnected"`, the server can't reach MongoDB.

### 3. Check Authentication
- Open browser DevTools (F12) → Network tab
- Try uploading a file
- Look at the `/api/files/upload` request
- Check if `Authorization: Bearer <token>` header is present
- If 401 error: You may need to log in again

### 4. Check Server Logs
After attempting upload, check the terminal running `node server.js` for:
```
Upload attempt - user: <email> file: <filename>
```

If you see "Auth middleware: No token provided", the frontend isn't sending the token.

### 5. Common Fixes

**Clear localStorage and re-login:**
```javascript
// In browser console (F12):
localStorage.clear();
// Then log in again
```

**Restart the server:**
```powershell
# Stop server (Ctrl+C in terminal)
# Start again:
cd server
node server.js
```

**Check uploads directory exists:**
The server creates `server/uploads/` automatically, but verify it exists.

## Quick Test Without MongoDB

If you don't have MongoDB installed yet, you can test with a mock:

1. Comment out the `PatientFile` save in `server/routes/files.js`
2. Return a fake success response
3. This lets you test the upload flow while setting up MongoDB

---

## Still Having Issues?

1. Check browser console (F12) for errors
2. Check server terminal for error logs
3. Verify you're logged in (token exists in localStorage)
4. Try with a small PDF or image (< 1MB)
