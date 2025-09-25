# blingauto_client

## Architecture Deep Dive

### Clean Architecture + DDD Pattern

```
┌─────────────────────────────────────────────────────────┐
│                    Presentation Layer                    │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐     │
│  │    BLoC     │  │   Widgets   │  │   Routes    │     │
│  └─────────────┘  └─────────────┘  └─────────────┘     │
└─────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────┐
│                     Domain Layer                        │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐     │
│  │ Aggregates  │  │ Use Cases   │  │ Repositories│     │
│  └─────────────┘  └─────────────┘  └─────────────┘     │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐     │
│  │  Entities   │  │   Events    │  │   Services  │     │
│  └─────────────┘  └─────────────┘  └─────────────┘     │
└─────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────┐
│                      Data Layer                         │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐     │
│  │ Data Sources│  │    Models   │  │ Repositories│     │
│  └─────────────┘  └─────────────┘  └─────────────┘     │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐     │
│  │   SQLite    │  │     API     │  │   Cache     │     │
│  └─────────────┘  └─────────────┘  └─────────────┘     │
└─────────────────────────────────────────────────────────┘
```

### Folder Structure

```
lib/
├── app/                          # Application bootstrap
│   ├── app.dart                 # Main application widget
│   ├── app_config.dart          # Environment configuration
│   └── app_initializer.dart     # App initialization logic
├── core/                         # Infrastructure & shared services
│   ├── config/                  # Configuration files
│   ├── constants/               # App-wide constants (colors, strings)
│   ├── di/                      # Dependency injection setup
│   ├── domain/                  # Base domain classes
│   ├── error/                   # Error handling & exceptions
│   ├── messaging/               # Event bus system
│   ├── network/                 # Network configuration
│   ├── providers/               # Global providers (theme, etc.)
│   ├── routing/                 # Route management
│   ├── security/                # Security interfaces
│   ├── services/                # Core service interfaces
│   └── utils/                   # Utility functions
├── data/                         # External data implementations
│   ├── local/                   # Local storage (SQLite, preferences)
│   └── services/                # Service implementations
├── features/                     # Business feature modules
│   ├── auth/                    # Authentication feature
│   ├── booking/                 # Booking management
│   ├── notification/            # Notifications
│   ├── profile/                 # User profile
│   ├── service/                 # Service catalog
│   ├── tracking/                # Real-time tracking
│   └── vehicle/                 # Vehicle management
├── routes/                       # Application routing
│   ├── route_names.dart         # Route name constants
│   └── router.dart              # Route configuration
├── shared/                       # Cross-feature shared components
│   ├── domain/                  # Shared domain objects
│   ├── presentation/            # Shared UI components
│   └── utils/                   # Shared utilities
├── main.dart                     # Application entry point
├── main_optimized.dart          # Performance-optimized entry point
└── main_simple.dart             # Simple entry point for testing
```
