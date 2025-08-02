# Real Market Data Setup Guide

This guide explains how to configure the Nivesh app to use real market data APIs instead of mock data.

## Environment Variables

Create a `.env` file in the root directory with the following variables:

```env
# Market Data API Configuration
# Set to 'true' to use real market data APIs, 'false' for mock data
VITE_USE_REAL_MARKET_DATA=false

# Alpha Vantage API Key (for additional market data)
# Get your free API key from: https://www.alphavantage.co/support/#api-key
VITE_ALPHA_VANTAGE_API_KEY=your_alpha_vantage_api_key_here

# Yahoo Finance API (no key required, but rate limited)
# Used for real-time stock data

# NSE India API (requires registration)
# Used for Indian market data

# BSE India API (requires registration)
# Used for Indian market data

# WebSocket Configuration
# For real-time updates (optional)
VITE_WEBSOCKET_ENABLED=false
VITE_WEBSOCKET_URL=wss://your-websocket-server.com

# Cache Configuration
VITE_CACHE_DURATION=300000
VITE_REFRESH_INTERVAL=30000
```

## Available APIs

### 1. Yahoo Finance API (Recommended for testing)
- **Cost**: Free
- **Rate Limit**: 2,000 requests per hour
- **Coverage**: Global markets including Indian stocks
- **Setup**: No API key required

### 2. Alpha Vantage API
- **Cost**: Free tier available (500 requests/day)
- **Rate Limit**: Varies by plan
- **Coverage**: Global markets
- **Setup**: Requires API key from https://www.alphavantage.co/

### 3. NSE India API
- **Cost**: Free (with registration)
- **Rate Limit**: Varies
- **Coverage**: Indian markets only
- **Setup**: Requires registration at NSE website

### 4. BSE India API
- **Cost**: Free (with registration)
- **Rate Limit**: Varies
- **Coverage**: Indian markets only
- **Setup**: Requires registration at BSE website

## Setup Instructions

### Step 1: Enable Real Data
Set `VITE_USE_REAL_MARKET_DATA=true` in your `.env` file.

### Step 2: Get API Keys (Optional)
For enhanced functionality, get API keys from:
- Alpha Vantage: https://www.alphavantage.co/support/#api-key
- NSE India: https://www.nseindia.com/
- BSE India: https://www.bseindia.com/

### Step 3: Configure WebSocket (Optional)
For real-time updates, set up a WebSocket server and configure:
```env
VITE_WEBSOCKET_ENABLED=true
VITE_WEBSOCKET_URL=wss://your-websocket-server.com
```

### Step 4: Restart the Application
After configuring the environment variables, restart your development server:
```bash
npm run dev
```

## Features Available with Real Data

1. **Real-time Stock Prices**: Live prices from Yahoo Finance
2. **Market Indices**: NIFTY 50, SENSEX, BANKNIFTY
3. **Stock Search**: Real stock search functionality
4. **Sector Data**: Sector-wise performance data
5. **Caching**: Intelligent caching for better performance
6. **WebSocket Updates**: Real-time price updates (when configured)

## Troubleshooting

### API Rate Limits
If you hit rate limits:
1. Increase cache duration in environment variables
2. Reduce refresh intervals
3. Upgrade to paid API plans

### CORS Issues
If you encounter CORS errors:
1. Use a CORS proxy
2. Set up a backend proxy server
3. Use browser extensions for development

### Data Accuracy
- Real data may have slight delays
- Some APIs provide delayed data for free tiers
- Verify data accuracy before making investment decisions

## Fallback to Mock Data

If real data APIs are unavailable or you want to use mock data:
1. Set `VITE_USE_REAL_MARKET_DATA=false`
2. The app will automatically use mock data
3. All features will work with simulated data

## Security Notes

- Never commit API keys to version control
- Use environment variables for sensitive data
- Consider using a backend proxy for production
- Implement proper rate limiting and error handling 