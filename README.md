# Beads-and-Leads
[Audio Visualizer Using Matplotlib](https://nbviewer.jupyter.org/github/magi-1/Beads-and-Leads/blob/master/beads_leads.ipynb)

In the above project I map frequency data to $[0, 2\pi]$ in order to steer a point in the plane based on the amplitude. I use the naming convention $beads$ and $leads$ to describe the two differnt kinds of data points I am working with. When you run the code you will see a lot of small points and 2 large ones, one color for each. These $beads$ (small) and $leads$ (large) are independent groups. Each group has 1 $lead$ and an arbitrary amount of beads. 

In order to steer a $lead$, I take some arbitrary interval $[(f_0, a_0), ... , (f_n, a_n)]$ Hz and map it to $[0, \theta_1, ... , \theta_n]$. For each interval, I have a list of frequencies and their corresponding amplitudes. As I iterative over the list, if the amplitude threshold is exceeded, I take the corresponding angle and add it to a 0 variable. Note that I repeat this process for each frame in the animation. Say I have the interval $[0,500]$ Hz and at some time $t$ a pure note is being played at 250Hz, then I would add $\pi$ to my angle variable; as a result the $lead$ would move directly to the left. Specifically, $\sum_{i=1}^{n} f_i*cos(\theta_i)$ for a $leads$ x-coordinate and so on.

Then after I have calculated a $leads$ new position, I calculate the distance from the $lead$ to every single $bead$ in the corresponding group and add the vector of distances, $\frac{1}{dist}$, to the vector containing the x,y-coordinates of the beads. 

Note that almost everything I have mentioned is scaled by some constant to make things look good and smooth, these can be instantiated in the parent class containing the paramaters. Also, in my syntax you might notice that I am a bit verbose when it comes to iterating over the intervals despite knowing I only am working with two in this particular version of the project i.e. range(len(self.intervals)). This is because in other versions of the project I have more than just two intervals. 

That is about it. I'm currently in the process of adding inter-group interactions to make it more dynamic. 

# Sources

[Audio Processing With Python](https://www.youtube.com/watch?v=AShHJdSIxkY)

[Matplotlib: Axes.plot](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.axes.Axes.plot.html#matplotlib.axes.Axes.plot)

[Line2D](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.lines.Line2D.html)



