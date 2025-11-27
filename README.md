# CipherForge

A modern, client-side encryption tool featuring keyed substitution-permutation cipher with PBKDF2 key derivation and configurable multi-round scrambling.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

## Features

- **PBKDF2 Key Derivation** - Industry-standard key derivation with configurable iterations (10,000-250,000)
- **Multi-Round Encryption** - 1-10 configurable rounds of substitution and permutation
- **Deterministic Encryption** - Same key and settings always produce the same output
- **Client-Side Only** - All encryption happens in your browser, nothing sent to servers
- **Dark Mode** - Eye-friendly dark theme with persistent preference
- **Responsive Design** - Works seamlessly on desktop and mobile devices
- **Clean Interface** - Minimal, intuitive UI focused on functionality

## Live Demo

**[Try it now](https://yourusername.github.io/cipherforge)**

## How It Works

CipherForge uses a combination of cryptographic techniques:

1. **Key Derivation**: Your password is processed through PBKDF2 with SHA-256
2. **Substitution**: Characters are mapped to a shuffled alphabet derived from your key
3. **Permutation**: Character positions are scrambled based on the derived key
4. **Multiple Rounds**: Steps 2-3 repeat for enhanced security (default: 3 rounds)

### Security Features

- **PBKDF2-SHA256**: Protects against brute-force attacks with configurable iterations
- **Cryptographically Secure RNG**: Uses `crypto.getRandomValues()` for key generation
- **Salt Integration**: Message length incorporated into key derivation
- **No External Dependencies**: Pure vanilla JavaScript, no third-party libraries

## Usage

### Encryption

1. Enter or generate a secure key
2. Type your plaintext message
3. Adjust rounds and iterations (optional)
4. Click **Encrypt → Ciphertext**
5. Share the ciphertext (keep your key secret)

### Decryption

1. Enter the same key used for encryption
2. Paste the ciphertext
3. Use the same rounds and iterations settings
4. Click **Decrypt → Plaintext**

### Configuration

**Rounds**: Number of substitution-permutation cycles (1-10)
- More rounds = stronger encryption but slower performance
- Recommended: 3-5 rounds for general use
  
**Iterations**: PBKDF2 iteration count (10,000-250,000)
- More iterations = better protection against brute-force attacks
- Recommended: 100,000 for general use

## Installation

### Use Online
Simply visit the [live demo](https://greedism.github.io/cipherforge) - no installation needed.

### Run Locally
```bash
# Clone the repository
git clone https://github.com/greedism/cipherforge.git

# Navigate to the directory
cd cipherforge

# Open in your browser
open index.html
# or start a local server
python -m http.server 8000
# then visit http://localhost:8000
```

### Self-Host

1. Download `index.html`
2. Upload to any static hosting service:
   - GitHub Pages
   - Netlify
   - Cloudflare Pages
   - Vercel
   - Your own web server

## Security Considerations

### What This Tool Is Good For

- Obfuscating text from casual viewing
- Educational purposes and learning cryptography concepts
- Sharing messages with friends using a shared key
- Adding a layer of encoding to your data

### Important Limitations

- **Not a replacement for industry-standard encryption** (like AES-GCM)
- No authentication or integrity checking (vulnerable to tampering)
- Encryption strength depends heavily on your key
- No forward secrecy or key rotation
- Character set limited to printable ASCII (chars 32-126)

### Best Practices

1. **Use strong keys**: Generate random keys with the built-in generator
2. **Keep keys secret**: Never share your key in the same channel as ciphertext
3. **Use high iterations**: 100,000+ iterations recommended for sensitive data
4. **Use multiple rounds**: 3+ rounds for better security
5. **Don't reuse keys**: Use different keys for different purposes

## Customization

The tool features a clean, minimal design with dark mode support. To customize:

- **Colors**: Edit the CSS variables in the `<style>` section
- **Rounds/Iterations**: Modify the default values in the `<select>` dropdowns
- **Character Set**: Adjust the `CHARSET` array in the JavaScript

## Technical Details

### Algorithm Overview
```
Encryption:
  1. Derive key using PBKDF2(password, salt, iterations)
  2. For each round:
     a. Generate substitution map from derived key + round number
     b. Substitute each character
     c. Generate permutation from derived key + round number + message length
     d. Permute character positions
  3. Output ciphertext

Decryption:
  1. Derive same key using PBKDF2(password, salt, iterations)
  2. For each round (in reverse):
     a. Generate permutation (same as encryption)
     b. Reverse permutation
     c. Generate substitution map (same as encryption)
     d. Reverse substitution
  3. Output plaintext
```

### Browser Compatibility

- Chrome 37+
- Firefox 34+
- Safari 11+
- Edge 79+

**Requirements:**
- Web Crypto API (`crypto.subtle`)
- ES6+ JavaScript features
- Local Storage (for theme preference)

## Contributing

Contributions are welcome. Please feel free to:

- Report bugs
- Suggest features
- Submit pull requests
- Improve documentation

## License

This project is open source and available under the [MIT License](LICENSE).

## Author

Made by greed

## Acknowledgments

- Inspired by classical cipher techniques
- Uses browser's native Web Crypto API
- Built with vanilla JavaScript - no frameworks needed

## Resources

- [PBKDF2 Specification (RFC 2898)](https://tools.ietf.org/html/rfc2898)
- [Web Crypto API Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API)
- [Substitution-Permutation Networks](https://en.wikipedia.org/wiki/Substitution%E2%80%93permutation_network)

---

**Disclaimer**: This tool is provided for educational and recreational purposes. For production-grade security, use established encryption standards like AES-GCM with proper key management.
