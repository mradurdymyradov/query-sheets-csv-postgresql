# Query Google Sheets/CSV Data via AI Agent using PostgreSQL

This repository contains an n8n workflow that demonstrates how to integrate Google Sheets or CSV data into a PostgreSQL database and query it using natural language via an AI agent. The workflow orchestrates data ingestion, persistence and an AI-powered query layer to make your tabular data accessible through human friendly questions.

## Features

- **Data Ingestion**: Extracts rows from a Google Sheets spreadsheet or uploads a CSV file and loads the data into a PostgreSQL table.
- **AI Powered Queries**: Exposes an HTTP endpoint where you can ask questions in plain English. An AI agent translates the question into SQL, runs it against PostgreSQL and returns a concise answer.
- **Extensible Workflow**: Uses modular nodes for ingestion, SQL execution and AI summarisation so you can adapt the flow to your own data sources or prompt templates.
- **Credential Management**: Uses n8n’s credential system to store Google and database credentials securely.

## Getting Started

1. **Prerequisites**

   - An [n8n](https://n8n.io/) instance (self‑hosted or cloud).
   - A PostgreSQL database you control.
   - Google service account credentials with access to the spreadsheet (if using Google Sheets).
   - An API key for your AI provider (e.g. OpenAI) to translate questions into SQL.

2. **Import the Workflow**

   - Download the `Query Google SheetsCSV data through an AI Agent using PostgreSQL.json` file in this repository.
   - In the n8n UI, click **Import workflow** and upload the JSON file.

3. **Configure Credentials**

   - Set up a new PostgreSQL credential in n8n and point it at your database.
   - Create Google Sheets credentials if you plan to pull data from Sheets.
   - Add your AI provider API key in the corresponding credential node.

4. **Ingest Data**

   - If using Google Sheets, specify the spreadsheet ID and worksheet name in the relevant node.
   - To load a CSV file, place it where n8n can access it (e.g. via the File Trigger node).
   - Run the ingestion nodes to populate your Postgres table.

5. **Query via AI**

   - Send a POST request to the HTTP endpoint exposed by the workflow with a JSON body containing your natural language question.
   - The AI agent will translate the question, execute the generated SQL and return the answer.

## Customisation

- Change the prompt used by the AI agent to influence the SQL generation.
- Modify the database schema or add indexes to optimise performance for your queries.
- Add additional data sources (e.g. API responses) by connecting new nodes upstream of the Postgres insert.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
