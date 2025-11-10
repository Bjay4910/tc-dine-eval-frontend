# TCDineEval Team Task Assignments

**Team Members**: Randy, James, Cian, Tracy

## Tech Stack
- **Frontend**: React 19 + TypeScript
- **Build Tool**: Vite
- **Styling**: Tailwind CSS (to be installed)
- **State Management**: React Query + Context API
- **Routing**: React Router v6
- **HTTP Client**: Axios

---

## 🔌 Randy: Backend Integration Lead

### Setup Phase
- [ ] Install dependencies: `npm install @tanstack/react-query axios`
- [ ] Configure API base URL in environment variables
- [ ] Set up axios instance with interceptors
- [ ] Configure React Query client in `src/app/queryClient.ts`

### Core Tasks

#### API Service Layer
- [ ] Complete `src/services/api.ts`
  - Create axios instance with base URL
  - Add request/response interceptors
  - Implement error handling
  - Add retry logic for failed requests

- [ ] Complete `src/services/meals.ts`
  - `useGetCurrentMeal()` - Fetch current meal based on time
  - `useGetMealByType(mealType)` - Fetch specific meal (BREAKFAST, LUNCH, etc.)
  - `useGetMealRating(mealId)` - Get meal's overall rating

- [ ] Complete `src/services/foodItems.ts`
  - `useGetFoodItem(id)` - Fetch single food item details
  - `useGetFoodItemsByMeal(mealType)` - Get all food items for a meal
  - `useGetFoodItemRatings(id)` - Get active and overall ratings

- [ ] Complete `src/services/reviews.ts`
  - `useGetReviewsByFoodItem(foodItemId)` - Fetch reviews for a food item
  - `useCreateReview()` - POST new review mutation
  - `useGetReviewsByDate(date)` - Get reviews by specific date

#### Type Definitions
- [ ] Update `src/types/meal.ts` to match backend API
- [ ] Update `src/types/foodItem.ts` to match backend API
- [ ] Update `src/types/review.ts` to match backend API
- [ ] Create `src/types/api.ts` for API response/error types

#### Backend Coordination
- [ ] Meet with backend team to confirm API endpoints
- [ ] Document API contract in `API_DOCS.md`
- [ ] Test all endpoints with Postman/Insomnia
- [ ] Handle authentication flow (if using userID)

---

## 🎨 James: UI Components Lead

### Setup Phase
- [ ] Install Tailwind CSS: `npm install -D tailwindcss postcss autoprefixer`
- [ ] Run `npx tailwindcss init -p`
- [ ] Configure `tailwind.config.js` with color theme
- [ ] Add Tailwind directives to main CSS file
- [ ] Create global styles in `src/styles/globals.css`

### Core Tasks

#### Design System
- [ ] Define color palette (primary, secondary, accent, neutral)
- [ ] Set up spacing scale (padding, margins)
- [ ] Define typography system (headings, body text)
- [ ] Create shared CSS variables/tokens

#### Core Components
- [ ] Complete `src/components/StarRating.tsx`
  - Display mode (show rating, read-only)
  - Input mode (clickable, for reviews)
  - Support half-stars for averages
  - Add hover effects

- [ ] Complete `src/components/ReviewForm.tsx`
  - Star rating input (1-5 stars)
  - Text area for comment
  - Form validation
  - Submit/cancel buttons
  - Loading state during submission
  - Success/error feedback

- [ ] Create `src/components/MealCard.tsx`
  - Display meal name
  - Show meal rating with stars
  - Show number of food items
  - Click to navigate to meal detail
  - Responsive card layout

- [ ] Create `src/components/FoodItemCard.tsx`
  - Display food item name
  - Show current day rating
  - Show overall average rating
  - Meal type badge
  - Click to navigate to detail page

- [ ] Create `src/components/RatingBadge.tsx`
  - Display rating number + stars
  - Different variants (large, small, compact)
  - Color coding (green for high, yellow for medium, red for low)

- [ ] Create `src/components/ReviewList.tsx`
  - List individual reviews
  - Show user rating, comment, date
  - Handle empty state (no reviews yet)
  - Pagination or infinite scroll

- [ ] Create `src/components/Loading.tsx`
  - Spinner component
  - Skeleton loaders for cards
  - Different sizes/variants

