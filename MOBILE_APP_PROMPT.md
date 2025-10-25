# QuillGlow Mobile App - React Native (Expo) Development Prompt

## Project Overview

Create a comprehensive mobile application for **QuillGlow**, an AI-powered student productivity and study management platform. The app should be built using **React Native with Expo** and provide a seamless, native mobile experience with all the features from the web application, plus mobile-specific enhancements.

---

## App Identity

**Name:** QuillGlow  
**Tagline:** "Illuminate Your Learning Journey"  
**Target Audience:** Students (high school, college, university)  
**Platform:** iOS and Android (via React Native + Expo)

---

## Core Technology Stack

### Framework & Tools
- **React Native** with **Expo** (latest stable version)
- **TypeScript** for type safety
- **Expo Router** for navigation (file-based routing)
- **React Native Reanimated** for smooth animations
- **React Native Gesture Handler** for touch interactions

### Backend & Database
- **Supabase** for:
  - PostgreSQL database
  - Authentication (email/password)
  - Real-time subscriptions
  - Row Level Security (RLS)
  - Storage for images/files

### AI & APIs
- **Google Gemini 2.5 Flash** for AI features:
  - Study plan generation
  - Flashcard generation from text
  - Syllabus analysis
  - AI suggestions for tasks
  - Stress relief coaching
- **Deepgram API** for voice-to-text transcription (Genius plan only)

### Payments
- **Stripe** for subscription management:
  - Scholar Plan (Free)
  - Genius Plan ($4.99/month)

### State Management & Storage
- **Zustand** for global state management
- **AsyncStorage** for local persistence
- **React Query** for server state and caching

### UI Components & Styling
- **NativeWind** (Tailwind CSS for React Native)
- Custom component library matching web design system
- **React Native Paper** or **React Native Elements** for base components
- **Expo Vector Icons** for icons

### Charts & Visualizations
- **Victory Native** or **React Native Chart Kit** for analytics charts

---

## Design System

