FFmpeg commands for video and audio processing including reduce size, extract audio, remove silence, and concatenate files.

Reduce video size:
    ffmpeg -i input_file.mp4 -vcodec libx264 -crf 24 output_file.mp4

Extract the audio stream from a video file:
   ffmpeg -i input.mov -vn -acodec copy output.m4a
      -i input.mov : Specifies the input file.
      -vn : Disables the video stream.
      -acodec copy : Copies the existing audio codec without re-encoding.
      output.m4a : Saves the extracted audio as an M4A file.

   ffmpeg -i input.mov -q:a 0 -map a output.mp3 (an 18gb .mov file took 90 seconds, file size 87MB)
      -q:a 0 : Ensures high audio quality.
      -map a : Extracts only the audio stream.

Remove silence from audio file:
    ffmpeg -i input_file.mp3 -af silenceremove=1:0:-50dB cleaned.mp3


Concatenate video files:
From: https://superuser.com/questions/1256223/combine-mov-video-files

Create a "to_merge.txt" file containing a list of files to combine
    find . -type f -iname "*.mov" | sort -V | awk '{print "file \x27" $0 "\x27"}' > to_merge.txt

Create a merge file from a date range
    find $PWD -type f -newermt "2023-06-20" ! -newermt "2023-07-01" -iname "*.MOV" | sort | awk 'NF {print "file \x27" $0 "\x27"}' > to_merge.txt

# [WHAT I USUALLY USE: FAST]
# 2. **If all of your .mov files have the same encoding** (ex: they were 
# all recorded on the same video camera and with the same settings), you can
# specify to use the "copy" codec via `-c copy`, which means it will NOT 
# have to re-encode the video. This just concatenates all the files together. 
# THIS TAKES **SECONDS**. 

    time ffmpeg -f concat -safe 0 -i to_merge.txt -c copy merged.mov|mp4

# [SLOW; SOMETIMES NECESSARY]
# OR 2. **If each of your .mov files has a different encoding,** you'll need to 
# re-encode them all into a single stream. 
# - This uses the "to_merge.txt" file created above, and outputs the merged 
#   file into "merged.mov". 
# THIS COULD TAKE **HOURS**. 

    time ffmpeg -f concat -safe 0 -i to_merge.txt merged.mov|mp4


