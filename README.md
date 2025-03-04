# Confluence AI Connector

## Overview

This Python script connects to an AI model (Ollama's LLaMA) to generate content and then uses the Confluence API to create a page with that content. It acts as a bridge between the AI model and Confluence, facilitating the creation of content in Confluence based on AI-generated data.

## Intention

The primary intention of this script is to automate the process of generating and posting content to Confluence. It achieves this by:
1. Sending a prompt to Ollama's LLaMA API to generate a title and content.
2. Creating a new page in Confluence with the generated title and content.

## Usage

1. **Set Up Confluence Credentials**:
   Replace the placeholders in the script with your actual Confluence URL, username, and API token.

   ```python
   CONFLUENCE_URL = 'https://atlassian url/wiki'
   CONFLUENCE_USERNAME = 'your_username'
   CONFLUENCE_API_TOKEN = 'your api key'
   ```

2. **Run the Script**:
   Execute the script to generate content and create a Confluence page.

   ```sh
   python confluence_ai_agent_ollama.py
   ```

## Suggestions to Make it an AI Agent

To transform this script into an AI agent, you can add functionalities that allow it to autonomously perform tasks based on certain triggers or schedules. Here are some steps to achieve this:

1. **Add a Scheduler**:
   Use a scheduler to run the agent at regular intervals. For example, you can use the `schedule` library to run the agent daily.

   ```python
   import schedule
   import time

   def run_agent():
       user_prompt = "Create a title and content for a Confluence page about 'Creating sample AI agents'."
       title, content = generate_content_and_title(user_prompt)

       if title and content:
           create_confluence_page(title, content)
       else:
           logging.error("Error: Could not generate content or title.")

   # Schedule the agent to run every day at 9 AM
   schedule.every().day.at("09:00").do(run_agent)

   if __name__ == "__main__":
       while True:
           schedule.run_pending()
           time.sleep(1)
   ```

2. **Add a Trigger Mechanism**:
   Implement a mechanism to trigger the agent based on specific events or conditions, such as new data availability or user actions.

3. **Enhance Decision-Making**:
   Add logic to make decisions based on the generated content or other inputs. For example, the agent could analyze the content and decide whether to post it based on certain criteria.

4. **Use Environment Variables for Security**:
   Replace hardcoded credentials with environment variables to enhance security.

   ```python
   import os

   CONFLUENCE_URL = os.getenv('CONFLUENCE_URL', 'https://atlassian url/wiki')
   CONFLUENCE_USERNAME = os.getenv('CONFLUENCE_USERNAME', 'your_username')
   CONFLUENCE_API_TOKEN = os.getenv('CONFLUENCE_API_TOKEN', 'your api key')
   ```

By implementing these suggestions, you can transform the script into a more autonomous and secure AI agent.
