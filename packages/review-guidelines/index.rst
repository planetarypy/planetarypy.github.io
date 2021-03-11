.. title: Review Guidelines
.. slug: review-guidelines
.. date: 2021-02-16 11:30:32 UTC-08:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
.. data: data/registry.json

This document describes the set of review criteria for packages applying to
become PlanetaryPy-affiliated, and is intended for reviewers.

If you are reading this because you have accepted to review an affiliated
package submission, thank you for taking the time to do this!

Note that unlike for a paper where the reviews from the referee are
passed on to the authors, one of the coordinators will also review
the package and will create a combined report from the submitted
reviews, so the report you write may not be seen by the authors
as-is. Reports should be emailed privately back to the coordinator
that contacted you.

Reviewing a package involves assessing how well the package does in several
areas, which we outline below. As a reviewer it is is expected that you review
on these criteria, and it is sufficient to *solely* use these criteria.
However, feel free to bring up any other aspect which you think is important.
For the categories below, you can let us know which of the 'traffic light'
levels you think the package should be rated as, in addition to providing
comments in cases where things aren't perfect.

In general we use the following color-coding, which also determines if a package
is accepted after its first review:

.. raw:: html

   <table class="table">
   <tr>
   <td class="w-25 align-center">
     <img src="https://img.shields.io/badge/Red-red.svg" alt="Red"></td>
   <td>Affiliated packages can only be accepted into the list if there
   are no red scores. Existing affiliated packages that have one
   category that drops down to red don’t get automatically kicked out,
   but they should resolve this, otherwise the package will be
   de-listed.</td>
   </tr>
   <tr>
   <td class="w-25 align-center">
     <img src="https://img.shields.io/badge/Orange-orange.svg" alt="Orange"></td>
   <td>Having orange scores is fine, but is both a warning to the user
   that not all is perfect about the package, and an incentive for
   developers to improve and reach green.</td>
   </tr>
   <tr>
   <td class="w-25 align-center">
     <img src="https://img.shields.io/badge/Green-brightgreen.svg" alt="Green"></td>
   <td>This is the standard we want all packages to aim for. Packages
   that have all-green scores may be featured in a separate table for
   well-maintained and supported packages.</td>
   </tr>
   </table>

The document also includes ``monospaced keywords`` for the categories
and levels.  These are the keywords and values to be used in the
`registry.json 
<https://github.com/planetarypy/planetarypy.github.io/blob/src/data/registry.json>`_
file that is the canonical source for affiliated package information.

The categories in which we assess the package are the following:

* Functionality (``functionality``)
* Integration with the PlanetaryPy ecosystem  (``ecointegration``)
* Documentation (``documentation``)
* Testing (``testing``)
* Development status (``devstatus``)
* Python version compatibility (``pythonver``)

{{% template %}}
<%def name="getshield(category, status)">
<%
    tcase = status.title()
    color = post.data("criteria")[category][status]

%>
<img src="https://img.shields.io/badge/${tcase | h}-${color}.svg" alt=${tcase}">
</%def>


<h2 id="functionality">Functionality (<code>functionality</code>)</h2>

<p>
We first need to make sure that the scope of the package is relevant
for the affiliated package system. The scopes are:
</p>

<table class="table">
  <tr>
   <td class="w-25 align-center">${getshield("functionality", "out of scope")}</tc>
   <td>Not useful for planetary work, or specific to one project/collaboration.</td>
  </tr>
  <tr>
   <td class="w-25 align-center">${getshield("functionality", "specialized package")}</td>
   <td>Useful to planetary scientists and engineers working in a very
   specific domain/field, or with a specific instrument and
   usable not just by a single collaboration but anyone within
   that domain.</td>
   </tr>
   <tr>
   <td class="w-25 align-center">${getshield("functionality", "general package")}</td>
   <td>Package that is useful for planetary researchers across more
   than just a single field or instrument.</td>
  </tr>
</table>

<p>
Note that general is not necessary better than specific, it’s just
a way to make sure we can present these separately.
</p>

<h2 id="ecointegration">Integration with the PlanetaryPy ecosystem
(<code>ecointegration</code>)</h2>

<p>
Next up, we need to check how well the package fits in to the
existing PlanetaryPy ecosystem - does it make use of existing
functionality, or does it duplicate it?
</p>

<p>
This factor is about what integration is possible given the current
state of the PlanetaryPy project.  If some functionality exists in
PlanetaryPy core or affiliated packages, that is the yardstick for
comparison here.  During the early stages of the PlanetaryPy project,
there is not much existing functionality, and most packages will
be Good against this criteria (because there simply isn't much
existant functionality to integate with).
</p>

<table class="table">
<tr>
<td class="w-25 align-center">${getshield("ecointegration", "none")}</td>
<td>Does not use PlanetaryPy core or affiliated packages anywhere
where it should be possible, and/or uses other libraries instead.</td>
</tr>
<tr>
<td class="w-25 align-center">${getshield("ecointegration", "partial")}</td>
<td>Makes an effort to use PlanetaryPy core or affiliated packages in
places, but still has other places where this could be done but
isn’t.</td>
</tr>
<tr>
<td class="w-25 align-center">${getshield("ecointegration", "good")}</td>
<td>Uses PlanetaryPy core or affiliated packages wherever possible.  Usage is not required,
but if there is reasonable existing functionality, it should be used.</td>
</tr>
</table>

