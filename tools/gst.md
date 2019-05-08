# gst play with waylandsink
gst-launch-1.0 playbin uri=file:///62377a.mp4 video-sink=waylandsink
gst-launch-1.0 -v filesrc location=62377a.mp4 ! decodebin3 ! queue  ! videoconvert ! videoscale ! video/x-raw, width=320, height=240 ! waylandsink
