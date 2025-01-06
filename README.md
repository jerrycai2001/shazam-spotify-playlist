# shazam-spotify-playlist
Once you hear a song from Shazam, you screenshot it - then compile the songs from Shazam into a Spotify or YouTube playlist. 

# Shazam Spotify Playlist

## Overview
**Shazam Spotify Playlist** is a Python-based application that automates the process of building Spotify or YouTube playlists from Shazam screenshots. Simply drop your Shazam screenshots into a folder, and this tool will extract the song information, search for them on Spotify, and create a playlist for you. No manual typing required!

## Features
- **OCR-based text extraction**: Leverages Tesseract OCR to extract song and artist details from Shazam screenshots.
- **HEIC and PNG support**: Automatically converts HEIC images to PNG for compatibility.
- **Spotify integration**: Creates playlists and adds songs using the Spotify Web API.
- **Customizable playlist names**: Set your desired playlist name for better organization.
- **Error handling**: Skips screenshots with incomplete or invalid data.

## Prerequisites
1. **Python 3.8+**
2. **Tesseract OCR**
   - macOS: `brew install tesseract`
   - Ubuntu: `sudo apt-get install tesseract-ocr`
   - Windows: [Download Tesseract OCR](https://github.com/tesseract-ocr/tesseract)
3. **Spotify Developer Account**
   - Create a new application in the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/).
   - Note down your `Client ID` and `Client Secret`.
4. **Required Python Libraries**
   ```bash
   pip install pillow pillow-heif pytesseract spotipy
   ```

## Environment Setup
1. **Set up Spotify credentials** as environment variables:
   ```bash
   export SPOTIPY_CLIENT_ID='your_client_id'
   export SPOTIPY_CLIENT_SECRET='your_client_secret'
   export SPOTIPY_REDIRECT_URI='http://localhost:8888/callback'
   ```
2. Ensure Tesseract OCR is correctly installed and added to your system path.

## Usage
1. **Prepare Screenshots**: Save all your Shazam screenshots in a folder (e.g., `screenshots/`). Supported formats: HEIC and PNG.
2. **Run the Application**:
   ```bash
   python main.py
   ```
3. **Output**: A new Spotify playlist with the name "My Shazam Playlist" will be created with the extracted songs.

## Directory Structure
```
shazam-spotify-playlist/
├── main.py              # Entry point for the script
├── requirements.txt     # Python dependencies
├── README.md            # Project documentation
├── utils.py             # Helper functions (e.g., text extraction, Spotify integration)
└── screenshots/         # Directory to place Shazam screenshots
```

## Key Functions
### Image Processing
- Extracts text from images using OCR.
- Supports HEIC and PNG file formats.

### Text Parsing
- Parses Shazam text to extract song title and artist.

### Spotify Integration
- Authenticates using Spotify Web API.
- Creates a new playlist and adds songs by searching Spotify's track database.

## Example Workflow
```python
# Main workflow structure
def process_shazam_screenshots(screenshot_directory):
    song_list = []
    for image in get_images(screenshot_directory):
        text = extract_text_from_image(image)
        song_info = parse_shazam_text(text)
        song_list.append(song_info)

    playlist = create_spotify_playlist()
    add_songs_to_playlist(playlist, song_list)
```

## Future Enhancements
1. **YouTube Playlist Support**: Add functionality for creating playlists on YouTube Music.
2. **Enhanced Error Handling**: Handle edge cases like failed API calls or invalid screenshots.
3. **Batch Processing**: Optimize for large numbers of screenshots.
4. **Mobile Integration**: Develop a mobile app version for easier use on the go.

## Contributions
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -m 'Add feature'`).
4. Push to the branch (`git push origin feature-name`).
5. Open a Pull Request.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgments
- [Pytesseract](https://github.com/madmaze/pytesseract) for OCR functionality.
- [Spotipy](https://github.com/plamere/spotipy) for Spotify API integration.

---

**Happy Playlist Building!**

