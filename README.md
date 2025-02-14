# RSS Feed to Email Automation

A Python-based automation system that scrapes articles from an RSS feed and sends them via email using the Gmail API. 

## Features
- RSS feed parsing with HTML entity decoding
- Automated email formatting
- Gmail API integration
- Customizable feed URLs and email content

## Prerequisites
- Python 3.6+
- Google account
- RSS feed URL

## Setup Instructions
### 1. Install Dependencies
```
pip install --upgrade google-api-python-client google-auth-httplib2 google-auth-oauthlib feedparser
```
### 2. Generate Google API Credentials
#### Step 2.1: Create Google Cloud Project
- Go to [Google Cloud Console](https://console.cloud.google.com/)
- Create new project and Enable Gmail API
#### Step 2.2: Create OAuth Credentials
- Navigate to APIs & Services > Credentials
- Create OAuth 2.0 Client ID (Desktop App type)
- Download credentials as `credentials.json`
#### Step 2.3: Generate Token
- Run `quickstart.ipynb`
- Follow authentication flow in your browser
- New `token.json` will be created with API access
### 3. Configure RSS Scraper
#### 3.1 Open RSS_feed_scraping.ipynb
#### 3.2 Replace default RSS URL if needed
```
articles = scrape_rss_feed('http://example.com/rss')  # Replace with your feed
```
#### 3.3 Set recipient email
```
def send_email(..., to='your_email@example.com')
```

## Usage
Run RSS_feed_scraping.ipynb to
- Scrape latest articles
- Format into email
- Send via Gmail

## Applications
Daily Content Digests 
- Automate morning news updates
- Competitor Monitoring: Track industry blogs/RSS feeds
- Course Updates: Follow educational content feeds
- Podcast Updates: Get episode notifications via email
- Custom Newsletters: Create themed content compilations

## Customization Options
- Change email frequency (modify code to use scheduling)
- Add HTML Email Formatting: Use `MIMEText` with HTML formatting for richer emails.
- Add multiple RSS feed support

## Troubleshooting

| Error                          | Solution                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| **Insufficient Permissions**   | Regenerate `token.json` with the correct scopes.                         |
| **403 Access Denied**          | Add your email to the test users in the Google Cloud Console.            |
| **HTML Entities in Email**     | Ensure `html.unescape()` is used to decode HTML entities.                |
| **Feed Parse Errors**          | Verify the RSS feed URL is valid and accessible.                         |
