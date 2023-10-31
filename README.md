# OpenAI-Meeting-Minutes
An automated meeting minutes generator with Whisper and GPT-4.

## Based on this tutorial:
https://platform.openai.com/docs/tutorials/meeting-minutes

## Install
```bash
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
python3 meeting-minutes.py
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
