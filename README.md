# Patient Information Chatbot

A modern, responsive chatbot interface for managing patient information through n8n webhooks. Features a beautiful gradient UI and supports markdown, JSON, and text responses.

## 🌟 Features

- **Multi-format Support**: Handles markdown, JSON, and plain text responses from n8n
- **Beautiful UI**: Purple gradient theme with smooth animations
- **Responsive Design**: Works perfectly on desktop and mobile devices
- **Markdown Rendering**: Full support for tables, lists, code blocks, and more
- **Patient Data Cards**: Elegant display for patient information
- **Quick Actions**: Pre-configured buttons for common queries
- **Connection Status**: Real-time webhook connection monitoring
- **Settings Management**: Easy webhook URL configuration

## 🚀 Deploy to GitHub Pages

### Step 1: Create a GitHub Repository

1. Go to [GitHub.com](https://github.com) and sign in
2. Click the **"+"** icon in the top right corner
3. Select **"New repository"**
4. Name your repository (e.g., `patient-chatbot`)
5. Make it **Public** (required for free GitHub Pages)
6. Click **"Create repository"**

### Step 2: Upload the Files

#### Option A: Using GitHub Web Interface (Easiest)

1. In your new repository, click **"uploading an existing file"**
2. Drag and drop the `index.html` file
3. Add commit message: "Initial chatbot deployment"
4. Click **"Commit changes"**

#### Option B: Using Git Command Line

```bash
# Clone your repository
git clone https://github.com/YOUR_USERNAME/patient-chatbot.git
cd patient-chatbot

# Add the index.html file to the repository
# Copy index.html to this folder, then:
git add index.html
git commit -m "Initial chatbot deployment"
git push origin main
```

### Step 3: Enable GitHub Pages

1. In your repository, click **"Settings"** (in the top menu)
2. Scroll down to **"Pages"** section (in left sidebar)
3. Under **"Source"**, select **"Deploy from a branch"**
4. Choose branch: **"main"** (or "master")
5. Choose folder: **"/ (root)"**
6. Click **"Save"**

### Step 4: Access Your Chatbot

1. GitHub will provide your site URL at the top of the Pages settings
2. Format: `https://YOUR_USERNAME.github.io/patient-chatbot/`
3. It may take 5-10 minutes for the first deployment
4. The site will automatically update when you push changes

## 🔧 n8n Webhook Configuration

### Setting Up Your n8n Webhook

1. **Create a Webhook Node** in n8n:
   ```json
   {
     "nodes": [
       {
         "name": "Webhook",
         "type": "n8n-nodes-base.webhook",
         "position": [250, 300],
         "webhookId": "YOUR_WEBHOOK_ID",
         "parameters": {
           "httpMethod": "POST",
           "path": "YOUR_PATH",
           "responseMode": "onReceived",
           "responseData": "allEntries"
         }
       }
     ]
   }
   ```

2. **Enable CORS** in your webhook response headers:
   ```json
   {
     "Access-Control-Allow-Origin": "*",
     "Access-Control-Allow-Methods": "POST, OPTIONS",
     "Access-Control-Allow-Headers": "Content-Type"
   }
   ```

3. **Response Formats** your webhook can return:

   **JSON Format (for patient data):**
   ```json
   {
     "patients": [
       {
         "name": "John Doe",
         "sex": "Male",
         "age": 30,
         "mobile": "1234567890",
         "email": "john@example.com",
         "history": "No significant medical history"
       }
     ]
   }
   ```

   **Markdown Format:**
   ```markdown
   # Patient Report
   
   | Name | Age | Status |
   |------|-----|--------|
   | John | 30  | Active |
   ```

   **Plain Text:**
   ```
   Patient John Doe has been successfully registered.
   ```

### Handling Different Query Types

Your n8n workflow should handle these common queries:

1. **List all patients**: Return JSON with `patients` array
2. **Search patient [name]**: Return JSON with single `patient` object
3. **Show statistics**: Return markdown with tables
4. **General queries**: Return text or markdown responses

## 🎨 Customization

### Changing the Webhook URL

1. Click the **⚙️ Settings** button in the chatbot
2. Enter your n8n webhook URL
3. The URL is saved locally in your browser

### Modifying Quick Actions

Edit the quick action buttons in `index.html`:

```html
<button class="quick-action-btn" onclick="quickAction('Your Custom Query')">
    Custom Action
</button>
```

### Changing Colors

Modify the gradient colors in the CSS:

```css
background: linear-gradient(135deg, #YOUR_COLOR_1 0%, #YOUR_COLOR_2 100%);
```

## 🛠️ Troubleshooting

### CORS Issues

If you see CORS errors:

1. **In n8n**, add a Set node after your webhook:
   ```json
   {
     "Access-Control-Allow-Origin": "*",
     "Access-Control-Allow-Methods": "POST, OPTIONS",
     "Access-Control-Allow-Headers": "Content-Type"
   }
   ```

2. **Alternative**: Use a CORS proxy service like `cors-anywhere`

### Connection Status Shows "Offline"

1. Verify your webhook URL is correct
2. Check if your n8n workflow is active
3. Ensure the webhook is set to accept POST requests
4. Test the webhook directly using Postman or curl

### GitHub Pages Not Loading

1. Check repository settings → Pages section
2. Ensure the repository is public
3. Wait 5-10 minutes for initial deployment
4. Check for build errors in Actions tab

## 📱 Mobile Responsiveness

The chatbot automatically adapts to mobile screens with:
- Full-screen mode on mobile devices
- Adjusted font sizes and spacing
- Touch-friendly buttons
- Optimized message bubbles

## 🔒 Security Notes

- The webhook URL is stored in browser's localStorage
- No sensitive data is transmitted without HTTPS
- Consider implementing authentication in your n8n workflow
- Use environment-specific webhook URLs for production

## 📄 License

This project is open source and available under the MIT License.

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 💬 Support

For issues or questions:
1. Check the troubleshooting section above
2. Open an issue in the GitHub repository
3. Contact your n8n administrator for webhook issues

---

**Built with ❤️ using HTML, CSS, JavaScript, and n8n**