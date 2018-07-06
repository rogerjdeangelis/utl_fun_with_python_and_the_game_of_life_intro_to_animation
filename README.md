# utl_fun_with_python_and_the_game_of_life_intro_to_animation
Fun with python and the game of life intro to animation.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

    Fun with python and the game of life intro to animation;

    see anamation (you have to download - or just view the DZONE aniimation)
    https://tinyurl.com/ycam8clu
    https://github.com/rogerjdeangelis/utl_fun_with_python_and_the_game_of_life_intro_to_animation/blob/master/utl_fun_with_python_and_the_game_of_life_intro_to_animation

    github
    https://tinyurl.com/yahxk5wv
    https://github.com/rogerjdeangelis/utl_fun_with_python_and_the_game_of_life_intro_to_animation

    DZONE
    https://tinyurl.com/y7unxuur
    https://dzone.com/articles/game-of-life-with-python-1?edition=385198&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-05

    INPUT
    =====

       %let generations=800;

       May want to reduce the number of generations
       800 takes about 2 minutes


    PROCESS (All the python code)
    ==============================

       Note the macro variable and output path.

       %utl_submit_wps64("
       options set=PYTHONHOME 'C:\Progra~1\Python~1.5\';
       options set=PYTHONPATH 'C:\Progra~1\Python~1.5\lib\';
       libname sd1 'd:/sd1';
       proc python;
       submit;
       import numpy as np;
       def life(X, steps):;
       .   def roll_it(x, y):;
       .       return np.roll(np.roll(X, y, axis=0), x, axis=1);
       .   for _ in range(steps):;
       .       Y = roll_it(1, 0) + roll_it(0, 1) + roll_it(-1, 0) \;
       .           + roll_it(0, -1) + roll_it(1, 1) + roll_it(-1, -1) \;
       .           + roll_it(1, -1) + roll_it(-1, 1);
       .       X = np.logical_or(np.logical_and(X, Y ==2), Y==3);
       .       X = X.astype(int);
       .       yield X;
       X = np.zeros((40, 40));
       X[23, 22:24] = 1;
       X[24, 21:23] = 1;
       X[25, 22] = 1;
       from matplotlib import pyplot as plt;
       import matplotlib.animation as manimation;
       FFMpegWriter = manimation.writers['ffmpeg'];
       metadata = dict(title='Game of life', artist='JustGlowing');
       writer = FFMpegWriter(fps=10, metadata=metadata);
       fig = plt.figure();
       fig.patch.set_facecolor('black');
       with writer.saving(fig, 'd:/mp4/game_of_life.mp4', 200):;
       .   plt.spy(X);
       .   plt.axis('off');
       .   writer.grab_frame();
       .   plt.clf();
       .   for x in life(X, &generations):;
       .       plt.spy(x);
       .       plt.axis('off');
       .       writer.grab_frame();
       .       plt.clf();
       endsubmit;
       run;quit;
       ");


    OUTPUT
    ======

    https://tinyurl.com/ycam8clu


