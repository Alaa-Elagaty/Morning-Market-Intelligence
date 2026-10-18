# Morning Market Intelligence

An n8n workflow that collects AI-related news from RSS feeds, filters stories by keywords and publication date, and sends a daily digest to Telegram.

## Overview

Morning Market Intelligence automates the process of keeping up with AI industry news. Instead of checking multiple sources manually, the workflow gathers recent articles, selects stories matching configured keywords, and delivers a concise list of headlines and links.

The workflow is designed to run automatically every morning at 7:00 AM, using the timezone configured in n8n.

## Features

- **Scheduled execution:** Runs daily using an n8n Schedule Trigger.
- **Multiple RSS sources:** Collects articles from three configured feeds.
- **Keyword filtering:** Selects articles whose titles match configured keywords.
- **Date filtering:** Excludes articles outside the configured age limit.
- **Latest-first ordering:** Sorts matching stories by publication date.
- **Configurable output:** Limits the number of stories included in the digest.
- **Telegram delivery:** Sends selected headlines and article links as a formatted message.

## Workflow

1. **Schedule Trigger** — Starts the workflow every morning at 7:00 AM.
2. **Search News** — Defines the RSS sources, keywords, date limit, and maximum number of stories.
3. **Split Out** — Separates the RSS feed URLs for individual processing.
4. **RSS Read** — Retrieves articles from each feed.
5. **Clean News** — Standardizes article titles, links, publication dates, and matching keywords.
6. **Filter** — Keeps articles that satisfy the configured date and keyword conditions.
7. **Sort** — Orders the selected articles by publication date.
8. **Limit** — Restricts the results to the configured maximum number of stories.
9. **Aggregate** — Combines the selected articles into a single collection.
10. **Telegram** — Formats and sends the daily digest.

## RSS Sources

| Source | Feed |
| --- | --- |
| AI Central Tools | https://aicentraltools.com/news/feed/ |
| Hacker News | https://hnrss.org/newest?q=AI |
| TechCrunch | https://techcrunch.com/category/artificial-intelligence/feed/ |

Feed availability and article formats may change over time.

## Configuration

The workflow's **Search News** node contains the main configuration values.

| Setting | Value | Purpose |
| --- | --- | --- |
| Schedule | 7:00 AM daily | Defines when the workflow runs |
| Maximum stories | 5 | Limits the number of articles |
| Date window | 4 days | Sets the maximum article age |
| Keywords | `llm`, `Openai`, `machine learning`, `agent`, `google`, `startup`, `model` | Selects relevant headlines |
| Delivery | Telegram | Sends the final digest |

These values can be modified to match your preferred news sources and topics.

**Note:** Keyword matching is performed against article titles. Matching a keyword does not guarantee that an article contains substantive AI news.

## Requirements

- An n8n instance with the required workflow nodes available.
- Internet access to retrieve the configured RSS feeds.
- Telegram bot credentials configured in n8n.
- A valid Telegram chat ID for the intended recipient.

## Installation

### 1. Download the workflow

Download [`Morning Market Intelligence.json`](./Morning%20Market%20Intelligence.json) from this repository.

### 2. Import into n8n

1. Open your n8n instance.
2. Create a new workflow or open the workflow import option.
3. Import the downloaded JSON file.
4. Review the imported nodes and their connections.

### 3. Configure Telegram

1. Open the Telegram node.
2. Configure your Telegram bot credentials.
3. Set the destination chat ID.
4. Ensure the bot has permission to send messages to the destination.

### 4. Review the workflow settings

Check the RSS URLs, keyword list, date window, maximum story count, and schedule.

Confirm the timezone configured in n8n before enabling the schedule.

### 5. Test and activate

1. Run the workflow manually.
2. Verify that the RSS feeds return articles.
3. Check the filtering, sorting, and aggregation steps.
4. Confirm that Telegram receives the formatted digest.
5. Activate the workflow after successful testing.

## Example Output

**AI News - [Date]**

1. [Article title]  
   [Article link]

2. [Article title]  
   [Article link]

The actual articles depend on the RSS sources, publication dates, keyword matches, and configured story limit.

## Limitations

- Results depend on the availability and quality of the configured RSS feeds.
- Title-based keyword matching may miss relevant articles.
- Matching headlines does not guarantee relevance or accuracy.
- The workflow does not currently demonstrate AI-generated summaries, sentiment analysis, financial forecasting, or investment recommendations.
- Telegram delivery requires valid credentials and a correctly configured destination.
- The workflow should be tested after changes to feed URLs, n8n versions, or node settings.

## Security

Before sharing or deploying the workflow:

- Review the exported JSON for personal information, recipient details, and chat IDs.
- Store credentials securely using n8n's credential management.
- Never commit bot tokens, passwords, or API keys to a public repository.

## Author

**Alaa Elagaty**

[GitHub Profile](https://github.com/Alaa-Elagaty)

## License

No license is currently specified. Unless a license is added, others should not assume they have permission to reuse, modify, or redistribute this project.