- [ ] Create `src/components/ErrorMessage.tsx`
  - Display error messages
  - Retry button
  - Different severity levels

- [ ] Create `src/components/Layout.tsx`
  - App header with logo/title
  - Navigation (if needed)
  - Main content area
  - Footer
  - Responsive layout

#### Styling
- [ ] Make all components mobile-responsive
- [ ] Add hover/focus states for interactive elements
- [ ] Ensure accessibility (ARIA labels, keyboard navigation)
- [ ] Test on different screen sizes

---

## 📄 Cian: Pages & Navigation Lead

### Setup Phase
- [ ] Install React Router: `npm install react-router-dom`
- [ ] Configure routing in `src/app/router.tsx`
- [ ] Set up route structure and navigation paths
- [ ] Create 404/NotFound page

### Core Tasks

#### Routing Setup
- [ ] Configure `src/app/router.tsx`
  - Route: `/` → HomePage
  - Route: `/meal/:mealType` → MealDetailPage
  - Route: `/food-item/:id` → FoodItemDetailPage
  - Route: `*` → NotFound page
  - Set up BrowserRouter in main.tsx

#### HomePage (`src/pages/HomePage.tsx`)
- [ ] Detect current meal based on time of day (use Randy's time util)
- [ ] Display current meal name and time range
- [ ] Show meal overall rating at the top
- [ ] Fetch and display list of food items in current meal
- [ ] Use James's MealCard or FoodItemCard components
- [ ] Add navigation to meal detail
- [ ] Handle loading state while fetching
- [ ] Handle error state if API fails
- [ ] Add refresh/reload functionality
- [ ] Show "No items in this meal" empty state

#### MealDetailPage (`src/pages/MealDetailPage.tsx`)
- [ ] Get meal type from URL params
- [ ] Fetch meal details and food items
- [ ] Display meal header with name and rating
- [ ] Show grid/list of all food items in the meal
- [ ] Show each food item's active rating
- [ ] Make food items clickable to navigate to detail
- [ ] Add breadcrumb: Home > [Meal Name]
- [ ] Handle loading state
- [ ] Handle error state
- [ ] Add back button to home

#### FoodItemDetailPage (`src/pages/FoodItemDetailPage.tsx`)
- [ ] Get food item ID from URL params
- [ ] Fetch food item details and reviews
- [ ] Display food item name and meal type
- [ ] Show two ratings side-by-side:
  - Today's rating (activeRating)
  - Overall average rating (overallRating)
- [ ] Display list of all reviews for this food item
- [ ] Include ReviewForm at bottom for submitting new review
- [ ] Handle review submission success (refresh reviews)
- [ ] Add breadcrumb: Home > [Meal] > [Food Item]
- [ ] Handle loading/error states
- [ ] Add back button

#### Navigation & UX
- [ ] Implement smooth page transitions
- [ ] Add loading indicators during navigation
- [ ] Handle browser back/forward buttons
- [ ] Test all navigation flows
- [ ] Ensure URLs are shareable

---

## 🔧 Tracy: Integration & Polish Lead

### Setup Phase
- [ ] Create `.env.example` file for environment variables
- [ ] Set up Vitest: `npm install -D vitest @testing-library/react @testing-library/jest-dom`
- [ ] Configure `vitest.config.ts`
- [ ] Create test setup file

### Core Tasks

#### Utilities
- [ ] Complete `src/utils/time.ts`
  - `getCurrentMeal()` - Return current meal based on EST time
  - `getMealTimeRange(mealType)` - Get time range for each meal
  - Define meal time boundaries:
    - BREAKFAST: 7:00 AM - 10:30 AM
    - LUNCH: 11:00 AM - 2:30 PM
    - AFTERNOON_SNACK: 3:00 PM - 5:00 PM
    - DINNER: 5:30 PM - 9:00 PM
  - Handle edge cases (late night, early morning)

- [ ] Create `src/utils/formatting.ts`
  - `formatDate(date)` - Format date for display
  - `formatRating(rating)` - Format rating to 1 decimal place
  - `formatMealType(type)` - Convert enum to display string
  - `getRelativeTime(date)` - "2 hours ago", "yesterday", etc.

- [ ] Create `src/utils/validation.ts`
  - `validateReviewForm(data)` - Validate review submission
  - `validateRating(rating)` - Ensure rating is 1-5
  - `validateComment(comment)` - Check comment length/content

#### State Management
- [ ] Create `src/contexts/UserContext.tsx` (if using userID)
  - Store user ID in context
  - Provide user authentication state
  - Handle anonymous vs logged-in users

- [ ] Create `src/hooks/useLocalStorage.ts`
  - Save user preferences
  - Store user ID if not anonymous

#### Error Handling
- [ ] Create `src/components/ErrorBoundary.tsx`
  - Catch React errors
  - Display friendly error message
  - Log errors for debugging

- [ ] Add global error handling
  - Network errors
  - API errors
  - Validation errors

#### Testing
- [ ] Write unit tests for `src/utils/time.ts`
- [ ] Write unit tests for `src/utils/formatting.ts`
- [ ] Write unit tests for `src/utils/validation.ts`
- [ ] Write component tests for StarRating
- [ ] Write component tests for ReviewForm
- [ ] Write integration tests for HomePage flow
- [ ] Test review submission end-to-end

#### Performance & Polish
- [ ] Implement lazy loading for pages
- [ ] Add code splitting for better performance
- [ ] Optimize images (if any)
- [ ] Add loading skeletons for better UX
- [ ] Test app on different browsers (Chrome, Firefox, Safari)
- [ ] Test app on mobile devices
- [ ] Fix any console warnings/errors
- [ ] Add meta tags for SEO
- [ ] Optimize bundle size

#### Deployment
- [ ] Create build configuration
- [ ] Set up environment variables for production
- [ ] Test production build locally
- [ ] Create deployment documentation
- [ ] Deploy to hosting platform (Vercel/Netlify)

---

## 📅 Suggested Timeline

### Day 1: Setup & Foundation
- **Randy**: Install packages, set up API client, define types
- **James**: Install Tailwind, create design system, start StarRating
- **Cian**: Install React Router, set up routing structure
- **Tracy**: Set up utilities, create time logic

### Day 2: Core Development
- **Randy**: Implement meal and food item services
- **James**: Complete StarRating, ReviewForm, cards
- **Cian**: Build HomePage with current meal detection
- **Tracy**: Complete formatting/validation utils, write tests

### Day 3: Integration Phase 1
- **Randy**: Implement review service, test all APIs
- **James**: Finish all components, ensure responsive design
- **Cian**: Build MealDetailPage
- **Tracy**: Set up error boundary, context providers

### Day 4: Integration Phase 2
- **Randy**: Help Cian integrate API calls into pages
- **James**: Help Cian with component integration and styling
- **Cian**: Build FoodItemDetailPage, integrate ReviewForm
- **Tracy**: Test all user flows, find bugs

### Day 5: Testing & Polish
- **Randy**: Fix API bugs, optimize queries
- **James**: Polish UI, fix styling issues
- **Cian**: Fix navigation bugs, improve UX
- **Tracy**: Write tests, fix bugs, prepare for deployment

### Day 6: Deployment
- **All**: Final testing, bug fixes, deploy to production

---

## 🤝 Coordination Guidelines

### Daily Standups (15 min)
Each person answers:
1. What did you complete?
2. What are you working on today?
3. Any blockers?

### Key Dependencies
- **Cian depends on James**: Need components before building pages
- **Cian depends on Randy**: Need API services for data fetching
- **James & Cian depend on Tracy**: Need time utils for current meal
- **Randy depends on Backend Team**: Need API endpoints and data format

### Communication
- **Randy**: Notify team when API services are ready to use
- **James**: Notify team when components are ready to integrate
- **Cian**: Report any issues with components or API integration
- **Tracy**: Share test results and bug reports daily

### Code Review
- Create pull requests for major features
- At least one team member reviews before merging
- Run tests before pushing to main

---

## 📦 Installation Commands

```bash
# Navigate to project
cd tc-dine-eval-frontend

# Install core dependencies
npm install @tanstack/react-query axios react-router-dom

# Install Tailwind CSS
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

# Install testing libraries
npm install -D vitest @testing-library/react @testing-library/jest-dom

# Run development server
npm run dev
```

---

## 📝 Notes
- Keep the backend team in the loop about data requirements
- Update this document if priorities change
- Check off tasks as you complete them
- Ask for help if blocked for more than 2 hours
- Commit code frequently with clear messages

**Questions?** Discuss in team chat or daily standup!
