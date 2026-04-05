# BarberBook: Cost Analysis & Financial Projections

**Prepared**: April 2026
**Document Type**: Financial Planning
**Confidential** -- For Internal Use Only

---

## 1. Executive Summary

BarberBook has an unusually capital-efficient cost structure. Infrastructure costs start at effectively $0 (free tiers of Vercel, Supabase, Mapbox) and scale to ~$450/mo at 100K+ users. Marketing dominates total spend. Breakeven at the Growth stage requires ~2,250 listings at a blended 1.5% paid conversion rate -- achievable with 2-3 metro areas. The platform can operate at near-zero cost until traction is proven, then scale spend proportionally with revenue.

---

## 2. Infrastructure Costs

### 2.1 Service-by-Service Breakdown

#### Hosting: Vercel (Next.js)

| Stage | Plan | Cost | What You Get |
|---|---|---|---|
| MVP (0-1K users) | Hobby (Free) | $0/mo | 100GB bandwidth, serverless functions, edge network |
| Growth (10-50K users) | Pro | $20/mo | 1TB bandwidth, advanced analytics, password protection |
| Scale (100K+ users) | Pro + overages | $40-$80/mo | Additional bandwidth at $40/100GB, compute at $0.18/GB-hr |

**Notes**: Vercel's free tier is generous for MVP. The jump to Pro at $20/mo covers most growth scenarios. Enterprise tier ($400+/mo) is unlikely to be needed in Year 1.

#### Database: Supabase (PostgreSQL + PostGIS)

| Stage | Plan | Cost | What You Get |
|---|---|---|---|
| MVP (0-1K users) | Free | $0/mo | 500MB storage, 2GB transfer, 50K monthly active users |
| Growth (10-50K users) | Pro | $25/mo | 8GB storage, 250GB transfer, daily backups |
| Growth (high) | Pro + compute add-on | $50/mo | Dedicated compute for PostGIS queries |
| Scale (100K+ users) | Pro + add-ons | $75-$150/mo | Additional storage, compute, PITR backups |

**Notes**: PostGIS spatial queries are compute-intensive. The free tier handles MVP but Growth will need dedicated compute. Supabase Pro at $25/mo is excellent value for PostgreSQL + extensions (pg_trgm, fuzzystrmatch, PostGIS).

#### Maps & Geocoding: Mapbox

| Stage | Usage | Cost | Pricing Detail |
|---|---|---|---|
| MVP (0-1K users) | < 50K map loads | $0/mo | 50K free map loads, 100K free geocoding requests |
| Growth (10-50K users) | 50K-200K loads | $0-$25/mo | $5 per 1,000 loads after free tier |
| Scale (100K+ users) | 500K-2M loads | $250-$500/mo | Volume pricing available |

**Notes**: Mapbox's free tier (50K loads + 100K geocode requests) is very generous. The "Add a Shop" geocoding flow uses the Geocoding API for address normalization -- this is the primary API cost driver at scale.

#### Address Validation: Smarty (formerly SmartyStreets)

| Stage | Usage | Cost |
|---|---|---|
| MVP | < 250 lookups | $0 (trial) |
| Growth | 1,000-5,000/mo | $6-$15/mo |
| Scale | 10,000-50,000/mo | $30-$60/mo |

**Notes**: Used for address normalization in duplicate detection. Low volume at MVP since user-submitted shops are the primary trigger.

#### Domain & SSL

| Item | Cost |
|---|---|
| Domain (barberbook.com or similar) | ~$12/yr ($1/mo) |
| SSL | Free (included with Vercel) |

### 2.2 Infrastructure Cost Summary

| Service | MVP (0-1K) | Growth (10-50K) | Scale (100K+) |
|---|---|---|---|
| Vercel | $0 | $20 | $40-$80 |
| Supabase | $0 | $25-$50 | $75-$150 |
| Mapbox | $0 | $0-$25 | $250-$500 |
| Smarty | $0 | $6-$15 | $30-$60 |
| Domain + SSL | ~$1 | ~$1 | ~$1 |
| **Total Infrastructure** | **~$1/mo** | **~$52-$111/mo** | **~$396-$791/mo** |

