# Huginn

**Huginn** is an AI-enhanced extension for [Bjorn](https://github.com/infinition/Bjorn), the Raspberry Pi-based ethical hacking assistant. Named after one of Odin's ravens, Huginn represents "thought"—perfectly aligned with the project’s goal of augmenting network security assessments with intelligent analysis and automation.

## Features

- 🧠 GPT-4-based vulnerability insights
- 📄 Professional HTML-to-PDF pentest reports
- 🧪 Hooks into Bjorn's scanning/orchestration system
- 📟 Summary output on Bjorn's e-ink screen
- 🌐 Optional Web UI enhancements

## Getting Started

### Requirements
- Python 3.11+
- `wkhtmltopdf`
- OpenAI API Key
- Existing Bjorn install

### Setup
```bash
git clone https://github.com/yourname/huginn.git
cd huginn
cp .env.example .env
pip install -r server/requirements.txt
```

### Run Server
```bash
cd server
python app.py
```

### Run Report Generator
```bash
cd reports
python generate_report.py
```

## Integrating with Bjorn
1. Copy `integration/bjorn_patch_orchestrator.py` into the `bjorn/` project.
2. After the nmap scan completes in Bjorn, call `send_to_ai(scan_output)` to receive and store analysis.
3. Copy `integration/bjorn_patch_webapp.py` into Bjorn’s `webapp.py` to enable report downloads.
4. Add `/generate_report` Flask route to trigger `generate_report.py` via subprocess.
5. Use the e-ink display module to show summary text from the AI analysis JSON.

## Docker
```bash
docker build -t huginn .
docker run -p 5000:5000 huginn
```

## License
MIT
```
