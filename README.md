# Email API

A simple email API built with Node.js and Nodemailer, deployed on Vercel. This API supports sending emails in HTML or plain text formats, with options for BCC, CC, and attachments.

## Features

- **Send Emails**: Supports both plain text and HTML email formats.
- **BCC and CC**: Includes options for BCC and CC recipients.
- **Attachments**: Allows attaching files to the email.
- **Cross-Origin Resource Sharing (CORS)**: Configured to handle requests from different origins.

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- A Gmail account for sending emails
- Vercel CLI for deployment

### Installation

1. **Clone the Repository**

   ```bash
   git clone https://github.com/your-username/email-api.git
   cd email-api
   ```

2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Setup Environment Variables**

   Create a `.env` file in the root of your project and add your Gmail credentials:

   ```env
   GMAIL_USER=your-email@gmail.com
   GMAIL_PASS=your-app-password
   ```

### Running Locally

To run the API locally:

1. **Start the Development Server**

   ```bash
   npm run dev
   ```

2. **Test the API**

   Use a tool like Postman or cURL to send a POST request to `http://localhost:3000/api/send-email` with the required fields.

### Deployment

Deploy the API to Vercel:

1. **Install Vercel CLI**

   ```bash
   npm install -g vercel
   ```

2. **Deploy the Project**

   ```bash
   vercel
   ```

3. **Set Environment Variables on Vercel**

   Go to your Vercel dashboard, navigate to your project, and set the environment variables:

   - `GMAIL_USER` = `your-email@gmail.com`
   - `GMAIL_PASS` = `your-app-password`

## API Usage

### Endpoint

`POST /api/send-email`

### Request Body

- `to` (string, required): Recipient email address.
- `cc` (string, optional): CC email address.
- `bcc` (string, optional): BCC email address.
- `subject` (string, required): Subject of the email.
- `message` (string, required): Content of the email.
- `isHtml` (boolean, optional): Set to `true` for HTML content, `false` for plain text. Default is `false`.
- `attachments` (array of objects, optional): List of attachment objects with `path` property. Example: `[ { "path": "http://example.com/file.pdf" } ]`.

### Example Request

**cURL:**

```bash
curl -X POST https://your-deployment-url.vercel.app/api/send-email \
-H "Content-Type: application/json" \
-d '{
    "to": "recipient@example.com",
    "cc": "cc@example.com",
    "bcc": "bcc@example.com",
    "subject": "Test Email",
    "message": "<h1>This is an HTML email</h1>",
    "isHtml": true,
    "attachments": [{ "path": "http://example.com/file.pdf" }]
}'
```

### Response

- **Success**: Returns `{ "success": "Email sent successfully" }`
- **Failure**: Returns `{ "error": "Error message" }`

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes. For major changes, please open an issue first to discuss what you would like to change.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For any questions or feedback, please reach out to [litnitimounsef@gmail.com](mailto:litnitimounsef@gmail.com).
