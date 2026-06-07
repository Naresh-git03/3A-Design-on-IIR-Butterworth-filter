# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```c
clc;
close;

wp=input('Enter the pass band frequency (Radians) = ');
ws=input('Enter the stop band frequency (Radians) = ');
alphap=input(' Enter the pass band attenuation (dB)= ');
alphas=input(' Enter the stop band attenuation(dB)= ');
T=input('Enter the Value of sampling Time=');

omegap=(2/T)*tan(wp/2);
disp(omegap,'omegap=');

omegas=(2/T)*tan(ws/2);
disp(omegas,'omegas=');

N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));
disp(N,'N=');

N=ceil(N);
disp(N,'Round off value of N=');

omegac=omegap/(((10^(0.1*alphap)-1)^(1/(2*N))));
disp(omegac,'omegac=');

disp('Normalised Analog LPF Transfer function H(S)=');
hs_Normalised = analpf(N,'butt',[0,0],1);
disp(hs_Normalised);

disp('Analog LPF Transfer function H(S)=');
hs = analpf(N,'butt',[0,0],omegac);
disp(hs);

z=poly(0,'z');

Hz=horner(hs,(2/T)*((z-1)/(z+1)));

disp('Digital LPF Transfer function H(Z)=');
disp(Hz);

HW=frmag(Hz,512);
w=0:%pi/511:%pi;
plot(w/%pi,abs(HW));

xlabel('Normalized Digital Frequency w');
ylabel('Magnitude ');
title(' Frequency Response of Butterworth IIR LPF');
```

# CALCULATIPNS:

<img width="1600" height="903" alt="edec0633-64d2-41c4-b687-dfb4c7d9da1b" src="https://github.com/user-attachments/assets/78574da1-258e-42d2-885f-dd58af235bfb" />
<img width="1600" height="903" alt="12f62c63-3807-4e51-b510-2cee1009f561" src="https://github.com/user-attachments/assets/496ef0ff-ba27-4f96-9917-8ea09b57df50" />


# OUTPUT: 
<img width="1920" height="1200" alt="Screenshot 2026-05-26 110911" src="https://github.com/user-attachments/assets/64aafa17-989e-4252-97b3-646bb12fe913" />


# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.

