# ffmpeg-git

FFmpeg container compiled from git master HEAD with the following configuration:

```--pkg-config-flags=--static --prefix=/ffmpeg/ffmpeg_build --extra-cflags='-I/ffmpeg/ffmpeg_build/include -static' --extra-ldflags='-L/ffmpeg/ffmpeg_build/lib -static' --extra-libs='-lpthread -lm' --bindir=/ffmpeg/bin --enable-static --disable-shared --disable-debug --disable-doc --disable-ffplay --enable-ffprobe --enable-gpl --enable-libfreetype --enable-libopus --enable-libx264 --enable-libx265```

This is intended as a base image for five82\batchtranscode but can be run as a standalone container.

For example:

    docker run \
    --name ffmpeg-git \
    -v <path/to/input/dir>:/input \
    -v <path/to/output/dir>:/output \
    five82/ffmpeg-git \
    /app/ffmpeg -i /input/input.mkv -c:v libx264 -preset medium -crf 20 -c:a aac -b:a 384k /output/output.mkv
