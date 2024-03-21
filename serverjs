const express = require('express');
const axios = require('axios');

const app = express();
const PORT = process.env.PORT || 3000;

// Middleware to parse JSON and URL encoded bodies
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Endpoint to proxy requests
app.post('/get/gateway', async (req, res) => {
    const url = req.body.url;
    try {
        const response = await axios.get(url, {
            proxy: {
                host: '172.67.180.55',
                port: 8080 // Adjust the port as per your proxy server configuration
            }
        });
        res.send(response.data);
    } catch (error) {
        res.status(500).send('Error: ' + error.message);
    }
});

// Serve static files (HTML, CSS, JS)
app.use(express.static('public'));

app.listen(PORT, () => {
    console.log(`Server is running on port ${PORT}`);
});
