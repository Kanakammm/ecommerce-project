# 🎬 Video Script – Kanakavalli (Frontend)
# Sprint 2 – PrivateMesh

---

## 🖥️ SCREEN SETUP BEFORE RECORDING
- Open VSCode with the `Sprint2_PrivateMesh` project
- Have a terminal open inside the `frontend/` folder
- Have the app running in a browser at `http://localhost:5173`
- Font size bumped up so text is readable on screen

---

## PART 1 — Introduction (30 seconds)

**[ Show: VSCode with frontend/src/ folder expanded in sidebar ]**

> "Hi, I'm Kanakavalli, the frontend developer on PrivateMesh.
> In Sprint 2, I built out the complete React interface —
> all the components, the login and registration pages,
> and the full unit test suite.
> I'll show you the components, then run the tests live."

---

## PART 2 — Frontend Structure Overview (1 minute)

**[ Show: VSCode sidebar — expand frontend/src/ ]**

> "The frontend is built with React and Vite,
> using Material UI for components.
> Everything is organized by feature inside the `src/` folder."

**[ Click through the folders as you mention each one ]**

> "`Login/` and `Registration/` handle authentication pages.
> `MainScreen/` is the core of the app —
> it contains the `ServerList` on the left,
> and `ServerAndMembers` on the right which holds
> the `ActiveServer` chat view and the `MenuBar` at the top.
> `CommonComponents/Search/` is our reusable search bar
> that's used in multiple places.
> And `UserBadge/` is the user profile component
> shown at the bottom of the server list."

**[ Click: frontend/src/MainScreen/ServerList/ServerList.jsx ]**

> "The ServerList is one of the most feature-rich components.
> It fetches groups from the backend, renders them as a list,
> supports real-time search filtering, channel selection,
> adding new channels, and profile editing."

**[ Click: frontend/src/MainScreen/ServerAndMembers/ActiveServer/ActiveServer.jsx ]**

> "The ActiveServer component displays the messages for
> whatever channel is selected, and handles sending new messages."

---

## PART 3 — Live App Demo (1.5 minutes)

**[ Switch to browser at http://localhost:5173 ]**

> "Here's the running application.
> This is what a user sees when they open PrivateMesh."

**[ Show the Login page ]**

> "The login page has a username and password field.
> Leaving them empty and clicking Sign In does nothing —
> that validation is working correctly."

**[ Fill in username and password, click Sign In ]**

> "After logging in, we land on the main screen.
> On the left is the server list — these are the groups
> the user is a member of.
> The search bar at the top filters servers in real time."

**[ Type something in the search bar, show filtering ]**

> "Typing here filters the list instantly — no page reload,
> no API call, just live filtering in the component."

**[ Click a server, show channels appear ]**

> "Selecting a server expands its channels below it.
> Clicking a channel loads its messages on the right."

**[ Click a channel, show message area ]**

> "Here's the active server view. Messages are displayed here,
> and at the bottom is the message input."

**[ Type a message and send it ]**

> "Typing a message and hitting Send posts it to the channel."

**[ Click the menu button to toggle member list ]**

> "The menu button in the top bar toggles the member list
> panel on the right side."

---

## PART 4 — Running Frontend Unit Tests (2 minutes)

**[ Switch to VSCode terminal inside frontend/ ]**

> "Now let me run the unit tests.
> These are written using Vitest with React Testing Library."

**[ Run: ]**
```
npm run test
```

**[ As tests start running, narrate each file ]**

> "The test suite covers all 11 components.
> Let me walk through the key ones."

**[ When UserBadge.test results appear ]**

> "UserBadge — renders correctly with and without props,
> shows the default icon when none is provided."

**[ When ServerList.test results appear ]**

> "ServerList — this one has 7 tests.
> It verifies all servers render, search filtering works,
> server selection fires the right callbacks,
> and adding a new channel updates the component correctly."

**[ When Login.test results appear ]**

> "Login — 4 tests covering rendering, empty form blocking,
> valid submission, and the Register button navigation."

**[ When MenuBar.test results appear ]**

> "MenuBar has 12 tests — it's the most thoroughly tested component
> because it handles channel switching, visibility toggling,
> and several edge cases like a server with no channels."

**[ When Registration.test results appear ]**

> "Registration — covers form rendering, validation logic,
> API submission, success and error states."

**[ When final summary appears ]**

> "All tests across all 11 files — passing.
> We aimed for a 1-to-1 ratio of unit tests to functions,
> and you can see that reflected in the coverage here."

---

## PART 5 — Running Cypress Component Tests (1.5 minutes)

**[ Keep terminal inside frontend/ ]**

> "Now let's run the Cypress component tests.
> These mount individual React components in isolation
> inside a real browser environment —
> which is a step up from unit tests because
> they test actual DOM interaction."

**[ Run: ]**
```
npx cypress run --component
```

**[ As ActiveServer.cy.jsx runs ]**

> "ActiveServer component tests —
> no server selected shows a placeholder,
> with a server and channel selected the chat interface appears,
> and sending a message clears the input field. All 3 passing."

**[ As Login.cy.jsx runs ]**

> "Login component tests — the form renders,
> empty fields block submission,
> valid credentials trigger the login callback,
> and the Register button navigates correctly. 5 out of 5 passing."

**[ As ServerList.cy.jsx runs ]**

> "ServerList component tests —
> all servers render on mount,
> the search input filters results correctly,
> clicking a server fires the selection callbacks,
> and adding a channel updates the list. 5 passing, 1 pending —
> the profile editing test is deferred to Sprint 3."

**[ When final summary table appears ]**

> "14 total component tests. 13 passing. 1 pending. Zero failures."

---

## PART 6 — Wrap Up (20 seconds)

**[ Show: frontend/src/test/ folder in VSCode sidebar ]**

> "To summarize — in Sprint 2 I built all the frontend components,
> connected them to the backend API,
> wrote unit tests for every component,
> and wrote Cypress component tests for the three
> most interactive parts of the interface.
> The full list of tests and files is in our Sprint2.md.
> That's the frontend for Sprint 2."

---

## ⏱️ ESTIMATED TOTAL TIME: ~7 minutes
