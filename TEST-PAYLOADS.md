# Test Payloads for Winnicki AI Sales System

## Workflow 1: Pre-Call Research

### Test Case 1: E-commerce Company

```bash
curl -X POST https://n8n.srv943791.hstgr.cloud/webhook/winnicki-lead-intake \
-H "Content-Type: application/json" \
-d '{
  "first_name": "Sarah",
  "last_name": "Johnson",
  "email": "sarah@blueoceanretail.com",
  "phone": "555-234-5678",
  "company_name": "Blue Ocean Retail",
  "website": "https://www.blueoceanretail.com",
  "interested_in": "E-commerce Solution",
  "additional_info": "Currently on Shopify but having scaling issues. Need better inventory management and multi-channel selling capabilities."
}'
```

---

### Test Case 2: Service Business

```bash
curl -X POST https://n8n.srv943791.hstgr.cloud/webhook/winnicki-lead-intake \
-H "Content-Type: application/json" \
-d '{
  "first_name": "Michael",
  "last_name": "Chen",
  "email": "michael@summitconsulting.co",
  "phone": "555-345-6789",
  "company_name": "Summit Consulting Group",
  "website": "https://www.summitconsulting.co",
  "interested_in": "Website Development",
  "additional_info": "Professional services firm needing complete website redesign. Current site is 5 years old. Want modern design, blog, case studies section, and better mobile experience."
}'
```

---

### Test Case 3: Startup

```bash
curl -X POST https://n8n.srv943791.hstgr.cloud/webhook/winnicki-lead-intake \
-H "Content-Type: application/json" \
-d '{
  "first_name": "Jessica",
  "last_name": "Martinez",
  "email": "jessica@techstartup.io",
  "phone": "555-456-7890",
  "company_name": "TechStart Innovations",
  "website": "https://www.techstartup.io",
  "interested_in": "Voice AI Agents",
  "additional_info": "Seed-stage SaaS company. Need AI-powered customer support to scale without hiring. Interested in voice agents for inbound queries."
}'
```

---

### Test Case 4: Local Business

```bash
curl -X POST https://n8n.srv943791.hstgr.cloud/webhook/winnicki-lead-intake \
-H "Content-Type: application/json" \
-d '{
  "first_name": "David",
  "last_name": "Thompson",
  "email": "david@greenvalleylawn.com",
  "phone": "555-567-8901",
  "company_name": "Green Valley Lawn Care",
  "website": "https://www.greenvalleylawn.com",
  "interested_in": "SEO Services",
  "additional_info": "Family-owned lawn care business. Not showing up in local searches. Need better Google rankings and online booking system."
}'
```

---

## Workflow 2: Proposal Generation

**IMPORTANT:** Use the same email as from Workflow 1 test.

---

### Test Case 1: E-commerce Follow-up

```bash
curl -X POST https://n8n.srv943791.hstgr.cloud/webhook/winnicki-post-call \
-H "Content-Type: application/json" \
-d '{
  "lead_email": "sarah@blueoceanretail.com",
  "call_date": "2025-01-14",
  "call_notes": "Excellent call with Sarah. Blue Ocean Retail is experiencing 40% growth but their current Shopify store cannot handle the inventory complexity (3000+ SKUs across 5 warehouse locations). They sell on Amazon, eBay, and their own site but inventory sync is manual. Looking for headless commerce solution with real-time inventory management. Sarah is VP of Operations, reports to CEO who will approve budget. Decision timeline is 30 days. They have developers in-house who can handle some integration work. Budget is flexible if ROI is clear.",
  "budget_discussed": "Yes",
  "budget_amount": 15000,
  "timeline_preference": "8-10 weeks for Phase 1, ongoing for Phase 2",
  "services_needed": ["E-commerce Platform", "Inventory Management Integration", "Multi-channel Sync", "API Development", "Training"],
  "pain_points": "Manual inventory updates across channels causing overselling and customer complaints. Current Shopify plan maxed out at 1500 SKUs. No real-time sync between warehouses. Mobile checkout has 60% abandonment rate. Cannot scale promotions across all channels simultaneously. Reporting is fragmented.",
  "business_goals": "Scale to 5000 SKUs by Q3. Reduce inventory errors by 90%. Increase conversion rate by 25%. Launch 2 new sales channels. Automate 80% of order processing. Real-time warehouse visibility.",
  "priority_level": "High"
}'
```

