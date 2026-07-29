# AI News Automation with n8n

## Overview

This project is an automated news content generation workflow built using n8n.

The workflow collects article data, extracts metadata and images, uses an AI model to generate factual summaries and social media captions, then formats the output as structured JSON.

## Workflow

The automation process:

1. Fetch news article data from RSS/API source
2. Parse article URL and retrieve webpage metadata
3. Extract:
   - Article title
   - Source
   - Publication date
   - Description
   - Image URL
4. Send article information to AI model
5. Generate:
   - 2 sentence factual summary
   - Social media caption
   - Relevant hashtags
6. Format the output for further publishing


## Tools Used

- n8n
- OpenAI API
- RSS Feed
- JavaScript Function Node


## AI Prompt

The prompt used for article summarization is available in:

`prompts/article-summary-prompt.txt`


## Challenges

During development, I encountered several issues:

1. The AI sometimes repeated the article title inside the summary.
   
   Solution:
   I modified the prompt by explicitly separating the article title as a headline and forcing the summary to use only information from the article content.

2. Some article titles contained the publisher name, for example:
   
   "Article Title | News Source"

   Solution:
   I added a JavaScript cleaning step to remove unnecessary source text from the title field.

3. Different websites had different metadata structures.

   Solution:
   I created a fallback extraction system using Open Graph metadata such as:
   - og:image
   - og:description
   - og:site_name


## Future Improvements

Possible improvements:

- Add article quality filtering
- Add duplicate article detection
- Add database storage for generated content
