# use pkg-config for getting CFLAGS and LDLIBS
FFMPEG_LIBS=    libavdevice                       \
                libavformat                       \
                libavcodec                        \
                libavfilter                       \
                libswresample                     \
                libswscale                        \
                libavutil                         \

SDL_LIBS=       sdl2                              \

CFLAGS += -Wall
#use pkg-config to get info of the libs
CFLAGS := $(shell pkg-config --cflags $(FFMPEG_LIBS) $(SDL_LIBS)) $(CFLAGS)
LDLIBS := $(shell pkg-config --libs $(FFMPEG_LIBS) $(SDL_LIBS)) $(LDLIBS)

PROGRAMS=       GetVideoFrames                    \
                GetAudioFrames                    \
                PlayVideoFrames                   \
                PlayAudioFrames                   \
                SyncVideo                         \
                SyncAudio                         \
                MultiThread                       \
                MultiThread_display_in_main       \
                MultiThread_display_in_thread     \
                SimplePlayer                      \
                AVTimestamps                      \
                GetInfo                           \
                SimplePlayer_filter               \
                SimplePlayer_multithread          \
                Filter_test                       \
                Video_Filter_test                 \

OBJS = $(addsuffix .o,$(PROGRAMS))
# implicit add LDLIBS and the objs with the same prefix name as the target
# implicit compile target with CFLAGS

# explicit add custom objects
CUSTOM_OBJS =   Clock.o                           \
                Queue.o                           \

FILTER_OBJ = Myfilter.o

SimplePlayer:                    $(CUSTOM_OBJS)
SimplePlayer_filter:             $(CUSTOM_OBJS)
SimplePlayer_multithread:        $(CUSTOM_OBJS)
SyncAudio:                       $(CUSTOM_OBJS)
MultiThread:                     $(CUSTOM_OBJS)
MultiThread_display_in_main:     $(CUSTOM_OBJS)
MultiThread_display_in_thread:   $(CUSTOM_OBJS)
AVTimestamps:                    $(CUSTOM_OBJS)
Filter_test:                     $(CUSTOM_OBJS) $(FILTER_OBJ)
Video_Filter_test:               $(CUSTOM_OBJS) $(FILTER_OBJ)

.phony: all clean

all:    $(OBJS) $(PROGRAMS)

clean:
	$(RM) $(PROGRAMS) $(OBJS) $(CUSTOM_OBJS) $(FILTER_OBJ)
