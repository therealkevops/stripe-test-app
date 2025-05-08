# Stripe Payment Testing App

A beginner-friendly application demonstrating how to use Stripe's payment processing in a test environment.

## Overview

This project is a simple payment processing application that demonstrates how to:

- Create a payment form with Stripe Elements
- Process test payments without using real money
- Handle successful and failed payment scenarios
- Receive webhook notifications from Stripe

Perfect for beginners learning payment integration or developers who need a quick Stripe testing environment.

## Prerequisites

Before you start, make sure you have:

- [Node.js](https://nodejs.org/) installed (version 14 or higher)
- A free [Stripe account](https://stripe.com/register)
- Basic knowledge of HTML, CSS, and JavaScript
- A text editor (like [Visual Studio Code](https://code.visualstudio.com/))

## Installation

1. **Clone this repository**
   ```bash
   git clone https://github.com/yourusername/stripe-test-app.git
   cd stripe-test-app
   ```

   Or set up a new project:
   ```bash
   mkdir stripe-test-app
   cd stripe-test-app
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   - Create a `.env` file in the project root
   - Add your Stripe API keys:
   ```
   STRIPE_PUBLISHABLE_KEY=pk_test_your_publishable_key
   STRIPE_SECRET_KEY=sk_test_your_secret_key
   STRIPE_WEBHOOK_SECRET=whsec_your_webhook_secret_key
   PORT=3000
   ```

4. **Update your Stripe publishable key in the frontend**
   - Open `public/index.html`
   - Find this line: `const stripe = Stripe('YOUR_STRIPE_PUBLISHABLE_KEY');`
   - Replace `'YOUR_STRIPE_PUBLISHABLE_KEY'` with your actual test publishable key

## Running the Application

1. **Start the server**
   ```bash
   node app.js
   ```

2. **Open your browser**
   - Go to [http://localhost:3000](http://localhost:3000)
   - You should see the payment form
  
   - _Alternatively use the LiveServer extension in VSCode_

## Testing Payments

Use these test cards to simulate different payment scenarios:

| Card Number | Scenario |
|-------------|----------|
| 4242 4242 4242 4242 | Successful payment |
| 4000 0000 0000 0002 | Card declined |
| 4000 0000 0000 9995 | Insufficient funds |

For all test cards:
- Use any future expiration date
- Use any 3-digit CVC
- Use any postal/ZIP code

## Project Structure

```
stripe-test-app/
│
├── node_modules/        # Dependencies
├── public/              # Frontend files
│   └── index.html       # Payment form
│
├── .env                 # Environment variables (API keys)
├── app.js               # Express server and Stripe integration
├── package.json         # Project configuration
└── README.md            # This file
```

## Understanding the Code

### Backend (app.js)

The server-side code handles:

1. **Starting a web server** using Express
2. **Creating payment intents** when a user submits the payment form
3. **Processing webhook events** from Stripe

Key parts:
- **Express routes**: Handle HTTP requests
- **Stripe SDK**: Communicates with Stripe's API
- **Environment variables**: Keep API keys secure

### Frontend (public/index.html)

The client-side code handles:

1. **Displaying a payment form** using Stripe Elements
2. **Collecting card information** securely
3. **Submitting payment data** to the server
4. **Showing payment results** to the user

Key parts:
- **Stripe.js**: Secure handling of card data
- **Fetch API**: Communication with the server
- **DOM manipulation**: Updating the UI based on payment results

## Setting Up Webhooks (Optional)

Webhooks allow Stripe to notify your application about events even if the customer closes their browser.

1. **Install the Stripe CLI** (follow instructions at [stripe.com/docs/stripe-cli](https://stripe.com/docs/stripe-cli))

2. **Login to your Stripe account**
   ```bash
   stripe login
   ```

3. **Forward webhook events to your local server**
   ```bash
   stripe listen --forward-to localhost:3000/webhook
   ```

4. **Update the webhook secret in your `.env` file** with the signing secret shown by the CLI

## Common Issues & Solutions

### Server won't start
- Check if Node.js is installed: `node --version`
- Verify all dependencies are installed: `npm install`
- Make sure no other application is using port 3000

### Payment form doesn't appear
- Check the browser console for errors
- Verify the server is running correctly
- Make sure your publishable key is correctly set in index.html

### Payments failing
- Confirm you're using valid test card numbers
- Check that your API keys are correct
- Look for error messages in the browser console and server logs

## Learning Resources

- [Stripe Documentation](https://stripe.com/docs)
- [Express.js Guide](https://expressjs.com/en/guide/routing.html)
- [Introduction to Webhooks](https://stripe.com/docs/webhooks)

## Next Steps

Ready to expand this project? Here are some ideas:

- Add a database to store order information
- Implement customer accounts and saved payment methods
- Add support for different payment methods (Apple Pay, Google Pay)
- Create a complete checkout flow with shipping information
- Deploy the application to a cloud platform

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Stripe for their excellent documentation and test environment
- The Express.js team for creating an easy-to-use web framework
- All the beginner developers who inspired this tutorial

---

Created with ❤️ for learning purposes. Not intended for production use.
