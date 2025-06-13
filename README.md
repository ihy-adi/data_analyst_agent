![Unknown](https://github.com/user-attachments/assets/cebdb696-a027-49af-857c-5c5a924663d2)# Data Analyst Agent - Comprehensive Documentation

## Overview

The Data Analyst Agent is an intelligent AI-powered tool that provides advanced data analysis capabilities. It can process various file formats, perform comprehensive analysis, generate insightful visualizations, and answer questions about data using natural language.

This tool combines the power of pandas for data manipulation, matplotlib and seaborn for visualization, and Together.ai's Llama-4-Maverick-17B model for natural language understanding and response generation.

**Last Updated:** 2025-06-13

## Key Features

- **Multi-format file processing**: Supports .txt, .docx, .pdf, .jpg, .png, .csv, .xlsx files
- **Comprehensive data analysis**: Performs statistical analysis, detects outliers, identifies correlations
- **Smart visualizations**: Generates appropriate visualizations based on data type and structure
- **AI-powered Q&A**: Answers questions about data in natural language
- **Built-in fallbacks**: Provides direct answers for common questions to avoid API calls
- **Interactive mode**: Allows users to upload files or use sample data for exploration

## Technologies and Services Used

### AI Services
- **Together.ai API**: Powers the natural language understanding and generation capabilities using the Llama-4-Maverick-17B-128E-Instruct-FP8 model
- **API Documentation**: https://docs.together.ai/reference/completions

### Development Environment
- **Google Colab**: The agent is designed to run in Google Colab notebooks, utilizing its file upload widgets and display capabilities
- **Google Colab URL**: https://colab.research.google.com/

### Key Libraries
- **pandas**: Data manipulation and analysis
- **matplotlib & seaborn**: Data visualization
- **pytesseract**: OCR for image text extraction
- **PyPDF2**: PDF text extraction
- **python-docx**: Word document processing
- **scikit-learn**: Used for advanced analysis techniques like outlier detection with IsolationForest

## Installation Requirements

```python
# Install required packages in Google Colab
!pip install python-docx PyPDF2 pytesseract scikit-learn seaborn

# API Key Configuration
TOGETHER_API_KEY = "your_api_key_here"  # Replace with actual API key
MODEL = "meta-llama/Llama-4-Maverick-17B-128E-Instruct-FP8"
```

## Class Structure

### DataAnalystAgent

The main class that orchestrates all functionality:

```python
agent = DataAnalystAgent(api_key="your_api_key")
agent.interactive_mode()  # Start the interactive session
```

## Detailed Method Documentation

### API Interaction

#### `query_together_ai(prompt, max_tokens=1024, temperature=0.7, retry_count=3, base_delay=5)`

Sends queries to Together.ai's API with advanced error handling and rate limiting.

- **Parameters**:
  - `prompt`: The text prompt to send to the AI model
  - `max_tokens`: Maximum number of tokens in the response
  - `temperature`: Controls randomness (lower = more deterministic)
  - `retry_count`: Number of retries on failure
  - `base_delay`: Base delay for exponential backoff

- **Returns**: Text response from the AI model or error message

### File Processing Methods

#### `process_file(file_path, file_content)`

Processes a file based on its extension and returns appropriate data structure.

- **Parameters**:
  - `file_path`: Path to the file
  - `file_content`: Binary content of the file

- **Returns**: Dictionary with processed data and metadata

#### Specialized Processing Methods

- `process_text_file(file_content)`: Extracts text from plain text files
- `process_docx_file(file_content)`: Extracts text from Word documents
- `process_pdf_file(file_content)`: Extracts text from PDF files
- `process_image_file(file_content)`: Uses OCR to extract text from images
- `process_csv_file(file_content)`: Loads CSV data into pandas DataFrame
- `process_excel_file(file_content)`: Loads Excel data into pandas DataFrame

### Data Analysis Methods

#### `analyze_tabular_data(data)`

Performs comprehensive analysis on tabular data.

- **Parameters**:
  - `data`: Dictionary containing a pandas DataFrame

- **Returns**: Dictionary with analysis results including:
  - Basic information (shape, columns, data types)
  - Missing data statistics
  - Numerical statistics
  - Categorical analysis
  - Correlation analysis
  - Outlier detection
  - Data quality metrics

#### `analyze_text_data(data)`

Analyzes text data with linguistic insights.

- **Parameters**:
  - `data`: Dictionary containing text content

- **Returns**: Dictionary with text analysis including:
  - Basic statistics (character count, word count, etc.)
  - Complexity metrics (reading ease, avg word length)
  - Word frequency analysis
  - Content preview

### Visualization Methods

#### `generate_visualizations(data)`

Generates comprehensive visualizations based on data type.

- **Parameters**:
  - `data`: Dictionary containing processed data

- **Returns**: List of dictionaries with visualization metadata and encoded images

#### `display_visualizations(visualizations)`

Displays visualizations in the notebook with HTML formatting.

- **Parameters**:
  - `visualizations`: List of visualization dictionaries

#### `generate_visualization_for_question(question)`

Generates a specific visualization based on the user's question.

- **Parameters**:
  - `question`: User's question about the data

- **Returns**: Text describing the visualization or None if no relevant visualization

### AI Agent Methods

#### `format_analysis_for_llm(data, analysis)`

Creates a comprehensive prompt for the AI model based on data analysis.

- **Parameters**:
  - `data`: Processed data dictionary
  - `analysis`: Analysis results dictionary

- **Returns**: Formatted prompt string

#### `ask_agent(question, context=None)`

Queries the AI agent with enhanced context and better prompting.

- **Parameters**:
  - `question`: User's question about the data
  - `context`: Optional additional context

- **Returns**: Response from the AI agent

#### `get_direct_answer(question)`

Provides direct answers for common questions without using the API.

- **Parameters**:
  - `question`: User's question about the data

- **Returns**: Direct answer or None if no direct answer is possible

### Interactive Methods

#### `upload_and_process_file()`

Uploads and processes a file using Google Colab's file upload functionality.

- **Returns**: Boolean indicating success or failure

#### `interactive_mode()`

Runs the agent in interactive mode, allowing users to choose between uploading a file or using a sample dataset.

#### `create_sample_dataset()`

Creates a sample customer dataset for demonstration purposes.

- **Returns**: Pandas DataFrame with sample data

## Sample Usage

The agent can be used in interactive mode, which provides a command-line interface for:

1. Uploading and analyzing a file
2. Using a sample dataset
3. Asking questions about the data

Example output:

```
🤖 Data Analyst Agent - Interactive Mode
========================================
1️⃣ Upload and analyze a file
2️⃣ Use a sample dataset
Enter your choice (1 or 2): 2

⏳ Creating sample dataset...
✅ Sample dataset created!
[DataFrame preview displayed]

🔍 Analyzing sample data...
📊 Generating visualizations...
![Unknown](https://github.com/user-attachments/assets/2afb30be-98e1-4f3d-abfa-1302f4e915d7)
![Unknown-1](https://github.com/user-attachments/assets/058ccfc8-f6da-4f7d-be19-a1a99bb7c133)
![Unknown-2](https://github.com/user-attachments/assets/5c49bd50-67e1-4bbc-9160-8de82b0289cb)
![Unknown-3](https://github.com/user-attachments/assets/c63cc6c9-615c-4e98-b37e-c29522f77fc9)
![Unknown-4](https://github.com/user-attachments/assets/d05cd139-c84b-40cb-8fcf-8a2d38d71d5b)
![Unknown-5](https://github.com/user-attachments/assets/fc8733b2-7bff-47b9-98f0-ad747b2857ba)

🔍 You can now ask questions about the data!
Type 'exit', 'quit', or 'bye' to end the session.

❓ Your question: what is the highest age?
⏳ Thinking...

🤖 Answer:
The highest value in 'Age' is 85.0.

❓ Your question: tell me the average purchase amount
⏳ Thinking...

🤖 Answer:
For 'Age':
- Mean (average): 43.9744
- Median: 44.0000

❓ Your question: what can you tell me about the subscription type
⏳ Thinking...

🤖 Answer:
[Detailed response about subscription type analysis]

❓ Your question: bye

Thank you for using the Data Analyst Agent! 👋
```

## Integration with Google Colab

The Data Analyst Agent is specifically designed to work within Google Colab notebooks, taking advantage of:

1. **File Upload Widgets**: Uses Colab's `files.upload()` for easy file uploading
2. **Rich Display Capabilities**: Leverages IPython display functions for rendering visualizations
3. **HTML Output**: Uses HTML formatting for better presentation of results
4. **Interactive Interface**: Provides a command-line style interface within notebook cells

To use in Colab:
1. Create a new notebook at [colab.research.google.com](https://colab.research.google.com/)
2. Copy the full DataAnalystAgent class implementation
3. Add API configuration with your Together.ai key
4. Run `agent = DataAnalystAgent()` followed by `agent.interactive_mode()`

## API Usage Details

The Together.ai API is used for natural language understanding and question answering:

```python
def query_together_ai(self, prompt, max_tokens=1024, temperature=0.7, retry_count=3, base_delay=5):
    url = "https://api.together.xyz/v1/completions"
    headers = {
        "Authorization": f"Bearer {self.api_key}",
        "Content-Type": "application/json"
    }
    data = {
        "model": self.model,
        "prompt": prompt,
        "max_tokens": max_tokens,
        "temperature": temperature
    }
    
    # API call and error handling logic follows...
```

**API Pricing**: Together.ai offers various pricing tiers, including a free tier with limited usage. Check the [Together.ai pricing page](https://www.together.ai/pricing) for current rates.

**Rate Limiting**: The code implements exponential backoff retry logic to handle rate limiting gracefully.

## Performance and Limitations

- **Performance**: The agent works best with datasets under 100,000 rows due to memory constraints in Google Colab's free tier.
- **Visualization Capabilities**: The agent can create various types of visualizations but may need additional customization for specialized plots.
- **API Limitations**: The Together.ai API has rate limits and token limits that may affect response times and completeness.
- **OCR Quality**: Text extraction from images depends on image quality and may not be perfect for complex or low-quality images.
- **Colab Session Limits**: Google Colab has session time limits (typically 12 hours) after which the runtime may disconnect.

## Future Enhancements

Potential areas for improvement:

1. Add support for more file formats (e.g., JSON, XML, parquet)
2. Implement more advanced data cleaning techniques
3. Incorporate machine learning capabilities for predictive analytics
4. Add natural language data querying (SQL generation from questions)
5. Enhance visualization recommendations based on data characteristics
6. Add multi-file analysis capabilities for comparative analytics
7. Implement caching to reduce API calls and improve performance

## Conclusion

The Data Analyst Agent provides a comprehensive solution for data exploration, visualization, and analysis using natural language. It combines traditional data analysis techniques with modern AI capabilities to make data analytics more accessible and efficient. By leveraging Google Colab's environment and Together.ai's powerful language models, it offers a user-friendly interface for interacting with data through natural language questions.
