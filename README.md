// This is a simplified example.
// You would use a library like Axios or the Fetch API for a real application.
document.getElementById('pay-button').addEventListener('click', function() {
    const orderDetails = {
        amount: 100.50, // Amount in USD
        currency: 'USD',
        crypto: 'BTC' // User selected Bitcoin
    };

    fetch('/create-crypto-invoice', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(orderDetails)
    })
    .then(response => response.json())
    .then(data => {
        // 'data' would contain the invoice information from your backend
        // This includes a payment address, QR code, and a checkout URL
        console.log(data);
        // Display the payment details to the user
        document.getElementById('payment-address').textContent = data.address;
        document.getElementById('qr-code').src = data.qrCodeUrl;
    })
    .catch(error => console.error('Error:', error));
});
