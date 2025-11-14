# Winnicki Digital AI Sales System - Setup Guide

## Quick Start

You have two workflow files ready to import:
1. `workflow-1-precall-research.json` - Pre-Call Research (6 parallel agents)
2. `workflow-2-proposal-generation.json` - Proposal Generation (4 sequential agents)

---

## Step 1: Import Workflows

### Import into n8n

1. Go to https://n8n.srv943791.hstgr.cloud/
2. Click **Workflows** in the left sidebar
3. Click **Import from File**
4. Upload `workflow-1-precall-research.json`
5. Repeat for `workflow-2-proposal-generation.json`

---

## Step 2: Configure Credentials

Both workflows need these credentials configured:

### A. Google Sheets OAuth

1. In any Google Sheets node, click **Create New Credential**
2. Choose **Google Sheets OAuth2 API**
3. Follow the OAuth flow to authorize access
4. Ensure the credential has access to: `1tq4zDWDhcQy_rQyv9mnxKv5K0Ugy9uwcEVTElNkjoQA`

### B. Gmail OAuth

1. In the Gmail node, click **Create New Credential**
2. Choose **Gmail OAuth2 API**
3. Authorize with `winnickidigital@gmail.com`

### C. Google Drive OAuth

1. In the Google Drive node (Workflow 2), click **Create New Credential**
2. Choose **Google Drive OAuth2 API**
3. Authorize with the same Google account

---

## Step 3: Verify Google Sheets Structure

Open your Google Sheet: https://docs.google.com/spreadsheets/d/1tq4zDWDhcQy_rQyv9mnxKv5K0Ugy9uwcEVTElNkjoQA/edit

### Required Column Headers (Row 1):

```
lead_id | email | first_name | last_name | company | website | phone | interested_in | additional_info | research_date | company_intelligence | contact_research | website_analysis | competitive_context | discovery_questions | anticipated_objections | status | call_date | call_notes | budget_discussed | budget_amount | timeline_preference | services_needed | pain_points | business_goals | priority_level | proposal_generated_date | proposal_url
```

**Critical:** The sheet must be named "Sheet1" (or update the workflow).

---

## Step 4: Activate Workflows

1. Open **Workflow 1: Pre-Call Research**
2. Click the toggle in the top right to **Activate**
3. Note the webhook URL (will look like: `https://n8n.srv943791.hstgr.cloud/webhook/winnicki-lead-intake`)
4. Repeat for **Workflow 2: Proposal Generation**
5. Note its webhook URL: `https://n8n.srv943791.hstgr.cloud/webhook/winnicki-post-call`

---

## Step 5: Test Workflow 1 (Pre-Call Research)

### Test Payload

Use this curl command or paste into Postman:

```bash
curl -X POST https://n8n.srv943791.hstgr.cloud/webhook/winnicki-lead-intake \
-H "Content-Type: application/json" \
-d '{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john.doe@acmecorp.com",
  "phone": "555-123-4567",
  "company_name": "Acme Corp",
  "website": "https://www.acme.com",
  "interested_in": "Website Development",
  "additional_info": "Looking for a modern website with e-commerce capabilities and better SEO"
}'
```

### Expected Results:

1. **Immediate response** (200 OK):
```json
{
  "success": true,
  "lead_id": "LEAD-20250114123045-A3F8D2",
  "message": "Pre-call research completed successfully"
}
```

2. **Within 1-2 minutes:**
   - New row in Google Sheets with all research populated
   - Email to winnickidigital@gmail.com with complete research summary

3. **Check Google Sheets:**
   - New row with lead data
   - All 6 agent outputs populated
   - Status: "Awaiting Call"

---

## Step 6: Test Workflow 2 (Proposal Generation)

### Test Payload

**Important:** Use the same email from Workflow 1 test so lookup works.

```bash
curl -X POST https://n8n.srv943791.hstgr.cloud/webhook/winnicki-post-call \
-H "Content-Type: application/json" \
-d '{
  "lead_email": "john.doe@acmecorp.com",
  "call_date": "2025-01-14",
  "call_notes": "Great call with John. Very interested in a complete website rebuild. Current site is outdated (built in 2018) and they are not ranking well in search. They want modern design, e-commerce, and better mobile experience. John mentioned they tried Wix before but found it limiting. Company is growing fast (30% YoY) and website needs to support that growth.",
  "budget_discussed": "Yes",
  "budget_amount": 5000,
  "timeline_preference": "ASAP, ideally launch in 4-6 weeks",
  "services_needed": ["Website Development", "E-commerce", "SEO", "Training"],
  "pain_points": "Current website is outdated, poor mobile experience, not ranking on Google, limited e-commerce functionality, no CRM integration, hard to update content",
  "business_goals": "Increase online sales by 50%, improve search rankings for key products, reduce customer support load through better self-service, integrate with existing Shopify backend",
  "priority_level": "High"
}'
```

### Expected Results:

1. **Immediate response** (200 OK):
```json
{
  "success": true,
  "company": "Acme Corp",
  "proposal_url": "https://drive.google.com/file/d/...",
  "message": "Proposal generated successfully"
}
```

