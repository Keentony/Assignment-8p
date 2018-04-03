%Assignment 8P
%Antonio Hernandez

clear clc

L = pi;
T = 10;
D = 0.1;
k = 1;
N = 10;
h = (L/(N+1));
Lam = 0.1*(10/pi^2);


%Evaluating the different graphs for 
%the exact solution with t= T/5, T/2 and T

x = zeros(1,N);
for j = 1:N
    x(j) = j*h;
end

Uexact = zeros(1,N);

for t = T/5;
    for j = 1:N;
        Uexact1(j) = exp(-D*(k^2)*t)*sin(k*j*h);
    end
end

for t = T/2;
    for  j = 1:N;
        Uexact2(j) = exp(-D*(k^2)*t)*sin(k*j*h);
    end
end


for t = T;
    for  j = 1:N;
        Uexact3(j) = exp(-D*(k^2)*t)*sin(k*j*h);
    end
end


plot(x,Uexact1)
hold on
plot(x,Uexact2)
hold on
plot(x,Uexact3)

