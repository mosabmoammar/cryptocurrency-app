# Cryptocurrency App

An Android app built with Kotlin and Jetpack Compose that lists cryptocurrencies and shows details for each coin, using the public CoinPaprika API. It is structured with Clean Architecture and MVVM.

<!--
Screenshots: add the coin list and a coin detail screen, for example:
<p float="left">
  <img src="screenshots/coin_list.png" width="220" />
  <img src="screenshots/coin_detail.png" width="220" />
</p>
-->

## Features

- Coin list with rank, name, symbol and active status
- Coin detail screen with the description, tags and team members
- Loading and error states driven by a `Resource` wrapper (success, error, loading)
- Navigation between the list and detail screens with Navigation Compose

## Tech stack

| Area | Tools |
|---|---|
| UI | Jetpack Compose, Material 3, Accompanist FlowLayout |
| Architecture | Clean Architecture, MVVM, use cases |
| Dependency injection | Hilt |
| Networking | Retrofit, Gson, OkHttp logging interceptor |
| Async | Kotlin Coroutines and Flow |

## Architecture

```
com.mosab.cryptocurrency/
├── data/
│   ├── remote/        # CoinPaprikaApi and DTOs
│   └── repository/    # CoinRepositoryImpl
├── domain/
│   ├── model/         # Coin, CoinDetail
│   ├── repository/    # CoinRepository contract
│   └── usecase/       # GetCoinsUseCase, GetCoinUseCase
├── presentation/
│   ├── coinlist/      # screen, ViewModel, state, list item
│   └── coindetail/    # screen, ViewModel, state, tag and team components
├── di/                # Hilt AppModule
└── common/            # Resource, constants
```

Each use case returns a `Flow<Resource<T>>`, and the ViewModels collect it into a single UI state that the screens render.

## Getting started

1. Clone the repository and open it in Android Studio.
2. Let Gradle sync, then run the `app` configuration on a device or emulator (Android 7.0, API 24, or newer).

No API key is needed. The app calls `https://api.coinpaprika.com/`.
