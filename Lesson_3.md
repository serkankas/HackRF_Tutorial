# Lesson 3

Decibel

I am not sure why the course has a specific video in the series about decibels but here's how it simply explains the decibel.

$$10:1 = 1 Bel$$
$$10:1 = 10 dB$$

$$100:1 = 2 Bel$$
$$100:1 = 20 dB$$

$$1000:1 = 3 Bel$$
$$1000:1 = 30 dB$$

So help of two ratios will be given in below is going to help you to measure dB in most cases.

$$ 3dB \approx 2.1 $$
$$ 10dB = 10 $$

With the help of these two, we could easily approximate the dB conversion like in the example

```assume that x = 2mW and y = 40mW. Find y based on x with decibel ratio.```

$$ x = 2mW $$
$$ y = 40mW $$
$$ y = 20 * (2mW) $$
$$ y = 20 * x $$
$$ y = (20:1) * x $$
$$ y = [(10 * 2 ):1] * x $$
$$ y = (10 * 2)dB * x $$
$$ y \approx (10dB + 3dB) x $$
$$ y \approx 13dBx $$

The thing that may be found strange is, how we convert from multiplication to addition. You should remember from the top explanation that decibel does not behave linear but it behaves logarithmic. Linear multiplication means logarithmic addition.

We should keep in mind that the decibel could go negative values for division application.

$$ 2:1 \approx 3dB $$
$$ 1:2 \approx -3dB $$
$$ 1:1 = 0dB $$

It may confusing at beginning but this is how should be said for relative to

```let's assume that x = 2y```

$$ x \approx 2y $$
$$ x \approx 3dBy $$
$$ y \approx -3dBx $$

in other world example. Let's assume that gain is opposite scenario of loss. In this case

$$ 3dB loss = -3dB gain $$
since
$$ loss = 1 / gain$$

<hr>

There is an assignment homework for decibel to ratio chart convertion. I will skip that part since I do NOT think that it's essential anyway.<br>
See you in other lecture notes.