### Color Palette
\`\`\`typescript
colors: {
  primary: '#3B82F6',      // Blue
  secondary: '#8B5CF6',    // Purple
  accent: '#F59E0B',       // Orange
  success: '#10B981',      // Green
  danger: '#EF4444',       // Red
  warning: '#F59E0B',      // Amber
  background: '#FFFFFF',   // White
  surface: '#F9FAFB',      // Light gray
  text: '#111827',         // Dark gray
  textSecondary: '#6B7280',// Medium gray
  border: '#E5E7EB',       // Light border
}
\`\`\`

### Typography
- **Headings:** Inter Bold (24-32px)
- **Body:** Inter Regular (14-16px)
- **Captions:** Inter Medium (12-14px)

### Design Principles
- Clean, modern, student-friendly interface
- Smooth animations and transitions
- Touch-friendly buttons (minimum 44x44pt)
- Consistent spacing (8px grid system)
- Glassmorphism effects for cards
- Gradient accents for CTAs

---

## Authentication Flow

### Screens
1. **Onboarding/Welcome Screen**
   - App introduction with swipeable slides
   - Features showcase
   - "Get Started" and "Sign In" buttons

2. **Sign Up Screen**
   - Email and password fields
   - Password strength indicator
   - Terms acceptance checkbox
   - "Create Account" button
   - "Already have an account? Sign In" link

3. **Sign In Screen**
   - Email and password fields
   - "Remember me" toggle
   - "Forgot Password?" link
   - "Sign In" button
   - "Don't have an account? Sign Up" link

4. **Email Verification Screen**
   - Message to check email
   - Resend verification email button
   - Auto-redirect after verification

5. **Forgot Password Screen**
   - Email input
   - "Send Reset Link" button
   - Back to sign in link

### Authentication Features
- Supabase Auth integration
- Biometric authentication (Face ID/Touch ID) after first login
- Secure token storage
- Auto-login on app launch
- Session management

---

## Main App Structure

### Bottom Tab Navigation (5 tabs)
1. **Dashboard** (Home icon)
2. **Planner** (Calendar icon)
3. **Flashcards** (Brain icon)
4. **Notes** (Document icon)
5. **Profile** (User icon)

### Additional Screens (Stack Navigation)
- Analytics
- Stress Relief
- Leaderboard
- Quests
- Settings
- Upgrade/Pricing
- Blog
- Individual Blog Post
- Contact Support

---

## Feature Specifications

### 1. Dashboard Screen

**Layout:**
- Header with greeting, streak counter, and notification bell
- Motivational quote card (changes daily)
- Study streak visualization (calendar heatmap)
- Today's tasks section (max 5 tasks shown)
- Quick actions: "Add Task", "Start Timer", "Take Break"
- Recent activity feed
- Study stats summary (hours today, tasks completed)

**Features:**
- Pull-to-refresh
- Animated streak counter
- Swipe tasks to mark complete
- Tap quote to share
- Real-time task updates

**API Endpoints:**
- `GET /api/profile` - User profile and streak
- `GET /api/tasks/today` - Today's tasks
- `GET /api/analytics/summary` - Study stats

---

### 2. Study Planner Screen

**Views:**
- **Calendar View** (default)
  - Month/week/day views
  - Color-coded tasks by subject
  - Tap date to see tasks
  - Long-press to add task
  
- **List View**
  - Grouped by date
  - Swipe to complete/delete
  - Drag to reorder

- **Pomodoro Timer View**
  - Large circular timer
  - Start/pause/reset controls
  - Session counter
  - Break timer
  - Focus mode (blocks notifications)

**Features:**
- Add/edit/delete tasks
- Set due dates and times
- Add subjects/tags
- Set priority levels
- Recurring tasks
- Task reminders (push notifications)
- AI-powered task suggestions
- AI study plan generator:
  - Input: Subject, exam date, current knowledge level
  - Output: Day-by-day study plan with goals
- Pomodoro timer with customizable intervals
- Study session tracking

**Components:**
- Calendar component with gesture support
- Task card with swipe actions
- Circular timer with animations
- AI suggestion modal
- Study plan generator modal

**API Endpoints:**
- `GET /api/tasks` - All tasks
- `POST /api/tasks` - Create task
- `PUT /api/tasks/:id` - Update task
- `DELETE /api/tasks/:id` - Delete task
- `POST /api/ai/generate-study-plan` - Generate AI study plan
- `POST /api/ai/suggest-tasks` - Get AI task suggestions

---

### 3. Flashcards Screen

**Views:**
- **Deck List View**
  - Grid of flashcard decks
  - Deck name, card count, last studied
  - Progress indicator
  - Search and filter

- **Study View**
  - Card flip animation
  - Swipe right (know it) / left (review)
  - Progress bar
  - Card counter (e.g., "5/20")
  - Difficulty rating (Easy/Medium/Hard)

- **Quiz Mode**
  - Multiple choice questions
  - True/False
  - Score tracking
  - Results summary

**Features:**
- Create/edit/delete decks
- Add/edit/delete cards
- AI flashcard generation from text:
  - Paste notes or upload image
  - AI generates Q&A pairs
  - Review and edit before saving
- Spaced repetition algorithm (SM-2)
- Study statistics per deck
- Export/import decks
- Share decks with friends
- Offline mode support

**Components:**
- Animated flip card
- Swipeable card stack
- Deck card with stats
- AI generation modal
- Quiz interface

**API Endpoints:**
- `GET /api/flashcards/decks` - All decks
- `GET /api/flashcards/deck/:id` - Deck with cards
- `POST /api/flashcards/deck` - Create deck
- `POST /api/flashcards/card` - Create card
- `POST /api/ai/generate-flashcards` - AI generation
- `PUT /api/flashcards/card/:id/review` - Update review data

---

### 4. Notes Screen

**Views:**
- **Notes List View**
  - Grid or list layout toggle
  - Search bar
  - Filter by tags
  - Sort by date/title
  - Pinned notes at top

- **Note Editor View**
  - Rich text editor with toolbar:
    - Bold, italic, underline
    - Headings (H1, H2, H3)
    - Bullet/numbered lists
    - Checkboxes
    - Code blocks
    - Links
  - Voice-to-text button (Genius plan only)
  - Auto-save indicator
  - Word count
  - Last edited timestamp

**Features:**
- Create/edit/delete notes
- Rich text formatting
- Add tags
- Pin important notes
- Search within notes
- Voice-to-text transcription (Genius plan):
  - Real-time transcription
  - Punctuation and formatting
  - Append to existing note
- Export notes (PDF, TXT, Markdown)
- Share notes
- Offline editing with sync
- Attach images

**Components:**
- Rich text editor component
- Voice recording modal
- Tag selector
- Export options modal

**API Endpoints:**
- `GET /api/notes` - All notes
- `GET /api/notes/:id` - Single note
- `POST /api/notes` - Create note
- `PUT /api/notes/:id` - Update note
- `DELETE /api/notes/:id` - Delete note
- `POST /api/transcribe-voice` - Voice transcription (Genius only)

---

### 5. Analytics Screen

**Sections:**
- **Study Time Overview**
  - Total hours this week/month
  - Daily average
  - Line chart showing trend
  - Comparison to previous period

- **Subject Breakdown**
  - Pie chart of time per subject
  - List with percentages
  - Most/least studied subjects

- **Task Completion**
  - Completion rate percentage
  - Bar chart by day
  - Streak visualization

- **GPA Estimator**
  - Input grades and credits
  - Calculate GPA
  - Track over time

- **Mood Tracking**
  - Daily mood selector (5 emojis)
  - Mood trend chart
  - Correlation with study hours

- **Burnout Risk Indicator**
  - Based on study hours and mood
  - Warning if at risk
  - Suggestions to prevent burnout

**Features:**
- Interactive charts (tap for details)
- Date range selector
- Export analytics report
- Goal setting and tracking
- Insights and recommendations

**Components:**
- Chart components (line, bar, pie)
- Stat cards
- Mood selector
- GPA calculator

**API Endpoints:**
- `GET /api/analytics/study-time` - Study time data
- `GET /api/analytics/subjects` - Subject breakdown
- `GET /api/analytics/tasks` - Task completion data
- `GET /api/analytics/mood` - Mood tracking data
- `POST /api/analytics/mood` - Log mood
- `GET /api/analytics/gpa` - GPA data
- `POST /api/analytics/gpa` - Update GPA

---

### 6. Stress Relief Screen

**Layout:**
- Background selector at top (5 calming backgrounds):
  - Ocean waves
  - Forest path
  - Sunset sky
  - Mountain landscape
  - Lavender field
- AI stress relief coach chat interface
- Breathing exercise overlay
- Timer for break duration

**Features:**
- **Changeable Backgrounds:**
  - Swipeable carousel
  - Full-screen immersive backgrounds
  - Smooth transitions

- **AI Stress Relief Coach:**
  - Chat interface
  - Empathetic responses
  - Journaling prompts
  - Stress management tips
  - Mindfulness exercises
  - Powered by Gemini 2.5 Flash

- **Breathing Exercises:**
  - Animated circle (inhale/exhale)
  - Guided breathing patterns:
    - 4-7-8 technique
    - Box breathing
    - Deep breathing
  - Haptic feedback
  - Calming sounds (optional)

- **Break Timer:**
  - Set duration (5, 10, 15, 20 minutes)
  - Countdown with progress ring
  - Notification when time's up
  - Pause/resume/stop controls

**Components:**
- Background carousel
- Chat interface
- Breathing animation
- Circular timer

**API Endpoints:**
- `POST /api/stress-relief-chat` - AI coach responses

---

### 7. Profile Screen

**Sections:**
- **Profile Header**
  - Avatar (editable)
  - Name and email
  - Study streak
  - Level and XP bar
  - Edit profile button

- **Subscription Status**
  - Current plan (Scholar/Genius)
  - Usage stats (tasks, AI generations, etc.)
  - Upgrade button (if Scholar)
  - Manage subscription (if Genius)

- **Achievements**
  - Grid of earned badges
  - Progress on locked achievements
  - Tap to see details

- **Settings**
  - Notifications
  - Theme (Light/Dark/Auto)
  - Language
  - Study reminders
  - Pomodoro settings
  - Data & Privacy
  - Help & Support
  - About
  - Sign Out

**Features:**
- Edit profile (name, avatar)
- View achievement details
- Manage subscription
- Configure app settings
- Dark mode toggle
- Push notification preferences
- Biometric authentication toggle
- Clear cache
- Export data
- Delete account

**Components:**
- Avatar picker
- Achievement card
- Settings list
- Subscription card

**API Endpoints:**
- `GET /api/profile` - User profile
- `PUT /api/profile/update` - Update profile
- `GET /api/achievements` - User achievements
- `GET /api/subscription/status` - Subscription info

---

### 8. Leaderboard Screen

**Layout:**
- Top 3 podium display
- Scrollable list of rankings
- User's rank highlighted
- Filter by timeframe (week/month/all-time)

**Features:**
- Rankings based on XP
- User avatars and levels
- Study hours displayed
- Tap user to view profile (if public)
- Pull-to-refresh

**API Endpoints:**
- `GET /api/leaderboard` - Leaderboard data

---

### 9. Quests Screen

**Layout:**
- Available quests list
- Active quests section
- Completed quests history
- Quest details modal

**Features:**
- Daily/weekly/special quests
- XP and rewards display
- Progress tracking
- Auto-generated quests based on study patterns
- Complete quest button
- Quest notifications

**Components:**
- Quest card
- Progress bar
- Reward badge

**API Endpoints:**
- `GET /api/quests/list` - All quests
- `POST /api/quests/start` - Start quest
- `POST /api/quests/submit` - Complete quest
- `POST /api/quests/generate` - Generate new quests

---

### 10. Upgrade/Pricing Screen

**Layout:**
- Plan comparison cards:
  - Scholar (Free)
  - Genius ($4.99/month)
- Feature comparison list
- Current usage stats
- Upgrade button

**Features:**
- Stripe checkout integration
- Plan feature comparison
- Usage limit indicators
- Secure payment processing
- Subscription management

**API Endpoints:**
- `POST /api/subscription/create-checkout` - Create Stripe session
- `POST /api/subscription/verify-payment` - Verify payment

---

### 11. Blog Screen

**Layout:**
- List of blog posts
- Cover images
- Title, excerpt, date
- Read time estimate
- View count

**Features:**
- Load posts from database
- Search and filter
- Tap to read full article
- Share article
- Bookmark articles

**API Endpoints:**
- `GET /api/blog` - All blog posts
- `GET /api/blog/:slug` - Single post

---

### 12. Settings Screen

**Categories:**
- **Account**
  - Edit profile
  - Change password
  - Email preferences
  - Delete account

- **Notifications**
  - Push notifications toggle
  - Task reminders
  - Study reminders
  - Achievement notifications
  - Quiet hours

- **Appearance**
  - Theme (Light/Dark/Auto)
  - Font size
  - Color scheme

- **Study Preferences**
  - Default Pomodoro duration
  - Break duration
  - Auto-start breaks
  - Focus mode settings

- **Privacy & Security**
  - Biometric authentication
  - Data export
  - Privacy policy
  - Terms of service

- **Support**
  - Help center
  - Contact support
  - Report a bug
  - Feature request

- **About**
  - App version
  - Credits
  - Open source licenses

---

## Mobile-Specific Features

### Push Notifications
- Task reminders
- Study session reminders
- Pomodoro timer alerts
- Achievement unlocked
- Streak reminders
- Quest completion
- Daily motivational quotes

### Offline Mode
- Cache notes for offline editing
- Queue actions when offline
- Sync when back online
- Offline indicator

### Widgets (iOS/Android)
- Today's tasks widget
- Study streak widget
- Pomodoro timer widget
- Quick add task widget

### Haptic Feedback
- Task completion
- Timer start/stop
- Button presses
- Swipe actions
- Breathing exercises

### Biometric Authentication
- Face ID / Touch ID
- Secure app access
- Quick login

### Share Extensions
- Share text to create flashcards
- Share images to notes
- Share links to save

### Background Tasks
- Sync data periodically
- Update widgets
- Process notifications

---

## Database Schema

### Tables (Supabase PostgreSQL)

1. **profiles**
   - id (uuid, primary key)
   - user_id (uuid, foreign key to auth.users)
   - full_name (text)
   - avatar_url (text)
   - study_streak (integer)
   - last_study_date (date)
   - xp (integer)
   - level (integer)
   - created_at (timestamp)
   - updated_at (timestamp)

2. **tasks**
   - id (uuid, primary key)
   - user_id (uuid, foreign key)
   - title (text)
   - description (text)
   - due_date (timestamp)
   - completed (boolean)
   - priority (text: low/medium/high)
   - subject (text)
   - tags (text[])
   - created_at (timestamp)
   - updated_at (timestamp)

3. **flashcard_decks**
   - id (uuid, primary key)
   - user_id (uuid, foreign key)
   - name (text)
   - description (text)
   - card_count (integer)
   - last_studied (timestamp)
   - created_at (timestamp)
   - updated_at (timestamp)

4. **flashcards**
   - id (uuid, primary key)
   - deck_id (uuid, foreign key)
   - question (text)
   - answer (text)
   - difficulty (integer)
   - next_review (timestamp)
   - review_count (integer)
   - created_at (timestamp)
   - updated_at (timestamp)

5. **notes**
   - id (uuid, primary key)
   - user_id (uuid, foreign key)
   - title (text)
   - content (text)
   - tags (text[])
   - pinned (boolean)
   - created_at (timestamp)
   - updated_at (timestamp)

6. **study_sessions**
   - id (uuid, primary key)
   - user_id (uuid, foreign key)
   - subject (text)
   - duration (integer, minutes)
   - date (date)
   - mood (text)
   - created_at (timestamp)

7. **subscriptions**
   - id (uuid, primary key)
   - user_id (uuid, foreign key)
   - plan_type (text: scholar/genius)
   - stripe_customer_id (text)
   - stripe_subscription_id (text)
   - status (text: active/canceled/past_due)
   - current_period_end (timestamp)
   - created_at (timestamp)
   - updated_at (timestamp)

8. **achievements**
   - id (uuid, primary key)
   - user_id (uuid, foreign key)
   - achievement_type (text)
   - unlocked_at (timestamp)
   - created_at (timestamp)

9. **quests**
   - id (uuid, primary key)
   - user_id (uuid, foreign key)
   - title (text)
   - description (text)
   - xp_reward (integer)
   - status (text: available/active/completed)
   - progress (integer)
   - target (integer)
   - expires_at (timestamp)
   - created_at (timestamp)

10. **blog_posts**
    - id (uuid, primary key)
    - title (text)
    - slug (text, unique)
    - excerpt (text)
    - content (text, markdown)
    - cover_image (text)
    - author (text)
    - published_at (timestamp)
    - view_count (integer)
    - created_at (timestamp)

11. **study_plans**
    - id (uuid, primary key)
    - user_id (uuid, foreign key)
    - title (text)
    - subject (text)
    - exam_date (date)
    - goals (jsonb)
    - created_at (timestamp)

---

## API Integration

### Supabase Setup
- Authentication with email/password
- Row Level Security (RLS) policies
- Real-time subscriptions for live updates
- Storage for avatars and images

### Gemini AI Integration
- Use `@google/generative-ai` package
- API key from environment variables
- Endpoints:
  - Study plan generation
  - Flashcard generation
  - Task suggestions
  - Stress relief coaching
  - Syllabus analysis

### Deepgram Integration (Genius Plan Only)
- Real-time voice transcription
- Use Deepgram REST API
- Chunked audio processing
- Append transcribed text to notes

### Stripe Integration
- Stripe SDK for React Native
- Checkout flow for subscriptions
- Subscription management
- Payment verification

---

## State Management

### Zustand Stores

1. **authStore**
   - user
   - session
   - isAuthenticated
   - login()
   - logout()
   - updateProfile()

2. **taskStore**
   - tasks
   - addTask()
   - updateTask()
   - deleteTask()
   - toggleComplete()

3. **flashcardStore**
   - decks
   - currentDeck
   - addDeck()
   - updateDeck()
   - deleteDeck()
   - addCard()
   - updateCard()

4. **noteStore**
   - notes
   - currentNote
   - addNote()
   - updateNote()
   - deleteNote()

5. **settingsStore**
   - theme
   - notifications
   - pomodoroSettings
   - updateSettings()

---

## Performance Optimization

- Lazy loading for screens
- Image optimization and caching
- Virtualized lists for long content
- Debounced search inputs
- Optimistic UI updates
- Background data sync
- Efficient re-renders with React.memo
- Code splitting

---

## Testing Requirements

- Unit tests for utilities and helpers
- Component tests with React Native Testing Library
- Integration tests for API calls
- E2E tests with Detox
- Test coverage > 80%

---

## Security Requirements

- Secure token storage (Expo SecureStore)
- HTTPS only for API calls
- Input validation and sanitization
- SQL injection prevention (Supabase handles this)
- XSS prevention
- Rate limiting on API endpoints
- Biometric authentication
- Encrypted local storage for sensitive data

---

## Accessibility

- Screen reader support
- Sufficient color contrast (WCAG AA)
- Touch target sizes (minimum 44x44pt)
- Keyboard navigation support
- Alternative text for images
- Semantic HTML/components
- Focus indicators

---

## Analytics & Monitoring

- Expo Analytics for usage tracking
- Sentry for error tracking
- Performance monitoring
- User behavior analytics
- Crash reporting

---

## Deployment

### iOS
- Apple Developer account
- App Store Connect setup
- TestFlight for beta testing
- App Store submission

### Android
- Google Play Console account
- Internal testing track
- Beta testing
- Production release

### Over-the-Air Updates
- Expo Updates for instant updates
- Staged rollouts
- Rollback capability

---

## Environment Variables

\`\`\`env
# Supabase
EXPO_PUBLIC_SUPABASE_URL=your_supabase_url
EXPO_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key

# Gemini AI
GEMINI_API_KEY=your_gemini_api_key

# Deepgram
DEEPGRAM_API_KEY=your_deepgram_api_key

# Stripe
STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_GENIUS_PRICE_ID=your_price_id

# App Config
EXPO_PUBLIC_API_URL=your_api_url
EXPO_PUBLIC_APP_ENV=development
\`\`\`

---

## Additional Requirements

### Animations
- Smooth screen transitions
- Card flip animations for flashcards
- Progress bar animations
- Skeleton loaders
- Pull-to-refresh animations
- Swipe gesture animations
- Breathing exercise animations

### Error Handling
- User-friendly error messages
- Retry mechanisms
- Offline error handling
- Network error handling
- Form validation errors
- Toast notifications for errors

### Loading States
- Skeleton screens
- Shimmer effects
- Progress indicators
- Pull-to-refresh
- Infinite scroll loading

### Empty States
- Friendly illustrations
- Helpful messages
- Call-to-action buttons
- Onboarding hints

---

## Success Metrics

- App Store rating > 4.5 stars
- Daily active users (DAU)
- User retention rate
- Average session duration
- Task completion rate
- Subscription conversion rate
- Crash-free rate > 99.5%

---

## Future Enhancements (Phase 2)

- Social features (study groups, friends)
- Calendar integration (Google Calendar, Apple Calendar)
- File attachments in notes
- Voice notes
- Collaborative flashcard decks
- Study room finder (nearby libraries)
- Study buddy matching
- Gamification leaderboards
- Custom themes
- Apple Watch / Wear OS app
- iPad optimization
- Desktop sync

---

## Development Timeline Estimate

- **Week 1-2:** Project setup, authentication, navigation
- **Week 3-4:** Dashboard, profile, settings
- **Week 5-6:** Study planner, tasks, Pomodoro timer
- **Week 7-8:** Flashcards, spaced repetition
- **Week 9-10:** Notes, rich text editor
- **Week 11-12:** Analytics, charts, mood tracking
- **Week 13-14:** Stress relief, AI coach, breathing exercises
- **Week 15-16:** Leaderboard, quests, achievements
- **Week 17-18:** Subscription, Stripe integration
- **Week 19-20:** Blog, contact, legal pages
- **Week 21-22:** Polish, animations, testing
- **Week 23-24:** Beta testing, bug fixes, deployment

---

## Deliverables

1. Fully functional React Native (Expo) mobile app
2. iOS and Android builds
3. Source code with TypeScript
4. API integration with Supabase
5. Stripe payment integration
6. AI features with Gemini
7. Voice transcription with Deepgram (Genius plan)
8. Push notifications
9. Offline mode support
10. Comprehensive documentation
11. Unit and integration tests
12. App Store and Play Store listings
13. Privacy policy and terms of service
14. User guide and help documentation

---

## Notes for Developer

- Follow React Native best practices
- Use TypeScript for all code
- Implement proper error boundaries
- Use React Query for data fetching
- Implement proper loading and error states
- Follow Expo's recommended patterns
- Use NativeWind for styling consistency
- Implement proper navigation patterns
- Use Expo's built-in APIs when possible
- Optimize for both iOS and Android
- Test on real devices, not just simulators
- Implement proper security measures
- Follow accessibility guidelines
- Use semantic versioning
- Write clean, maintainable code
- Document complex logic
- Use meaningful variable names
- Keep components small and focused
- Implement proper state management
- Use proper TypeScript types
- Handle edge cases gracefully

---

## Contact & Support

For questions or clarifications during development, refer to:
- Web app repository for reference implementation
- Supabase documentation
- Expo documentation
- React Native documentation
- Stripe mobile SDK documentation

---

**End of Prompt**

This comprehensive prompt should provide all the necessary information to build a fully-featured QuillGlow mobile app with React Native and Expo. The app will match the web version's functionality while providing an optimized mobile experience with native features like push notifications, offline mode, and biometric authentication.
