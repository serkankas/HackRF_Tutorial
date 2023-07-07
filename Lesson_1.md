# Lesson 1

I will follow the link that's been given in the [README](/README.md) file.

| Abbreviations | Definitions
| --- | ---
| SDR | Software Defined Radio
| RF | Radio Frequency
| DSP | Digital Signal Processing
| LPF | Low Pass Filter
| HPF | High Pass Filter
| GNU | GNU's Not Unix (programmer jokes for nested functions)
| FFT | Fast Fourier Transform
| GUI | Graphical User Interface
| WBFM | Wide-Band Frequency Modulation

For Platform

We are going to use:
* HackRF One with Portapack H2 (hopefully with USB serial connected to PC)
* GNU Radio (v3.10.6.0)

We are going to create Hello world base of RF processing by creating FM Radio Receiver.<br>
In the backside, GNU Radio uses Python and generate Python. ~~That's an advantage from my side since I'm an experienced Python Programmer~~.<br>
GRC is handling the creation of python program for us. The interface is a bit different than what it shown in video. But hopefully, it'll be okay.

After watching first video and with the current version of GNU Radio Companion, I am ended up with this example.

<hr>

![Picture](/Pictures/1.png)

This picture contains lot of information and we will go through all of them one by one. I will skip through the installation process. However if you need links for installation, [Here's the link for SDR Driver](https://hackrf.readthedocs.io/en/latest/installing_hackrf_software.html) and [Here's the link for GNU Radio Companion](https://wiki.gnuradio.org/index.php/InstallingGR).<br>
If you have HackRF One with Portapack H2, like mine, you should use in HackRF mode instead of standalone mode. Connecting via USB will make the data transition between PC and HackRF.

![Picture](/Pictures/2.jpg)

After these settings, HackRF GNU Companion should work without any problem.

<hr>

![Picture](/Pictures/3.png)

This is Python Terminal part of the program. Do NOT assume that it's a shell that you can type bunch of code, NO! You can only debug if is there any error in your structure for schema.

<hr>

![Picture](/Pictures/4.png)

This is the part where you can visualize your progress. These are the QT Widget parts we could say. How the GUI elements are working will be explaining deeply in next sessions.

<hr>

![Picture](/Pictures/5.png)

For easier to follow, I divide the screen into 8 part. Before I explain the concepts, I need to tell couple things. First, CTRL + C & CTRL + V for pasting lead program to crush. So, you should avoid to use keyboard shortcut for them. Second, There is no autosave in program so keep in that mind. If your program crushes everything you did will be losen. Last, Running code with section 7 (I will explain), also saves the code. Keep these things in mind.

Sections:

1. Option Part: This part basically contains general information about your structure. What output you want as program, mine is selected as Python, What Generating Options you want to use, selected and supported as QT at this version, title, etc.
1. The Variables: In order to follow structure in easier way, we use variables. I will not explain whole concept of variables anyway, so feel free to check why we use variables, etc.
1. QT Gui Range Widget: That's the part where we control our slider in GUI
1. Importing tab: We could find and import the necessary tool to our structure from that part. Drag and drop working, so highly recommend to use that way.
1. Small Python Debug Console: If you don't want to use that black screen, here is an small alternative for it.
1. The Structure/Schema: I will dive into individual parts later but this part, we could say, where we built our structure/schema/program with the help of gui.
1. Execution Section: This is the part where we built, execute/run, determine the code.
1. Clipboard Section: This is the section where you can use copy, paste, cut, delete instead of keyboard shortcut, because the keyboard shortcuts lead to crash program anyway.

<hr>

With that being said, let's dive more into Structure Part

![Picture](/Pictures/6.png)

I will explain every block the meaning and why we used it but you should also know the variables so, here's the variables for easier to follow. The not mentioned sections in blocks are probably entered manually.

![Picture](/Pictures/7.png)

Structure Parts:

1. Osmocom Source: This is the part where the program knows that the source of structure is HackRF. I didn't specified any of the USB. It automatically capture which USB is HackRF. Sample rate is already binded to variable __sam_rate__, and I tune the device with __hw_freq__. 
1. Signal Source: This is the part where we want to adjust our frequency. With example, If we want to adjust our frequency to any lower or higher, we set our __sw_shift_freq__ variable as needed and make both signal input the 3. block
1. Multiply: This is a simple mathematical multiplication operation. ~~I am not an expertise on DSP, but I assume multiplication with Time Based signal has shifting effect on Frequency Domain?~~
1. QT GUI Frequency Sink for HackRF: This is QT Widget that used for showing original tune for machine. However, it's shown gray since I disable to show.
1. QT GUI Frequency Sink for tuned Frequency: This is show panel in GUI section. Center Frequency is set as __hw_freq - sw_shift_freq__. Just for demo purpose.
1. LPF: In radio usage, we low pass the signal the abstract the audio signal from carrier signal. Sampling rate should be minimum doubled frequency of your highest desired frequency. We set Cut of frequency little bit higher since the behaviour of filter is, ~~probably~~, not the ideal.
<br>![Picture](/Pictures/8.png)
<br>Decimation part is where we lower our frequency with division. That part written as __samp_rate / freq_bandwith__<br>
How we need to do simple math. samp_rate = 10M, bandwith = 200k -> decimation is 50. So, 10M / 50 -> 200k (We are going to use this number for further blocks. It should be adjusted carefully.)
1. Rational Sampler: This is also used for adjusting the previous calculation. You remember that we had 200KHz signal that given to us. We need to adjust into a frequency range that our soudcard most likely support. Most soundcard also support 48k so, we are going to adjust based on that.
<br>200k * 12 / 5 = 480k
1. WBFM Receiver: This part is also fine tune our signal to something that our soundcard process and we could hear from application.
<br> 480k / 10 = 48k (Audio Sampling)
1. Multiply By Const: This one is used audio amplification. If you remember QT GUI Range (Slider for GUI Application), we gave input as that application name __audio_gain__.
1. Audio Sink: The application that allow us to receive signal as sound.

<hr>

With these information, all the first lesson notes are shared.<br>
See you in other lecture notes.