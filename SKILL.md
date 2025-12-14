# Email Capture & Lead Magnet System

Complete email marketing integration system using Systeme.io API. Creates site-specific popups, lead magnets, and tagged subscriber management.

---

## Systeme.io API Integration

### API Configuration
```javascript
const SYSTEME_API = {
  baseUrl: 'https://api.systeme.io/api',
  apiKey: '82tyjz6r3hzl5kq6qyl9ix9rusrkh3j7c8abj0fxaotfu4ruqftksnvuwxujhloc',
  headers: {
    'X-API-Key': '82tyjz6r3hzl5kq6qyl9ix9rusrkh3j7c8abj0fxaotfu4ruqftksnvuwxujhloc',
    'Content-Type': 'application/json'
  }
};
```

### Available Endpoints
```
GET  /contacts          - List contacts
POST /contacts          - Create contact
GET  /contacts/{id}     - Get contact
PUT  /contacts/{id}     - Update contact
DELETE /contacts/{id}   - Delete contact
GET  /tags              - List tags
POST /tags              - Create tag
```

---

## Tag Strategy by Site

### Tag Format
```
[site-slug]-[source]-[content-type]
```

### Tags for 7 Sites Being Built

#### wealthfromai.com
```
wealthfromai-popup-aiwealth101
wealthfromai-footer-newsletter
wealthfromai-sidebar-stockalerts
wealthfromai-leadmagnet-aistrategyguide
wealthfromai-exit-freeebook
```

#### aidiscoverydigest.com
```
aidiscoverydigest-popup-weeklydigest
aidiscoverydigest-footer-newsletter
aidiscoverydigest-sidebar-toolalerts
aidiscoverydigest-leadmagnet-top100tools
aidiscoverydigest-exit-trendsreport
```

#### aiinactionhub.com
```
aiinactionhub-popup-practicalai
aiinactionhub-footer-newsletter
aiinactionhub-sidebar-tutorialupdates
aiinactionhub-leadmagnet-prompttemplates
aiinactionhub-exit-implementationguide
```

#### clearainews.com
```
clearainews-popup-dailybriefing
clearainews-footer-newsletter
clearainews-sidebar-breakingalerts
clearainews-leadmagnet-ailandscapereport
clearainews-exit-weeklyrecap
```

#### pulsegearreviews.com
```
pulsegearreviews-popup-buyersguide
pulsegearreviews-footer-newsletter
pulsegearreviews-sidebar-dealalerts
pulsegearreviews-leadmagnet-fitnesstechguide
pulsegearreviews-exit-comparisoncharts
```

#### wearablegearreviews.com
```
wearablegearreviews-popup-healthdata101
wearablegearreviews-footer-newsletter
wearablegearreviews-sidebar-newreleases
wearablegearreviews-leadmagnet-accuracyguide
wearablegearreviews-exit-topwearables
```

#### smarthomegearreviews.com
```
smarthomegearreviews-popup-setupguide
smarthomegearreviews-footer-newsletter
smarthomegearreviews-sidebar-ecosystemupdates
smarthomegearreviews-leadmagnet-starterkit
smarthomegearreviews-exit-compatibilityguide
```

---

## Lead Magnets by Site

### wealthfromai.com
**Lead Magnet**: "AI Wealth Strategy Blueprint 2025"
- Format: PDF Guide (25+ pages)
- Content: Top AI tools for investing, automation strategies, case studies
- Popup trigger: 45% scroll or 30 second delay
- Exit intent: Yes

### aidiscoverydigest.com
**Lead Magnet**: "Top 100 AI Tools Database"
- Format: Notion Template + PDF
- Content: Curated AI tools by category with ratings
- Popup trigger: End of article
- Exit intent: Yes

### aiinactionhub.com
**Lead Magnet**: "AI Prompt Template Library"
- Format: Google Sheets + PDF
- Content: 100+ proven prompts for business use
- Popup trigger: 60% scroll
- Exit intent: Yes

### clearainews.com
**Lead Magnet**: "AI Industry Landscape Report Q1 2025"
- Format: PDF Report (40+ pages)
- Content: Market analysis, key players, trends
- Popup trigger: After 2 articles read
- Exit intent: Yes

### pulsegearreviews.com
**Lead Magnet**: "Ultimate Fitness Tech Buyer's Guide"
- Format: PDF + Comparison Spreadsheet
- Content: How to choose, what to look for, top picks by budget
- Popup trigger: On product pages
- Exit intent: Yes

### wearablegearreviews.com
**Lead Magnet**: "Wearable Accuracy Testing Guide"
- Format: PDF Guide
- Content: How to test your device, accuracy benchmarks
- Popup trigger: 40% scroll on review pages
- Exit intent: Yes

