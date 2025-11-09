# Floating Chatbot Setup Guide

## Component Created
✅ `src/components/FloatingChatbot.tsx` - Professional floating chatbot widget

## How to Use

### 1. Already Integrated
The component is already imported and rendered in `App.tsx`. The floating chatbot will appear on every page.

### 2. Verify Your Setup
- React and TypeScript are configured ✓
- Tailwind CSS is configured ✓
- lucide-react icons are available ✓
- All animations are in your index.css ✓

### 3. Backend API Integration

Update your backend to handle:

```
POST /api/chat
Content-Type: application/json

Request:
{
  "message": "User's message here"
}

Response:
{
  "response": "Bot's response here"
}
```

### 4. Backend Logic (Node.js/Express example)

```javascript
app.post('/api/chat', async (req, res) => {
  const { message } = req.body;
  
  try {
    let response;
    
    // Route to appropriate API based on query
    if (message.toLowerCase().includes('weather')) {
      response = await getWeatherData(message);
    } else if (message.toLowerCase().includes('satellite') || message.includes('ocean')) {
      response = await getMosdacData(message);
    } else {
      response = await getGeminiResponse(message);
    }
    
    res.json({ response });
  } catch (error) {
    res.status(500).json({ response: 'Error processing request' });
  }
});
```

## Features

✅ Circular floating button (bottom-right)
✅ Click to expand chat window (glassmorphic design)
✅ Text input with send button
✅ Voice input (Web Speech API)
✅ Conversation history
✅ Typing indicator
✅ Responsive design
✅ Smooth animations

## Component Props
The component takes no props - it's self-contained.

```tsx
<FloatingChatbot />
```

## Customization

To customize the component:

1. **Change position**: Modify `bottom-6 right-6` Tailwind classes
2. **Change colors**: Update `from-blue-500 to-indigo-600` gradient classes
3. **Change initial message**: Edit the `messages` state in the component

## Voice Input Support
- Chrome, Edge, Opera: Full support
- Safari: Full support (webkit prefix)
- Firefox: Limited support
- Mobile browsers: Varies by OS

## API Endpoints Expected

Your backend should support:
- `POST /api/chat` - Main endpoint for both text and voice queries

The component automatically handles both text and voice-to-text conversion on the frontend.

## Testing Locally

1. Start your React dev server: `npm run dev`
2. Open your browser
3. Look for the blue circular button in the bottom-right corner
4. Click it to expand the chat window
5. Test text input and voice input (if supported)
