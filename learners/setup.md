---
title: Setup
---

# Setup

## Before the Workshop

### System Requirements

You need:

- **Web browser**: Chrome, Firefox, Edge, or Safari (recent version recommended - updated within last 6 months)
- **Internet connection**: Stable, broadband recommended (minimum 2 Mbps for file uploads)
- **Pomona College account**: Active @pomona.edu email and password
- **DUO Multi-Factor Authentication**: Either mobile app or phone number for SMS codes
- **No SSH needed!** OnDemand is entirely web-based

### Browser Compatibility

OnDemand works best on:
- Chrome/Chromium (version 90+)
- Firefox (version 88+)
- Safari (version 14+)
- Edge (version 90+)

If you experience issues, try a different browser.

### Preparing Your Computer

1. **Update your browser** to the latest version
   - Click Help menu → About [Browser Name]
   - It will automatically update if available

2. **Test your internet connection**
   - OnDemand requires stable connection
   - Upload and download speeds matter for file transfers
   - Contact your IT if you have slow/unstable WiFi

3. **Have your Pomona credentials ready** (username and password)
   - You'll use these to log into OnDemand
   - Example username: alice (not alice@pomona.edu)

4. **Set up DUO MFA** if not already done:
   - Go to https://duo.pomona.edu
   - Log in with Pomona username and password
   - Follow DUO setup instructions
   - Choose: Download Duo Mobile app OR register phone number for SMS
   - Recommended: Use Duo Mobile app for most reliable authentication

### What is OnDemand?

OnDemand is a **web-based interface to HPC resources**. You get:
- File management (upload, download, organize)
- Interactive applications (Jupyter notebooks, RStudio)
- Job submission and monitoring
- Web terminal (if you need command-line access)
- No need to learn SSH or install special software

OnDemand runs on **Sagehen HPC cluster** at Pomona College. All your regular HPC storage and jobs are accessible through the web interface.

### Accessing OnDemand

1. Open your web browser
2. Navigate to: **https://ondemand.hpc.pomona.edu/**
3. You should see a login screen titled "Sagehen OnDemand Portal"
4. Enter your Pomona credentials
5. Complete DUO authentication
6. You'll see the OnDemand dashboard

If you see an error:
- Check that URL is correct (note the "s" in https)
- Clear browser cache (Ctrl+Shift+Delete or Cmd+Shift+Delete)
- Try a different browser
- Check internet connection

### Test Your Access Before Workshop

Complete this checklist before the workshop to ensure everything works:

- [ ] Successfully log into OnDemand
- [ ] See the main dashboard (Files, Jobs, Apps menu)
- [ ] Can access Files → Home Directory
- [ ] Can access Interactive Apps → Web Terminal
- [ ] DUO authentication completes quickly
- [ ] Dashboard loads within 5 seconds

If any item is unchecked, troubleshoot before the workshop (see Troubleshooting section below).

## What to Bring

- **Working laptop or desktop computer** (not just a tablet)
- **Notes or questions** about your research data or computing needs
- **Sample files to practice uploading** (optional, 1-100 MB)
- **Questions!** This is an interactive workshop

## Pre-Workshop Checklist

::::::::::::::::::::::::::::::::::: checklist

### Account & Authentication
- [ ] I have an active Pomona (@pomona.edu) email account
- [ ] I know my Pomona username (the part before @pomona.edu)
- [ ] I've set up or can access my DUO account
- [ ] I can log into Pomona email or Canvas successfully

### Browser & Computer
- [ ] My web browser is updated (within last 6 months)
- [ ] My computer has reliable internet connection
- [ ] I've tested OnDemand access at least once
- [ ] I can access OnDemand dashboard

### HPC Account
- [ ] I have an HPC account on Sagehen (ask its-hpc@pomona.edu if unsure)
- [ ] My account is active (not suspended)
- [ ] I know my Pomona username for OnDemand login

:::::::::::::::::::::::::::::::::::

## Troubleshooting Pre-Workshop

| Problem | Solution |
|---------|----------|
| "Authentication failed" | Verify Pomona username (not email). Try password reset at https://duo.pomona.edu |
| DUO request appears but I don't approve it | Deny the request. Try logging in again. If repeated denials, contact its-hpc@pomona.edu |
| Browser shows "Connection refused" or similar | Check internet connection. Try different browser. Clear cache (Ctrl+Shift+Delete) |
| "Connection timed out" | Try again later. OnDemand may be under maintenance. Check https://www.pomona.edu/its/ for status |
| OnDemand loads but is very slow | This is normal during peak hours (9am-5pm weekdays). Try again in evening or early morning |
| Can't find OnDemand URL or it's blocked | Contact your network admin if on institutional network. You may need VPN if off-campus |

## Getting Help Before the Workshop

If you encounter issues:

- **Account/Pomona credentials**: Contact ITS Help Desk (see directory)
- **DUO setup or problems**: Contact ITS Help Desk
- **OnDemand access issues**: Email its-hpc@pomona.edu
- **No HPC account yet**: Email its-hpc@pomona.edu to request one

Include in your email:
- What you're trying to do
- What error message you see (screenshot helpful)
- When it happens
- What you've already tried

## Notes for This Workshop

- **Duration**: about 3.5 hours
- **Level**: No prior HPC or command-line experience needed
- **Format**: Interactive hands-on with live demonstrations
- **Outcome**: You'll be comfortable using OnDemand for file management, running interactive applications, and submitting jobs

## Questions Before Starting?

Email: its-hpc@pomona.edu
Instructor: Consult workshop schedule
Documentation: https://www.pomona.edu/its/

Welcome to the workshop!
