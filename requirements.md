# Requirements Document

## Introduction

A static single-page web application serving as a daily household safety checklist, themed around Women's Day awareness. The app presents five safety tasks the user should complete before leaving home, allows the user to check off each task, and provides feedback when the "Done for Today" button is clicked. The entire application is delivered as a single HTML file with embedded CSS and JavaScript.

## Glossary

- **App**: The Women's Day Safety Reminder static web application.
- **Checklist**: The set of five safety task items displayed as checkboxes.
- **Task**: An individual safety action item (e.g., "Turn off LPG gas").
- **Done_Button**: The button labeled "Done for Today".
- **Alert**: The browser-native alert dialog shown after the Done_Button is clicked.
- **User**: The person interacting with the App in a web browser.

---

## Requirements

### Requirement 1: Single-File Delivery

**User Story:** As a developer, I want the entire application in one HTML file, so that it can be deployed and shared without a build step or server.

#### Acceptance Criteria

1. THE App SHALL be delivered as a single HTML file named `index.html`.
2. THE App SHALL include all CSS inside a `<style>` tag within the HTML file.
3. THE App SHALL include all JavaScript inside a `<script>` tag within the HTML file.
4. THE App SHALL require no external dependencies, frameworks, or network requests to function.

---

### Requirement 2: Women's Day Theme and Layout

**User Story:** As a user, I want a visually appealing Women's Day-themed interface, so that the app feels welcoming and relevant to the occasion.

#### Acceptance Criteria

1. THE App SHALL apply a color palette consisting of soft pink, purple, and white tones throughout the UI.
2. THE App SHALL center all content horizontally and vertically on the page.
3. THE App SHALL display the main content inside a card-style container with rounded corners and a visible box shadow.
4. THE App SHALL use a legible font size of at least 16px for body text.

---

### Requirement 3: Header Section

**User Story:** As a user, I want a clear header, so that I immediately understand the purpose of the app.

#### Acceptance Criteria

1. THE App SHALL display the title "Women's Safety Reminder" as the primary heading.
2. THE App SHALL display the subtitle "Don't forget these before leaving home ❤️" directly below the title.
3. THE App SHALL visually distinguish the title from the subtitle using font size or weight.

---

### Requirement 4: Safety Checklist

**User Story:** As a user, I want to see all safety tasks as checkboxes, so that I can mark each one as completed before leaving home.

#### Acceptance Criteria

1. THE App SHALL display exactly five checklist tasks: "Turn off LPG gas", "Switch off motor", "Lock the door", "Turn off lights", and "Turn off fan".
2. THE App SHALL render each task as a checkbox input paired with a visible label.
3. THE App SHALL apply consistent spacing between each checklist item for readability.
4. THE App SHALL render all checkboxes in an unchecked state on initial page load.
5. WHEN a User clicks a checklist item label or checkbox, THE App SHALL toggle the checked state of that item.

---

### Requirement 5: Done for Today Button

**User Story:** As a user, I want a prominent button to submit my checklist, so that I receive feedback on my completion status.

#### Acceptance Criteria

1. THE App SHALL display a button labeled "Done for Today".
2. WHEN a User hovers over the Done_Button, THE App SHALL apply a visible style change such as a background color shift or scale animation.
3. THE App SHALL position the Done_Button below the Checklist.

---

### Requirement 6: Completion Feedback

**User Story:** As a user, I want an alert message after clicking the button, so that I know whether I completed all tasks or missed some.

#### Acceptance Criteria

1. WHEN the Done_Button is clicked and all five tasks are checked, THE App SHALL display an Alert with the message "Great job! All tasks completed 🎉".
2. WHEN the Done_Button is clicked and one or more tasks are unchecked, THE App SHALL display an Alert with the message "You missed X tasks! Please check again ⚠️", where X is the exact count of unchecked tasks.
3. THE App SHALL calculate X as the total number of tasks (5) minus the number of checked checkboxes at the time the Done_Button is clicked.

---

### Requirement 7: Footer

**User Story:** As a user, I want a footer with a Women's Day message, so that the app feels complete and celebratory.

#### Acceptance Criteria

1. THE App SHALL display a footer containing the text "Happy Women's Day 💐".
2. THE App SHALL position the footer below the Done_Button within the card or at the bottom of the page.

---

### Requirement 8: Mobile Responsiveness

**User Story:** As a user on a mobile device, I want the app to display correctly on small screens, so that I can use it on my phone.

#### Acceptance Criteria

1. THE App SHALL use CSS flexbox or equivalent centering techniques to adapt the layout to varying viewport widths.
2. THE App SHALL constrain the card container to a maximum width (e.g., 480px) so it does not stretch excessively on wide screens.
3. WHEN the viewport width is 480px or less, THE App SHALL ensure the card fills the available width with appropriate padding so no content is clipped.
