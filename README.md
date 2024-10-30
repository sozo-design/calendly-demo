# Calendly Integration Demo

A flexible and customizable integration solution for embedding Calendly scheduling widgets into your website. This project provides both inline and popup widget options with various customization features.

## Features

- **Multiple Widget Types**
  - Inline Widget: Embedded directly in your webpage
  - Popup Widget: Opens in a modal overlay

- **Customization Options**
  - Hide/Show event details
  - Hide/Show cookie banner
  - Enable/Disable auto-resize
  - Pre-fill attendee information

- **Developer Tools**
  - Real-time code generation
  - Event logging
  - Copy-to-clipboard functionality
  - Auto-formatting

## Quick Start

1. Clone or download this repository
2. Replace the Calendly URL in `config.url` with your own Calendly scheduling link:
```javascript
const config = {
    url: 'YOUR_CALENDLY_URL_HERE',
    hideDetails: false,
    hideCookieBanner: false,
    enableResize: false
};
```
3. Open `index.html` in a web browser

## Usage

### Basic Integration

1. Open the demo page
2. Select your preferred widget type (Inline/Popup)
3. Configure desired options
4. Click "Generate Code"
5. Copy the generated code
6. Paste into your website's HTML

### Configuration Options

#### Widget Settings
- **Hide Event Type Details**: Removes event information from the scheduling page
- **Hide Cookie Banner**: Disables the GDPR cookie consent banner
- **Enable Auto Resize**: Allows the widget to adjust its height automatically

#### Pre-fill Information
- **Name**: Pre-populate the name field
- **Email**: Pre-populate the email field
- **Custom Answer**: Pre-fill custom question responses

### Event Handling

The integration includes built-in event handling for:
- Profile page views
- Event type views
- Date/time selection
- Successful scheduling

Example event listener:
```javascript
window.addEventListener('message', function(e) {
    if (e.origin === "https://calendly.com" && e.data.event) {
        console.log('Calendly Event:', e.data.event);
        if (e.data.event === 'calendly.event_scheduled') {
            console.log('Meeting scheduled!');
        }
    }
});
```

## Technical Details

### Dependencies
- Calendly External Widget CSS
- Calendly External Widget JavaScript

### Browser Support
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

### Performance Considerations
- JavaScript is loaded with `defer` attribute
- CSS is only loaded for popup widgets
- Minimal DOM manipulation
- Event delegation for better performance

## Integration Examples

### Inline Widget
```html
<!-- Calendly Inline Widget Begin -->
<div class="calendly-inline-widget" style="min-width:320px;height:700px;" id="calendly-embed"></div>
<script src="https://assets.calendly.com/assets/external/widget.js" defer></script>
<script>
window.addEventListener('load', function() {
    Calendly.initInlineWidget({
        url: 'YOUR_CALENDLY_URL',
        parentElement: document.getElementById('calendly-embed')
    });
});
</script>
<!-- Calendly Inline Widget End -->
```

### Popup Widget
```html
<!-- Calendly Widget Begin -->
<link href="https://assets.calendly.com/assets/external/widget.css" rel="stylesheet">
<script src="https://assets.calendly.com/assets/external/widget.js" defer></script>
<button onclick="openCalendlyPopup()">Schedule Meeting</button>
<script>
function openCalendlyPopup() {
    Calendly.initPopupWidget({
        url: 'YOUR_CALENDLY_URL'
    });
    return false;
}
</script>
<!-- Calendly Widget End -->
```

## Customization

### Styling
The demo includes default styles that can be customized:
- Widget container styling
- Button appearances
- Notification displays
- Event log formatting

### Advanced Configuration
For advanced users, the integration supports:
- Custom URL parameters
- UTM tracking
- Custom event handling
- Dynamic prefill data

## Troubleshooting

Common issues and solutions:

1. **Widget Not Loading**
   - Check if Calendly scripts are loading properly
   - Verify your Calendly URL is correct
   - Check browser console for errors

2. **Height Issues**
   - Enable auto-resize option
   - Set explicit height in container div
   - Check for CSS conflicts

3. **Event Handling**
   - Verify origin in message listener
   - Check event names match Calendly's documentation
   - Ensure proper event bubbling