<h2 id="documentation">Documentation (<code>documentation</code>)</h2>

<p>
No code is complete without documentation! Take a look at the
documentation (if it exists) and see how the package fares:
</p>

<table class="table">
<tr>
<td class="w-25 align-center">${getshield("documentation", "insufficient")}</td>
<td>No documentation or some documentation, but very bare bones/minimal
and incomplete or incorrect in a number of places.  Governance documents that
significantly diverge from those of the PlanetaryPy Project.</td>
</tr>
<td class="w-25 align-center">${getshield("documentation", "partial")}</td>
<td>Reasonable documentation (which could be a very well written
README), installation instructions and at least one usage example,
but some parts missing.</td>
</tr>
<tr>
<td class="w-25 align-center">${getshield("documentation", "good")}</td>
<td>Extensive documentation, including at least: motivation/scope
of package, installation instructions, usage examples, and API
documentation. In terms of infrastructure, the documentation should
be automatically built on readthedocs.org or similar. If appropriate, one or
more tutorials should be included.</td>
</tr>
</table>

<p>
This is also a good point to examine what 'governance documents', if any, 
exist for the submitted package.  If they do exist, they should be compared 
with the PlaneatryPy Project governance documents, and any major divergences
should be noted.
</p>

<h2 id="testing">Testing (<code>testing</code>)</h2>

<p>
In our terminology, “tests” refer to those that can be run in an automated way,
and we do not consider examples that need to be run and/or checked manually to
be acceptable as the primary way of satisfying “tests”.
</p>

<table class="table">
<tr>
<td class="w-25 align-center">${getshield("testing", "insufficient")}</td>
<td>No tests or tests that are not trivial to run or don’t use a
standard testing framework, or low test coverage (no exact threshold
for coverage since this is not always easy to measure, but in this
category most of the code is not covered).</td>
</tr>
<tr>
<td class="w-25 align-center">${getshield("testing", "partial")}</td>
<td>A reasonable fraction of the code is covered by tests, but still
some parts of the code that are missing tests. To be in this category,
packages should use a standard framework (unittest, pytest, nose, etc.) and
be runnable with a single command.</td>
</tr>
<tr>
<td class="w-25 align-center">${getshield("testing", "good")}</td>
<td>Test coverage is very high (for example 90% or more), tests use
a standard framework (unittest, pytest, nose, etc.) and are easy to run and
continuous integration is used to ensure package stability over
time.</td>
</tr>
</table>

<p>
Test coverage can be tricky to measure, so this will be carefully assessed for
each package. The main idea is to determine whether it is low, medium or high
compared to what one might realistically achieve.
</p>

<h2 id="devstatus">Development status (<code>devstatus</code>)</h2>

<table class="table">
<tr>
<td class="w-25 align-center">${getshield("devstatus", "nonfunctional")}</td>
<td>Package is not or no longer fully functional, even if stable releases exist.</td>
</tr>
<tr>
<td class="w-25 align-center">${getshield("devstatus", "heavy development")}</td>
<td>Stable releases exist, but still under heavy development (so
API changes can be frequent).</td>
</tr>
<tr>
<td class="w-25 align-center">${getshield("devstatus", "functional but unmaintained")}</td>
<td>Stable releases exist and there are no active developers/maintainers
but package remains mostly functional.</td>
</tr>
<tr>
<td class="w-25 align-center">${getshield("devstatus", "functional but low activity")}</td>
<td>Stable releases exist but the maintainers only make occasional
comments/commits (and package is not in excellent condition, because
otherwise it’s fine to have a completely stable package with little
activity if it can be considered 'finished')</td>
</tr><tr>
<td class="w-25 align-center">${getshield("devstatus", "good")}</td>
<td>Package has stable releases, and package is actively developed
(as needed). A metric for active development is whether most
recently-opened issues have some kind of reply from maintainers.</td>
</tr>
</table>

<h2 id="pythonver">Python version compatibility (<code>pythonver</code>)</h2>

<p>
The PlanetaryPy Project requires that packages be compatible with
Python version ${post.data("criteria")["pythonver"]}.  Being
compatible with later versions of Python is great, too, but must
be compatible with at least ${post.data("criteria")["pythonver"]}.
</p>

<table class="table">
<tr>
<td class="w-25 align-center"><img src="https://img.shields.io/badge/Incompatible-red.svg" alt="Incompatible"></td>
<td>Not compatible with Python ${post.data("criteria")["pythonver"]}.</td>
</tr>
<tr>
<tr>
<td class="w-25 align-center"><img src="https://img.shields.io/badge/${post.data("criteria")["pythonver"]}-brightgreen.svg" alt="${post.data("criteria")["pythonver"]}"></td>
<td>Compatible with Python ${post.data("criteria")["pythonver"]}.</td>
</tr>
</table>
{{% /template %}}
