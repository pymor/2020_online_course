# 2020_online_course
Materials for the 2020 pyMOR online course

## Installing pyMOR

Since we are using a feature branch for the exercise and tutorial materials you will need
to install pyMOR following the following instructions should you want to work on the exercises on your own machine.

### Conda (OSX, Windows, Linux)


### Manylinux Wheels (Linux)

To install pyMOR the appropiate wheel for you Python version (supported are 3.6,3.7 and 3.8) follow these steps in a
terminal bash session:
```
export TARGET_DIRECTORY=${HOME}/pymor_course
mkdir ${TARGET_DIRECTORY}
git clone https://github.com/pymor/2020_online_course ${TARGET_DIRECTORY}/material
python3 -m virtualenv ${TARGET_DIRECTORY}/virtualenv
. ${TARGET_DIRECTORY}/virtualenv/bin/activate
export WHL_VERSION=$(python -c 'import sys; m="m"; vi=sys.version_info; print(f"cp{vi[0]}{vi[1]}-cp{vi[0]}{vi[1]}{m if vi[1] < 8 else str()}-manylinux1_x86_64")')
pip install ${TARGET_DIRECTORY}/material/packages/wheels/linux-64/pymor-2020_online_course-${WHL_VERSION}.whl[full]

# now you can start a Jupter Notebook server to work on the exercises:
jupyter notebook --notebook-dir=${TARGET_DIRECTORY}/material/exercises
```

### Docker

If you have a working docker setup you can use also to work on the exercises.

```
# first build the image
docker build --build-arg NB_USER=${USER} --build-arg NB_UID=$(id -u) -t pymor_course -f .binder/Dockerfile  .
# then start the Jupyter server
docker run pymor_course:latest bash -c "jupyter notebook --ip 0.0.0.0 --no-browser --notebook-dir=/pymor --NotebookApp.disable_check_xsrf=True"
# now open the displayed URL (127.0.0.1) in your browser
```

## pyMOR documentation

You can find the documentation [here](https://docs.pymor.org/2020-online-course/index.html)

## Literature

### Python programming

Note that due to time constraints,
we are unable to give an introduction to Python/NumPy/SciPy,
but there are plenty of free online resources to learn the basics:

- for inexperienced programmers:
    - https://greenteapress.com/wp/think-python-2e/
    - https://automatetheboringstuff.com/
    - https://link.springer.com/book/10.1007/978-3-319-32428-9
    - https://python.swaroopch.com/
    - https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners
- for more experienced programmers:
    - https://docs.python.org/3/tutorial/index.html
    - https://diveintopython3.problemsolving.io/
    - https://docs.python-guide.org/
    - https://docs.scipy.org/doc/numpy/user/quickstart.html
    - https://docs.scipy.org/doc/numpy/user/numpy-for-matlab-users.html
    - http://hyperpolyglot.org/numerical-analysis
    - https://matplotlib.org/tutorials/index.html


### Model Order Reduction

There are several monographs available on model order reduction. In particular:

- [P. Benner, M. Ohlberger, A. Cohen, K. Willcox, "Model Reduction and Approximation: Theory and Algorithms", 2017](https://doi.org/10.1137/1.9781611974829)
- [A. Quarteroni, A. Manzoni, F. Negri, "Reduced Basis Methods for Partial Differential Equations", 2016](https://doi.org/10.1007/978-3-319-15431-2)
- [J. S. Hesthaven, G. Rozza, B. Stamm, "Certified Reduced Basis Methods for Parametrized Partial Differential Equations", 2016](https://doi.org/10.1007/978-3-319-22470-1)
- [A. C. Antoulas, "Approximation of Large-Scale Dynamical Systems", 2005](https://doi.org/10.1137/1.9780898718713)

Freely available lecture notes are:

- [Uni Stuttgart RB lecture notes](https://pnp.mathematik.uni-stuttgart.de/ians/haasdonk/publications/RBtutorial_preprint_update_with_header.pdf)
- [Uni Hamburg MOR lecture notes](https://www.math.uni-hamburg.de/home/voigt/Modellreduktion_SoSe19/Notes_ModelReduction.pdf)

Also see:

- [MOR Wiki](http://modelreduction.org)
