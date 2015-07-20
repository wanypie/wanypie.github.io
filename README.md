# wanypie.github.io
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {
    "collapsed": true,
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "#Identifying important 21st century STEM competencies \n",
    "##Using data of workplaces\n",
    "### Hyewon Jang\n",
    "\n",
    "[http://wanypie.github.io/](http://wanypie.github.io/)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "subslide"
    }
   },
   "source": [
    "##Gaps between education and required skills\n",
    "\n",
    "###Do we, STEM educators, know what competencies are important for STEM disciplines?\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "##Motivation\n",
    "Henry Petrosky,Professor of Duke Civil and Environmental Engineering:\n",
    "<blockquote>...engineering criteria was a failure from the perspective of practicing engineers</blockquote>\n",
    "[Invention by design : how engineers get from thought to thing. 1996, Cambridge, Mass.: Harvard University Press]\n",
    "\n",
    "How should we identify important competencies?"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "##Our Approach\n",
    "* Data collected directly from employess of most occupations\n",
    "* Categorization using framework of human general performance\n",
    "* Comparison our results with previous frameworks relevant to 21st century skills and engineering education\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "##Data\n",
    "###The Occupational Information Network (O*NET)\n",
    "\n",
    "* Dictionary of occupations which involve all information, such as wage, tasks, required skills, and so on\n",
    "* Content model\n",
    "\n",
    "<center>\n",
    "<img src=\"http://www.onetcenter.org/image/model/model.png\" height = 50% width = 50%>\n",
    "</center>"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "##Data\n",
    "\n",
    "* the importance of 35 skill, 33 types of knowledge, and 51 work activities\n",
    "* For example, with respect of Knowledge of Mathematics, job incumbents were asked as,\n",
    "<blockquote>How important is this knowledge of Mathematics to the performance of your current job? </blockquote>\n",
    "* Ratings were made on a five-point scale (1 = not important, 2= somewhat unimportant, 3 = important, 4 = very important, 5 = extremely important)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "skip"
    }
   },
   "source": [
    "## Data source\n",
    "\n",
    "|                 | Number of ratings |  Rating source | Total participants | STEM participants |   Survey date   |\n",
    "|:---------------:|:-----------------:|:--------------:|:------------------:|:-----------------:|:---------------:|\n",
    "|      Skills     |         35        |  Job analysts  |        7,352       |       1,240       | 06/2010~07/2013 |\n",
    "|    Knolwedge    |         33        | Job incumbents |       26,685       |       4,370       | 03/2002~07/2013 |\n",
    "| Work activities |         51        | Job incumbents |       26,209       |       4,392       | 03/2002~07/2013 |"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 'High' and 'Low' skills, knowledge, and work activities\n",
    "\n",
    "* High > 2.95 points> Low\n",
    "\n",
    "|                 | High Number(Mean, SD) | Low Number(Mean, SD) | Wilcoxon rank sum test Z (p-value) |\n",
    "|:---------------:|:---------------------:|:--------------------:|:----------------------------------:|\n",
    "|      Skills     |    18 (3.35, 0.29)    |    17 (2.23, 0.50)   |        Z = -49.95 (p < .001)       |\n",
    "|    Knolwedge    |     7 (3.31, 0.32)    |    26 (2.12, 0.46)   |        Z = 35.30 (p < .001)        |\n",
    "| Work activities |    27 (3.60, 0.39)    |    14 (2.44, 0.25)   |        Z =- 48.9 (p < .001)        |\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "##GEVD to the Rescue\n",
    "\n",
    "* three parameter distribution that gives us really good control over shape\n",
    "    * shape: controls how far out the tail goes, all else equal\n",
    "    * loc: controls where the spike is, aee\n",
    "    * scale: controls fatness around the location, aee\n",
    "* `scipy.stats.genextreme` exposes easy draws from this distribution which we can then use to check out our expenditure distribution and what happens in different payment models"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {
    "collapsed": false,
    "slideshow": {
     "slide_type": "skip"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Populating the interactive namespace from numpy and matplotlib\n"
     ]
    }
   ],
   "source": [
    "%pylab inline\n",
    "from scipy.stats import genextreme, norm\n",
    "import numpy as np\n",
    "import matplotlib.pyplot as plt\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {
    "collapsed": true,
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "outputs": [],
   "source": [
    "def plt_extreme(x, c, loc, scale):\n",
    "    \"\"\"\n",
    "    Plots GEVD ppf at x (array-like) with shape parameter c,\n",
    "    location parameter loc, and scale parameter scale.\n",
    "    \"\"\"\n",
    "    \n",
    "    fig, ax = plt.subplots()\n",
    "    y = genextreme.pdf(x, c, loc=loc, scale=scale)\n",
    "    ax.plot(x, y, label=r'$\\xi$ = {0}, $\\sigma$ = {1}'.format(c, scale))\n",
    "    ax.axvline(loc, c='k', linestyle='--', label=r'$\\mu$ = {}'.format(loc))\n",
    "    ax.legend(bbox_to_anchor=(1.5,0.5))\n",
    "    ax.set_xscale('log')\n",
    "    ax.set_xlabel('Expenditure')\n",
    "    ax.set_ylabel('Frequency')\n",
    "    return ax"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {
    "collapsed": false,
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "outputs": [],
   "source": [
    "loc = 3200 #location parameter\n",
    "c = -0.75 #shape parameter !!scipy flips from wiki's sign choices\n",
    "scale = loc * -c #gives us support down to zero\n",
    "x = np.linspace(genextreme.ppf(0.00001, c, loc=loc, scale=scale),\n",
    "                genextreme.ppf(0.99999, c, loc=loc, scale=scale),\n",
    "                100000)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {
    "collapsed": false,
    "scrolled": true,
    "slideshow": {
     "slide_type": "subslide"
    }
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7fad0e1226d0>"
      ]
     },
     "execution_count": 4,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\nedLsvS+ILdQAAAAASUVORK5CYII=\n",
      "text/plain": [
       "<matplotlib.figure.Figure at 0x7fad0e122190>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "plt_extreme(x, c, loc, scale)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {
    "collapsed": false,
    "slideshow": {
     "slide_type": "subslide"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Full sample mean:  8850.994\n",
      "Confidence interval:  (8410.17, 9291.82)\n"
     ]
    }
   ],
   "source": [
    "#and some summary statistics\n",
    "dist = genextreme(c=c, loc=loc, scale=scale)\n",
    "vals = dist.rvs(size=5000)\n",
    "vals[vals > 125000] = 125000\n",
    "full_std_error = vals.std() / np.sqrt(len(vals))\n",
    "full_sample_interval = (round(vals.mean() - 2 * full_std_error, 2),\n",
    "                        round(vals.mean() + 2 * full_std_error, 2))\n",
    "print 'Full sample mean: ', vals.mean().round(3)\n",
    "print 'Confidence interval: ', full_sample_interval"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "##Estimate savings from the above?\n",
    "\n",
    "* If we wanted to know likelihood that the mean we observed was less than, say, \\$9,000, we'd be all set\n",
    "* What we want: distribution that can give us the likelihood that what we observed has a lower mean than *some other distribution*, itself the result of some random process.\n",
    "\n",
    "We'll get at that by resampling."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "##Quick Example\n",
    "\n",
    "**Demo group**: groups of Medicare providers with some expenditures benchmark. If their observed expenditures are lower than the benchmark they get paid. We want probably not to pay this demo group if they don't beat their benchmark. So we want to know the likelihood that the group \"really\" beat its benchmark given that we observe some level of expenditures and some benchmark.\n",
    "\n",
    "###Approach:\n",
    "\n",
    "Treat draws from the expenditure distribution as beneficiaries with that value for their expenditures in both benchmark and performance distributions. Treat the initially selected beneficiaries as a pseudo-population of the \"true\" population that the demo group should be responsible for. Resample from the pseudo-population to estimate mean expenditures and standard error of that mean for both the benchmark and performance distributions."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {
    "collapsed": false,
    "slideshow": {
     "slide_type": "subslide"
    }
   },
   "outputs": [],
   "source": [
    "def resampled_mean(a):\n",
    "    \"\"\"\n",
    "    Returns mean of resampled distribution from a 1-d array of values.\n",
    "    \"\"\"\n",
    "    \n",
    "    assert a.ndim == 1\n",
    "    \n",
    "    sample = np.random.choice(a, size=len(a), replace=True)\n",
    "    return [sample.mean(), sample.std()]\n",
    "\n",
    "def est_interv(orig_mean, sample_stds, n):\n",
    "    \"\"\"\n",
    "    Estimates interval around mean for sample_mean, sample_std, from\n",
    "    sample of size n.\n",
    "    \n",
    "    Takes mean of standard error of the mean estimated for each\n",
    "    bootstrapped calculation of the mean.\n",
    "    \"\"\"\n",
    "    \n",
    "    std_errors = (sample_stds/np.sqrt(n)).mean()\n",
    "    return (orig_mean - 2 * std_errors,\n",
    "            orig_mean + 2 * std_errors)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "##Visualizing Results\n",
    "\n",
    "Quick check to confirm that our estimate of the distribution of means doesn't tell us anything radically different from what we knew from above."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {
    "collapsed": true,
    "slideshow": {
     "slide_type": "skip"
    }
   },
   "outputs": [],
   "source": [
    "resampling = np.array([resampled_mean(vals) for i in range(10000)])\n",
    "means, stds = resampling[:,0], resampling[:,1]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {
    "collapsed": false,
    "slideshow": {
     "slide_type": "skip"
    }
   },
   "outputs": [],
   "source": [
    "full_fences = full_sample_interval\n",
    "resampled_fences = est_interv(vals.mean(), stds, len(vals))\n",
    "\n",
    "full_sample_x = np.linspace(\n",
    "    norm.ppf(0.001, loc=vals.mean(), scale=full_std_error),\n",
    "    norm.ppf(0.999, loc=vals.mean(), scale=full_std_error),\n",
    "    1000\n",
    ")\n",
    "full_sample_y = norm.pdf(full_sample_x, vals.mean(), full_std_error)\n",
    "\n",
    "resampled_params = norm.fit(means)\n",
    "resampled_x = np.linspace(\n",
    "    norm.ppf(0.001, *resampled_params),\n",
    "    norm.ppf(0.999, *resampled_params),\n",
    "    1000\n",
    ")\n",
    "resampled_y = norm.pdf(resampled_x, *resampled_params)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {
    "collapsed": false,
    "scrolled": true,
    "slideshow": {
     "slide_type": "subslide"
    }
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.legend.Legend at 0x7fad0dbf8f50>"
      ]
     },
     "execution_count": 9,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<matplotlib.figure.Figure at 0x7fad0deb5e50>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "fig, ax = plt.subplots()\n",
    "ax.hist(means, bins=100, normed=True)\n",
    "ax.axvline(vals.mean(), label='full sample mean')\n",
    "ax.axvline(means.mean(), linestyle='dashed', label='mean of means')\n",
    "ax.vlines(resampled_fences, *ax.get_ylim(), linestyle='dashed', colors='k', label='resampled std')\n",
    "ax.vlines(full_fences, *ax.get_ylim(), linestyle='dashed', colors='r', label='full samp std')\n",
    "ax.plot(resampled_x, resampled_y, label = 'resampled dist')\n",
    "ax.plot(full_sample_x, full_sample_y, label='full sample dist')\n",
    "plt.legend(bbox_to_anchor=(1.5, .5))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "###Estimating Savings\n",
    "\n",
    "Treat the above as our estimation of the benchmark. We then want to know the likelihood that another value we observe from a different distribution is actually savings, or \"higher value\" care.\n",
    "\n",
    "This is a ratio of two distributions, so we leave the realm of normal distributions and have to think about fat tails.\n",
    "\n",
    "Resampling lets us choose \"we tried it a whole bunch of times, and we're x% sure the value of care increased\" over \"Cauchy distribution said so,\" which is useful for interpretability."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {
    "collapsed": false,
    "slideshow": {
     "slide_type": "subslide"
    }
   },
   "outputs": [],
   "source": [
    "#can play with parameters of uniform to show different\n",
    "#mean savings rates\n",
    "#vals2 is our second expenditure distribution,\n",
    "#calculated as vals + uniform random noise\n",
    "vals2 = vals * np.random.uniform(\n",
    "    low=0.975, high=1.01,\n",
    "    size=len(vals)\n",
    ")\n",
    "resampling2 = np.array([resampled_mean(vals2) for i in range(10000)])\n",
    "means2, stds2 = resampling2[:,0], resampling2[:,1]\n",
    "\n",
    "save_rates = 1 - np.random.choice(means2, size=250000) /\\\n",
    "    np.random.choice(means, size=250000)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {
    "collapsed": false,
    "slideshow": {
     "slide_type": "subslide"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Mean increase in value (savings):  0.006\n",
      "Proportion of observations of increased value:  0.575\n",
      "Proportion increased value if we treated first mean as fixed: \n",
      "     0.612\n",
      "Overconfidence:  0.064\n"
     ]
    }
   ],
   "source": [
    "print 'Mean increase in value (savings): ', save_rates.mean().round(3)\n",
    "print 'Proportion of observations of increased value: ',\\\n",
    "    (save_rates > 0).mean().round(3)\n",
    "print \"\"\"Proportion increased value if we treated first mean as fixed: \n",
    "    \"\"\", (means2 < vals.mean()).mean().round(3)\n",
    "print 'Overconfidence: ',\\\n",
    "    round((means2 < vals.mean()).mean() / (save_rates > 0).mean() - 1, 3)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {
    "collapsed": false,
    "slideshow": {
     "slide_type": "subslide"
    }
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.legend.Legend at 0x7fad0deb5310>"
      ]
     },
     "execution_count": 12,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<matplotlib.figure.Figure at 0x7fad0deb57d0>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "fig, ax = plt.subplots()\n",
    "est_norm = norm.fit(save_rates)\n",
    "alt = norm.rvs(*est_norm, size=150000)\n",
    "ax.hist([save_rates, alt], histtype='step',\n",
    "        bins=100, normed=True,\n",
    "        label=['bootstrapped', 'not bootstrapped'])\n",
    "ax.set_title('Distribution of Simulated Savings Rate')\n",
    "ax.legend(bbox_to_anchor = (1.5, 0.5))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "skip"
    }
   },
   "source": [
    "##Further Applications\n",
    "\n",
    "Note that this is just a highest-level look at simulation. If you happen to know something about [a link between diagnoses and expenditures](https://www.cms.gov/Research-Statistics-Data-and-Systems/Research/HealthCareFinancingReview/downloads/04summerpg119.pdf) and to know something about [the geographic distribution of diagnoses](http://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Geographic-Variation/GV_PUF.html), you could compose your extreme value distribution of less exotic distributions and do more specific simulations:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {
    "collapsed": true,
    "slideshow": {
     "slide_type": "skip"
    }
   },
   "outputs": [],
   "source": [
    "x1 = np.linspace(\n",
    "    norm.ppf(0.00001, loc=1100, scale=900),\n",
    "    norm.ppf(0.99999, loc=1100, scale=900),\n",
    "    10000\n",
    ")\n",
    "x2 = np.linspace(\n",
    "    norm.ppf(0.00001, loc=25000, scale=6000),\n",
    "    norm.ppf(0.99999, loc=25000, scale=6000),\n",
    "    10000\n",
    ")\n",
    "x3 = np.linspace(\n",
    "    norm.ppf(0.00001, loc=75000, scale=15000),\n",
    "    norm.ppf(0.99999, loc=75000, scale=15000),\n",
    "    10000\n",
    ")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {
    "collapsed": false,
    "scrolled": true,
    "slideshow": {
     "slide_type": "skip"
    }
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.legend.Legend at 0x7fad0d9d0610>"
      ]
     },
     "execution_count": 14,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\nd1qXp9GIDbEAAAAASUVORK5CYII=\n",
      "text/plain": [
       "<matplotlib.figure.Figure at 0x7fad0db2e990>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "#each curve is an expenditure distribution for beneficiaries with\n",
    "#a particular diagnosis\n",
    "fig, ax = plt.subplots()\n",
    "ax.plot(x1, norm.pdf(x1, 1200, 900), '-', label='diagnosis1')\n",
    "ax.plot(x2, norm.pdf(x2, 25000, 6000), '-', label='diagnosis2')\n",
    "ax.plot(x3, norm.pdf(x3, 75000, 15000), '-', label='diagnosis3')\n",
    "ax.set_xlim((0,150000))\n",
    "ax.legend()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "slide"
    }
   },
   "source": [
    "#Thank You\n",
    "###james.santucci@gmail.com"
   ]
  }
 ],
 "metadata": {
  "celltoolbar": "Slideshow",
  "kernelspec": {
   "display_name": "Python 2",
   "language": "python",
   "name": "python2"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 2
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython2",
   "version": "2.7.6"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 0
}
