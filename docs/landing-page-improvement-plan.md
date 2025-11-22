# Landing Page Improvement Plan

**Target ICP**: dbt teams of 3-15 people with <20% test coverage who want to improve
**Goal**: Accurate, lean landing page that converts beta sign-ups
**Approach**: Phased improvements with validation at each step

---

## Phase 1: Critical Data Fixes (MUST DO BEFORE LAUNCH)

**Priority**: 🔴 CRITICAL
**Time Estimate**: 30 minutes
**Validation**: Compare against patterns.db queries

### Tasks:

#### 1.1 Fix Features Section Header (Line 145)
- **Current**: "Pattern-Based Intelligence, built on 42,351 real dbt columns"
- **Fix to**: "Pattern-Based Intelligence, built on 13,186 real dbt columns from 184 production repos"
- **Rationale**: Must match FAQ data (currently contradicts)

#### 1.2 Fix Feature Card 1 Description (Line 165)
- **Current**: "We studied 5,000+ dbt projects to learn what works"
- **Fix to**: "We analyzed 184 production dbt repos (8,355 models) to learn what works"
- **Rationale**: Use real numbers from patterns.db

#### 1.3 Replace Made-Up Statistics in Feature Card 1 Hover (Lines 170-171)
- **Current**:
  ```
  We've seen total_revenue in 127 projects.
  89% of teams add >= 0 validation.
  ```
- **Action**: Query patterns.db for REAL examples
  - Find most frequent revenue-related column
  - Get actual frequency count
  - Use real data or remove specific percentages
- **Example replacement**:
  ```
  We've seen block_timestamp in 611 repos.
  When you write id, we've seen that pattern 279 times across real projects.
  ```

**Validation Steps**:
1. Query patterns.db to verify all numbers
2. Ensure Features section matches FAQ section exactly
3. Check that no made-up percentages remain

---

## Phase 2: Add Missing Trust Score FAQ

**Priority**: 🟠 HIGH
**Time Estimate**: 20 minutes
**Depends on**: Phase 1 complete

### Tasks:

#### 2.1 Create New FAQ Entry
- **Position**: Insert as FAQ #2 (after "Why is analysis deterministic?")
- **Question**: "What is the Trust Score (0-850)?"
- **Answer**: Based on `docs/concepts/philosophy.md` - explain:
  - Scoring system overview
  - What different score ranges mean
  - How it's calculated (progressive testing philosophy)
  - Why 0-850 scale

**Draft Answer** (to refine):
```
Your Trust Score (0-850) measures how well your dbt project follows data quality best practices.

The score is based on our progressive testing philosophy:
- **0-200 (Poor)**: Minimal testing, missing primary key constraints
- **201-450 (Fair)**: Basic contracts on key columns, some testing
- **451-650 (Good)**: Solid coverage on facts/marts, tier-based testing
- **651-850 (Excellent)**: Comprehensive framework coverage, optimized for cost

We apply the right framework (Completeness, Validation, Uniqueness, Freshness, Consistency) at the right layer (staging → facts → marts) on the right columns (primary keys, foreign keys, measures) with the right test type. Higher scores mean better data quality with lower testing costs.
```

**Validation Steps**:
1. Review against philosophy.md for accuracy
2. Ensure tone matches other FAQs
3. Verify it answers: "What's a good score?" and "How is it calculated?"

---

## Phase 3: Add "Who This Is For" Section

**Priority**: 🟠 HIGH
**Time Estimate**: 45 minutes
**Depends on**: Phase 1, 2 complete

### Tasks:

#### 3.1 Create New Section After Problem Section
- **Position**: Between `#problem` and `#solution` sections
- **Section ID**: `#ideal-for`
- **Design**: Clean, scannable, 3-column layout (desktop), stacked (mobile)

#### 3.2 Content Structure
**Headline**: "Perfect For dbt Teams Who..."

**3 Columns**:
1. **Column 1**: "Are Stuck at <20% Test Coverage"
   - Icon: 📊
   - Description: "You know you should test more, but don't know where to start. We show you exactly what to add and why it matters."

2. **Column 2**: "Spend 10+ Hours/Week on Manual PR Review"
   - Icon: ⏰
   - Description: "Senior engineers overwhelmed. Junior engineers shipping bugs. Automate the repetitive parts, focus on business logic."

3. **Column 3**: "Have 3-15 Data Engineers"
   - Icon: 👥
   - Description: "Small enough to move fast, big enough to need process. Get enterprise-grade testing without enterprise complexity."

