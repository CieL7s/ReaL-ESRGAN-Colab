# Real-ESRGAN Video Upscaler (Google Colab)

A Google Colab notebook for upscaling videos using Real-ESRGAN AI models. This tool can enhance video quality by upscaling to various resolutions including FHD, 2K, and 4K.

## Features

- **Multiple Resolution Options**:
  - FHD (1920 x 1080)
  - 2K (2560 x 1440)
  - 4K (3840 x 2160)
  - 2x, 3x, or 4x original resolution

- **Multiple AI Models**:
  - `RealESRGAN_x4plus` - Best for general videos
  - `RealESRGAN_x4plus_anime_6B` - Optimized for anime content
  - `realesr-animevideov3` - Advanced anime video model

- **Google Drive Integration**: Automatically save upscaled videos to your Google Drive
- **GPU Acceleration**: Utilizes CUDA for faster processing
- **Automatic Aspect Ratio Handling**: Maintains proper video dimensions

## Requirements

- Google Colab account (free tier works)
- GPU runtime enabled in Colab
- Sufficient Google Drive storage (optional, for saving outputs)

## How to Use

### 1. Setup and Installation

Run the first code cell to:
- Check GPU availability
- Clone Real-ESRGAN repository
- Install required dependencies
- Mount Google Drive (optional)

```python
mount_drive = True  # Set to False if you don't want to use Google Drive
```

### 2. Fix Import Errors

Run the "FIXING ERROR" cell to patch compatibility issues with torchvision.

### 3. Upscale Your Video

Configure the parameters in the final cell:

```python
video_path = "/content/your_video.mp4"  # Path to your input video
output_dir = "/content/"                 # Output directory
resolution = "FHD (1920 x 1080)"        # Choose your target resolution
model = "RealESRGAN_x4plus"             # Select AI model
```

Then run the cell to start upscaling.

## Parameters Explained

### video_path
Path to your input video file. If using Google Drive:
```python
video_path = "/content/gdrive/MyDrive/your_video.mp4"
```

### output_dir
Directory where the upscaled video will be saved.

### resolution
Target output resolution:
- `"FHD (1920 x 1080)"` - Full HD
- `"2k (2560 x 1440)"` - 2K resolution
- `"4k (3840 x 2160)"` - 4K Ultra HD
- `"2 x original"` - Double the original dimensions
- `"3 x original"` - Triple the original dimensions
- `"4 x original"` - Quadruple the original dimensions

### model
AI model for upscaling:
- `RealESRGAN_x4plus` - General purpose, best for real-world videos
- `RealESRGAN_x4plus_anime_6B` - Optimized for anime/cartoon content
- `realesr-animevideov3` - Latest anime video model

## Output

The upscaled video will be saved as:
- Local: `{output_dir}/{video_name}_upscaled_{width}_{height}.mp4`
- Google Drive (if enabled): `MyDrive/Upscaled Videos (REAL-ESRGAN)/{video_name}_upscaled_{width}_{height}.mp4`

## Processing Time

Processing time depends on:
- Video length and resolution
- Target upscale resolution
- GPU availability (T4, V100, etc.)
- Model complexity

Example: A 1-minute 720p video upscaled to 1080p may take 5-10 minutes on a T4 GPU.

## Troubleshooting

### "GPU not detected"
Make sure GPU is enabled:
1. Go to Runtime → Change runtime type
2. Select "T4 GPU" or "V100" under Hardware accelerator
3. Save and restart the notebook

### Out of Memory Error
Try:
- Reducing the target resolution
- Processing shorter video clips
- Restarting the runtime to clear memory

### Video file not found
- Verify the file path is correct
- If using Google Drive, ensure it's properly mounted
- Check that the file exists in the specified location

## Credits

- Original notebook fixed by: CielV7
- Real-ESRGAN: [xinntao/Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN)
- For bugs or issues: [Open an issue on GitHub](https://github.com/CieL7s/ReaL-ESRGAN-Colab)

## License

This project uses Real-ESRGAN which is licensed under the BSD 3-Clause License.

## Notes

- First run will download model weights (may take a few minutes)
- Ensure stable internet connection during setup
- Free Colab tier has usage limits; consider Colab Pro for longer sessions
- Always backup your original videos before processing
