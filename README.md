# Video Processing Service

A lightweight microservice for video processing and compression built with Node.js, Express, and FFmpeg.

## Features

- Convert and compress videos to 360p resolution
- Simple REST API for video processing
- Handles input/output file paths
- Error handling and status reporting

## Prerequisites

- Node.js (v14 or higher)
- FFmpeg installed on the system
- npm or yarn package manager

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/video-processing-service.git
   cd video-processing-service
   ```

2. Install dependencies:
   ```
   npm install
   ```

3. Make sure FFmpeg is installed on your system:
   - For macOS: `brew install ffmpeg`
   - For Ubuntu/Debian: `sudo apt install ffmpeg`
   - For Windows: Download from [FFmpeg website](https://ffmpeg.org/download.html)

## Configuration

The application automatically locates FFmpeg on your system, but if needed, you can manually set the path in `index.ts`:

```typescript
ffmpeg.setFfmpegPath('/path/to/ffmpeg');
```

## Usage

1. Start the service:
   ```
   npm start
   ```

2. The service will run on http://localhost:3000 by default (configurable via PORT environment variable)

3. To process a video, send a POST request to `/process-video`:
   ```json
   {
     "inputFilePath": "/path/to/input/video.mp4",
     "outputFilePath": "/path/to/output/video.mp4"
   }
   ```

4. The service will respond with status 200 upon successful processing

## API Documentation

### POST /process-video

Processes a video and compresses it to 360p resolution.

**Request Body:**
```json
{
  "inputFilePath": "string", // Required: Path to the input video file
  "outputFilePath": "string" // Required: Path where the processed video will be saved
}
```

**Responses:**
- `200 OK`: Processing finished successfully
- `400 Bad Request`: Missing input or output file path
- `500 Internal Server Error`: Processing error (with error message)

## Development

1. Install development dependencies:
   ```
   npm install
   ```

2. Run in development mode with hot reload:
   ```
   npm run dev
   ```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
