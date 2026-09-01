### Step 1: Import API key and libraries
import os
from openai import OpenAI
from IPython import Markdown, display
from dotenv import load_dotenv

load_dotenv()

OPENAI_API_KEY = os.getenv("OPENAI_API_KEY")

if OPENAI_API_KEY is None:
    raise Exception(API key is missing)


### Step 2: Call the API
client = OpenAI()

messages=[
    {"role":"system", "content":"You are a helpful assistant"},
    {"role":"user", "content":"I am going to Spain next week"}
]

response = client.chat.completion.create(
    model="gpt-4.1-mini",
    messages=messages
)

reply = response.choices[0].message.content
display(Markdown(reply))