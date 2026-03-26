# 🎬 Video Script – Anish (Backend + E2E Testing)
# Sprint 2 – PrivateMesh

---

## 🖥️ SCREEN SETUP BEFORE RECORDING
- Open VSCode with the `Sprint2_PrivateMesh` project
- Have a terminal open at the project root
- Have a second terminal open inside the `frontend/` folder
- Font size bumped up so text is readable on screen

---

## PART 1 — Introduction (30 seconds)

**[ Show: VSCode with project folder open in sidebar ]**

> "Hi, I'm Anish, the backend developer on PrivateMesh.
> In Sprint 2, my focus was on building out the complete backend API,
> writing all the backend unit tests, and handling the Cypress end-to-end
> tests that validate the full integrated application flow.
> Let me walk you through everything."

---

## PART 2 — Project Structure Overview (45 seconds)

**[ Show: VSCode sidebar — expand the folder tree ]**
**[ Click through: internal/, tests/, models/ ]**

> "Here's the project structure.
> The entire backend lives inside the `internal/` folder.
> We have `api/v1/` which contains the actual route handlers —
> `sector.go` for all the CRUD operations,
> `auth.go` for the login and challenge endpoints,
> and `sector.gen.go` which is auto-generated from our OpenAPI schema."

**[ Click: internal/api/v1/sector.go ]**

> "Inside `sector.go` you can see handlers for accounts, groups,
> channels, and messages — all the core resources of the application."

**[ Click: internal/auth/jwt.go ]**

> "JWT authentication is handled here — token generation and validation.
> And over in `internal/middleware/auth.go`, every protected route
> goes through a JWT check before the handler is ever called."

**[ Click: models/v1/schema.yaml ]**

> "The entire API is defined in this OpenAPI schema file.
> This is the single source of truth — the Go server code
> and the frontend TypeScript types are both generated from this file
> using the `generate.sh` script."

---

## PART 3 — Running the Backend Unit Tests (2 minutes)

**[ Show: Terminal at project root ]**

> "Let's run the backend unit tests now."

**[ Type and run: ]**
```
go test -p 1 -v ./...
```

**[ Wait for output to start scrolling ]**

> "The `-p 1` flag runs tests sequentially — this is required
> because OrbitDB, our peer-to-peer database, can't handle
> parallel connections during testing."

**[ As TestAuthenticationStandalone appears ]**

> "The first test suite covers authentication in isolation —
> the full challenge-response flow, JWT token persistence,
> and rejection of invalid signatures."

**[ As TestSectorV1 starts running ]**

> "The main test suite is `TestSectorV1`. It spins up a mock IPFS node
> and an in-memory OrbitDB instance so tests run without
> needing a live IPFS daemon."

**[ As Account tests run ]**

> "Account management — creating, updating, deleting, retrieving,
> and searching accounts. All passing."

**[ As Group tests run ]**

> "Group management — including adding and removing members,
> and searching groups by name, ID, creation time, and membership."

**[ As Channel tests run ]**

> "Channel management — creating channels inside groups,
> updating, deleting with cascade, and searching."

**[ As Message tests run ]**

> "Message management — the most granular resource.
> Search covers body content, author, channel, pinned status,
> and creation time."

**[ As Authentication middleware tests run ]**

> "And finally, the authentication middleware tests —
> confirming that unauthenticated requests are rejected
> and that the full login flow works end to end."

**[ When PASS line appears at the bottom ]**

> "42 tests. Zero failures. 2.258 seconds.
> Every single API function has a corresponding unit test."

---

## PART 4 — Swagger API Documentation (45 seconds)

**[ Show: internal/api/v1/swagger-ui.html in VSCode ]**

> "The API is fully documented using Swagger UI.
> When the server is running, you can visit
> localhost:3000/v1/swagger-ui/ to browse every endpoint interactively."

**[ Click: models/v1/schema.yaml — scroll through it briefly ]**

> "The schema covers authentication, accounts, groups, channels,
> and messages — with full request bodies, response shapes,
> and JWT authorization requirements documented for each endpoint.
> All of this documentation is also saved in our Sprint2.md file."

---

## PART 5 — Cypress E2E Tests (2 minutes)

**[ Show: frontend/cypress/e2e/ folder in VSCode sidebar ]**

> "Beyond the backend, I also wrote the Cypress end-to-end tests.
> These are different from component tests — E2E tests
> launch the actual running application and simulate
> a real user clicking through the interface."

**[ Click: frontend/cypress/e2e/app-flow.cy.js ]**

> "The app flow test covers the core user journey —
> selecting a server, picking a channel, sending a message,
> adding a new channel, toggling the member sidebar,
> and searching for servers."

**[ Click: frontend/cypress/e2e/login-flow.cy.js ]**

> "The login flow test verifies the login page renders correctly,
> blocks empty submissions, and successfully logs in
> and transitions to the main screen."

**[ Click: frontend/cypress/e2e/registration.cy.js ]**

> "The registration test checks the registration form renders
> and that navigation back to login works."

**[ Switch to terminal inside frontend/ folder ]**

> "Let me run these now. The frontend dev server needs to be running first."

**[ Terminal 1 — run: ]**
```
npm run dev
```

**[ Wait for: 'Local: http://localhost:5173/' ]**

> "Server is up on port 5173."

**[ Open Terminal 2 inside frontend/ — run: ]**
```
npx cypress run --e2e
```

**[ As app-flow.cy.js runs ]**

> "App flow — 6 tests, all passing."

**[ As login-flow.cy.js runs ]**

> "Login flow — 4 tests, all passing."

**[ As registration.cy.js runs ]**

> "Registration — 3 passing, 2 pending.
> The 2 pending tests require a live backend connection
> to validate form errors, so those are deferred to Sprint 3
> once full authentication is wired up end to end."

**[ When final summary table appears ]**

> "15 total E2E tests. 13 passing. 2 pending. Zero failures."

---

## PART 6 — Wrap Up (20 seconds)

**[ Show: Sprint2.md open in VSCode ]**

> "Everything I've shown — the 42 backend tests,
> the 13 E2E tests, and the full API documentation —
> is captured in our Sprint2.md submission file.
> That's my contribution to Sprint 2. Passing it over to Kanakavalli
> for the frontend walkthrough."

---

## ⏱️ ESTIMATED TOTAL TIME: ~6 minutes