### smarthomegearreviews.com
**Lead Magnet**: "Smart Home Starter Kit Checklist"
- Format: PDF Checklist + Setup Guide
- Content: Essential devices, setup order, compatibility matrix
- Popup trigger: Homepage, category pages
- Exit intent: Yes

---

## Popup Component Templates

### Standard Exit-Intent Popup
```html
<div class="email-popup exit-intent" data-site="[SITE-SLUG]" data-tag="[TAG]">
  <div class="popup-overlay"></div>
  <div class="popup-container">
    <button class="popup-close" aria-label="Close">×</button>
    <div class="popup-content">
      <div class="popup-icon">
        <!-- Site-specific icon -->
      </div>
      <h3 class="popup-headline">[SITE-SPECIFIC-HEADLINE]</h3>
      <p class="popup-subtext">[SITE-SPECIFIC-DESCRIPTION]</p>
      <form class="popup-form" data-systeme-tag="[TAG]">
        <input type="email" name="email" placeholder="Enter your email" required>
        <button type="submit" class="btn-popup-submit">[CTA-TEXT]</button>
      </form>
      <p class="popup-disclaimer">No spam, ever. Unsubscribe anytime.</p>
    </div>
  </div>
</div>
```

### Site-Specific Popup Styles

#### wealthfromai.com (Premium Dark)
```css
.email-popup[data-site="wealthfromai"] {
  --popup-bg: linear-gradient(135deg, #0A0F1C 0%, #141B2D 100%);
  --popup-accent: #D4AF37;
  --popup-text: #F5F5F5;
  --popup-btn-bg: #D4AF37;
  --popup-btn-text: #0A0F1C;
}

.email-popup[data-site="wealthfromai"] .popup-icon::before {
  content: "📈";
  font-size: 3rem;
}

.email-popup[data-site="wealthfromai"] .popup-headline {
  font-family: 'DM Serif Display', serif;
}
```

#### clearainews.com (Editorial)
```css
.email-popup[data-site="clearainews"] {
  --popup-bg: #FFFFFF;
  --popup-accent: #1E40AF;
  --popup-text: #0F172A;
  --popup-btn-bg: #1E40AF;
  --popup-btn-text: #FFFFFF;
  --popup-border: 1px solid #E2E8F0;
}

.email-popup[data-site="clearainews"] .popup-icon::before {
  content: "📰";
  font-size: 3rem;
}
```

#### pulsegearreviews.com (Athletic Bold)
```css
.email-popup[data-site="pulsegearreviews"] {
  --popup-bg: #FFFFFF;
  --popup-accent: #FF4136;
  --popup-text: #1A1A1A;
  --popup-btn-bg: #FF4136;
  --popup-btn-text: #FFFFFF;
}

.email-popup[data-site="pulsegearreviews"] .popup-icon::before {
  content: "💪";
  font-size: 3rem;
}

.email-popup[data-site="pulsegearreviews"] .popup-headline {
  font-family: 'Bebas Neue', sans-serif;
  text-transform: uppercase;
}
```

---

## JavaScript Implementation

