# 📱 Telecom Virtual Agent

<div align="center">
  
![License](https://img.shields.io/badge/license-MIT-blue)
![Platform](https://img.shields.io/badge/platform-Google%20Cloud-4285F4)
![Status](https://img.shields.io/badge/status-active-success)

*An intelligent virtual assistant for telecommunications customer service built on Google's Conversational AI platform*

</div>

## 🌟 Overview

This virtual assistant is designed to provide seamless telecommunications customer service, handling a wide range of inquiries automatically before connecting customers to human agents when necessary. Built on Google's robust Conversational AI platform, it delivers personalized, efficient support around the clock.

## ✨ Key Features

### Core Capabilities

| Feature | Description |
|:-------:|:------------|
| 💼 **Account Management** | Access balance information and manage account profile details |
| 🔐 **Authentication** | Secure verification through phone number and passcode |
| 💳 **Billing Support** | Explanation of charges and convenient payment processing |
| 🛠️ **Technical Assistance** | Step-by-step troubleshooting for common service issues |
| 👥 **Agent Handoff** | Smooth transition to human agents for complex inquiries |

### Technical Support Categories

The assistant provides automated troubleshooting for frequent technical issues:

- 📶 No signal/poor network connectivity
- 🚀 Slow data connections
- 📞 Dropped calls

### Conversation Flows

```mermaid
graph TD
    A[Default Start Flow] --> B{Menu Options}
    B -->|Account/Balance| C[Authentication]
    B -->|Billing| C
    B -->|Technical Support| D[Technical Support Flow]
    B -->|Agent Request| E[Agent Handoff]
    B -->|Promotions| F[New Promotions]
    C -->|Successful Auth| G[Account Management/Billing]
    C -->|Failed Auth| E
    D -->|Troubleshooting| H[Issue Resolution]
    H -->|Resolved| I[End Session]
    H -->|Unresolved| E
```

## 🏗️ Technical Architecture

The virtual agent is built with these components:

- **Entity Types**: Structured data recognition (phone numbers, dates, names)
- **Intents**: Machine learning models trained to understand user requests
- **Flows**: Orchestrated conversation paths for different scenarios
- **Pages**: Individual interaction steps within each flow
- **Webhooks**: API integrations for secure verification and data retrieval

## ⚙️ Setup & Deployment

### Prerequisites

- Google Cloud Platform account with Dialogflow CX / CCAI enabled
- Access to webhook endpoints (configured at `tia-func-907971469140.us-central1.run.app`)

### Configuration

The agent includes pre-configured settings:

- 🌐 Default language: English
- 🗣️ Speech adaptation for improved recognition
- 🔢 DTMF (touch-tone) support for phone interactions
- 📊 Comprehensive logging for conversation analytics

## 👤 User Experience

The virtual agent provides a context-aware conversational interface with time-based greetings:

> "Good [morning/afternoon/evening]! Hello! I'm Mobile's virtual assistant. What can I assist you with today?"

## 🚀 Extended Capabilities

- **Multi-channel Support**: Optimized for voice, chat, and messaging platforms
- **Authentication Security**: Three-attempt limit with automatic agent handoff
- **Integration Ready**: Flexible webhook system for seamless backend connectivity

## 🔧 Development & Architecture

```mermaid
graph TD
    User[Customer] --> Channels
    subgraph Channels
        Web[Web Widget]
        Mobile[Mobile App]
        SMS[SMS]
        Phone[Phone IVR]
    end
    
    Channels --> DF[Dialogflow CX]
    
    subgraph "Google Cloud Platform"
        DF --> Webhook[Cloud Functions Webhook]
        Webhook --> Firestore[Firestore Database]
        Webhook --> SecretMgr[Secret Manager]
        Webhook --> Legacy[Legacy Systems API]
        DF --> Logs[Cloud Logging]
        Webhook --> Logs
    end
    
    Legacy --> CRM[Customer Records]
    Legacy --> Billing[Billing System]
    Legacy --> Inventory[Inventory Management]
```

The agent architecture allows for easy expansion of:

- ✅ New intents and training phrases
- ✅ Additional flows for new service offerings
- ✅ Enhanced entity recognition capabilities

## 🔄 Interaction Flow

```mermaid
sequenceDiagram
    participant User
    participant DF as Dialogflow CX
    participant CF as Cloud Function
    participant DB as Database
    
    User->>DF: "What's my account balance?"
    DF->>DF: Intent recognition
    DF->>DF: Check authentication state
    alt Not authenticated
        DF->>User: Request phone number
        User->>DF: Provides phone number
        DF->>CF: Validate phone number
        CF->>DB: Query customer records
        DB->>CF: Return validation result
        CF->>DF: Phone validation response
        DF->>User: Request passcode
        User->>DF: Provides passcode
        DF->>CF: Validate passcode
        CF->>DB: Check credentials
        DB->>CF: Return authentication result
        CF->>DF: Authentication response
    end
    
    DF->>CF: Request account balance
    CF->>DB: Query balance information
    DB->>CF: Return balance data
    CF->>DF: Balance information
    DF->>User: "Your current balance is $X"
    DF->>User: "Is there anything else?"
```

## 🔮 Future Enhancements

- 💰 Additional payment methods and billing options
- 🛠️ Expanded technical troubleshooting capabilities
- 🎯 Personalized recommendations based on customer profiles
- 🌐 Multilingual support for diverse customer base

---

<div align="center">

*This virtual agent provides 24/7 customer support for telecommunications services while maintaining robust security standards and ensuring seamless handoff to human agents when required.*

[Report an Issue](https://github.com/Wiikay/CCAI/issues) • [Request a Feature](https://github.com/Wiikay/CCAI/issues)

</div>