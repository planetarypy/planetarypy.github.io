.. title: Packages
.. slug: index
.. date: 2021-02-16 11:30:32 UTC-08:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. data: data/registry.json

If you have an existing package that you think others would benefit from,
please consider applying for it to be a PlanetaryPy Affiliated Package
by reading about our `Review Process <link://slug/review-process>`__
and `Review Guidelines <link://slug/review-guidelines>`__.

These are the PlanetaryPy Affiliated Packages:

{{% template %}}

<%def name="getshield(category, status)">
<%
    tcase = status.title()
    try:
        color = post.data("criteria")[category][status]
    except KeyError as err:
        if status.casefold() == "to be filled out by the reviewer":
            color = "black"
        else:
            raise ValueError(
                f"The value '{status}' isn't allowable for category '{category}' "
                f"in registry.json."
            ) from err
%>
<img src="https://img.shields.io/badge/${tcase | h}-${color}.svg" alt=${tcase}">
</%def>

<%def name="getver(ver)">
<%
    import math
    verinfo = tuple(map(int, ver.split(".")))
    pyver = tuple(map(int, post.data("criteria")["pythonver"].split(".")))
    pymaxver = tuple(map(int, post.data("criteria")["pythonmaxver"].split(".")))
    try:
        if verinfo == pyver:
            status = f"{ver}-brightgreen"
        elif pyver < verinfo <= pymaxver:
            status = f"{ver}-orange"
        else:
            status = f"{ver}-red"
    except ValueError as err:
        if ver.casefold() == "to be filled out by the reviewer":
            status = f"{ver}-black"
        else:
            raise ValueError(
                f"The value '{ver}' isn't allowable for category 'pythonver' "
                f"in registry.json."
            ) from err
%>
<img src="https://img.shields.io/badge/${status}.svg" alt="${ver}">
</%def>

<%def name="packages_table()">
<table class="table">
<%
    sorted_packages = sorted(
        post.data("packages"), key = lambda i: i["name"].casefold()
    )
%>
% for pack in sorted_packages:
<tr>
<td>${pack["name"]}</td>
<td><p><a href="${pack["home_url"]}" class="btn btn-primary">Website</a>
       <a href="${pack["repo_url"]}" class="btn btn-secondary">Repository</a>
       <a href="https://pypi.org/project/${pack["pypi_name"]}/">
         <img src="/images/pypi-logo-small.svg" height="30"
         alt="PyPI" />
    </p>
    <p>${pack["description"]}</p>
    <p>Maintainer(s): ${pack["maintainer"]}</p>
    <table class="table table-sm table-borderless" style="font-size: 14px">
      <thead>
        <tr>
          <th class="align-bottom">Functionality</th>
          <th class="align-bottom">Integration</th>
          <th class="align-bottom">Documentation</th>
          <th class="align-bottom">Tests</th>
          <th class="align-bottom">Development</th>
          <th class="align-bottom">Python Version</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          % for cat in ("functionality", "ecointegration", "documentation", "testing", "devstatus"):
          <td class="align-top">
            ${getshield(cat, pack["review"][cat].lower())}</td>
          % endfor
          <td class="align-top">
            ${getver(pack["review"]["pythonver"])}</td>
        </tr>
      </tbody>
    </table>
</tr>
% endfor
</table>
</%def>

${packages_table()}
{{% /template %}}
