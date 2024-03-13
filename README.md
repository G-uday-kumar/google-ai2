"""
At the command line, only need to run once to install the package via pip:

$ pip install google-generativeai
"""

import google.generativeai as genai

genai.configure(api_key="YOUR_API_KEY")

# Set up the model
generation_config = {
  "temperature": 0.9,
  "top_p": 1,
  "top_k": 1,
  "max_output_tokens": 2048,
}

safety_settings = [
  {
    "category": "HARM_CATEGORY_HARASSMENT",
    "threshold": "BLOCK_MEDIUM_AND_ABOVE"
  },
  {
    "category": "HARM_CATEGORY_HATE_SPEECH",
    "threshold": "BLOCK_MEDIUM_AND_ABOVE"
  },
  {
    "category": "HARM_CATEGORY_SEXUALLY_EXPLICIT",
    "threshold": "BLOCK_MEDIUM_AND_ABOVE"
  },
  {
    "category": "HARM_CATEGORY_DANGEROUS_CONTENT",
    "threshold": "BLOCK_MEDIUM_AND_ABOVE"
  },
]

model = genai.GenerativeModel(model_name="gemini-1.0-pro",
                              generation_config=generation_config,
                              safety_settings=safety_settings)

prompt_parts = [
  "input: how  the google gemini ai 1.5 works",
  "input 2: the google gemini ai is a software interacting model, it works on the basis of the user interacting, it has the pre defined answers with this it gave or react with the user in the user friendly, you can get answer on any type of questions",
  "input: how many language's you know & able to speek",
  "input 2: yes i can speak about more than 40+ language's",
  "input: i love you ai",
  "input 2: thank you for your love , i apology for this i am not able to your physical partner i am here to help you, you can ask any dounts",
  "input: then who is my love",
  "input 2: your parent and friends are the real lovers for you",
  "input: how the google gemini ai 1.5 works",
  "input 2: ",
]

response = model.generate_content(prompt_parts)
print(response.text)
