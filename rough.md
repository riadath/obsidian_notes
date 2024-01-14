## Error Messages and Explanation
****
#### C:\\Shorts\\shorts.mp3: No such file or directory
**Explanation**
- There was an issue with the provided file path.
- Either the `shorts.mp3` file does not exist in the specified directory or the provided directory path is incorrect.
**Suggested Action**
- Check that the `download_video` function successfully downloaded the audio file and that it was saved with the correct filename
- Check the spelling and case sensitivity of the filename.
#### An error occurred while running ffmpeg.
**Explanation**
- Exact type or nature or error was not specified.
- There was an issue with running the ffmpeg command in `merge_audio_video` or `edit_video` function.

**Suggested Action**
- Check if  `ffmpeg` is installed on your system or not.
- Verify that the paths used in the `ffmpeg` commands are correct and properly escaped if necessary
#### C:\\Shorts\\i-survived-50-hours-in-antarctica_merged.mp4: No such file or directory"
- There was an issue with the provided file path.
- Either the `i-survived-50-hours-in-antarctica_merged.mp4` file does not exist in the specified directory or the provided directory path is incorrect.


