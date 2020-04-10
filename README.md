# Beads-and-Leads

Note that the video and music are out of sync slightly in the examples. This is due to me pushing my computer to the limit to process all of the data. If there were less points, it would run in real time. 

In the above project I map frequency data to $[0, 2\pi]$ a fixed number of frequencies in order to steer a point in the plane based on the amplitude. I use the naming convention $beads$ and $leads$ to describe the two differnt kinds of objects points I am working with. When you run the code you will see a lot of small points and 2 large ones, one color for each. These $beads$ (small) and $leads$ (large) are independent groups. Each group has 1 $lead$ and an arbitrary amount of beads. 

In order to steer a $lead$, I take some arbitrary interval of frequencies and their respective amplitude, $[(f_0, a_0), ... , (f_n, a_n)]$, and map it to $[0, 2\pi]$ so that I have $[(f_0, a_0, 0), (f_0, a_0, \theta_1), ... , (f_0, a_0, \theta_{n-1}), (f_n, a_n, 2\pi)]$. For each frame of the animation, I caculating a rolling sum of radians and average them conditioned on the fact that the amplitude for a given frequency exceeds a chosen threshold. Say I have the interval $[0,500]$ Hz and at some time $t$ a pure note is being played at 250Hz, then I would add $\pi$ to my angle variable; as a result the $lead$ would move directly to the left. Specifically, $\theta_{\mu} = \frac{1}{n} \sum_{i=1}^{n}\theta_i$ and $f_{\mu} \frac{1}{n} \sum_{i=1}^{n}f_i$ such that given it's old positions $x_0, y_0$. The new positions are

$\begin{align}\begin{center}
x0+f_{\mu}cos(\theta_{\mu}) \\ y0+f_{\mu}sin(\theta_{\mu}).
\end{center}
\end{align}
$

Still for the same frame, after I have calculated a $leads$ new position, I calculate the distance from the $lead$ to every single $bead$ in the corresponding group and add the vector of distances, $\frac{1}{dist}$, to the vector containing the x,y-coordinates of the beads. 

Note that almost everything I have mentioned is scaled by some constant to make things look smooth, these can be initialized in the parent class containing the paramaters. Also, in my syntax you might notice that I am a bit verbose when it comes to iterating over the intervals despite knowing I only am working with two in this particular version of the project i.e. range(len(self.intervals)). This is because in other versions of the project I have more than just two intervals. 

That is about it. I would like to add inter-group interactions to make it more dynamic but we will see about that.

# Sources

[Audio Processing With Python](https://www.youtube.com/watch?v=AShHJdSIxkY)

[Matplotlib: Axes.plot](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.axes.Axes.plot.html#matplotlib.axes.Axes.plot)

[Matplotlib: Line2D](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.lines.Line2D.html)