2. **Within 2-3 minutes:**
   - Google Sheets row updated with call data
   - Proposal created in Google Drive
   - Email to Shannon with proposal link and summary
   - Status updated to "Proposal Sent"

3. **Check Results:**
   - Google Sheets: Updated with all call data + proposal URL
   - Google Drive: New proposal document
   - Email: Summary with Drive link

---

## Step 7: Connect to Your Lead Forms

### For Workflow 1 (Lead Intake):

Update your lead form webhook to point to:
```
https://n8n.srv943791.hstgr.cloud/webhook/winnicki-lead-intake
```

Form fields must map to these JSON keys:
- `first_name`
- `last_name`
- `email`
- `phone`
- `company_name`
- `website`
- `interested_in`
- `additional_info`

### For Workflow 2 (Post-Call):

Update your Wix discovery form webhook to:
```
https://n8n.srv943791.hstgr.cloud/webhook/winnicki-post-call
```

Form fields must map to these JSON keys:
- `lead_email` (CRITICAL: Must match email from Workflow 1)
- `call_date`
- `call_notes`
- `budget_discussed`
- `budget_amount`
- `timeline_preference`
- `services_needed` (array)
- `pain_points`
- `business_goals`
- `priority_level`

---

## Troubleshooting

### Workflow 1 Issues:

**Problem:** Agents timeout or fail
- **Solution:** Check Gemini API quota at https://console.cloud.google.com
- **Solution:** Verify API key is valid: `AIzaSyBycZecSHytgNdI6tM-EVeqMEBrEJ-m_Ls`

**Problem:** Google Sheets not updating
- **Solution:** Verify credential has write access
- **Solution:** Check column headers match exactly (case-sensitive)
- **Solution:** Ensure sheet is named "Sheet1"

**Problem:** Email not arriving
- **Solution:** Check Gmail OAuth is authorized
- **Solution:** Verify email address: winnickidigital@gmail.com
- **Solution:** Check spam folder

### Workflow 2 Issues:

**Problem:** "Lead not found" error
- **Solution:** Ensure `lead_email` in Workflow 2 matches `email` from Workflow 1
- **Solution:** Check Google Sheets has data from Workflow 1
- **Solution:** Verify email is exact match (case-sensitive)

**Problem:** Agents using incomplete data
- **Solution:** Verify Workflow 1 completed successfully first
- **Solution:** Check that all research fields are populated in Sheets

**Problem:** Google Drive file not created
- **Solution:** Check Google Drive OAuth credential
- **Solution:** Verify folder permissions
- **Solution:** Check n8n has write access to Drive

---

## Cost & Performance

### Expected Performance:

**Workflow 1:**
- Total time: 60-90 seconds
- Cost per run: ~$0.005 (Gemini API)
- 6 parallel API calls

**Workflow 2:**
- Total time: 90-120 seconds
- Cost per run: ~$0.008 (Gemini API)
- 4 sequential API calls

**Total per lead:** ~$0.013 per complete cycle

### Monitoring:

1. Check n8n execution logs: Workflows → [Workflow Name] → Executions
2. Monitor Gemini API usage: Google Cloud Console
3. Track costs: Review API usage weekly
4. Review quality: Read generated proposals and refine prompts

---

## Customization Options

### Adjust Agent Prompts:

To modify what agents focus on:
1. Open workflow in n8n
2. Find the HTTP Request node (e.g., "Agent 1: Company Intelligence")
3. Edit the `jsonBody` parameter
4. Modify the prompt text inside the "text" field
5. Save and test

### Change Email Format:

1. Open workflow
2. Find "Format Email" node (Workflow 1) or "Email Shannon" node (Workflow 2)
3. Edit the `email_body` assignment
4. Use HTML for formatting
5. Test with your email

### Add More Agents:

Workflow 1 (Parallel):
1. Duplicate an agent HTTP Request node
2. Update prompt for new research area
3. Connect to "Aggregate All Agents" node
4. Add new column to Google Sheets
5. Update "Save to Google Sheets" mapping

Workflow 2 (Sequential):
1. Duplicate an agent HTTP Request node
2. Insert in sequence between existing agents
3. Update prompts to reference previous agent outputs
4. Test thoroughly

---

## Production Checklist

Before going live:

- [ ] Both workflows imported successfully
- [ ] All OAuth credentials configured and working
- [ ] Google Sheets column headers match exactly
- [ ] Test Workflow 1 with sample data
- [ ] Verify email arrives with complete research
- [ ] Test Workflow 2 with sample call data
- [ ] Verify proposal generates and saves to Drive
- [ ] Check proposal quality and content
- [ ] Update lead form webhook to Workflow 1 URL
- [ ] Update Wix form webhook to Workflow 2 URL
- [ ] Set up error monitoring (optional)
- [ ] Document webhook URLs for Shannon
- [ ] Create backup of workflows (export JSON)

---

## Support

If you encounter issues:

1. Check n8n execution logs for detailed errors
2. Verify all credentials are properly authorized
3. Test individual nodes in isolation
4. Check Google Sheets data integrity
5. Verify webhook URLs are correct
6. Review Gemini API quotas and billing

---

**You're ready to deploy!** Start with a few test leads to verify everything works end-to-end before connecting production forms.
