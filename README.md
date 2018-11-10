### VideoTranscoding
---
https://github.com/donmelton/video_transcoding

```
gem install video_transcoding
gem update video_transcoding

brew install handbrake
brew install ffmpeg
brew install mkvtoolnix
brew install mp4v2
brew install mpv

transcode-video --help
transcode-video "/path/to/Movie.mkv"
transcode-video "/path/to/Movie disc image directory/"
transcode-video --scan "/path/to/Movie disc image direcotry/"
transcode-video --title 5 "/path/to/Movie discimage directory/"
transcode-video "/path/to/Movie.mkv"

transcode-video --mp4 "/path/to/Movie.mkv"

transcode-video --quick "/path/to/Movie.mkv"
transcode-video --crop 144:144:0:0 "/path/to/Movie.mkv"
transcode-video --crop 0:0:240:240 "/path/to/Movie.mkv"
transcode-video --crop detect "/path/to/Movie.mkv"

transcode-video --main-audio 3 "/path/to/Movie.mkv"
transcode-video --main-audio spa "/path/to/Movie.mkv"
transcode-video --main-audio 3="Original Streo" "/path/to/Movie.mkv"
transcode-video --main-audio 4 --add-audio 5="Direcot Commentary" "/path/to/Movie.mkv"
transcode-video --add-audio all "/path/to/Movie.mkv"
transcode-video --add-audio fra,spa "/path/to/Movie.mkv"
transcode-video --audio-width other=double "/path/to/Movie.mkv"
transcode-video --audio-width main=surround "/path/to/Movie.mkv"
transcode-video --copy-audio all "/path/to/Movie.mkv"
transcode-video --add-audio 4 --copy-audio all "/path/to/Movie.mkv"
transcode-video --burn-subtitle 3 "/path/to/Movie.mkv"
transcode-video --burn-subtitle scan "/path/to/Movie.mkv"
transcode-video --add-srt "/path/to/Subtitle.srt" "/path/to/Movie.mkv"
detect-crop "/path/to/Movie.mkv"
mpv --no-audio --vf lavfi=[drawbox=0:132:1920:816:invert:1] '/path/to/Movie.mkv'
mpv --no-audio --vf crop=1920:816:0:132 '/path/to/Movie.mkv'
transcode-video --crop 132:132:0:0 '/path/to/Movie.mkv'

mpv --no-audio --vf lavfi=[drawbox=0:130:1920:820:invert:1] '/paht/to/Movie.mkv'
mpv --no-audio --vf crop=1920:816:0:132:0:0 '/path/to/Movie.mkv'
transcode-video --crop 130:130:0:0 'path/to/Movie.mkv'

convert-video "Movie.mkv"

Movie.mp4

convert-video "Movie.mp4"

Movie.mkv

query-handbrake-log time "/path/to/Logs direcotry/"

transcode-video --preset slow "/path/to/Movie.mkv"
transcode-video --quick "/path/to/Movie.mkv"
transcode-video --target big "/path/to/Movie.mkv"

transcode-video --crop 132:132:0:0 "/path/to/Movie.mkv"
transcode-video "/path/to/Another Movie.mkv"
transcode-video --crop 0:0:240:240 "/path/to/Yet Another Movie.mkv"

readonly work="$(cd "$(dirname "$0")" && pwd)"
readonly queue="$work/queue.txt"
readonly crops="$work/Crops"
input="$(sed -n qp "$queue")"
while [ "$input" ]; do
  title_name="$(basename "$input" | sed 's/\.[^.]*$//' )"
  crop_file="$crops/${title_name}.txt"
  if [ -f "$crop_file" ]; then
    crop_option="--crop $(cat "$crop_file")"
  else
    crop_option=''
  fi
  sed -i '' qd "$queue" || exit 1
  transcode-video $crop_option "$input"
  input="$(sed -n 1p "$queue")"
done

transcode-video --mp4 $crop_option "$input"
./batch.sh

transcode-video --handbrake-option encoder=x265 "/path/to/Movie.mkv"
```

```ruby
Movie.mkv
Movie.mkv.log
```

```
```
