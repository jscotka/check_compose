# check_compose

This contains [avocado testing framework](http://avocado-framework.github.io/)
based tests to conduct various module checks.

* check_compose.py - check validity of module composition (_work in progress_)

## Setup

Install prerequisite RPMs if necessary:

* python2-aexpect - dependency for python-avocado
* python2-avocado - avocado testing framework
* python2-modulemd - Module metadata manipulation library
* python2-dnf - Python 2 interface to DNF

## Running check_compose.py

Call avocado to run check_compose.py, providing the path to the composed
repository and the modulemd file using
[avocado's parameter passing mechanism](http://avocado-framework.readthedocs.io/en/latest/WritingTests.html#accessing-test-parameters):

    avocado run ./check_compose.py --mux-inject 'run:repo:/path/to/repository' 'run:modulemd:/path/to/modulemd.yaml'

For convenience during development of the test script, a wrapper script is
provided that simplifies passing the required parameters:

    ./run-checkcomp.sh [--debug] /path/to/repository /path/to/modulemd.yaml

### Taskotron

This check should eventually be called by [Taskotron](https://fedoraproject.org/wiki/Taskotron). A *non-working* start of a task definition has been included:

    runtask -i "modules/testmodule#aaca87a82c35c1f0eb85556191f09f8a842abd9f" -t dist_git_commit -a noarch ./runtask.yml


