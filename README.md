# Dinmo Tag (Server-side)

The Dinmo Tag processes incoming GA4 requests and stores the data in BigQuery.

## How does the script work?

The script processes event data in the following steps:

1. **Data Extraction:** Reads event data received from the tagging server.
2. **Transformation:** Filters, transforms, and maps the data into a predefined schema compatible with BigQuery.
3. **Enrichment:** Adds user metadata, query parameters, and additional fields for enriched analytics.
4. **Insertion:** Inserts the transformed data into BigQuery table.

It includes:
- Filtering of unwanted parameters.
- Support for GA4 event fields.
- Automatic handling of nested fields such as `items`.

## Implementation

### Prerequisites

- A Google Cloud project with BigQuery enabled.
- A BigQuery dataset created in your project.
- A BigQuery table set up using the `table.json` file from this github repository.
- Correct permissions assigned to your provided service account email (BigQuery Write permissions).
- A properly configured GTM server-side tagging environment.

### Setup

1. Add the template.tpl to your server-side GTM container.
2. Configure the following fields in the script:
   - `bqProjectId`: Your Google Cloud Project ID.
   - `bqDatasetId`: The BigQuery dataset name.
   - `bqTableId`: The BigQuery table name.
3. Set optional fields such as excluded parameters (`excludeParams`) and update parameters (`updateParams`).
4. Deploy the container to your server.

## Features

- **Data Transformation:** Automatically maps GA4 fields to BigQuery-compatible fields.
- **Field Filtering:** Excludes unnecessary or sensitive fields using `excludeParams`.
- **Enrichment:** Adds query parameters and user properties to event data.
- **Error Logging:** Logs errors and success messages for easy debugging.

## How to Verify Data

To ensure that the integration works as expected:

1. Check logs in the GTM server-side container for successful and failed events.
2. Query your BigQuery table to verify the inserted data.

## Reporting Bugs/Feedback

Encountered an issue or have feedback? Please report bugs via GitHub or contact us directly at support@addingwell.com.

## Open Source

The Dinmo tag for GTM Server-Side is developed and maintained by [Addingwell](https://www.addingwell.com/) under the Apache 2.0 license.
