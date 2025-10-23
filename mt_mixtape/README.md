# MT Mixtape — n8n Workflow

_Automate your team's weekly music discovery, powered by AI, Notion, Spotify, and Telegram._

---

## About Madara’s Automation Library

Madara’s Automation Library delivers reusable, production-tested n8n workflows for teams who want to work smarter, not harder. Built by [Madara Knutina](mailto:madara.knutina@gmail.com), these automations are designed for clarity, reusability, and real-world impact. If you’re a solopreneur, small team, NGO, or operator, this library helps you save hours and focus on what matters.

---

## MT Mixtape: What Does This Workflow Do?

**MT Mixtape** is a plug-and-play n8n workflow that automates the process of:

- Collecting music artist and song suggestions from your team via Telegram
- Enriching submissions with AI (artist bios, genres, key songs)
- Managing a collaborative artist database in Notion
- Adding songs directly to a shared Spotify playlist
- Running a weekly artist selection and review cycle
- Gathering ratings and stats, and sharing them back to the group

**Who is it for?**
- Teams, clubs, or friend groups who want a fun, low-effort way to discover new music together
- Operators who want to automate group curation and reduce manual admin
- Anyone who wants to combine AI, Notion, Telegram, and Spotify in a seamless workflow

**Problems Solved:**
- No more scattered music suggestions — everything is tracked, enriched, and organized
- No manual copy-paste between chat, Notion, and Spotify
- Everyone participates, votes, and rates, with zero admin overhead
- Stats and progress are always visible

---

## Features at a Glance

- ⚡ **Telegram Bot**: Accepts `/artist`, `/song`, `/next`, `/done`, `/stats` commands
- 🤖 **AI Enrichment**: Uses GPT-4 to clean up submissions, fix typos, and add context
- 🛠 **Integrations**: Notion (artist DB), Spotify (playlist), Telegram (chat)
- 🔄 **Weekly Cycle**: Picks a new artist, collects ratings, and updates status
- 📊 **Stats**: Shares group progress and top genres/artists on demand

---

## How It Works (Walkthrough)

### 1. Suggest an Artist or Song
- Team members send `/artist [name]` or `/song [title]` in the Telegram group.
- The workflow extracts the artist/song, cleans up the input, and enriches it with AI (bio, genres, key songs).
- If it's a song, it’s added to the shared Spotify playlist. Optionally, the artist can be added to the Notion DB.

### 2. Queue Management
- Each new artist is checked for duplicates in Notion.
- If new, it’s added to the "Queue" with all AI-enriched info and submitter details.
- If already exists, the bot notifies the user.

### 3. Weekly Artist Selection
- On `/next`, the bot picks the next queued artist and posts their info in Telegram.
- The group can approve or shuffle for a new pick.
- Once approved, the artist status is set to "Current".

### 4. Review and Rating
- After a week, `/done` triggers a rating form in Telegram.
- Ratings are stored in Notion, and the artist is marked as "Completed".
- The bot prompts the group to pick the next artist.

### 5. Stats and Progress
- `/stats` command shares:
  - Total artists
  - Weeks completed
  - Average rating
  - Most explored genres
  - Highest-rated artists
  - Link to the full Notion artist list

---

## Quickstart Tutorial

### Prerequisites
- n8n instance (self-hosted or cloud)
- Telegram bot token
- Notion integration (API key, DB set up)
- Spotify developer account (OAuth credentials)

### Setup Steps
1. **Import the Workflow** into n8n.
2. **Configure Credentials**:
   - Telegram: Add your bot token
   - Notion: Connect your Notion integration and select your artist DB
   - Spotify: Set up OAuth2 credentials
3. **Set Webhooks**: Ensure your Telegram bot is set up to receive messages from your group.
4. **Customize Notion DB**: Make sure your DB has fields for Artist Name, Genre, Key Songs, Summary, Submitted By, Status, Rating, Featured Song (URL).
5. **Test**: Send `/artist [name]` or `/song [title]` in your Telegram group. Watch the workflow run and check Notion/Spotify for updates.
6. **Go Live**: Share `/next`, `/done`, and `/stats` commands with your group.

---

## Example Usage

- `/artist Joni Mitchell shared by MJ` → Adds Joni Mitchell to Notion with AI-generated summary, genres, and submitter info.
- `/song Bohemian Rhapsody by Queen` → Adds the song to Spotify playlist, then asks if you want to add Queen as an artist.
- `/next` → Picks the next artist in the queue, posts details in Telegram, and waits for approval.
- `/done` → Collects group rating for the current artist.
- `/stats` → Shares group progress and stats in Telegram.

---

## Workflow Diagram

Telegram Trigger ⚡
   └── Switch: Which command?
        ├─ /artist → AI Agent → Notion DB (check/add) → Telegram reply
        ├─ /song → AI Agent → Spotify add → Telegram confirm → (optional) Notion add
        ├─ /next → Notion (pick next) → Telegram approval → Notion update
        ├─ /done → Notion (current) → Telegram rating form → Notion update → Telegram next prompt
        └─ /stats → Notion (stats) → Telegram summary

---

## Customization & Tips

- **Change Playlist**: Update the Spotify playlist ID in the workflow.
- **Expand Notion DB**: Add more fields (e.g., links, notes) as needed.
- **Restrict Access**: Use the Filter node to limit who can submit commands.
- **AI Model**: Swap GPT-4 for another model if desired.
- **Notifications**: Add more Telegram messages for reminders or milestones.

---

## Limitations

- Requires all integrations to be set up and connected (Telegram, Notion, Spotify, OpenAI)
- AI may occasionally misinterpret ambiguous submissions
- Notion DB schema must match workflow expectations
- Designed for small/medium groups (not public bots)

---

## Support & Contact

**Author:** Madara Knutina  
**Email:** madara.knutina@gmail.com  
**LinkedIn:** [linkedin.com/in/madaraknutina](https://www.linkedin.com/in/madaraknutina/)

Need help or want customizations? Reach out for consulting or support.

---

*Automation you can actually reuse — for operators, NGOs, and founders needing leverage without headcount.*
