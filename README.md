%Assignment 8P
%Antonio Hernandez

clear; clc

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

for t = T/5
    for j = 1:N
        Uexact1(j) = exp(-D*(k^2)*t)*sin(k*j*h);
    end
end

for t = T/2
    for  j = 1:N
        Uexact2(j) = exp(-D*(k^2)*t)*sin(k*j*h);
    end
end

for t = T
    for  j = 1:N
        Uexact3(j) = exp(-D*(k^2)*t)*sin(k*j*h);
    end
end

%{
plot(x,Uexact1);
hold on
plot(x,Uexact2);
hold on
plot(x,Uexact3);
%}

%Setting the matrix D for coefficients of n+1 terms
A1 = (2+2*Lam)*ones(1,N);
A2 = -Lam*ones(1,N-1);
A = diag(A1);
B = diag(A2,1);
C = diag(A2,-1);
D = A+B+C;

%Setting the matrix G for coefficients of n terms
E = (2-2*Lam)*ones(1,N);
F = diag(E);
G = F+(-B)+(-C);

%Setting the matrix for the boundary condition of 
%u(x,0)=f(x)
for j = 1:N
    Ut0(j) = sin(k*h*j);
end

%Evaluating the first set of Un+1 terms aka t=1
Un1t1 = ((Ut0*G)')\D;
%The second set of Un1t2 should equall the Uexact1 
%values which are at t=2
Un1t2  =((Un1t1*G)')\D;
%Implementing pseudo code to repat the process 
%of updating the Un values and solce for Un+1
a(1) = 0;
a = (2+2*Lam)*ones(1,N);

