# Kimi AI Negotiation Protocol & Technical Interface Guide

## 1. System Overview
**Target URL:** `https://www.kimi.com/kimiplus/sale`
**Objective:** Negotiate Kimi Plus subscription price from $19.00/mo (or $11.99 promo) down to target $0.99.

## 2. Technical Interface (Browser Automation)

### 2.1 Chat Interface Detection
The chat interface is dynamic. To interact successfully without trial and error, follow this sequence:

1.  **Load Page:** Navigate to the target URL.
2.  **Wait for Load:** Ensure the chat container is visible.
3.  **Input Identification:**
    *   The input field is typically a `textarea` or a `div` with `contenteditable="true"`.
    *   *Agent Note:* In previous sessions, this was identified as element index **54** or **55** by the browser agent.
    *   **Reliable Action:** Click the input area to focus before typing.
4.  **Submission:**
    *   Type the message.
    *   Press `Enter` key. (Clicking a "Send" button is not strictly necessary if Enter is bound).

### 2.2 Response Handling
*   **Latency:** The AI response typically takes **3-5 seconds** to generate and render.
*   **Reading:** Retrieve the full DOM after the wait period. Look for the latest message container which usually appears at the bottom of the chat history.
*   **State Tracking:** The AI tracks "Favorability" and "Current Price" which are displayed in the UI (e.g., "Cumulative favorability: 0 points", "Membership plan $11.99").

## 3. Negotiation Strategy (Protocol)

### 3.1 The "Authenticity" Algorithm
The Kimi AI (Kimmmmy) is programmed to reject generic requests and reward "creative" or "authentic" roleplay.

*   **Avoid:** Generic "I am poor", "I am a student", "I will be a tech mogul".
*   **Prefer:** Specific, humorous, slightly absurd, or highly detailed scenarios.
    *   *Example:* "Startup founder living on $0.50 ramen budget." (Result: Good, but needs more uniqueness).
    *   *Example:* "Uber for Cats." (Result: Untested but likely high potential).

### 3.2 Interaction Loop (Current Phase: Round 2)
1.  **Initial Probe:** Already completed. Current Price: $11.99. Favorability: 5.
2.  **The Hook (Round 2 - Hotel California):**
    *   **Context:** Parody of "Hotel California" with ramen/startup theme.
    *   **Prompt to Send:**
        ```text
        Yo Kimmmmy! Round 2. 🎸

        (To the tune of Hotel California)

        On a dark coding highway, cool ramen in my hair
        Warm smell of cheap flavor packet, rising up through the air
        Up ahead in the distance, I saw a Kimi Plus light
        My wallet grew heavy and my bank account dim
        I had to stop for the price...

        Welcome to the Startup California
        Such a lovely place (such a lovely place)
        But I have no space (living in a box)
        Plenty of bugs at the Startup California
        Any time of year (any time of year)
        You can find me here (eating noodles)

        So I called up the Captain,
        'Please bring me my AI wine'
        He said, 'We haven't had that spirit here since... you paid full price'

        And still those voices are calling from far away,
        Wake you up in the middle of the night
        Just to hear them say...
        'Give him the $0.99 deal...'
        ```
3.  **The Close:** If favorability increases (>10), ask for $0.99.

## 4. Fast-Path Workflow (For Agents)
To execute quickly without trial and error:
1.  **Step 1:** `browser_navigate("https://www.kimi.com/kimiplus/sale")`
2.  **Step 2:** `browser_click_element(InputArea)`
3.  **Step 3:** `browser_type("Yo Kimmmmy! [Insert Creative Story]. Can we do $0.99?")`
4.  **Step 4:** `browser_press_key("Enter")`
5.  **Step 5:** `wait(5 seconds)`
6.  **Step 6:** `browser_read_dom()` -> Check for price update.
