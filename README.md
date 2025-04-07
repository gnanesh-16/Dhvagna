# Dhvagna

![Version](https://img.shields.io/badge/version-0.1.2-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Python](https://img.shields.io/badge/python-3.7%2B-blue)

A powerful multilingual voice transcription tool that supports both Telugu and English speech, powered by Google's Gemini AI. Dhvagna makes it easy to transcribe speech from both recordings and live microphone input, with support for customizable prompts and formatting.

## 🔑 API Key Required

To use Dhvagna, you need a valid API key with the following requirements:

- **Valid API key format**: All API keys must start with `dk-` followed by a unique alphanumeric string
- **Limited usage**: Each API key is limited to 100 transcriptions
- **Verification**: API keys are verified with our servers

### How to obtain an API key:

Visit [https://github.com/gnanesh-16/Dhvagna](https://github.com/gnanesh-16/Dhvagna) to register and receive your API key. or Here is the Free *DHVAGNA_API_KEY = "dk-uahdh8374hasjojnufouahe74" has upto (10 tokens availablity)

### Setting up your API key:

```bash
# On Windows (Command Prompt)
set DHVGNA_API_KEY=dk-your_unique_key_here

# On Windows (PowerShell)
$env:DHVGNA_API_KEY="dk-your_unique_key_here"

# On Linux/MacOS
export DHVGNA_API_KEY="dk-your_unique_key_here"
```

Alternatively, you can create a `.env` file in your project directory:

```
DHVGNA_API_KEY=dk-your_unique_key_here
```

### Usage tracking:

The package tracks usage against your API key quota. You'll receive notifications about:

- Remaining transcriptions at startup
- Updated count after each transcription
- Errors when your limit is reached

## 🌟 Features

- **Multilingual Support**: Transcribe both Telugu and English speech with high accuracy
- **Multiple Input Methods**:
  - Live microphone recording with simple keyboard controls
  - Process existing WAV audio files
- **Smart Language Detection**: Automatically detects whether the speech is in Telugu or English
- **Advanced Processing**:
  - Raw transcription preserving original speech patterns
  - Refined output with improved grammar and formatting
  - Customizable prompts for different use cases
- **Flexible Output**:
  - Customizable title formatting
  - Both raw and refined transcriptions
  - Automatic file saving with timestamps
- **Easy-to-Use Interface**:
  - Simple keyboard controls ('K' to start/stop recording)
  - Progress indicators and timers
  - Beautiful console output with color coding
- **API Key Management**:
  - Secure API key validation
  - Usage tracking with quota limits
  - Graceful error handling for exceeded quotas

## 📦 Installation

```bash
pip install dhvagna
```

## 🚀 Quick Start

### Basic Usage

```python
from dhvagna import record_audio, transcribe_wav_file

# Make sure you've set your DHVGNA_API_KEY environment variable first!
# The key must start with 'dk-' and be registered with our service

# Record and transcribe from microphone
record_audio()

# Or transcribe an existing WAV file
result = transcribe_wav_file("path/to/audio.wav")
```

## 📝 Examples

The package includes several example scripts to help you get started:

### 1. Basic Example

```python
# basic_example.py
import os
from dhvagna import record_audio, transcribe_wav_file

def check_api_key():
    """Check if API key is properly set"""
    api_key = os.getenv('DHVGNA_API_KEY')
    if not api_key:
        print("\n❌ Error: DHVGNA_API_KEY environment variable not found!")
        print("\nTo set your API key:")
        print("1. Get your API key from: https://github.com/gnanesh-16/Dhwagna")
        print("\n2. Set it as an environment variable:")
        print("   Windows (Command Prompt):")
        print("   set DHVGNA_API_KEY=your_api_key_here")
        return False
    return True

def main():
    print("===== Dhvagna Basic Usage Example =====")
    
    # First, verify API key is set
    if not check_api_key():
        return
    
    # Present options to user
    print("\nWhat would you like to do?")
    print("1. Record audio from microphone")
    print("2. Transcribe a WAV file")
    
    choice = input("\nEnter your choice (1 or 2): ")
    
    if choice == "1":
        print("\nPress 'K' to start recording")
        print("Press 'K' again to stop recording")
        record_audio()
        
    elif choice == "2":
        file_path = input("\nEnter the path to your WAV file: ")
        if file_path.strip():
            result = transcribe_wav_file(file_path.strip())
            if result:
                original, refined, language = result
                print(f"\nTranscription successful!")
                print(f"Detected language: {language}")

if __name__ == "__main__":
    main()
```

### 2. Simple Example

```python
# simple_example.py
import os
from dhvagna import record_audio, transcribe_wav_file, set_custom_prompts

def verify_api_key():
    """Make sure API key is set up correctly"""
    api_key = os.getenv('DHVGNA_API_KEY')
    if not api_key:
        print("\n❌ Error: DHVGNA_API_KEY not found!")
        print("\nGet your API key from:")
        print("https://github.com/gnanesh-16/Dhwagna")
        return False
    if not api_key.startswith('dk'):
        print("\n❌ Error: Invalid API key format!")
        print("Dhvagna API keys must start with 'dk'")
        return False
    return True

def main():
    print("===== Dhvagna Quick Start =====")
    
    # Check API key first
    if not verify_api_key():
        return
    
    # Set up a simple custom prompt (optional)
    custom_prompt = """
Transcribe this content in Telugu or English.
Identify the language as [LANGUAGE: Telugu] or [LANGUAGE: English].
Capture the speech exactly as spoken.
"""
    set_custom_prompts(new_transcription_prompt=custom_prompt)
    
    # Show options
    print("\nWhat would you like to do?")
    print("1. Record new audio")
    print("2. Transcribe WAV file")
    
    choice = input("\nChoice (1 or 2): ")
    
    if choice == "1":
        print("\nRecording:")
        print("1. Press 'K' to start")
        print("2. Speak your content")
        print("3. Press 'K' again to stop")
        record_audio()
    
    elif choice == "2":
        file_path = input("\nEnter WAV file path: ")
        if file_path.strip():
            print("\nTranscribing file...")
            transcribe_wav_file(file_path.strip())

if __name__ == "__main__":
    main()
```

### 3. Prompt Customization Example

```python
# prompt_customization_example.py
import os
from dhvagna import (
    record_audio, 
    transcribe_wav_file, 
    set_custom_prompts,
    reset_prompts,
    DEFAULT_TRANSCRIPTION_PROMPT,
    DEFAULT_REFINEMENT_PROMPT_TEMPLATE,
    DEFAULT_TITLE_FORMAT
)

# View and customize different aspects of transcription
def main():
    print("===== Dhvagna Customization Example =====")
    
    # First, verify API key is set
    if not check_api_key():
        return
    
    # Let's customize for technical documentation
    technical_prompt = """
Transcribe this technical content. The speech may be in Telugu or English.
Identify the language and indicate it with [LANGUAGE: Telugu] or [LANGUAGE: English].
Focus on capturing:
- Code snippets and technical terms
- API references and documentation
- Software architecture descriptions
"""
    
    technical_template = """
Here is a technical transcription in {language}: "{text}"

Please refine this text while:
1. Maintaining all technical terms and code references exactly
2. Using proper technical writing style
3. Organizing content logically
"""
    
    technical_title = "💻 Technical {language} Documentation"
    
    # Set all custom options
    set_custom_prompts(
        new_transcription_prompt=technical_prompt,
        new_refinement_prompt_template=technical_template,
        new_title_format=technical_title
    )
    
    # Try the custom settings
    print("\nPress 'K' to start recording technical documentation")
    print("Press 'K' again to stop")
    record_audio()

if __name__ == "__main__":
    main()
```

### 4. Advanced Example

```python
# advanced_example.py
import os
from rich.console import Console
from rich.panel import Panel
from dhvagna import (
    record_audio, 
    transcribe_wav_file, 
    set_custom_prompts,
    reset_prompts
)

# Create Rich console for beautiful output
console = Console()

class TranscriptionProfile:
    """Represents a complete transcription configuration profile"""
    def __init__(self, name, prompt, template, title_format, description):
        self.name = name
        self.prompt = prompt
        self.template = template
        self.title_format = title_format
        self.description = description
    
    def apply(self):
        """Apply this profile's settings"""
        set_custom_prompts(
            new_transcription_prompt=self.prompt,
            new_refinement_prompt_template=self.template,
            new_title_format=self.title_format
        )

# Define specialized transcription profiles
PROFILES = {
    "academic": TranscriptionProfile(
        name="Academic",
        prompt="""
Transcribe this academic content with high precision. The speech may be in Telugu or English.
Identify the language and indicate it with [LANGUAGE: Telugu] or [LANGUAGE: English].
Focus on capturing:
- Technical and academic terminology
- Research methodologies and findings
- Statistical data and measurements
""",
        template="""
Here is an academic transcription in {language}: "{text}"

Please refine this content while:
1. Maintaining academic rigor and technical accuracy
2. Preserving all citations and references
3. Structuring into proper academic sections
""",
        title_format="🎓 Academic {language} Transcript",
        description="Optimized for research presentations, lectures, and academic discussions"
    ),
    
    # Additional profiles defined for medical and legal transcription
    # ...
}

def main():
    console.print(Panel(
        "[bold cyan]Welcome to the Advanced Dhvagna Example![/]\n\n"
        "This example demonstrates all features including:\n"
        "• Specialized transcription profiles\n"
        "• Custom formatting options\n"
        "• Multiple use cases\n"
        "• Profile switching",
        title="🚀 Advanced Features Demo",
        border_style="green"
    ))
    
    # Apply profile and record
    profile = PROFILES["academic"]
    profile.apply()
    console.print(f"\n[green]✓[/] Applied [bold]{profile.name}[/] profile!")
    
    console.print("\nPress 'K' to start recording")
    console.print("Press 'K' again to stop")
    record_audio()

if __name__ == "__main__":
    main()
```

Each example is located in the `dhvagna/examples/` directory and demonstrates different aspects of using the Dhvagna package.

## 🛠️ API Key Troubleshooting

If you encounter API key issues:

- **Invalid key format**: Ensure your key starts with `dk-`
- **Verification failure**: Check that your key is registered in our system
- **Usage limit exceeded**: Contact us to upgrade your plan if you need more than 100 transcriptions
- **Server connection issues**: The package will run in offline mode with limited functionality if it can't connect to our servers

## 🎯 Use Cases

### Academic Research
- Transcribe research presentations
- Document academic discussions
- Record seminar content

### Medical Transcription
- Patient consultations
- Medical dictations
- Clinical observations

### Legal Documentation
- Court proceedings
- Client interviews
- Legal consultations

### General Purpose
- Meeting minutes
- Interviews
- Personal notes

## 🛠️ Customization Options

### 1. Transcription Prompts
Customize how the initial transcription is processed:
```python
set_custom_prompts(new_transcription_prompt="Your custom prompt here")
```

### 2. Refinement Templates
Control how the transcription is refined:
```python
template = """
Refine this {language} text: "{text}"
Include your refinement instructions here.
"""
set_custom_prompts(new_refinement_prompt_template=template)
```

### 3. Title Formatting
Customize the display title:
```python
set_custom_prompts(new_title_format="✨ Custom {language} Title")
```

## 📝 Requirements

- Python 3.7+
- Microphone (for recording features)
- Internet connection (for AI processing and API key verification)
- WAV file support
- Valid Dhvagna API key

## 🔧 Technical Details

- Uses Dhvagna for advanced language processing
- Supports WAV audio format
- Real-time audio processing
- Automatic language detection
- Multi-threaded recording handling
- Smart error recovery and fallback options
- Secure API key validation and usage tracking

## 🌐 Links

- GitHub: [https://github.com/gnanesh-16/Dhvagna](https://github.com/gnanesh-16/Dhvagna)
- pypi: [https://pypi.org/project/dhvagna/#description](https://pypi.org/project/dhvagna/#description)
- Author: Gnox79 {Gnanesh B}

## 📄 License

MIT License - See LICENSE file for details

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. See our [Contributing Guidelines](CONTRIBUTING.md) for more information.
