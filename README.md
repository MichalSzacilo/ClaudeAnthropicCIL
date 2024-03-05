# ClaudeAnthropicCIL
 Here is a translation of a command line conversation .
1. Create a new notepad document and paste the script using your own API obtained from the Cloud Anthropic service provider website.
2. Save in anthropic_chat.py format .
3. Run in any Command line using the command python anthropic_chat.py
4. At the bottom is a script in the Phython language which needs to be copied.

Code for copy 


import json

API_KEY = 'Your API Kay'
API_URL = 'https://api.anthropic.com/v1/complete'

def chat(prompt):
    headers = {
        'Content-Type': 'application/json',
        'X-API-Key': API_KEY,
        'anthropic-version': '2023-06-01'
    }
    data = {
        'prompt': f'\n\nHuman: {prompt}\n\nAssistant:',  # Zmieniony format promptu
        'model': 'claude-v1',
        'max_tokens_to_sample': 1000
    }
    response = requests.post(API_URL, headers=headers, data=json.dumps(data))
    
    if response.status_code == 200:
        return response.json()['completion']
    else:
        return f'Error {response.status_code}: {response.text}'

while True:
    try:
        user_input = input('You: ')
        response = chat(user_input)
        print(f'Assistant: {response}')
    except KeyboardInterrupt:
        print('\nGoodbye!')
        break
