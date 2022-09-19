# AMS325_hw2

# pi_est

    function pe = pi_est(Ntotal)

        %Use to store the number of points inside circle
        Ninside = 0;

        %Loop for each number of points in vector Ntotal
        x=2*rand(1,Ntotal)-1;
        y=2*rand(1,Ntotal)-1;

        for i = 1:Ntotal
            %if the point is inside the circle
            if x(i)^2+y(i)^2 <= 1
                %Increase number of points inside by 1
                Ninside = Ninside + 1;
            end
        %compute the estimated value of pi for ith number of points
        pe = 4*(Ninside/Ntotal);
    end


# HW2_Q1

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
    saveas(gcf,'pi_est','svg')


# pi_est2

    function pe = pi_est2(tol)
        N_inside = 0;
        pe = 0;
        pi_est = pi;
        n = 1;
        Ntotal = 1000;
    
        while abs(pi_est)/pi <= tol && Ntotal <= 1000000
            x=2*rand(1,Ntotal)-1;
            y=2*rand(1,Ntotal)-1;
            while (n <= Ntotal)
                if x(n)^2+y(n)^2 <= 1
                    N_inside = N_inside + 1;
                end
                n = n + 1;
            end
            %compute the estimated value of pi for ith number of points
            pe = 4*N_inside/Ntotal;
            %convert pi_est into while loop's abs(pi_est-pi)
            pi_est = pe;
            %loop can be ended by multiplying Ntotal by 2
            Ntotal = Ntotal * 2
        end
        pe
    end


# HW2_Q2

    %% 2-a

    t = -5:-1:-10;
    tol = 2.^t;
    piest =zeros(1,6);
    computeCost = zeros(1,6);
    i = 1;
    for k=5:1:10
        tic
        piest(1,i) = pi_est2(2^-k);
        computeCost(1,i) = toc;
        i = i + 1;
    end
    piest

    %% 2-b
    figure
    plot (tol, computeCost, '-r*')
    title('computational cost versus tol')
    xlabel('tol')
    ylabel('computational cost')
    saveas(gcf,'pi_est2','svg')


# cirrdn

    function cirrdn(Ntotal)
        figure;
        hold('on');
        grid on;
        axis([-1, 1, -1, 1])
        video = VideoWriter('piest.avi');
        open(video);
        %generating x,y
        x=2*rand(1,Ntotal)-1;
        y=2*rand(1,Ntotal)-1;
        for i = 1:Ntotal
            if ((x(i)^2+y(i)^2<=1))
                scatter(x(i),y(i),'r')
                drawnow;
            elseif ((x(i)^2+y(i)^2>1))
                scatter(x(i),y(i),'b')
                drawnow;
            else
                break
            end
            writeVideo(video, getframe(gcf));
        end
        hold('off');
        close(video);
    end
