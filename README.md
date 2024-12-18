# htaccess Redirect Generator

A simple web-based tool to generate Apache htaccess redirects from a CSV file. Created by Abe Rubarts at Locus Digital.

## Features

- Upload CSV with "Old Path" and "New Path" columns
- Automatically strips domain and protocol from old paths
- Properly escapes special characters for htaccess rules
- Generates correctly formatted RewriteRule directives
- Includes RewriteCond statements for both www and non-www domains
- One-click copy to clipboard functionality

## Usage

1. Open `index.html` in your web browser
2. Upload your CSV file containing:
   - "Old Path" column: Original URLs or paths
   - "New Path" column: Destination URLs or paths
3. Click "Generate Redirects"
4. Use the "Copy to Clipboard" button to copy the generated rules
5. Paste the rules into your .htaccess file

## Generated Rules Format

The tool generates rules in the following format:

```apache
RewriteEngine on

# Redirect root domain
RewriteCond %{HTTP_HOST} ^shop\.govirtualoffice\.com$ [OR]
RewriteCond %{HTTP_HOST} ^www\.shop\.govirtualoffice\.com$
RewriteRule ^/?$ "https://govirtualoffice.com/" [R=301,L]

# Redirect for example-path
RewriteCond %{HTTP_HOST} ^shop\.govirtualoffice\.com$ [OR]
RewriteCond %{HTTP_HOST} ^www\.shop\.govirtualoffice\.com$
RewriteRule ^example\-path$ "https://govirtualoffice.com/new-path/" [R=301,L]
```

## Features

- Handles both www and non-www domains
- Includes proper escaping of special characters
- Adds [R=301,L] flags for permanent redirects
- Formats paths correctly by removing leading/trailing slashes
- Strips domain and protocol from old paths to match server paths

## Creator

Created by Abe Rubarts at Locus Digital