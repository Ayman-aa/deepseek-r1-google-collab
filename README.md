# DeepSeek-R1 Google Colab

This repository contains a Jupyter notebook to get hands-on experience with the DeepSeek-R1:7b model. 

## Prerequisites

1. **Fresh Google Account**: For development purposes, it is recommended to use a fresh Google account to take advantage of the free 16GB storage on Google Drive.
2. **Google Colab**: Ensure you have access to Google Colab, which provides free GPU resources.

## Setup Instructions

1. **Clone the Repository**:
    ```sh
    git clone https://github.com/yourusername/deepseek-r1-google-collab.git
    cd deepseek-r1-google-collab
    ```

2. **Open the Notebook**:
    - Upload the [deepseek_r1.ipynb](http://_vscodecontentref_/1) notebook to your Google Drive.
    - Open the notebook with Google Colab.

3. **Install Required Packages**:
    - The notebook includes cells to install necessary packages. Run the following cells to install the `ollama` package and other dependencies:
        ```python
        # Installing the ollama package with pip
        !pip install ollama

        # Install lshw
        !sudo apt-get install lshw

        # Install Ollama
        !curl -fsSL https://ollama.com/install.sh | sh
        ```

4. **Start the Ollama Server**:
    - The notebook includes a cell to start the Ollama server. Run the following cell:
        ```python
        import subprocess
        import time

        # Start the Ollama server and wait for a few seconds to ensure it's ready
        subprocess.Popen("ollama serve", shell=True)
        time.sleep(5)  # Wait for 5 seconds
        ```

5. **Run the DeepSeek-R1 Model**:
    - Execute the following cell to run the DeepSeek-R1:7b model:
        ```python
        !ollama run deepseek-r1:7b
        ```

6. **Chat with the Model**:
    - Use the following cell to interact with the model:
        ```python
        from ollama import chat
        from ollama import ChatResponse

        response: ChatResponse = chat(model='deepseek-r1:7b', messages=[
          {
            'role': 'user',
            # Change your prompt in the content parameter
            'content': 'Why is the sky blue?',
          },
        ])
        print(response['message']['content'])
        # or access fields directly from the response object
        print(response.message.content)
        ```

## Notes

- The process may terminate after installation, so you may need to restart the Ollama server using the provided cell.
- Modify the prompt in the `content` parameter to ask different questions or interact with the model as needed.

## License

This project is licensed under the MIT License. See the LICENSE file for details.