---

### Test Case 2: Service Business Follow-up

```bash
curl -X POST https://n8n.srv943791.hstgr.cloud/webhook/winnicki-post-call \
-H "Content-Type: application/json" \
-d '{
  "lead_email": "michael@summitconsulting.co",
  "call_date": "2025-01-14",
  "call_notes": "Great conversation with Michael, Managing Partner at Summit Consulting. Firm has 25 consultants and strong reputation but website doesn not reflect their expertise. Current site built in 2019 on WordPress, lots of plugin conflicts and security concerns. Want complete rebrand with case study showcase, thought leadership blog, consultant profiles, and client portal for project updates. Michael emphasized they need mobile-first design since partners review on phones. SEO is priority - they are not ranking for key consulting terms. Need CRM integration with HubSpot. Michael can make decision but wants buy-in from 2 other partners (will present our proposal to them).",
  "budget_discussed": "Yes",
  "budget_amount": 8000,
  "timeline_preference": "6 weeks, with Q1 launch goal",
  "services_needed": ["Website Development", "SEO Services", "CRM Integration", "Content Strategy", "Training"],
  "pain_points": "Website looks dated and does not build trust. Mobile experience is poor. Blog has not been updated in 18 months. Not ranking for target keywords. No lead capture strategy. HubSpot data separate from website. Cannot track which content drives leads.",
  "business_goals": "Attract 50% more qualified leads. Rank on page 1 for 10 target keywords. Establish thought leadership through content. Integrate all marketing data. Reduce sales cycle by providing better self-education.",
  "priority_level": "Medium"
}'
```

---

### Test Case 3: Startup Follow-up

```bash
curl -X POST https://n8n.srv943791.hstgr.cloud/webhook/winnicki-post-call \
-H "Content-Type: application/json" \
-d '{
  "lead_email": "jessica@techstartup.io",
  "call_date": "2025-01-14",
  "call_notes": "Energizing call with Jessica (CEO/Founder). TechStart just raised seed round and needs to scale support without headcount. Currently gets 200+ support inquiries daily, 70% are repetitive questions. Jessica wants AI voice agent to handle Tier 1 support 24/7, escalate complex issues to humans. Integration with their Zendesk required. Want natural conversation flow, not robotic. They have API docs ready. Jessica is solo decision maker, moving fast. Mentioned competitor launched similar feature and they need to match quickly.",
  "budget_discussed": "Yes",
  "budget_amount": 6000,
  "timeline_preference": "ASAP - 3 weeks if possible",
  "services_needed": ["Voice AI Agent Setup", "Zendesk Integration", "Custom Training", "Monthly Optimization"],
  "pain_points": "Support ticket volume growing 30% monthly. Cannot afford to hire 5+ support reps. Response time is 8+ hours. Customers frustrated with slow replies. Same questions asked repeatedly. Support team burned out. Missing sales opportunities due to slow inquiry response.",
  "business_goals": "Handle 80% of Tier 1 inquiries via AI. Reduce response time to under 1 minute. Free support team for complex issues. Operate 24/7 support. Improve customer satisfaction scores. Scale without linear cost increases.",
  "priority_level": "High"
}'
```

---

### Test Case 4: Local Business Follow-up

