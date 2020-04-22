# Steam Controller Singer

This project is a fork of [Roboton3042's fork](https://github.com/Roboron3042/SteamControllerSinger) of [Pila's SteamControllerSinger](https://gitlab.com/Pilatomic/SteamControllerSinger) including Roboton3042's dirty fix to make the Steam Controller sing again. 
Also I added the feature to pick which 2 channels will Steam Controller sing, instead of just the first 2, yay!

## HOW TO

1. Turn on your Steam Controller
2. Drag the midi file onto steamcontrollersinger executable
3. When prompted, press ENTER
4. Enjoy!

### Where can I find midi songs?

You can find midi songs ready to be played with Steam Controller Singer in my [Roboton3042's Collection](https://mega.nz/#F!BWpEWKzB!r7WPw5bZ_domN4pk-FJsjg). You can also download midi songs from various websites such [musescore.com](https://musescore.com/), but they may or may not be ready to be played with Steam Controller Singer (see Midi files tips in that case).

### Usage from command prompt:
	steamcontrollersinger [-r][-l DEBUG_LEVEL] [-i INTERVAL] [-yLEFT_CH] [-tRIGHT_CH] MIDI_FILE

	-i INTERVAL argument to choose player sleep interval (in microseconds). Lower generally means better song fidelity, but higher cpu usage, and at some point goidn lower won't improve any more. Default value is 10000

	-l DEBUG_LEVEL argument to choose libusb debug level. Default is 0, no debug output. max is 4, max verbosity output
	
	-r to enable repeat mode, which plays continously (restart the song when finished)
	
	-y and -t to enter which channel from midi should play on left/right haptic respectively

### Midi files tips:

Midi files may need to be edited with a software such [MidiEditor](https://www.midieditor.org/) to be correctly played with Steam Controller Singer following the next tips:

* Notes from midi channel 0 are played on right haptic
* Notes from midi channel 1 are played on left haptic
* Notes from others channels are ignored
* **Avoid multiple notes active at the same time on the same channel**, since haptic actuators can only play one note at the time.

## CHANGELOG
[V1.8]
* Added channel pick feature

[V1.7]
* Fixed music stopped playing after a few seconds

[V1.6]
* Fixed major bugs in playback algorithm

[V1.5]
* Changed debug level argument from -d to -l
* Added -r argument to enable demo mode
* Enhanced arguments parsing
* Does not rely on Steam Controller duration anymore
* Updated note display
* Now stops playing when interrupting the process ( on Ctrl+C )

[V1.4]
* Fixed a bug in MIDI librairie that would compute a null duration for notes when ON event and previous OFF event had the same timetick

[V1.3]
* Added -iINTERVAL argument
* Added -dDEBUG_LEVEL argument 

[V1.2]
* Fixed being stuck on "Command error" when disconnecting controller while playing. Now continue playing (even if keep failing)
* Removed the now deprecated 20ms note duration reduction