**Key insight**: Infrastructure is dirt cheap. The entire platform can run for $1/mo during MVP. Even at 100K+ users, infrastructure stays under $800/mo.

---

## 3. Marketing Costs

### 3.1 Channel-by-Channel Breakdown

#### Google Ads

| Keyword Category | CPC Range | Monthly Impressions (est.) | Conversion Rate |
|---|---|---|---|
| "barber near me" | $2-$6 | High (110K+ searches) | 3-5% CTR |
| "barbershop reviews [city]" | $1-$3 | Medium | 4-6% CTR |
| "best barber [city]" | $2-$4 | Medium | 3-5% CTR |
| "barber for [hair type]" | $0.50-$2 | Low (but high intent) | 5-8% CTR |

| Stage | Monthly Budget | Expected Clicks | Expected New Users |
|---|---|---|---|
| MVP | $0 | -- | -- |
| Growth | $500-$1,000 | 200-500 | 100-250 |
| Scale | $2,000 | 600-1,000 | 300-500 |

#### Meta / Instagram Ads

| Ad Format | CPC Range | Best For |
|---|---|---|
| Feed photo/video | $0.70-$1.50 | Brand awareness, before/after content |
| Story ads | $0.80-$2.00 | Feature demos (hair-type picker) |
| Carousel | $1.00-$2.50 | Barber spotlights, multiple styles |
| Lookalike audiences | $1.50-$3.35 | Scaling proven audiences |

| Stage | Monthly Budget | Expected Clicks | Expected New Users |
|---|---|---|---|
| MVP | $0 | -- | -- |
| Launch | $300 | 200-430 | 50-100 |
| Growth | $400-$800 | 250-600 | 60-150 |
| Scale | $1,500 | 450-1,000 | 110-250 |

#### SEO Tools (Phase 4+)

| Tool | Cost | Purpose |
|---|---|---|
| Ahrefs Lite | $130/mo | Keyword tracking, backlink analysis, competitor monitoring |

#### Other Marketing Costs

| Item | Cost | Phase |
|---|---|---|
| Printed materials (QR code flyers for shop outreach) | ~$50-$100 one-time | Phase 1 |
| Influencer partnerships | $500-$1,000/mo | Phase 4 |

### 3.2 Marketing Cost Summary

| Channel | MVP | Growth | Scale |
|---|---|---|---|
| Google Ads | $0 | $500-$1,000 | $2,000 |
| Meta/Instagram Ads | $0 | $400-$800 | $1,500 |
| TikTok Ads | $0 | $0-$200 | $500 |
| SEO Tools | $0 | $0 | $130 |
| Influencer Partnerships | $0 | $0 | $500-$1,000 |
| **Total Marketing** | **$0/mo** | **~$900-$2,000/mo** | **~$4,630-$5,130/mo** |

---

## 4. Total Cost Summary

| Category | MVP (0-1K) | Growth (10-50K) | Scale (100K+) |
|---|---|---|---|
| Infrastructure | ~$1 | ~$75 | ~$450 |
| Marketing | $0 | ~$1,500 | ~$4,800 |
| **Total Monthly** | **~$1** | **~$1,575** | **~$5,250** |
| **Total Annual** | **~$12** | **~$18,900** | **~$63,000** |

**Cost composition**: At every stage, marketing dominates. Infrastructure is <10% of total costs at Growth and Scale. This means the business can run at near-zero cost while validating product-market fit.

---

## 5. Revenue Model

### 5.1 Pricing Tiers

| Tier | Price | Target | Key Features |
|---|---|---|---|
| **Free** | $0/mo | All shops (adoption driver) | Basic profile, respond to reviews, search visibility |
| **Pro** | $19/mo | Active shops wanting visibility | Portfolio, analytics, review tools, Pro badge, all staff included |
| **Premium** | $49/mo | High-volume shops wanting leads | Promoted placement, lead alerts, messaging, marketing tools, priority support |

**No per-staff fees. No commissions. No client fees. Month-to-month.**

### 5.2 Revenue Per Listing (Blended)

Assumption: Of all listings (claimed + unclaimed), a percentage convert to paid tiers.

