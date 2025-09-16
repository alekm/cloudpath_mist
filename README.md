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

## Security Note

The Mist secret key is currently hardcoded in the template. For production use, consider implementing a more secure method of key management.
