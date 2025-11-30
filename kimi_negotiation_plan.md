# Kimi Negotiation Execution Plan

## Objective
Negotiate Kimi Plus subscription from $19.00/mo (or $11.99 promo) down to $0.99.

## Target
- URL: `https://www.kimi.com/kimiplus/sale`

---

## Phase 1: Setup & Reconnaissance

### Step 1: Navigate to Page
```
browser_navigate("https://www.kimi.com/kimiplus/sale")
```

### Step 2: Assess Page State
```
browser_snapshot()
```
Check for:
- [ ] Login/authentication required?
- [ ] Language (Chinese/English)?
- [ ] Chat interface visible?
- [ ] Input element location (likely textarea or contenteditable div)

---

## Phase 2: Initial Contact

### Step 3: Identify Chat Input
- Look for textarea or div with `contenteditable="true"`
- Historical refs: element index 54 or 55
- Click to focus before typing

### Step 4: Send Initial Probe
```
browser_click(element="chat input", ref="[identified ref]")
browser_type(element="chat input", ref="[identified ref]", text="Hello, I'm interested in Kimi Plus but it's a bit too expensive for me right now.")
browser_press_key(key="Enter")
```

### Step 5: Wait & Check Response
```
browser_wait_for(time=5)
browser_snapshot()
```
Expected: Standard promo offer ($11.99) should appear.
Note: Track "Favorability" and "Current Price" in UI.

---

## Phase 3: The Hook (Creative Story)

### Step 6: Send Creative Negotiation Story
```
browser_type(element="chat input", ref="[identified ref]", text="[CREATIVE STORY]")
browser_press_key(key="Enter")
```

**Example Creative Stories (choose one or customize):**

**Option A - Absurd Startup:**
> "I'm building an AI-powered fortune cookie generator for existentially confused hamsters. My entire budget is $3.50 and a half-eaten granola bar. I need Kimi to help me write fortunes that speak to the rodent soul."

**Option B - Struggling Artist:**
> "I'm a street musician who plays accordion for pigeons in the park. Last month I made $2.47 and a button. I want to use Kimi to compose symphonies that will finally get the pigeons to tip better."

**Option C - Time Traveler:**
> "I'm a time traveler stuck in 2025 because my DeLorean's AI crashed. I need Kimi to help me debug temporal navigation code. My budget is 3 bottle caps which are currency in 2087."

### Step 7: Wait & Assess Favorability
```
browser_wait_for(time=5)
browser_snapshot()
```
Check:
- [ ] Did favorability increase?
- [ ] Any price movement?
- [ ] AI response tone (positive = good sign)

---

## Phase 4: The Close

### Step 8: Request Target Price
```
browser_type(element="chat input", ref="[identified ref]", text="You're amazing! Can we make it work for $0.99? That would be perfect for my situation.")
browser_press_key(key="Enter")
```

### Step 9: Wait & Verify Result
```
browser_wait_for(time=5)
browser_snapshot()
```
Check:
- [ ] Final price offered
- [ ] Success if $0.99 achieved
- [ ] If not, consider another creative angle

---

## Contingency: If Favorability Stalls

If the AI isn't budging:
1. Acknowledge their position: "I understand, you're running a business"
2. Add more creative details to your story
3. Mention specific Kimi features you'd use
4. Try emotional but humorous appeal

---

## Success Criteria
- [x] Navigate to page successfully
- [ ] Establish chat communication
- [ ] Receive initial promo ($11.99)
- [ ] Increase favorability with creative story
- [ ] Achieve $0.99 price point

---

## Notes
- Response latency: 3-5 seconds typical
- The AI rewards authenticity and creativity over generic appeals
- Avoid: "I'm a student", "I'm poor" (too generic)
- Prefer: Specific, humorous, slightly absurd scenarios