| Conversion Scenario | Pro Rate | Premium Rate | Blended Revenue/Listing/Mo |
|---|---|---|---|
| Conservative (Year 1) | 1.0% | 0.5% | $0.435 |
| Moderate (Year 2) | 2.0% | 1.0% | $0.870 |
| Mature (Year 3+) | 3.0% | 1.5% | $1.305 |
| Industry benchmark | 4.0% | 2.0% | $1.740 |

**Context**: SMB SaaS freemium-to-paid conversion benchmarks are 2-5%. Local business platforms (Yelp, Google Business) see 6-10% of businesses engage with paid features. Our conservative estimate of 1.5% total paid conversion is deliberately below industry norms.

### 5.3 Future Revenue Streams (Phase 2+, not modeled in breakeven)

| Stream | Revenue Model | Estimated Contribution |
|---|---|---|
| Payment processing | 2.2% pass-through (cost basis, no markup) | Break-even -- trust builder, not profit center |
| Product affiliates | 5-15% commission on recommended grooming products | $2-$5/transaction, low volume initially |
| Local brand advertising | Geo-fenced ads from grooming brands (Andis, Wahl, etc.) | $500-$5,000/mo at scale |

---

## 6. Breakeven Analysis

### 6.1 Listings Required to Break Even

Using blended revenue of $0.435/listing/mo (conservative 1.5% paid conversion):

| Stage | Monthly Cost | Listings to Break Even | Listings per City (3 cities) |
|---|---|---|---|
| MVP | $1 | 3 | 1 |
| Growth | $1,575 | 3,621 | 1,207 |
| Scale | $5,250 | 12,069 | 4,023 (assuming 3 cities) |

### 6.2 Breakeven Sensitivity

| Paid Conversion Rate | Revenue/Listing | Listings for Growth BE | Listings for Scale BE |
|---|---|---|---|
| 1.0% (pessimistic) | $0.290 | 5,431 | 18,103 |
| 1.5% (conservative) | $0.435 | 3,621 | 12,069 |
| 2.0% (moderate) | $0.580 | 2,716 | 9,052 |
| 3.0% (optimistic) | $0.870 | 1,810 | 6,034 |
| 4.0% (industry avg) | $1.160 | 1,358 | 4,526 |

### 6.3 Feasibility Check

| Data Point | Value |
|---|---|
| US barbershops | ~80,000 |
| US salons | ~1,000,000+ |
| Barbershops in Austin, TX | ~800+ |
| Barbershops in Brooklyn, NY | ~600+ |
| Barbershops in Los Angeles, CA | ~3,000+ |
| **3-city total** | **~4,400+ barbershops alone** |

At 1.5% conversion, Growth breakeven requires ~3,621 listings. Three launch cities have 4,400+ barbershops (not counting salons). **Breakeven is achievable within Year 1 with just barbershops in 3 metros, before expanding to salons or new cities.**

---

## 7. Financial Projections (24-Month Model)

### 7.1 Conservative Scenario

| Month | Listings | Claimed % | Paid % | MRR | Monthly Cost | Net |
|---|---|---|---|---|---|---|
| 1 | 500 | 5% | 0% | $0 | $1 | -$1 |
| 2 | 800 | 8% | 0% | $0 | $1 | -$1 |
| 3 | 1,200 | 10% | 0.5% | $92 | $500 | -$408 |
| 4 | 1,800 | 12% | 0.8% | $220 | $600 | -$380 |
| 5 | 2,500 | 14% | 1.0% | $383 | $1,000 | -$617 |
| 6 | 3,500 | 15% | 1.2% | $643 | $1,200 | -$557 |
| 8 | 5,000 | 17% | 1.5% | $1,148 | $1,500 | -$352 |
| 10 | 7,500 | 18% | 1.8% | $2,066 | $1,800 | +$266 |
| 12 | 10,000 | 20% | 2.0% | $3,060 | $2,000 | **+$1,060** |
| 18 | 25,000 | 22% | 2.5% | $9,563 | $3,500 | **+$6,063** |
| 24 | 50,000 | 25% | 3.0% | $22,950 | $5,000 | **+$17,950** |