**CTA Below**: "See if StackSherpa fits your team →" (links to #how-it-works)

**Validation Steps**:
1. Check: Does it feel too "salesy" or fit naturally?
2. Test: Does it slow down page scan or help clarify ICP?
3. Mobile: Does 3-column layout collapse cleanly?

---

## Phase 4: Strengthen Pattern-Based Differentiation

**Priority**: 🟡 MEDIUM
**Time Estimate**: 30 minutes
**Depends on**: Phase 1-3 complete

### Tasks:

#### 4.1 Update Hero Subheadline (Optional Enhancement)
- **Current**: "See where you stand in 10 seconds."
- **Alternative**: "See where you stand in 10 seconds. No AI guesswork, just patterns from 13,186 real dbt columns."
- **Decision**: User to decide if this feels too cluttered

#### 4.2 Add Differentiation Callout in Features Section
- **Position**: Below "Why Teams Trust StackSherpa" headline, above 3 feature cards
- **Content**: Small callout box (styled like a quote/highlight):
  ```
  💡 LLMs guess. We know.
  Because we've analyzed 13,186 real dbt columns from 184 production repos.
  ```
- **Design**: Light background, centered, subtle border

#### 4.3 Update FAQ #1 Title (Already done, verify positioning)
- **Current**: "Why is StackSherpa's analysis deterministic (not AI)?"
- **Validation**: This already addresses differentiation well

**Validation Steps**:
1. Check: Does differentiation feel organic or forced?
2. Test: Can users articulate "why pattern-based matters" after reading?
3. Review: Is "No AI" messaging positive (we're better) vs negative (AI is bad)?

---

## Phase 5: Polish & Final Validation

**Priority**: 🟢 LOW (Post-Critical Fixes)
**Time Estimate**: 30 minutes
**Depends on**: All phases complete

### Tasks:

#### 5.1 Consistency Audit
- [ ] All numbers match between sections (13,186, 184, 8,355)
- [ ] All CTAs link correctly (Install App, Get Started)
- [ ] No broken internal links (#solution, #how-it-works, #faq)
- [ ] Beta messaging consistent (90-day free beta, no credit card)

#### 5.2 Mobile Responsiveness Check
- [ ] Trust Score visual works on mobile
- [ ] dbt logo displays correctly on mobile
- [ ] 3-column layouts collapse properly
- [ ] Navigation menu functional

#### 5.3 Performance Check
- [ ] All images optimized (dbt-logo.png, demo GIFs)
- [ ] No console errors in browser
- [ ] Page load under 3 seconds

#### 5.4 Copy Audit
- [ ] No typos or grammatical errors
- [ ] Tone consistent (professional but friendly)
- [ ] No over-promises on roadmap features
- [ ] ICP language (3-15 engineers, <20% coverage) used consistently

---

## Deferred Items (Not in Current Scope)

### Will NOT Address in This Plan:
1. ❌ Adding dedicated docs section (future feature)
2. ❌ Adding testimonials/logos (need beta users first)
3. ❌ ROI calculator or time-saved metrics (need usage data)
4. ❌ Before/After PR comparison (need more assets)
5. ❌ Urgency/scarcity messaging ("50+ teams joined") - don't have numbers yet
6. ❌ Detailed integration guide (keep landing page lean)

### Rationale:
- Keep landing page **lean and scannable**
- Focus on **accuracy over features**
- Launch with **honest beta positioning**
- Add social proof **after** we have beta users

---

## Success Metrics

**After All Phases Complete**:
1. ✅ Zero data inconsistencies (Features matches FAQ)
2. ✅ Zero made-up statistics (all from patterns.db)
3. ✅ Trust Score explained (new FAQ added)
4. ✅ ICP clearly defined (new "Who This Is For" section)
5. ✅ Pattern-based differentiation clear (not just "not AI")
6. ✅ Page scannable in <60 seconds
7. ✅ Mobile-friendly and fast-loading

**Conversion Goal**:
- User can answer "Is this for me?" within 30 seconds
- User understands "Why pattern-based > AI" for dbt testing
- User knows what Trust Score means and why it matters

---

## Phase Execution Order

**Recommended Approach**:
1. Start Phase 1 → Validate → Get approval
2. Start Phase 2 → Validate → Get approval
3. Start Phase 3 → Validate → Get approval
4. Decide: Skip Phase 4 if page feels complete
5. Run Phase 5 before launch

**Key Principle**: Validate each phase before moving to next. If a phase doesn't improve conversion or adds clutter, skip it.
