# FFmpeg Dockerized Application

This project provides a simple way to run FFmpeg commands using Docker. The setup ensures a lightweight and portable FFmpeg environment, making video and audio processing efficient and easy.

## Features
- **FFmpeg Installation**: Pre-installed FFmpeg in a Docker container.
- **Volume Mounting**: Easily process files on your host system by mounting a volume.
- **Interactive Access**: Open stdin and tty for interactive FFmpeg use.

## Requirements
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Setup Instructions
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. Build the Docker image:
   ```bash
   docker-compose build
   ```

3. Run the container:
   ```bash
   docker-compose up
   ```

## Usage
You can process media files by placing them in the `media` folder in your project directory. The volume mounts this folder into the container at `/media`.

### Example FFmpeg Command
Convert an MP4 file to a GIF:
```bash
docker exec -it ffmpeg-container ffmpeg -i /media/input.mp4 -vf "fps=10,scale=320:-1:flags=lanczos" -c:v gif /media/output.gif
```

### Timestamp Example
Convert a specific portion of a video to a GIF:
```bash
docker exec -it ffmpeg-container ffmpeg -ss 00:00:10 -i /media/input.mp4 -t 5 -vf "fps=10,scale=320:-1:flags=lanczos" -c:v gif /media/output.gif
```

## Cleaning Up
To stop and remove the container:
```bash
docker-compose down
```

## Customization
You can edit the `Dockerfile` to include additional dependencies or FFmpeg configurations as needed. Update the `docker-compose.yml` for advanced volume or networking setups.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

---

Feel free to reach out if you have any issues or suggestions!
