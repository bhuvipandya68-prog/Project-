# Project-
Fujk
clc;
clear;
close;

A = 5;              // Amplitude
f = 1;              // Frequency (KHz)
fs = 1000;          // Sampling frequency (KHz)
t = 0:1/fs:1;       // 1 cycle of sine wave

x = A*sin(2*%pi*f*t); // Input signal
mu = 255; // standard μ Value

x_comp = sign(x).*log(1 + mu*abs(x)) / log(1 + mu); // Compression (μ-law)
x_exp = sign(x_comp).*((1 + mu).^abs(x_comp) - 1) / mu; // Expansion (μ-law)
scf()
subplot(3,1,1)
plot(t, x)
xtitle('Original Signal','Time','Amplitude')
subplot(3,1,2)
plot(t, x_comp)
xtitle('Compressed Signal (μ-law)','Time’, ‘Amplitude')
subplot(3,1,3)
plot(t, x_exp)
xtitle('Expanded Signal (Recovered)','Time’, ‘Amplitude')







exp 6
clc
clear 
close 
disp('************SNR calculations for PCM ****************')
N=input(' Enter number of bits used in PCM (N) :');
SNRDB1=(1.78+6*N);
SNRDB2=(4.78+6*N);
disp('SNR(dB) for PCM if signal is sinusoidal is = ')
disp(SNRDB1);
disp('SNR(dB) for PCM if signal is non-sinusoidal is = ')
disp(SNRDB2);
disp('----------------------------------------------------')
disp('************SNR calculations for DM ****************')
fm=input('Enter modulating signal frquency  used in  DM(fm in Hz) :');
// Lets assume bandwidth W=fm 
W=fm;
fs=input('Enter sampling frquency  used in  DM(fs in Hz) :');
SNR3=(3*fs^3)/(8*%pi^2*W*fm^2);
SNRDB3=10*log10(SNR3);
disp('SNR(dB) for DM  is = ')
disp(SNRDB3);
disp('----------------------------------------------------')





exp 8
clc;
clear;
close;

t = -10:0.01:10;
T = 4;
fm = 1/T;
x = cos(2 * %pi * fm * t);

// Plot continuous time signal
subplot(2, 2, 1);plot(t, x);
xtitle('E2125Continuous time signal','Time','x(t)');

// Different sampling frequencies
fs1 = 1.6 * fm;
fs2 = 2 * fm;
fs3 = 8 * fm;

//  Recovered signal with fs < 2fm
n1 = -4:1:4;
x1 = cos(2 * %pi * fm / fs1 * n1);
subplot(2, 2, 2);plot2d3('gnn',n1,x1); plot(n1, x1, 'b'); 
xtitle('Recovered signal with fs < 2fm','Time','x(n)');
xgrid; 

// Recovered signal with fs = 2fm
n2 = -5:1:5;
x2 = cos(2 * %pi * fm / fs2 * n2);
subplot(2, 2, 3); plot2d3('gnn',n2,x2); plot(n2, x2, 'g')
xtitle('Recovered signal with fs = 2fm','Time','x(n)');
xgrid;

//  Recovered signal with fs > 2fm
n3 = -20:1:20;
x3 = cos(2 * %pi * fm / fs3 * n3);
subplot(2, 2, 4); plot2d3('gnn',n3,x3); plot(n3, x3, 'r')
xtitle('Recovered signal with fs > 2fm','Time','x(n)');
xgrid;