**MRR calculation**: Listings x Paid% x (70% Pro at $19 + 30% Premium at $49) = Listings x Paid% x $28/avg

### 7.2 Revenue Milestones

| Milestone | When (Conservative) | Listings | MRR |
|---|---|---|---|
| First revenue | Month 3 | 1,200 | ~$92 |
| Cover infrastructure | Month 5 | 2,500 | ~$383 |
| Cover all costs (breakeven) | Month 10 | 7,500 | ~$2,066 |
| $5K MRR | Month 14 | 15,000 | ~$5,000 |
| $10K MRR | Month 18 | 25,000 | ~$10,000 |
| $25K MRR | Month 24 | 50,000 | ~$25,000 |

### 7.3 Cumulative Cash Flow

| Period | Revenue | Costs | Net | Cumulative |
|---|---|---|---|---|
| Months 1-3 | $92 | $503 | -$411 | -$411 |
| Months 4-6 | $1,246 | $2,800 | -$1,554 | -$1,965 |
| Months 7-9 | $3,858 | $4,500 | -$642 | -$2,607 |
| Months 10-12 | $6,186 | $5,800 | +$386 | **-$2,221** |
| Months 13-18 | $38,076 | $18,000 | +$20,076 | **+$17,855** |
| Months 19-24 | $104,400 | $28,000 | +$76,400 | **+$94,255** |

**Maximum cash outlay before profitability**: ~$2,607 (Month 9). This is the total capital needed to reach breakeven -- extraordinarily low for a tech platform.

---

## 8. Unit Economics

### 8.1 Customer Acquisition Cost (CAC)

| Channel | Cost per Acquired Paid Business |
|---|---|
| Organic (SEO, social, referrals) | ~$0-$5 |
| In-person outreach | ~$30-$50 (time cost) |
| Paid ads (indirect -- consumer drives business claim) | ~$50-$100 |
| **Blended CAC** | **~$25-$50** |

### 8.2 Lifetime Value (LTV)

| Tier | Monthly Revenue | Avg. Retention | 12-Mo LTV | 24-Mo LTV |
|---|---|---|---|---|
| Pro ($19/mo) | $19 | 80% (9.6 months) | $182 | $328 |
| Premium ($49/mo) | $49 | 85% (10.2 months) | $500 | $900 |
| **Blended** (70/30 Pro/Premium) | **$28** | **82%** | **$277** | **$500** |

### 8.3 LTV:CAC Ratio

| Scenario | CAC | 12-Mo LTV | LTV:CAC | Healthy? |
|---|---|---|---|---|
| Organic acquisition | $5 | $277 | 55:1 | Excellent |
| Outreach acquisition | $40 | $277 | 7:1 | Strong |
| Paid acquisition | $75 | $277 | 3.7:1 | Acceptable |
| **Blended** | **$35** | **$277** | **7.9:1** | **Strong** |

**Industry benchmark**: LTV:CAC > 3:1 is considered healthy for SaaS. BarberBook's blended 7.9:1 leaves significant room for increased marketing spend.

### 8.4 CAC Payback Period

| Scenario | CAC | Monthly Revenue | Payback Period |
|---|---|---|---|
| Organic | $5 | $28 | < 1 month |
| Outreach | $40 | $28 | 1.4 months |
| Paid | $75 | $28 | 2.7 months |
| **Blended** | **$35** | **$28** | **1.25 months** |

---

## 9. Comparison: BarberBook vs. Competitor Cost to Barbers

### 9.1 Monthly Cost for a 5-Chair Barbershop

| Platform | Subscription | Staff Fees | Processing (on $8K/mo) | Commission (5 new clients x $40) | Client Fees | **Total Monthly** |
|---|---|---|---|---|---|---|
| **BarberBook Pro** | $19 | $0 | N/A (no processing yet) | $0 | $0 | **$19** |
| **BarberBook Premium** | $49 | $0 | N/A | $0 | $0 | **$49** |
| Booksy | $30 | $80 (4 extra) | $209 | $60 (Boost) | $0 | **$379** |
| Fresha | $20 + $48 (4 team) | Included | $176 | $48 | $0 | **$292** |
| Squire (Shop tier) | $100 | Included | $208 | $40 | Variable | **$348+** |
| Vagaro | $30 | $40 (4 extra) | $176 | $0 | $0 | **$246** |
| StyleSeat | $35 | N/A (solo) | $196 | $60 | Client pays | **$291+** |

