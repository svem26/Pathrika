# Pathrika
Your Personal Dynamic Information Wall

# Pathrika

> A self-hosted, dynamic information dashboard designed for wall-mounted displays, including E-ink screens.

![License](https://img.shields.io/github/license/yourusername/patrika)
![Version](https://img.shields.io/github/v/release/yourusername/patrika)
![Build Status](https://img.shields.io/github/workflow/status/yourusername/patrika/CI)

Patrika transforms your wall-mounted display into a living newspaper, aggregating and presenting your personal information feeds in a clean, distraction-free interface. Perfect for E-ink displays and regular monitors alike.

## 🌟 Features

### Core Features
- **Dynamic Masonry Layout**: Auto-organizing, responsive grid that reshuffles periodically
- **Rotating Widget Stacks**: Multiple information widgets that rotate in each grid position
- **E-ink Optimized**: Special rendering mode for E-ink displays with optimized refresh rates
- **Self-hosted**: Complete control over your data and privacy

### Information Sources
- Live News Updates from your chosen sources and topics
- Live Sports scores of your choice
- Plex Media Updates
- YouTube Channel Summaries
- Home Assistant Integration
- Calendar Events
- Family Location Tracking
- RSS Feed Aggregation
- Social Media Updates
- Home Status Monitoring

## Getting Started

### Prerequisites
- Node.js 18.0 or higher
- A modern web browser
- (Optional) Home Assistant instance
- (Optional) Plex Media Server

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/patrika.git
cd patrika
```

2. Install dependencies:
```bash
npm install
```

3. Configure your sources:
```bash
cp .env.example .env
# Edit .env with your settings
```

4. Start the server:
```bash
npm start
```

### Docker Installation
```bash
docker pull yourusername/patrika
docker run -p 3000:3000 -v config:/app/config yourusername/patrika
```

## ⚙️ Configuration

### Basic Configuration
Create a `config.yaml` file:

```yaml
display:
  type: "e-ink"  # or "regular"
  refresh_rate: 300  # seconds
  layout:
    columns: 4
    shuffle_interval: 1800  # seconds

sources:
  plex:
    enabled: true
    server_url: "http://your-plex-server:32400"
    token: "your-token"
  
  youtube:
    enabled: true
    channels:
      - "UCXuqSBlHAE6Xw-yeJA0Tunw"  # Linus Tech Tips
      - "UCBJycsmduvYEL83R_U4JriQ"  # MKBHD

  home_assistant:
    enabled: true
    url: "http://your-homeassistant:8123"
    token: "your-long-lived-token"
```

### Widget Configuration
Each widget can be customized in `widgets.yaml`:

```yaml
widgets:
  plex_recent:
    rotation_interval: 30
    max_items: 5
    
  weather:
    location: "New York"
    units: "metric"
```

## 🎨 Customization

### Creating Custom Widgets

1. Create a new widget file in `src/widgets`:
```typescript
import { Widget } from '../types';

export class CustomWidget implements Widget {
  async getData(): Promise<any> {
    // Fetch and return your data
  }

  render(): JSX.Element {
    // Return your widget's JSX
  }
}
```

2. Register your widget in `src/widgets/index.ts`

### Styling
- Override default styles in `src/styles/custom.css`
- E-ink specific styles in `src/styles/e-ink.css`

## Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

### Development Setup
1. Fork the repository
2. Create a feature branch
3. Install development dependencies:
```bash
npm install --dev
```
4. Run tests:
```bash
npm test
```

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

##  Acknowledgments

- [Home Assistant](https://www.home-assistant.io/) for home automation integration
- [Plex](https://www.plex.tv/) for media server capabilities
- All our [contributors](CONTRIBUTORS.md)

## Documentation

Full documentation is available at [docs.patrika.dev](https://docs.patrika.dev)

##  Security

For security issues, please read our [Security Policy](SECURITY.md) and email security@patrika.dev
