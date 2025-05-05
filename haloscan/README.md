# Haloscan MCP Server

A Model Context Protocol (MCP) server for interacting with the Haloscan SEO API.  
This server allows easy integration with Claude for Desktop, N8N, and other MCP-compatible clients.

---

## Features

- Exposes Haloscan SEO API functionality through MCP tools
- Provides prompts for common SEO tasks
- Easy integration with workflow automation tools like N8N

---

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/mcp-haloscan-server.git
cd mcp-haloscan-server

# Install dependencies
npm install

# Build the project
npm run build
```

## API

### Tools

#### 1. User Tools

  - **get_user_credit**<br>
    ∘ Retrieves the remaining credit for the user identified by the provided API key.<br>
    ∘ 

#### 2. Keyword Explorer Tools
  - **get_keywords_overview**<br>
    ∘ Retrieves the remaining credit for the user identified by the provided API key.<br>
    ∘ Inputs:<br>
        ▪ `keyword` (string): Requested keyword.<br>
        ▪ `requested_data` (string[]): Any combination of [keyword_match, related_search, related_question, similar_category, similar_serp, top_sites, similar_highlight, categories, synonyms, metrics, volume_history, serp ].<br>

  - **get_keywords_match**<br>
    ∘ Retrieves the remaining credit for the user identified by the provided API key.<br>
    ∘ Input:<br>
        ▪ `keyword` (string): Requested keyword.<br>

  - **get_keywords_similar**<br>
    ∘ Retrieves the list of keywords that are semantically or topically similar to a given keyword.<br>
    ∘ Input:<br>
        ▪ `keyword` (string): Requested keyword.<br>

  - **get_keywords_highlights**<br>
    ∘ Retrieves the key performance highlights from a given keyword.<br>
    ∘ Input:<br>
        ▪ `keyword` (string): Requested keyword.<br>

  - **get_keywords_related**<br>
    ∘ Retrieves the list of keywords that are contextually or topically related to a given keyword.<br>
    ∘ Input:<br>
        ▪ `keyword` (string): Requested keyword.<br>

  - **get_keywords_questions**<br>
    ∘ Retrieves a list of question-based keywords related to a given keyword.<br>
    ∘ Input:<br>
        ▪ `keyword` (string): Requested keyword.<br>

  - **get_keywords_synonyms**<br>
    ∘ Retrieves a list of synonyms related to a given keyword.<br>
    ∘ Input:<br>
        ▪ `keyword` (string): Requested keyword.<br>

  - **get_keywords_find**<br>
    ∘ Retrieves comprehensive data for a given keyword or list of keywords, including search volume, competition, and trend analysis.<br>
    ∘ Inputs:<br>
        ▪ `keyword` (string): Requested keyword.<br>
        ▪ `keywords` (string[]): Requested keywords.<br>
        ▪ `keywords_sources` (string): Which strategies to use to find keywords from input (Any combination of [match, serp, related, highlights, categories, questions]).<br>

  - **get_keywords_site_structure**<br>
    ∘ Retrieves the remaining credit for the user identified by the provided API key.<br>
    ∘ Input:<br> 
        ▪ `keyword` (string): Requested keyword.<br>

  - **get_keywords_serp_compare**<br>
    ∘ Retrieves the remaining credit for the user identified by the provided API key.<br>
    ∘ Inputs:<br>
        ▪ `keyword` (string): Requested keyword.<br>
        ▪ `period` (string): The comparison period for SERPs (1 month, 3 months, 6 months, 12 months, custom).<br>

  - **get_keywords_serp_availableDates**<br>
    ∘ Retrieves the remaining credit for the user identified by the provided API key.<br>
    ∘ Input:<br> 
        ▪ `keyword` (string): Requested keyword.<br>

  - **get_keywords_serp_pageEvolution**<br>
    ∘ Retrieves the remaining credit for the user identified by the provided API key.<br>
    ∘ Inputs:<br>
        ▪ `keyword` (string): Requested keyword.<br>
        ▪ `first_date` (string): Date in YYYY-MM-DD format.<br>
        ▪ `second_date` (string): Date in YYYY-MM-DD format.<br>
        ▪ `url` (string)<br>

  - **get_keywords_bulk**<br>
    ∘ Retrieves the remaining credit for the user identified by the provided API key.<br>
    ∘ Input:<br> 
        ▪ `keywords` (string[]): Array containing the requested keywords.<br>

  - **get_keywords_scrap**<br>
    ∘ Retrieves the remaining credit for the user identified by the provided API key.<br>
    ∘ Input:<br>
        ▪ `keywords` (string[]): Array containing the requested keywords.<br>

---

## Usage with Claude Desktop

Add this to your `claude_desktop_config.json`:

### NPX

{
  "mcpServers": {
    "haloscan": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/haloscan-server",
        "start"  
      ],
      "env": {
        "NODE_ENV": "production",
        "HALOSCAN_API_KEY": "haloscan_api_key"
      }
    }
  }
}


Usage
Environment Variables
Set your Haloscan API key as an environment variable:
bashexport HALOSCAN_API_KEY=your_api_key_here
Alternatively, you can use the set_api_key tool to set it programmatically.
Running the Server
bashnpm start
Using with Claude Desktop
Add this server to your Claude Desktop configuration at ~/Library/Application Support/Claude/claude_desktop_config.json (macOS) or %APPDATA%\Claude\claude_desktop_config.json (Windows):
json{
  "mcpServers": {
    "haloscan": {
      "command": "node",
      "args": ["/absolute/path/to/mcp-haloscan-server/build/index.js"],
      "env": {
        "HALOSCAN_API_KEY": "your_api_key_here"
      }
    }
  }
}
Using with N8N

Install the MCP N8N node
Configure it to point to your running MCP Haloscan server
Use the exposed tools in your workflows

Available Tools
ToolDescriptionset_api_keySet the Haloscan API key programmaticallyanalyze_urlAnalyze a URL for SEO insightskeyword_suggestionsGet keyword suggestions related to a seed keywordkeyword_difficultyCheck the difficulty score for specific keywordsbacklink_dataGet backlink data for a specified domaindomain_metricsGet SEO metrics for a specified domainserp_rankingsGet SERP rankings for a domain and keywordscontent_analysisAnalyze content for SEO optimizationcompetitor_analysisAnalyze competitors for a specific domain
Available Prompts
PromptDescriptionseo_auditGenerate an SEO audit for a websitekeyword_researchConduct keyword research for a topiccontent_optimizationGet content optimization suggestions
Examples
Analyze a URL
Use the analyze_url tool to check SEO issues for example.com
Get Keyword Suggestions
Use the keyword_suggestions tool to find keywords related to "organic gardening"
Content Optimization
Use the content_optimization prompt to optimize this content for the keyword "best running shoes"
Development
To start the server in development mode:
bashnpm run dev
License
MIT
