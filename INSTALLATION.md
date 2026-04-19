# Installation Guide

## Latest Stable Release (PyPI)

Install the latest stable version from PyPI:

```bash
pip install appium-mcp
```

## Development Installation

For development and contributing:

```bash
# Clone the repository
git clone https://github.com/youcanautomate-yca/ai-driven-mobile-automation.git
cd ai-driven-mobile-automation

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install in development mode
pip install -e ".[dev]"

# Install pre-commit hooks (optional)
pre-commit install
```

## Prerequisites

### System Requirements
- Python 3.8 or higher
- Node.js 14+ (for Appium server)
- macOS, Linux, or Windows

### For iOS Testing
- Xcode 12.0 or higher
- iOS Simulator or physical iOS device

### For Android Testing
- Android SDK/Emulator
- Java Development Kit (JDK) 8+

## Appium Server Setup

### Installation
```bash
# Install Appium globally
npm install -g appium

# Install Appium drivers
appium driver install xcuitest  # For iOS
appium driver install uiautomator2  # For Android
```

### Start Appium Server
```bash
# Start Appium on default port (4723)
appium

# Or specify custom host/port
appium --address 0.0.0.0 --port 4723
```

## AWS Setup (Optional)

For AI-powered test generation using AWS Bedrock:

1. Configure AWS credentials:
```bash
aws configure

# Enter: AWS Access Key ID, Secret Access Key, Region, Output format
```

2. Ensure your AWS account has access to Claude models in Bedrock:
   - Go to AWS Console > Bedrock > Model Access
   - Request access to Claude models you want to use

3. Set Bedrock model in `.env`:
```
BEDROCK_MODEL=anthropic.claude-3-sonnet-20240229-v1:0
AWS_REGION=us-east-1
```

## Verification

Verify installation successfully:

```bash
# Check package installation
python -c "import appium_mcp; print('✓ appium-mcp installed')"

# Check Appium server
appium --version

# Start interactive chatbot
appium-mcp-chatbot
```

## Troubleshooting

### Import Errors
```bash
# Ensure virtual environment is activated
source venv/bin/activate

# Reinstall with verbose output
pip install -v appium-mcp
```

### Appium Connection Issues
```bash
# Check if Appium is running
curl http://localhost:4723/status

# Start Appium with debug output
appium --log-level debug
```

### AWS Bedrock Access
```bash
# Verify AWS credentials
aws sts get-caller-identity

# Check Bedrock model access
aws bedrock list-foundation-models --region us-east-1
```

## Using as a Library

```python
from appium_mcp import MobileAutomationFramework
from appium.options.ios import XCUITestOptions

# Initialize framework
framework = MobileAutomationFramework()

# Or use with custom driver options
options = XCUITestOptions()
options.device_name = "iPhone 14"
options.platform_version = "16.0"

driver = framework.create_session(options)
```

## Next Steps

- [Quick Start Guide](README.md#quick-start-interactive-chatbot)
- [Page Object Model Guide](POM_GUIDE.md)
- [Chatbot Guide](CHATBOT_GUIDE.md)
- [API Documentation](README.md)
