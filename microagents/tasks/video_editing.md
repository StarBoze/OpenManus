---
name: video_editing
type: task
version: 1.0.0
author: openhands
agent: CodeActAgent
inputs:
  - name: VIDEO_FILE
    description: "Path to the input video file"
    required: true
  - name: OPERATION
    description: "Video editing operation to perform (transcode, trim, add_text, extract_frames, get_info, transcribe)"
    required: true
  - name: OUTPUT_FILE
    description: "Path to save the output file"
    required: true
  - name: START_TIME
    description: "Start time for trimming (in seconds or HH:MM:SS format)"
    required: false
  - name: END_TIME
    description: "End time for trimming (in seconds or HH:MM:SS format)"
    required: false
  - name: TEXT
    description: "Text to overlay on the video"
    required: false
  - name: TEXT_POSITION
    description: "Position of text overlay (top, bottom, center)"
    required: false
  - name: FRAME_RATE
    description: "Frame rate for extracting frames (frames per second)"
    required: false
  - name: OUTPUT_FORMAT
    description: "Output format for transcoding (mp4, webm, etc.)"
    required: false
---

I'll help you edit the video file at "{{ VIDEO_FILE }}" using the OpenHands Video Editor Agent.

Based on your selected operation "{{ OPERATION }}", I'll perform the following task:

{% if OPERATION == "transcode" %}
I'll transcode the video to {% if OUTPUT_FORMAT %}{{ OUTPUT_FORMAT }}{% else %}mp4{% endif %} format and save it to "{{ OUTPUT_FILE }}".

{% elif OPERATION == "trim" %}
I'll trim the video from {% if START_TIME %}{{ START_TIME }}{% else %}the beginning{% endif %} to {% if END_TIME %}{{ END_TIME }}{% else %}the end{% endif %} and save it to "{{ OUTPUT_FILE }}".

{% elif OPERATION == "add_text" %}
I'll add the text "{{ TEXT }}" to the video at position {% if TEXT_POSITION %}{{ TEXT_POSITION }}{% else %}center{% endif %} and save it to "{{ OUTPUT_FILE }}".

{% elif OPERATION == "extract_frames" %}
I'll extract frames from the video at {% if FRAME_RATE %}{{ FRAME_RATE }}{% else %}1{% endif %} frames per second and save them using the pattern "{{ OUTPUT_FILE }}".

{% elif OPERATION == "get_info" %}
I'll analyze the video and provide detailed information about its format, duration, resolution, and other properties.

{% elif OPERATION == "transcribe" %}
I'll generate a transcription of the audio in the video and save it to "{{ OUTPUT_FILE }}".

{% else %}
I'm not familiar with the operation "{{ OPERATION }}". The supported operations are:
- transcode: Convert the video to a different format
- trim: Cut the video to a specific time range
- add_text: Add text overlay to the video
- extract_frames: Extract still frames from the video
- get_info: Get detailed information about the video
- transcribe: Generate a transcription of the audio

{% endif %}

Let me execute this task for you now.