**BarberBook is 5-20x cheaper** than incumbents for a typical barbershop. Even at the Premium tier ($49), it's the cheapest option in the market by a wide margin. Note: BarberBook does not include payment processing in Phase 1 -- this is a discovery platform, not a POS replacement.

### 9.2 What Barbers Save by Switching

| Switching From | Current Cost | BarberBook Premium | **Monthly Savings** | **Annual Savings** |
|---|---|---|---|---|
| Booksy | $379 | $49 | $330 | $3,960 |
| Squire | $348 | $49 | $299 | $3,588 |
| Fresha | $292 | $49 | $243 | $2,916 |
| Vagaro | $246 | $49 | $197 | $2,364 |
| StyleSeat | $291 | $49 | $242 | $2,904 |

---

## 10. Risk Factors & Mitigations

### 10.1 Financial Risks

| Risk | Impact | Likelihood | Mitigation |
|---|---|---|---|
| Paid conversion < 1% | Breakeven delayed to 15K+ listings | Medium | Free tier drives volume; focus outreach on shops already getting reviews |
| Marketing spend inefficiency | CAC exceeds $100 | Low-Medium | Organic-first strategy limits paid dependency; gate spend on ROAS |
| Mapbox costs spike at scale | +$500/mo at 100K users | Medium | Negotiate volume pricing; cache map tiles; lazy-load maps |
| Competitor price war | Incumbents drop prices to match | Low | Our costs are already at floor; competitors can't match without restructuring revenue |

### 10.2 Operational Risks

| Risk | Impact | Likelihood | Mitigation |
|---|---|---|---|
| Cold start (no reviews) | Users leave empty platform | High (early) | Pre-seed 200-500 shops + reviews before public launch |
| Review spam/fraud | Trust erosion | Medium | Honeypot, rate limiting, time validation, fingerprinting, minimum text length |
| Duplicate listings | Messy directory | Medium | 3-layer dedup (UX interception + composite scoring + address normalization) |
| Data accuracy (unclaimed shops) | Wrong info frustrates users | Medium | User flagging system; incentivize owners to claim and correct |

---

## 11. Capital Requirements Summary

| Phase | Duration | Total Spend | Cumulative | Funded By |
|---|---|---|---|---|
| Pre-Launch | Month 1-2 | ~$2 | $2 | Founder |
| Launch | Month 3-4 | ~$1,100 | ~$1,100 | Founder |
| Early Growth | Month 5-9 | ~$7,500 | ~$8,600 | Founder + early revenue |
| Breakeven | Month 10 | -- | -- | Self-sustaining |
| Growth | Month 10-24 | Revenue-funded | -- | Operating cash flow |

**Total capital required to reach breakeven: ~$2,600**

This is achievable as a bootstrapped project with zero external funding. The business is profitable from Month 10 in the conservative scenario, and the maximum cash outlay is under $3,000.

---

## 12. Key Takeaways

1. **Near-zero startup cost**: The platform can launch and validate for under $100 using free tiers of Vercel, Supabase, and Mapbox.

2. **Marketing dominates costs**: Infrastructure is <10% of spend at every stage. Financial success depends on marketing efficiency, not engineering costs.

3. **Low breakeven threshold**: ~3,600 listings at 1.5% paid conversion covers Growth-stage costs. Three metro areas provide 4,400+ barbershops alone.

4. **Under $3K to profitability**: Maximum capital outlay before breakeven is ~$2,600 -- achievable without external funding.

5. **Strong unit economics**: 7.9:1 LTV:CAC ratio with 1.25-month payback period provides significant margin for experimentation.

6. **Massive savings for barbers**: BarberBook is 5-20x cheaper than incumbents, making the switch decision trivial for cost-conscious shop owners.

7. **Multiple levers for revenue growth**: Paid conversion rate, listing volume, and future revenue streams (processing, affiliates, advertising) all compound independently.

---

*Document version 1.0 -- April 2026*
