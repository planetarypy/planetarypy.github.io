.. title: Contributing
.. slug: contributing
.. date: 2021-02-27 12:07:44 UTC-08:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text


Contributions and corrections to the PlanetaryPy webpage are welcome, and they are 
greatly appreciated! Every little bit helps, and credit will always be given.

The PlanetaryPy webpage uses the `Nikola Static Site Generator
<https://getnikola.com/>`_ which means that the "source" of the
webpages are found not in the ``master`` branch of the
`planetarypy.github.io
<https://github.com/planetarypy/planetarypy.github.io>`_ repo, but
in the `src branch
<https://github.com/planetarypy/planetarypy.github.io/tree/src>`_.

So to make contributions or corrections, you must first fork the repo, and your
changes must be PRs to the ``src`` branch, not the ``master`` branch.


You can contribute in many ways:

Types of Contributions
----------------------

Report Problems or Ask for Features via Issues
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We want to hear from you!  You can report issues or typos, ask for new features,
or just raise issues or concerns via logging an `Issue via our
GitHub repo <https://github.com/planetarypy/planetarypy.github.io/issues>`_.


Fix Bugs or Implement Features
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Look through the GitHub Issues for bugs to fix or feautures to implement.
If anything looks tractable to you, work on it.  Most (if not all) PRs should
be based on an Issue, so if you're thinking about doing some coding on a topic
that isn't covered in an Issue, please author one so you can get some feedback
while you work on your PR.

You can either just use the GitHub web interface for small PRs to the ``src`` branch,
or you can do more substantial work by working locally (detailed below).



Submit Feedback
~~~~~~~~~~~~~~~

The best way to send feedback is to file an `Issue
<https://github.com/planetarypy/planetarypy.github.io/issues>`_.


Get Started!
------------

Ready to contribute? Here's how to set up ``planetarypy.github.io`` for local development.

1. Fork the ``planetarypy.github.io`` repo on GitHub.
2. Clone your fork locally::

    $ git clone git@github.com:your_name_here/planetarypy.github.io.git

3. Make sure to also get the ``src`` branch::

    $ git branch -f src origin/src
    $ git checkout src

3. Install Nikola, doing so via conda is the easiest::

    $ conda create --name nikola
    $ conda activate nikola
    $ conda install nikola


4. Make your changes and commits on your ``src`` branch, test locally with 
   ``nikola build`` and ``nikola serve``

5. When you're done making changes, check that your changes actually do build
   with ``nikola build`` and ``nikola check -rfl``.  You may get errors related to 
   links generated from the registry in packages/index.html.  Package authors
   sometimes provide short, readable URLs that get redirected to different URLs,
   and these errors can be ignored.


6. Commit your changes and push to your forked branch on GitHub::

    $ git add .
    $ git commit -m "Your detailed description of your changes."
    $ git push

7. Submit a `pull request <https://github.com/planetarypy/planetarypy.github.io/pulls>`_


Pull Request Guidelines
-----------------------

Before you submit a pull request, check that it passes
``nikola build`` and ``nikola check``.


What to expect
--------------

We want to keep the webpage moving forward, and you should expect
activity on your PR within a week or so (we're all volunteers).


Rules for Merging Pull Requests
-------------------------------

Any change to resources in this repository must be through pull
requests (PRs). This applies to all changes to documentation, code,
binary files, etc. Even long term committers must use pull requests.

In general, the submitter of a PR is responsible for making changes
to the PR. Any changes to the PR can be suggested by others in the
PR thread (or via PRs to the PR), but changes to the primary PR
should be made by the PR author (unless they indicate otherwise in
their comments). In order to merge a PR, it must satisfy these conditions:

1. Have been open for 24 hours.
2. Have one approval.
3. If the PR has been open for 48 hours without approval or comment, then it
   may be merged without any approvals.

**Unless** that file is the ``data/registry.json`` file.  That is
the cannonical list of PlanetaryPy packages, and PRs to that file—and
that file only—have these more restrictive requirements:

1. Have been open for 24 hours.
2. Have two approvals.


Pull requests should sit for at least 24 hours to ensure that
contributors in other timezones have time to review. Consideration
should also be given to weekends and other holiday periods to ensure
active committers all have reasonable time to become involved in
the discussion and review process if they wish.

In order to encourage involvement and review, we encourage at least
one explicit approval from committers that are not the PR author.

However, in order to keep development moving along with our low number of
active contributors, if a PR has been open for two days without comment, then
it could be committed without an approval.

The default for each contribution is that it is accepted once no
committer has an objection, and the above requirements are
satisfied. 

In the case of an objection being raised in a pull request by another
committer, all involved committers should seek to arrive at a
consensus by way of addressing concerns being expressed by discussion,
compromise on the proposed change, or withdrawal of the proposed
change.

If a contribution is controversial and committers cannot agree about
how to get it merged or if it should merge, then the developers
will escalate the matter to the PlanetaryPy TC for guidance.  It
is expected that only a small minority of issues be brought to the
PlanetaryPy TC for resolution and that discussion and compromise
among committers be the default resolution mechanism.

Exceptions to the above are minor typo fixes or cosmetic changes
that don't alter the meaning of a document. Those edits can be made
via a PR and the requirement for being open 24 h is waived in this
case.


planetarypy.github.io People
----------------------------

- A **Contributor** is any individual creating or commenting
  on an issue or pull request.

- A **Committer** is a subset of contributors who have been
  given write access to the repository.

Those individuals that are authorized by the PlanetaryPy TC
can become Committers.  Individuals who wish to be considered for
commit-access may create an Issue or contact an existing Committer
directly.

Committers are expected to follow this policy and continue to send
pull requests, go through proper review, etc.
