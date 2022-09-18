# AMS325_hw2
%% 1-a

%creating vector of values from 10 to 20
%%compute the number of points 2^k
piest = zeros(1,11);
i = 1;
for k=10:1:20
    piest(1,i) = pi_est(2^k);
    i = i + 1;
end
piest

%% 1-b

k=10:1:20;
Ntotal=2.^k;
yyaxis left
semilogx(Ntotal , piest);
ylabel('Est\pi');

yyaxis right
semilogx(Ntotal , abs(piest-pi));
ylabel('|Est\pi-\pi|')

xlabel('Ntotal')
