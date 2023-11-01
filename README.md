# OpenAI-Meeting-Minutes
An automated meeting minutes generator with Whisper and GPT-4.

## Based on this tutorial:
https://platform.openai.com/docs/tutorials/meeting-minutes

## Install
```bash
# checkout code
git clone https://github.com/johntday/openai_meeting_minutes.git

cd openai_meeting_minutes/

cp .env.sample .env

# create python virtual env
rm -rf venv/
python3 -m venv venv

# set virtual env active
source venv/bin/activate

# install python packages required
pip3 install -r requirements.txt
```

Edit file `.env` to include your `OPENAI_API_KEY`

## Usage

```bash
# see command line options
python3 meeting-minutes.py -h

# typical usage
python3 meeting-minutes.py 'audio/20231101_wp_demo' -e m4a
```

```bash
extension: '*.m4a'
input dir: 'audio/20231101_wp_demo'

found 2 audio files: ['audio/20231101_wp_demo/New Recording 6.m4a', 'audio/20231101_wp_demo/New Recording 5.m4a']

Complete the sentence: "This is a meeting about..." (or press Enter to skip): demo for hybris and aem after bug fixes
Transcribing audio files...

transcription files written to: 'audio/20231101_wp_demo/20231101_wp_demo_transcription.txt'
Generating meeting minutes...

Meeting summary written to: 'audio/20231101_wp_demo/20231101_wp_demo_summary.docx'
```


## Caveats
 - API usage will cost some money, about $1-2/hr of audio
 - The Whisper API has a hard limit of 25 MB per audio file

## Tips
 - Shrink the size of your audio files:
   - I use GarageBand to export them as Low Quality (64 kBit/s) MP3 files
   - Alternatively, try the `pydub` Python package powered by FFmpeg to further reduce the bitrate, following the formula `New bitrate = (Target file size / Current file size) * Current bitrate`
 - If you can't get your audio file under 25 MB, you'll have to split it up into chunks, transcribe each chunk separately, then concatenate the transcription strings together to obtain the minutes (this would require tweaking the code)

## References
 - https://github.com/sapols/OpenAI-Meeting-Minutes
