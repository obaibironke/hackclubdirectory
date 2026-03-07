# hackclubdirectory

Overview:

This is a directory that I created specifically for use in Hack Club. It has a database of Hack Club Programs, who to contact for them, and different aspects within them. I used AI to do all of the code because I can't code at all, but the rest is me. It has AI responses, a language feature, and Airtable integrations.

Set Up and Use:

As far as I know this can only be run using N8N which i used to build this. You need to make sure to have the slack bot credentials, (with correct scopes added) Airtable database wuth programs, aspects, and contacts, Airtable credentials, and AI API credentials.

Nodes:

1. Slack Trigger:
     Original input from user, contains question
2. Rate Limiter
     Prevents a single user from spamming the bot
3. If Rate High
     If rate is high goes to "Too many messages" reply node if not, continues as normal
4. Too many messages
     Returns message informing user that they are sending way to many messages
5. Check for inappropriate language
     Checks for profanity, sexual language, or self harm language in messages. If detected message is flagged and response is generated
6. If inappropriate language
     Checks if message was flagged for inappropriate language send to "No bad words" node which returns pre-determined response, if not continue as normal
7. No bad words
     Tells user that the bot can't continue with that kind of language
8. Search Programs
     Gets all programs in the Airtable
9. Search Aspects
      Gets all aspects in the Airtable
10. Combine programs and aspects
      Combines all information from the programs and aspects into one data table for the AI to use
11. Build Prompt
      Generates the AI prompt using the information recieved from previous nodes and outputs the prompt
12. Call LLM
      Calls the LLM and gives it the prompt from the previous node and then outputts a message based on the prompt
13. Format messages
      Formats the messages so that it can be returned to the user in a way that is presentable
14. Reply with answer
      The final node, it gives the user the contact information they requested

AI and Prompt Rules:

This workflow uses Gemini 2.5 Flash through the Hack Club AI API. The prompt for the AI is generated solely based on information from the database and it never makes up contacts. It never uses outside sources so the information is accurate.

Final notes:

This is still a work in progress and I am very open to suggestions if you have any please reach out to me (@Oba) on Slack. 

Licensing:

Business Source License 1.1

Licensor: Oba Ibironke

Licensed Work: Hack Club Directory Bot

Use Limitation: You may not use, copy, modify, merge, publish,
distribute, sublicense, or sell copies of the Licensed Work,
or use it as part of any product or service, without explicit
written permission from the Licensor.

To request permission, contact: @Oba on Slack

The source code is made available for viewing and educational
purposes only. All other rights are reserved.

Copyright (c) 2026 Oba Ibironke. All Rights Reserved.
