# Recurrent Sands Browser-Based Music Application

Recurrent Sands is a browser-based musical instrument created as part of the "BitRate: Machine Learning & Music Series" contest hosted by Gray Area and the Magenta team at Google Research.

The instrument connects two exciting areas of development within the world of electronic music: granular synthesis and machine learning. I have attempted to reconcile transparency and a user-friendly aesthetic, avoiding technical language wherever possible in the interface. Below is an overview of the instrument and its techniques:

Granular synthesis is a digital signal processing technique that uses as its source an audio buffer, typically a few seconds long but potentially much shorter. This instrument allows 8 buffers to loop at a time. Upon start, the first part begins playing automatically; additional loops can be added by pressing the radio buttons displayed below "Sound Selector". The currently selected buffer is visualized through a real-time oscilloscope, a real-time spectrogram, and a static waveform display of its full contents. It can be manipulated through four X/Y control pads:

"Start Position & Loop Size": The X coordinate sets the relative start position of the loop, ranging from the beginning to the end of the buffer's length. The Y coordinate sets the size of the loop's playback, ranging from its full length (bottom coordinate) to one millisecond (top coordinate), which plays as a steady 1000Hz tone with a timbre dependent on the source material. When the buffer's end point is smaller than its start point, the buffer plays in reverse. This occurs in the lower triangle formed by the diagonal between the bottom-left and top-right vertices of the pad.

"Playback Rate & Detune": The X coordinate controls the playback rate, which ranges from one-tenth to ten times the normal speed of the loop. The Y coordinate controls the pitch, which ranges from one octave below to one octave above the normal pitch. These two parameters are decoupled from each other, allowing independent manipulation of the speed and pitch.

"Grain Size & Overlap": Per the ToneJS API: "The grainSize is the amount of time each small chunk of audio is played for and the overlap is the amount of crossfading transition time between successive grains." The X coordinate sets the grain size, and the Y coordinate sets the overlap (both ranging from 0 to 2 seconds). Setting the overlap larger than the grain size can create interesting textural washes, while manipulating these controls in conjunction with the playback rate can create interesting rhythmic and timbral patterns.

"Grain Size & Overlap": Per the ToneJS API: "The grainSize is the amount of time each small chunk of audio is played for and the overlap is the amount of crossfading transition time between successive grains." The X coordinate controls the grain size, and the Y coordinate controls the overlap (both ranging from 0 to 2 seconds). Setting the overlap larger than the grain size can create interesting textural washes, while manipulating these controls in conjunction with the playback rate can create interesting rhythmic and timbral patterns.

"Filter & Delay": The X cordinate controls a low-pass filter set in the range from 1000Hz to 16000Hz. The Y coordinate controls a delay. From the bottom coordinate through the fourth quintile, this controls the percentage of delay mixed with the signal, with the bottom coordinate passing a dry signal and 80% passing a wet signal. The top quintile of the Y axis adds additional feedback to the signal's delay path. The length of the delay is randomized for each synth at the program's load.

The Synthesis Selector creates a neural network-generated melody, which is played in parallel by a digital synthesizer and a corresponding granular sample. At startup, a seed chord is generated, which both sets the instrument's synthesizer drone and the seed for the neural network generation. The last three notes from the generated part are fed into the model as the notes for the next seed, creating a recursive relationship that can build under the user's temporal control. The length of the melody can be set using the slider in the bottom right, while the global tempo is set directly above. Very high tempi do tend to cause generation to slow significantly.

The dropdown menu in the 4th column displays the sounds that are pre-loaded to each buffer. By default, each of the 8 "Sound Selector" parts corresponds to its matching sound in the dropdown menu. The buffer for the current looping part (displayed by the radiobutton) can be replaced at any time by choosing a new sound from the dropdown menu. When the user records audio input or loads a file, the dropdown menu expands with the new user sound, and the new sound replaces the buffer for the currently selected looping part. The overdub button records all current computer output (sans master-bus reverb). This allows the user to capture neural-network-generated synthesis parts, as well as specific textures designed and manipulated live by the user through the X/Y control pads.

The volume controls are to the right, along with volume buses for both the granular parts and the digital synthesizers. There is also a volume control for the drone synthesizer, which begins when the user presses the start button. Its chord is reset alongside the melodic seed each time a new melody is generated.

When the user records, an audio source will appear above the instrument. This source can be downloaded, and will always display the latest recorded audio. It's intended for quick capture of ideas, but given that it saves in the compressed .ogg and doesn't include the reverb, I'd suggest using internal routing to a DAW or a VLC-like player for extended recording.

Acknowledgements:
This instrument uses extensive resources from Tone.js, NexusUI, P5.js, and Magenta.js. Thank you all to the developers that have worked on these projects, as well as to Tero Parviainen, and Rachel Rose Waterhouse for the inspiring presentations given as part of this contest. Thank you to Gray Area and Google Magenta for their work in this space and their efforts to build an inclusive and encouraging community around these topics.