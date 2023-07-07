# Lesson 2

Basics of DSP

In DSP, we usually handle time-based signals. However, the domains that we deal is not always time thou. We often switch to the frequency domain since it's easier to apply and to handle more complex problems. Although the frequency domain is not the only domain you can work on, it is probably the most common one. Using FFT, the signal can be switched between the time and the frequency domain. <br>
Let's have a look at how we handle signals in real-life scenarios. Analog signals are continuous and have an infinite range of values between two points. However, it is not applicable mathematically in computer systems. In order to handle analog signals, the quantization and sampling process needs to be taken.<br>
Sampling is a process that we chop continuous signals into small sections and capture them one by one in order to make the whole signal discrete.<br>
Quantization is estimating and initiating the value from the infinite range to the more arrangeable range.<br>
With the end result, we are able to convert analog signals to digital, which is the beginning of the DSP areas.

![Picture](/Pictures/9.avif)

As you can see in the picture, its divide 8 section for signal amplitude definition (or quantization we could say), and 1 second is divided into 10 part which means the sampling rate is 10Hz.

<hr>

We could experimentally see progess with help of GNU radio by changing frequency, sampling frequency, amplitude, etc. I create a simple example for just see the relation between signal frequency and amplitude and response at frequency domain.

![Picture](/Pictures/10.png)

<hr>

I didn't add anything new in this lesson so, see you in other lectures note.