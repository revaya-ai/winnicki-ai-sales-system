# Winnicki AI Sales System - Quick Reference Card

## Shannon's Cheat Sheet

### System Overview

**What it does:**
1. When a lead fills out your form → Instant AI research → Email to you
2. After your discovery call → AI generates custom proposal → Email to you

**Cost:** ~$0.01 per lead (basically free)  
**Time saved:** 2-3 hours per proposal

---

## Workflow 1: When Lead Submits Form

### What Happens Automatically:

1. **Instant** - Lead form triggers research
2. **60-90 seconds** - AI researches:
   - Company background
   - Contact info
   - Website analysis
   - Competitive landscape
   - Suggested discovery questions
   - Likely objections

3. **Email arrives** with complete pre-call brief
4. **Google Sheet updated** with all research

### Your Action:
- Read the email summary
- Review discovery questions
- Schedule your call prepared!

---

## Workflow 2: After Discovery Call

### What You Do:

1. **Complete discovery call** with lead
2. **Fill out Wix form** with:
   - Lead's email (IMPORTANT: Must match original)
   - Call date
   - Your notes
   - Budget discussed
   - Services they need
   - Pain points
   - Business goals
   - Priority level (High/Medium/Low)

### What Happens Automatically:

1. **Instant** - Form triggers proposal generation
2. **90-120 seconds** - AI creates proposal with:
   - Solution design
   - Detailed pricing
   - Project timeline
   - Personalized narrative

3. **Google Drive** - Proposal saved automatically
4. **Email arrives** with:
   - Link to proposal
   - Quick summary
   - All call notes

5. **Google Sheet updated** with proposal link

### Your Action:
- Review proposal in Google Drive
- Make any edits needed
- Send to lead when ready

---

## Webhook URLs (For Forms)

### Lead Intake Form:
```
https://n8n.srv943791.hstgr.cloud/webhook/winnicki-lead-intake
```

### Post-Call Discovery Form:
```
https://n8n.srv943791.hstgr.cloud/webhook/winnicki-post-call
```

---

## Google Sheet Location

**All lead data:**  
https://docs.google.com/spreadsheets/d/1tq4zDWDhcQy_rQyv9mnxKv5K0Ugy9uwcEVTElNkjoQA/edit

**Status meanings:**
- "Awaiting Call" - Research done, call not yet scheduled
- "Proposal Sent" - Proposal generated and ready to send
- "Closed Won" - Deal closed (update manually)
- "Closed Lost" - Lead didn't convert (update manually)

---

## Troubleshooting

### "I didn't get the research email"
- Check spam folder
- Check Google Sheet - data might be there anyway
- Check n8n execution logs

### "Proposal failed to generate"
- Did you use the EXACT same email?
- Check if Workflow 1 completed first
- Look at n8n execution error message

### "Proposal quality is off"
- Review and edit in Google Drive before sending
- Send feedback on what to improve
- We can refine the AI prompts

### "Need to regenerate proposal"
- Just resubmit the Wix discovery form
- System will overwrite previous proposal
- Google Sheet will update with latest version

---

## Best Practices

### Before the Call:
✅ Read the pre-call research email thoroughly  
✅ Review discovery questions  
✅ Note anticipated objections  
✅ Check their website yourself  

### During the Call:
✅ Take detailed notes in your own words  
✅ Confirm budget expectations  
✅ Get specific about timeline  
✅ Ask about decision process  

### After the Call:
✅ Fill out Wix form immediately while fresh  
✅ Be specific about pain points  
✅ Note exact services discussed  
✅ Set priority level accurately  

### Before Sending Proposal:
✅ Review AI-generated proposal  
✅ Personalize opening if needed  
✅ Verify pricing is correct  
✅ Check timeline is realistic  
✅ Add any call-specific details  

---

## Key Reminders

**The system works best when:**
- You provide detailed call notes
- You capture specific pain points
- You set realistic priority levels
- You review proposals before sending

**The system saves time on:**
- Company research
- Competitive analysis
- Pricing calculations
- Timeline planning
- Proposal writing
- Data organization

**You still own:**
- Building rapport on calls
- Final proposal review
- Client relationships
- Follow-up strategy
- Deal closing

---

## Emergency Contacts

**n8n Dashboard:**  
https://n8n.srv943791.hstgr.cloud/

**Google Sheet:**  
https://docs.google.com/spreadsheets/d/1tq4zDWDhcQy_rQyv9mnxKv5K0Ugy9uwcEVTElNkjoQA/edit

**Your Email:**  
winnickidigital@gmail.com

**System Status:**  
Check n8n dashboard → Workflows → View Executions

---

## Quick Wins

**Week 1:** Test with 2-3 leads, refine prompts  
**Week 2:** Process 5-10 leads, measure time saved  
**Week 3:** Full production, track conversion rates  
**Month 1:** Review proposal quality and close rates  

**Target Metrics:**
- Research time: <2 minutes (vs 30+ minutes manual)
- Proposal time: <3 minutes (vs 2-3 hours manual)
- Proposal quality: High enough to send with minimal edits
- Time savings: 2+ hours per qualified lead

---

**You've got this!** The AI does the heavy lifting. You focus on building relationships and closing deals.
