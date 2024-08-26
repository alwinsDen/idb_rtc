## Run the emulator with ffmpeg compression.
```shell
idb video-stream --fps 60 --format h264 --compression-quality 0.5 --udid AEE9C40F-8A34-4242-BFEB-79269582715F | \
ffmpeg -re -f h264 -i pipe:0 -vf scale=640:1343 -pix_fmt yuv420p -vcodec libvpx -b:v 1000k -cpu-used 8 -deadline realtime -g 1 -bufsize 200k -error-resilient 1 -auto-alt-ref 1 -f rtp 'rtp://127.0.0.1:5004?pkt_size=1200'
```