# Flutter Quiz App (Single-file Preview)

A Flutter quiz app preview implemented in a single Dart file (`Quiz app.dart`) with an attractive Material 3 UI. This repository also includes a minimal `lib/` structure and models for growing into a full Firebase-backed quiz application later.

## Quick Start

1) Ensure Flutter SDK is installed and on PATH

```bash
flutter --version
```

2) Install dependencies

```bash
flutter pub get
```

3) Run the single-file preview directly

```bash
flutter run -t "Quiz app.dart"
```

Alternatively, run the default entry (if you want to use `lib/main.dart` later):

```bash
flutter run
```

If you see an error about missing platform folders (`android/`, `ios/`), create them:

```bash
flutter create .
```

Then run again.

## What’s Included

- `Quiz app.dart`: Self-contained Flutter UI preview
  - Gradient AppBar, decorative background, welcoming header
  - Statistics cards with icons and shadows
  - 6-category grid with gradients and tap animation
  - Bottom navigation (static preview)
- `pubspec.yaml`: Minimal configuration with Material 3 enabled
- `lib/` (scaffolded for future expansion)
  - `lib/models/` (User, Quiz, Question, QuizResult)
  - `lib/services/` (AuthService, FirestoreService, QuizService)
  - `lib/utils/` (constants, theme, validators)
  - `lib/main.dart` (basic app entry)

Note: The single-file preview does not require Firebase to run. The `lib/` services are prepared for Firebase when you’re ready to integrate.

## Project Structure (current)

```
.
├── Quiz app.dart                # Single-file runnable preview
├── pubspec.yaml                 # Minimal Flutter app config
├── lib/
│   ├── main.dart                # Basic app entry (not required for preview)
│   ├── models/
│   │   ├── user_model.dart
│   │   ├── question_model.dart
│   │   ├── quiz_model.dart
│   │   └── quiz_result_model.dart
│   ├── services/
│   │   ├── auth_service.dart
│   │   ├── firestore_service.dart
│   │   └── quiz_service.dart
│   ├── utils/
│   │   ├── constants.dart
│   │   ├── theme.dart
│   │   └── validators.dart
│   ├── providers/               # Placeholder for future Provider classes
│   └── screens/                 # Placeholder for auth/home/quiz/profile
└── README.md
```

## Running in VS Code

- Open this folder in VS Code
- Make sure the Dart & Flutter extensions are installed
- Press F5 or use the Run panel
- If using the single-file entry, VS Code may not pick it automatically. Use the terminal:

```bash
flutter run -t "Quiz app.dart"
```

## Customization

- Colors: Adjust in `_buildInlineTheme()` inside `Quiz app.dart`
- Fonts: `pubspec.yaml` includes `uses-material-design: true`. To use Poppins as a bundled font, add the font files to `assets/fonts` and uncomment the `fonts:` section in `pubspec.yaml`, then run `flutter pub get`.

## Firebase (Optional, Later)

When you’re ready to turn the preview into a full app with Firebase Authentication and Firestore:

- Create a Firebase project
- Add `google-services.json` (Android) and `GoogleService-Info.plist` (iOS)
- Run `flutterfire configure`
- Add dependencies to `pubspec.yaml`:
  - `firebase_core`, `firebase_auth`, `cloud_firestore`
- Initialize Firebase in `main()` and wire services/providers to UI

## Troubleshooting

- Missing platform folders:

```bash
flutter create .
```

- Dependencies not resolving:

```bash
flutter pub get
```

- Run a specific file entry (this project uses spaces in filename):

```bash
flutter run -t "Quiz app.dart"
```

- Analyzer warnings about unused variables: run `Flutter: Clean Project` or `flutter clean` and rebuild:

```bash
flutter clean && flutter pub get && flutter run -t "Quiz app.dart"
```

## License

This project is provided as-is for learning and prototyping purposes.

# Flutter Quiz App

A comprehensive quiz application built with Flutter and Dart that includes multiple screens, state management, and a beautiful UI.

## Features

### 📱 Screens
1. **Home Screen** - Displays available quiz categories with cards showing:
   - Quiz title and icon
   - Number of questions
   - Difficulty level (Easy, Medium, Hard)
   - Time limit

2. **Quiz Screen** - Interactive question display with:
   - Progress bar showing completion
   - Timer countdown (when applicable)
   - Multiple choice answers with visual feedback
   - Previous/Next navigation
   - Submit button on the last question

3. **Results Screen** - Comprehensive results display showing:
   - Final score and percentage
   - Correct/Incorrect answer breakdown
   - Time taken
   - Performance message based on score
   - Action buttons for reviewing, retaking, or returning home

4. **Review Answers Screen** - Detailed answer review with:
   - All questions with user's selected answers
   - Correct answers highlighted
   - Explanations for each question
   - Visual indicators (checkmarks/X icons)

### 🎨 UI/UX Features
- **Material Design 3** styling
- **Gradient backgrounds** for visual appeal
- **Smooth animations** and transitions
- **Color-coded feedback** (green for correct, red for incorrect)
- **Progress indicators**
- **Responsive layout**

### 🧩 State Management
- Uses **Provider** for state management
- Manages current quiz, question index, user answers, score, and timer
- Reactive UI updates with ChangeNotifier

### 📊 Sample Data
The app includes 3 pre-loaded quizzes:
- **Dart Fundamentals** (5 questions, Easy, 5 minutes)
- **Flutter Basics** (5 questions, Medium, 7 minutes)
- **Advanced Dart** (5 questions, Hard, 10 minutes)

## Getting Started

### Prerequisites
- Flutter SDK installed
- Dart installed
- Android Studio / VS Code with Flutter extensions

### Installation

1. Install dependencies:
```bash
flutter pub get
```

2. Run the app:
```bash
flutter run
```

## Project Structure

```
Quiz app.dart          # Main application file with all components
pubspec.yaml           # Flutter project configuration
```

### Components in the file:
- **Models**: Question and Quiz data structures
- **Provider**: QuizProvider for state management
- **Screens**: HomeScreen, QuizScreen, ResultsScreen, ReviewAnswersScreen
- **Widgets**: ProgressBar, AnswerButton (reusable components)
- **Data**: QuizData with sample questions
- **Main App**: Entry point with routing

## Usage

1. **Select a Quiz**: On the home screen, tap any quiz card to start
2. **Answer Questions**: Click on answer choices (highlighted in blue)
3. **Navigate**: Use Previous/Next buttons to move between questions
4. **Submit**: Click "Submit" on the last question
5. **Review**: View detailed results and review your answers
6. **Actions**: 
   - Review answers with explanations
   - Retake the quiz
   - Return to home screen

## Customization

### Adding New Quizzes
Add new quizzes to the `QuizData.getQuizzes()` method:

```dart
Quiz(
  title: 'Your Quiz Title',
  category: 'Category Name',
  difficulty: 'Easy',  // or 'Medium', 'Hard'
  icon: '🎯',  // emoji icon
  timeLimit: 300,  // seconds
  questions: [
    Question(
      question: 'Your question?',
      options: ['Option A', 'Option B', 'Option C', 'Option D'],
      correctAnswerIndex: 0,
      explanation: 'Optional explanation text',
    ),
    // Add more questions...
  ],
)
```

### Styling
Modify colors, fonts, and layouts by editing the individual widgets in the file.

## Technologies Used
- **Flutter** - UI framework
- **Dart** - Programming language
- **Provider** - State management
- **Material Design 3** - UI components

## License
This is a learning project created for educational purposes.

---

Made with ❤️ using Flutter and Dart


