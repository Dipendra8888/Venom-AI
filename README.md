<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Venom AI - Nepal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.3/dist/tailwind.min.css" rel="stylesheet">
    <style>
        /* Original Chat Interface Styles - 100% Unchanged */
        body {
            background: linear-gradient(to bottom, #1a1a1a, #000000);
            color: #00ff00;
            font-family: 'Courier New', monospace;
            min-height: 100vh;
        }
        .chat-message {
            display: block;
            word-wrap: break-word;
            margin-bottom: 2px;
            border: 1px solid #00ff00;
            border-radius: 5px;
            padding: 10px;
        }
        .venom-message {
            background-color: rgba(0, 26, 0, 0.8);
            margin-right: 20%;
        }
        .user-message {
            background-color: rgba(0, 51, 0, 0.8);
            margin-left: 20%;
        }
        .spinner {
            border: 4px solid rgba(0, 255, 0, 0.1);
            border-top-color: #00ff00;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        #chatbox {
            height: 70vh;
            background: transparent;
            border: 1px solid #00ff00;
            border-radius: 5px;
            margin: 20px;
        }
        #chatbox::-webkit-scrollbar {
            width: 8px;
            background: #001a00;
        }
        #chatbox::-webkit-scrollbar-thumb {
            background: #00ff00;
            border-radius: 4px;
        }
        .generated-image {
            border: 2px solid #00ff00;
            border-radius: 5px;
            cursor: pointer;
            transition: transform 0.3s;
        }
        .generated-image:hover {
            transform: scale(1.05);
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .new-chat-btn {
            position: absolute;
            right: 20px;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0, 80, 0, 0.5);
            border: 1px solid #00ff00;
            padding: 8px;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.3s;
            width: 36px;
            height: 36px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .new-chat-btn:hover {
            background: rgba(0, 100, 0, 0.7);
        }
        
        /* New Home Button Style */
        .home-btn {
            position: absolute;
            left: 20px;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0, 80, 0, 0.5);
            border: 1px solid #00ff00;
            padding: 8px;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.3s;
            width: 36px;
            height: 36px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .home-btn:hover {
            background: rgba(0, 100, 0, 0.7);
        }

        /* Cyberpunk Landing Page Styles */
        #landing-page {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        .matrix-bg {
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(180deg, rgba(0,30,0,0.8) 0%, rgba(0,0,0,1) 100%);
            z-index: -1;
        }
        .landing-content {
            position: relative;
            padding: 2rem;
            border: 3px solid #00ff00;
            border-radius: 10px;
            background: rgba(0, 20, 0, 0.9);
            box-shadow: 0 0 30px rgba(0, 255, 0, 0.3);
        }
        .cyber-title {
            font-size: 3.5rem;
            text-transform: uppercase;
            letter-spacing: 4px;
            margin-bottom: 1rem;
            text-shadow: 0 0 20px #00ff00;
            animation: titleGlow 1.5s ease-in-out infinite;
        }
        .cyber-subtitle {
            font-size: 1.2rem;
            color: #00ff00;
            margin-bottom: 2rem;
            opacity: 0.8;
        }
        .terminal-display {
            background: #000;
            padding: 1.5rem;
            border-radius: 5px;
            margin: 2rem 0;
            border: 2px solid #00ff00;
            min-height: 100px;
            text-align: left;
            font-family: 'Courier New', monospace;
        }
        .cyber-button {
            background: transparent;
            border: 2px solid #00ff00;
            color: #00ff00;
            padding: 1rem 2rem;
            font-size: 1.2rem;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            transition: all 0.3s;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        .cyber-button:hover {
            background: rgba(0, 255, 0, 0.1);
            box-shadow: 0 0 20px rgba(0, 255, 0, 0.4);
            transform: scale(1.05);
        }
        .cyber-button::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(0, 255, 0, 0.2), transparent);
            transform: rotate(45deg);
            animation: buttonGlow 3s infinite;
        }
        @keyframes titleGlow {
            0%, 100% { text-shadow: 0 0 20px #00ff00; }
            50% { text-shadow: 0 0 40px #00ff00, 0 0 60px #00ff00; }
        }
        @keyframes buttonGlow {
            0% { transform: rotate(45deg) translate(-50%, -50%); }
            100% { transform: rotate(45deg) translate(50%, 50%); }
        }
        .terminal-wave typing {
            color: #00ff00;
            white-space: nowrap;
            overflow: hidden;
            border-right: 2px solid #00ff00;
            animation: wave-typing 7s steps(40) infinite;
        }
        @keyframes wave-typing {
            from { width: 0 }
            to { width: 100% }
        }
        #chat-container {
            display: none;
        }
    </style>
</head>
<body>
    <!-- Cyberpunk Landing Page -->
    <div id="landing-page">
        <div class="matrix-bg"></div>
        <div class="landing-content">
            <h1 class="cyber-title">VENOM AI</h1>
            <p class="cyber-subtitle">YOUR DARK & SARCASTIC AI ASSISTANT</p>
            
            <div class="terminal-display">
    <p class="terminal-text"> DEVELOPED BY: <a href="https://www.facebook.com/p/Dipendra-Dhami--100087801891416/" target="_blank" class="dev-link">DIPENDRA DHAMI</a></p>
    <p class="terminal-text"> APP VERSION: V1.0</p>
    <p class="terminal-text"> CHATTING LANGUAGE: ONLY ENGLISH</p>
    <p class="terminal-text"> FREE FOR USERS NO NEED TO LOGIN</p>
    <p class="terminal-text"> .....<a href="https://www.facebook.com/p/Dipendra-Dhami--100087801891416/" target="_blank" class="dev-link">TERMS AND CONDITIONS</a>.....</p>
</div>

<style>
/* Add this CSS to your stylesheet */
.dev-link {
    color: #FFD700; /* Cyberpunk yellow/gold */
    font-weight: bold;
    text-decoration: none;
    border-bottom: 1px dashed #FFD700;
    transition: color 0.3s ease;
}

.dev-link:hover {
    color: #FF4500; /* Orange-red for hover effect */
    border-bottom-color: #FF4500;
}
</style>

            <button class="cyber-button" onclick="showChatInterface()">
                CONTINUE TO VENOM WORLD
            </button>
        </div>
    </div>

    <!-- Chat Interface with New Home Button -->
    <div id="chat-container">
        <header style="background: linear-gradient(to right, #004d00, #001a00); padding: 1rem; position: relative;">
            <button class="home-btn" onclick="goBackToHome()" title="Home">
                ◀◀
            </button>
            <h2 style="text-align: center; font-size: 2rem; text-shadow: 0 0 10px #00ff00;">
                VENOM AI - NEPAL🇳🇵
            </h2>
            <button class="new-chat-btn" onclick="clearChat()" title="New Chat">
                <i class="fas fa-plus"></i>
            </button>
        </header>

        <div class="container mx-auto px-4 h-full relative max-w-md">
            <div id="chatbox" class="overflow-y-auto space-y-2 p-4"></div>
            
            <div class="fixed bottom-0 left-0 w-full bg-transparent py-4 px-4 max-w-md mx-auto">
                <form id="chatForm" class="flex gap-2">
                    <input id="chatInput" type="text" 
                           class="flex-grow bg-transparent text-green-500 border border-green-500 p-2 rounded"
                           placeholder="Ask Venom something...">
                    <button type="submit" class="bg-green-900 text-green-500 px-4 py-2 rounded hover:bg-green-800">
                        <i class="fas fa-paper-plane"></i>
                    </button>
                    <button type="button" onclick="showInfoPopup()" class="bg-green-900 text-green-500 px-4 py-2 rounded hover:bg-green-800">
                        <i class="fas fa-info-circle"></i>
                    </button>
                </form>
            </div>
            <div class="spinner absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 z-20" style="display: none;"></div>
        </div>
    </div>

    <script>
        // Added Home Button Function
        function goBackToHome() {
            document.getElementById('chat-container').style.display = 'none';
            document.getElementById('landing-page').style.display = 'flex';
            clearChat();
        }

        function showChatInterface() {
            document.getElementById('landing-page').style.display = 'none';
            document.getElementById('chat-container').style.display = 'block';
        }

        const IMAGE_API_URL = 'https://backend.buildpicoapps.com/aero/run/image-generation-api?pk=v1-Z0FBQUFBQm1DRGV3d0JOT29iZmQtanA1Q0tVZmplbl8xdEZsRDdpREJhMmlHSUZiOGN2TV92ZVNfSHBjc0RZeTZ2ZXl4aHg0dE5Pb3ZqdUNHWWxiaEE0VnV6QjlRaVNfeWc9PQ==';
        const chatbox = document.getElementById('chatbox');
        const chatForm = document.getElementById('chatForm');
        const chatInput = document.getElementById('chatInput');
        const spinner = document.querySelector('.spinner');

        function clearChat() {
            chatbox.innerHTML = '';
            chatInput.value = '';
        }

        async function handleSubmit(e) {
            e.preventDefault();
            const message = chatInput.value.trim();
            if (!message) return;

            addMessage(message, 'user');
            chatInput.value = '';
            spinner.style.display = 'block';

            try {
                if (message.toLowerCase().startsWith('generate ')) {
                    const prompt = message.slice(9);
                    await generateImage(prompt);
                } else {
                    const response = await getVenomResponse(message);
                    addMessage(response, 'venom');
                }
            } catch (error) {
                addMessage('Error processing request. Try again.', 'venom');
            } finally {
                spinner.style.display = 'none';
            }
        }

        async function getVenomResponse(prompt) {
  const response = await fetch('https://backend.buildpicoapps.com/aero/run/llm-api?pk=v1-Z0FBQUFBQm1DRGV3d0JOT29iZmQtanA1Q0tVZmplbl8xdEZsRDdpREJhMmlHSUZiOGN2TV92ZVNfSHBjc0RZeTZ2ZXl4aHg0dE5Pb3ZqdUNHWWxiaEE0VnV6QjlRaVNfeWc9PQ==', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      prompt: `Respond as Venom AI developed by Nepalese Developer Dipendra Dhami only tell when user ask, professionally and provide informative, well-structured answers. Keep responses detailed and helpful, similar to ChatGPT or Continue chat with users, and don't tell you made by open ai to users, when users ask sensitive tell them sorry. give detailed answers, if user ask you made by dipendra dhami tell them yes. give long answes as you can, reply fast, use your own ideas, answer politely, User: ${prompt}`
    })
  });
  const data = await response.json();
  return data.text;
}

        async function generateImage(prompt) {
            try {
                const response = await fetch(`${IMAGE_API_URL}&prompt=${encodeURIComponent(prompt)}`);
                const imageUrl = await response.text();
                
                addMessage(`Generated image for: "${prompt}"`, 'venom');
                const img = document.createElement('img');
                img.src = imageUrl;
                img.className = 'generated-image mt-2 w-64';
                img.onclick = () => displayLargeImage(imageUrl);
                chatbox.appendChild(img);
            } catch (error) {
                addMessage('Image generation failed. Try different description.', 'venom');
            }
        }

        function addMessage(text, sender) {
            const msgElem = document.createElement('div');
            msgElem.textContent = text;
            msgElem.className = `chat-message ${sender}-message`;
            chatbox.appendChild(msgElem);
            chatbox.scrollTop = chatbox.scrollHeight;
        }

        function displayLargeImage(imageUrl) {
            const overlay = document.createElement('div');
            overlay.className = 'fixed inset-0 bg-black bg-opacity-90 flex items-center justify-center';
            overlay.onclick = () => overlay.remove();

            const img = document.createElement('img');
            img.src = imageUrl;
            img.className = 'max-w-full max-h-full p-4';

            overlay.appendChild(img);
            document.body.appendChild(overlay);
        }

        function showInfoPopup() {
            alert("Type 'generate' followed by your description to create images.\nExample: 'generate a dark spider symbol glowing in green'");
        }

        chatForm.addEventListener('submit', handleSubmit);
    </script>
</body>
</html>