```bash
curl -X POST https://n8n.srv943791.hstgr.cloud/webhook/winnicki-post-call \
-H "Content-Type: application/json" \
-d '{
  "lead_email": "david@greenvalleylawn.com",
  "call_date": "2025-01-14",
  "call_notes": "Down-to-earth conversation with David, owner of Green Valley Lawn Care. Family business, 20 employees, serving local area for 15 years. Current website is DIY on Wix, not mobile-friendly. Does not show up when people search lawn care in the area. Most leads come from referrals and yard signs. David wants to grow 30% next year but needs online presence. Interested in local SEO, Google Business Profile optimization, and simple booking system. Budget is modest but David understands value. Wants to start small and expand if it works. Decision is his alone but wants to discuss with wife who handles bookkeeping.",
  "budget_discussed": "Yes - somewhat budget-conscious",
  "budget_amount": 3000,
  "timeline_preference": "Flexible, but wants to launch before spring busy season (8 weeks)",
  "services_needed": ["Website Development", "Local SEO", "Google Business Profile", "Online Booking", "Basic Training"],
  "pain_points": "Not appearing in local searches. Losing jobs to competitors with better websites. No way for customers to book online (must call during business hours). Website looks unprofessional. Missing out on mobile users. Cannot track where leads come from. No reviews showcased on site.",
  "business_goals": "Rank in top 3 for local lawn care searches. Get 20+ online bookings per month. Increase revenue by 30%. Build credible online presence. Showcase 50+ positive reviews. Reduce phone call volume for simple bookings.",
  "priority_level": "Medium"
}'
```

---

## Postman Collection (Alternative to curl)

If you prefer using Postman:

### Workflow 1 Request:

**Method:** POST  
**URL:** `https://n8n.srv943791.hstgr.cloud/webhook/winnicki-lead-intake`  
**Headers:**  
```
Content-Type: application/json
```

**Body (raw JSON):**
```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@example.com",
  "phone": "555-123-4567",
  "company_name": "Example Corp",
  "website": "https://www.example.com",
  "interested_in": "Website Development",
  "additional_info": "Your notes here"
}
```

---

### Workflow 2 Request:

**Method:** POST  
**URL:** `https://n8n.srv943791.hstgr.cloud/webhook/winnicki-post-call`  
**Headers:**  
```
Content-Type: application/json
```

**Body (raw JSON):**
```json
{
  "lead_email": "john@example.com",
  "call_date": "2025-01-14",
  "call_notes": "Detailed call summary here...",
  "budget_discussed": "Yes",
  "budget_amount": 5000,
  "timeline_preference": "4-6 weeks",
  "services_needed": ["Website Development", "SEO"],
  "pain_points": "List specific pain points discussed...",
  "business_goals": "List specific goals discussed...",
  "priority_level": "High"
}
```

---

## Testing Checklist

### After Workflow 1 Test:

- [ ] Received 200 OK response with lead_id
- [ ] Email arrived at winnickidigital@gmail.com
- [ ] New row in Google Sheets
- [ ] All 6 agent columns populated
- [ ] Status set to "Awaiting Call"
- [ ] Research quality is good

### After Workflow 2 Test:

- [ ] Received 200 OK response with proposal_url
- [ ] Google Sheets updated with call data
- [ ] Proposal created in Google Drive
- [ ] Email arrived with Drive link
- [ ] Status changed to "Proposal Sent"
- [ ] Proposal quality is high
- [ ] Proposal references pre-call research

---

## Common Testing Mistakes

❌ Using different email in Workflow 2 than Workflow 1  
✅ Use exact same email for both workflows

❌ Running Workflow 2 before Workflow 1 completes  
✅ Wait for Workflow 1 email before testing Workflow 2

❌ Not checking Google Sheets between tests  
✅ Verify data after each workflow execution

❌ Forgetting to activate workflows  
✅ Toggle workflows to "Active" before testing

❌ Using production webhooks for testing  
✅ Test thoroughly before connecting real forms

---

## Expected Response Times

**Workflow 1:**
- Webhook response: Instant (< 1 second)
- Total execution: 60-90 seconds
- Email arrival: Within 2 minutes

**Workflow 2:**
- Webhook response: Instant (< 1 second)
- Total execution: 90-150 seconds
- Email arrival: Within 3 minutes

If either workflow takes longer than 5 minutes, check n8n execution logs for errors.

---

**Ready to test?** Start with Test Case 1 for both workflows, then try the others to see how the system handles different scenarios.
