# Cloudpath Mist Integration

This repository contains a custom Cloudpath template that integrates with Mist's external guest portal functionality.

## Files

- `cloudpath_mist.html` - The main Cloudpath template with Mist integration

## Features

- **Credential Verification Page**: Displays user information for verification before proceeding
- **Mist Authorization**: Generates proper HMAC-SHA1 signatures for Mist portal authorization
- **Cloudpath Integration**: Uses standard Cloudpath CSS classes and form submission flow
- **User-Friendly Interface**: Clean, professional verification interface with Continue/Back buttons

## How It Works

1. User reaches the credential verification page
2. Page displays their name and email for confirmation
3. When "Confirm & Continue" is clicked:
   - Generates Mist authorization URL with proper HMAC-SHA1 signature
   - Submits Cloudpath form with Mist URL as `RETURN_URL`
   - Cloudpath handles the redirect to Mist portal

## Technical Details

- Uses Web Crypto API for HMAC-SHA1 signature generation
- Follows Mist's external guest portal specification
- Compatible with Cloudpath template system
- Supports all standard Cloudpath variables and functionality

## Usage

1. Upload `cloudpath_mist.html` to your Cloudpath system
2. Configure as a message template in your Cloudpath workflow
3. Ensure Mist variables are properly passed through Cloudpath
4. Set the Mist secret key in the template (currently hardcoded)

## Mist Configuration

The template expects the following Mist variables to be available:
- `wlan_id`
- `ap_mac` 
- `client_mac`
- `url`
- `ap_name`
- `site_name`
- `authorize_url`
- `CLIENT_IP`

## Configuration

Before using this template, you must configure your Mist WLAN API Key:

1. Open `cloudpath_mist.html` in a text editor
2. Find the line: `const MIST_SECRET = 'YOUR_MIST_WLAN_API_KEY_HERE';`
3. Replace `YOUR_MIST_WLAN_API_KEY_HERE` with your actual Mist WLAN API Key
4. Save the file

### Finding Your Mist WLAN API Key

1. Log into your Mist dashboard
2. Navigate to Settings > WLANs
3. Select your guest WLAN
4. Find the "API Key" field and copy the value

## Security Note

The Mist secret key must be configured in the template before deployment. For production use, consider implementing a more secure method of key management than hardcoding in the template.
