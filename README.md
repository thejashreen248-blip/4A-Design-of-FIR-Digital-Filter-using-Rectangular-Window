# Design-of-FIR-Filters-using-rectangular-window
#          DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of low pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 

clc;
clear;
close;

// Input values
M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off frequency = ');

// Centre value
alpha = (M - 1)/2;

// Ideal LPF impulse response
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = Wc/%pi;
    else
        hd(n) = sin(Wc*((n-1)-alpha)) / (((n-1)-alpha)*%pi);
    end
end

// Rectangular Window
for n = 1:M
    W(n) = 1;
end

// Windowing process
h = hd .* W;

// Display filter coefficients
disp(h, 'Filter Coefficients are');

// Frequency response
[hzm, fr] = frmag(h, 256);

// Magnitude response
subplot(2,1,1);
plot(2*fr, hzm);
xlabel('Normalized Digital Frequency W');
ylabel('Magnitude');
title('Frequency Response of FIR LPF using Rectangular Window');

// Magnitude response in dB
hzm_dB = 20*log10(hzm);

subplot(2,1,2);
plot(2*fr, hzm_dB);
xlabel('Normalized Digital Frequency W');
ylabel('Magnitude in dB');
title('Frequency Response of FIR LPF using Rectangular Window');



# OUTPUT
<img width="752" height="662" alt="image" src="https://github.com/user-attachments/assets/c497d22a-cc08-420b-af26-e9d87785dee8" />

# RESULT
Thus design of low pass FIR digital filter waveforms were plotted and output was verified. 
