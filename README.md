AI Agent Loop with Function Calling

This repository contains a basic implementation of an AI agent loop using LiteLLM and function calling for structured tool execution. The project demonstrates how a stateless large language model (LLM) can be transformed into a goal-driven agent by combining system instructions, explicit memory handling, bounded tools, and iterative feedback.

The agent repeatedly evaluates user input, selects actions through function calls, executes those actions in Python, and incorporates the results into its ongoing context until a termination condition is reached.

*** Core Architecture ***

The agent operates using a simplified agent loop:

Combine system rules with current memory

Send context to the LLM

Receive either a structured function call or text response

Execute the corresponding Python function

Store results in memory

Repeat until termination

This approach enables multi-step reasoning, controlled environment interaction, and adaptive behavior.

*** Tools Implemented ***

The agent is provided with three tools:

list_files()
Lists files in the current working directory.

read_file(file_name: str)
Reads and returns the contents of a specified file.

terminate(message: str)
Ends the agent loop and prints a summary message.

Tools are exposed to the LLM using JSON Schema and executed dynamically through a function registry.

*** Key Features ***

Explicit memory management using message history

Structured tool execution via function calling

Dynamic dispatch of tool calls

Robust error handling

System-level behavior constraints

Iteration safety limits

*** Setup & Usage ***
Install dependencies
pip install litellm

Set your OpenAI API key (example for Google Colab)
from google.colab import userdata
import os

api_key = userdata.get('OPENAI_API_KEY')
os.environ['OPENAI_API_KEY'] = api_key

Run the agent

Execute the script and provide a task when prompted:

What would you like me to do?


The agent will autonomously select tools, execute actions, and iterate until the task is complete.

*** Concepts Demonstrated ***

Stateless LLM behavior and external memory simulation

Agent loops for multi-step task completion

Tool-based environment interaction

Function calling for structured responses

Feedback-driven decision making

*** Project Purpose ***

This repository serves as a learning example for building AI agents using modern function calling APIs and iterative control loops. It illustrates how to move beyond single-response chat interactions toward autonomous, tool-driven AI workflows.

*** Possible Extensions ***

Additional task-specific tools

Persistent memory storage

Dynamic tool registration

Planning and goal decomposition

Improved error recovery