### Popup Controller
```javascript
class EmailPopupController {
  constructor(config) {
    this.config = {
      site: config.site,
      tag: config.tag,
      systemeApiKey: '82tyjz6r3hzl5kq6qyl9ix9rusrkh3j7c8abj0fxaotfu4ruqftksnvuwxujhloc',
      triggers: {
        scroll: config.scrollPercent || 50,
        delay: config.delaySeconds || 30,
        exitIntent: config.exitIntent !== false
      },
      cookieDays: config.cookieDays || 7
    };
    
    this.init();
  }
  
  init() {
    if (this.hasSeenPopup()) return;
    
    this.setupTriggers();
    this.setupForm();
  }
  
  hasSeenPopup() {
    return document.cookie.includes(`popup_${this.config.site}=seen`);
  }
  
  setSeenCookie() {
    const days = this.config.cookieDays;
    const date = new Date();
    date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
    document.cookie = `popup_${this.config.site}=seen; expires=${date.toUTCString()}; path=/`;
  }
  
  setupTriggers() {
    // Scroll trigger
    if (this.config.triggers.scroll) {
      window.addEventListener('scroll', () => {
        const scrollPercent = (window.scrollY / (document.body.scrollHeight - window.innerHeight)) * 100;
        if (scrollPercent >= this.config.triggers.scroll) {
          this.showPopup();
        }
      }, { once: true });
    }
    
    // Exit intent trigger
    if (this.config.triggers.exitIntent) {
      document.addEventListener('mouseout', (e) => {
        if (e.clientY <= 0) {
          this.showPopup();
        }
      }, { once: true });
    }
    
    // Delay trigger
    if (this.config.triggers.delay) {
      setTimeout(() => this.showPopup(), this.config.triggers.delay * 1000);
    }
  }
  
  showPopup() {
    const popup = document.querySelector(`.email-popup[data-site="${this.config.site}"]`);
    if (popup) {
      popup.classList.add('active');
      document.body.style.overflow = 'hidden';
    }
  }
  
  hidePopup() {
    const popup = document.querySelector(`.email-popup[data-site="${this.config.site}"]`);
    if (popup) {
      popup.classList.remove('active');
      document.body.style.overflow = '';
      this.setSeenCookie();
    }
  }
  
  async setupForm() {
    const form = document.querySelector(`.email-popup[data-site="${this.config.site}"] .popup-form`);
    if (!form) return;
    
    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      const email = form.querySelector('input[name="email"]').value;
      const tag = form.dataset.systemeTag || this.config.tag;
      
      try {
        await this.submitToSysteme(email, tag);
        this.showSuccess();
      } catch (error) {
        this.showError(error);
      }
    });
  }
  
  async submitToSysteme(email, tag) {
    // Note: In production, this should go through your backend
    // to protect the API key
    const response = await fetch('/api/subscribe', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ email, tag, site: this.config.site })
    });
    
    if (!response.ok) throw new Error('Subscription failed');
    return response.json();
  }
  
  showSuccess() {
    const popup = document.querySelector(`.email-popup[data-site="${this.config.site}"]`);
    const content = popup.querySelector('.popup-content');
    content.innerHTML = `
      <div class="popup-success">
        <div class="success-icon">✓</div>
        <h3>You're In!</h3>
        <p>Check your inbox for your free guide.</p>
      </div>
    `;
    setTimeout(() => this.hidePopup(), 3000);
  }
}
```

### WordPress Backend Handler
```php
<?php
// functions.php or custom plugin

add_action('rest_api_init', function() {
    register_rest_route('email/v1', '/subscribe', [
        'methods' => 'POST',
        'callback' => 'handle_email_subscription',
        'permission_callback' => '__return_true'
    ]);
});

function handle_email_subscription($request) {
    $email = sanitize_email($request->get_param('email'));
    $tag = sanitize_text_field($request->get_param('tag'));
    $site = sanitize_text_field($request->get_param('site'));
    
    if (!is_email($email)) {
        return new WP_Error('invalid_email', 'Invalid email address', ['status' => 400]);
    }
    
    $systeme_api_key = '82tyjz6r3hzl5kq6qyl9ix9rusrkh3j7c8abj0fxaotfu4ruqftksnvuwxujhloc';
    
    $response = wp_remote_post('https://api.systeme.io/api/contacts', [
        'headers' => [
            'X-API-Key' => $systeme_api_key,
            'Content-Type' => 'application/json'
        ],
        'body' => json_encode([
            'email' => $email,
            'tags' => [$tag],
            'fields' => [
                'source_site' => $site
            ]
        ])
    ]);
    
    if (is_wp_error($response)) {
        return new WP_Error('api_error', 'Failed to subscribe', ['status' => 500]);
    }
    
    return ['success' => true, 'message' => 'Subscribed successfully'];
}
```

---

## n8n Workflow Integration

### Auto-Tag New Subscribers
```json
{
  "name": "Systeme.io Auto-Tag Workflow",
  "nodes": [
    {
      "name": "Webhook",
      "type": "n8n-nodes-base.webhook",
      "parameters": {
        "path": "systeme-webhook",
        "method": "POST"
      }
    },
    {
      "name": "Add Site Tag",
      "type": "n8n-nodes-base.httpRequest",
      "parameters": {
        "url": "https://api.systeme.io/api/contacts/{{ $json.contact_id }}/tags",
        "method": "POST",
        "headers": {
          "X-API-Key": "82tyjz6r3hzl5kq6qyl9ix9rusrkh3j7c8abj0fxaotfu4ruqftksnvuwxujhloc"
        },
        "body": {
          "tag_id": "{{ $json.tag_id }}"
        }
      }
    }
  ]
}
```

---

## Files Reference

```
email-capture-system/
├── SKILL.md (this file)
├── popups/
│   ├── popup-base.html
│   ├── popup-wealthfromai.html
│   ├── popup-clearainews.html
│   ├── popup-pulsegearreviews.html
│   └── ... (all sites)
├── css/
│   ├── popup-base.css
│   └── popup-site-themes.css
├── js/
│   ├── email-popup-controller.js
│   └── systeme-integration.js
├── php/
│   └── email-subscription-handler.php
├── lead-magnets/
│   ├── templates/
│   └── descriptions/
└── n8n/
    └── subscriber-tagging-workflow.json
```
