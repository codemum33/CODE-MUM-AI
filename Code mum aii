async function sendMessage() {
    let userInput = document.getElementById('userInput').value;
    if (!userInput) return;
    appendMessage('user', userInput);
    document.getElementById('userInput').value = '';

    const response = await fetch('https://api.freegpt.app/v1/chat/completions', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
            model: 'gpt-3.5-turbo',
            messages: [{ role: 'user', content: userInput }]
        })
    });

    const data = await response.json();
    const botReply = data.choices[0].message.content;
    appendMessage('bot', botReply);
    speak(botReply);
}

function appendMessage(sender, message) {
    const chatbox = document.getElementById('chatbox');
    const messageDiv = document.createElement('div');
    messageDiv.className = sender;
    messageDiv.innerText = message;
    chatbox.appendChild(messageDiv);
    chatbox.scrollTop = chatbox.scrollHeight;
}

function speak(text) {
    const synth = window.speechSynthesis;
    const utter = new SpeechSynthesisUtterance(text);
    synth.speak(utter);
}
