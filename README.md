### MediaMaster

MediaMaster is a lightweight Bash utility that recursively counts common audio and video files across one or more directories. It also detects GVFS SFTP mount paths (e.g. `/run/user/1000/gvfs/sftp:host=...`) and runs the scan remotely over SSH for faster, more reliable results than traversing the mount locally.

#### Features

- Recursively counts media files (audio + video) by extension
- Accepts multiple directories in a single call
- Case-insensitive matching (e.g. `.mp3`, `.MP3`, `.Mp3`)
- GVFS SFTP mount detection:
  - Extracts `host`, `user`, and remote path from the GVFS mount
  - Executes `find` on the remote server via SSH and returns the count
- Minimal dependencies (Bash + standard Unix tools)

#### Supported extensions

Audio:
- `mp3`, `wav`, `flac`, `aac`, `ogg`, `m4a`

Video:
- `mp4`, `avi`, `mkv`, `mov`, `wmv`, `flv`, `webm`

To add more, edit the `AUDIO_EXTS` and `VIDEO_EXTS` arrays in `mediamaster.sh`.

#### Requirements

Local counting:
- `bash`
- `find`
- `wc`

GVFS SFTP remote acceleration (only when scanning a GVFS SFTP mount path):
- `ssh` locally
- `find` and `wc` available on the remote host
- SSH access to `user@host` (keys recommended)

#### Installation

Clone and make executable:

```bash
git clone https://github.com/fpucore/mediamaster.git
cd mediamaster
chmod +x mediamaster
