# Libtool

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html><!-- This manual is for GNU Libtool (version 2.4.7-dirty, 17 March 2022).

Copyright (C) 1996-2019, 2021-2022 Free Software Foundation,
Inc.

Permission is granted to copy, distribute and/or modify this document
under the terms of the GNU Free Documentation License, Version 1.3
or any later version published by the Free Software Foundation;
with no Invariant Sections, with no Front-Cover Texts,
and with no Back-Cover Texts.  A copy of the license is included in
the section entitled "GNU Free Documentation License". --><!-- Created by GNU Texinfo 6.7, http://www.gnu.org/software/texinfo/ --><head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">

<meta name="description" content="Libtool">
<meta name="keywords" content="Libtool">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">
<meta name="Generator" content="makeinfo">
<link href="#Top" rel="start" title="Top">
<link href="#Combined-Index" rel="index" title="Combined Index">
<link href="#SEC_Contents" rel="contents" title="Table of Contents">
<link href="https://www.gnu.org/savannah-checkouts/gnu/libtool/manual/dir.html#Top" rel="up" title="(dir)">
<link rel="stylesheet" type="text/css" href="README_files/manual.css">


</head>

<body lang="en">
<h1 class="settitle" align="center">Libtool</h1>







<span id="SEC_Contents"></span>
<h2 class="contents-heading">Table of Contents</h2>

<div class="contents">

<ul class="no-bullet">
  <li><a id="toc-Introduction-1" href="#Introduction">1 Introduction</a>
  <ul class="no-bullet">
    <li><a id="toc-Motivation-for-writing-libtool" href="#Motivation">1.1 Motivation for writing libtool</a></li>
    <li><a id="toc-Implementation-issues" href="#Issues">1.2 Implementation issues</a></li>
    <li><a id="toc-Other-implementations-1" href="#Other-implementations">1.3 Other implementations</a></li>
    <li><a id="toc-A-postmortem-analysis-of-other-implementations" href="#Postmortem">1.4 A postmortem analysis of other implementations</a></li>
  </ul></li>
  <li><a id="toc-The-libtool-paradigm" href="#Libtool-paradigm">2 The libtool paradigm</a></li>
  <li><a id="toc-Using-libtool-1" href="#Using-libtool">3 Using libtool</a>
  <ul class="no-bullet">
    <li><a id="toc-Creating-object-files-1" href="#Creating-object-files">3.1 Creating object files</a></li>
    <li><a id="toc-Linking-libraries-1" href="#Linking-libraries">3.2 Linking libraries</a></li>
    <li><a id="toc-Linking-executables-1" href="#Linking-executables">3.3 Linking executables</a>
    <ul class="no-bullet">
      <li><a id="toc-Wrapper-executables-for-uninstalled-programs" href="#Wrapper-executables">3.3.1 Wrapper executables for uninstalled programs</a></li>
    </ul></li>
    <li><a id="toc-Debugging-executables-1" href="#Debugging-executables">3.4 Debugging executables</a></li>
    <li><a id="toc-Installing-libraries-1" href="#Installing-libraries">3.5 Installing libraries</a></li>
    <li><a id="toc-Installing-executables-1" href="#Installing-executables">3.6 Installing executables</a></li>
    <li><a id="toc-Linking-static-libraries" href="#Static-libraries">3.7 Linking static libraries</a></li>
  </ul></li>
  <li><a id="toc-Invoking-libtool-1" href="#Invoking-libtool">4 Invoking <code>libtool</code></a>
  <ul class="no-bullet">
    <li><a id="toc-Compile-mode-1" href="#Compile-mode">4.1 Compile mode</a></li>
    <li><a id="toc-Link-mode-1" href="#Link-mode">4.2 Link mode</a></li>
    <li><a id="toc-Execute-mode-1" href="#Execute-mode">4.3 Execute mode</a></li>
    <li><a id="toc-Install-mode-1" href="#Install-mode">4.4 Install mode</a></li>
    <li><a id="toc-Finish-mode-1" href="#Finish-mode">4.5 Finish mode</a></li>
    <li><a id="toc-Uninstall-mode-1" href="#Uninstall-mode">4.6 Uninstall mode</a></li>
    <li><a id="toc-Clean-mode-1" href="#Clean-mode">4.7 Clean mode</a></li>
  </ul></li>
  <li><a id="toc-Integrating-libtool-with-your-package" href="#Integrating-libtool">5 Integrating libtool with your package</a>
  <ul class="no-bullet">
    <li><a id="toc-Autoconf-macros-exported-by-libtool" href="#Autoconf-macros">5.1 Autoconf macros exported by libtool</a></li>
    <li><a id="toc-Writing-Makefile-rules-for-libtool" href="#Makefile-rules">5.2 Writing <samp>Makefile</samp> rules for libtool</a></li>
    <li><a id="toc-Using-Automake-with-libtool" href="#Using-Automake">5.3 Using Automake with libtool</a></li>
    <li><a id="toc-Configuring-libtool" href="#Configuring">5.4 Configuring libtool</a>
    <ul class="no-bullet">
      <li><a id="toc-The-LT_005fINIT-macro" href="#LT_005fINIT">5.4.1 The <code>LT_INIT</code> macro</a></li>
      <li><a id="toc-Platform_002dspecific-configuration-notes" href="#Configure-notes">5.4.2 Platform-specific configuration notes</a></li>
    </ul></li>
    <li><a id="toc-Including-libtool-in-your-package" href="#Distributing">5.5 Including libtool in your package</a>
    <ul class="no-bullet">
      <li><a id="toc-Invoking-libtoolize-1" href="#Invoking-libtoolize">5.5.1 Invoking <code>libtoolize</code></a></li>
      <li><a id="toc-Autoconf-and-LTLIBOBJS-1" href="#Autoconf-and-LTLIBOBJS">5.5.2 Autoconf and <code>LTLIBOBJS</code></a></li>
    </ul></li>
    <li><a id="toc-Static_002donly-libraries-1" href="#Static_002donly-libraries">5.6 Static-only libraries</a></li>
  </ul></li>
  <li><a id="toc-Using-libtool-with-other-languages" href="#Other-languages">6 Using libtool with other languages</a>
  <ul class="no-bullet">
    <li><a id="toc-Writing-libraries-for-C_002b_002b" href="#C_002b_002b-libraries">6.1 Writing libraries for C++</a></li>
    <li><a id="toc-Tags-1" href="#Tags">6.2 Tags</a></li>
  </ul></li>
  <li><a id="toc-Library-interface-versions" href="#Versioning">7 Library interface versions</a>
  <ul class="no-bullet">
    <li><a id="toc-What-are-library-interfaces_003f" href="#Interfaces">7.1 What are library interfaces?</a></li>
    <li><a id="toc-Libtool_0027s-versioning-system" href="#Libtool-versioning">7.2 Libtool’s versioning system</a></li>
    <li><a id="toc-Updating-library-version-information" href="#Updating-version-info">7.3 Updating library version information</a></li>
    <li><a id="toc-Managing-release-information" href="#Release-numbers">7.4 Managing release information</a></li>
  </ul></li>
  <li><a id="toc-Tips-for-interface-design" href="#Library-tips">8 Tips for interface design</a>
  <ul class="no-bullet">
    <li><a id="toc-Writing-C-header-files" href="#C-header-files">8.1 Writing C header files</a></li>
  </ul></li>
  <li><a id="toc-Inter_002dlibrary-dependencies-1" href="#Inter_002dlibrary-dependencies">9 Inter-library dependencies</a></li>
  <li><a id="toc-Dlopened-modules-1" href="#Dlopened-modules">10 Dlopened modules</a>
  <ul class="no-bullet">
    <li><a id="toc-Building-modules-to-dlopen" href="#Building-modules">10.1 Building modules to dlopen</a></li>
    <li><a id="toc-Dlpreopening-1" href="#Dlpreopening">10.2 Dlpreopening</a></li>
    <li><a id="toc-Linking-with-dlopened-modules-1" href="#Linking-with-dlopened-modules">10.3 Linking with dlopened modules</a></li>
    <li><a id="toc-Finding-the-correct-name-to-dlopen" href="#Finding-the-dlname">10.4 Finding the correct name to dlopen</a></li>
    <li><a id="toc-Unresolved-dlopen-issues" href="#Dlopen-issues">10.5 Unresolved dlopen issues</a></li>
  </ul></li>
  <li><a id="toc-Using-libltdl-1" href="#Using-libltdl">11 Using libltdl</a>
  <ul class="no-bullet">
    <li><a id="toc-How-to-use-libltdl-in-your-programs" href="#Libltdl-interface">11.1 How to use libltdl in your programs</a></li>
    <li><a id="toc-Creating-modules-that-can-be-dlopened" href="#Modules-for-libltdl">11.2 Creating modules that can be <code>dlopen</code>ed</a></li>
    <li><a id="toc-Using-libltdl-in-a-multi-threaded-environment" href="#Thread-Safety-in-libltdl">11.3 Using libltdl in a multi threaded environment</a></li>
    <li><a id="toc-Data-associated-with-loaded-modules" href="#User-defined-module-data">11.4 Data associated with loaded modules</a></li>
    <li><a id="toc-How-to-create-and-register-new-module-loaders" href="#Module-loaders-for-libltdl">11.5 How to create and register new module loaders</a>
    <ul class="no-bullet">
      <li><a id="toc-Error-handling-within-user-module-loaders" href="#Error-handling-within-user-module-loaders">11.5.1 Error handling within user module loaders</a></li>
    </ul></li>
    <li><a id="toc-How-to-distribute-libltdl-with-your-package" href="#Distributing-libltdl">11.6 How to distribute libltdl with your package</a></li>
  </ul></li>
  <li><a id="toc-Libtool_0027s-trace-interface" href="#Trace-interface">12 Libtool’s trace interface</a></li>
  <li><a id="toc-Frequently-Asked-Questions-about-libtool" href="#FAQ">13 Frequently Asked Questions about libtool</a>
  <ul class="no-bullet">
    <li><a id="toc-Why-does-libtool-strip-link-flags-when-creating-a-library_003f" href="#Stripped-link-flags">13.1 Why does libtool strip link flags when creating a library?</a></li>
  </ul></li>
  <li><a id="toc-Troubleshooting-1" href="#Troubleshooting">14 Troubleshooting</a>
  <ul class="no-bullet">
    <li><a id="toc-The-libtool-test-suite" href="#Libtool-test-suite">14.1 The libtool test suite</a>
    <ul class="no-bullet">
      <li><a id="toc-Description-of-test-suite" href="#Test-descriptions">14.1.1 Description of test suite</a></li>
      <li><a id="toc-When-tests-fail-1" href="#When-tests-fail">14.1.2 When tests fail</a></li>
    </ul></li>
    <li><a id="toc-Reporting-bugs-1" href="#Reporting-bugs">14.2 Reporting bugs</a></li>
  </ul></li>
  <li><a id="toc-Maintenance-notes-for-libtool" href="#Maintaining">15 Maintenance notes for libtool</a>
  <ul class="no-bullet">
    <li><a id="toc-Porting-libtool-to-new-systems" href="#New-ports">15.1 Porting libtool to new systems</a>
    <ul class="no-bullet">
      <li><a id="toc-Information-sources-1" href="#Information-sources">15.1.1 Information sources</a></li>
      <li><a id="toc-Porting-inter_002dlibrary-dependencies-support" href="#Porting-inter_002dlibrary-dependencies">15.1.2 Porting inter-library dependencies support</a></li>
    </ul></li>
    <li><a id="toc-Tested-platforms-1" href="#Tested-platforms">15.2 Tested platforms</a></li>
    <li><a id="toc-Platform-quirks-1" href="#Platform-quirks">15.3 Platform quirks</a>
    <ul class="no-bullet">
      <li><a id="toc-References-1" href="#References">15.3.1 References</a></li>
      <li><a id="toc-Compilers-1" href="#Compilers">15.3.2 Compilers</a></li>
      <li><a id="toc-Reloadable-objects-1" href="#Reloadable-objects">15.3.3 Reloadable objects</a></li>
      <li><a id="toc-Multiple-dependencies-1" href="#Multiple-dependencies">15.3.4 Multiple dependencies</a></li>
      <li><a id="toc-Archivers-1" href="#Archivers">15.3.5 Archivers</a></li>
      <li><a id="toc-Cross-compiling-1" href="#Cross-compiling">15.3.6 Cross compiling</a></li>
      <li><a id="toc-File-name-conversion-1" href="#File-name-conversion">15.3.7 File name conversion</a>
      <ul class="no-bullet">
        <li><a id="toc-File-Name-Conversion-Failure-1" href="#File-Name-Conversion-Failure">15.3.7.1 File Name Conversion Failure</a></li>
        <li><a id="toc-Native-MinGW-File-Name-Conversion-1" href="#Native-MinGW-File-Name-Conversion">15.3.7.2 Native MinGW File Name Conversion</a></li>
        <li><a id="toc-Cygwin_002fWindows-File-Name-Conversion-1" href="#Cygwin_002fWindows-File-Name-Conversion">15.3.7.3 Cygwin/Windows File Name Conversion</a></li>
        <li><a id="toc-Unix_002fWindows-File-Name-Conversion-1" href="#Unix_002fWindows-File-Name-Conversion">15.3.7.4 Unix/Windows File Name Conversion</a></li>
        <li><a id="toc-LT_005fCYGPATH-1" href="#LT_005fCYGPATH">15.3.7.5 LT_CYGPATH</a></li>
        <li><a id="toc-Cygwin-to-MinGW-Cross-1" href="#Cygwin-to-MinGW-Cross">15.3.7.6 Cygwin to MinGW Cross</a></li>
      </ul></li>
      <li><a id="toc-Windows-DLLs-1" href="#Windows-DLLs">15.3.8 Windows DLLs</a></li>
    </ul></li>
    <li><a id="toc-libtool-script-contents-1" href="#libtool-script-contents">15.4 <code>libtool</code> script contents</a></li>
    <li><a id="toc-Cheap-tricks-1" href="#Cheap-tricks">15.5 Cheap tricks</a></li>
  </ul></li>
  <li><a id="toc-GNU-Free-Documentation-License-1" href="#GNU-Free-Documentation-License">Appendix A GNU Free Documentation License</a></li>
  <li><a id="toc-Combined-Index-1" href="#Combined-Index" rel="index">Combined Index</a></li>
</ul>
</div>


<span id="Top"></span><div class="header">
<p>
Next: <a href="#Introduction" accesskey="n" rel="next">Introduction</a>, Previous: <a href="https://www.gnu.org/savannah-checkouts/gnu/libtool/manual/dir.html#Top" accesskey="p" rel="prev">(dir)</a>, Up: <a href="https://www.gnu.org/savannah-checkouts/gnu/libtool/manual/dir.html#Top" accesskey="u" rel="up">(dir)</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Shared-library-support-for-GNU"></span><h1 class="top">Shared library support for GNU</h1>

<p>This file documents GNU Libtool, a script that allows package developers
to provide generic shared library support.  This edition documents
version 2.4.7-dirty.
</p>
<p>See <a href="#Reporting-bugs">Reporting bugs</a>, for information on how to report problems with
GNU Libtool.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Introduction" accesskey="1">Introduction</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">What the heck is libtool?
</td></tr>
<tr><td align="left" valign="top">• <a href="#Libtool-paradigm" accesskey="2">Libtool paradigm</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How libtool’s view of libraries is different.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Using-libtool" accesskey="3">Using libtool</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Example of using libtool to build libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Invoking-libtool" accesskey="4">Invoking libtool</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Running the <code>libtool</code> script.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Integrating-libtool" accesskey="5">Integrating libtool</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Using libtool in your own packages.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Other-languages" accesskey="6">Other languages</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Using libtool without a C compiler.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Versioning" accesskey="7">Versioning</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Using library interface versions.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Library-tips" accesskey="8">Library tips</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Tips for library interface design.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Inter_002dlibrary-dependencies" accesskey="9">Inter-library dependencies</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Libraries that depend on other libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Dlopened-modules">Dlopened modules</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top"><code>dlopen</code>ing libtool-created libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Using-libltdl">Using libltdl</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Libtool’s portable <code>dlopen</code> wrapper library.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Trace-interface">Trace interface</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Libtool’s trace interface.
</td></tr>
<tr><td align="left" valign="top">• <a href="#FAQ">FAQ</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Frequently Asked Questions
</td></tr>
<tr><td align="left" valign="top">• <a href="#Troubleshooting">Troubleshooting</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">When libtool doesn’t work as advertised.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Maintaining">Maintaining</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Information used by the libtool maintainer.
</td></tr>
<tr><td align="left" valign="top">• <a href="#GNU-Free-Documentation-License">GNU Free Documentation License</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">License for this manual.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Combined-Index" rel="index">Combined Index</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Full index.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
</pre></th></tr><tr><th colspan="3" align="left" valign="top"><pre class="menu-comment"> — The Detailed Node Listing —

Introduction

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Motivation">Motivation</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Why does GNU need a libtool?
</td></tr>
<tr><td align="left" valign="top">• <a href="#Issues">Issues</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">The problems that need to be addressed.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Other-implementations">Other implementations</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How other people have solved these issues.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Postmortem">Postmortem</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Learning from past difficulties.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Using libtool

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Creating-object-files">Creating object files</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Compiling object files for libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Linking-libraries">Linking libraries</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating libraries from object files.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Linking-executables">Linking executables</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Linking object files against libtool libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Debugging-executables">Debugging executables</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Running GDB on libtool-generated programs.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Installing-libraries">Installing libraries</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Making libraries available to users.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Installing-executables">Installing executables</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Making programs available to users.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Static-libraries">Static libraries</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">When shared libraries are not wanted.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Linking executables

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Wrapper-executables">Wrapper executables</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Wrapper executables for some platforms.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Invoking <code>libtool</code>

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Compile-mode">Compile mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating library object files.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Link-mode">Link mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Generating executables and libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Execute-mode">Execute mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Debugging libtool-generated programs.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Install-mode">Install mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Making libraries and executables public.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Finish-mode">Finish mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Completing a library installation.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Uninstall-mode">Uninstall mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Removing installed executables and libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Clean-mode">Clean mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Removing uninstalled executables and libraries.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Integrating libtool with your package

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Autoconf-macros">Autoconf macros</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Autoconf macros exported by libtool.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Makefile-rules">Makefile rules</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Writing <samp>Makefile</samp> rules for libtool.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Using-Automake">Using Automake</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Automatically supporting libtool.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Configuring">Configuring</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Configuring libtool for a host system.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Distributing">Distributing</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">What files to distribute with your package.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Static_002donly-libraries">Static-only libraries</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Sometimes shared libraries are just a pain.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Configuring libtool

</pre></th></tr><tr><td align="left" valign="top">• <a href="#LT_005fINIT">LT_INIT</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Configuring <code>libtool</code> in <samp>configure.ac</samp>.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Configure-notes">Configure notes</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Platform-specific notes for configuration.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Including libtool in your package

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Invoking-libtoolize">Invoking libtoolize</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top"><code>libtoolize</code> command line options.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Autoconf-and-LTLIBOBJS">Autoconf and LTLIBOBJS</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Autoconf automates LTLIBOBJS generation.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Using libtool with other languages

</pre></th></tr><tr><td align="left" valign="top">• <a href="#C_002b_002b-libraries">C++ libraries</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Writing libraries for C++
</td></tr>
<tr><td align="left" valign="top">• <a href="#Tags">Tags</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Tags
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Library interface versions

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Interfaces">Interfaces</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">What are library interfaces?
</td></tr>
<tr><td align="left" valign="top">• <a href="#Libtool-versioning">Libtool versioning</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Libtool’s versioning system.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Updating-version-info">Updating version info</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Changing version information before releases.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Release-numbers">Release numbers</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Breaking binary compatibility for aesthetics.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Tips for interface design

</pre></th></tr><tr><td align="left" valign="top">• <a href="#C-header-files">C header files</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How to write portable include files.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Dlopened modules

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Building-modules">Building modules</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating dlopenable objects and libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Dlpreopening">Dlpreopening</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Dlopening that works on static platforms.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Linking-with-dlopened-modules">Linking with dlopened modules</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Using dlopenable modules in libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Finding-the-dlname">Finding the dlname</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Choosing the right file to <code>dlopen</code>.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Dlopen-issues">Dlopen issues</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Unresolved problems that need your attention.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Using libltdl

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Libltdl-interface">Libltdl interface</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How to use libltdl in your programs.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Modules-for-libltdl">Modules for libltdl</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating modules that can be <code>dlopen</code>ed.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Thread-Safety-in-libltdl">Thread Safety in libltdl</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Registering callbacks for multi-thread safety.
</td></tr>
<tr><td align="left" valign="top">• <a href="#User-defined-module-data">User defined module data</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Associating data with loaded modules.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating user defined module loaders.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Distributing-libltdl">Distributing libltdl</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How to distribute libltdl with your package.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Frequently Asked Questions about libtool

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Stripped-link-flags">Stripped link flags</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Dropped flags when creating a library
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Troubleshooting

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Libtool-test-suite">Libtool test suite</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Libtool’s self-tests.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Reporting-bugs">Reporting bugs</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How to report problems with libtool.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
The libtool test suite

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Test-descriptions">Test descriptions</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">The contents of the old test suite.
</td></tr>
<tr><td align="left" valign="top">• <a href="#When-tests-fail">When tests fail</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">What to do when a test fails.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Maintenance notes for libtool

</pre></th></tr><tr><td align="left" valign="top">• <a href="#New-ports">New ports</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How to port libtool to new systems.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Tested-platforms">Tested platforms</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">When libtool was last tested.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Platform-quirks">Platform quirks</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Information about different library systems.
</td></tr>
<tr><td align="left" valign="top">• <a href="#libtool-script-contents">libtool script contents</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Configuration information that libtool uses.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Cheap-tricks">Cheap tricks</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Making libtool maintainership easier.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Porting libtool to new systems

</pre></th></tr><tr><td align="left" valign="top">• <a href="#Information-sources">Information sources</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Where to find relevant documentation
</td></tr>
<tr><td align="left" valign="top">• <a href="#Porting-inter_002dlibrary-dependencies">Porting inter-library dependencies</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Implementation details explained
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
Platform quirks

</pre></th></tr><tr><td align="left" valign="top">• <a href="#References">References</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Finding more information.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Compilers">Compilers</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating object files from source files.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Reloadable-objects">Reloadable objects</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Binding object files together.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Multiple-dependencies">Multiple dependencies</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Removing duplicate dependent libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Archivers">Archivers</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Programs that create static archives.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Cross-compiling">Cross compiling</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Issues that arise when cross compiling.
</td></tr>
<tr><td align="left" valign="top">• <a href="#File-name-conversion">File name conversion</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Converting file names between platforms.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Windows-DLLs">Windows DLLs</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Windows header defines.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
File name conversion

</pre></th></tr><tr><td align="left" valign="top">• <a href="#File-Name-Conversion-Failure">File Name Conversion Failure</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">What happens when file name conversion fails
</td></tr>
<tr><td align="left" valign="top">• <a href="#Native-MinGW-File-Name-Conversion">Native MinGW File Name Conversion</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">MSYS file name conversion idiosyncrasies
</td></tr>
<tr><td align="left" valign="top">• <a href="#Cygwin_002fWindows-File-Name-Conversion">Cygwin/Windows File Name Conversion</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Using <code>cygpath</code> to convert Cygwin file names
</td></tr>
<tr><td align="left" valign="top">• <a href="#Unix_002fWindows-File-Name-Conversion">Unix/Windows File Name Conversion</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Using Wine to convert Unix paths
</td></tr>
<tr><td align="left" valign="top">• <a href="#LT_005fCYGPATH">LT_CYGPATH</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Invoking <code>cygpath</code> from other environments
</td></tr>
<tr><td align="left" valign="top">• <a href="#Cygwin-to-MinGW-Cross">Cygwin to MinGW Cross</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Other notes concerning MinGW cross
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
</pre></th></tr></tbody></table>


<hr>
<span id="Introduction"></span><div class="header">
<p>
Next: <a href="#Libtool-paradigm" accesskey="n" rel="next">Libtool paradigm</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Introduction-1"></span><h2 class="chapter">1 Introduction</h2>

<p>In the past, if you were a source code package developer and wanted to
take advantage of the power of shared libraries, you needed to write
custom support code for each platform on which your package ran.  You
also had to design a configuration interface so that the package
installer could choose what sort of libraries were built.
</p>
<p>GNU Libtool simplifies your job by encapsulating both the
platform-specific dependencies, and the user interface, in a single
script.  GNU Libtool is designed so that the complete functionality of
each host type is available via a generic interface, but nasty quirks
are hidden from the programmer.
</p>
<p>GNU Libtool’s consistent interface is reassuring… users don’t need
to read obscure documentation to have their favorite source
package build shared libraries.  They just run your package
<code>configure</code> script (or equivalent), and libtool does all the dirty
work.
</p>
<p>There are several examples throughout this document.  All assume the
same environment: we want to build a library, <samp>libhello</samp>, in a
generic way.
</p>
<p><samp>libhello</samp> could be a shared library, a static library, or
both… whatever is available on the host system, as long as libtool
has been ported to it.
</p>
<p>This chapter explains the original design philosophy of libtool.  Feel
free to skip to the next chapter, unless you are interested in history,
or want to write code to extend libtool in a consistent way.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Motivation" accesskey="1">Motivation</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Why does GNU need a libtool?
</td></tr>
<tr><td align="left" valign="top">• <a href="#Issues" accesskey="2">Issues</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">The problems that need to be addressed.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Other-implementations" accesskey="3">Other implementations</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How other people have solved these issues.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Postmortem" accesskey="4">Postmortem</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Learning from past difficulties.
</td></tr>
</tbody></table>

<hr>
<span id="Motivation"></span><div class="header">
<p>
Next: <a href="#Issues" accesskey="n" rel="next">Issues</a>, Up: <a href="#Introduction" accesskey="u" rel="up">Introduction</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Motivation-for-writing-libtool"></span><h3 class="section">1.1 Motivation for writing libtool</h3>

<span id="index-motivation-for-writing-libtool"></span>
<span id="index-design-philosophy"></span>
<p>Since early 1995, several different GNU developers have recognized the
importance of having shared library support for their packages.  The
primary motivation for such a change is to encourage modularity and
reuse of code (both conceptually and physically) in GNU programs.
</p>
<p>Such a demand means that the way libraries are built in GNU packages
needs to be general, to allow for any library type the package installer
might want.  The problem is compounded by the absence of a standard
procedure for creating shared libraries on different platforms.
</p>
<p>The following sections outline the major issues facing shared library
support in GNU, and how shared library support could be standardized
with libtool.
</p>
<span id="index-specifications-for-libtool"></span>
<span id="index-libtool-specifications"></span>
<p>The following specifications were used in developing and evaluating this
system:
</p>
<ol>
<li> The system must be as elegant as possible.

</li><li> The system must be fully integrated with the GNU Autoconf and Automake
utilities, so that it will be easy for GNU maintainers to use.  However,
the system must not require these tools, so that it can be used by
non-GNU packages.

</li><li> Portability to other (non-GNU) architectures and tools is desirable.
</li></ol>

<hr>
<span id="Issues"></span><div class="header">
<p>
Next: <a href="#Other-implementations" accesskey="n" rel="next">Other implementations</a>, Previous: <a href="#Motivation" accesskey="p" rel="prev">Motivation</a>, Up: <a href="#Introduction" accesskey="u" rel="up">Introduction</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Implementation-issues"></span><h3 class="section">1.2 Implementation issues</h3>

<span id="index-tricky-design-issues"></span>
<span id="index-design-issues"></span>
<p>The following issues need to be addressed in any reusable shared library
system, specifically libtool:
</p>
<ol>
<li> The package installer should be able to control what sort of libraries
are built.

</li><li> It can be tricky to run dynamically linked programs whose libraries have
not yet been installed.  <code>LD_LIBRARY_PATH</code> must be set properly (if
it is supported), or programs fail to run.

</li><li> The system must operate consistently even on hosts that don’t support
shared libraries.

</li><li> The commands required to build shared libraries may differ wildly from
host to host.  These need to be determined at configure time in
a consistent way.

</li><li> It is not always obvious with what prefix or suffix a shared library
should be installed.  This makes it difficult for <samp>Makefile</samp> rules,
since they generally assume that file names are the same from host to
host.

</li><li> The system needs a simple library version number abstraction, so that
shared libraries can be upgraded in place.  The programmer should be
informed how to design the interfaces to the library to maximize binary
compatibility.

</li><li> The install <samp>Makefile</samp> target should warn the package installer to set
the proper environment variables (<code>LD_LIBRARY_PATH</code> or equivalent),
or run <code>ldconfig</code>.
</li></ol>

<hr>
<span id="Other-implementations"></span><div class="header">
<p>
Next: <a href="#Postmortem" accesskey="n" rel="next">Postmortem</a>, Previous: <a href="#Issues" accesskey="p" rel="prev">Issues</a>, Up: <a href="#Introduction" accesskey="u" rel="up">Introduction</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Other-implementations-1"></span><h3 class="section">1.3 Other implementations</h3>

<p>Even before libtool was developed, many free software packages built and
installed their own shared libraries.  At first, these packages were
examined to avoid reinventing existing features.
</p>
<p>Now it is clear that none of these packages have documented the details
of shared library systems that libtool requires.  So, other packages
have been more or less abandoned as influences.
</p>
<hr>
<span id="Postmortem"></span><div class="header">
<p>
Previous: <a href="#Other-implementations" accesskey="p" rel="prev">Other implementations</a>, Up: <a href="#Introduction" accesskey="u" rel="up">Introduction</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="A-postmortem-analysis-of-other-implementations"></span><h3 class="section">1.4 A postmortem analysis of other implementations</h3>

<span id="index-other-implementations_002c-flaws-in"></span>
<span id="index-reusability-of-library-systems"></span>
<p>In all fairness, each of the implementations that were examined do the
job that they were intended to do, for a number of different host
systems.  However, none of these solutions seem to function well as a
generalized, reusable component.
</p>
<span id="index-complexity-of-library-systems"></span>
<p>Most were too complex to use (much less modify) without understanding
exactly what the implementation does, and they were generally not
documented.
</p>
<p>The main difficulty is that different vendors have different views of
what libraries are, and none of the packages that were examined seemed
to be confident enough to settle on a single paradigm that just
<em>works</em>.
</p>
<p>Ideally, libtool would be a standard that would be implemented as series
of extensions and modifications to existing library systems to make them
work consistently.  However, it is not an easy task to convince
operating system developers to mend their evil ways, and people want to
build shared libraries right now, even on buggy, broken, confused
operating systems.
</p>
<p>For this reason, libtool was designed as an independent shell script.
It isolates the problems and inconsistencies in library building that
plague <samp>Makefile</samp> writers by wrapping the compiler suite on
different platforms with a consistent, powerful interface.
</p>
<p>With luck, libtool will be useful to and used by the GNU community, and
that the lessons that were learned in writing it will be taken up by
designers of future library systems.
</p>
<hr>
<span id="Libtool-paradigm"></span><div class="header">
<p>
Next: <a href="#Using-libtool" accesskey="n" rel="next">Using libtool</a>, Previous: <a href="#Introduction" accesskey="p" rel="prev">Introduction</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="The-libtool-paradigm"></span><h2 class="chapter">2 The libtool paradigm</h2>

<p>At first, libtool was designed to support an arbitrary number of library
object types.  After libtool was ported to more platforms, a new
paradigm gradually developed for describing the relationship between
libraries and programs.
</p>
<span id="index-definition-of-libraries"></span>
<span id="index-libraries_002c-definition-of"></span>
<p>In summary, “libraries are programs with multiple entry points, and
more formally defined interfaces.”
</p>
<p>Version 0.7 of libtool was a complete redesign and rewrite of libtool to
reflect this new paradigm.  So far, it has proved to be successful:
libtool is simpler and more useful than before.
</p>
<p>The best way to introduce the libtool paradigm is to contrast it with
the paradigm of existing library systems, with examples from each.  It
is a new way of thinking, so it may take a little time to absorb, but
when you understand it, the world becomes simpler.
</p>
<hr>
<span id="Using-libtool"></span><div class="header">
<p>
Next: <a href="#Invoking-libtool" accesskey="n" rel="next">Invoking libtool</a>, Previous: <a href="#Libtool-paradigm" accesskey="p" rel="prev">Libtool paradigm</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Using-libtool-1"></span><h2 class="chapter">3 Using libtool</h2>

<span id="index-examples-of-using-libtool"></span>
<span id="index-libtool-examples"></span>
<p>It makes little sense to talk about using libtool in your own packages
until you have seen how it makes your life simpler.  The examples in
this chapter introduce the main features of libtool by comparing the
standard library building procedure to libtool’s operation on two
different platforms:
</p>
<dl compact="compact">
<dt>‘<samp>a23</samp>’</dt>
<dd><p>An Ultrix 4.2 platform with only static libraries.
</p>
</dd>
<dt>‘<samp>burger</samp>’</dt>
<dd><p>A NetBSD/i386 1.2 platform with shared libraries.
</p></dd>
</dl>

<p>You can follow these examples on your own platform, using the
preconfigured libtool script that was installed with libtool
(see <a href="#Configuring">Configuring</a>).
</p>
<p>Source files for the following examples are taken from the <samp>demo</samp>
subdirectory of the libtool distribution.  Assume that we are building a
library, <samp>libhello</samp>, out of the files <samp>foo.c</samp> and
<samp>hello.c</samp>.
</p>
<p>Note that the <samp>foo.c</samp> source file uses the <code>cos</code> math library
function, which is usually found in the standalone math library, and not
the C library (see <a href="https://www.gnu.org/software/libc/manual/html_mono/libc.html#Trig-Functions">Trigonometric Functions</a> in <cite>The GNU C Library Reference Manual</cite>).  So, we need to add <samp>-lm</samp> to
the end of the link line whenever we link <samp>foo.lo</samp> into an
executable or a library (see <a href="#Inter_002dlibrary-dependencies">Inter-library dependencies</a>).
</p>
<p>The same rule applies whenever you use functions that don’t appear in
the standard C library… you need to add the appropriate
<samp>-l<var>name</var></samp> flag to the end of the link line when you link
against those objects.
</p>
<p>After we have built that library, we want to create a program by linking
<samp>main.o</samp> against <samp>libhello</samp>.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Creating-object-files" accesskey="1">Creating object files</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Compiling object files for libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Linking-libraries" accesskey="2">Linking libraries</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating libraries from object files.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Linking-executables" accesskey="3">Linking executables</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Linking object files against libtool libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Debugging-executables" accesskey="4">Debugging executables</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Running GDB on libtool-generated programs.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Installing-libraries" accesskey="5">Installing libraries</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Making libraries available to users.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Installing-executables" accesskey="6">Installing executables</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Making programs available to users.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Static-libraries" accesskey="7">Static libraries</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">When shared libraries are not wanted.
</td></tr>
</tbody></table>

<hr>
<span id="Creating-object-files"></span><div class="header">
<p>
Next: <a href="#Linking-libraries" accesskey="n" rel="next">Linking libraries</a>, Up: <a href="#Using-libtool" accesskey="u" rel="up">Using libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Creating-object-files-1"></span><h3 class="section">3.1 Creating object files</h3>

<span id="index-compiling-object-files"></span>
<span id="index-object-files_002c-compiling"></span>
<p>To create an object file from a source file, the compiler is invoked
with the <samp>-c</samp> flag (and any other desired flags):
</p>
<div class="example">
<pre class="example">burger$ <kbd>gcc -g -O -c main.c</kbd>
burger$
</pre></div>

<p>The above compiler command produces an object file, usually named
<samp>main.o</samp>, from the source file <samp>main.c</samp>.
</p>
<p>For most library systems, creating object files that become part of a
static library is as simple as creating object files that are linked to
form an executable:
</p>
<div class="example">
<pre class="example">burger$ <kbd>gcc -g -O -c foo.c</kbd>
burger$ <kbd>gcc -g -O -c hello.c</kbd>
burger$
</pre></div>

<span id="index-position_002dindependent-code"></span>
<span id="index-PIC-_0028position_002dindependent-code_0029"></span>
<p>Shared libraries, however, may only be built from
<em>position-independent code</em> (PIC).  So, special flags must be passed
to the compiler to tell it to generate PIC rather than the standard
position-dependent code.
</p>
<span id="index-library-object-file"></span>
<span id="index-_002elo-files"></span>
<span id="index-object-files_002c-library"></span>
<p>Since this is a library implementation detail, libtool hides the
complexity of PIC compiler flags and uses separate library object files
(the PIC one lives in the <samp>.libs</samp> subdirectory and the
static one lives in the current directory).  On systems without shared
libraries, the PIC library object files are not created, whereas on
systems where all code is PIC, such as AIX, the static ones are not
created.
</p>
<p>To create library object files for <samp>foo.c</samp> and <samp>hello.c</samp>,
simply invoke libtool with the standard compilation command as
arguments (see <a href="#Compile-mode">Compile mode</a>):
</p>
<div class="example">
<pre class="example">a23$ <kbd>libtool --mode=compile gcc -g -O -c foo.c</kbd>
gcc -g -O -c foo.c -o foo.o
a23$ <kbd>libtool --mode=compile gcc -g -O -c hello.c</kbd>
gcc -g -O -c hello.c -o hello.o
a23$
</pre></div>

<p>Note that libtool silently creates an additional control file on each
‘<samp>compile</samp>’ invocation.  The <samp>.lo</samp> file is the libtool object,
which Libtool uses to determine what object file may be built into a
shared library.  On ‘<samp>a23</samp>’, only static libraries are supported so
the library objects look like this:
</p>
<div class="example">
<pre class="example"># foo.lo - a libtool object file
# Generated by ltmain.sh (GNU libtool) 2.4.7-dirty
#
# Please DO NOT delete this file!
# It is necessary for linking the library.

# Name of the PIC object.
pic_object=none

# Name of the non-PIC object.
non_pic_object='foo.o'
</pre></div>

<p>On shared library systems, libtool automatically generates an
additional PIC object by inserting the appropriate PIC generation
flags into the compilation command:
</p>
<div class="example">
<pre class="example">burger$ <kbd>libtool --mode=compile gcc -g -O -c foo.c</kbd>
mkdir .libs
gcc -g -O -c foo.c  -fPIC -DPIC -o .libs/foo.o
gcc -g -O -c foo.c -o foo.o &gt;/dev/null 2&gt;&amp;1
burger$
</pre></div>

<p>Note that Libtool automatically created <samp>.libs</samp> directory
upon its first execution, where PIC library object files will be stored.
</p>
<p>Since ‘<samp>burger</samp>’ supports shared libraries, and requires PIC
objects to build them, Libtool has compiled a PIC object this time,
and made a note of it in the libtool object:
</p>
<div class="example">
<pre class="example"># foo.lo - a libtool object file
# Generated by ltmain.sh (GNU libtool) 2.4.7-dirty
#
# Please DO NOT delete this file!
# It is necessary for linking the library.

# Name of the PIC object.
pic_object='.libs/foo.o'

# Name of the non-PIC object.
non_pic_object='foo.o'
</pre></div>

<span id="index-_002dno_002dsuppress_002c-libtool-compile-mode-option"></span>
<p>Notice that the second run of GCC has its output discarded.  This is
done so that compiler warnings aren’t annoyingly duplicated.  If you
need to see both sets of warnings (you might have conditional code
inside ‘<samp>#ifdef PIC</samp>’ for example), you can turn off suppression with
the <samp>-no-suppress</samp> option to libtool’s compile mode:
</p>
<div class="example">
<pre class="example">burger$ <kbd>libtool --mode=compile gcc -no-suppress -g -O -c hello.c</kbd>
gcc -g -O -c hello.c  -fPIC -DPIC -o .libs/hello.o
gcc -g -O -c hello.c -o hello.o
burger$
</pre></div>


<hr>
<span id="Linking-libraries"></span><div class="header">
<p>
Next: <a href="#Linking-executables" accesskey="n" rel="next">Linking executables</a>, Previous: <a href="#Creating-object-files" accesskey="p" rel="prev">Creating object files</a>, Up: <a href="#Using-libtool" accesskey="u" rel="up">Using libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Linking-libraries-1"></span><h3 class="section">3.2 Linking libraries</h3>

<span id="index-ar"></span>
<p>Without libtool, the programmer would invoke the <code>ar</code> command to
create a static library:
</p>
<div class="example">
<pre class="example">burger$ <kbd>ar cr libhello.a hello.o foo.o</kbd>
burger$
</pre></div>

<span id="index-ranlib"></span>
<p>But of course, that would be too simple, so many systems require that
you run the <code>ranlib</code> command on the resulting library (to give it
better karma, or something):
</p>
<div class="example">
<pre class="example">burger$ <kbd>ranlib libhello.a</kbd>
burger$
</pre></div>

<p>It seems more natural to use the C compiler for this task, given
libtool’s “libraries are programs” approach.  So, on platforms without
shared libraries, libtool simply acts as a wrapper for the system
<code>ar</code> (and possibly <code>ranlib</code>) commands.
</p>
<span id="index-libtool-libraries"></span>
<span id="index-_002ela-files"></span>
<p>Again, the libtool control file name (<samp>.la</samp> suffix) differs from
the standard library name (<samp>.a</samp> suffix).  The arguments to
libtool are the same ones you would use to produce an executable named
<samp>libhello.la</samp> with your compiler (see <a href="#Link-mode">Link mode</a>):
</p>
<div class="example">
<pre class="example">a23$ <kbd>libtool --mode=link gcc -g -O -o libhello.la foo.o hello.o</kbd>
*** Warning: Linking the shared library libhello.la against the
*** non-libtool objects foo.o hello.o is not portable!
ar cr .libs/libhello.a
ranlib .libs/libhello.a
creating libhello.la
(cd .libs &amp;&amp; rm -f libhello.la &amp;&amp; ln -s ../libhello.la libhello.la)
a23$
</pre></div>

<p>Aha!  Libtool caught a common error… trying to build a library
from standard objects instead of special <samp>.lo</samp> object files.  This
doesn’t matter so much for static libraries, but on shared library
systems, it is of great importance.  (Note that you may replace
<samp>libhello.la</samp> with <samp>libhello.a</samp> in which case libtool won’t
issue the warning any more.  But although this method works, this is
not intended to be used because it makes you lose the benefits of
using Libtool.)
</p>
<p>So, let’s try again, this time with the library object files.  Remember
also that we need to add <samp>-lm</samp> to the link command line because
<samp>foo.c</samp> uses the <code>cos</code> math library function (see <a href="#Using-libtool">Using libtool</a>).
</p>
<p>Another complication in building shared libraries is that we need to
specify the path to the directory wher they will (eventually) be
installed (in this case, <samp>/usr/local/lib</samp>)<a id="DOCF1" href="#FOOT1"><sup>1</sup></a>:
</p>
<div class="example">
<pre class="example">a23$ <kbd>libtool --mode=link gcc -g -O -o libhello.la foo.lo hello.lo \
                -rpath /usr/local/lib -lm</kbd>
ar cr .libs/libhello.a foo.o hello.o
ranlib .libs/libhello.a
creating libhello.la
(cd .libs &amp;&amp; rm -f libhello.la &amp;&amp; ln -s ../libhello.la libhello.la)
a23$
</pre></div>

<p>Now, let’s try the same trick on the shared library platform:
</p>
<div class="example">
<pre class="example">burger$ <kbd>libtool --mode=link gcc -g -O -o libhello.la foo.lo hello.lo \
                -rpath /usr/local/lib -lm</kbd>
rm -fr  .libs/libhello.a .libs/libhello.la
ld -Bshareable -o .libs/libhello.so.0.0 .libs/foo.o .libs/hello.o -lm
ar cr .libs/libhello.a foo.o hello.o
ranlib .libs/libhello.a
creating libhello.la
(cd .libs &amp;&amp; rm -f libhello.la &amp;&amp; ln -s ../libhello.la libhello.la)
burger$
</pre></div>

<p>Now that’s significantly cooler… Libtool just ran an obscure
<code>ld</code> command to create a shared library, as well as the static
library.
</p>
<span id="index-_002elibs-subdirectory"></span>
<p>Note how libtool creates extra files in the <samp>.libs</samp>
subdirectory, rather than the current directory.  This feature is to
make it easier to clean up the build directory, and to help ensure that
other programs fail horribly if you accidentally forget to use libtool
when you should.
</p>
<p>Again, you may want to have a look at the <samp>.la</samp> file
to see what Libtool stores in it.  In particular, you will see that
Libtool uses this file to remember the destination directory for the
library (the argument to <samp>-rpath</samp>) as well as the dependency
on the math library (‘<samp>-lm</samp>’).
</p>
<hr>
<span id="Linking-executables"></span><div class="header">
<p>
Next: <a href="#Debugging-executables" accesskey="n" rel="next">Debugging executables</a>, Previous: <a href="#Linking-libraries" accesskey="p" rel="prev">Linking libraries</a>, Up: <a href="#Using-libtool" accesskey="u" rel="up">Using libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Linking-executables-1"></span><h3 class="section">3.3 Linking executables</h3>

<span id="index-linking-against-installed-libraries"></span>
<p>If you choose at this point to <em>install</em> the library (put it in a
permanent location) before linking executables against it, then you
don’t need to use libtool to do the linking.  Simply use the appropriate
<samp>-L</samp> and <samp>-l</samp> flags to specify the library’s location.
</p>
<span id="index-buggy-system-linkers"></span>
<p>Some system linkers insist on encoding the full directory name of each
shared library in the resulting executable.  Libtool has to work around
this misfeature by special magic to ensure that only permanent directory
names are put into installed executables.
</p>
<span id="index-security-problems-with-buggy-linkers"></span>
<span id="index-bugs_002c-subtle-ones-caused-by-buggy-linkers"></span>
<p>The importance of this bug must not be overlooked: it won’t cause
programs to crash in obvious ways.  It creates a security hole,
and possibly even worse, if you are modifying the library source code
after you have installed the package, you will change the behaviour of
the installed programs!
</p>
<p>So, if you want to link programs against the library before you install
it, you must use libtool to do the linking.
</p>
<span id="index-linking-against-uninstalled-libraries"></span>
<p>Here’s the old way of linking against an uninstalled library:
</p>
<div class="example">
<pre class="example">burger$ <kbd>gcc -g -O -o hell.old main.o libhello.a -lm</kbd>
burger$
</pre></div>

<p>Libtool’s way is almost the same<a id="DOCF2" href="#FOOT2"><sup>2</sup></a>
(see <a href="#Link-mode">Link mode</a>):
</p>
<div class="example">
<pre class="example">a23$ <kbd>libtool --mode=link gcc -g -O -o hell main.o libhello.la</kbd>
gcc -g -O -o hell main.o  ./.libs/libhello.a -lm
a23$
</pre></div>

<p>That looks too simple to be true.  All libtool did was transform
<samp>libhello.la</samp> to <samp>./.libs/libhello.a</samp>, but remember
that ‘<samp>a23</samp>’ has no shared libraries.  Notice that Libtool also
remembered that <samp>libhello.la</samp> depends on <samp>-lm</samp>, so even
though we didn’t specify <samp>-lm</samp> on the libtool command
line<a id="DOCF3" href="#FOOT3"><sup>3</sup></a> Libtool has added it to the <code>gcc</code> link line for us.
</p>
<p>On ‘<samp>burger</samp>’ Libtool links against the uninstalled shared library:
</p>
<div class="example">
<pre class="example">burger$ <kbd>libtool --mode=link gcc -g -O -o hell main.o libhello.la</kbd>
gcc -g -O -o .libs/hell main.o -L./.libs -R/usr/local/lib -lhello -lm
creating hell
burger$
</pre></div>

<span id="index-linking-with-installed-libtool-libraries"></span>
<p>Now assume <samp>libhello.la</samp> had already been installed, and you want
to link a new program with it.  You could figure out where it lives by
yourself, then run:
</p>
<div class="example">
<pre class="example">burger$ <kbd>gcc -g -O -o test test.o -L/usr/local/lib -lhello -lm</kbd>
</pre></div>

<p>However, unless <samp>/usr/local/lib</samp> is in the standard library search
path, you won’t be able to run <code>test</code>.  However, if you use libtool
to link the already-installed libtool library, it will do The Right
Thing (TM) for you:
</p>
<div class="example">
<pre class="example">burger$ <kbd>libtool --mode=link gcc -g -O -o test test.o \
                /usr/local/lib/libhello.la</kbd>
gcc -g -O -o .libs/test test.o -Wl,--rpath \
        -Wl,/usr/local/lib /usr/local/lib/libhello.a -lm
creating test
burger$
</pre></div>

<p>Note that libtool added the necessary run-time path flag, as well as
<samp>-lm</samp>, the library libhello.la depended upon.  Nice, huh?
</p>
<span id="index-wrapper-scripts-for-programs"></span>
<span id="index-program-wrapper-scripts"></span>
<p>Notice that the executable, <code>hell</code>, was actually created in the
<samp>.libs</samp> subdirectory.  Then, a wrapper script (or, on
certain platforms, a wrapper executable see <a href="#Wrapper-executables">Wrapper executables</a>) was
created in the current directory.
</p>
<p>Since libtool created a wrapper script, you should use libtool to
install it and debug it too.  However, since the program does not depend
on any uninstalled libtool library, it is probably usable even without
the wrapper script.
</p>
<p>On NetBSD 1.2, libtool encodes the installation directory of
<samp>libhello</samp>, by using the ‘<samp>-R/usr/local/lib</samp>’ compiler flag.
Then, the wrapper script guarantees that the executable finds the
correct shared library (the one in <samp>./.libs</samp>) until it is
properly installed.
</p>
<p>Let’s compare the two different programs:
</p>
<div class="example">
<pre class="example">burger$ <kbd>time ./hell.old</kbd>
Welcome to GNU Hell!
** This is not GNU Hello.  There is no built-in mail reader. **
        0.21 real         0.02 user         0.08 sys
burger$ <kbd>time ./hell</kbd>
Welcome to GNU Hell!
** This is not GNU Hello.  There is no built-in mail reader. **
        0.63 real         0.09 user         0.59 sys
burger$
</pre></div>

<p>The wrapper script takes significantly longer to execute, but at least
the results are correct, even though the shared library hasn’t been
installed yet.
</p>
<p>So, what about all the space savings that shared libraries are supposed
to yield?
</p>
<div class="example">
<pre class="example">burger$ <kbd>ls -l hell.old libhello.a</kbd>
-rwxr-xr-x  1 gord  gord  15481 Nov 14 12:11 hell.old
-rw-r--r--  1 gord  gord   4274 Nov 13 18:02 libhello.a
burger$ <kbd>ls -l .libs/hell .libs/libhello.*</kbd>
-rwxr-xr-x  1 gord  gord  11647 Nov 14 12:10 .libs/hell
-rw-r--r--  1 gord  gord   4274 Nov 13 18:44 .libs/libhello.a
-rwxr-xr-x  1 gord  gord  12205 Nov 13 18:44 .libs/libhello.so.0.0
burger$
</pre></div>

<p>Well, that sucks.  Maybe I should just scrap this project and take up
basket weaving.
</p>
<p>Actually, it just proves an important point: shared libraries incur
overhead because of their (relative) complexity.  In this situation, the
price of being dynamic is eight kilobytes, and the payoff is about four
kilobytes.  So, having a shared <samp>libhello</samp> won’t be an advantage
until we link it against at least a few more programs.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Wrapper-executables" accesskey="1">Wrapper executables</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Wrapper executables for some platforms.
</td></tr>
</tbody></table>

<hr>
<span id="Wrapper-executables"></span><div class="header">
<p>
Up: <a href="#Linking-executables" accesskey="u" rel="up">Linking executables</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Wrapper-executables-for-uninstalled-programs"></span><h4 class="subsection">3.3.1 Wrapper executables for uninstalled programs</h4>
<span id="index-wrapper-executables-for-uninstalled-programs"></span>
<span id="index-program-wrapper-executables"></span>

<p>Some platforms, notably those hosted on Windows such as Cygwin
and MinGW, use a wrapper executable rather than a wrapper script
to ensure proper operation of uninstalled programs linked by libtool
against uninstalled shared libraries. The wrapper executable thus
performs the same function as the wrapper script used on other
platforms, but allows to satisfy the <code>make</code> rules for the
program, whose name ends in <code>$(EXEEXT)</code>. The actual program
executable is created below .libs, and its name will end
in <code>$(EXEEXT)</code> and may or may not contain an <code>lt-</code> prefix.
This wrapper executable sets various environment values so that the
program executable may locate its (uninstalled) shared libraries,
and then launches the program executable.
</p>
<p>The wrapper executable provides a debug mode, enabled by passing the
command-line option <code>--lt-debug</code> (see below). When executing in
debug mode, diagnostic information will be printed to <code>stderr</code>
before the program executable is launched.
</p>
<p>Finally, the wrapper executable supports a number of command line
options that may be useful when debugging the operation of the wrapper
system. All of these options begin with <code>--lt-</code>, and if present
they and their arguments will be removed from the argument list passed
on to the program executable.  Therefore, the program executable may not
employ command line options that begin with <code>--lt-</code>. (In fact, the
wrapper executable will detect any command line options that begin with
<code>--lt-</code> and abort with an error message if the option is not
recognized). If this presents a problem, please contact the Libtool
team at the Libtool bug reporting address <a href="mailto:bug-libtool@gnu.org">bug-libtool@gnu.org</a>.
</p>
<p>These command line options include:
</p>
<dl compact="compact">
<dt><samp>--lt-dump-script</samp></dt>
<dd><p>Causes the wrapper to print a copy of the wrapper <em>script</em>
to <code>stdout</code>, and exit.
</p>
</dd>
<dt><samp>--lt-debug</samp></dt>
<dd><p>Causes the wrapper to print diagnostic information to <code>stdout</code>,
before launching the program executable.
</p>
</dd>
</dl>

<p>For consistency, both the wrapper <em>script</em> and the wrapper
<em>executable</em> support these options.
</p>
<hr>
<span id="Debugging-executables"></span><div class="header">
<p>
Next: <a href="#Installing-libraries" accesskey="n" rel="next">Installing libraries</a>, Previous: <a href="#Linking-executables" accesskey="p" rel="prev">Linking executables</a>, Up: <a href="#Using-libtool" accesskey="u" rel="up">Using libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Debugging-executables-1"></span><h3 class="section">3.4 Debugging executables</h3>

<p>If <samp>hell</samp> was a complicated program, you would certainly want to
test and debug it before installing it on your system.  In the above
section, you saw how the libtool wrapper script makes it possible to run
the program directly, but unfortunately, this mechanism interferes with
the debugger:
</p>
<div class="example">
<pre class="example">burger$ <kbd>gdb hell</kbd>
GDB is free software and you are welcome to distribute copies of it
 under certain conditions; type "show copying" to see the conditions.
There is no warranty for GDB; type "show warranty" for details.
GDB 4.16 (i386-unknown-netbsd), (C) 1996 Free Software Foundation, Inc.

"hell": not in executable format: File format not recognized

(gdb) <kbd>quit</kbd>
burger$
</pre></div>

<p>Sad.  It doesn’t work because GDB doesn’t know where the executable
lives.  So, let’s try again, by invoking GDB directly on the executable:
</p>
<div class="example">
<pre class="example">burger$ <kbd>gdb .libs/hell</kbd>
GNU gdb 5.3 (i386-unknown-netbsd)
Copyright 2002 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it
under certain conditions.  Type "show copying" to see the conditions.
There is no warranty for GDB.  Type "show warranty" for details.
(gdb) <kbd>break main</kbd>
Breakpoint 1 at 0x8048547: file main.c, line 29.
(gdb) <kbd>run</kbd>
Starting program: /home/src/libtool/demo/.libs/hell
/home/src/libtool/demo/.libs/hell: can't load library 'libhello.so.0'

Program exited with code 020.
(gdb) <kbd>quit</kbd>
burger$
</pre></div>

<p>Argh.  Now GDB complains because it cannot find the shared library that
<samp>hell</samp> is linked against.  So, we must use libtool to
properly set the library path and run the debugger.  Fortunately, we can
forget all about the <samp>.libs</samp> directory, and just run it on
the executable wrapper (see <a href="#Execute-mode">Execute mode</a>):
</p>
<div class="example">
<pre class="example">burger$ <kbd>libtool --mode=execute gdb hell</kbd>
GNU gdb 5.3 (i386-unknown-netbsd)
Copyright 2002 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it
under certain conditions.  Type "show copying" to see the conditions.
There is no warranty for GDB.  Type "show warranty" for details.
(gdb) <kbd>break main</kbd>
Breakpoint 1 at 0x8048547: file main.c, line 29.
(gdb) <kbd>run</kbd>
Starting program: /home/src/libtool/demo/.libs/hell

Breakpoint 1, main (argc=1, argv=0xbffffc40) at main.c:29
29        printf ("Welcome to GNU Hell!\n");
(gdb) <kbd>quit</kbd>
The program is running.  Quit anyway (and kill it)? (y or n) <kbd>y</kbd>
burger$
</pre></div>

<hr>
<span id="Installing-libraries"></span><div class="header">
<p>
Next: <a href="#Installing-executables" accesskey="n" rel="next">Installing executables</a>, Previous: <a href="#Debugging-executables" accesskey="p" rel="prev">Debugging executables</a>, Up: <a href="#Using-libtool" accesskey="u" rel="up">Using libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Installing-libraries-1"></span><h3 class="section">3.5 Installing libraries</h3>

<span id="index-strip"></span>
<p>Installing libraries on a non-libtool system is quite
straightforward… just copy them into place:<a id="DOCF4" href="#FOOT4"><sup>4</sup></a>
</p>
<span id="index-su"></span>
<div class="example">
<pre class="example">burger$ <kbd>su</kbd>
Password: <kbd>********</kbd>
burger# <kbd>cp libhello.a /usr/local/lib/libhello.a</kbd>
burger#
</pre></div>

<p>Oops, don’t forget the <code>ranlib</code> command:
</p>
<div class="example">
<pre class="example">burger# <kbd>ranlib /usr/local/lib/libhello.a</kbd>
burger#
</pre></div>

<span id="index-install"></span>
<p>Libtool installation is quite simple, as well.  Just use the
<code>install</code> or <code>cp</code> command that you normally would
(see <a href="#Install-mode">Install mode</a>):
</p>
<div class="example">
<pre class="example">a23# <kbd>libtool --mode=install cp libhello.la /usr/local/lib/libhello.la</kbd>
cp libhello.la /usr/local/lib/libhello.la
cp .libs/libhello.a /usr/local/lib/libhello.a
ranlib /usr/local/lib/libhello.a
a23#
</pre></div>

<p>Note that the libtool library <samp>libhello.la</samp> is also installed, to
help libtool with uninstallation (see <a href="#Uninstall-mode">Uninstall mode</a>) and linking
(see <a href="#Linking-executables">Linking executables</a>) and to help programs with dlopening
(see <a href="#Dlopened-modules">Dlopened modules</a>).
</p>
<p>Here is the shared library example:
</p>
<div class="example">
<pre class="example">burger# <kbd>libtool --mode=install install -c libhello.la \
                /usr/local/lib/libhello.la</kbd>
install -c .libs/libhello.so.0.0 /usr/local/lib/libhello.so.0.0
install -c libhello.la /usr/local/lib/libhello.la
install -c .libs/libhello.a /usr/local/lib/libhello.a
ranlib /usr/local/lib/libhello.a
burger#
</pre></div>

<span id="index-stripping-libraries"></span>
<span id="index-libraries_002c-stripping"></span>
<p>It is safe to specify the <samp>-s</samp> (strip symbols) flag if you use a
BSD-compatible install program when installing libraries.
Libtool will either ignore the <samp>-s</samp> flag, or will run a program
that will strip only debugging and compiler symbols from the library.
</p>
<p>Once the libraries have been put in place, there may be some additional
configuration that you need to do before using them.  First, you must
make sure that where the library is installed actually agrees with the
<samp>-rpath</samp> flag you used to build it.
</p>
<span id="index-postinstallation"></span>
<span id="index-installation_002c-finishing"></span>
<span id="index-libraries_002c-finishing-installation"></span>
<p>Then, running ‘<samp>libtool -n finish <var>libdir</var></samp>’ can give you
further hints on what to do (see <a href="#Finish-mode">Finish mode</a>):
</p>
<div class="example">
<pre class="example">burger# <kbd>libtool -n finish /usr/local/lib</kbd>
PATH="$PATH:/sbin" ldconfig -m /usr/local/lib
-----------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

To link against installed libraries in a given directory, LIBDIR,
you must use the '-LLIBDIR' flag during linking.

 You will also need to do one of the following:
   - add LIBDIR to the 'LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the 'LD_RUN_PATH' environment variable
     during linking
   - use the '-RLIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld and ld.so manual pages.
-----------------------------------------------------------------
burger#
</pre></div>

<p>After you have completed these steps, you can go on to begin using the
installed libraries.  You may also install any executables that depend
on libraries you created.
</p>
<hr>
<span id="Installing-executables"></span><div class="header">
<p>
Next: <a href="#Static-libraries" accesskey="n" rel="next">Static libraries</a>, Previous: <a href="#Installing-libraries" accesskey="p" rel="prev">Installing libraries</a>, Up: <a href="#Using-libtool" accesskey="u" rel="up">Using libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Installing-executables-1"></span><h3 class="section">3.6 Installing executables</h3>

<p>If you used libtool to link any executables against uninstalled libtool
libraries (see <a href="#Linking-executables">Linking executables</a>), you need to use libtool to
install the executables after the libraries have been installed
(see <a href="#Installing-libraries">Installing libraries</a>).
</p>
<p>So, for our Ultrix example, we would run:
</p>
<div class="example">
<pre class="example">a23# libtool --mode=install install -c hell /usr/local/bin/hell
install -c hell /usr/local/bin/hell
a23#
</pre></div>

<p>On shared library systems that require wrapper scripts, libtool just
ignores the wrapper script and installs the correct binary:
</p>
<div class="example">
<pre class="example">burger# libtool --mode=install install -c hell /usr/local/bin/hell
install -c .libs/hell /usr/local/bin/hell
burger#
</pre></div>


<hr>
<span id="Static-libraries"></span><div class="header">
<p>
Previous: <a href="#Installing-executables" accesskey="p" rel="prev">Installing executables</a>, Up: <a href="#Using-libtool" accesskey="u" rel="up">Using libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Linking-static-libraries"></span><h3 class="section">3.7 Linking static libraries</h3>

<span id="index-static-linking"></span>
<span id="index-convenience-libraries"></span>
<p>Why return to <code>ar</code> and <code>ranlib</code> silliness when you’ve had a
taste of libtool?  Well, sometimes it is desirable to create a static
archive that can never be shared.  The most frequent case is when you
have a set of object files that you use to build several different
libraries.  You can create a “convenience library” out of those
objects, and link against that with the other libraries, instead of
listing all the object files every time.
</p>
<p>If you just want to link this convenience library into programs, then
you could just ignore libtool entirely, and use the old <code>ar</code> and
<code>ranlib</code> commands (or the corresponding GNU Automake
‘<samp>_LIBRARIES</samp>’ rules).  You can even install a convenience library
using GNU Libtool, though you probably don’t want to and hence GNU
Automake doesn’t allow you to do so.
</p>
<div class="example">
<pre class="example">burger$ <kbd>libtool --mode=install ./install-sh -c libhello.a \
                /local/lib/libhello.a</kbd>
./install-sh -c libhello.a /local/lib/libhello.a
ranlib /local/lib/libhello.a
burger$
</pre></div>

<p>Using libtool for static library installation protects your library from
being accidentally stripped (if the installer used the <samp>-s</samp> flag),
as well as automatically running the correct <code>ranlib</code> command.
</p>
<p>But libtool libraries are more than just collections of object files:
they can also carry library dependency information, which old archives
do not.  If you want to create a libtool static convenience library, you
can omit the <samp>-rpath</samp> flag and use <samp>-static</samp> to indicate that
you’re only interested in a static library.  When you link a program
with such a library, libtool will actually link all object files and
dependency libraries into the program.
</p>
<p>If you omit both <samp>-rpath</samp> and <samp>-static</samp>, libtool will create a
convenience library that can be used to create other libtool
libraries, even shared ones.  Just like in the static case, the library
behaves as an alias to a set of object files and dependency libraries,
but in this case the object files are suitable for inclusion in shared
libraries.  But be careful not to link a single convenience library,
directly or indirectly, into a single program or library, otherwise you
may get errors about symbol redefinitions.
</p>
<p>The key is remembering that a convenience library contains PIC
objects, and can be linked where a list of PIC objects makes sense;
i.e. into a shared library.  A static convenience library contains
non-PIC objects, so can be linked into an old static library, or
a program.
</p>
<p>When GNU Automake is used, you should use <code>noinst_LTLIBRARIES</code>
instead of <code>lib_LTLIBRARIES</code> for convenience libraries, so that
the <samp>-rpath</samp> option is not passed when they are linked.
</p>
<p>As a rule of thumb, link a libtool convenience library into at most one
libtool library, and never into a program, and link libtool static
convenience libraries only into programs, and only if you need to carry
library dependency information to the user of the static convenience
library.
</p>
<span id="index-standalone-binaries"></span>
<p>Another common situation where static linking is desirable is in
creating a standalone binary.  Use libtool to do the linking and add the
<samp>-all-static</samp> flag.
</p>
<hr>
<span id="Invoking-libtool"></span><div class="header">
<p>
Next: <a href="#Integrating-libtool" accesskey="n" rel="next">Integrating libtool</a>, Previous: <a href="#Using-libtool" accesskey="p" rel="prev">Using libtool</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Invoking-libtool-1"></span><h2 class="chapter">4 Invoking <code>libtool</code></h2>
<span id="index-libtool"></span>
<span id="index-libtool-command-options"></span>
<span id="index-options_002c-libtool-command"></span>
<span id="index-command-options_002c-libtool"></span>

<p>The <code>libtool</code> program has the following synopsis:
</p>
<div class="example">
<pre class="example">libtool [<var>option</var>]… [<var>mode-arg</var>]…
</pre></div>

<p>and accepts the following options:
</p>
<dl compact="compact">
<dt><samp>--config</samp></dt>
<dd><p>Display libtool configuration variables and exit.
</p>
</dd>
<dt><samp>--debug</samp></dt>
<dd><p>Dump a trace of shell script execution to standard output.  This
produces a lot of output, so you may wish to pipe it to <code>less</code> (or
<code>more</code>) or redirect to a file.
</p>
</dd>
<dt><samp>-n</samp></dt>
<dt><samp>--dry-run</samp></dt>
<dd><p>Don’t create, modify, or delete any files, just show what commands would
be executed by libtool.
</p>
</dd>
<dt><samp>--features</samp></dt>
<dd><p>Display basic configuration options.  This provides a way for packages
to determine whether shared or static libraries will be built.
</p>
</dd>
<dt><samp>--finish</samp></dt>
<dd><p>Same as <samp>--mode=finish</samp>.
</p>
</dd>
<dt><samp>-h</samp></dt>
<dd><p>Display short help message.
</p>
</dd>
<dt><samp>--help</samp></dt>
<dd><p>Display a help message and exit.  If <samp>--mode=<var>mode</var></samp> is
specified, then detailed help for <var>mode</var> is displayed.
</p>
</dd>
<dt><samp>--help-all</samp></dt>
<dd><p>Display help for the general options as well as detailed help for each
operation mode, and exit.
</p>
</dd>
<dt><samp>--mode=<var>mode</var></samp></dt>
<dd><p>Use <var>mode</var> as the operation mode.  When using libtool from the
command line, you can give just <var>mode</var> (or a unique abbreviation
of it) as the first argument as a shorthand for the full
<samp>--mode=<var>mode</var></samp>.  For example, the following are equivalent:
</p>
<div class="example">
<pre class="example">$ <kbd>libtool --mode=execute --dry-run gdb prog.exe</kbd>
$ <kbd>libtool        execute --dry-run gdb prog.exe</kbd>
$ <kbd>libtool        exe     --dry-run gdb prog.exe</kbd>
$ <kbd>libtool        e       --dry-run gdb prog.exe</kbd>
</pre></div>

<p><var>mode</var> must be set to one of the following:
</p>
<dl compact="compact">
<dt><samp>compile</samp></dt>
<dd><p>Compile a source file into a libtool object.
</p>
</dd>
<dt><samp>execute</samp></dt>
<dd><p>Automatically set the library path so that another program can use
uninstalled libtool-generated programs or libraries.
</p>
</dd>
<dt><samp>link</samp></dt>
<dd><p>Create a library or an executable.
</p>
</dd>
<dt><samp>install</samp></dt>
<dd><p>Install libraries or executables.
</p>
</dd>
<dt><samp>finish</samp></dt>
<dd><p>Complete the installation of libtool libraries on the system.
</p>
</dd>
<dt><samp>uninstall</samp></dt>
<dd><p>Delete installed libraries or executables.
</p>
</dd>
<dt><samp>clean</samp></dt>
<dd><p>Delete uninstalled libraries or executables.
</p></dd>
</dl>

</dd>
<dt><samp>--tag=<var>tag</var></samp></dt>
<dd><p>Use configuration variables from tag <var>tag</var> (see <a href="#Tags">Tags</a>).
</p>
</dd>
<dt><samp>--preserve-dup-deps</samp></dt>
<dd><p>Do not remove duplicate dependencies in libraries.  When building packages
with static libraries, the libraries may depend circularly on each other
(shared libs can too, but for those it doesn’t matter), so there are
situations, where -la -lb -la is required, and the second -la may not be
stripped or the link will fail.  In cases where these duplications are
required, this option will preserve them, only stripping the libraries
that libtool knows it can safely.
</p>
</dd>
<dt><samp>--quiet</samp></dt>
<dt><samp>--silent</samp></dt>
<dd><p>Do not print out any progress or informational messages.
</p>
</dd>
<dt><samp>-v</samp></dt>
<dt><samp>--verbose</samp></dt>
<dd><p>Print out progress and informational messages (enabled by default),
as well as additional messages not ordinary seen by default.
</p>
</dd>
<dt><samp>--no-quiet</samp></dt>
<dt><samp>--no-silent</samp></dt>
<dd><p>Print out the progress and informational messages that are seen
by default. This option has no effect on whether the additional
messages seen in <samp>--verbose</samp> mode are shown.
</p>
</dd>
<dt><samp>--no-verbose</samp></dt>
<dd><p>Do not print out any additional informational messages beyond
those ordinarily seen by default. This option has no effect
on whether the ordinary progress and informational messages
enabled by <samp>--no-quiet</samp> are shown.
</p>
<p>Thus, there are now three different message levels (not counting
<samp>--debug</samp>), depending on whether the normal messages and/or
the additional verbose messages are displayed.  Note that there is
no mechanism to display verbose messages, without also displaying
normal messages.
</p>
<dl compact="compact">
<dt><strong>default</strong></dt>
<dd><p>Normal messages are displayed, verbose messages are not displayed.
In addition to being the default mode, it can be forcibly achieved
by using both option <samp>--no-verbose</samp> and either option
<samp>--no-silent</samp> or option <samp>--no-quiet</samp>.
</p>
</dd>
<dt><strong>silent</strong></dt>
<dd><p>Neither normal messages nor verbose messages are displayed. This
mode can be achieved using either option <samp>--silent</samp> or
option <samp>--quiet</samp>.
</p>
</dd>
<dt><strong>verbose</strong></dt>
<dd><p>Both normal messages and verbose messages are displayed. This mode
can be achieved using either option <samp>-v</samp> or option
<samp>--verbose</samp>.
</p></dd>
</dl>

</dd>
<dt><samp>--version</samp></dt>
<dd><p>Print libtool version information and exit.
</p></dd>
</dl>

<p>The current <code>libtool</code> implementation is done with a shell script
that needs to be invoked by the shell that <code>configure</code> chose for
configuring <code>libtool</code> (see <a href="https://www.gnu.org/software/autoconf/manual/autoconf.html#config_002estatus-Invocation">The
Autoconf Manual</a> in <cite>The Autoconf Manual</cite>).  This shell is set in
the she-bang (‘<samp>#!</samp>’) line of the <code>libtool</code> script.  Using a
different shell may cause undefined behavior.
</p>
<p>The <var>mode-args</var> are a variable number of arguments, depending on the
selected operation mode.  In general, each <var>mode-arg</var> is interpreted
by programs libtool invokes, rather than libtool itself.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Compile-mode" accesskey="1">Compile mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating library object files.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Link-mode" accesskey="2">Link mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Generating executables and libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Execute-mode" accesskey="3">Execute mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Debugging libtool-generated programs.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Install-mode" accesskey="4">Install mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Making libraries and executables public.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Finish-mode" accesskey="5">Finish mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Completing a library installation.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Uninstall-mode" accesskey="6">Uninstall mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Removing installed executables and libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Clean-mode" accesskey="7">Clean mode</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Removing uninstalled executables and libraries.
</td></tr>
</tbody></table>

<hr>
<span id="Compile-mode"></span><div class="header">
<p>
Next: <a href="#Link-mode" accesskey="n" rel="next">Link mode</a>, Up: <a href="#Invoking-libtool" accesskey="u" rel="up">Invoking libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Compile-mode-1"></span><h3 class="section">4.1 Compile mode</h3>
<span id="index-mode_002c-compile"></span>
<span id="index-compile-mode"></span>

<p>For <em>compile</em> mode, <var>mode-args</var> is a compiler command to be used
in creating a “standard” object file.  These arguments should begin with
the name of the C compiler, and contain the <samp>-c</samp> compiler flag so
that only an object file is created.
</p>
<p>Libtool determines the name of the output file by removing the directory
component from the source file name, then substituting the source code
suffix (e.g. ‘<samp>.c</samp>’ for C source code) with the library object suffix,
‘<samp>.lo</samp>’.
</p>
<p>If shared libraries are being built, any necessary PIC generation flags
are substituted into the compilation command.
</p>
<p>The following components of <var>mode-args</var> are treated specially:
</p>
<dl compact="compact">
<dt><samp>-o</samp></dt>
<dd><p>Note that the <samp>-o</samp> option is now fully supported.  It is emulated
on the platforms that don’t support it (by locking and moving the
objects), so it is really easy to use libtool, just with minor
modifications to your Makefiles.  Typing for example
</p><div class="example">
<pre class="example">libtool --mode=compile gcc -c foo/x.c -o foo/x.lo
</pre></div>
<p>will do what you expect.
</p>
<p>Note, however, that, if the compiler does not support <samp>-c</samp> and
<samp>-o</samp>, it is impossible to compile <samp>foo/x.c</samp> without
overwriting an existing <samp>./x.o</samp>.  Therefore, if you do have a
source file <samp>./x.c</samp>, make sure you introduce dependencies in your
<samp>Makefile</samp> to make sure <samp>./x.o</samp> (or <samp>./x.lo</samp>) is
re-created after any sub-directory’s <samp>x.lo</samp>:
</p>
<div class="example">
<pre class="example">x.o x.lo: foo/x.lo bar/x.lo
</pre></div>

<p>This will also ensure that make won’t try to use a temporarily corrupted
<samp>x.o</samp> to create a program or library.  It may cause needless
recompilation on platforms that support <samp>-c</samp> and <samp>-o</samp>
together, but it’s the only way to make it safe for those that don’t.
</p>
</dd>
<dt><samp>-no-suppress</samp></dt>
<dd><p>If both PIC and non-PIC objects are being built, libtool will normally
suppress the compiler output for the PIC object compilation to save
showing very similar, if not identical duplicate output for each
object.  If the <samp>-no-suppress</samp> option is given in compile mode,
libtool will show the compiler output for both objects.
</p>
</dd>
<dt><samp>-prefer-pic</samp></dt>
<dd><p>Libtool will try to build only PIC objects.
</p>
</dd>
<dt><samp>-prefer-non-pic</samp></dt>
<dd><p>Libtool will try to build only non-PIC objects.
</p>
</dd>
<dt><samp>-shared</samp></dt>
<dd><p>Even if Libtool was configured with <samp>--enable-static</samp>, the object
file Libtool builds will not be suitable for static linking.  Libtool
will signal an error if it was configured with <samp>--disable-shared</samp>,
or if the host does not support shared libraries.
</p>
</dd>
<dt><samp>-static</samp></dt>
<dd><p>Even if libtool was configured with <samp>--disable-static</samp>, the
object file Libtool builds <strong>will</strong> be suitable for static
linking.
</p>
</dd>
<dt><samp>-Wc,<var>flag</var></samp></dt>
<dt><samp>-Xcompiler <var>flag</var></samp></dt>
<dd><p>Pass a flag directly to the compiler.  With <code>-Wc,</code>, multiple flags
may be separated by commas, whereas <code>-Xcompiler </code> passes through
commas unchanged.
</p></dd>
</dl>

<hr>
<span id="Link-mode"></span><div class="header">
<p>
Next: <a href="#Execute-mode" accesskey="n" rel="next">Execute mode</a>, Previous: <a href="#Compile-mode" accesskey="p" rel="prev">Compile mode</a>, Up: <a href="#Invoking-libtool" accesskey="u" rel="up">Invoking libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Link-mode-1"></span><h3 class="section">4.2 Link mode</h3>
<span id="index-link-mode"></span>
<span id="index-mode_002c-link"></span>

<p><em>Link</em> mode links together object files (including library
objects) to form another library or to create an executable program.
</p>
<p><var>mode-args</var> consist of a command using the C compiler to create an
output file (with the <samp>-o</samp> flag) from several object files.
</p>
<p>The following components of <var>mode-args</var> are treated specially:
</p>
<dl compact="compact">
<dd><span id="index-undefined-symbols_002c-allowing"></span>
<span id="index-unresolved-symbols_002c-allowing"></span>
</dd>
<dt><samp>-all-static</samp></dt>
<dd><p>If <var>output-file</var> is a program, then do not link it against any
shared libraries at all.  If <var>output-file</var> is a library, then only
create a static library.  In general, this flag cannot be used together
with ‘<samp>disable-static</samp>’ (see <a href="#LT_005fINIT">LT_INIT</a>).
</p>
</dd>
<dt><samp>-avoid-version</samp></dt>
<dd><p>Tries to avoid versioning (see <a href="#Versioning">Versioning</a>) for libraries and modules,
i.e. no version information is stored and no symbolic links are created.
If the platform requires versioning, this option has no effect.
</p>
</dd>
<dt><samp>-bindir</samp></dt>
<dd><p>Pass the absolute name of the directory for installing executable
programs (see <a href="https://www.gnu.org/prep/standards/standards.html#Directory-Variables">Directory Variables</a> in <cite>The GNU Coding Standards</cite>).  <code>libtool</code> may use this value to
install shared libraries there on systems that do not provide for any
library hardcoding and use the directory of a program and the <code>PATH</code>
variable as library search path.  This is typically used for DLLs on
Windows or other systems using the PE (Portable Executable) format.
On other systems, <samp>-bindir</samp> is ignored.  The default value used
is <samp><var>libdir</var>/../bin</samp> for libraries installed to
<samp><var>libdir</var></samp>.  You should not use <samp>-bindir</samp> for modules.
</p>
</dd>
<dt><samp>-dlopen <var>file</var></samp></dt>
<dd><p>Same as <samp>-dlpreopen <var>file</var></samp>, if native dlopening is not
supported on the host platform (see <a href="#Dlopened-modules">Dlopened modules</a>) or if
the program is linked with <samp>-static</samp>,
<samp>-static-libtool-libs</samp>, or <samp>-all-static</samp>.  Otherwise, no
effect.  If <var>file</var> is <code>self</code> Libtool will make sure that the
program can <code>dlopen</code> itself, either by enabling
<samp>-export-dynamic</samp> or by falling back to <samp>-dlpreopen self</samp>.
</p>
</dd>
<dt><samp>-dlpreopen <var>file</var></samp></dt>
<dd><p>Link <var>file</var> into the output program, and add its symbols to the
list of preloaded symbols (see <a href="#Dlpreopening">Dlpreopening</a>).  If <var>file</var> is
<code>self</code>, the symbols of the program itself will be added to
preloaded symbol lists.  If <var>file</var> is <code>force</code> Libtool will
make sure that a preloaded symbol list is always <em>defined</em>,
regardless of whether it’s empty or not.
</p>
</dd>
<dt><samp>-export-dynamic</samp></dt>
<dd><p>Allow symbols from <var>output-file</var> to be resolved with <code>dlsym</code>
(see <a href="#Dlopened-modules">Dlopened modules</a>).
</p>
</dd>
<dt><samp>-export-symbols <var>symfile</var></samp></dt>
<dd><p>Tells the linker to export only the symbols listed in <var>symfile</var>.
The symbol file should end in <samp>.sym</samp> and must contain the name of one
symbol per line.  This option has no effect on some platforms.
By default all symbols are exported.
</p>
</dd>
<dt><samp>-export-symbols-regex <var>regex</var></samp></dt>
<dd><p>Same as <samp>-export-symbols</samp>, except that only symbols matching
the regular expression <var>regex</var> are exported.
By default all symbols are exported.
</p>
</dd>
<dt><samp>-L<var>libdir</var></samp></dt>
<dd><p>Search <var>libdir</var> for required libraries that have already been
installed.
</p>
</dd>
<dt><samp>-l<var>name</var></samp></dt>
<dd><p><var>output-file</var> requires the installed library <samp>lib<var>name</var></samp>.
This option is required even when <var>output-file</var> is not an
executable.
</p>
</dd>
<dt><samp>-module</samp></dt>
<dd><p>Creates a library that can be dlopened (see <a href="#Dlopened-modules">Dlopened modules</a>).
This option doesn’t work for programs.
Module names don’t need to be prefixed with ‘<samp>lib</samp>’.
In order to prevent name clashes, however, <samp>lib<var>name</var></samp> and <samp><var>name</var></samp>
must not be used at the same time in your package.
</p>
</dd>
<dt><samp>-no-fast-install</samp></dt>
<dd><p>Disable fast-install mode for the executable <var>output-file</var>.  Useful
if the program won’t be necessarily installed.
</p>
</dd>
<dt><samp>-no-install</samp></dt>
<dd><p>Link an executable <var>output-file</var> that can’t be installed and
therefore doesn’t need a wrapper script on systems that allow hardcoding
of library paths.  Useful if the program is only used in the build tree,
e.g., for testing or generating other files.
</p>
</dd>
<dt><samp>-no-undefined</samp></dt>
<dd><p>Declare that <var>output-file</var> does not depend on any libraries other
than the ones listed on the command line, i.e., after linking, it will
not have unresolved symbols.  Some platforms require all symbols in
shared libraries to be resolved at library creation (see <a href="#Inter_002dlibrary-dependencies">Inter-library dependencies</a>), and using this parameter allows <code>libtool</code> to
assume that this will not happen.
</p>
</dd>
<dt><samp>-o <var>output-file</var></samp></dt>
<dd><p>Create <var>output-file</var> from the specified objects and libraries.
</p>
</dd>
<dt><samp>-objectlist <var>file</var></samp></dt>
<dd><p>Use a list of object files found in <var>file</var> to specify objects.
</p>
</dd>
<dt><samp>-os2dllname <var>name</var></samp></dt>
<dd><p>Use this to change the DLL base name on OS/2 to <var>name</var>, to keep
within the 8 character base name limit on this system.
</p>
</dd>
<dt><samp>-precious-files-regex <var>regex</var></samp></dt>
<dd><p>Prevents removal of files from the temporary output directory whose
names match this regular expression.  You might specify ‘<samp>\.bbg?$</samp>’
to keep those files created with <code>gcc -ftest-coverage</code> for example.
</p>
</dd>
<dt><samp>-release <var>release</var></samp></dt>
<dd><p>Specify that the library was generated by release <var>release</var> of your
package, so that users can easily tell what versions are newer than
others.  Be warned that no two releases of your package will be binary
compatible if you use this flag.  If you want binary compatibility, use
the <samp>-version-info</samp> flag instead (see <a href="#Versioning">Versioning</a>).
</p>
</dd>
<dt><samp>-rpath <var>libdir</var></samp></dt>
<dd><p>If <var>output-file</var> is a library, it will eventually be installed in
<var>libdir</var>.  If <var>output-file</var> is a program, add <var>libdir</var> to
the run-time path of the program.  On platforms that don’t support
hardcoding library paths into executables and only search PATH for
shared libraries, such as when <var>output-file</var> is a Windows (or
other PE platform) DLL, the <samp>.la</samp> control file will be installed in
<var>libdir</var>, but see <samp>-bindir</samp> above for the eventual destination
of the <samp>.dll</samp> or other library file itself.
</p>
</dd>
<dt><samp>-R <var>libdir</var></samp></dt>
<dd><p>If <var>output-file</var> is a program, add <var>libdir</var> to its run-time
path.  If <var>output-file</var> is a library, add <samp>-R<var>libdir</var></samp> to its
<var>dependency_libs</var>, so that, whenever the library is linked into a
program, <var>libdir</var> will be added to its run-time path.
</p>
</dd>
<dt><samp>-shared</samp></dt>
<dd><p>If <var>output-file</var> is a program, then link it against any
uninstalled shared libtool libraries (this is the default behavior).
If <var>output-file</var> is a library, then only create a shared library.
In the later case, libtool will signal an error if it was configured
with <samp>--disable-shared</samp>, or if the host does not support shared
libraries.
</p>
</dd>
<dt><samp>-shrext <var>suffix</var></samp></dt>
<dd><p>If <var>output-file</var> is a libtool library, replace the system’s standard
file name extension for shared libraries with <var>suffix</var> (most systems
use <samp>.so</samp> here).  This option is helpful in certain cases where an
application requires that shared libraries (typically modules) have an
extension other than the default one.  Please note you must supply the
full file name extension including any leading dot.
</p>
</dd>
<dt><samp>-static</samp></dt>
<dd><p>If <var>output-file</var> is a program, then do not link it against any
uninstalled shared libtool libraries.  If <var>output-file</var> is a
library, then only create a static library.
</p>
</dd>
<dt><samp>-static-libtool-libs</samp></dt>
<dd><p>If <var>output-file</var> is a program, then do not link it against any
shared libtool libraries.  If <var>output-file</var> is a library, then only
create a static library.
</p>
</dd>
<dt><samp>-version-info <var>current</var>[:<var>revision</var>[:<var>age</var>]]</samp></dt>
<dd><p>If <var>output-file</var> is a libtool library, use interface version
information <var>current</var>, <var>revision</var>, and <var>age</var> to build it
(see <a href="#Versioning">Versioning</a>).  Do <strong>not</strong> use this flag to specify package
release information, rather see the <samp>-release</samp> flag.
</p>
</dd>
<dt><samp>-version-number <var>major</var>[:<var>minor</var>[:<var>revision</var>]]</samp></dt>
<dd><p>If <var>output-file</var> is a libtool library, compute interface version
information so that the resulting library uses the specified major, minor and
revision numbers.  This is designed to permit libtool to be used with
existing projects where identical version numbers are already used across
operating systems.  New projects should use the <samp>-version-info</samp> flag
instead.
</p>
</dd>
<dt><samp>-weak <var>libname</var></samp></dt>
<dd><p>if <var>output-file</var> is a libtool library, declare that it provides a
weak <var>libname</var> interface.  This is a hint to libtool that there is
no need to append <var>libname</var> to the list of dependency libraries of
<var>output-file</var>, because linking against <var>output-file</var> already
supplies the same interface (see <a href="#Linking-with-dlopened-modules">Linking with dlopened modules</a>).
</p>
</dd>
<dt><samp>-Wc,<var>flag</var></samp></dt>
<dt><samp>-Xcompiler <var>flag</var></samp></dt>
<dd><p>Pass a linker-specific flag directly to the compiler.  With <code>-Wc,</code>,
multiple flags may be separated by commas, whereas <code>-Xcompiler </code>
passes through commas unchanged.
</p>
</dd>
<dt><samp>-Wa,<var>flag</var></samp></dt>
<dt><samp>-Xassembler <var>flag</var></samp></dt>
<dd><p>Pass a linker-specific flag directly to the assembler.  With <code>-Wa,</code>,
multiple flags may be separated by commas, whereas <code>-Xassembler </code>
passes through commas unchanged.
</p>
</dd>
<dt><samp>-Wl,<var>flag</var></samp></dt>
<dt><samp>-Xlinker <var>flag</var></samp></dt>
<dd><p>Pass a linker-specific flag directly to the linker.
</p>
</dd>
<dt><samp>-XCClinker <var>flag</var></samp></dt>
<dd><p>Pass a link-specific flag to the compiler driver (<code>CC</code>) during linking.
</p></dd>
</dl>

<p>If the <var>output-file</var> ends in <samp>.la</samp>, then a libtool library is
created, which must be built only from library objects (<samp>.lo</samp> files).
The <samp>-rpath</samp> option is required.  In the current implementation,
libtool libraries may not depend on other uninstalled libtool libraries
(see <a href="#Inter_002dlibrary-dependencies">Inter-library dependencies</a>).
</p>
<p>If the <var>output-file</var> ends in <samp>.a</samp>, then a standard library is
created using <code>ar</code> and possibly <code>ranlib</code>.
</p>
<span id="index-partial-linking"></span>
<span id="index-linking_002c-partial"></span>
<p>If <var>output-file</var> ends in <samp>.o</samp> or <samp>.lo</samp>, then a reloadable object
file is created from the input files (generally using ‘<samp>ld -r</samp>’).
This method is often called <em>partial linking</em>.
</p>
<p>Otherwise, an executable program is created.
</p>
<hr>
<span id="Execute-mode"></span><div class="header">
<p>
Next: <a href="#Install-mode" accesskey="n" rel="next">Install mode</a>, Previous: <a href="#Link-mode" accesskey="p" rel="prev">Link mode</a>, Up: <a href="#Invoking-libtool" accesskey="u" rel="up">Invoking libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Execute-mode-1"></span><h3 class="section">4.3 Execute mode</h3>
<span id="index-execute-mode"></span>
<span id="index-mode_002c-execute"></span>

<p>For <em>execute</em> mode, the library path is automatically set, then a
program is executed.
</p>
<p>The first of the <var>mode-args</var> is treated as a program name, with the
rest as arguments to that program.
</p>
<p>The following components of <var>mode-args</var> are treated specially:
</p>
<dl compact="compact">
<dt><samp>-dlopen <var>file</var></samp></dt>
<dd><p>Add the directory containing <var>file</var> to the library path.
</p></dd>
</dl>

<p>This mode sets the library path environment variable according to any
<samp>-dlopen</samp> flags.
</p>
<p>If any of the <var>args</var> are libtool executable wrappers, then they are
translated into the name of their corresponding uninstalled binary, and
any of their required library directories are added to the library path.
</p>
<hr>
<span id="Install-mode"></span><div class="header">
<p>
Next: <a href="#Finish-mode" accesskey="n" rel="next">Finish mode</a>, Previous: <a href="#Execute-mode" accesskey="p" rel="prev">Execute mode</a>, Up: <a href="#Invoking-libtool" accesskey="u" rel="up">Invoking libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Install-mode-1"></span><h3 class="section">4.4 Install mode</h3>
<span id="index-install-mode"></span>
<span id="index-mode_002c-install"></span>

<p>In <em>install</em> mode, libtool interprets most of the elements of
<var>mode-args</var> as an installation command beginning with
<code>cp</code>, or a BSD-compatible <code>install</code> program.
</p>
<p>The following components of <var>mode-args</var> are treated specially:
</p>
<dl compact="compact">
<dt><samp>-inst-prefix-dir <var>inst-prefix-dir</var></samp></dt>
<dd><p>When installing into a temporary staging area, rather than the
final <code>prefix</code>, this argument is used to reflect the
temporary path, in much the same way <code>automake</code> uses
<code>DESTDIR</code>.  For instance, if <code>prefix</code> is <samp>/usr/local</samp>,
but <var>inst-prefix-dir</var> is <samp>/tmp</samp>, then the object will be
installed under <samp>/tmp/usr/local/</samp>.  If the installed object
is a libtool library, then the internal fields of that library
will reflect only <code>prefix</code>, not <var>inst-prefix-dir</var>:
</p>
<div class="example">
<pre class="example"># Directory that this library needs to be installed in:
libdir='/usr/local/lib'
</pre></div>

<p>not
</p>
<div class="example">
<pre class="example"># Directory that this library needs to be installed in:
libdir='/tmp/usr/local/lib'
</pre></div>

<p><code>inst-prefix</code> is also used to ensure that if the installed
object must be relinked upon installation, that it is relinked
against the libraries in <var>inst-prefix-dir</var>/<code>prefix</code>,
not <code>prefix</code>.
</p>
<p>In truth, this option is not really intended for use when calling
libtool directly; it is automatically used when <code>libtool --mode=install</code>
calls <code>libtool --mode=relink</code>.  Libtool does this by
analyzing the destination path given in the original
<code>libtool --mode=install</code> command and comparing it to the
expected installation path established during <code>libtool --mode=link</code>.
</p>
<p>Thus, end-users need change nothing, and <code>automake</code>-style
<code>make install DESTDIR=/tmp</code> will Just Work(tm) most of the time.
For systems where fast installation cannot be turned on, relinking
may be needed.  In this case, a ‘<samp>DESTDIR</samp>’ install will fail.
</p>
<p>Currently it is not generally possible to install into a temporary
staging area that contains needed third-party libraries that are
not yet visible at their final location.
</p></dd>
</dl>

<p>The rest of the <var>mode-args</var> are interpreted as arguments to the
<code>cp</code> or <code>install</code> command.
</p>
<p>The command is run, and any necessary unprivileged post-installation
commands are also completed.
</p>
<hr>
<span id="Finish-mode"></span><div class="header">
<p>
Next: <a href="#Uninstall-mode" accesskey="n" rel="next">Uninstall mode</a>, Previous: <a href="#Install-mode" accesskey="p" rel="prev">Install mode</a>, Up: <a href="#Invoking-libtool" accesskey="u" rel="up">Invoking libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Finish-mode-1"></span><h3 class="section">4.5 Finish mode</h3>
<span id="index-finish-mode"></span>
<span id="index-mode_002c-finish"></span>

<p><em>Finish</em> mode has two functions.  One is to help system administrators
install libtool libraries so that they can be located and linked into
user programs.  To invoke this functionality, pass the name of a library
directory as <var>mode-arg</var>.  Running this command may require superuser
privileges, and the <samp>--dry-run</samp> option may be useful.
</p>
<p>The second is to facilitate transferring libtool libraries to a native
compilation environment after they were built in a cross-compilation
environment.  Cross-compilation environments may rely on recent libtool
features, and running libtool in finish mode will make it easier to
work with older versions of libtool.  This task is performed whenever
the <var>mode-arg</var> is a <samp>.la</samp> file.
</p>
<hr>
<span id="Uninstall-mode"></span><div class="header">
<p>
Next: <a href="#Clean-mode" accesskey="n" rel="next">Clean mode</a>, Previous: <a href="#Finish-mode" accesskey="p" rel="prev">Finish mode</a>, Up: <a href="#Invoking-libtool" accesskey="u" rel="up">Invoking libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Uninstall-mode-1"></span><h3 class="section">4.6 Uninstall mode</h3>
<span id="index-uninstall-mode"></span>
<span id="index-mode_002c-uninstall"></span>

<p><em>Uninstall</em> mode deletes installed libraries, executables and objects.
</p>
<p>The first <var>mode-arg</var> is the name of the program to use to delete
files (typically <code>/bin/rm</code>).
</p>
<p>The remaining <var>mode-args</var> are either flags for the deletion program
(beginning with a ‘<samp>-</samp>’), or the names of files to delete.
</p>
<hr>
<span id="Clean-mode"></span><div class="header">
<p>
Previous: <a href="#Uninstall-mode" accesskey="p" rel="prev">Uninstall mode</a>, Up: <a href="#Invoking-libtool" accesskey="u" rel="up">Invoking libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Clean-mode-1"></span><h3 class="section">4.7 Clean mode</h3>
<span id="index-clean-mode"></span>
<span id="index-mode_002c-clean"></span>

<p><em>Clean</em> mode deletes uninstalled libraries, executables, objects
and libtool’s temporary files associated with them.
</p>
<p>The first <var>mode-arg</var> is the name of the program to use to delete
files (typically <code>/bin/rm</code>).
</p>
<p>The remaining <var>mode-args</var> are either flags for the deletion program
(beginning with a ‘<samp>-</samp>’), or the names of files to delete.
</p>
<hr>
<span id="Integrating-libtool"></span><div class="header">
<p>
Next: <a href="#Other-languages" accesskey="n" rel="next">Other languages</a>, Previous: <a href="#Invoking-libtool" accesskey="p" rel="prev">Invoking libtool</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Integrating-libtool-with-your-package"></span><h2 class="chapter">5 Integrating libtool with your package</h2>

<p>This chapter describes how to integrate libtool with your packages so
that your users can install hassle-free shared libraries.
</p>
<p>There are several ways that Libtool may be integrated in your
package, described in the following sections.  Typically, the Libtool
macro files as well as <samp>ltmain.sh</samp> are copied into your package
using <code>libtoolize</code> and <code>aclocal</code> after setting up the
<samp>configure.ac</samp> and toplevel <samp>Makefile.am</samp>, then
<code>autoconf</code> adds the needed tests to the <samp>configure</samp> script.
These individual steps are often automated with <code>autoreconf</code>.
</p>
<p>Here is a diagram showing how such a typical Libtool configuration works
when preparing a package for distribution, assuming that <samp>m4</samp> has
been chosen as location for additional Autoconf macros, and
<samp>build-aux</samp> as location for auxiliary build tools (see <a href="https://www.gnu.org/software/autoconf/manual/autoconf.html#Input">The Autoconf Manual</a> in <cite>The Autoconf Manual</cite>):
</p>
<div class="example">
<pre class="example">libtool.m4 -----.                .--&gt; aclocal.m4 -----.
ltoptions.m4 ---+  .-&gt; aclocal* -+                    +--&gt; autoconf*
ltversion.m4 ---+--+             `--&gt; [copy in m4/] --+       |
ltsugar.m4 -----+  |                    ^             |       \/
lt~obsolete.m4 -+  +-&gt; libtoolize* -----'             |    configure
[ltdl.m4] ------+  |                                  |
                   `----------------------------------'

ltmain.sh -----------&gt; libtoolize* -&gt; [copy in build-aux/]
</pre></div>

<p>During configuration, the <samp>libtool</samp> script is generated either
through <code>config.status</code> or <code>config.lt</code>:
</p>
<div class="example">
<pre class="example">             .--&gt; config.status* --.
configure* --+                     +--&gt; libtool
             `--&gt; [config.lt*] ----'      ^
                                          |
ltmain.sh --------------------------------'
</pre></div>

<p>At <code>make</code> run time, <code>libtool</code> is then invoked as needed
as a wrapper around compilers, linkers, install and cleanup programs.
</p>
<p>There are alternatives choices to several parts of the setup; for
example, the Libtool macro files can either be copied or symlinked into
the package, or copied into <samp>aclocal.m4</samp>.  As another example, an
external, pre-configured <code>libtool</code> script may be used,
by-passing most of the tests and package-specific setup for Libtool.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Autoconf-macros" accesskey="1">Autoconf macros</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Autoconf macros exported by libtool.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Makefile-rules" accesskey="2">Makefile rules</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Writing <samp>Makefile</samp> rules for libtool.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Using-Automake" accesskey="3">Using Automake</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Automatically supporting libtool.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Configuring" accesskey="4">Configuring</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Configuring libtool for a host system.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Distributing" accesskey="5">Distributing</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">What files to distribute with your package.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Static_002donly-libraries" accesskey="6">Static-only libraries</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Sometimes shared libraries are just a pain.
</td></tr>
</tbody></table>

<hr>
<span id="Autoconf-macros"></span><div class="header">
<p>
Next: <a href="#Makefile-rules" accesskey="n" rel="next">Makefile rules</a>, Up: <a href="#Integrating-libtool" accesskey="u" rel="up">Integrating libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Autoconf-macros-exported-by-libtool"></span><h3 class="section">5.1 Autoconf macros exported by libtool</h3>

<p>Libtool uses a number of macros to interrogate the host system when it
is being built, and you can use some of them yourself too.  Although
there are a great many other macros in the libtool installed m4 files,
these do not form part of the published interface, and are subject to
change between releases.
</p>
<p>Macros in the ‘<samp>LT_CMD_</samp>’ namespace check for various shell
commands:
</p>
<dl>
<dt id="index-LT_005fCMD_005fMAX_005fLEN">Macro: <strong>LT_CMD_MAX_LEN</strong></dt>
<dd><p>Finds the longest command line that can be safely passed to
‘<samp>$SHELL</samp>’ without being truncated, and store in the shell variable
‘<samp>$max_cmd_len</samp>’.  It is only an approximate value, but command
lines of this length or shorter are guaranteed not to be truncated.
</p></dd></dl>

<p>Macros in the ‘<samp>LT_FUNC_</samp>’ namespace check characteristics of
library functions:
</p>
<dl>
<dt id="index-LT_005fFUNC_005fDLSYM_005fUSCORE">Macro: <strong>LT_FUNC_DLSYM_USCORE</strong></dt>
<dd><p>‘<samp>AC_DEFINE</samp>’ the preprocessor symbol ‘<samp>DLSYM_USCORE</samp>’ if we
have to add an underscore to symbol-names passed in to ‘<samp>dlsym</samp>’.
</p></dd></dl>

<p>Macros in the ‘<samp>LT_LIB_</samp>’ namespace check characteristics of system
libraries:
</p>
<dl>
<dt id="index-LT_005fLIB_005fM">Macro: <strong>LT_LIB_M</strong></dt>
<dd><p>Set ‘<samp>LIBM</samp>’ to the math library or libraries required on this
machine, if any.
</p></dd></dl>

<dl>
<dt id="index-LT_005fLIB_005fDLLOAD">Macro: <strong>LT_LIB_DLLOAD</strong></dt>
<dd><p>This is the macro used by ‘<samp>libltdl</samp>’ to determine what dlloaders
to use on this machine, if any.  Several shell variables are set (and
‘<samp>AC_SUBST</samp>’ed) depending on the dlload interfaces are available on
this machine.  ‘<samp>LT_DLLOADERS</samp>’ contains a list of libtool
libraries that can be used, and if necessary also sets
‘<samp>LIBADD_DLOPEN</samp>’ if additional system libraries are required by
the ‘<samp>dlopen</samp>’ loader, and ‘<samp>LIBADD_SHL_LOAD</samp>’ if additional
system libraries are required by the ‘<samp>shl_load</samp>’ loader,
respectively.  Finally some symbols are set in <samp>config.h</samp>
depending on the loaders that are found to work: ‘<samp>HAVE_LIBDL</samp>’,
‘<samp>HAVE_SHL_LOAD</samp>’, ‘<samp>HAVE_DYLD</samp>’, ‘<samp>HAVE_DLD</samp>’.
</p></dd></dl>

<p>Macros in the ‘<samp>LT_PATH_</samp>’ namespace search the system for the full
path to particular system commands:
</p>
<dl>
<dt id="index-LT_005fPATH_005fLD">Macro: <strong>LT_PATH_LD</strong></dt>
<dd><p>Add a <samp>--with-gnu-ld</samp> option to <samp>configure</samp>.  Try to find
the path to the linker used by ‘<samp>$CC</samp>’, and whether it is the
GNU linker.  The result is stored in the shell variable
‘<samp>$LD</samp>’, which is <code>AC_SUBST</code>ed.
</p></dd></dl>

<dl>
<dt id="index-LT_005fPATH_005fNM">Macro: <strong>LT_PATH_NM</strong></dt>
<dd><p>Try to find a BSD-compatible <code>nm</code> or a MS-compatible
<code>dumpbin</code> command on this machine.  The result is stored in the
shell variable ‘<samp>$NM</samp>’, which is <code>AC_SUBST</code>ed.
</p></dd></dl>

<p>Macros in the ‘<samp>LT_SYS_</samp>’ namespace probe for system
characteristics:
</p>
<dl>
<dt id="index-LT_005fSYS_005fDLOPEN_005fSELF">Macro: <strong>LT_SYS_DLOPEN_SELF</strong></dt>
<dd><p>Tests whether a program can dlopen itself, and then also whether the
same program can still dlopen itself when statically linked.  Results
are stored in the shell variables ‘<samp>$enable_dlopen_self</samp>’ and
‘<samp>enable_dlopen_self_static</samp>’ respectively.
</p></dd></dl>

<dl>
<dt id="index-LT_005fSYS_005fDLOPEN_005fDEPLIBS">Macro: <strong>LT_SYS_DLOPEN_DEPLIBS</strong></dt>
<dd><p>Define the preprocessor symbol ‘<samp>LTDL_DLOPEN_DEPLIBS</samp>’ if the
OS needs help to load dependent libraries for ‘<samp>dlopen</samp>’ (or
equivalent).
</p></dd></dl>

<dl>
<dt id="index-LT_005fSYS_005fDLSEARCH_005fPATH">Macro: <strong>LT_SYS_DLSEARCH_PATH</strong></dt>
<dd><p>Define the preprocessor symbol ‘<samp>LT_DLSEARCH_PATH</samp>’ to the system
default library search path.
</p></dd></dl>

<dl>
<dt id="index-LT_005fSYS_005fMODULE_005fEXT">Macro: <strong>LT_SYS_MODULE_EXT</strong></dt>
<dd><p>Define the preprocessor symbol ‘<samp>LT_MODULE_EXT</samp>’ to the extension
used for runtime loadable modules.  If you use libltdl to open
modules, then you can simply use the libtool library extension,
<samp>.la</samp>.
</p></dd></dl>

<dl>
<dt id="index-LT_005fSYS_005fMODULE_005fPATH">Macro: <strong>LT_SYS_MODULE_PATH</strong></dt>
<dd><p>Define the preprocessor symbol ‘<samp>LT_MODULE_PATH_VAR</samp>’ to the name
of the shell environment variable that determines the run-time module
search path.
</p></dd></dl>

<dl>
<dt id="index-LT_005fSYS_005fSYMBOL_005fUSCORE">Macro: <strong>LT_SYS_SYMBOL_USCORE</strong></dt>
<dd><p>Set the shell variable ‘<samp>sys_symbol_underscore</samp>’ to ‘<samp>no</samp>’
unless the compiler prefixes global symbols with an underscore.
</p></dd></dl>


<hr>
<span id="Makefile-rules"></span><div class="header">
<p>
Next: <a href="#Using-Automake" accesskey="n" rel="next">Using Automake</a>, Previous: <a href="#Autoconf-macros" accesskey="p" rel="prev">Autoconf macros</a>, Up: <a href="#Integrating-libtool" accesskey="u" rel="up">Integrating libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Writing-Makefile-rules-for-libtool"></span><h3 class="section">5.2 Writing <samp>Makefile</samp> rules for libtool</h3>
<span id="index-Makefile"></span>
<span id="index-Makefile_002eam"></span>
<span id="index-Makefile_002ein"></span>

<p>Libtool is fully integrated with Automake (see <a href="https://www.gnu.org/software/automake/manual/automake.html#Top">Introduction</a> in <cite>The Automake Manual</cite>), starting with Automake version 1.2.
</p>
<p>If you want to use libtool in a regular <samp>Makefile</samp> (or
<samp>Makefile.in</samp>), you are on your own.  If you’re not using
Automake, and you don’t know how to incorporate libtool into your
package you need to do one of the following:
</p>
<ol>
<li> Download the latest Automake distribution from your nearest GNU
mirror, install it, and start using it.

</li><li> Learn how to write <samp>Makefile</samp> rules by hand.  They’re sometimes complex,
but if you’re clever enough to write rules for compiling your old
libraries, then you should be able to figure out new rules for libtool
libraries (hint: examine the <samp>Makefile.in</samp> in the <samp>tests/demo</samp>
subdirectory of the libtool distribution… note especially that it
was automatically generated from the <samp>Makefile.am</samp> by Automake).
</li></ol>

<hr>
<span id="Using-Automake"></span><div class="header">
<p>
Next: <a href="#Configuring" accesskey="n" rel="next">Configuring</a>, Previous: <a href="#Makefile-rules" accesskey="p" rel="prev">Makefile rules</a>, Up: <a href="#Integrating-libtool" accesskey="u" rel="up">Integrating libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Using-Automake-with-libtool"></span><h3 class="section">5.3 Using Automake with libtool</h3>

<span id="index-LTLIBRARIES"></span>
<p>Libtool library support is implemented under the ‘<samp>LTLIBRARIES</samp>’
primary.
</p>
<p>Here are some samples from the Automake <samp>Makefile.am</samp> in the
libtool distribution’s <samp>demo</samp> subdirectory.
</p>
<p>First, to link a program against a libtool library, just use the
‘<samp>program_LDADD</samp>’<a id="DOCF5" href="#FOOT5"><sup>5</sup></a> variable:
</p>
<div class="example">
<pre class="example">bin_PROGRAMS = hell hell_static

# Build hell from main.c and libhello.la
hell_SOURCES = main.c
hell_LDADD = libhello.la

# Create a statically linked version of hell.
hell_static_SOURCES = main.c
hell_static_LDADD = libhello.la
hell_static_LDFLAGS = -static
</pre></div>

<p>You may use the ‘<samp>program_LDFLAGS</samp>’ variable to stuff in any flags
you want to pass to libtool while linking <samp>program</samp> (such as
<samp>-static</samp> to avoid linking uninstalled shared libtool libraries).
</p>
<p>Building a libtool library is almost as trivial… note the use of
‘<samp>libhello_la_LDFLAGS</samp>’ to pass the <samp>-version-info</samp>
(see <a href="#Versioning">Versioning</a>) option to libtool:
</p>
<div class="example">
<pre class="example"># Build a libtool library, libhello.la for installation in libdir.
lib_LTLIBRARIES = libhello.la
libhello_la_SOURCES = hello.c foo.c
libhello_la_LDFLAGS = -version-info 3:12:1
</pre></div>

<p>The <samp>-rpath</samp> option is passed automatically by Automake (except for
libraries listed as <code>noinst_LTLIBRARIES</code>), so you
should not specify it.
</p>
<p>See <a href="https://www.gnu.org/software/automake/manual/automake.html#A-Shared-Library">The Automake Manual</a> in <cite>The Automake Manual</cite>, for more information.
</p>
<p>When building libtool archives which depend on built sources (for example a
generated header file), you may find it necessary to manually record
these dependencies.
Because libtool archives generate object file names manually recording these
dependencies is not as straightforward as the examples in Automake’s manual
describe in their examples.
This effects header files in particular, because simply listing them as
‘<samp>nodist_libfoo_la_SOURCES</samp>’ will not cause Automake to establish a
dependent relationship for the object files of <samp>libfoo.la</samp>.
A useful trick (although somewhat imprecise) is to manually record built
sources used by a libtool archive as dependencies of all the objects for that
library as shown below (as opposed to a particular object file):
</p>
<div class="example">
<pre class="example"># Build a libtool library, libhello.la which depends on a generated header.
hello.h:
	echo '#define HELLO_MESSAGE  "Hello, World!"' &gt; $@
BUILT_SOURCES = hello.h
CLEANFILES = hello.h
nodist_libhello_la_SOURCES = hello.h
libhello_la_SOURCES = hello.c foo.h foo.c bar.h bar.c
# Manually record hello.h as a prerequisite for all objects in libhello.la
$(libhello_la_OBJECTS): hello.h
</pre></div>

<p>See <a href="https://www.gnu.org/software/automake/manual/automake.html#Built-Sources-Example">The Automake Manual</a> in <cite>The Automake Manual</cite>, for more information.
</p>
<hr>
<span id="Configuring"></span><div class="header">
<p>
Next: <a href="#Distributing" accesskey="n" rel="next">Distributing</a>, Previous: <a href="#Using-Automake" accesskey="p" rel="prev">Using Automake</a>, Up: <a href="#Integrating-libtool" accesskey="u" rel="up">Integrating libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Configuring-libtool"></span><h3 class="section">5.4 Configuring libtool</h3>
<span id="index-configuring-libtool"></span>

<p>Libtool requires intimate knowledge of your compiler suite and operating
system to be able to create shared libraries and link against
them properly.  When you install the libtool distribution, a
system-specific libtool script is installed into your binary directory.
</p>
<p>However, when you distribute libtool with your own packages
(see <a href="#Distributing">Distributing</a>), you do not always know the compiler suite and
operating system that are used to compile your package.
</p>
<p>For this reason, libtool must be <em>configured</em> before it can be
used.  This idea should be familiar to anybody who has used a GNU
<code>configure</code> script.  <code>configure</code> runs a number of tests for
system features, then generates the <samp>Makefile</samp>s (and possibly a
<samp>config.h</samp> header file), after which you can run <code>make</code> and
build the package.
</p>
<p>Libtool adds its own tests to your <code>configure</code> script to
generate a libtool script for the installer’s host machine.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#LT_005fINIT" accesskey="1">LT_INIT</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Configuring <code>libtool</code> in <samp>configure.ac</samp>.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Configure-notes" accesskey="2">Configure notes</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Platform-specific notes for configuration.
</td></tr>
</tbody></table>

<hr>
<span id="LT_005fINIT"></span><div class="header">
<p>
Next: <a href="#Configure-notes" accesskey="n" rel="next">Configure notes</a>, Up: <a href="#Configuring" accesskey="u" rel="up">Configuring</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="The-LT_005fINIT-macro"></span><h4 class="subsection">5.4.1 The <code>LT_INIT</code> macro</h4>

<p>If you are using GNU Autoconf (or Automake), you should add a call to
<code>LT_INIT</code> to your <samp>configure.ac</samp> file.  This macro
adds many new tests to the <code>configure</code> script so that the generated
libtool script will understand the characteristics of the host.  It’s the
most important of a number of macros defined by Libtool:
</p>
<dl>
<dt id="index-LT_005fPREREQ">Macro: <strong>LT_PREREQ</strong> <em>(<var>version</var>)</em></dt>
<dd><p>Ensure that a recent enough version of Libtool is being used.  If the
version of Libtool used for <code>LT_INIT</code> is earlier than
<var>version</var>, print an error message to the standard
error output and exit with failure (exit status is 63).  For example:
</p>
<div class="example">
<pre class="example">LT_PREREQ([2.4.7-dirty])
</pre></div>
</dd></dl>

<dl>
<dt id="index-LT_005fINIT">Macro: <strong>LT_INIT</strong> <em>(<var>options</var>)</em></dt>
<dt id="index-AC_005fPROG_005fLIBTOOL">Macro: <strong>AC_PROG_LIBTOOL</strong></dt>
<dt id="index-AM_005fPROG_005fLIBTOOL">Macro: <strong>AM_PROG_LIBTOOL</strong></dt>
<dd><p>Add support for the <samp>--enable-shared</samp>, <samp>--disable-shared</samp>,
<samp>--enable-static</samp>, <samp>--disable-static</samp>, <samp>--with-pic</samp>, and
<samp>--without-pic</samp> <code>configure</code> flags.<a id="DOCF6" href="#FOOT6"><sup>6</sup></a>  <code>AC_PROG_LIBTOOL</code> and
<code>AM_PROG_LIBTOOL</code> are deprecated names for older versions of this macro;
<code>autoupdate</code> will upgrade your <samp>configure.ac</samp> files.
</p>
<p>By default, this macro turns on shared libraries if they are available,
and also enables static libraries if they don’t conflict with the shared
libraries.  You can modify these defaults by passing either
<code>disable-shared</code> or <code>disable-static</code> in the option list to
<code>LT_INIT</code>, or using <code>AC_DISABLE_SHARED</code> or <code>AC_DISABLE_STATIC</code>.
</p>
<div class="example">
<pre class="example"># Turn off shared libraries during beta-testing, since they
# make the build process take too long.
LT_INIT([disable-shared])
</pre></div>

<p>The user may specify modified forms of the configure flags
<samp>--enable-shared</samp> and <samp>--enable-static</samp> to choose whether
shared or static libraries are built based on the name of the package.
For example, to have shared ‘<samp>bfd</samp>’ and ‘<samp>gdb</samp>’ libraries built,
but not shared ‘<samp>libg++</samp>’, you can run all three <code>configure</code>
scripts as follows:
</p>
<div class="example">
<pre class="example">trick$ ./configure --enable-shared=bfd,gdb
</pre></div>

<p>In general, specifying <samp>--enable-shared=<var>pkgs</var></samp> is the same as
configuring with <samp>--enable-shared</samp> every package named in the
comma-separated <var>pkgs</var> list, and every other package with
<samp>--disable-shared</samp>.  The <samp>--enable-static=<var>pkgs</var></samp> flag
behaves similarly, but it uses <samp>--enable-static</samp> and
<samp>--disable-static</samp>.  The same applies to the
<samp>--enable-fast-install=<var>pkgs</var></samp> flag, which uses
<samp>--enable-fast-install</samp> and <samp>--disable-fast-install</samp>.
</p>
<p>The package name ‘<samp>default</samp>’ matches any packages that have not set
their name in the <code>PACKAGE</code> environment variable.
</p>
<p>The <samp>--with-pic</samp> and <samp>--without-pic</samp> configure flags can be used
to specify whether or not <code>libtool</code> uses PIC objects.  By default,
<code>libtool</code> uses PIC objects for shared libraries and non-PIC objects for
static libraries.  The <samp>--with-pic</samp> option also accepts a comma-separated
list of package names.  Specifying <samp>--with-pic=<var>pkgs</var></samp> is the same
as configuring every package in <var>pkgs</var> with <samp>--with-pic</samp> and every
other package with the default configuration.  The package name ‘<samp>default</samp>’
is treated the same as for <samp>--enable-shared</samp> and
<samp>--enable-static</samp>.
</p>
<p>This macro also sets the shell variable <code>LIBTOOL_DEPS</code>, that you
can use to automatically update the libtool script if it becomes
out-of-date.  In order to do that, add to your <samp>configure.ac</samp>:
</p>
<div class="example">
<pre class="example">LT_INIT
AC_SUBST([LIBTOOL_DEPS])
</pre></div>

<p>and, to <samp>Makefile.in</samp> or <samp>Makefile.am</samp>:
</p>
<div class="example">
<pre class="example">LIBTOOL_DEPS = @LIBTOOL_DEPS@
libtool: $(LIBTOOL_DEPS)
        $(SHELL) ./config.status libtool
</pre></div>

<p>If you are using GNU Automake, you can omit the assignment, as Automake
will take care of it.  You’ll obviously have to create some dependency
on <samp>libtool</samp>.
</p>
<p>Aside from <code>disable-static</code> and <code>disable-shared</code>, there are
other options that you can pass to <code>LT_INIT</code> to modify its
behaviour.  Here is a full list:
</p>
<dl compact="compact">
<dt>‘<samp>dlopen</samp>’</dt>
<dd><p>Enable checking for dlopen support.  This option should be used if
the package makes use of the <samp>-dlopen</samp> and <samp>-dlpreopen</samp>
libtool flags, otherwise libtool will assume that the system does not
support dlopening.
</p>
</dd>
<dt>‘<samp>win32-dll</samp>’</dt>
<dd><p>This option should be used if the package has been ported to build clean
dlls on win32 platforms.  Usually this means that any library data items
are exported with <code>__declspec(dllexport)</code> and imported with
<code>__declspec(dllimport)</code>.  If this option is not used, libtool will
assume that the package libraries are not dll clean and will build only
static libraries on win32 hosts.
</p>
<p>Provision must be made to pass <samp>-no-undefined</samp> to <code>libtool</code>
in link mode from the package <code>Makefile</code>.  Naturally, if you pass
<samp>-no-undefined</samp>, you must ensure that all the library symbols
<strong>really are</strong> defined at link time!
</p>
</dd>
<dt>‘<samp>aix-soname=aix</samp>’</dt>
<dt>‘<samp>aix-soname=svr4</samp>’</dt>
<dt>‘<samp>aix-soname=both</samp>’</dt>
<dd><p>Enable the <samp>--with-aix-soname</samp> to <code>configure</code>, which the
user can pass to override the given default.
</p>
<p>By default (and <strong>always</strong> in releases prior to 2.4.4), Libtool always
behaves as if <code>aix-soname=aix</code> is given, with no <code>configure</code>
option for the user to override. Specifically, when the <samp>-brtl</samp> linker
flag is seen in <code>LDFLAGS</code> at build-time, static archives are built from
static objects only, otherwise, traditional AIX shared library archives of
shared objects using in-archive versioning are built (with the <code>.a</code> file
extension!). Similarly, with <samp>-brtl</samp> in <code>LDFLAGS</code>, libtool
shared archives are built from shared objects, without any filename-based
versioning; and without <samp>-brtl</samp> no shared archives are built at all.
</p>
<p>When <code>aix-soname=svr4</code> option is given, or the
<samp>--with-aix-soname=svr4</samp> <code>configure</code> option is passed, static
archives are always created from static objects, even without <samp>-brtl</samp>
in <code>LDFLAGS</code>. Shared archives are made from shared objects, and filename
based versioning is enabled.
</p>
<p>When <code>aix-soname=both</code> option is given, or the
<samp>--with-aix-soname=svr4</samp> <code>configure</code> option is passed, static
archives are built traditionally (as <samp>aix-soname=aix</samp>), and both
kinds of shared archives are built. The <code>.la</code> pseudo-archive specifies
one or the other depending on whether <samp>-brtl</samp> is specified in
<code>LDFLAGS</code> when the library is built.
</p>
</dd>
<dt>‘<samp>disable-fast-install</samp>’</dt>
<dd><p>Change the default behaviour for <code>LT_INIT</code> to disable
optimization for fast installation.  The user may still override this
default, depending on platform support, by specifying
<samp>--enable-fast-install</samp> to <code>configure</code>.
</p>
</dd>
<dt>‘<samp>shared</samp>’</dt>
<dd><p>Change the default behaviour for <code>LT_INIT</code> to enable
shared libraries.  This is the default on all systems where
Libtool knows how to create shared libraries.
The user may still override this default by specifying
<samp>--disable-shared</samp> to <code>configure</code>.
</p>
</dd>
<dt>‘<samp>disable-shared</samp>’</dt>
<dd><p>Change the default behaviour for <code>LT_INIT</code> to disable
shared libraries.  The user may still override this default by
specifying <samp>--enable-shared</samp> to <code>configure</code>.
</p>
</dd>
<dt>‘<samp>static</samp>’</dt>
<dd><p>Change the default behaviour for <code>LT_INIT</code> to enable
static libraries.  This is the default on all systems where
shared libraries have been disabled for some reason, and on
most systems where shared libraries have been enabled.
If shared libraries are enabled, the user may still override
this default by specifying <samp>--disable-static</samp> to
<code>configure</code>.
</p>
</dd>
<dt>‘<samp>disable-static</samp>’</dt>
<dd><p>Change the default behaviour for <code>LT_INIT</code> to disable
static libraries.  The user may still override this default by
specifying <samp>--enable-static</samp> to <code>configure</code>.
</p>
</dd>
<dt>‘<samp>pic-only</samp>’</dt>
<dd><p>Change the default behaviour for <code>libtool</code> to try to use only
PIC objects.  The user may still override this default by specifying
<samp>--without-pic</samp> to <code>configure</code>.
</p>
</dd>
<dt>‘<samp>no-pic</samp>’</dt>
<dd><p>Change the default behaviour of <code>libtool</code> to try to use only
non-PIC objects.  The user may still override this default by
specifying <samp>--with-pic</samp> to <code>configure</code>.
</p>
</dd>
</dl>

</dd></dl>

<dl>
<dt id="index-LT_005fLANG">Macro: <strong>LT_LANG</strong> <em>(<var>language</var>)</em></dt>
<dd><p>Enable <code>libtool</code> support for the language given if it
has not yet already been enabled.  Languages accepted are “C++”,
“Fortran 77”, “Java”, “Go”, and “Windows Resource”.
</p>
<p>If Autoconf language support macros such as <code>AC_PROG_CXX</code> are
used in your <samp>configure.ac</samp>, Libtool language support will automatically
be enabled.
</p>
<p>Conversely using <code>LT_LANG</code> to enable language support for Libtool
will automatically enable Autoconf language support as well.
</p>
<p>Both of the following examples are therefore valid ways of adding C++
language support to Libtool.
</p>
<div class="example">
<pre class="example">LT_INIT
LT_LANG([C++])
</pre></div>

<div class="example">
<pre class="example">LT_INIT
AC_PROG_CXX
</pre></div>

</dd></dl>

<dl>
<dt id="index-AC_005fLIBTOOL_005fDLOPEN">Macro: <strong>AC_LIBTOOL_DLOPEN</strong></dt>
<dd><p>This macro is deprecated, the ‘<samp>dlopen</samp>’ option to <code>LT_INIT</code> should be
used instead.
</p></dd></dl>

<dl>
<dt id="index-AC_005fLIBTOOL_005fWIN32_005fDLL">Macro: <strong>AC_LIBTOOL_WIN32_DLL</strong></dt>
<dd><p>This macro is deprecated, the ‘<samp>win32-dll</samp>’ option to <code>LT_INIT</code> should
be used instead.
</p></dd></dl>

<dl>
<dt id="index-AC_005fDISABLE_005fFAST_005fINSTALL">Macro: <strong>AC_DISABLE_FAST_INSTALL</strong></dt>
<dd><p>This macro is deprecated, the ‘<samp>disable-fast-install</samp>’ option to <code>LT_INIT</code>
should be used instead.
</p></dd></dl>

<dl>
<dt id="index-AC_005fDISABLE_005fSHARED">Macro: <strong>AC_DISABLE_SHARED</strong></dt>
<dt id="index-AM_005fDISABLE_005fSHARED">Macro: <strong>AM_DISABLE_SHARED</strong></dt>
<dd><p>Change the default behaviour for <code>LT_INIT</code> to disable shared libraries.
The user may still override this default by specifying ‘<samp>--enable-shared</samp>’.
The option ‘<samp>disable-shared</samp>’ to <code>LT_INIT</code> is a shorthand for this.
<code>AM_DISABLE_SHARED</code> is a deprecated alias for <code>AC_DISABLE_SHARED</code>.
</p></dd></dl>

<dl>
<dt id="index-AC_005fENABLE_005fSHARED">Macro: <strong>AC_ENABLE_SHARED</strong></dt>
<dt id="index-AM_005fENABLE_005fSHARED">Macro: <strong>AM_ENABLE_SHARED</strong></dt>
<dd><p>Change the default behaviour for <code>LT_INIT</code> to enable shared libraries.
This is the default on all systems where Libtool knows how to create
shared libraries.  The user may still override this default by specifying
‘<samp>--disable-shared</samp>’.  The option ‘<samp>shared</samp>’ to <code>LT_INIT</code> is a
shorthand for this.
<code>AM_ENABLE_SHARED</code> is a deprecated alias for <code>AC_ENABLE_SHARED</code>.
</p></dd></dl>

<dl>
<dt id="index-AC_005fDISABLE_005fSTATIC">Macro: <strong>AC_DISABLE_STATIC</strong></dt>
<dt id="index-AM_005fDISABLE_005fSTATIC">Macro: <strong>AM_DISABLE_STATIC</strong></dt>
<dd><p>Change the default behaviour for <code>LT_INIT</code> to disable static libraries.
The user may still override this default by specifying ‘<samp>--enable-static</samp>’.
The option ‘<samp>disable-static</samp>’ to <code>LT_INIT</code> is a shorthand for this.
<code>AM_DISABLE_STATIC</code> is a deprecated alias for <code>AC_DISABLE_STATIC</code>.
</p></dd></dl>

<dl>
<dt id="index-AC_005fENABLE_005fSTATIC">Macro: <strong>AC_ENABLE_STATIC</strong></dt>
<dt id="index-AM_005fENABLE_005fSTATIC">Macro: <strong>AM_ENABLE_STATIC</strong></dt>
<dd><p>Change the default behaviour for <code>LT_INIT</code> to enable static libraries.
This is the default on all systems where shared libraries have been disabled
for some reason, and on most systems where shared libraries have been enabled.
If shared libraries are enabled, the user may still override this default by
specifying ‘<samp>--disable-static</samp>’.  The option ‘<samp>static</samp>’ to <code>LT_INIT</code>
is a shorthand for this.
<code>AM_ENABLE_STATIC</code> is a deprecated alias for <code>AC_ENABLE_STATIC</code>.
</p></dd></dl>

<p>The tests in <code>LT_INIT</code> also recognize the following
environment variables:
</p>
<dl>
<dt id="index-CC">Variable: <strong>CC</strong></dt>
<dd><p>The C compiler that will be used by the generated <code>libtool</code>.  If
this is not set, <code>LT_INIT</code> will look for <code>gcc</code> or
<code>cc</code>.
</p></dd></dl>

<dl>
<dt id="index-CFLAGS">Variable: <strong>CFLAGS</strong></dt>
<dd><p>Compiler flags used to generate standard object files.  If this is not
set, <code>LT_INIT</code> will not use any such flags.  It affects
only the way <code>LT_INIT</code> runs tests, not the produced
<code>libtool</code>.
</p></dd></dl>

<dl>
<dt id="index-CPPFLAGS">Variable: <strong>CPPFLAGS</strong></dt>
<dd><p>C preprocessor flags.  If this is not set, <code>LT_INIT</code> will
not use any such flags.  It affects only the way <code>LT_INIT</code>
runs tests, not the produced <code>libtool</code>.
</p></dd></dl>

<dl>
<dt id="index-LD">Variable: <strong>LD</strong></dt>
<dd><p>The system linker to use (if the generated <code>libtool</code> requires one).
If this is not set, <code>LT_INIT</code> will try to find out what is
the linker used by <code>CC</code>.
</p></dd></dl>

<dl>
<dt id="index-LDFLAGS">Variable: <strong>LDFLAGS</strong></dt>
<dd><p>The flags to be used by <code>libtool</code> when it links a program.  If
this is not set, <code>LT_INIT</code> will not use any such flags.  It
affects only the way <code>LT_INIT</code> runs tests, not the produced
<code>libtool</code>.
</p></dd></dl>

<dl>
<dt id="index-LIBS">Variable: <strong>LIBS</strong></dt>
<dd><p>The libraries to be used by <code>LT_INIT</code> when it links a
program.  If this is not set, <code>LT_INIT</code> will not use any
such flags.  It affects only the way <code>LT_INIT</code> runs tests,
not the produced <code>libtool</code>.
</p></dd></dl>

<dl>
<dt id="index-NM">Variable: <strong>NM</strong></dt>
<dd><p>Program to use rather than checking for <code>nm</code>.
</p></dd></dl>

<dl>
<dt id="index-RANLIB">Variable: <strong>RANLIB</strong></dt>
<dd><p>Program to use rather than checking for <code>ranlib</code>.
</p></dd></dl>

<dl>
<dt id="index-LN_005fS">Variable: <strong>LN_S</strong></dt>
<dd><p>A command that creates a link of a program, a soft-link if possible, a
hard-link otherwise.  <code>LT_INIT</code> will check for a suitable
program if this variable is not set.
</p></dd></dl>

<dl>
<dt id="index-DLLTOOL">Variable: <strong>DLLTOOL</strong></dt>
<dd><p>Program to use rather than checking for <code>dlltool</code>.  Only meaningful
for Cygwin/MS-Windows.
</p></dd></dl>

<dl>
<dt id="index-OBJDUMP">Variable: <strong>OBJDUMP</strong></dt>
<dd><p>Program to use rather than checking for <code>objdump</code>.  Only meaningful
for Cygwin/MS-Windows.
</p></dd></dl>

<dl>
<dt id="index-AS">Variable: <strong>AS</strong></dt>
<dd><p>Program to use rather than checking for <code>as</code>.  Only used on
Cygwin/MS-Windows at the moment.
</p></dd></dl>

<dl>
<dt id="index-MANIFEST_005fTOOL">Variable: <strong>MANIFEST_TOOL</strong></dt>
<dd><p>Program to use rather than checking for <code>mt</code>, the Manifest Tool.
Only used on Cygwin/MS-Windows at the moment.
</p></dd></dl>

<dl>
<dt id="index-LT_005fSYS_005fLIBRARY_005fPATH">Variable: <strong>LT_SYS_LIBRARY_PATH</strong></dt>
<dd><p>Libtool has heuristics for the system search path for runtime-loaded
libraries.  If the guessed default does not match the setup of the host
system, this variable can be used to modify that path list, as follows
(<code>LT_SYS_LIBRARY_PATH</code> is a colon-delimited list like <code>PATH</code>):
</p><ul>
<li> <code>path:</code>
The heuristically determined paths will be appened after the trailing
colon;
</li><li> <code>:path</code>
The heuristically determined paths will be prepended before the leading
colon;
</li><li> <code>path::path</code>
The heuristically determined paths will be inserted between the double
colons;
</li><li> <code>path</code>
With no dangling colons, the heuristically determined paths will be
ignored entirely.
</li></ul>
</dd></dl>

<p>With 1.3 era libtool, if you wanted to know any details of what
libtool had discovered about your architecture and environment, you
had to run the script with <samp>--config</samp> and grep through the
results.  This idiom was supported up to and including 1.5.x era
libtool, where it was possible to call the generated libtool script
from <samp>configure.ac</samp> as soon as <code>LT_INIT</code> had
completed.  However, one of the features of libtool 1.4 was that the
libtool configuration was migrated out of a separate <samp>ltconfig</samp>
file, and added to the <code>LT_INIT</code> macro (nee <code>AC_PROG_LIBTOOL</code>),
so the results of the configuration tests were available directly to code in
<samp>configure.ac</samp>, rendering the call out to the generated libtool
script obsolete.
</p>
<p>Starting with libtool 2.0, the multipass generation of the libtool
script has been consolidated into a single <samp>config.status</samp> pass,
which happens after all the code in <samp>configure.ac</samp> has
completed.  The implication of this is that the libtool script does
not exist during execution of code from <samp>configure.ac</samp>, and so
obviously it cannot be called for <samp>--config</samp> details anymore.  If
you are upgrading projects that used this idiom to libtool 2.0 or
newer, you should replace those calls with direct references to the
equivalent Autoconf shell variables that are set by the configure time
tests before being passed to <samp>config.status</samp> for inclusion in the
generated libtool script.
</p>
<dl>
<dt id="index-LT_005fOUTPUT">Macro: <strong>LT_OUTPUT</strong></dt>
<dd><p>By default, the configured <samp>libtool</samp> script is generated by the
call to <code>AC_OUTPUT</code> command, and there is rarely any need to use
<samp>libtool</samp> from <samp>configure</samp>.  However, sometimes it is
necessary to run configure time compile and link tests using
<samp>libtool</samp>.  You can add <code>LT_OUTPUT</code> to your
<samp>configure.ac</samp> any time after <code>LT_INIT</code> and any
<code>LT_LANG</code> calls; that done, <samp>libtool</samp> will be created by a
specially generated <samp>config.lt</samp> file, and available for use in
later tests.
</p>
<p>Also, when <code>LT_OUTPUT</code> is used, for backwards compatibility with
Automake regeneration rules, <samp>config.status</samp> will call
<samp>config.lt</samp> to regenerate <samp>libtool</samp>, rather than generating
the file itself.
</p></dd></dl>

<span id="index-aclocal"></span>
<p>When you invoke the <code>libtoolize</code> program (see <a href="#Invoking-libtoolize">Invoking libtoolize</a>), it will tell you where to find a definition of
<code>LT_INIT</code>.  If you use Automake, the <code>aclocal</code> program
will automatically add <code>LT_INIT</code> support to your
<samp>configure</samp> script when it sees the invocation of <code>LT_INIT</code>
in <samp>configure.ac</samp>.
</p>
<p>Because of these changes, and the runtime version compatibility checks
Libtool now executes, we now advise <strong>against</strong> including a copy of
<samp>libtool.m4</samp> (and brethren) in <samp>acinclude.m4</samp>.  Instead,
you should set your project macro directory with
<code>AC_CONFIG_MACRO_DIRS</code>.  When you <code>libtoolize</code> your
project, a copy of the relevant macro definitions will be placed in
your <code>AC_CONFIG_MACRO_DIRS</code>, where <code>aclocal</code> can reference
them directly from <samp>aclocal.m4</samp>.
</p>

<hr>
<span id="Configure-notes"></span><div class="header">
<p>
Previous: <a href="#LT_005fINIT" accesskey="p" rel="prev">LT_INIT</a>, Up: <a href="#Configuring" accesskey="u" rel="up">Configuring</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Platform_002dspecific-configuration-notes"></span><h4 class="subsection">5.4.2 Platform-specific configuration notes</h4>

<p>While Libtool tries to hide as many platform-specific features as possible,
some have to be taken into account when configuring either the Libtool package
or a libtoolized package.
</p>
<ul>
<li> You currently need GNU make to build the Libtool package itself.

</li><li> On AIX there are two different styles of shared linking, one where symbols
are bound at link-time and one where symbols are bound at runtime only,
similar to ELF.  In case of doubt use <code>LDFLAGS=-Wl,-brtl</code> for the latter style.

</li><li> On AIX, native tools are to be preferred over binutils; especially for C++ code,
if using the AIX Toolbox GCC 4.0 and binutils, configure with
<code>AR=/usr/bin/ar LD=/usr/bin/ld NM='/usr/bin/nm -B'</code>.

</li><li> On AIX, the <code>/bin/sh</code> is very slow due to its inefficient handling
of here-documents.  A modern shell is preferable:
<div class="example">
<pre class="example">CONFIG_SHELL=/bin/bash; export $CONFIG_SHELL
$CONFIG_SHELL ./configure [...]
</pre></div>

</li><li> For C++ code with templates, it may be necessary to specify the way the compiler
will generate the instantiations.  For Portland pgCC version5, use
<code>CXX='pgCC --one_instantiation_per_object'</code> and avoid parallel <code>make</code>.

</li><li> On Darwin, for C++ code with templates you need two level shared libraries.
Libtool builds these by default if <code>MACOSX_DEPLOYMENT_TARGET</code> is set to
10.3 or later at <code>configure</code> time.  See <a href="rdar://problem/4135857">rdar://problem/4135857</a>
for more information on this issue.


</li><li> The default shell on UNICOS 9, a ksh 88e variant, is too buggy to
correctly execute the libtool script.  Users are advised to install a
modern shell such as GNU bash.

</li><li> Some HP-UX <code>sed</code> programs are horribly broken, and cannot handle
libtool’s requirements, so users may report unusual problems.  There
is no workaround except to install a working <code>sed</code> (such as GNU sed)
on these systems.

</li><li> The vendor-distributed NCR MP-RAS <code>cc</code> programs emits copyright
on standard error that confuse tests on size of <samp>conftest.err</samp>.  The
workaround is to specify <code>CC</code> when run configure with
<code>CC='cc -Hnocopyr'</code>.

</li><li> Any earlier DG/UX system with ELF executables, such as R3.10 or
R4.10, is also likely to work, but hasn’t been explicitly tested.

</li><li> On Reliant Unix libtool has only been tested with the Siemens C-compiler
and an old version of <code>gcc</code> provided by Marco Walther.

</li><li> <samp>libtool.m4</samp>, <samp>ltdl.m4</samp> and the <samp>configure.ac</samp> files are marked
to use autoconf-mode, which is distributed with GNU Emacs 21, Autoconf itself,
and all recent releases of XEmacs.

</li><li> When building on some GNU/Linux systems for multilib targets <code>libtool</code>
sometimes guesses the wrong paths that the linker and dynamic linker search by
default. If this occurs for the dynamic library path, you may use the
<code>LT_SYS_LIBRARY_PATH</code> environment variable to adjust. Otherwise, at
<code>configure</code> time you may override libtool’s guesses by setting the
<code>autoconf</code> cache variables <code>lt_cv_sys_lib_search_path_spec</code> and
<code>lt_cv_sys_lib_dlsearch_path_spec</code> respectively.

</li></ul>


<hr>
<span id="Distributing"></span><div class="header">
<p>
Next: <a href="#Static_002donly-libraries" accesskey="n" rel="next">Static-only libraries</a>, Previous: <a href="#Configuring" accesskey="p" rel="prev">Configuring</a>, Up: <a href="#Integrating-libtool" accesskey="u" rel="up">Integrating libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Including-libtool-in-your-package"></span><h3 class="section">5.5 Including libtool in your package</h3>

<p>In order to use libtool, you need to include the following files with
your package:
</p>
<dl compact="compact">
<dt><samp>config.guess</samp></dt>
<dd><span id="index-config_002eguess"></span>
<p>Attempt to guess a canonical system name.
</p>
</dd>
<dt><samp>config.sub</samp></dt>
<dd><span id="index-config_002esub"></span>
<p>Canonical system name validation subroutine script.
</p>
</dd>
<dt><samp>install-sh</samp></dt>
<dd><span id="index-install_002dsh"></span>
<p>BSD-compatible <code>install</code> replacement script.
</p>
</dd>
<dt><samp>ltmain.sh</samp></dt>
<dd><span id="index-ltmain_002esh"></span>
<p>A generic script implementing basic libtool functionality.
</p></dd>
</dl>

<p>Note that the libtool script itself should <em>not</em> be included with
your package.  See <a href="#Configuring">Configuring</a>.
</p>
<p>You should use the <code>libtoolize</code> program, rather than manually
copying these files into your package.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Invoking-libtoolize" accesskey="1">Invoking libtoolize</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top"><code>libtoolize</code> command line options.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Autoconf-and-LTLIBOBJS" accesskey="2">Autoconf and LTLIBOBJS</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Autoconf automates LTLIBOBJS generation.
</td></tr>
</tbody></table>

<hr>
<span id="Invoking-libtoolize"></span><div class="header">
<p>
Next: <a href="#Autoconf-and-LTLIBOBJS" accesskey="n" rel="next">Autoconf and LTLIBOBJS</a>, Up: <a href="#Distributing" accesskey="u" rel="up">Distributing</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Invoking-libtoolize-1"></span><h4 class="subsection">5.5.1 Invoking <code>libtoolize</code></h4>
<span id="index-libtoolize"></span>
<span id="index-libtoolize-command-options"></span>
<span id="index-command-options_002c-libtoolize"></span>
<span id="index-options_002c-libtoolize-command"></span>

<p>The <code>libtoolize</code> program provides a standard way to add libtool
support to your package.  In the future, it may implement better usage
checking, or other features to make libtool even easier to use.
</p>
<p>The <code>libtoolize</code> program has the following synopsis:
</p>
<div class="example">
<pre class="example">libtoolize [<var>option</var>]…
</pre></div>

<p>and accepts the following options:
</p>
<dl compact="compact">
<dt><samp>--copy</samp></dt>
<dt><samp>-c</samp></dt>
<dd><p>Copy files from the libtool data directory rather than creating
symlinks.
</p>
</dd>
<dt><samp>--debug</samp></dt>
<dd><p>Dump a trace of shell script execution to standard output.  This
produces a lot of output, so you may wish to pipe it to <code>less</code> (or
<code>more</code>) or redirect to a file.
</p>
</dd>
<dt><samp>--dry-run</samp></dt>
<dt><samp>-n</samp></dt>
<dd><p>Don’t run any commands that modify the file system, just print them
out.
</p>
</dd>
<dt><samp>--force</samp></dt>
<dt><samp>-f</samp></dt>
<dd><p>Replace existing libtool files.  By default, <code>libtoolize</code> won’t
overwrite existing files.
</p>
</dd>
<dt><samp>--help</samp></dt>
<dd><p>Display a help message and exit.
</p>
</dd>
<dt><samp>--ltdl [<var>target-directory-name</var>]</samp></dt>
<dd><p>Install libltdl in the <var>target-directory-name</var> subdirectory of
your package.  Normally, the directory is extracted from the argument
to <code>LT_CONFIG_LTDL_DIR</code> in <samp>configure.ac</samp>, though you can
also specify a subdirectory name here if you are not using Autoconf
for example.  If <code>libtoolize</code> can’t determine the target
directory, ‘<samp>libltdl</samp>’ is used as the default.
</p>
</dd>
<dt><samp>--no-warn</samp></dt>
<dd><p>Normally, Libtoolize tries to diagnose use of deprecated libtool macros
and other stylistic issues.  If you are deliberately using outdated
calling conventions, this option prevents Libtoolize from explaining
how to update your project’s Libtool conventions.
</p>
</dd>
<dt><samp>--nonrecursive</samp></dt>
<dd><p>If passed in conjunction with <samp>--ltdl</samp>, this option will cause
the <code>libltdl</code> installed by ‘<samp>libtoolize</samp>’ to be set up for
use with a non-recursive <code>automake</code> build.  To make use of it,
you will need to add the following to the <samp>Makefile.am</samp> of the
parent project:
</p>
<div class="example">
<pre class="example">## libltdl/ltdl.mk <span class="roman">appends to the following variables</span>
## <span class="roman">so we set them here before including it:</span>
BUILT_SOURCES   =

AM_CPPFLAGS        =
AM_LDFLAGS         =

include_HEADERS    =
noinst_LTLIBRARIES =
lib_LTLIBRARIES   =
EXTRA_LTLIBRARIES  =

EXTRA_DIST   =

CLEANFILES   =
MOSTLYCLEANFILES   =

include libltdl/ltdl.mk
</pre></div>


</dd>
<dt><samp>--quiet</samp></dt>
<dt><samp>-q</samp></dt>
<dd><p>Work silently.  ‘<samp>libtoolize --quiet</samp>’ is used by GNU Automake
to add libtool files to your package if necessary.
</p>
</dd>
<dt><samp>--recursive</samp></dt>
<dd><p>If passed in conjunction with <samp>--ltdl</samp>, this option will cause
the <code>libtoolize</code> installed ‘<samp>libltdl</samp>’ to be set up for use
with a recursive <code>automake</code> build.  To make use of it, you
will need to adjust the parent project’s <samp>configure.ac</samp>:
</p>
<div class="example">
<pre class="example">AC_CONFIG_FILES([libltdl/Makefile])
</pre></div>

<p>and <samp>Makefile.am</samp>:
</p>
<div class="example">
<pre class="example">SUBDIRS += libltdl
</pre></div>

</dd>
<dt><samp>--subproject</samp></dt>
<dd><p>If passed in conjunction with <samp>--ltdl</samp>, this option will cause
the <code>libtoolize</code> installed ‘<samp>libltdl</samp>’ to be set up for
independent configuration and compilation as a self-contained
subproject.  To make use of it, you should arrange for your build to
call <code>libltdl/configure</code>, and then run <code>make</code> in the
<samp>libltdl</samp> directory (or the subdirectory you put libltdl into).
If your project uses Autoconf, you can use the supplied
‘<samp>LT_WITH_LTDL</samp>’ macro, or else call ‘<samp>AC_CONFIG_SUBDIRS</samp>’
directly.
</p>
<p>Previous releases of ‘<samp>libltdl</samp>’ built exclusively in this mode,
but now it is the default mode both for backwards compatibility and
because, for example, it is suitable for use in projects that wish to
use ‘<samp>libltdl</samp>’, but not use the Autotools for their own build
process.
</p>
</dd>
<dt><samp>--verbose</samp></dt>
<dt><samp>-v</samp></dt>
<dd><p>Work noisily!  Give a blow by blow account of what
<code>libtoolize</code> is doing.
</p>
</dd>
<dt><samp>--version</samp></dt>
<dd><p>Print <code>libtoolize</code> version information and exit.
</p></dd>
</dl>

<span id="index-LIBTOOLIZE_005fOPTIONS"></span>
<p>Sometimes it can be useful to pass options to <code>libtoolize</code> even
though it is called by another program, such as <code>autoreconf</code>.  A
limited number of options are parsed from the environment variable
<code>LIBTOOLIZE_OPTIONS</code>: currently <samp>--debug</samp>, <samp>--no-warn</samp>,
<samp>--quiet</samp> and <samp>--verbose</samp>.  Multiple options passed in
<code>LIBTOOLIZE_OPTIONS</code> must be separated with a space, comma or a
colon.
</p>
<p>By default, a warning is issued for unknown options found in
<code>LIBTOOLIZE_OPTIONS</code> unless the first such option is
<samp>--no-warn</samp>.  Where <code>libtoolize</code> has always quit
on receipt of an unknown option at the command line, this and all
previous releases of <code>libtoolize</code> will continue unabated whatever
the content of <code>LIBTOOLIZE_OPTIONS</code> (modulo some possible warning
messages).
</p>
<div class="example">
<pre class="example">trick$ <kbd>LIBTOOLIZE_OPTIONS=--no-warn,--quiet autoreconf --install</kbd>
</pre></div>

<span id="index-AC_005fCONFIG_005fMACRO_005fDIRS"></span>
<p>If <code>libtoolize</code> detects an explicit call to
<code>AC_CONFIG_MACRO_DIRS</code> (see <a href="https://www.gnu.org/software/autoconf/manual/autoconf.html#Input">The Autoconf Manual</a> in <cite>The Autoconf Manual</cite>) in your <samp>configure.ac</samp>, it will
put the Libtool macros in the specified directory.
</p>
<p>In the future other Autotools will automatically check the contents of
<code>AC_CONFIG_MACRO_DIRS</code>, but at the moment it is more portable to
add the macro directory to <code>ACLOCAL_AMFLAGS</code> in
<samp>Makefile.am</samp>, which is where the tools currently look.  If
<code>libtoolize</code> doesn’t see <code>AC_CONFIG_MACRO_DIRS</code>, it too
will honour the first ‘<samp>-I</samp>’ argument in <code>ACLOCAL_AMFLAGS</code>
when choosing a directory to store libtool configuration macros in.
It is perfectly sensible to use both <code>AC_CONFIG_MACRO_DIRS</code> and
<code>ACLOCAL_AMFLAGS</code>, as long as they are kept in synchronisation.
</p>
<div class="example">
<pre class="example">ACLOCAL_AMFLAGS = -I m4
</pre></div>

<p>When you bootstrap your project with <code>aclocal</code>, then you will
need to explicitly pass the same macro directory with
<code>aclocal</code>’s ‘<samp>-I</samp>’ flag:
</p>
<div class="example">
<pre class="example">trick$ <kbd>aclocal -I m4</kbd>
</pre></div>

<span id="index-AC_005fCONFIG_005fAUX_005fDIR"></span>
<p>If <code>libtoolize</code> detects an explicit call to
<code>AC_CONFIG_AUX_DIR</code> (see <a href="https://www.gnu.org/software/autoconf/manual/autoconf.html#Input">The Autoconf Manual</a> in <cite>The Autoconf Manual</cite>) in your <samp>configure.ac</samp>, it
will put the other support files in the specified directory.
Otherwise they too end up in the project root directory.
</p>
<p>Unless <samp>--no-warn</samp> is passed, <code>libtoolize</code> displays
hints for adding libtool support to your package, as well.
</p>
<hr>
<span id="Autoconf-and-LTLIBOBJS"></span><div class="header">
<p>
Previous: <a href="#Invoking-libtoolize" accesskey="p" rel="prev">Invoking libtoolize</a>, Up: <a href="#Distributing" accesskey="u" rel="up">Distributing</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Autoconf-and-LTLIBOBJS-1"></span><h4 class="subsection">5.5.2 Autoconf and <code>LTLIBOBJS</code></h4>

<p>People used to add code like the following to their
<samp>configure.ac</samp>:
</p>
<span id="index-LTLIBOBJS"></span>
<div class="example">
<pre class="example">LTLIBOBJS=`echo "$LIBOBJS" | sed 's/\.[^.]* /.lo /g;s/\.[^.]*$/.lo/'`
AC_SUBST([LTLIBOBJS])
</pre></div>

<p>This is no longer required (since Autoconf 2.54), and doesn’t take
Automake’s deansification support into account either, so doesn’t work
correctly even with ancient Autoconfs!
</p>
<p>Provided you are using a recent (2.54 or better) incarnation of
Autoconf, the call to <code>AC_OUTPUT</code> takes care of setting
<code>LTLIBOBJS</code> up correctly, so you can simply delete such snippets
from your <samp>configure.ac</samp> if you had them.
</p>

<hr>
<span id="Static_002donly-libraries"></span><div class="header">
<p>
Previous: <a href="#Distributing" accesskey="p" rel="prev">Distributing</a>, Up: <a href="#Integrating-libtool" accesskey="u" rel="up">Integrating libtool</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Static_002donly-libraries-1"></span><h3 class="section">5.6 Static-only libraries</h3>
<span id="index-debugging-libraries"></span>
<span id="index-developing-libraries"></span>
<span id="index-double_002dcompilation_002c-avoiding"></span>
<span id="index-avoiding-shared-libraries"></span>
<span id="index-eliding-shared-libraries"></span>
<span id="index-using-shared-libraries_002c-not"></span>
<span id="index-shared-libraries_002c-not-using"></span>
<span id="index-time_002c-saving"></span>
<span id="index-saving-time"></span>

<p>When you are developing a package, it is often worthwhile to configure
your package with the <samp>--disable-shared</samp> flag, or to override the
defaults for <code>LT_INIT</code> by using the <code>disable-shared</code> option
(see <a href="#LT_005fINIT">The <code>LT_INIT</code> macro</a>).  This prevents libtool
from building shared libraries, which has several advantages:
</p>
<ul>
<li> compilation is twice as fast, which can speed up your development cycle,

</li><li> debugging is easier because you don’t need to deal with any complexities
added by shared libraries, and

</li><li> you can see how libtool behaves on static-only platforms.
</li></ul>

<p>You may want to put a small note in your package <samp>README</samp> to let
other developers know that <samp>--disable-shared</samp> can save them time.
The following example note is taken from the GIMP<a id="DOCF7" href="#FOOT7"><sup>7</sup></a> distribution <samp>README</samp>:
</p>
<div class="example">
<pre class="example">The GIMP uses GNU Libtool to build shared libraries on a
variety of systems.  While this is very nice for making usable
binaries, it can be a pain when trying to debug a program.  For that
reason, compilation of shared libraries can be turned off by
specifying the <samp>--disable-shared</samp> option to <samp>configure</samp>.
</pre></div>


<hr>
<span id="Other-languages"></span><div class="header">
<p>
Next: <a href="#Versioning" accesskey="n" rel="next">Versioning</a>, Previous: <a href="#Integrating-libtool" accesskey="p" rel="prev">Integrating libtool</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Using-libtool-with-other-languages"></span><h2 class="chapter">6 Using libtool with other languages</h2>
<span id="index-C_002c-not-using"></span>
<span id="index-languages_002c-non_002dC"></span>
<span id="index-C_002b_002b_002c-using"></span>

<p>Libtool was first implemented to add support for writing shared
libraries in the C language.  However, over time, libtool is being
integrated with other languages, so that programmers are free to reap
the benefits of shared libraries in their favorite programming language.
</p>
<p>This chapter describes how libtool interacts with other languages,
and what special considerations you need to make if you do not use C.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#C_002b_002b-libraries" accesskey="1">C++ libraries</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Writing libraries for C++
</td></tr>
<tr><td align="left" valign="top">• <a href="#Tags" accesskey="2">Tags</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Tags
</td></tr>
</tbody></table>

<hr>
<span id="C_002b_002b-libraries"></span><div class="header">
<p>
Next: <a href="#Tags" accesskey="n" rel="next">Tags</a>, Up: <a href="#Other-languages" accesskey="u" rel="up">Other languages</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Writing-libraries-for-C_002b_002b"></span><h3 class="section">6.1 Writing libraries for C++</h3>
<span id="index-trouble-with-C_002b_002b"></span>
<span id="index-pitfalls-using-C_002b_002b"></span>
<span id="index-C_002b_002b_002c-pitfalls"></span>

<p>Creating libraries of C++ code should be a fairly straightforward
process, because its object files differ from C ones in only three ways:
</p>
<ol>
<li> Because of name mangling, C++ libraries are only usable by the C++
compiler that created them.  This decision was made by the designers of
C++ to protect users from conflicting implementations of
features such as constructors, exception handling, and RTTI.

</li><li> On some systems, the C++ compiler must take special actions for the
dynamic linker to run dynamic (i.e., run-time) initializers.  This means
that we should not call <code>ld</code> directly to link such libraries, and
we should use the C++ compiler instead.

</li><li> C++ compilers will link some Standard C++ library in by default, but
libtool does not know what these libraries are, so it cannot even run
the inter-library dependence analyzer to check how to link it in.
Therefore, running <code>ld</code> to link a C++ program or library is deemed
to fail.
</li></ol>

<p>Because of these three issues, Libtool has been designed to always use
the C++ compiler to compile and link C++ programs and libraries.  In
some instances the <code>main()</code> function of a program must also be
compiled with the C++ compiler for static C++ objects to be properly
initialized.
</p>
<hr>
<span id="Tags"></span><div class="header">
<p>
Previous: <a href="#C_002b_002b-libraries" accesskey="p" rel="prev">C++ libraries</a>, Up: <a href="#Other-languages" accesskey="u" rel="up">Other languages</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Tags-1"></span><h3 class="section">6.2 Tags</h3>
<span id="index-tag-names"></span>
<span id="index-language-names"></span>
<span id="index-inferring-tags"></span>

<p>Libtool supports multiple languages through the use of tags.  Technically
a tag corresponds to a set of configuration variables associated with a
language.  These variables tell <code>libtool</code> how it should create
objects and libraries for each language.
</p>
<p>Tags are defined at <code>configure</code>-time for each language activated
in the package (see <code>LT_LANG</code> in <a href="#LT_005fINIT">LT_INIT</a>).  Here is the
correspondence between language names and tags names.
</p>
<table>
<tbody><tr><td>Language name</td><td>Tag name</td></tr>
<tr><td>C</td><td>CC</td></tr>
<tr><td>C++</td><td>CXX</td></tr>
<tr><td>Java</td><td>GCJ</td></tr>
<tr><td>Fortran 77</td><td>F77</td></tr>
<tr><td>Fortran</td><td>FC</td></tr>
<tr><td>Go</td><td>GO</td></tr>
<tr><td>Windows Resource</td><td>RC</td></tr>
</tbody></table>

<p><code>libtool</code> tries to automatically infer what tag to use from
the compiler command being used to compile or link.  If it can’t infer
a tag, then it defaults to the configuration for the <code>C</code> language.
</p>
<p>The tag can also be specified using <code>libtool</code>’s
<samp>--tag=<var>tag</var></samp> option (see <a href="#Invoking-libtool">Invoking libtool</a>).  It is a good
idea to do so in <samp>Makefile</samp> rules, because that will allow users to
substitute the compiler without relying on <code>libtool</code> inference
heuristics.  When no tag is specified, <code>libtool</code> will default
to <code>CC</code>; this tag always exists.
</p>
<p>Finally, the set of tags available in a particular project can be
retrieved by tracing for the <code>LT_SUPPORTED_TAG</code> macro (see <a href="#Trace-interface">Trace interface</a>).
</p>
<hr>
<span id="Versioning"></span><div class="header">
<p>
Next: <a href="#Library-tips" accesskey="n" rel="next">Library tips</a>, Previous: <a href="#Other-languages" accesskey="p" rel="prev">Other languages</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Library-interface-versions"></span><h2 class="chapter">7 Library interface versions</h2>
<span id="index-dynamic-dependencies"></span>
<span id="index-dependency-versioning"></span>
<span id="index-shared-library-versions"></span>

<p>The most difficult issue introduced by shared libraries is that of
creating and resolving runtime dependencies.  Dependencies on programs
and libraries are often described in terms of a single name, such as
<code>sed</code>.  So, one may say “libtool depends on sed,” and that is
good enough for most purposes.
</p>
<p>However, when an interface changes regularly, we need to be more
specific: “Gnus 5.1 requires Emacs 19.28 or above.”  Here, the
description of an interface consists of a name, and a “version
number.”
</p>
<p>Even that sort of description is not accurate enough for some purposes.
What if Emacs 20 changes enough to break Gnus 5.1?
</p>
<p>The same problem exists in shared libraries: we require a formal version
system to describe the sorts of dependencies that programs have on
shared libraries, so that the dynamic linker can guarantee that programs
are linked only against libraries that provide the interface they
require.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Interfaces" accesskey="1">Interfaces</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">What are library interfaces?
</td></tr>
<tr><td align="left" valign="top">• <a href="#Libtool-versioning" accesskey="2">Libtool versioning</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Libtool’s versioning system.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Updating-version-info" accesskey="3">Updating version info</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Changing version information before releases.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Release-numbers" accesskey="4">Release numbers</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Breaking binary compatibility for aesthetics.
</td></tr>
</tbody></table>

<hr>
<span id="Interfaces"></span><div class="header">
<p>
Next: <a href="#Libtool-versioning" accesskey="n" rel="next">Libtool versioning</a>, Up: <a href="#Versioning" accesskey="u" rel="up">Versioning</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="What-are-library-interfaces_003f"></span><h3 class="section">7.1 What are library interfaces?</h3>
<span id="index-library-interfaces"></span>

<p>Interfaces for libraries may be any of the following (and more):
</p>
<ul>
<li> global variables: both names and types

</li><li> global functions: argument types and number, return types, and function names

</li><li> standard input, standard output, standard error, and file formats

</li><li> sockets, pipes, and other inter-process communication protocol formats
</li></ul>

<p>Note that static functions do not count as interfaces, because they are
not directly available to the user of the library.
</p>
<hr>
<span id="Libtool-versioning"></span><div class="header">
<p>
Next: <a href="#Updating-version-info" accesskey="n" rel="next">Updating version info</a>, Previous: <a href="#Interfaces" accesskey="p" rel="prev">Interfaces</a>, Up: <a href="#Versioning" accesskey="u" rel="up">Versioning</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Libtool_0027s-versioning-system"></span><h3 class="section">7.2 Libtool’s versioning system</h3>
<span id="index-libtool-library-versions"></span>
<span id="index-formal-versioning"></span>
<span id="index-versioning_002c-formal"></span>

<p>Libtool has its own formal versioning system.  It is not as flexible as
some, but it is definitely the simplest of the more powerful versioning
systems.
</p>
<p>Think of a library as exporting several sets of interfaces, arbitrarily
represented by integers.  When a program is linked against a library, it
may use any subset of those interfaces.
</p>
<p>Libtool’s description of the interfaces that a program uses is simple:
it encodes the least and the greatest interface numbers in the resulting
binary (<var>first-interface</var>, <var>last-interface</var>).
</p>
<p>The dynamic linker is guaranteed that if a library supports <em>every</em>
interface number between <var>first-interface</var> and <var>last-interface</var>,
then the program can be relinked against that library.
</p>
<p>Note that this can cause problems because libtool’s compatibility
requirements are actually stricter than is necessary.
</p>
<p>Say <samp>libhello</samp> supports interfaces 5, 16, 17, 18, and 19, and that
libtool is used to link <samp>test</samp> against <samp>libhello</samp>.
</p>
<p>Libtool encodes the numbers 5 and 19 in <samp>test</samp>, and the dynamic
linker will only link <samp>test</samp> against libraries that support
<em>every</em> interface between 5 and 19.  So, the dynamic linker refuses
to link <samp>test</samp> against <samp>libhello</samp>!
</p>
<p>In order to eliminate this problem, libtool only allows libraries to
declare consecutive interface numbers.  So, <samp>libhello</samp> can declare at
most that it supports interfaces 16 through 19.  Then, the dynamic
linker will link <samp>test</samp> against <samp>libhello</samp>.
</p>
<p>So, libtool library versions are described by three integers:
</p>
<dl compact="compact">
<dt><var>current</var></dt>
<dd><p>The most recent interface number that this library implements.
</p>
</dd>
<dt><var>revision</var></dt>
<dd><p>The implementation number of the <var>current</var> interface.
</p>
</dd>
<dt><var>age</var></dt>
<dd><p>The difference between the newest and oldest interfaces that this
library implements.  In other words, the library implements all the
interface numbers in the range from number <code><var>current</var> -
<var>age</var></code> to <code><var>current</var></code>.
</p></dd>
</dl>

<p>If two libraries have identical <var>current</var> and <var>age</var> numbers,
then the dynamic linker chooses the library with the greater
<var>revision</var> number.
</p>
<hr>
<span id="Updating-version-info"></span><div class="header">
<p>
Next: <a href="#Release-numbers" accesskey="n" rel="next">Release numbers</a>, Previous: <a href="#Libtool-versioning" accesskey="p" rel="prev">Libtool versioning</a>, Up: <a href="#Versioning" accesskey="u" rel="up">Versioning</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Updating-library-version-information"></span><h3 class="section">7.3 Updating library version information</h3>

<p>If you want to use libtool’s versioning system, then you must specify
the version information to libtool using the <samp>-version-info</samp> flag
during link mode (see <a href="#Link-mode">Link mode</a>).
</p>
<p>This flag accepts an argument of the form
‘<samp><var>current</var>[:<var>revision</var>[:<var>age</var>]]</samp>’.  So, passing
<samp>-version-info 3:12:1</samp> sets <var>current</var> to 3, <var>revision</var> to
12, and <var>age</var> to 1.
</p>
<p>If either <var>revision</var> or <var>age</var> are omitted, they default to 0.
Also note that <var>age</var> must be less than or equal to the <var>current</var>
interface number.
</p>
<p>Here are a set of rules to help you update your library version
information:
</p>
<ol>
<li> Start with version information of ‘<samp>0:0:0</samp>’ for each libtool library.

</li><li> Update the version information only immediately before a public release
of your software.  More frequent updates are unnecessary, and only
guarantee that the current interface number gets larger faster.

</li><li> If the library source code has changed at all since the last update,
then increment <var>revision</var> (‘<samp><var>c</var>:<var>r</var>:<var>a</var></samp>’ becomes
‘<samp><var>c</var>:<em>r+1</em>:<var>a</var></samp>’).

</li><li> If any interfaces have been added, removed, or changed since the last
update, increment <var>current</var>, and set <var>revision</var> to 0.

</li><li> If any interfaces have been added since the last public release, then
increment <var>age</var>.

</li><li> If any interfaces have been removed or changed since the last public
release, then set <var>age</var> to 0.
</li></ol>

<p><strong><em>Never</em></strong> try to set the interface numbers so that they
correspond to the release number of your package.  This is an abuse that
only fosters misunderstanding of the purpose of library versions.
Instead, use the <samp>-release</samp> flag (see <a href="#Release-numbers">Release numbers</a>), but be
warned that every release of your package will not be binary compatible
with any other release.
</p>
<p>The following explanation may help to understand the above rules a bit
better: consider that there are three possible kinds of reactions from
users of your library to changes in a shared library:
</p>
<ol>
<li> Programs using the previous version may use the new version as
drop-in replacement, and programs using the new version can also work
with the previous one.  In other words, no recompiling nor relinking
is needed.  In this case, bump <var>revision</var> only, don’t touch
<var>current</var> nor <var>age</var>.

</li><li> Programs using the previous version may use the new version as
drop-in replacement, but programs using the new version may use APIs not
present in the previous one.  In other words, a program linking against
the new version may fail with “unresolved symbols” if linking against
the old version at runtime: set <var>revision</var> to 0, bump <var>current</var>
and <var>age</var>.

</li><li> Programs may need to be changed, recompiled, and relinked in order to use
the new version.  Bump <var>current</var>, set <var>revision</var> and <var>age</var>
to 0.
</li></ol>

<p>In the above description, <em>programs</em> using the library in question
may also be replaced by other libraries using it.
</p>

<hr>
<span id="Release-numbers"></span><div class="header">
<p>
Previous: <a href="#Updating-version-info" accesskey="p" rel="prev">Updating version info</a>, Up: <a href="#Versioning" accesskey="u" rel="up">Versioning</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Managing-release-information"></span><h3 class="section">7.4 Managing release information</h3>

<p>Often, people want to encode the name of the package release into the
shared library so that it is obvious to the user what package their
programs are linked against.  This convention is used especially on
GNU/Linux:
</p>
<div class="example">
<pre class="example">trick$ <kbd>ls /usr/lib/libbfd*</kbd>
/usr/lib/libbfd.a           /usr/lib/libbfd.so.2.7.0.2
/usr/lib/libbfd.so
trick$
</pre></div>

<p>On ‘<samp>trick</samp>’, <samp>/usr/lib/libbfd.so</samp> is a symbolic link to
<samp>libbfd.so.2.7.0.2</samp>, which was distributed as a part of
‘<samp>binutils-2.7.0.2</samp>’.
</p>
<p>Unfortunately, this convention conflicts directly with libtool’s idea of
library interface versions, because the library interface rarely changes
at the same time that the release number does, and the library suffix is
never the same across all platforms.
</p>
<p>So, to accommodate both views, you can use the <samp>-release</samp>
flag to set release information for libraries for which you do not
want to use <samp>-version-info</samp>.  For the <samp>libbfd</samp> example, the
next release that uses libtool should be built with ‘<samp>-release
2.9.0</samp>’, which will produce the following files on GNU/Linux:
</p>
<div class="example">
<pre class="example">trick$ <kbd>ls /usr/lib/libbfd*</kbd>
/usr/lib/libbfd-2.9.0.so     /usr/lib/libbfd.a
/usr/lib/libbfd.so
trick$
</pre></div>

<p>In this case, <samp>/usr/lib/libbfd.so</samp> is a symbolic link to
<samp>libbfd-2.9.0.so</samp>.  This makes it obvious that the user is dealing
with ‘<samp>binutils-2.9.0</samp>’, without compromising libtool’s idea of
interface versions.
</p>
<p>Note that this option causes a modification of the library name, so do
not use it unless you want to break binary compatibility with any past
library releases.  In general, you should only use <samp>-release</samp> for
package-internal libraries or for ones whose interfaces change very
frequently.
</p>
<hr>
<span id="Library-tips"></span><div class="header">
<p>
Next: <a href="#Inter_002dlibrary-dependencies" accesskey="n" rel="next">Inter-library dependencies</a>, Previous: <a href="#Versioning" accesskey="p" rel="prev">Versioning</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Tips-for-interface-design"></span><h2 class="chapter">8 Tips for interface design</h2>
<span id="index-library-interfaces_002c-design"></span>
<span id="index-design-of-library-interfaces"></span>

<p>Writing a good library interface takes a lot of practice and thorough
understanding of the problem that the library is intended to solve.
</p>
<p>If you design a good interface, it won’t have to change often, you won’t
have to keep updating documentation, and users won’t have to keep
relearning how to use the library.
</p>
<p>Here is a brief list of tips for library interface design that may
help you in your exploits:
</p>
<dl compact="compact">
<dt>Plan ahead</dt>
<dd><p>Try to make every interface truly minimal, so that you won’t need to
delete entry points very often.
</p>
</dd>
<dt>Avoid interface changes</dt>
<dd><span id="index-renaming-interface-functions"></span>
<p>Some people love redesigning and changing entry points just for the heck
of it (note: <em>renaming</em> a function is considered changing an entry
point).  Don’t be one of those people.  If you must redesign an
interface, then try to leave compatibility functions behind so that
users don’t need to rewrite their existing code.
</p>
</dd>
<dt>Use opaque data types</dt>
<dd><span id="index-opaque-data-types"></span>
<p>The fewer data type definitions a library user has access to, the
better.  If possible, design your functions to accept a generic pointer
(that you can cast to an internal data type), and provide access
functions rather than allowing the library user to directly manipulate
the data.
That way, you have the freedom to change the data structures without
changing the interface.
</p>
<p>This is essentially the same thing as using abstract data types and
inheritance in an object-oriented system.
</p>
</dd>
<dt>Use header files</dt>
<dd><span id="index-header-files"></span>
<p>If you are careful to document each of your library’s global functions
and variables in header files, and include them in your library source
files, then the compiler will let you know if you make any interface
changes by accident (see <a href="#C-header-files">C header files</a>).
</p>
</dd>
<dt>Use the <code>static</code> keyword (or equivalent) whenever possible</dt>
<dd><span id="index-global-functions"></span>
<p>The fewer global functions your library has, the more flexibility you’ll
have in changing them.  Static functions and variables may change forms
as often as you like… your users cannot access them, so they
aren’t interface changes.
</p>
</dd>
<dt>Be careful with array dimensions</dt>
<dd><p>The number of elements in a global array is part of an interface, even
if the header just declares <code>extern int foo[];</code>.  This is because
on i386 and some other SVR4/ELF systems, when an application
references data in a shared library the size of that data (whatever
its type) is included in the application executable.  If you might
want to change the size of an array or string then provide a pointer
not the actual array.
</p></dd>
</dl>

<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#C-header-files" accesskey="1">C header files</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How to write portable include files.
</td></tr>
</tbody></table>

<hr>
<span id="C-header-files"></span><div class="header">
<p>
Up: <a href="#Library-tips" accesskey="u" rel="up">Library tips</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Writing-C-header-files"></span><h3 class="section">8.1 Writing C header files</h3>
<span id="index-portable-C-headers"></span>
<span id="index-C-header-files_002c-portable"></span>
<span id="index-include-files_002c-portable"></span>

<p>Writing portable C header files can be difficult, since they may be read
by different types of compilers:
</p>
<dl compact="compact">
<dt>C++ compilers</dt>
<dd><p>C++ compilers require that functions be declared with full prototypes,
since C++ is more strongly typed than C.  C functions and variables also
need to be declared with the <code>extern "C"</code> directive, so that the
names aren’t mangled.  See <a href="#C_002b_002b-libraries">C++ libraries</a>, for other issues relevant
to using C++ with libtool.
</p>
</dd>
<dt>ANSI C compilers</dt>
<dd><p>ANSI C compilers are not as strict as C++ compilers, but functions
should be prototyped to avoid unnecessary warnings when the header file
is <code>#include</code>d.
</p>
</dd>
<dt>non-ANSI C compilers</dt>
<dd><p>Non-ANSI compilers will report errors if functions are prototyped.
</p></dd>
</dl>

<p>These complications mean that your library interface headers must use
some C preprocessor magic to be usable by each of the above compilers.
</p>
<p><samp>foo.h</samp> in the <samp>tests/demo</samp> subdirectory of the libtool
distribution serves as an example for how to write a header file that
can be safely installed in a system directory.
</p>
<p>Here are the relevant portions of that file:
</p>
<div class="example">
<pre class="example">/* BEGIN_C_DECLS should be used at the beginning of your declarations,
   so that C++ compilers don't mangle their names.  Use END_C_DECLS at
   the end of C declarations. */
#undef BEGIN_C_DECLS
#undef END_C_DECLS
#ifdef __cplusplus
# define BEGIN_C_DECLS extern "C" {
# define END_C_DECLS }
#else
# define BEGIN_C_DECLS /* empty */
# define END_C_DECLS /* empty */
#endif

/* PARAMS is a macro used to wrap function prototypes, so that
   compilers that don't understand ANSI C prototypes still work,
   and ANSI C compilers can issue warnings about type mismatches. */
#undef PARAMS
#if defined __STDC__ || defined _AIX \
        || (defined __mips &amp;&amp; defined _SYSTYPE_SVR4) \
        || defined WIN32 || defined __cplusplus
# define PARAMS(protos) protos
#else
# define PARAMS(protos) ()
#endif
</pre></div>

<p>These macros are used in <samp>foo.h</samp> as follows:
</p>
<div class="example">
<pre class="example">#ifndef FOO_H
#define FOO_H 1

/* The above macro definitions. */
#include "…"

BEGIN_C_DECLS

int foo PARAMS((void));
int hello PARAMS((void));

END_C_DECLS

#endif /* !FOO_H */
</pre></div>

<p>Note that the <samp>#ifndef FOO_H</samp> prevents the body of <samp>foo.h</samp>
from being read more than once in a given compilation.
</p>
<p>Also the only thing that must go outside the
<code>BEGIN_C_DECLS</code>/<code>END_C_DECLS</code> pair are <code>#include</code> lines.
Strictly speaking it is only C symbol names that need to be protected,
but your header files will be more maintainable if you have a single
pair of these macros around the majority of the header contents.
</p>
<p>You should use these definitions of <code>PARAMS</code>, <code>BEGIN_C_DECLS</code>,
and <code>END_C_DECLS</code> into your own headers.  Then, you may use them to
create header files that are valid for C++, ANSI, and non-ANSI
compilers<a id="DOCF8" href="#FOOT8"><sup>8</sup></a>.
</p>
<p>Do not be naive about writing portable code.  Following the tips given
above will help you miss the most obvious problems, but there are
definitely other subtle portability issues.  You may need to cope with
some of the following issues:
</p>
<ul>
<li> Pre-ANSI compilers do not always support the <code>void *</code> generic
pointer type, and so need to use <code>char *</code> in its place.

</li><li> The <code>const</code>, <code>inline</code> and <code>signed</code> keywords are not
supported by some compilers, especially pre-ANSI compilers.

</li><li> The <code>long double</code> type is not supported by many compilers.
</li></ul>


<hr>
<span id="Inter_002dlibrary-dependencies"></span><div class="header">
<p>
Next: <a href="#Dlopened-modules" accesskey="n" rel="next">Dlopened modules</a>, Previous: <a href="#Library-tips" accesskey="p" rel="prev">Library tips</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Inter_002dlibrary-dependencies-1"></span><h2 class="chapter">9 Inter-library dependencies</h2>
<span id="index-dependencies-between-libraries"></span>
<span id="index-inter_002dlibrary-dependencies"></span>

<p>By definition, every shared library system provides a way for
executables to depend on libraries, so that symbol resolution is
deferred until runtime.
</p>
<p>An <em>inter-library dependency</em> is where a library depends on
other libraries.  For example, if the libtool library <samp>libhello</samp>
uses the <code>cos</code> function, then it has an inter-library dependency
on <samp>libm</samp>, the math library that implements <code>cos</code>.
</p>
<p>Some shared library systems provide this feature in an
internally-consistent way: these systems allow chains of dependencies of
potentially infinite length.
</p>
<p>However, most shared library systems are restricted in that they only
allow a single level of dependencies.  In these systems, programs may
depend on shared libraries, but shared libraries may not depend on other
shared libraries.
</p>
<p>In any event, libtool provides a simple mechanism for you to declare
inter-library dependencies: for every library <samp>lib<var>name</var></samp> that
your own library depends on, simply add a corresponding
<code>-l<var>name</var></code> option to the link line when you create your
library.  To make an example of our <samp>libhello</samp> that depends on
<samp>libm</samp>:
</p>
<div class="example">
<pre class="example">burger$ <kbd>libtool --mode=link gcc -g -O -o libhello.la foo.lo hello.lo \
                -rpath /usr/local/lib -lm</kbd>
burger$
</pre></div>

<p>When you link a program against <samp>libhello</samp>, you don’t need to
specify the same ‘<samp>-l</samp>’ options again: libtool will do that for you,
to guarantee that all the required libraries are found.  This
restriction is only necessary to preserve compatibility with static
library systems and simple dynamic library systems.
</p>
<p>Some platforms, such as Windows, do not even allow you this
flexibility.  In order to build a shared library, it must be entirely
self-contained or it must have dependencies known at link time (that is,
have references only to symbols that are found in the <samp>.lo</samp> files
or the specified ‘<samp>-l</samp>’ libraries), and you need to specify the
<samp>-no-undefined</samp> flag.  By default, libtool builds only static
libraries on these kinds of platforms.
</p>
<p>The simple-minded inter-library dependency tracking code of libtool
releases prior to 1.2 was disabled because it was not clear when it was
possible to link one library with another, and complex failures would
occur.  A more complex implementation of this concept was re-introduced
before release 1.3, but it has not been ported to all platforms that
libtool supports.  The default, conservative behavior is to avoid
linking one library with another, introducing their inter-dependencies
only when a program is linked with them.
</p>
<hr>
<span id="Dlopened-modules"></span><div class="header">
<p>
Next: <a href="#Using-libltdl" accesskey="n" rel="next">Using libltdl</a>, Previous: <a href="#Inter_002dlibrary-dependencies" accesskey="p" rel="prev">Inter-library dependencies</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Dlopened-modules-1"></span><h2 class="chapter">10 Dlopened modules</h2>
<span id="index-dlopen"></span>
<span id="index-dlsym"></span>
<span id="index-dlclose"></span>
<span id="index-shl_005fload"></span>
<span id="index-dynamic-linking_002c-applications"></span>
<span id="index-dlopening-modules"></span>
<span id="index-modules_002c-dynamic"></span>
<span id="index-application_002dlevel-dynamic-linking"></span>

<p>It can sometimes be confusing to discuss <em>dynamic linking</em>, because
the term is used to refer to two different concepts:
</p>
<ol>
<li> Compiling and linking a program against a shared library, which is
resolved automatically at run time by the dynamic linker.  In this
process, dynamic linking is transparent to the application.

</li><li> The application calling functions such as <code>dlopen</code> that load
arbitrary, user-specified modules at runtime.  This type of dynamic
linking is explicitly controlled by the application.
</li></ol>

<p>To mitigate confusion, this manual refers to the second type of dynamic
linking as <em>dlopening</em> a module.
</p>
<p>The main benefit to dlopening object modules is the ability to access
compiled object code to extend your program, rather than using an
interpreted language.  In fact, dlopen calls are frequently used in
language interpreters to provide an efficient way to extend the
language.
</p>
<p>Libtool provides support for dlopened modules.  However, you should
indicate that your package is willing to use such support, by using the
<code>LT_INIT</code> option ‘<samp>dlopen</samp>’ in <samp>configure.ac</samp>.  If this
option is not given, libtool will assume no dlopening mechanism is
available, and will try to simulate it.
</p>
<p>This chapter discusses how you as a dlopen application developer might
use libtool to generate dlopen-accessible modules.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Building-modules" accesskey="1">Building modules</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating dlopenable objects and libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Dlpreopening" accesskey="2">Dlpreopening</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Dlopening that works on static platforms.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Linking-with-dlopened-modules" accesskey="3">Linking with dlopened modules</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Using dlopenable modules in libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Finding-the-dlname" accesskey="4">Finding the dlname</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Choosing the right file to <code>dlopen</code>.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Dlopen-issues" accesskey="5">Dlopen issues</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Unresolved problems that need your attention.
</td></tr>
</tbody></table>

<hr>
<span id="Building-modules"></span><div class="header">
<p>
Next: <a href="#Dlpreopening" accesskey="n" rel="next">Dlpreopening</a>, Up: <a href="#Dlopened-modules" accesskey="u" rel="up">Dlopened modules</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Building-modules-to-dlopen"></span><h3 class="section">10.1 Building modules to dlopen</h3>

<p>On some operating systems, a program symbol must be specially declared
in order to be dynamically resolved with the <code>dlsym</code> (or
equivalent) function.  Libtool provides the <samp>-export-dynamic</samp> and
<samp>-module</samp> link flags (see <a href="#Link-mode">Link mode</a>), for you to make that
declaration.  You need to use these flags if you are linking an
application program that dlopens other modules or a libtool library
that will also be dlopened.
</p>
<p>For example, if we wanted to build a shared library, <samp>hello</samp>,
that would later be dlopened by an application, we would add
<samp>-module</samp> to the other link flags:
</p>
<div class="example">
<pre class="example">burger$ <kbd>libtool --mode=link gcc -module -o hello.la foo.lo \
                hello.lo -rpath /usr/local/lib -lm</kbd>
burger$
</pre></div>

<p>If symbols from your <em>executable</em> are needed to satisfy unresolved
references in a library you want to dlopen you will have to use the flag
<samp>-export-dynamic</samp>.  You should use <samp>-export-dynamic</samp> while
linking the executable that calls dlopen:
</p>
<div class="example">
<pre class="example">burger$ <kbd>libtool --mode=link gcc -export-dynamic -o helldl main.o</kbd>
burger$
</pre></div>

<hr>
<span id="Dlpreopening"></span><div class="header">
<p>
Next: <a href="#Linking-with-dlopened-modules" accesskey="n" rel="next">Linking with dlopened modules</a>, Previous: <a href="#Building-modules" accesskey="p" rel="prev">Building modules</a>, Up: <a href="#Dlopened-modules" accesskey="u" rel="up">Dlopened modules</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Dlpreopening-1"></span><h3 class="section">10.2 Dlpreopening</h3>

<p>Libtool provides special support for dlopening libtool object and
libtool library files, so that their symbols can be resolved
<em>even on platforms without any <code>dlopen</code> and <code>dlsym</code>
functions</em>.
</p>
<p>Consider the following alternative ways of loading code into your
program, in order of increasing “laziness”:
</p>
<ol>
<li> Linking against object files that become part of the program executable,
whether or not they are referenced.  If an object file cannot be found,
then the compile time linker refuses to create the executable.

</li><li> Declaring a static library to the linker, so that it is searched at link
time to satisfy any undefined references in the above object
files.  If the static library cannot be found, then the compile time
linker refuses to create the executable.

</li><li> Declaring a shared library to the runtime linker, so that it is searched
at runtime to satisfy any undefined references in the above
files.  If the shared library cannot be found, then the dynamic linker
aborts the program before it runs.

</li><li> Dlopening a module, so that the application can resolve its own,
dynamically-computed references.  If there is an error opening the
module, or the module is not found, then the application can recover
without crashing.
</li></ol>

<p>Libtool emulates <samp>-dlopen</samp> on static platforms by linking objects
into the program at compile time, and creating data structures that
represent the program’s symbol table.  In order to use this feature,
you must declare the objects you want your application to dlopen by
using the <samp>-dlopen</samp> or <samp>-dlpreopen</samp> flags when you link your
program (see <a href="#Link-mode">Link mode</a>).
</p>
<dl>
<dt id="index-lt_005fdlsymlist">Data Type: <strong>lt_dlsymlist</strong> <em>typedef struct   { const&nbsp;char&nbsp;*<var>name</var>;<!-- /@w --> void&nbsp;*<var>address</var>;<!-- /@w --> } lt_dlsymlist</em></dt>
<dd><p>The <var>name</var> attribute is a null-terminated character string of the
symbol name, such as <code>"fprintf"</code>.  The <var>address</var> attribute is a
generic pointer to the appropriate object, such as <code>&amp;fprintf</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fpreloaded_005fsymbols_005b_005d">Variable: <em>const lt_dlsymlist</em> <strong>lt_preloaded_symbols[]</strong></dt>
<dd><p>An array of <code>lt_dlsymlist</code> structures, representing all the preloaded
symbols linked into the program proper.  For each module
<samp>-dlpreopen</samp>ed by the Libtool linked program
there is an element with the <var>name</var> of the module and an <var>address</var>
of <code>0</code>, followed by all symbols exported from this file.
For the executable itself the special name ‘<samp>@PROGRAM@</samp>’ is used.
The last element of all has a <var>name</var> and <var>address</var> of
<code>0</code>.
</p>
<p>To facilitate inclusion of symbol lists into libraries,
<code>lt_preloaded_symbols</code> is ‘<samp>#define</samp>’d to a suitably unique name
in <samp>ltdl.h</samp>.
</p>
<p>This variable may not be declared <code>const</code> on some systems due to
relocation issues.
</p></dd></dl>

<p>Some compilers may allow identifiers that are not valid in ANSI C, such
as dollar signs.  Libtool only recognizes valid ANSI C symbols (an
initial ASCII letter or underscore, followed by zero or more ASCII
letters, digits, and underscores), so non-ANSI symbols will not appear
in <code>lt_preloaded_symbols</code>.
</p>
<dl>
<dt id="index-lt_005fdlpreload">Function: <em>int</em> <strong>lt_dlpreload</strong> <em>(const lt_dlsymlist *<var>preloaded</var>)</em></dt>
<dd><p>Register the list of preloaded modules <var>preloaded</var>.
If <var>preloaded</var> is <code>NULL</code>, then all previously registered
symbol lists, except the list set by <code>lt_dlpreload_default</code>,
are deleted.  Return 0 on success.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlpreload_005fdefault">Function: <em>int</em> <strong>lt_dlpreload_default</strong> <em>(const lt_dlsymlist *<var>preloaded</var>)</em></dt>
<dd><p>Set the default list of preloaded modules to <var>preloaded</var>, which
won’t be deleted by <code>lt_dlpreload</code>.  Note that this function does
<em>not</em> require libltdl to be initialized using <code>lt_dlinit</code> and
can be used in the program to register the default preloaded modules.
Instead of calling this function directly, most programs will use the
macro <code>LTDL_SET_PRELOADED_SYMBOLS</code>.
</p>
<p>Return 0 on success.
</p></dd></dl>

<dl>
<dt id="index-LTDL_005fSET_005fPRELOADED_005fSYMBOLS">Macro: <strong>LTDL_SET_PRELOADED_SYMBOLS</strong></dt>
<dd><p>Set the default list of preloaded symbols.
Should be used in your program to initialize libltdl’s
list of preloaded modules.
</p>
<div class="example">
<pre class="example">#include &lt;ltdl.h&gt;

int main() {
  /* ... */
  LTDL_SET_PRELOADED_SYMBOLS();
  /* ... */
}
</pre></div>
</dd></dl>

<dl>
<dt id="index-lt_005fdlpreload_005fcallback_005ffunc">Function Type: <em>int</em> <strong>lt_dlpreload_callback_func</strong> <em>(lt_dlhandle <var>handle</var>)</em></dt>
<dd><p>Functions of this type can be passed to <code>lt_dlpreload_open</code>,
which in turn will call back into a function thus passed for each
preloaded module that it opens.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlpreload_005fopen">Function: <em>int</em> <strong>lt_dlpreload_open</strong> <em>(const&nbsp;char&nbsp;*<var>originator</var>,<!-- /@w --> <span class="nolinebreak">lt_dlpreload_callback_func</span>&nbsp;*<var>func</var>)<!-- /@w --></em></dt>
<dd><p>Load all of the preloaded modules for <var>originator</var>.  For every
module opened in this way, call <var>func</var>.
</p>
<p>To open all of the modules preloaded into <samp>libhell.la</samp>
(presumably from within the <samp>libhell.a</samp> initialisation code):
</p>
<div class="example">
<pre class="example">#define preloaded_symbols lt_libhell_LTX_preloaded_symbols

static int hell_preload_callback (lt_dlhandle handle);

int
hell_init (void)
{
  …
  if (lt_dlpreload (&amp;preloaded_symbols) == 0)
    {
      lt_dlpreload_open ("libhell", preload_callback);
    }
  …
}
</pre></div>

<p>Note that to prevent clashes between multiple preloaded modules, the
preloaded symbols are accessed via a mangled symbol name: to get the
symbols preloaded into ‘<samp>libhell</samp>’, you must prefix
‘<samp>preloaded_symbols</samp>’ with ‘<samp>lt_</samp>’; the originator name,
‘<samp>libhell</samp>’ in this case; and ‘<samp>_LTX_</samp>’.  That is,
‘<samp>lt_libhell_LTX_preloaded_symbols</samp>’ here.
</p></dd></dl>


<hr>
<span id="Linking-with-dlopened-modules"></span><div class="header">
<p>
Next: <a href="#Finding-the-dlname" accesskey="n" rel="next">Finding the dlname</a>, Previous: <a href="#Dlpreopening" accesskey="p" rel="prev">Dlpreopening</a>, Up: <a href="#Dlopened-modules" accesskey="u" rel="up">Dlopened modules</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Linking-with-dlopened-modules-1"></span><h3 class="section">10.3 Linking with dlopened modules</h3>
<span id="index-linking_002c-dlopen"></span>
<span id="index-linking_002c-dlpreopen"></span>

<p>When, say, an interpreter application uses dlopened modules to extend
the list of methods it provides, an obvious abstraction for the
maintainers of the interpreter is to have all methods (including the
built in ones supplied with the interpreter) accessed through
dlopen.  For one thing, the dlopening functionality will be tested
even during routine invocations.  For another, only one subsystem has
to be written for getting methods into the interpreter.
</p>
<p>The downside of this abstraction is, of course, that environments that
provide only static linkage can’t even load the intrinsic interpreter
methods.  Not so!  We can statically link those methods by
<strong>dlpreopening</strong> them.
</p>
<p>Unfortunately, since platforms such as AIX and cygwin require
that all library symbols must be resolved at compile time, the
interpreter maintainers will need to provide a library to both its own
dlpreopened modules, and third-party modules loaded by dlopen.  In
itself, that is not so bad, except that the interpreter too must
provide those same symbols otherwise it will be impossible to resolve
all the symbols required by the modules as they are loaded.  Things
are even worse if the code that loads the modules for the interpreter
is itself in a library – and that is usually the case for any
non-trivial application.  Modern platforms take care of this by
automatically loading all of a module’s dependency libraries as the
module is loaded (libltdl can do this even on platforms that can’t do
it by themselves).  In the end, this leads to problems with duplicated
symbols and prevents modules from loading, and prevents the
application from compiling when modules are preloaded.
</p>
<div class="example">
<pre class="example">,-------------.    ,------------------.    ,-----------------.
| Interpreter |----&gt;     Module------------&gt;   Third-party   |
`-------------'    |     Loader       |    |Dlopened Modules |
                   |        |         |    `-----------------'
                   |,-------v--------.|             |
                   ||  Dlpreopened   ||             |
                   ||    Modules     ||             |
                   |`----------------'|             |
                   |        |         |             |
                   |,-------v--------.|    ,--------v--------.
                   ||Module Interface||    |Module Interface |
                   ||    Library     ||    |     Library     |
                   |`----------------'|    `-----------------'
                   `------------------'
</pre></div>

<p>Libtool has the concept of <em>weak library interfaces</em> to circumvent
this problem.  Recall that the code that dlopens method-provider
modules for the interpreter application resides in a library: All of
the modules and the dlopener library itself should be linked against
the common library that resolves the module symbols at compile time.
To guard against duplicate symbol definitions, and for dlpreopened
modules to work at all in this scenario, the dlopener library must
declare that it provides a weak library interface to the common
symbols in the library it shares with the modules.  That way, when
<code>libtool</code> links the <strong>Module Loader</strong> library with some
<strong>Dlpreopened Modules</strong> that were in turn linked against the
<strong>Module Interface Library</strong>, it knows that the <strong>Module
Loader</strong> provides an already loaded <strong>Module Interface Library</strong>
to resolve symbols for the <strong>Dlpreopened Modules</strong>, and doesn’t
ask the compiler driver to link an identical <strong>Module Interface
Library</strong> dependency library too.
</p>
<p>In conjunction with Automake, the <samp>Makefile.am</samp> for the
<strong>Module Loader</strong> might look like this:
</p>
<div class="example">
<pre class="example">lib_LTLIBRARIES = libinterface.la libloader.la

libinterface_la_SOURCES = interface.c interface.h
libinterface_la_LDFLAGS = -version-info 3:2:1

libloader_la_SOURCES    = loader.c
libloader_la_LDFLAGS    = -weak libinterface.la \
                          -version-info 3:2:1 \
                          -dlpreopen ../modules/intrinsics.la
libloader_la_LIBADD     = $(libinterface_la_OBJECTS)
</pre></div>

<p>And the <samp>Makefile.am</samp> for the <samp>intrinsics.la</samp> module in a
sibling <samp>modules</samp> directory might look like this:
</p>
<div class="example">
<pre class="example">AM_CPPFLAGS             = -I$(srcdir)/../libloader
AM_LDFLAGS              = -no-undefined -module -avoid-version \
                          -export-dynamic

noinst_LTLIBRARIES      = intrinsics.la

intrinsics_la_LIBADD    = ../libloader/libinterface.la

../libloader/libinterface.la:
        cd ../libloader &amp;&amp; $(MAKE) $(AM_MAKEFLAGS) libinterface.la
</pre></div>

<span id="index-_002dweak-option"></span>
<p>For a more complex example, see the sources of <samp>libltdl</samp> in the
Libtool distribution, which is built with the help of the <samp>-weak</samp>
option.
</p>

<hr>
<span id="Finding-the-dlname"></span><div class="header">
<p>
Next: <a href="#Dlopen-issues" accesskey="n" rel="next">Dlopen issues</a>, Previous: <a href="#Linking-with-dlopened-modules" accesskey="p" rel="prev">Linking with dlopened modules</a>, Up: <a href="#Dlopened-modules" accesskey="u" rel="up">Dlopened modules</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Finding-the-correct-name-to-dlopen"></span><h3 class="section">10.4 Finding the correct name to dlopen</h3>
<span id="index-names-of-dynamic-modules"></span>
<span id="index-dynamic-modules_002c-names"></span>

<p>After a library has been linked with <samp>-module</samp>, it can be dlopened.
Unfortunately, because of the variation in library names,
your package needs to determine the correct file to dlopen.
</p>
<p>The most straightforward and flexible implementation is to determine the
name at runtime, by finding the installed <samp>.la</samp> file, and searching
it for the following lines:
</p>
<div class="example">
<pre class="example"># The name that we can <code>dlopen</code>.
dlname='<var>dlname</var>'
</pre></div>

<p>If <var>dlname</var> is empty, then the library cannot be dlopened.
Otherwise, it gives the dlname of the library.  So, if the library was
installed as <samp>/usr/local/lib/libhello.la</samp>, and the <var>dlname</var> was
<samp>libhello.so.3</samp>, then <samp>/usr/local/lib/libhello.so.3</samp> should be
dlopened.
</p>
<p>If your program uses this approach, then it should search the
directories listed in the <code>LD_LIBRARY_PATH</code><a id="DOCF9" href="#FOOT9"><sup>9</sup></a> environment variable, as well as
the directory where libraries will eventually be installed.  Searching
this variable (or equivalent) will guarantee that your program can find
its dlopened modules, even before installation, provided you have linked
them using libtool.
</p>
<hr>
<span id="Dlopen-issues"></span><div class="header">
<p>
Previous: <a href="#Finding-the-dlname" accesskey="p" rel="prev">Finding the dlname</a>, Up: <a href="#Dlopened-modules" accesskey="u" rel="up">Dlopened modules</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Unresolved-dlopen-issues"></span><h3 class="section">10.5 Unresolved dlopen issues</h3>
<span id="index-pitfalls-with-dlopen"></span>
<span id="index-dlopening_002c-pitfalls"></span>
<span id="index-trouble-with-dlopen"></span>

<p>The following problems are not solved by using libtool’s dlopen support:
</p>
<ul>
<li> Dlopen functions are generally only available on shared library
platforms.  If you want your package to be portable to static platforms,
you have to use either libltdl (see <a href="#Using-libltdl">Using libltdl</a>) or develop your
own alternatives to dlopening dynamic code.
Most reasonable solutions involve writing wrapper functions for the
<code>dlopen</code> family, which do package-specific tricks when dlopening
is unsupported or not available on a given platform.

</li><li> There are major differences in implementations of the <code>dlopen</code>
family of functions.  Some platforms do not even use the same function
names (notably HP-UX, with its <code>shl_load</code> family).

</li><li> The application developer must write a custom search function
to discover the correct module filename to supply to <code>dlopen</code>.
</li></ul>

<hr>
<span id="Using-libltdl"></span><div class="header">
<p>
Next: <a href="#Trace-interface" accesskey="n" rel="next">Trace interface</a>, Previous: <a href="#Dlopened-modules" accesskey="p" rel="prev">Dlopened modules</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Using-libltdl-1"></span><h2 class="chapter">11 Using libltdl</h2>
<span id="index-libltdl"></span>
<span id="index-dlopen-1"></span>
<span id="index-dlsym-1"></span>
<span id="index-dlclose-1"></span>
<span id="index-dlerror"></span>
<span id="index-shl_005fload-1"></span>
<span id="index-dynamic-linking_002c-applications-1"></span>
<span id="index-dlopening-modules-1"></span>
<span id="index-modules_002c-dynamic-1"></span>
<span id="index-application_002dlevel-dynamic-linking-1"></span>

<p>Libtool provides a small library, called <samp>libltdl</samp>, that aims at
hiding the various difficulties of dlopening libraries from programmers.
It consists of a few headers and small C source files that can be
distributed with applications that need dlopening functionality.  On
some platforms, whose dynamic linkers are too limited for a simple
implementation of <samp>libltdl</samp> services, it requires GNU DLD, or it
will only emulate dynamic linking with libtool’s dlpreopening mechanism.
</p>
<p>libltdl supports currently the following dynamic linking mechanisms:
</p>
<ul>
<li> <code>dlopen</code> (POSIX compliant systems, GNU/Linux, etc.)
</li><li> <code>shl_load</code> (HP-UX)
</li><li> <code>LoadLibrary</code> (Win16 and Win32)
</li><li> <code>load_add_on</code> (BeOS)
</li><li> <code>NSAddImage</code> or <code>NSLinkModule</code> (Darwin and Mac OS X)
</li><li> GNU DLD (emulates dynamic linking for static libraries)
</li><li> libtool’s dlpreopen (see <a href="#Dlpreopening">Dlpreopening</a>)
</li></ul>

<p>libltdl is licensed under the terms of the GNU Lesser General
Public License, with the following exception:
</p>
<blockquote>
<p>As a special exception to the GNU Lesser General Public License,
if you distribute this file as part of a program or library that
is built using GNU Libtool, you may include it under the same
distribution terms that you use for the rest of that program.
</p></blockquote>

<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Libltdl-interface" accesskey="1">Libltdl interface</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How to use libltdl in your programs.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Modules-for-libltdl" accesskey="2">Modules for libltdl</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating modules that can be <code>dlopen</code>ed.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Thread-Safety-in-libltdl" accesskey="3">Thread Safety in libltdl</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Registering callbacks for multi-thread safety.
</td></tr>
<tr><td align="left" valign="top">• <a href="#User-defined-module-data" accesskey="4">User defined module data</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Associating data with loaded modules.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Module-loaders-for-libltdl" accesskey="5">Module loaders for libltdl</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating user defined module loaders.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Distributing-libltdl" accesskey="6">Distributing libltdl</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How to distribute libltdl with your package.
</td></tr>
</tbody></table>

<hr>
<span id="Libltdl-interface"></span><div class="header">
<p>
Next: <a href="#Modules-for-libltdl" accesskey="n" rel="next">Modules for libltdl</a>, Up: <a href="#Using-libltdl" accesskey="u" rel="up">Using libltdl</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="How-to-use-libltdl-in-your-programs"></span><h3 class="section">11.1 How to use libltdl in your programs</h3>

<p>The libltdl API is similar to the POSIX dlopen interface,
which is very simple but powerful.
</p>
<p>To use libltdl in your program you have to include the header file <samp>ltdl.h</samp>:
</p>
<div class="example">
<pre class="example">#include &lt;ltdl.h&gt;
</pre></div>

<p>The early releases of libltdl used some symbols that violated the
POSIX namespace conventions.  These symbols are now deprecated,
and have been replaced by those described here.  If you have code that
relies on the old deprecated symbol names, defining
‘<samp>LT_NON_POSIX_NAMESPACE</samp>’ before you include <samp>ltdl.h</samp> provides
conversion macros.  Whichever set of symbols you use, the new API is
not binary compatible with the last, so you will need to recompile
your application to use this version of libltdl.
</p>
<p>Note that libltdl is not well tested in a multithreaded environment,
though the intention is that it should work (see <a href="#Thread-Safety-in-libltdl">Using libltdl in a multi threaded environment</a>).  It was
reported that GNU/Linux’s glibc 2.0’s <code>dlopen</code> with
‘<samp>RTLD_LAZY</samp>’ (that libltdl uses by default) is not thread-safe,
but this problem is supposed to be fixed in glibc 2.1.  On the other
hand, ‘<samp>RTLD_NOW</samp>’ was reported to introduce problems in
multi-threaded applications on FreeBSD.  Working around these problems
is left as an exercise for the reader; contributions are certainly
welcome.
</p>
<p>The following macros are defined by including <samp>ltdl.h</samp>:
</p>
<dl>
<dt id="index-LT_005fPATHSEP_005fCHAR">Macro: <strong>LT_PATHSEP_CHAR</strong></dt>
<dd><p><code>LT_PATHSEP_CHAR</code> is the system-dependent path separator,
that is, ‘<samp>;</samp>’ on Windows and ‘<samp>:</samp>’ everywhere else.
</p></dd></dl>

<dl>
<dt id="index-LT_005fDIRSEP_005fCHAR">Macro: <strong>LT_DIRSEP_CHAR</strong></dt>
<dd><p>If <code>LT_DIRSEP_CHAR</code> is defined, it can be used as directory
separator in addition to ‘<samp>/</samp>’.  On Windows, this contains
‘<samp>\</samp>’.
</p></dd></dl>


<p>The following types are defined in <samp>ltdl.h</samp>:
</p>
<dl>
<dt id="index-lt_005fdlhandle">Type: <strong>lt_dlhandle</strong></dt>
<dd><p><code>lt_dlhandle</code> is a module “handle”.
Every lt_dlopened module has a handle associated with it.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdladvise">Type: <strong>lt_dladvise</strong></dt>
<dd><p><code>lt_dladvise</code> is used to control optional module loading modes.
If it is not used, the default mode of the underlying system module
loader is used.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlsymlist-1">Type: <strong>lt_dlsymlist</strong></dt>
<dd><p><code>lt_dlsymlist</code> is a symbol list for dlpreopened modules
(see <a href="#Dlpreopening">Dlpreopening</a>).
</p></dd></dl>

<p>libltdl provides the following functions:
</p>
<dl>
<dt id="index-lt_005fdlinit">Function: <em>int</em> <strong>lt_dlinit</strong> <em>(void)</em></dt>
<dd><p>Initialize libltdl.
This function must be called before using libltdl
and may be called several times.
Return 0 on success, otherwise the number of errors.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlexit">Function: <em>int</em> <strong>lt_dlexit</strong> <em>(void)</em></dt>
<dd><p>Shut down libltdl and close all modules.
This function will only then shut down libltdl when it was called as
many times as <code>lt_dlinit</code> has been successfully called.
Return 0 on success, otherwise the number of errors.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlopen">Function: <em>lt_dlhandle</em> <strong>lt_dlopen</strong> <em>(const char *<var>filename</var>)</em></dt>
<dd><p>Open the module with the file name <var>filename</var> and return a
handle for it.  <code>lt_dlopen</code> is able to open libtool dynamic
modules, preloaded static modules, the program itself and
native dynamic modules<a id="DOCF10" href="#FOOT10"><sup>10</sup></a>.
</p>
<p>Unresolved symbols in the module are resolved using its dependency
libraries and previously dlopened modules.  If the executable using
this module was linked with the <samp>-export-dynamic</samp> flag, then the
global symbols in the executable will also be used to resolve
references in the module.
</p>
<p>If <var>filename</var> is <code>NULL</code> and the program was linked with
<samp>-export-dynamic</samp> or <samp>-dlopen self</samp>, <code>lt_dlopen</code> will
return a handle for the program itself, which can be used to access its
symbols.
</p>
<p>If libltdl cannot find the library and the file name <var>filename</var> does
not have a directory component it will additionally look in the
following search paths for the module (in the following order):
</p>
<ol>
<li> user-defined search path:
This search path can be changed by the program using the
functions <code>lt_dlsetsearchpath</code>, <code>lt_dladdsearchdir</code> and
<code>lt_dlinsertsearchdir</code>.

</li><li> libltdl’s search path:
This search path is the value of the environment variable
<code>LTDL_LIBRARY_PATH</code>.

</li><li> system library search path:
The system dependent library search path
(e.g. on GNU/Linux it is <code>LD_LIBRARY_PATH</code>).
</li></ol>

<p>Each search path must be a list of absolute directories separated by
<code>LT_PATHSEP_CHAR</code>, for example, <code>"/usr/lib/mypkg:/lib/foo"</code>.
The directory names may not contain the path separator.
</p>
<p>If the same module is loaded several times, the same handle is returned.
If <code>lt_dlopen</code> fails for any reason, it returns <code>NULL</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlopenext">Function: <em>lt_dlhandle</em> <strong>lt_dlopenext</strong> <em>(const char *<var>filename</var>)</em></dt>
<dd><p>The same as <code>lt_dlopen</code>, except that it tries to append
different file name extensions to the file name.
If the file with the file name <var>filename</var> cannot be found
libltdl tries to append the following extensions:
</p>
<ol>
<li> the libtool archive extension <samp>.la</samp>
</li><li> the extension used for native dynamically loadable modules on the host platform, e.g., <samp>.so</samp>, <samp>.sl</samp>, etc.
</li></ol>

<p>This lookup strategy was designed to allow programs that don’t
have knowledge about native dynamic libraries naming conventions
to be able to <code>dlopen</code> such libraries as well as libtool modules
transparently.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlopenadvise">Function: <em>lt_dlhandle</em> <strong>lt_dlopenadvise</strong> <em>(const char *<var>filename</var>, <span class="nolinebreak">lt_dladvise</span>&nbsp;<var>advise</var><!-- /@w -->)</em></dt>
<dd><p>The same as <code>lt_dlopen</code>, except that it also requires an additional
argument that may contain additional hints to the underlying system
module loader.  The <var>advise</var> parameter is opaque and can only be
accessed with the functions documented below.
</p>
<p>Note that this function does not change the content of <var>advise</var>, so
unlike the other calls in this API takes a direct <code>lt_dladvise</code>
type, and not a pointer to the same.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdladvise_005finit">Function: <em>int</em> <strong>lt_dladvise_init</strong> <em>(lt_dladvise *<var>advise</var>)</em></dt>
<dd><p>The <var>advise</var> parameter can be used to pass hints to the module
loader when using <code>lt_dlopenadvise</code> to perform the loading.
The <var>advise</var> parameter needs to be initialised by this function
before it can be used.  Any memory used by <var>advise</var> needs to be
recycled with <code>lt_dladvise_destroy</code> when it is no longer needed.
</p>
<p>On failure, <code>lt_dladvise_init</code> returns non-zero and sets an error
message that can be retrieved with <code>lt_dlerror</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdladvise_005fdestroy">Function: <em>int</em> <strong>lt_dladvise_destroy</strong> <em>(lt_dladvise *<var>advise</var>)</em></dt>
<dd><p>Recycle the memory used by <var>advise</var>.  For an example, see the
documentation for <code>lt_dladvise_ext</code>.
</p>
<p>On failure, <code>lt_dladvise_destroy</code> returns non-zero and sets an error
message that can be retrieved with <code>lt_dlerror</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdladvise_005fext">Function: <em>int</em> <strong>lt_dladvise_ext</strong> <em>(lt_dladvise *<var>advise</var>)</em></dt>
<dd><p>Set the <code>ext</code> hint on <var>advise</var>.  Passing an <var>advise</var>
parameter to <code>lt_dlopenadvise</code> with this hint set causes it to
try to append different file name extensions like <code>lt_dlopenext</code>.
</p>
<p>The following example is equivalent to calling
<code>lt_dlopenext (filename)</code>:
</p>
<div class="example">
<pre class="example">lt_dlhandle
my_dlopenext (const char *filename)
{
  lt_dlhandle handle = 0;
  lt_dladvise advise;

  if (!lt_dladvise_init (&amp;advise) &amp;&amp; !lt_dladvise_ext (&amp;advise))
    handle = lt_dlopenadvise (filename, advise);

  lt_dladvise_destroy (&amp;advise);

  return handle;
}
</pre></div>

<p>On failure, <code>lt_dladvise_ext</code> returns non-zero and sets an error
message that can be retrieved with <code>lt_dlerror</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdladvise_005fglobal">Function: <em>int</em> <strong>lt_dladvise_global</strong> <em>(lt_dladvise *<var>advise</var>)</em></dt>
<dd><p>Set the <code>symglobal</code> hint on <var>advise</var>.  Passing an <var>advise</var>
parameter to <code>lt_dlopenadvise</code> with this hint set causes it to try
to make the loaded module’s symbols globally available for resolving
unresolved symbols in subsequently loaded modules.
</p>
<p>If neither the <code>symglobal</code> nor the <code>symlocal</code> hints are set,
or if a module is loaded without using the <code>lt_dlopenadvise</code> call
in any case, then the visibility of the module’s symbols will be as per
the default for the underlying module loader and OS.  Even if a
suitable hint is passed, not all loaders are able to act upon it in
which case <code>lt_dlgetinfo</code> will reveal whether the hint was actually
followed.
</p>
<p>On failure, <code>lt_dladvise_global</code> returns non-zero and sets an error
message that can be retrieved with <code>lt_dlerror</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdladvise_005flocal">Function: <em>int</em> <strong>lt_dladvise_local</strong> <em>(lt_dladvise *<var>advise</var>)</em></dt>
<dd><p>Set the <code>symlocal</code> hint on <var>advise</var>.  Passing an <var>advise</var>
parameter to <code>lt_dlopenadvise</code> with this hint set causes it to try
to keep the loaded module’s symbols hidden so that they are not
visible to subsequently loaded modules.
</p>
<p>If neither the <code>symglobal</code> nor the <code>symlocal</code> hints are set,
or if a module is loaded without using the <code>lt_dlopenadvise</code> call
in any case, then the visibility of the module’s symbols will be as per
the default for the underlying module loader and OS.  Even if a
suitable hint is passed, not all loaders are able to act upon it in
which case <code>lt_dlgetinfo</code> will reveal whether the hint was actually
followed.
</p>
<p>On failure, <code>lt_dladvise_local</code> returns non-zero and sets an error
message that can be retrieved with <code>lt_dlerror</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdladvise_005fresident">Function: <em>int</em> <strong>lt_dladvise_resident</strong> <em>(lt_dladvise *<var>advise</var>)</em></dt>
<dd><p>Set the <code>resident</code> hint on <var>advise</var>.  Passing an <var>advise</var>
parameter to <code>lt_dlopenadvise</code> with this hint set causes it to try
to make the loaded module resident in memory, so that it cannot be
unloaded with a later call to <code>lt_dlclose</code>.
</p>
<p>On failure, <code>lt_dladvise_resident</code> returns non-zero and sets an error
message that can be retrieved with <code>lt_dlerror</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdladvise_005fpreload">Function: <em>int</em> <strong>lt_dladvise_preload</strong> <em>(lt_dladvise *<var>advise</var>)</em></dt>
<dd><p>Set the <code>preload</code> hint on <var>advise</var>.  Passing an <var>advise</var>
parameter to <code>lt_dlopenadvise</code> with this hint set causes it to
load only preloaded modules, so that if a suitable preloaded module is
not found, <code>lt_dlopenadvise</code> will return <code>NULL</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlclose">Function: <em>int</em> <strong>lt_dlclose</strong> <em>(lt_dlhandle <var>handle</var>)</em></dt>
<dd><p>Decrement the reference count on the module <var>handle</var>.
If it drops to zero and no other module depends on this module,
then the module is unloaded.
Return 0 on success.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlsym">Function: <em>void *</em> <strong>lt_dlsym</strong> <em>(lt_dlhandle <var>handle</var>, const char *<var>name</var>)</em></dt>
<dd><p>Return the address in the module <var>handle</var>, where the symbol given
by the null-terminated string <var>name</var> is loaded.
If the symbol cannot be found, <code>NULL</code> is returned.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlerror">Function: <em>const char *</em> <strong>lt_dlerror</strong> <em>(void)</em></dt>
<dd><p>Return a human readable string describing the most
recent error that occurred from any of libltdl’s functions.
Return <code>NULL</code> if no errors have occurred since initialization
or since it was last called.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdladdsearchdir">Function: <em>int</em> <strong>lt_dladdsearchdir</strong> <em>(const char *<var>search_dir</var>)</em></dt>
<dd><p>Append the search directory <var>search_dir</var> to the current user-defined
library search path.  Return 0 on success.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlinsertsearchdir">Function: <em>int</em> <strong>lt_dlinsertsearchdir</strong> <em>(const&nbsp;char&nbsp;*<var>before</var><!-- /@w -->, const&nbsp;char&nbsp;*<var><span class="nolinebreak">search_dir</span></var><!-- /@w -->)</em></dt>
<dd><p>Insert the search directory <var>search_dir</var> into the user-defined library
search path, immediately before the element starting at address
<var>before</var>.  If <var>before</var> is ‘<samp>NULL</samp>’, then <var>search_dir</var> is
appending as if <code>lt_dladdsearchdir</code> had been called.  Return 0 on success.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlsetsearchpath">Function: <em>int</em> <strong>lt_dlsetsearchpath</strong> <em>(const char *<var>search_path</var>)</em></dt>
<dd><p>Replace the current user-defined library search path with
<var>search_path</var>, which must be a list of absolute directories separated
by <code>LT_PATHSEP_CHAR</code>.  Return 0 on success.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlgetsearchpath">Function: <em>const char *</em> <strong>lt_dlgetsearchpath</strong> <em>(void)</em></dt>
<dd><p>Return the current user-defined library search path.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlforeachfile">Function: <em>int</em> <strong>lt_dlforeachfile</strong> <em>(const&nbsp;char&nbsp;*<var><span class="nolinebreak">search_path</span></var><!-- /@w -->, int&nbsp;(*<var>func</var>)&nbsp;(const&nbsp;char&nbsp;*<var>filename</var>,&nbsp;void&nbsp;*&nbsp;<var>data</var>)<!-- /@w -->, void&nbsp;*&nbsp;<var>data</var><!-- /@w -->)</em></dt>
<dd><p>In some applications you may not want to load individual modules with
known names, but rather find all of the modules in a set of
directories and load them all during initialisation.  With this function
you can have libltdl scan the <code>LT_PATHSEP_CHAR</code>-delimited directory list
in <var>search_path</var> for candidates, and pass them, along with
<var>data</var> to your own callback function, <var>func</var>.  If <var>search_path</var> is
‘<samp>NULL</samp>’, then search all of the standard locations that
<code>lt_dlopen</code> would examine.  This function will continue to make
calls to <var>func</var> for each file that it discovers in <var>search_path</var>
until one of these calls returns non-zero, or until the files are
exhausted.  ‘<samp>lt_dlforeachfile</samp>’ returns the value returned by the last
call made to <var>func</var>.
</p>
<p>For example you could define <var>func</var> to build an ordered
<em>argv</em>-like vector of files using <var>data</var> to hold the address of
the start of the vector.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlmakeresident">Function: <em>int</em> <strong>lt_dlmakeresident</strong> <em>(lt_dlhandle <var>handle</var>)</em></dt>
<dd><p>Mark a module so that it cannot be ‘<samp>lt_dlclose</samp>’d.  This can be
useful if a module implements some core functionality in your project
that would cause your code to crash if removed.  Return 0 on success.
</p>
<p>If you use ‘<samp>lt_dlopen (NULL)</samp>’ to get a <var>handle</var> for the running
binary, that handle will always be marked as resident, and consequently
cannot be successfully ‘<samp>lt_dlclose</samp>’d.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlisresident">Function: <em>int</em> <strong>lt_dlisresident</strong> <em>(lt_dlhandle <var>handle</var>)</em></dt>
<dd><p>Check whether a particular module has been marked as resident, returning 1
if it has or 0 otherwise.  If there is an error while executing this
function, return -1 and set an error message for retrieval with
<code>lt_dlerror</code>.
</p></dd></dl>

<hr>
<span id="Modules-for-libltdl"></span><div class="header">
<p>
Next: <a href="#Thread-Safety-in-libltdl" accesskey="n" rel="next">Thread Safety in libltdl</a>, Previous: <a href="#Libltdl-interface" accesskey="p" rel="prev">Libltdl interface</a>, Up: <a href="#Using-libltdl" accesskey="u" rel="up">Using libltdl</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Creating-modules-that-can-be-dlopened"></span><h3 class="section">11.2 Creating modules that can be <code>dlopen</code>ed</h3>

<p>Libtool modules are created like normal libtool libraries with a few
exceptions:
</p>
<p>You have to link the module with libtool’s <samp>-module</samp> switch,
and you should link any program that is intended to dlopen the module with
<samp>-dlopen <var>modulename.la</var></samp> where possible, so that libtool can
dlpreopen the module on platforms that do not support dlopening.  If
the module depends on any other libraries, make sure you specify them
either when you link the module or when you link programs that dlopen it.
If you want to disable versioning (see <a href="#Versioning">Versioning</a>) for a specific module
you should link it with the <samp>-avoid-version</samp> switch.
Note that libtool modules don’t need to have a "lib" prefix.
However, Automake 1.4 or higher is required to build such modules.
</p>
<p>Usually a set of modules provide the same interface, i.e. exports the same
symbols, so that a program can dlopen them without having to know more
about their internals: In order to avoid symbol conflicts all exported
symbols must be prefixed with "modulename_LTX_" (<var>modulename</var> is
the name of the module).  Internal symbols must be named in such a way
that they won’t conflict with other modules, for example, by prefixing
them with "_modulename_".  Although some platforms support having the
same symbols defined more than once it is generally not portable and
it makes it impossible to dlpreopen such modules.
</p>
<p>libltdl will automatically cut the prefix off to get the real name of
the symbol.  Additionally, it supports modules that do not use a
prefix so that you can also dlopen non-libtool modules.
</p>
<p><samp>foo1.c</samp> gives an example of a portable libtool module.
Exported symbols are prefixed with "foo1_LTX_", internal symbols
with "_foo1_".  Aliases are defined at the beginning so that the code
is more readable.
</p>
<div class="example">
<pre class="example">/* aliases for the exported symbols */
#define foo  foo1_LTX_foo
#define bar  foo1_LTX_bar

/* a global variable definition */
int bar = 1;

/* a private function */
int _foo1_helper() {
  return bar;
}

/* an exported function */
int foo() {
  return _foo1_helper();
}
</pre></div>

<p>The <samp>Makefile.am</samp> contains the necessary rules to build the
module <samp>foo1.la</samp>:
</p>
<div class="example">
<pre class="example">...
lib_LTLIBRARIES = foo1.la

foo1_la_SOURCES = foo1.c
foo1_la_LDFLAGS = -module
...
</pre></div>


<hr>
<span id="Thread-Safety-in-libltdl"></span><div class="header">
<p>
Next: <a href="#User-defined-module-data" accesskey="n" rel="next">User defined module data</a>, Previous: <a href="#Modules-for-libltdl" accesskey="p" rel="prev">Modules for libltdl</a>, Up: <a href="#Using-libltdl" accesskey="u" rel="up">Using libltdl</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Using-libltdl-in-a-multi-threaded-environment"></span><h3 class="section">11.3 Using libltdl in a multi threaded environment</h3>

<p>Libltdl provides a wrapper around whatever dynamic run-time object
loading mechanisms are provided by the host system, many of which are
themselves not thread safe.  Consequently libltdl cannot itself be
consistently thread safe.
</p>
<p>If you wish to use libltdl in a multithreaded environment, then you
must mutex lock around libltdl calls, since they may in turn be calling
non-thread-safe system calls on some target hosts.
</p>
<p>Some old releases of libtool provided a mutex locking API that
was unusable with POSIX threads, so callers were forced to lock around
all libltdl API calls anyway.  That mutex locking API was
next to useless, and is not present in current releases.
</p>
<p>Some future release of libtool may provide a new POSIX thread
compliant mutex locking API.
</p>
<hr>
<span id="User-defined-module-data"></span><div class="header">
<p>
Next: <a href="#Module-loaders-for-libltdl" accesskey="n" rel="next">Module loaders for libltdl</a>, Previous: <a href="#Thread-Safety-in-libltdl" accesskey="p" rel="prev">Thread Safety in libltdl</a>, Up: <a href="#Using-libltdl" accesskey="u" rel="up">Using libltdl</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Data-associated-with-loaded-modules"></span><h3 class="section">11.4 Data associated with loaded modules</h3>

<p>Some of the internal information about each loaded module that is
maintained by libltdl is available to the user, in the form of this
structure:
</p>
<dl>
<dt id="index-lt_005fdlinfo">Type: <em>struct</em> <strong>lt_dlinfo</strong> <em>{ char&nbsp;*<var>filename</var>;<!-- /@w -->   char&nbsp;*<var>name</var>;<!-- /@w --> int&nbsp;<var><span class="nolinebreak">ref_count</span></var>;<!-- /@w -->   int&nbsp;<var><span class="nolinebreak">is_resident</span></var>;<!-- /@w --> int&nbsp;<var><span class="nolinebreak">is_symglobal</span></var>;<!-- /@w -->   int&nbsp;<var><span class="nolinebreak">is_symlocal</span></var>;<!-- /@w -->}</em></dt>
<dd><p><code>lt_dlinfo</code> is used to store information about a module.
The <var>filename</var> attribute is a null-terminated character string of
the real module file name.  If the module is a libtool module then
<var>name</var> is its module name (e.g. <code>"libfoo"</code> for
<code>"dir/libfoo.la"</code>), otherwise it is set to <code>NULL</code>.  The
<var>ref_count</var> attribute is a reference counter that describes how
often the same module is currently loaded. The remaining fields can
be compared to any hints that were passed to <code>lt_dlopenadvise</code>
to determine whether the underlying loader was able to follow them.
</p></dd></dl>

<p>The following function will return a pointer to libltdl’s internal copy
of this structure for the given <var>handle</var>:
</p>
<dl>
<dt id="index-lt_005fdlgetinfo">Function: <em>const lt_dlinfo *</em> <strong>lt_dlgetinfo</strong> <em>(<span class="nolinebreak">lt_dlhandle</span>&nbsp;<var>handle</var><!-- /@w -->)</em></dt>
<dd><p>Return a pointer to a struct that contains some information about
the module <var>handle</var>.  The contents of the struct must not be modified.
Return <code>NULL</code> on failure.
</p></dd></dl>

<p>Furthermore, to save you from having to keep a list of the
handles of all the modules you have loaded, these functions allow you to
iterate over libltdl’s list of loaded modules:
</p>
<dl>
<dt id="index-lt_005fdlinterface_005fid">Type: <strong>lt_dlinterface_id</strong></dt>
<dd><p>The opaque type used to hold the module interface details for each
registered libltdl client.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlhandle_005finterface">Type: <em>int</em> <strong>lt_dlhandle_interface</strong> <em>(<span class="nolinebreak">lt_dlhandle</span>&nbsp;<var>handle</var>,<!-- /@w -->   const&nbsp;char&nbsp;*<var><span class="nolinebreak">id_string</span></var><!-- /@w -->)</em></dt>
<dd><p>Functions of this type are called to check that a handle conforms to a
library’s expected module interface when iterating over the global
handle list.  You should be careful to write a callback function of
this type that can correctly identify modules that belong to this
client, both to prevent other clients from accidentally finding your
loaded modules with the iterator functions below, and vice versa.  The
best way to do this is to check that module <var>handle</var> conforms
to the interface specification of your loader using <code>lt_dlsym</code>.
</p>
<p>The callback may be given <strong>every</strong> module loaded by all the
libltdl module clients in the current address space, including any
modules loaded by other libraries such as libltdl itself, and should
return non-zero if that module does not fulfill the interface
requirements of your loader.
</p>
<div class="example">
<pre class="example">int
my_interface_cb (lt_dlhandle handle, const char *id_string)
{
  char *(*module_id) (void) = NULL;

  /* <span class="roman">A valid my_module must provide all of these symbols.</span>  */
  if (!((module_id = (char*(*)(void)) lt_dlsym ("module_version"))
        &amp;&amp; lt_dlsym ("my_module_entrypoint")))
      return 1;

  if (strcmp (id_string, module_id()) != 0)
      return 1;

  return 0;
}
</pre></div>
</dd></dl>

<dl>
<dt id="index-lt_005fdlinterface_005fregister">Function: <em>lt_dlinterface_id</em> <strong>lt_dlinterface_register</strong> <em>(const&nbsp;char&nbsp;*<var><span class="nolinebreak">id_string</span></var><!-- /@w -->, <span class="nolinebreak">lt_dlhandle_interface</span>&nbsp;*<var>iface</var><!-- /@w -->)</em></dt>
<dd><p>Use this function to register your interface validator with libltdl,
and in return obtain a unique key to store and retrieve per-module data.
You supply an <var>id_string</var> and <var>iface</var> so that the resulting
<code>lt_dlinterface_id</code> can be used to filter the module handles
returned by the iteration functions below.  If <var>iface</var> is <code>NULL</code>,
all modules will be matched.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlinterface_005ffree">Function: <em>void</em> <strong>lt_dlinterface_free</strong> <em>(<span class="nolinebreak">lt_dlinterface_id</span>&nbsp;<var>iface</var><!-- /@w -->)</em></dt>
<dd><p>Release the data associated with <var>iface</var>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlhandle_005fmap">Function: <em>int</em> <strong>lt_dlhandle_map</strong> <em>(<span class="nolinebreak">lt_dlinterface_id</span>&nbsp;<var>iface</var><!-- /@w -->,   int&nbsp;(*<var>func</var>)&nbsp;<span class="nolinebreak">(lt_dlhandle</span>&nbsp;<var>handle</var>,&nbsp;void&nbsp;*&nbsp;<var>data</var>)<!-- /@w -->,   void&nbsp;*&nbsp;<var>data</var><!-- /@w -->)</em></dt>
<dd><p>For each module that matches <var>iface</var>, call the function
<var>func</var>.  When writing the <var>func</var> callback function, the
argument <var>handle</var> is the handle of a loaded module, and
<var>data</var> is the last argument passed to <code>lt_dlhandle_map</code>. As
soon as <var>func</var> returns a non-zero value for one of the handles,
<code>lt_dlhandle_map</code> will stop calling <var>func</var> and immediately
return that non-zero value.  Otherwise 0 is eventually returned when
<var>func</var> has been successfully called for all matching modules.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlhandle_005fiterate">Function: <em>lt_dlhandle</em> <strong>lt_dlhandle_iterate</strong> <em>(<span class="nolinebreak">lt_dlinterface_id</span>&nbsp;&nbsp;&nbsp;<var>iface</var><!-- /@w -->, <span class="nolinebreak">lt_dlhandle</span>&nbsp;<var>place</var><!-- /@w -->)</em></dt>
<dd><p>Iterate over the module handles loaded by <var>iface</var>, returning the
first matching handle in the list if <var>place</var> is <code>NULL</code>, and
the next one on subsequent calls.  If <var>place</var> is the last element
in the list of eligible modules, this function returns <code>NULL</code>.
</p>
<div class="example">
<pre class="example">lt_dlhandle handle = 0;
lt_dlinterface_id iface = my_interface_id;

while ((handle = lt_dlhandle_iterate (iface, handle)))
  {
    …
  }
</pre></div>
</dd></dl>

<dl>
<dt id="index-lt_005fdlhandle_005ffetch">Function: <em>lt_dlhandle</em> <strong>lt_dlhandle_fetch</strong> <em>(<span class="nolinebreak">lt_dlinterface_id</span>&nbsp;<var>iface</var><!-- /@w -->, const&nbsp;char&nbsp;*<var><span class="nolinebreak">module_name</span></var><!-- /@w -->)</em></dt>
<dd><p>Search through the module handles loaded by <var>iface</var> for a module named
<var>module_name</var>, returning its handle if found or else <code>NULL</code>
if no such named module has been loaded by <var>iface</var>.
</p></dd></dl>

<p>However, you might still need to maintain your own list of loaded
module handles (in parallel with the list maintained inside libltdl)
if there were any other data that your application wanted to associate
with each open module.  Instead, you can use the following API
calls to do that for you.  You must first obtain a unique interface id
from libltdl as described above, and subsequently always use it to
retrieve the data you stored earlier.  This allows different libraries
to each store their own data against loaded modules, without
interfering with one another.
</p>
<dl>
<dt id="index-lt_005fdlcaller_005fset_005fdata">Function: <em>void *</em> <strong>lt_dlcaller_set_data</strong> <em>(<span class="nolinebreak">lt_dlinterface_id</span>&nbsp;<var>key</var><!-- /@w -->, <span class="nolinebreak">lt_dlhandle</span>&nbsp;<var>handle</var><!-- /@w -->, void&nbsp;*&nbsp;<var>data</var><!-- /@w -->)</em></dt>
<dd><p>Set <var>data</var> as the set of data uniquely associated with <var>key</var> and
<var>handle</var> for later retrieval.  This function returns the <var>data</var>
previously associated with <var>key</var> and <var>handle</var> if any.  A result of
0, may indicate that a diagnostic for the last error (if any) is available
from <code>lt_dlerror()</code>.
</p>
<p>For example, to correctly remove some associated data:
</p>
<div class="example">
<pre class="example">void *stale = lt_dlcaller_set_data (key, handle, 0);
if (stale != NULL)
  {
    free (stale);
  }
else
  {
    char *error_msg = lt_dlerror ();

    if (error_msg != NULL)
      {
        my_error_handler (error_msg);
        return STATUS_FAILED;
      }
  }
</pre></div>
</dd></dl>

<dl>
<dt id="index-lt_005fdlcaller_005fget_005fdata">Function: <em>void *</em> <strong>lt_dlcaller_get_data</strong> <em>(<span class="nolinebreak">lt_dlinterface_id</span>&nbsp;<var>key</var><!-- /@w -->, <span class="nolinebreak">lt_dlhandle</span>&nbsp;<var>handle</var><!-- /@w -->)</em></dt>
<dd><p>Return the address of the data associated with <var>key</var> and
<var>handle</var>, or else <code>NULL</code> if there is none.
</p></dd></dl>

<p>Old versions of libltdl also provided a simpler, but similar, API
based around <code>lt_dlcaller_id</code>.  Unfortunately, it had no
provision for detecting whether a module belonged to a particular
interface as libltdl didn’t support multiple loaders in the same
address space at that time.  Those APIs are no longer supported
as there would be no way to stop clients of the old APIs from
seeing (and accidentally altering) modules loaded by other libraries.
</p>

<hr>
<span id="Module-loaders-for-libltdl"></span><div class="header">
<p>
Next: <a href="#Distributing-libltdl" accesskey="n" rel="next">Distributing libltdl</a>, Previous: <a href="#User-defined-module-data" accesskey="p" rel="prev">User defined module data</a>, Up: <a href="#Using-libltdl" accesskey="u" rel="up">Using libltdl</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="How-to-create-and-register-new-module-loaders"></span><h3 class="section">11.5 How to create and register new module loaders</h3>

<p>Sometimes libltdl’s many ways of gaining access to modules are not
sufficient for the purposes of a project.  You can write your own
loader, and register it with libltdl so that <code>lt_dlopen</code> will be
able to use it.
</p>
<p>Writing a loader involves writing at least three functions that can be
called by <code>lt_dlopen</code>, <code>lt_dlsym</code> and <code>lt_dlclose</code>.
Optionally, you can provide a finalisation function to perform any
cleanup operations when <code>lt_dlexit</code> executes, and a symbol prefix
string that will be prepended to any symbols passed to <code>lt_dlsym</code>.
These functions must match the function pointer types below, after
which they can be allocated to an instance of <code>lt_user_dlloader</code>
and registered.
</p>
<p>Registering the loader requires that you choose a name for it, so that it
can be recognised by <code>lt_dlloader_find</code> and removed with
<code>lt_dlloader_remove</code>.  The name you choose must be unique, and not
already in use by libltdl’s builtin loaders:
</p>
<dl compact="compact">
<dt>"dlopen"</dt>
<dd><p>The system dynamic library loader, if one exists.
</p></dd>
<dt>"dld"</dt>
<dd><p>The GNU dld loader, if <samp>libdld</samp> was installed when libltdl was
built.
</p></dd>
<dt>"dlpreload"</dt>
<dd><p>The loader for <code>lt_dlopen</code>ing of preloaded static modules.
</p></dd>
</dl>

<p>The prefix "dl" is reserved for loaders supplied with future versions of
libltdl, so you should not use that for your own loader names.
</p>
<p>The following types are defined in <samp>ltdl.h</samp>:
</p>
<dl>
<dt id="index-lt_005fmodule">Type: <strong>lt_module</strong></dt>
<dd><p><code>lt_module</code> is a dlloader dependent module.
The dynamic module loader extensions communicate using these low
level types.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlloader">Type: <strong>lt_dlloader</strong></dt>
<dd><p><code>lt_dlloader</code> is a handle for module loader types.
</p></dd></dl>

<dl>
<dt id="index-lt_005fuser_005fdata">Type: <strong>lt_user_data</strong></dt>
<dd><p><code>lt_user_data</code> is used for specifying loader instance data.
</p></dd></dl>

<dl>
<dt id="index-lt_005fuser_005fdlloader">Type: <em>struct</em> <strong>lt_user_dlloader</strong> <em>{const&nbsp;char&nbsp;*<var><span class="nolinebreak">sym_prefix</span></var>;<!-- /@w --> <span class="nolinebreak">lt_module_open</span>&nbsp;*<var><span class="nolinebreak">module_open</span></var>;<!-- /@w --> <span class="nolinebreak">lt_module_close</span>&nbsp;*<var><span class="nolinebreak">module_close</span></var>;<!-- /@w --> <span class="nolinebreak">lt_find_sym</span>&nbsp;*<var><span class="nolinebreak">find_sym</span></var>;<!-- /@w --> <span class="nolinebreak">lt_dlloader_exit</span>&nbsp;*<var><span class="nolinebreak">dlloader_exit</span></var>;<!-- /@w --> }</em></dt>
<dd><p>If you want to define a new way to open dynamic modules, and have the
<code>lt_dlopen</code> API use it, you need to instantiate one of these
structures and pass it to <code>lt_dlloader_add</code>.  You can pass whatever
you like in the <var>dlloader_data</var> field, and it will be passed back as
the value of the first parameter to each of the functions specified in
the function pointer fields.
</p></dd></dl>

<dl>
<dt id="index-lt_005fmodule_005fopen">Type: <em>lt_module</em> <strong>lt_module_open</strong> <em>(const&nbsp;char&nbsp;*<var>filename</var><!-- /@w -->)</em></dt>
<dd><p>The type of the loader function for an <code>lt_dlloader</code> module
loader.  The value set in the dlloader_data field of the <code>struct
lt_user_dlloader</code> structure will be passed into this function in the
<var>loader_data</var> parameter.  Implementation of such a function should
attempt to load the named module, and return an <code>lt_module</code>
suitable for passing in to the associated <code>lt_module_close</code> and
<code>lt_sym_find</code> function pointers.  If the function fails it should
return <code>NULL</code>, and set the error message with <code>lt_dlseterror</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fmodule_005fclose">Type: <em>int</em> <strong>lt_module_close</strong> <em>(<span class="nolinebreak">lt_user_data</span>&nbsp;<var><span class="nolinebreak">loader_data</span></var>,<!-- /@w --> <span class="nolinebreak">lt_module</span>&nbsp;<var>module</var><!-- /@w -->)</em></dt>
<dd><p>The type of the unloader function for a user defined module loader.
Implementation of such a function should attempt to release
any resources tied up by the <var>module</var> module, and then unload it
from memory.  If the function fails for some reason, set the error
message with <code>lt_dlseterror</code> and return non-zero.
</p></dd></dl>

<dl>
<dt id="index-lt_005ffind_005fsym">Type: <em>void *</em> <strong>lt_find_sym</strong> <em>(<span class="nolinebreak">lt_module</span>&nbsp;<var>module</var>,<!-- /@w --> const&nbsp;char&nbsp;*<var>symbol</var><!-- /@w -->)</em></dt>
<dd><p>The type of the symbol lookup function for a user defined module loader.
Implementation of such a function should return the address of the named
<var>symbol</var> in the module <var>module</var>, or else set the error message
with <code>lt_dlseterror</code> and return <code>NULL</code> if lookup fails.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlloader_005fexit">Type: <em>int</em> <strong>lt_dlloader_exit</strong> <em>(<span class="nolinebreak">lt_user_data</span>&nbsp;<var><span class="nolinebreak">loader_data</span></var><!-- /@w -->)</em></dt>
<dd><p>The type of the finalisation function for a user defined module loader.
Implementation of such a function should free any resources associated
with the loader, including any user specified data in the
<code>dlloader_data</code> field of the <code>lt_user_dlloader</code>.  If non-<code>NULL</code>,
the function will be called by <code>lt_dlexit</code>, and
<code>lt_dlloader_remove</code>.
</p></dd></dl>

<p>For example:
</p>
<div class="example">
<pre class="example">int
register_myloader (void)
{
  lt_user_dlloader dlloader;

  /* User modules are responsible for their own initialisation. */
  if (myloader_init () != 0)
    return MYLOADER_INIT_ERROR;

  dlloader.sym_prefix    = NULL;
  dlloader.module_open   = myloader_open;
  dlloader.module_close  = myloader_close;
  dlloader.find_sym      = myloader_find_sym;
  dlloader.dlloader_exit = myloader_exit;
  dlloader.dlloader_data = (lt_user_data)myloader_function;

  /* Add my loader as the default module loader. */
  if (lt_dlloader_add (lt_dlloader_next (NULL), &amp;dlloader,
                       "myloader") != 0)
    return ERROR;

  return OK;
}
</pre></div>

<p>Note that if there is any initialisation required for the loader,
it must be performed manually before the loader is registered –
libltdl doesn’t handle user loader initialisation.
</p>
<p>Finalisation <em>is</em> handled by libltdl however, and it is important
to ensure the <code>dlloader_exit</code> callback releases any resources claimed
during the initialisation phase.
</p>
<p>libltdl provides the following functions for writing your own module
loaders:
</p>
<dl>
<dt id="index-lt_005fdlloader_005fadd">Function: <em>int</em> <strong>lt_dlloader_add</strong> <em>(<span class="nolinebreak">lt_dlloader</span>&nbsp;*<var>place</var>,<!-- /@w -->   <span class="nolinebreak">lt_user_dlloader</span>&nbsp;*<var>dlloader</var>,<!-- /@w --> const&nbsp;char&nbsp;*<var><span class="nolinebreak">loader_name</span></var><!-- /@w -->)</em></dt>
<dd><p>Add a new module loader to the list of all loaders, either as the
last loader (if <var>place</var> is <code>NULL</code>), else immediately before the
loader passed as <var>place</var>.  <var>loader_name</var> will be returned by
<code>lt_dlloader_name</code> if it is subsequently passed a newly
registered loader.  These <var>loader_name</var>s must be unique, or
<code>lt_dlloader_remove</code> and <code>lt_dlloader_find</code> cannot
work.  Returns 0 for success.
</p>
<div class="example">
<pre class="example">/* Make myloader be the last one. */
if (lt_dlloader_add (NULL, myloader) != 0)
  perror (lt_dlerror ());
</pre></div>
</dd></dl>

<dl>
<dt id="index-lt_005fdlloader_005fremove">Function: <em>int</em> <strong>lt_dlloader_remove</strong> <em>(const&nbsp;char&nbsp;*<var><span class="nolinebreak">loader_name</span></var><!-- /@w -->)</em></dt>
<dd><p>Remove the loader identified by the unique name, <var>loader_name</var>.
Before this can succeed, all modules opened by the named loader must
have been closed.  Returns 0 for success, otherwise an error message can
be obtained from <code>lt_dlerror</code>.
</p>
<div class="example">
<pre class="example">/* Remove myloader. */
if (lt_dlloader_remove ("myloader") != 0)
  perror (lt_dlerror ());
</pre></div>
</dd></dl>

<dl>
<dt id="index-lt_005fdlloader_005fnext">Function: <em>lt_dlloader *</em> <strong>lt_dlloader_next</strong> <em>(<span class="nolinebreak">lt_dlloader</span>&nbsp;*<var>place</var><!-- /@w -->)</em></dt>
<dd><p>Iterate over the module loaders, returning the first loader if <var>place</var> is
<code>NULL</code>, and the next one on subsequent calls.  The handle is for use with
<code>lt_dlloader_add</code>.
</p>
<div class="example">
<pre class="example">/* Make myloader be the first one. */
if (lt_dlloader_add (lt_dlloader_next (NULL), myloader) != 0)
  return ERROR;
</pre></div>
</dd></dl>

<dl>
<dt id="index-lt_005fdlloader_005ffind">Function: <em>lt_dlloader *</em> <strong>lt_dlloader_find</strong> <em>(const&nbsp;char&nbsp;*<var><span class="nolinebreak">loader_name</span></var><!-- /@w -->)</em></dt>
<dd><p>Return the first loader with a matching <var>loader_name</var> identifier, or else
<code>NULL</code>, if the identifier is not found.
</p>
<p>The identifiers that may be used by libltdl itself, if the host
architecture supports them are <em>dlopen</em><a id="DOCF11" href="#FOOT11"><sup>11</sup></a>, <em>dld</em> and <em>dlpreload</em>.
</p>
<div class="example">
<pre class="example">/* Add a user loader as the next module loader to be tried if
   the standard dlopen loader were to fail when lt_dlopening. */
if (lt_dlloader_add (lt_dlloader_find ("dlopen"), myloader) != 0)
  return ERROR;
</pre></div>
</dd></dl>

<dl>
<dt id="index-lt_005fdlloader_005fname">Function: <em>const char *</em> <strong>lt_dlloader_name</strong> <em>(<span class="nolinebreak">lt_dlloader</span>&nbsp;*<var>place</var><!-- /@w -->)</em></dt>
<dd><p>Return the identifying name of <var>place</var>, as obtained from
<code>lt_dlloader_next</code> or <code>lt_dlloader_find</code>.  If this function fails,
it will return <code>NULL</code> and set an error for retrieval with
<code>lt_dlerror</code>.
</p></dd></dl>

<dl>
<dt id="index-lt_005fdlloader_005fdata">Function: <em>lt_user_data *</em> <strong>lt_dlloader_data</strong> <em>(<span class="nolinebreak">lt_dlloader</span>&nbsp;*<var>place</var><!-- /@w -->)</em></dt>
<dd><p>Return the address of the <code>dlloader_data</code> of <var>place</var>, as
obtained from <code>lt_dlloader_next</code> or <code>lt_dlloader_find</code>.  If
this function fails, it will return <code>NULL</code> and set an error for
retrieval with <code>lt_dlerror</code>.
</p></dd></dl>

<span id="Error-handling-within-user-module-loaders"></span><h4 class="subsection">11.5.1 Error handling within user module loaders</h4>

<dl>
<dt id="index-lt_005fdladderror">Function: <em>int</em> <strong>lt_dladderror</strong> <em>(const&nbsp;char&nbsp;*<var>diagnostic</var><!-- /@w -->)</em></dt>
<dd><p>This function allows you to integrate your own error messages into
<code>lt_dlerror</code>.  Pass in a suitable diagnostic message for return by
<code>lt_dlerror</code>, and an error identifier for use with
<code>lt_dlseterror</code> is returned.
</p>
<p>If the allocation of an identifier fails, this function returns -1.
</p>
<div class="example">
<pre class="example">int myerror = lt_dladderror ("doh!");
if (myerror &lt; 0)
  perror (lt_dlerror ());
</pre></div>
</dd></dl>

<dl>
<dt id="index-lt_005fdlseterror">Function: <em>int</em> <strong>lt_dlseterror</strong> <em>(int&nbsp;<var>errorcode</var><!-- /@w -->)</em></dt>
<dd><p>When writing your own module loaders, you should use this function to
raise errors so that they are propagated through the <code>lt_dlerror</code>
interface.  All of the standard errors used by libltdl are declared in
<samp>ltdl.h</samp>, or you can add more of your own with
<code>lt_dladderror</code>.  This function returns 0 on success.
</p>
<div class="example">
<pre class="example">if (lt_dlseterror (LTDL_ERROR_NO_MEMORY) != 0)
  perror (lt_dlerror ());
</pre></div>
</dd></dl>

<hr>
<span id="Distributing-libltdl"></span><div class="header">
<p>
Previous: <a href="#Module-loaders-for-libltdl" accesskey="p" rel="prev">Module loaders for libltdl</a>, Up: <a href="#Using-libltdl" accesskey="u" rel="up">Using libltdl</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="How-to-distribute-libltdl-with-your-package"></span><h3 class="section">11.6 How to distribute libltdl with your package</h3>

<p>Even though libltdl is installed together with libtool, you may wish
to include libltdl in the distribution of your package, for the
convenience of users of your package that don’t have libtool or
libltdl installed, or if you are using features of a very new version
of libltdl that you don’t expect your users to have yet.  In such
cases, you must decide what flavor of libltdl you want to use: a
convenience library or an installable libtool library.
</p>
<p>The most simplistic way to add <code>libltdl</code> to your package is to
copy all the <samp>libltdl</samp> source files to a subdirectory within
your package and to build and link them along with the rest of your
sources.  To help you do this, the m4 macros for Autoconf are
available in <samp>ltdl.m4</samp>.  You must ensure that they are available
in <samp>aclocal.m4</samp> before you run Autoconf<a id="DOCF12" href="#FOOT12"><sup>12</sup></a>.  Having made the macros available, you must add a call to the
‘<samp>LTDL_INIT</samp>’ macro (after the call to ‘<samp>LT_INIT</samp>’)
to your package’s <samp>configure.ac</samp> to
perform the configure time checks required to build the library
correctly.  Unfortunately, this method has problems if you then try to
link the package binaries with an installed libltdl, or a library that
depends on libltdl, because of the duplicate symbol definitions.  For
example, ultimately linking against two different versions of libltdl,
or against both a local convenience library and an installed libltdl
is bad.  Ensuring that only one copy of the libltdl sources are linked
into any program is left as an exercise for the reader.
</p>
<dl>
<dt id="index-LT_005fCONFIG_005fLTDL_005fDIR">Macro: <strong>LT_CONFIG_LTDL_DIR</strong> <em>(<var>directory</var>)</em></dt>
<dd><p>Declare <var>directory</var> to be the location of the <code>libltdl</code>
source files, for <code>libtoolize --ltdl</code> to place
them. See <a href="#Invoking-libtoolize">Invoking libtoolize</a>, for more details.  Provided that you
add an appropriate <code>LT_CONFIG_LTDL_DIR</code> call in your
<samp>configure.ac</samp> before calling <code>libtoolize</code>, the
appropriate <code>libltdl</code> files will be installed automatically.
</p></dd></dl>

<dl>
<dt id="index-LTDL_005fINIT">Macro: <strong>LTDL_INIT</strong> <em>(<var>options</var>)</em></dt>
<dt id="index-LT_005fWITH_005fLTDL">Macro: <strong>LT_WITH_LTDL</strong></dt>
<dt id="index-AC_005fWITH_005fLTDL">Macro: <strong>AC_WITH_LTDL</strong></dt>
<dd><p><code>AC_WITH_LTDL</code> and <code>LT_WITH_LTDL</code> are deprecated names for
older versions of this macro; <code>autoupdate</code> will update your
<samp>configure.ac</samp> file.
</p>
<p>This macro adds the following options to the <code>configure</code>
script:
</p>
<dl compact="compact">
<dt><samp>--with-ltdl-include <var>installed-ltdl-header-dir</var></samp></dt>
<dd><p>The <code>LTDL_INIT</code> macro will look in the standard header file
locations to find the installed <code>libltdl</code> headers.  If
<code>LTDL_INIT</code> can’t find them by itself, the person who builds
your package can use this option to tell <code>configure</code> where
the installed <code>libltdl</code> headers are.
</p>
</dd>
<dt><samp>--with-ltdl-lib <var>installed-ltdl-library-dir</var></samp></dt>
<dd><p>Similarly, the person building your package can use this option to
help <code>configure</code> find the installed <samp>libltdl.la</samp>.
</p>
</dd>
<dt><samp>--with-included-ltdl</samp></dt>
<dd><p>If there is no installed <code>libltdl</code>, or in any case if the
person building your package would rather use the <code>libltdl</code>
sources shipped with the package in the subdirectory named by
<code>LT_CONFIG_LTDL_DIR</code>, they should pass this option to
<code>configure</code>.
</p></dd>
</dl>

<p>If the <samp>--with-included-ltdl</samp> is not passed at
configure time, and an installed <code>libltdl</code> is not
found<a id="DOCF13" href="#FOOT13"><sup>13</sup></a>, then <code>configure</code> will exit immediately with an error that
asks the user to either specify the location of an installed
<code>libltdl</code> using the <samp>--with-ltdl-include</samp> and
<samp>--with-ltdl-lib</samp> options, or to build with the
<code>libltdl</code> sources shipped with the package by passing
<samp>--with-included-ltdl</samp>.
</p>
<p>If an installed <code>libltdl</code> is found, then <code>LIBLTDL</code> is set to
the link flags needed to use it, and <code>LTDLINCL</code> to the preprocessor
flags needed to find the installed headers, and <code>LTDLDEPS</code> will
be empty.  Note, however, that no version checking is performed.  You
should manually check for the <code>libltdl</code> features you need in
<samp>configure.ac</samp>:
</p>
<div class="example">
<pre class="example">LT_INIT([dlopen])
LTDL_INIT

# The lt_dladvise_init symbol was added with libtool-2.2
if test yes != "$with_included_ltdl"; then
  save_CFLAGS=$CFLAGS
  save_LDFLAGS=$LDFLAGS
  CFLAGS="$CFLAGS $LTDLINCL"
  LDFLAGS="$LDFLAGS $LIBLTDL"
  AC_CHECK_LIB([ltdl], [lt_dladvise_init],
                [],
        [AC_MSG_ERROR([installed libltdl is too old])])
  LDFLAGS=$save_LDFLAGS
  CFLAGS=$save_CFLAGS
fi
</pre></div>

<p><var>options</var> may include no more than one of the following build
modes depending on how you want your project to build <code>libltdl</code>:
‘<samp>nonrecursive</samp>’, ‘<samp>recursive</samp>’, or ‘<samp>subproject</samp>’.  In order
for <code>libtoolize</code> to detect this option correctly, if you
supply one of these arguments, they must be given literally (i.e.,
macros or shell variables that expand to the correct ltdl mode will not
work).
</p>
<dl compact="compact">
<dt>‘<samp>nonrecursive</samp>’</dt>
<dd><p>This is how the Libtool project distribution builds the <code>libltdl</code>
we ship and install.  If you wish to use Automake to build
<code>libltdl</code> without invoking a recursive make to descend into the
<code>libltdl</code> subdirectory, then use this option.  You will need to set
your configuration up carefully to make this work properly, and you will
need releases of Autoconf and Automake that support
<code>subdir-objects</code> and <code>LIBOBJDIR</code> properly.  In your
<samp>configure.ac</samp>, add:
</p>
<div class="example">
<pre class="example">AM_INIT_AUTOMAKE([subdir-objects])
AC_CONFIG_HEADERS([config.h])
LT_CONFIG_LTDL_DIR([libltdl])
LT_INIT([dlopen])
LTDL_INIT([nonrecursive])
</pre></div>

<p>You <em>have to</em> use a config header, but it may have a name different
than <samp>config.h</samp>.
</p>
<p>Also, add the following near the top of your <samp>Makefile.am</samp>:
</p>
<div class="example">
<pre class="example">AM_CPPFLAGS =
AM_LDFLAGS =

BUILT_SOURCES =
EXTRA_DIST =
CLEANFILES =
MOSTLYCLEANFILES =

include_HEADERS =
noinst_LTLIBRARIES =
lib_LTLIBRARIES =
EXTRA_LTLIBRARIES =

include libltdl/ltdl.mk
</pre></div>

<p>Unless you build no other libraries from this <samp>Makefile.am</samp>,
you will also need to change <code>lib_LTLIBRARIES</code> to assign with
‘<samp>+=</samp>’ so that the <code>libltdl</code> targets declared in
<samp>ltdl.mk</samp> are not overwritten.
</p>
</dd>
<dt>‘<samp>recursive</samp>’</dt>
<dd><p>This build mode still requires that you use Automake, but (in contrast
with ‘<samp>nonrecursive</samp>’) uses the more usual device of starting another
<code>make</code> process in the <samp>libltdl</samp> subdirectory.  To use this
mode, you should add to your <samp>configure.ac</samp>:
</p>
<div class="example">
<pre class="example">AM_INIT_AUTOMAKE
AC_CONFIG_HEADERS([config.h])
LT_CONFIG_LTDL_DIR([libltdl])
LT_INIT([dlopen])
LTDL_INIT([recursive])
AC_CONFIG_FILES([libltdl/Makefile])
</pre></div>

<p>Again, you <em>have to</em> use a config header, but it may have a name
different than <samp>config.h</samp> if you like.
</p>
<p>Also, add this to your <samp>Makefile.am</samp>:
</p>
<div class="example">
<pre class="example">SUBDIRS = libltdl
</pre></div>

</dd>
<dt>‘<samp>subproject</samp>’</dt>
<dd><p>This mode is the default unless you explicitly add <code>recursive</code> or
<code>nonrecursive</code> to your <code>LTDL_INIT</code> options;  <code>subproject</code>
is the only mode supported by previous releases of libltdl.  Even if you
do not use Autoconf in the parent project, then, in ‘<samp>subproject</samp>’
mode, still <code>libltdl</code> contains all the necessary files to configure
and build itself – you just need to arrange for your build system to
call <samp>libltdl/configure</samp> with appropriate options, and then run
<code>make</code> in the <code>libltdl</code> subdirectory.
</p>
<p>If you <em>are</em> using Autoconf and Automake, then you will need to add
the following to your <samp>configure.ac</samp>:
</p>
<div class="example">
<pre class="example">LT_CONFIG_LTDL_DIR([libltdl])
LTDL_INIT
</pre></div>

<p>and to <samp>Makefile.am</samp>:
</p>
<div class="example">
<pre class="example">SUBDIRS = libltdl
</pre></div>
</dd>
</dl>

<p>Aside from setting the libltdl build mode, there are other keywords
that you can pass to <code>LTDL_INIT</code> to modify its behavior when
<samp>--with-included-ltdl</samp> has been given:
</p>
<dl compact="compact">
<dt>‘<samp>convenience</samp>’</dt>
<dd><p>This is the default unless you explicitly add <code>installable</code> to
your <code>LTDL_INIT</code> options.
</p>
<p>This keyword will cause options to be passed to the <code>configure</code>
script in the subdirectory named by <code>LT_CONFIG_LTDL_DIR</code>
to cause it to be built as a convenience library.  If you’re not
using automake, you will need to define <code>top_build_prefix</code>,
<code>top_builddir</code>, and <code>top_srcdir</code> in your makefile so that
<code>LIBLTDL</code>, <code>LTDLDEPS</code>, and <code>LTDLINCL</code> expand correctly.
</p>
<p>One advantage of the convenience library is that it is not installed,
so the fact that you use <code>libltdl</code> will not be apparent to the
user, and it won’t overwrite a pre-installed version of
<code>libltdl</code> the system might already have in the installation
directory.  On the other hand, if you want to upgrade <code>libltdl</code>
for any reason (e.g. a bugfix) you’ll have to recompile your package
instead of just replacing the shared installed version of
<code>libltdl</code>.  However, if your programs or libraries are linked
with other libraries that use such a pre-installed version of
<code>libltdl</code>, you may get linker errors or run-time crashes.
Another problem is that you cannot link the convenience library into
more than one libtool library, then link a single program with those
libraries, because you may get duplicate symbols.  In general you can
safely use the convenience library in programs that don’t depend on
other libraries that might use <code>libltdl</code> too.
</p>
</dd>
<dt>‘<samp>installable</samp>’</dt>
<dd><p>This keyword will pass options to the <code>configure</code>
script in the subdirectory named by <code>LT_CONFIG_LTDL_DIR</code>
to cause it to be built as an installable library.  If you’re not
using automake, you will need to define <code>top_build_prefix</code>,
<code>top_builddir</code> and <code>top_srcdir</code> in your makefile so that
<code>LIBLTDL</code>, <code>LTDLDEPS</code>, and <code>LTDLINCL</code> are expanded
properly.
</p>
<p>Be aware that you could overwrite another <code>libltdl</code> already
installed to the same directory if you use this option.
</p></dd>
</dl>
</dd></dl>

<p>Whatever method you use, ‘<samp>LTDL_INIT</samp>’ will define the shell variable
<code>LIBLTDL</code> to the link flag that you should use to link with
<code>libltdl</code>, the shell variable <code>LTDLDEPS</code> to the files that
can be used as a dependency in <samp>Makefile</samp> rules, and the shell
variable <code>LTDLINCL</code> to the preprocessor flag that you should use to
compile programs that include <samp>ltdl.h</samp>. So, when you want to link a
program with libltdl, be it a convenience, installed or installable
library, just use ‘<samp>$(LTDLINCL)</samp>’ for preprocessing and compilation,
and ‘<samp>$(LIBLTDL)</samp>’ for linking.
</p>
<ul>
<li> If your package is built using an installed version of <code>libltdl</code>,
<code>LIBLTDL</code> will be set to the compiler flags needed to link against
the installed library, <code>LTDLDEPS</code> will be empty, and <code>LTDLINCL</code>
will be set to the compiler flags needed to find the <code>libltdl</code>
header files.

</li><li> If your package is built using the convenience libltdl, <code>LIBLTDL</code>
and <code>LTDLDEPS</code> will be the pathname for the convenience version of
libltdl (starting with ‘<samp>${top_builddir}/</samp>’ or
‘<samp>${top_build_prefix}</samp>’) and <code>LTDLINCL</code> will be <samp>-I</samp>
followed by the directory that contains <samp>ltdl.h</samp> (starting with
‘<samp>${top_srcdir}/</samp>’).

</li><li> If an installable version of the included <code>libltdl</code> is being
built, its pathname starting with ‘<samp>${top_builddir}/</samp>’ or
‘<samp>${top_build_prefix}</samp>’, will be stored in <code>LIBLTDL</code> and
<code>LTDLDEPS</code>, and <code>LTDLINCL</code> will be set just like in the case of
convenience library.
</li></ul>

<p>You should probably also use the ‘<samp>dlopen</samp>’ option to <code>LT_INIT</code>
in your <samp>configure.ac</samp>, otherwise libtool will assume no dlopening
mechanism is supported, and revert to dlpreopening, which is probably not
what you want.  Avoid using the <samp>-static</samp>,
<samp>-static-libtool-libs</samp>, or <samp>-all-static</samp>
switches when linking programs with libltdl.  This will not work on
all platforms, because the dlopening functions may not be available
for static linking.
</p>
<p>The following example shows you how to embed an installable libltdl in
your package.  In order to use the convenience variant, just replace the
<code>LTDL_INIT</code> option ‘<samp>installable</samp>’ with ‘<samp>convenience</samp>’.  We
assume that libltdl was embedded using ‘<samp>libtoolize --ltdl</samp>’.
</p>
<p>configure.ac:
</p><div class="example">
<pre class="example">...
# Name the subdirectory that contains libltdl sources
LT_CONFIG_LTDL_DIR([libltdl])

# Configure libtool with dlopen support if possible
LT_INIT([dlopen])

# Enable building of the installable libltdl library
LTDL_INIT([installable])
...
</pre></div>

<p>Makefile.am:
</p><div class="example">
<pre class="example">...
SUBDIRS = libltdl

AM_CPPFLAGS = $(LTDLINCL)

myprog_LDFLAGS = -export-dynamic
myprog_LDADD = $(LIBLTDL) -dlopen self -dlopen foo1.la
myprog_DEPENDENCIES = $(LTDLDEPS) foo1.la
...
</pre></div>

<dl>
<dt id="index-LTDL_005fINSTALLABLE">Macro: <strong>LTDL_INSTALLABLE</strong></dt>
<dt id="index-AC_005fLIBLTDL_005fINSTALLABLE">Macro: <strong>AC_LIBLTDL_INSTALLABLE</strong></dt>
<dd><p>These macros are deprecated, the ‘<samp>installable</samp>’ option to
<code>LTDL_INIT</code> should be used instead.
</p></dd></dl>

<dl>
<dt id="index-LTDL_005fCONVENIENCE">Macro: <strong>LTDL_CONVENIENCE</strong></dt>
<dt id="index-AC_005fLIBLTDL_005fCONVENIENCE">Macro: <strong>AC_LIBLTDL_CONVENIENCE</strong></dt>
<dd><p>These macros are deprecated, the ‘<samp>convenience</samp>’ option to
<code>LTDL_INIT</code> should be used instead.
</p></dd></dl>


<hr>
<span id="Trace-interface"></span><div class="header">
<p>
Next: <a href="#FAQ" accesskey="n" rel="next">FAQ</a>, Previous: <a href="#Using-libltdl" accesskey="p" rel="prev">Using libltdl</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Libtool_0027s-trace-interface"></span><h2 class="chapter">12 Libtool’s trace interface</h2>
<span id="index-trace-interface"></span>
<span id="index-autoconf-traces"></span>

<p>This section describes macros whose sole purpose is to be traced using
Autoconf’s <samp>--trace</samp> option (see <a href="https://www.gnu.org/software/autoconf/manual/autoconf.html#autoconf-Invocation">The
Autoconf Manual</a> in <cite>The Autoconf Manual</cite>) to query the Libtool
configuration of a project.  These macros are called by Libtool
internals and should never be called by user code; they should only be
traced.
</p>
<dl>
<dt id="index-LT_005fSUPPORTED_005fTAG">Macro: <strong>LT_SUPPORTED_TAG</strong> <em>(<var>tag</var>)</em></dt>
<dd><p>This macro is called once for each language enabled in the package.  Its
only argument, <var>tag</var>, is the tag-name corresponding to the language
(see <a href="#Tags">Tags</a>).
</p>
<p>You can therefore retrieve the list of all tags enabled in a project
using the following command:
</p><div class="example">
<pre class="example">autoconf --trace 'LT_SUPPORTED_TAG:$1'
</pre></div>
</dd></dl>


<hr>
<span id="FAQ"></span><div class="header">
<p>
Next: <a href="#Troubleshooting" accesskey="n" rel="next">Troubleshooting</a>, Previous: <a href="#Trace-interface" accesskey="p" rel="prev">Trace interface</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Frequently-Asked-Questions-about-libtool"></span><h2 class="chapter">13 Frequently Asked Questions about libtool</h2>

<p>This chapter covers some questions that often come up on the mailing
lists.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Stripped-link-flags" accesskey="1">Stripped link flags</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Dropped flags when creating a library
</td></tr>
</tbody></table>

<hr>
<span id="Stripped-link-flags"></span><div class="header">
<p>
Up: <a href="#FAQ" accesskey="u" rel="up">FAQ</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Why-does-libtool-strip-link-flags-when-creating-a-library_003f"></span><h3 class="section">13.1 Why does libtool strip link flags when creating a library?</h3>

<p>When creating a shared library, but not when compiling or creating
a program, <code>libtool</code> drops some flags from the command line
provided by the user.  This is done because flags unknown to
<code>libtool</code> may interfere with library creation or require
additional support from <code>libtool</code>, and because omitting
flags is usually the conservative choice for a successful build.
</p>
<p>If you encounter flags that you think are useful to pass, as a
work-around you can prepend flags with <code>-Wc,</code> or <code>-Xcompiler </code>
to allow them to be passed through to the compiler driver
(see <a href="#Link-mode">Link mode</a>).  Another possibility is to add flags already
to the compiler command at <code>configure</code> run time:
</p>
<div class="example">
<pre class="example">./configure CC='gcc -m64'
</pre></div>

<p>If you think <code>libtool</code> should let some flag through by default,
here’s how you can test such an inclusion: grab the Libtool development
tree, edit the <samp>ltmain.in</samp> file in the <samp>libltdl/config</samp>
subdirectory to pass through the flag (search for ‘<samp>Flags to be
passed through</samp>’), re-bootstrap and build with the flags in question
added to <code>LDFLAGS</code>, <code>CFLAGS</code>, <code>CXXFLAGS</code>, etc. on the
<code>configure</code> command line as appropriate.  Run the testsuite
as described in the <samp>README</samp> file and report results to
the Libtool bug reporting address <a href="mailto:bug-libtool@gnu.org">bug-libtool@gnu.org</a>.
</p>
<hr>
<span id="Troubleshooting"></span><div class="header">
<p>
Next: <a href="#Maintaining" accesskey="n" rel="next">Maintaining</a>, Previous: <a href="#FAQ" accesskey="p" rel="prev">FAQ</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Troubleshooting-1"></span><h2 class="chapter">14 Troubleshooting</h2>
<span id="index-troubleshooting"></span>
<span id="index-problems_002c-solving"></span>
<span id="index-solving-problems"></span>
<span id="index-problems_002c-blaming-somebody-else-for"></span>

<p>Libtool is under constant development, changing to remain up-to-date
with modern operating systems.  If libtool doesn’t work the way you
think it should on your platform, you should read this chapter to help
determine what the problem is, and how to resolve it.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Libtool-test-suite" accesskey="1">Libtool test suite</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Libtool’s self-tests.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Reporting-bugs" accesskey="2">Reporting bugs</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How to report problems with libtool.
</td></tr>
</tbody></table>

<hr>
<span id="Libtool-test-suite"></span><div class="header">
<p>
Next: <a href="#Reporting-bugs" accesskey="n" rel="next">Reporting bugs</a>, Up: <a href="#Troubleshooting" accesskey="u" rel="up">Troubleshooting</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="The-libtool-test-suite"></span><h3 class="section">14.1 The libtool test suite</h3>
<span id="index-test-suite"></span>

<p>Libtool comes with two integrated sets of tests to check that your build
is sane, that test its capabilities, and report obvious bugs in the
libtool program.  These tests, too, are constantly evolving, based on
past problems with libtool, and known deficiencies in other operating
systems.
</p>
<p>As described in the <samp>README</samp> file, you may run <kbd>make -k check</kbd>
after you have built libtool (possibly before you install it)
to make sure that it meets basic functional requirements.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Test-descriptions" accesskey="1">Test descriptions</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">The contents of the old test suite.
</td></tr>
<tr><td align="left" valign="top">• <a href="#When-tests-fail" accesskey="2">When tests fail</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">What to do when a test fails.
</td></tr>
</tbody></table>

<hr>
<span id="Test-descriptions"></span><div class="header">
<p>
Next: <a href="#When-tests-fail" accesskey="n" rel="next">When tests fail</a>, Up: <a href="#Libtool-test-suite" accesskey="u" rel="up">Libtool test suite</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Description-of-test-suite"></span><h4 class="subsection">14.1.1 Description of test suite</h4>

<p>Here is a list of the current programs in the old test suite, and what
they test for:
</p>
<dl compact="compact">
<dt><samp>cdemo-conf.test</samp></dt>
<dt><samp>cdemo-make.test</samp></dt>
<dt><samp>cdemo-exec.test</samp></dt>
<dt><samp>cdemo-static.test</samp></dt>
<dt><samp>cdemo-static-make.test</samp></dt>
<dt><samp>cdemo-static-exec.test</samp></dt>
<dt><samp>cdemo-shared.test</samp></dt>
<dt><samp>cdemo-shared-make.test</samp></dt>
<dt><samp>cdemo-shared-exec.test</samp></dt>
<dt><samp>cdemo-undef.test</samp></dt>
<dt><samp>cdemo-undef-make.test</samp></dt>
<dt><samp>cdemo-undef-exec.test</samp></dt>
<dd><span id="index-cdemo_002dconf_002etest"></span>
<span id="index-cdemo_002dmake_002etest"></span>
<span id="index-cdemo_002dexec_002etest"></span>
<span id="index-cdemo_002dstatic_002etest"></span>
<span id="index-cdemo_002dstatic_002dmake_002etest"></span>
<span id="index-cdemo_002dstatic_002dexec_002etest"></span>
<span id="index-cdemo_002dshared_002etest"></span>
<span id="index-cdemo_002dshared_002dmake_002etest"></span>
<span id="index-cdemo_002dshared_002dexec_002etest"></span>
<span id="index-cdemo_002dundef_002etest"></span>
<span id="index-cdemo_002dundef_002dmake_002etest"></span>
<span id="index-cdemo_002dundef_002dexec_002etest"></span>
<p>These programs check to see that the <samp>tests/cdemo</samp> subdirectory of
the libtool distribution can be configured and built correctly.
</p>
<p>The <samp>tests/cdemo</samp> subdirectory contains a demonstration of libtool
convenience libraries, a mechanism that allows build-time static
libraries to be created, in a way that their components can be later
linked into programs or other libraries, even shared ones.
</p>
<p>The tests matching <samp>cdemo-*make.test</samp> and <samp>cdemo-*exec.test</samp>
are executed three times, under three different libtool configurations:
<samp>cdemo-conf.test</samp> configures <samp>cdemo/libtool</samp> to build both
static and shared libraries (the default for platforms that support
both), <samp>cdemo-static.test</samp> builds only static libraries
(‘<samp>--disable-shared</samp>’), and <samp>cdemo-shared.test</samp> builds only
shared libraries (‘<samp>--disable-static</samp>’).
</p>
<p>The test <samp>cdemo-undef.test</samp> tests the generation of shared
libraries with undefined symbols on systems that allow this.
</p>
</dd>
<dt><samp>demo-conf.test</samp></dt>
<dt><samp>demo-make.test</samp></dt>
<dt><samp>demo-exec.test</samp></dt>
<dt><samp>demo-inst.test</samp></dt>
<dt><samp>demo-unst.test</samp></dt>
<dt><samp>demo-static.test</samp></dt>
<dt><samp>demo-static-make.test</samp></dt>
<dt><samp>demo-static-exec.test</samp></dt>
<dt><samp>demo-static-inst.test</samp></dt>
<dt><samp>demo-static-unst.test</samp></dt>
<dt><samp>demo-shared.test</samp></dt>
<dt><samp>demo-shared-make.test</samp></dt>
<dt><samp>demo-shared-exec.test</samp></dt>
<dt><samp>demo-shared-inst.test</samp></dt>
<dt><samp>demo-shared-unst.test</samp></dt>
<dt><samp>demo-nofast.test</samp></dt>
<dt><samp>demo-nofast-make.test</samp></dt>
<dt><samp>demo-nofast-exec.test</samp></dt>
<dt><samp>demo-nofast-inst.test</samp></dt>
<dt><samp>demo-nofast-unst.test</samp></dt>
<dt><samp>demo-pic.test</samp></dt>
<dt><samp>demo-pic-make.test</samp></dt>
<dt><samp>demo-pic-exec.test</samp></dt>
<dt><samp>demo-nopic.test</samp></dt>
<dt><samp>demo-nopic-make.test</samp></dt>
<dt><samp>demo-nopic-exec.test</samp></dt>
<dd><span id="index-demo_002dconf_002etest"></span>
<span id="index-demo_002dmake_002etest"></span>
<span id="index-demo_002dexec_002etest"></span>
<span id="index-demo_002dinst_002etest"></span>
<span id="index-demo_002dunst_002etest"></span>
<span id="index-demo_002dstatic_002etest"></span>
<span id="index-demo_002dstatic_002dmake_002etest"></span>
<span id="index-demo_002dstatic_002dexec_002etest"></span>
<span id="index-demo_002dstatic_002dinst_002etest"></span>
<span id="index-demo_002dstatic_002dunst_002etest"></span>
<span id="index-demo_002dshared_002etest"></span>
<span id="index-demo_002dshared_002dmake_002etest"></span>
<span id="index-demo_002dshared_002dexec_002etest"></span>
<span id="index-demo_002dshared_002dinst_002etest"></span>
<span id="index-demo_002dshared_002dunst_002etest"></span>
<span id="index-demo_002dnofast_002etest"></span>
<span id="index-demo_002dnofast_002dmake_002etest"></span>
<span id="index-demo_002dnofast_002dexec_002etest"></span>
<span id="index-demo_002dnofast_002dinst_002etest"></span>
<span id="index-demo_002dnofast_002dunst_002etest"></span>
<span id="index-demo_002dpic_002etest"></span>
<span id="index-demo_002dpic_002dmake_002etest"></span>
<span id="index-demo_002dpic_002dexec_002etest"></span>
<span id="index-demo_002dnopic_002etest"></span>
<span id="index-demo_002dnopic_002dmake_002etest"></span>
<span id="index-demo_002dnopic_002dexec_002etest"></span>
<p>These programs check to see that the <samp>tests/demo</samp> subdirectory of
the libtool distribution can be configured, built, installed, and
uninstalled correctly.
</p>
<p>The <samp>tests/demo</samp> subdirectory contains a demonstration of a trivial
package that uses libtool.  The tests matching <samp>demo-*make.test</samp>,
<samp>demo-*exec.test</samp>, <samp>demo-*inst.test</samp> and
<samp>demo-*unst.test</samp> are executed four times, under four different
libtool configurations: <samp>demo-conf.test</samp> configures
<samp>demo/libtool</samp> to build both static and shared libraries,
<samp>demo-static.test</samp> builds only static libraries
(<samp>--disable-shared</samp>), and <samp>demo-shared.test</samp> builds only
shared libraries (<samp>--disable-static</samp>).
<samp>demo-nofast.test</samp> configures <samp>demo/libtool</samp> to
disable the fast-install mode (<samp>--enable-fast-install=no</samp>).
<samp>demo-pic.test</samp> configures <samp>demo/libtool</samp> to
prefer building PIC code (<samp>--with-pic</samp>), <samp>demo-nopic.test</samp>
to prefer non-PIC code (<samp>--without-pic</samp>).
</p>
</dd>
<dt><samp>demo-deplibs.test</samp></dt>
<dd><span id="index-demo_002ddeplibs_002etest"></span>
<p>Many systems cannot link static libraries into shared libraries.
libtool uses a <code>deplibs_check_method</code> to prevent such cases.
This tests checks whether libtool’s <code>deplibs_check_method</code>
works properly.
</p>
</dd>
<dt><samp>demo-hardcode.test</samp></dt>
<dd><span id="index-demo_002dhardcode_002etest"></span>
<p>On all systems with shared libraries, the location of the library can be
encoded in executables that are linked against it see <a href="#Linking-executables">Linking executables</a>.  This test checks under what conditions your system
linker hardcodes the library location, and guarantees that they
correspond to libtool’s own notion of how your linker behaves.
</p>
</dd>
<dt><samp>demo-relink.test</samp></dt>
<dt><samp>depdemo-relink.test</samp></dt>
<dd><span id="index-demo_002drelink_002etest"></span>
<span id="index-depdemo_002drelink_002etest"></span>
<p>These tests check whether variable <code>shlibpath_overrides_runpath</code> is
properly set.  If the test fails, it will indicate what the variable should
have been set to.
</p>
</dd>
<dt><samp>demo-noinst-link.test</samp></dt>
<dd><span id="index-demo_002dnoinst_002dlink_002etest"></span>
<p>Checks whether libtool will not try to link with a previously installed
version of a library when it should be linking with a just-built one.
</p>
</dd>
<dt><samp>depdemo-conf.test</samp></dt>
<dt><samp>depdemo-make.test</samp></dt>
<dt><samp>depdemo-exec.test</samp></dt>
<dt><samp>depdemo-inst.test</samp></dt>
<dt><samp>depdemo-unst.test</samp></dt>
<dt><samp>depdemo-static.test</samp></dt>
<dt><samp>depdemo-static-make.test</samp></dt>
<dt><samp>depdemo-static-exec.test</samp></dt>
<dt><samp>depdemo-static-inst.test</samp></dt>
<dt><samp>depdemo-static-unst.test</samp></dt>
<dt><samp>depdemo-shared.test</samp></dt>
<dt><samp>depdemo-shared-make.test</samp></dt>
<dt><samp>depdemo-shared-exec.test</samp></dt>
<dt><samp>depdemo-shared-inst.test</samp></dt>
<dt><samp>depdemo-shared-unst.test</samp></dt>
<dt><samp>depdemo-nofast.test</samp></dt>
<dt><samp>depdemo-nofast-make.test</samp></dt>
<dt><samp>depdemo-nofast-exec.test</samp></dt>
<dt><samp>depdemo-nofast-inst.test</samp></dt>
<dt><samp>depdemo-nofast-unst.test</samp></dt>
<dd><span id="index-depdemo_002dconf_002etest"></span>
<span id="index-depdemo_002dmake_002etest"></span>
<span id="index-depdemo_002dexec_002etest"></span>
<span id="index-depdemo_002dinst_002etest"></span>
<span id="index-depdemo_002dunst_002etest"></span>
<span id="index-depdemo_002dstatic_002etest"></span>
<span id="index-depdemo_002dstatic_002dmake_002etest"></span>
<span id="index-depdemo_002dstatic_002dexec_002etest"></span>
<span id="index-depdemo_002dstatic_002dinst_002etest"></span>
<span id="index-depdemo_002dstatic_002dunst_002etest"></span>
<span id="index-depdemo_002dshared_002etest"></span>
<span id="index-depdemo_002dshared_002dmake_002etest"></span>
<span id="index-depdemo_002dshared_002dexec_002etest"></span>
<span id="index-depdemo_002dshared_002dinst_002etest"></span>
<span id="index-depdemo_002dshared_002dunst_002etest"></span>
<span id="index-depdemo_002dnofast_002etest"></span>
<span id="index-depdemo_002dnofast_002dmake_002etest"></span>
<span id="index-depdemo_002dnofast_002dexec_002etest"></span>
<span id="index-depdemo_002dnofast_002dinst_002etest"></span>
<span id="index-depdemo_002dnofast_002dunst_002etest"></span>
<p>These programs check to see that the <samp>tests/depdemo</samp> subdirectory
of the libtool distribution can be configured, built, installed, and
uninstalled correctly.
</p>
<p>The <samp>tests/depdemo</samp> subdirectory contains a demonstration of
inter-library dependencies with libtool.  The test programs link some
interdependent libraries.
</p>
<p>The tests matching <samp>depdemo-*make.test</samp>, <samp>depdemo-*exec.test</samp>,
<samp>depdemo-*inst.test</samp> and <samp>depdemo-*unst.test</samp> are executed
four times, under four different libtool configurations:
<samp>depdemo-conf.test</samp> configures <samp>depdemo/libtool</samp> to build both
static and shared libraries, <samp>depdemo-static.test</samp> builds only static
libraries (<samp>--disable-shared</samp>), and <samp>depdemo-shared.test</samp> builds
only shared libraries (<samp>--disable-static</samp>).
<samp>depdemo-nofast.test</samp> configures <samp>depdemo/libtool</samp> to
disable the fast-install mode (<samp>--enable-fast-install=no</samp>).
</p>
</dd>
<dt><samp>mdemo-conf.test</samp></dt>
<dt><samp>mdemo-make.test</samp></dt>
<dt><samp>mdemo-exec.test</samp></dt>
<dt><samp>mdemo-inst.test</samp></dt>
<dt><samp>mdemo-unst.test</samp></dt>
<dt><samp>mdemo-static.test</samp></dt>
<dt><samp>mdemo-static-make.test</samp></dt>
<dt><samp>mdemo-static-exec.test</samp></dt>
<dt><samp>mdemo-static-inst.test</samp></dt>
<dt><samp>mdemo-static-unst.test</samp></dt>
<dt><samp>mdemo-shared.test</samp></dt>
<dt><samp>mdemo-shared-make.test</samp></dt>
<dt><samp>mdemo-shared-exec.test</samp></dt>
<dt><samp>mdemo-shared-inst.test</samp></dt>
<dt><samp>mdemo-shared-unst.test</samp></dt>
<dd><span id="index-mdemo_002dconf_002etest"></span>
<span id="index-mdemo_002dmake_002etest"></span>
<span id="index-mdemo_002dexec_002etest"></span>
<span id="index-mdemo_002dinst_002etest"></span>
<span id="index-mdemo_002dunst_002etest"></span>
<span id="index-mdemo_002dstatic_002etest"></span>
<span id="index-mdemo_002dstatic_002dmake_002etest"></span>
<span id="index-mdemo_002dstatic_002dexec_002etest"></span>
<span id="index-mdemo_002dstatic_002dinst_002etest"></span>
<span id="index-mdemo_002dstatic_002dunst_002etest"></span>
<span id="index-mdemo_002dshared_002etest"></span>
<span id="index-mdemo_002dshared_002dmake_002etest"></span>
<span id="index-mdemo_002dshared_002dexec_002etest"></span>
<span id="index-mdemo_002dshared_002dinst_002etest"></span>
<span id="index-mdemo_002dshared_002dunst_002etest"></span>
<p>These programs check to see that the <samp>tests/mdemo</samp> subdirectory of
the libtool distribution can be configured, built, installed, and
uninstalled correctly.
</p>
<p>The <samp>tests/mdemo</samp> subdirectory contains a demonstration of a
package that uses libtool and the system independent dlopen wrapper
<samp>libltdl</samp> to load modules.  The library <samp>libltdl</samp> provides a
dlopen wrapper for various platforms (POSIX)
including support for dlpreopened modules (see <a href="#Dlpreopening">Dlpreopening</a>).
</p>
<p>The tests matching <samp>mdemo-*make.test</samp>, <samp>mdemo-*exec.test</samp>,
<samp>mdemo-*inst.test</samp> and <samp>mdemo-*unst.test</samp> are executed
three times, under three different libtool configurations:
<samp>mdemo-conf.test</samp> configures <samp>mdemo/libtool</samp> to build both
static and shared libraries, <samp>mdemo-static.test</samp> builds only static
libraries (<samp>--disable-shared</samp>), and <samp>mdemo-shared.test</samp> builds
only shared libraries (<samp>--disable-static</samp>).
</p>
</dd>
<dt><samp>mdemo-dryrun.test</samp></dt>
<dd><span id="index-mdemo_002ddryrun_002etest"></span>
<p>This test checks whether libtool’s <samp>--dry-run</samp> mode works properly.
</p>
</dd>
<dt><samp>mdemo2-conf.test</samp></dt>
<dt><samp>mdemo2-exec.test</samp></dt>
<dt><samp>mdemo2-make.test</samp></dt>
<dd><span id="index-mdemo2_002dconf_002etest"></span>
<span id="index-mdemo2_002dexec_002etest"></span>
<span id="index-mdemo2_002dmake_002etest"></span>
<p>These programs check to see that the <samp>tests/mdemo2</samp> subdirectory of
the libtool distribution can be configured, built, and executed
correctly.
</p>
<p>The <samp>tests/mdemo2</samp> directory contains a demonstration of a package
that attempts to link with a library (from the <samp>tests/mdemo</samp>
directory) that itself does dlopening of libtool modules.
</p>
</dd>
<dt><samp>link.test</samp></dt>
<dd><span id="index-link_002etest"></span>
<p>This test guarantees that linking directly against a non-libtool static
library works properly.
</p>
</dd>
<dt><samp>link-2.test</samp></dt>
<dd><span id="index-link_002d2_002etest"></span>
<p>This test makes sure that files ending in <samp>.lo</samp> are never linked
directly into a program file.
</p>
</dd>
<dt><samp>nomode.test</samp></dt>
<dd><span id="index-nomode_002etest"></span>
<p>Check whether we can actually get help for libtool.
</p>
</dd>
<dt><samp>objectlist.test</samp></dt>
<dd><span id="index-objectlist_002etest"></span>
<p>Check that a nonexistent objectlist file is properly detected.
</p>
</dd>
<dt><samp>pdemo-conf.test</samp></dt>
<dt><samp>pdemo-make.test</samp></dt>
<dt><samp>pdemo-exec.test</samp></dt>
<dt><samp>pdemo-inst.test</samp></dt>
<dd><span id="index-pdemo_002dconf_002etest"></span>
<span id="index-pdemo_002dmake_002etest"></span>
<span id="index-pdemo_002dexec_002etest"></span>
<span id="index-pdemo_002dinst_002etest"></span>
<p>These programs check to see that the <samp>tests/pdemo</samp> subdirectory of
the libtool distribution can be configured, built, and executed
correctly.
</p>
<p>The <samp>pdemo-conf.test</samp> lowers the <code>max_cmd_len</code> variable in the
generated libtool script to test the measures to evade command line
length limitations.
</p>
</dd>
<dt><samp>quote.test</samp></dt>
<dd><span id="index-quote_002etest"></span>
<p>This program checks libtool’s metacharacter quoting.
</p>
</dd>
<dt><samp>sh.test</samp></dt>
<dd><span id="index-sh_002etest"></span>
<p>Checks for some nonportable or dubious or undesired shell constructs in
shell scripts.
</p>
</dd>
<dt><samp>suffix.test</samp></dt>
<dd><span id="index-suffix_002etest"></span>
<p>When other programming languages are used with libtool (see <a href="#Other-languages">Other languages</a>), the source files may end in suffixes other than <samp>.c</samp>.
This test validates that libtool can handle suffixes for all the file
types that it supports, and that it fails when the suffix is invalid.
</p>
</dd>
<dt><samp>tagdemo-conf.test</samp></dt>
<dt><samp>tagdemo-make.test</samp></dt>
<dt><samp>tagdemo-exec.test</samp></dt>
<dt><samp>tagdemo-static.test</samp></dt>
<dt><samp>tagdemo-static-make.test</samp></dt>
<dt><samp>tagdemo-static-exec.test</samp></dt>
<dt><samp>tagdemo-shared.test</samp></dt>
<dt><samp>tagdemo-shared-make.test</samp></dt>
<dt><samp>tagdemo-shared-exec.test</samp></dt>
<dt><samp>tagdemo-undef.test</samp></dt>
<dt><samp>tagdemo-undef-make.test</samp></dt>
<dt><samp>tagdemo-undef-exec.test</samp></dt>
<dd><span id="index-tagdemo_002dconf_002etest"></span>
<span id="index-tagdemo_002dmake_002etest"></span>
<span id="index-tagdemo_002dexec_002etest"></span>
<span id="index-tagdemo_002dstatic_002etest"></span>
<span id="index-tagdemo_002dstatic_002dmake_002etest"></span>
<span id="index-tagdemo_002dstatic_002dexec_002etest"></span>
<span id="index-tagdemo_002dshared_002etest"></span>
<span id="index-tagdemo_002dshared_002dmake_002etest"></span>
<span id="index-tagdemo_002dshared_002dexec_002etest"></span>
<span id="index-tagdemo_002dundef_002etest"></span>
<span id="index-tagdemo_002dundef_002dmake_002etest"></span>
<span id="index-tagdemo_002dundef_002dexec_002etest"></span>
<p>These programs check to see that the <samp>tests/tagdemo</samp> subdirectory
of the libtool distribution can be configured, built, and executed
correctly.
</p>
<p>The <samp>tests/tagdemo</samp> directory contains a demonstration of a package
that uses libtool’s multi-language support through configuration tags.
It generates a library from C++ sources, which is then linked to a C++
program.
</p>
</dd>
<dt><samp>f77demo-conf.test</samp></dt>
<dt><samp>f77demo-make.test</samp></dt>
<dt><samp>f77demo-exec.test</samp></dt>
<dt><samp>f77demo-static.test</samp></dt>
<dt><samp>f77demo-static-make.test</samp></dt>
<dt><samp>f77demo-static-exec.test</samp></dt>
<dt><samp>f77demo-shared.test</samp></dt>
<dt><samp>f77demo-shared-make.test</samp></dt>
<dt><samp>f77demo-shared-exec.test</samp></dt>
<dd><span id="index-f77demo_002dconf_002etest"></span>
<span id="index-f77demo_002dmake_002etest"></span>
<span id="index-f77demo_002dexec_002etest"></span>
<span id="index-f77demo_002dstatic_002etest"></span>
<span id="index-f77demo_002dstatic_002dmake_002etest"></span>
<span id="index-f77demo_002dstatic_002dexec_002etest"></span>
<span id="index-f77demo_002dshared_002etest"></span>
<span id="index-f77demo_002dshared_002dmake_002etest"></span>
<span id="index-f77demo_002dshared_002dexec_002etest"></span>
<p>These programs check to see that the <samp>tests/f77demo</samp> subdirectory
of the libtool distribution can be configured, built, and executed
correctly.
</p>
<p>The <samp>tests/f77demo</samp> tests test Fortran 77 support in libtool by
creating libraries from Fortran 77 sources, and mixed Fortran and C
sources, and a Fortran 77 program to use the former library, and a C
program to use the latter library.
</p>
</dd>
<dt><samp>fcdemo-conf.test</samp></dt>
<dt><samp>fcdemo-make.test</samp></dt>
<dt><samp>fcdemo-exec.test</samp></dt>
<dt><samp>fcdemo-static.test</samp></dt>
<dt><samp>fcdemo-static-make.test</samp></dt>
<dt><samp>fcdemo-static-exec.test</samp></dt>
<dt><samp>fcdemo-shared.test</samp></dt>
<dt><samp>fcdemo-shared-make.test</samp></dt>
<dt><samp>fcdemo-shared-exec.test</samp></dt>
<dd><span id="index-fcdemo_002dconf_002etest"></span>
<span id="index-fcdemo_002dmake_002etest"></span>
<span id="index-fcdemo_002dexec_002etest"></span>
<span id="index-fcdemo_002dstatic_002etest"></span>
<span id="index-fcdemo_002dstatic_002dmake_002etest"></span>
<span id="index-fcdemo_002dstatic_002dexec_002etest"></span>
<span id="index-fcdemo_002dshared_002etest"></span>
<span id="index-fcdemo_002dshared_002dmake_002etest"></span>
<span id="index-fcdemo_002dshared_002dexec_002etest"></span>
<p>These programs check to see that the <samp>tests/fcdemo</samp> subdirectory
of the libtool distribution can be configured, built, and executed
correctly.
</p>
<p>The <samp>tests/fcdemo</samp> is similar to the <samp>tests/f77demo</samp>
directory, except that Fortran 90 is used in combination with the
‘<samp>FC</samp>’ interface provided by Autoconf and Automake.
</p>
</dd>
</dl>

<p>The new, Autotest-based test suite uses keywords to classify certain
test groups:
</p>
<dl compact="compact">
<dt>‘<samp>CXX</samp>’</dt>
<dt>‘<samp>F77</samp>’</dt>
<dt>‘<samp>FC</samp>’</dt>
<dt>‘<samp>GCJ</samp>’</dt>
<dd><p>The test group exercises one of these <code>libtool</code> language tags.
</p>
</dd>
<dt>‘<samp>autoconf</samp>’</dt>
<dt>‘<samp>automake</samp>’</dt>
<dd><p>These keywords denote that the respective external program is needed
by the test group.  The tests are typically skipped if the program is
not installed.  The ‘<samp>automake</samp>’ keyword may also denote use of the
<code>aclocal</code> program.
</p>
</dd>
<dt>‘<samp>interactive</samp>’</dt>
<dd><p>This test group may require user interaction on some systems.  Typically,
this means closing a popup window about a DLL load error on Windows.
</p>
</dd>
<dt>‘<samp>libltdl</samp>’</dt>
<dd><p>Denote that the <samp>libltdl</samp> library is exercised by the test group.
</p>
</dd>
<dt>‘<samp>libtool</samp>’</dt>
<dt>‘<samp>libtoolize</samp>’</dt>
<dd><p>Denote that the <code>libtool</code> or <code>libtoolize</code> scripts are
exercised by the test group, respectively.
</p>
</dd>
<dt>‘<samp>recursive</samp>’</dt>
<dd><p>Denote that this test group may recursively re-invoke the test suite
itself, with changed settings and maybe a changed <code>libtool</code>
script.  You may use the <code>INNER_TESTSUITEFLAGS</code> variable to pass
additional settings to this recursive invocation.  Typically, recursive
invocations delimit the set of tests with another keyword, for example
by passing <code>-k libtool</code> right before the expansion of the
<code>INNER_TESTSUITEFLAGS</code> variable (without an intervening space, so
you get the chance for further delimitation).
</p>
<p>Test groups with the keyword ‘<samp>recursive</samp>’ should not be denoted with
keywords, in order to avoid infinite recursion.  As a consequence,
recursive test groups themselves should never require user interaction,
while the test groups they invoke may do so.
</p></dd>
</dl>

<span id="index-check_002dinteractive"></span>
<span id="index-check_002dnoninteractive"></span>
<p>There is a convenience target ‘<samp>check-noninteractive</samp>’ that runs
all tests from both test suites that do not cause user interaction on
Windows.  Conversely, the target ‘<samp>check-interactive</samp>’ runs the
complement of tests and might require closing popup windows about DLL
load errors on Windows.
</p>

<hr>
<span id="When-tests-fail"></span><div class="header">
<p>
Previous: <a href="#Test-descriptions" accesskey="p" rel="prev">Test descriptions</a>, Up: <a href="#Libtool-test-suite" accesskey="u" rel="up">Libtool test suite</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="When-tests-fail-1"></span><h4 class="subsection">14.1.2 When tests fail</h4>
<span id="index-failed-tests"></span>
<span id="index-tests_002c-failed"></span>

<p>When the tests in the old test suite are run via <code>make check</code>,
output is caught in per-test <samp>tests/<var>test-name</var>.log</samp> files
and summarized in the <samp>test-suite.log</samp> file.  The exit status of each
program tells the <samp>Makefile</samp> whether or not the test succeeded.
</p>
<p>If a test fails, it means that there is either a programming error in
libtool, or in the test program itself.
</p>
<p>To investigate a particular test, you may run it directly, as you would
a normal program.  When the test is invoked in this way, it produces
output that may be useful in determining what the problem is.
</p>
<p>The new, Autotest-based test suite produces as output a file
<samp>tests/testsuite.log</samp> that contains information about failed
tests.
</p>
<p>You can pass options to the test suite through the <code>make</code>
variable <code>TESTSUITEFLAGS</code> (see <a href="https://www.gnu.org/software/autoconf/manual/autoconf.html#testsuite-Invocation">The Autoconf Manual</a> in <cite>The Autoconf Manual</cite>).
</p>

<hr>
<span id="Reporting-bugs"></span><div class="header">
<p>
Previous: <a href="#Libtool-test-suite" accesskey="p" rel="prev">Libtool test suite</a>, Up: <a href="#Troubleshooting" accesskey="u" rel="up">Troubleshooting</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Reporting-bugs-1"></span><h3 class="section">14.2 Reporting bugs</h3>
<span id="index-bug-reports"></span>
<span id="index-reporting-bugs"></span>
<span id="index-problem-reports"></span>

<p>If you think you have discovered a bug in libtool, you should think
twice: the libtool maintainer is notorious for passing the buck (or
maybe that should be “passing the bug”).  Libtool was invented to fix
known deficiencies in shared library implementations, so, in a way, most
of the bugs in libtool are actually bugs in other operating systems.
However, the libtool maintainer would definitely be happy to add support
for somebody else’s buggy operating system.  [I wish there was a good
way to do winking smiley-faces in Texinfo.]
</p>
<p>Genuine bugs in libtool include problems with shell script portability,
documentation errors, and failures in the test suite (see <a href="#Libtool-test-suite">Libtool test suite</a>).
</p>
<p>First, check the documentation and help screens to make sure that the
behaviour you think is a problem is not already mentioned as a feature.
</p>
<p>Then, you should read the Emacs guide to reporting bugs (see <a href="https://www.gnu.org/software/emacs/manual/html_mono/emacs.html#Bugs">Reporting Bugs</a> in <cite>The Emacs Manual</cite>).  Some of the details
listed there are specific to Emacs, but the principle behind them is a
general one.
</p>
<p>Finally, send a bug report to the Libtool bug reporting address <a href="mailto:bug-libtool@gnu.org">bug-libtool@gnu.org</a> with any appropriate
<em>facts</em>, such as test suite output (see <a href="#When-tests-fail">When tests fail</a>), all
the details needed to reproduce the bug, and a brief description of why
you think the behaviour is a bug.  Be sure to include the word
“libtool” in the subject line, as well as the version number you are
using (which can be found by typing <kbd>libtool --version</kbd>).
</p>
<hr>
<span id="Maintaining"></span><div class="header">
<p>
Next: <a href="#GNU-Free-Documentation-License" accesskey="n" rel="next">GNU Free Documentation License</a>, Previous: <a href="#Troubleshooting" accesskey="p" rel="prev">Troubleshooting</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Maintenance-notes-for-libtool"></span><h2 class="chapter">15 Maintenance notes for libtool</h2>

<p>This chapter contains information that the libtool maintainer finds
important.  It will be of no use to you unless you are considering
porting libtool to new systems, or writing your own libtool.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#New-ports" accesskey="1">New ports</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">How to port libtool to new systems.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Tested-platforms" accesskey="2">Tested platforms</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">When libtool was last tested.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Platform-quirks" accesskey="3">Platform quirks</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Information about different library systems.
</td></tr>
<tr><td align="left" valign="top">• <a href="#libtool-script-contents" accesskey="4">libtool script contents</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Configuration information that libtool uses.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Cheap-tricks" accesskey="5">Cheap tricks</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Making libtool maintainership easier.
</td></tr>
</tbody></table>

<hr>
<span id="New-ports"></span><div class="header">
<p>
Next: <a href="#Tested-platforms" accesskey="n" rel="next">Tested platforms</a>, Up: <a href="#Maintaining" accesskey="u" rel="up">Maintaining</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Porting-libtool-to-new-systems"></span><h3 class="section">15.1 Porting libtool to new systems</h3>

<p>Before you embark on porting libtool to an unsupported system, it is
worthwhile to send e-mail to the Libtool mailing list <a href="mailto:libtool@gnu.org">libtool@gnu.org</a>, to make sure that you are
not duplicating existing work.
</p>
<p>If you find that any porting documentation is missing, please complain!
Complaints with patches and improvements to the documentation, or to
libtool itself, are more than welcome.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#Information-sources" accesskey="1">Information sources</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Where to find relevant documentation
</td></tr>
<tr><td align="left" valign="top">• <a href="#Porting-inter_002dlibrary-dependencies" accesskey="2">Porting inter-library dependencies</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Implementation details explained
</td></tr>
</tbody></table>

<hr>
<span id="Information-sources"></span><div class="header">
<p>
Next: <a href="#Porting-inter_002dlibrary-dependencies" accesskey="n" rel="next">Porting inter-library dependencies</a>, Up: <a href="#New-ports" accesskey="u" rel="up">New ports</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Information-sources-1"></span><h4 class="subsection">15.1.1 Information sources</h4>

<p>Once it is clear that a new port is necessary, you’ll generally need the
following information:
</p>
<dl compact="compact">
<dt>canonical system name</dt>
<dd><p>You need the output of <code>config.guess</code> for this system, so that you
can make changes to the libtool configuration process without affecting
other systems.
</p>
</dd>
<dt>man pages for <code>ld</code> and <code>cc</code></dt>
<dd><p>These generally describe what flags are used to generate PIC, to create
shared libraries, and to link against only static libraries.  You may
need to follow some cross references to find the information that is
required.
</p>
</dd>
<dt>man pages for <code>ld.so</code>, <code>rtld</code>, or equivalent</dt>
<dd><p>These are a valuable resource for understanding how shared libraries are
loaded on the system.
</p>
</dd>
<dt>man page for <code>ldconfig</code>, or equivalent</dt>
<dd><p>This page usually describes how to install shared libraries.
</p>
</dd>
<dt>output from <kbd>ls -l /lib /usr/lib</kbd></dt>
<dd><p>This shows the naming convention for shared libraries on the system,
including what names should be symbolic links.
</p>
</dd>
<dt>any additional documentation</dt>
<dd><p>Some systems have special documentation on how to build and install
shared libraries.
</p></dd>
</dl>

<p>If you know how to program the Bourne shell, then you can complete the
port yourself; otherwise, you’ll have to find somebody with the relevant
skills who will do the work.  People on the libtool mailing list are
usually willing to volunteer to help you with new ports, so you can send
the information to them.
</p>
<p>To do the port yourself, you’ll definitely need to modify the
<code>libtool.m4</code> macros to make platform-specific changes to
the configuration process.  You should search that file for the
<code>PORTME</code> keyword, which will give you some hints on what you’ll
need to change.  In general, all that is involved is modifying the
appropriate configuration variables (see <a href="#libtool-script-contents">libtool script contents</a>).
</p>
<p>Your best bet is to find an already-supported system that is similar to
yours, and make your changes based on that.  In some cases, however,
your system will differ significantly from every other supported system,
and it may be necessary to add new configuration variables, and modify
the <code>ltmain.in</code> script accordingly.  Be sure to write to the
mailing list before you make changes to <code>ltmain.in</code>, since they may
have advice on the most effective way of accomplishing what you want.
</p>
<hr>
<span id="Porting-inter_002dlibrary-dependencies"></span><div class="header">
<p>
Previous: <a href="#Information-sources" accesskey="p" rel="prev">Information sources</a>, Up: <a href="#New-ports" accesskey="u" rel="up">New ports</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Porting-inter_002dlibrary-dependencies-support"></span><h4 class="subsection">15.1.2 Porting inter-library dependencies support</h4>
<span id="index-inter_002dlibrary-dependency"></span>
<span id="index-deplibs_005fcheck_005fmethod"></span>

<p>Since version 1.2c, libtool has re-introduced the ability to do
inter-library dependency on some platforms, thanks to a patch by Toshio
Kuratomi <a href="mailto:badger@prtr-13.ucsc.edu">badger@prtr-13.ucsc.edu</a>.  Here’s a shortened version
of the message that contained his patch:
</p>
<p>The basic architecture is this: in <samp>libtool.m4</samp>, the person who
writes libtool makes sure ‘<samp>$deplibs</samp>’ is included in
‘<samp>$archive_cmds</samp>’ somewhere and also sets the variable
‘<samp>$deplibs_check_method</samp>’, and maybe ‘<samp>$file_magic_cmd</samp>’ when
‘<samp>deplibs_check_method</samp>’ is file_magic.
</p>
<p>‘<samp>deplibs_check_method</samp>’ can be one of five things:
</p><dl compact="compact">
<dt>‘<samp>file_magic [<var>regex</var>]</samp>’</dt>
<dd><span id="index-file_005fmagic"></span>
<span id="index-file_005fmagic_005fcmd"></span>
<span id="index-file_005fmagic_005ftest_005ffile"></span>
<p>looks in the library link path for libraries that have the right
libname.  Then it runs ‘<samp>$file_magic_cmd</samp>’ on the library and checks
for a match against the extended regular expression <var>regex</var>.  When
<code>file_magic_test_file</code> is set by <samp>libtool.m4</samp>, it is used as an
argument to ‘<samp>$file_magic_cmd</samp>’ to verify whether the
regular expression matches its output, and warn the user otherwise.
</p>
</dd>
<dt>‘<samp>test_compile</samp>’</dt>
<dd><span id="index-test_005fcompile"></span>
<p>just checks whether it is possible to link a program out of a list of
libraries, and checks which of those are listed in the output of
<code>ldd</code>.  It is currently unused, and will probably be dropped in the
future.
</p>
</dd>
<dt>‘<samp>pass_all</samp>’</dt>
<dd><span id="index-pass_005fall"></span>
<p>will pass everything without any checking.  This may work on platforms
where code is position-independent by default and inter-library
dependencies are properly supported by the dynamic linker, for example,
on DEC OSF/1 3 and 4.
</p>
</dd>
<dt>‘<samp>none</samp>’</dt>
<dd><span id="index-none"></span>
<p>It causes deplibs to be reassigned ‘<samp>deplibs=""</samp>’.  That way
‘<samp>archive_cmds</samp>’ can contain deplibs on all platforms, but not have
deplibs used unless needed.
</p>
</dd>
<dt>‘<samp>unknown</samp>’</dt>
<dd><span id="index-unknown"></span>
<p>is the default for all systems unless overridden in <samp>libtool.m4</samp>.
It is the same as ‘<samp>none</samp>’, but it documents that we really don’t
know what the correct value should be, and we welcome patches that
improve it.
</p></dd>
</dl>

<p>Then in <samp>ltmain.in</samp> we have the real workhorse: a little
initialization and postprocessing (to setup/release variables for use
with eval echo libname_spec etc.) and a case statement that decides
the method that is being used.  This is the real code… I wish I could
condense it a little more, but I don’t think I can without function
calls.  I’ve mostly optimized it (moved things out of loops, etc.) but
there is probably some fat left.  I thought I should stop while I was
ahead, work on whatever bugs you discover, etc. before thinking about
more than obvious optimizations.
</p>
<hr>
<span id="Tested-platforms"></span><div class="header">
<p>
Next: <a href="#Platform-quirks" accesskey="n" rel="next">Platform quirks</a>, Previous: <a href="#New-ports" accesskey="p" rel="prev">New ports</a>, Up: <a href="#Maintaining" accesskey="u" rel="up">Maintaining</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Tested-platforms-1"></span><h3 class="section">15.2 Tested platforms</h3>

<p>This table describes when libtool was last known to be tested on
platforms where it claims to support shared libraries:
</p>
<div class="example">
<pre class="example">-------------------------------------------------------
canonical host name          compiler  libtool results
  (tools versions)                     release
-------------------------------------------------------
alpha-dec-osf5.1		cc	 1.3e	  ok (1.910)
alpha-dec-osf4.0f               gcc      1.3e     ok (1.910)
alpha-dec-osf4.0f               cc       1.3e     ok (1.910)
alpha-dec-osf3.2                gcc      0.8      ok
alpha-dec-osf3.2                cc       0.8      ok
alpha-dec-osf2.1                gcc      1.2f     NS
alpha*-unknown-linux-gnu        gcc      1.3b     ok
  (egcs-1.1.2, GNU ld 2.9.1.0.23)
hppa2.0w-hp-hpux11.00           cc       1.2f     ok
hppa2.0-hp-hpux10.20            cc       1.3.2    ok
hppa1.1-hp-hpux10.20            gcc      1.2f     ok
hppa1.1-hp-hpux10.20            cc       1.3c     ok (1.821)
hppa1.1-hp-hpux10.10            gcc      1.2f     ok
hppa1.1-hp-hpux10.10            cc       1.2f     ok
hppa1.1-hp-hpux9.07             gcc      1.2f     ok
hppa1.1-hp-hpux9.07             cc       1.2f     ok
hppa1.1-hp-hpux9.05             gcc      1.2f     ok
hppa1.1-hp-hpux9.05             cc       1.2f     ok
hppa1.1-hp-hpux9.01             gcc      1.2f     ok
hppa1.1-hp-hpux9.01             cc       1.2f     ok
i*86-*-beos                     gcc      1.2f     ok
i*86-*-bsdi4.0.1                gcc      1.3c     ok
  (gcc-2.7.2.1)
i*86-*-bsdi4.0                  gcc      1.2f     ok
i*86-*-bsdi3.1                  gcc      1.2e     NS
i*86-*-bsdi3.0                  gcc      1.2e     NS
i*86-*-bsdi2.1                  gcc      1.2e     NS
i*86-pc-cygwin                  gcc      1.3b     NS
  (egcs-1.1 stock b20.1 compiler)
i*86-*-dguxR4.20MU01            gcc      1.2      ok
i*86-*-freebsd4.3		gcc      1.3e     ok (1.912)
i*86-*-freebsdelf4.0            gcc      1.3c     ok
  (egcs-1.1.2)
i*86-*-freebsdelf3.2            gcc      1.3c     ok
  (gcc-2.7.2.1)
i*86-*-freebsdelf3.1            gcc      1.3c     ok
  (gcc-2.7.2.1)
i*86-*-freebsdelf3.0            gcc      1.3c     ok
i*86-*-freebsd3.0               gcc      1.2e     ok
i*86-*-freebsd2.2.8             gcc      1.3c     ok
  (gcc-2.7.2.1)
i*86-*-freebsd2.2.6             gcc      1.3b     ok
  (egcs-1.1 &amp; gcc-2.7.2.1, native ld)
i*86-*-freebsd2.1.5             gcc      0.5      ok
i*86-*-netbsd1.5                gcc      1.3e     ok (1.901)
  (egcs-1.1.2)
i*86-*-netbsd1.4                gcc      1.3c     ok
  (egcs-1.1.1)
i*86-*-netbsd1.4.3A             gcc      1.3e     ok (1.901)
i*86-*-netbsd1.3.3              gcc      1.3c     ok
  (gcc-2.7.2.2+myc2)
i*86-*-netbsd1.3.2              gcc      1.2e     ok
i*86-*-netbsd1.3I               gcc      1.2e     ok
  (egcs 1.1?)
i*86-*-netbsd1.2                gcc      0.9g     ok
i*86-*-linux-gnu		gcc	 1.3e	  ok (1.901)
  (Red Hat 7.0, gcc "2.96")
i*86-*-linux-gnu		gcc	 1.3e	  ok (1.911)
  (SuSE 7.0, gcc 2.95.2)
i*86-*-linux-gnulibc1           gcc      1.2f     ok
i*86-*-openbsd2.5               gcc      1.3c     ok
  (gcc-2.8.1)
i*86-*-openbsd2.4               gcc      1.3c     ok
  (gcc-2.8.1)
i*86-*-solaris2.7               gcc      1.3b     ok
  (egcs-1.1.2, native ld)
i*86-*-solaris2.6               gcc      1.2f     ok
i*86-*-solaris2.5.1             gcc      1.2f     ok
i*86-ncr-sysv4.3.03             gcc      1.2f     ok
i*86-ncr-sysv4.3.03             cc       1.2e     ok
  (cc -Hnocopyr)
i*86-pc-sco3.2v5.0.5		cc	 1.3c	  ok
i*86-pc-sco3.2v5.0.5		gcc	 1.3c	  ok
  (gcc 95q4c)
i*86-pc-sco3.2v5.0.5		gcc	 1.3c	  ok
  (egcs-1.1.2)
i*86-sco-sysv5uw7.1.1		gcc	 1.3e	  ok (1.901)
  (gcc-2.95.2, SCO linker)
i*86-UnixWare7.1.0-sysv5	cc	 1.3c	  ok
i*86-UnixWare7.1.0-sysv5	gcc	 1.3c	  ok
  (egcs-1.1.1)
m68k-next-nextstep3             gcc      1.2f     NS
m68k-sun-sunos4.1.1             gcc      1.2f     NS
  (gcc-2.5.7)
m88k-dg-dguxR4.12TMU01          gcc      1.2      ok
m88k-motorola-sysv4             gcc      1.3      ok
  (egcs-1.1.2)
mips-sgi-irix6.5                gcc      1.2f     ok
  (gcc-2.8.1)
mips-sgi-irix6.4                gcc      1.2f     ok
mips-sgi-irix6.3                gcc      1.3b     ok
  (egcs-1.1.2, native ld)
mips-sgi-irix6.3                cc       1.3b     ok
  (cc 7.0)
mips-sgi-irix6.2                gcc      1.2f     ok
mips-sgi-irix6.2                cc       0.9      ok
mips-sgi-irix5.3                gcc      1.2f     ok
  (egcs-1.1.1)
mips-sgi-irix5.3                gcc      1.2f     NS
  (gcc-2.6.3)
mips-sgi-irix5.3                cc       0.8      ok
mips-sgi-irix5.2                gcc      1.3b     ok
  (egcs-1.1.2, native ld)
mips-sgi-irix5.2                cc       1.3b     ok
  (cc 3.18)
mips-sni-sysv4			cc       1.3.5    ok
  (Siemens C-compiler)
mips-sni-sysv4			gcc      1.3.5    ok
  (gcc-2.7.2.3, GNU assembler 2.8.1, native ld)
mipsel-unknown-openbsd2.1       gcc      1.0      ok
powerpc-apple-darwin6.4         gcc      1.5      ok
(apple dev tools released 12/2002)
powerpc-ibm-aix4.3.1.0          gcc      1.2f     ok
  (egcs-1.1.1)
powerpc-ibm-aix4.2.1.0          gcc      1.2f     ok
  (egcs-1.1.1)
powerpc-ibm-aix4.1.5.0          gcc      1.2f     ok
  (egcs-1.1.1)
powerpc-ibm-aix4.1.5.0          gcc      1.2f     NS
  (gcc-2.8.1)
powerpc-ibm-aix4.1.4.0          gcc      1.0      ok
powerpc-ibm-aix4.1.4.0          xlc      1.0i     ok
rs6000-ibm-aix4.1.5.0           gcc      1.2f     ok
  (gcc-2.7.2)
rs6000-ibm-aix4.1.4.0           gcc      1.2f     ok
  (gcc-2.7.2)
rs6000-ibm-aix3.2.5             gcc      1.0i     ok
rs6000-ibm-aix3.2.5             xlc      1.0i     ok
sparc-sun-solaris2.8		gcc	 1.3e	  ok (1.913)
  (gcc-2.95.3 &amp; native ld)
sparc-sun-solaris2.7            gcc      1.3e     ok (1.913)
  (gcc-2.95.3 &amp; native ld)
sparc-sun-solaris2.6            gcc      1.3e     ok (1.913)
  (gcc-2.95.3 &amp; native ld)
sparc-sun-solaris2.5.1          gcc      1.3e     ok (1.911)
sparc-sun-solaris2.5            gcc      1.3b     ok
  (egcs-1.1.2, GNU ld 2.9.1 &amp; native ld)
sparc-sun-solaris2.5            cc       1.3b     ok
  (SC 3.0.1)
sparc-sun-solaris2.4            gcc      1.0a     ok
sparc-sun-solaris2.4            cc       1.0a     ok
sparc-sun-solaris2.3            gcc      1.2f     ok
sparc-sun-sunos4.1.4            gcc      1.2f     ok
sparc-sun-sunos4.1.4            cc       1.0f     ok
sparc-sun-sunos4.1.3_U1         gcc      1.2f     ok
sparc-sun-sunos4.1.3C           gcc      1.2f     ok
sparc-sun-sunos4.1.3            gcc      1.3b     ok
  (egcs-1.1.2, GNU ld 2.9.1 &amp; native ld)
sparc-sun-sunos4.1.3            cc       1.3b     ok
sparc-unknown-bsdi4.0           gcc      1.2c     ok
sparc-unknown-linux-gnulibc1    gcc      1.2f     ok
sparc-unknown-linux-gnu         gcc      1.3b     ok
  (egcs-1.1.2, GNU ld 2.9.1.0.23)
sparc64-unknown-linux-gnu       gcc      1.2f     ok

Notes:
- "ok" means "all tests passed".
- "NS" means "Not Shared", but OK for static libraries
</pre></div>

<p>Note: The vendor-distributed HP-UX <code>sed</code>(1) programs are horribly
broken, and cannot handle libtool’s requirements, so users may report
unusual problems.  There is no workaround except to install a working
<code>sed</code> (such as GNU <code>sed</code>) on these systems.
</p>
<p>Note: The vendor-distributed NCR MP-RAS <code>cc</code> programs emits
copyright on standard error that confuse tests on size of
<samp>conftest.err</samp>.  The workaround is to specify <code>CC</code>
when run <code>configure</code> with <kbd>CC='cc -Hnocopyr'</kbd>.
</p>
<hr>
<span id="Platform-quirks"></span><div class="header">
<p>
Next: <a href="#libtool-script-contents" accesskey="n" rel="next">libtool script contents</a>, Previous: <a href="#Tested-platforms" accesskey="p" rel="prev">Tested platforms</a>, Up: <a href="#Maintaining" accesskey="u" rel="up">Maintaining</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Platform-quirks-1"></span><h3 class="section">15.3 Platform quirks</h3>

<p>This section is dedicated to the sanity of the libtool maintainers.  It
describes the programs that libtool uses, how they vary from system to
system, and how to test for them.
</p>
<p>Because libtool is a shell script, it can be difficult to understand
just by reading it from top to bottom.  This section helps show why
libtool does things a certain way.  Combined with the scripts
themselves, you should have a better sense of how to improve libtool, or
write your own.
</p>
<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#References" accesskey="1">References</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Finding more information.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Compilers" accesskey="2">Compilers</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Creating object files from source files.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Reloadable-objects" accesskey="3">Reloadable objects</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Binding object files together.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Multiple-dependencies" accesskey="4">Multiple dependencies</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Removing duplicate dependent libraries.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Archivers" accesskey="5">Archivers</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Programs that create static archives.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Cross-compiling" accesskey="6">Cross compiling</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Issues that arise when cross compiling.
</td></tr>
<tr><td align="left" valign="top">• <a href="#File-name-conversion" accesskey="7">File name conversion</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Converting file names between platforms.
</td></tr>
<tr><td align="left" valign="top">• <a href="#Windows-DLLs" accesskey="8">Windows DLLs</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Windows header defines.
</td></tr>
</tbody></table>

<hr>
<span id="References"></span><div class="header">
<p>
Next: <a href="#Compilers" accesskey="n" rel="next">Compilers</a>, Up: <a href="#Platform-quirks" accesskey="u" rel="up">Platform quirks</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="References-1"></span><h4 class="subsection">15.3.1 References</h4>

<p>The following is a list of valuable documentation references:
</p>
<ul>
<li> SGI’s IRIX Manual Pages can be found at<br>
<a href="http://techpubs.sgi.com/cgi-bin/infosrch.cgi?cmd=browse&amp;db=man">http://techpubs.sgi.com/cgi-bin/infosrch.cgi?cmd=browse&amp;db=man</a>.

</li><li> Sun’s free service area
(<a href="http://www.sun.com/service/online/free.html">http://www.sun.com/service/online/free.html</a>) and documentation
server (<a href="http://docs.sun.com/">http://docs.sun.com/</a>).

</li><li> Compaq’s Tru64 UNIX online documentation is at<br>
(<a href="http://tru64unix.compaq.com/faqs/publications/pub_page/doc_list.html">http://tru64unix.compaq.com/faqs/publications/pub_page/doc_list.html</a>)
with C++ documentation at<br>
(<a href="http://tru64unix.compaq.com/cplus/docs/index.htm">http://tru64unix.compaq.com/cplus/docs/index.htm</a>).

</li><li> Hewlett-Packard has online documentation at
(<a href="http://docs.hp.com/index.html">http://docs.hp.com/index.html</a>).

</li><li> IBM has online documentation at
(<a href="http://www.rs6000.ibm.com/resource/aix_resource/Pubs/">http://www.rs6000.ibm.com/resource/aix_resource/Pubs/</a>).
</li></ul>

<hr>
<span id="Compilers"></span><div class="header">
<p>
Next: <a href="#Reloadable-objects" accesskey="n" rel="next">Reloadable objects</a>, Previous: <a href="#References" accesskey="p" rel="prev">References</a>, Up: <a href="#Platform-quirks" accesskey="u" rel="up">Platform quirks</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Compilers-1"></span><h4 class="subsection">15.3.2 Compilers</h4>

<p>The only compiler characteristics that affect libtool are the flags
needed (if any) to generate PIC objects.  In general, if a C compiler
supports certain PIC flags, then any derivative compilers support the
same flags.  Until there are some noteworthy exceptions to this rule,
this section will document only C compilers.
</p>
<p>The following C compilers have standard command line options, regardless
of the platform:
</p>
<dl compact="compact">
<dt><code>gcc</code></dt>
<dd>
<p>This is the GNU C compiler, which is also the system compiler for many
free operating systems (FreeBSD, GNU/Hurd, GNU/Linux, Lites, NetBSD, and
OpenBSD, to name a few).
</p>
<p>The <samp>-fpic</samp> or <samp>-fPIC</samp> flags can be used to generate
position-independent code.  <samp>-fPIC</samp> is guaranteed to generate
working code, but the code is slower on m68k, m88k, and SPARC chips.
However, using <samp>-fpic</samp> on those chips imposes arbitrary size limits
on the shared libraries.
</p></dd>
</dl>

<p>The rest of this subsection lists compilers by the operating system that
they are bundled with:
</p>

<dl compact="compact">
<dt><code>aix3*</code></dt>
<dt><code>aix4*</code></dt>
<dd><p>Most AIX compilers have no PIC flags, since AIX (with the exception of
AIX for IA-64) runs on PowerPC and RS/6000 chips. <a id="DOCF14" href="#FOOT14"><sup>14</sup></a>
</p>
</dd>
<dt><code>hpux10*</code></dt>
<dd><p>Use ‘<samp>+Z</samp>’ to generate PIC.
</p>
</dd>
<dt><code>osf3*</code></dt>
<dd><p>Digital/UNIX 3.x does not have PIC flags, at least not on the PowerPC
platform.
</p>
</dd>
<dt><code>solaris2*</code></dt>
<dd><p>Use <samp>-KPIC</samp> to generate PIC.
</p>
</dd>
<dt><code>sunos4*</code></dt>
<dd><p>Use <samp>-PIC</samp> to generate PIC.
</p></dd>
</dl>

<hr>
<span id="Reloadable-objects"></span><div class="header">
<p>
Next: <a href="#Multiple-dependencies" accesskey="n" rel="next">Multiple dependencies</a>, Previous: <a href="#Compilers" accesskey="p" rel="prev">Compilers</a>, Up: <a href="#Platform-quirks" accesskey="u" rel="up">Platform quirks</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Reloadable-objects-1"></span><h4 class="subsection">15.3.3 Reloadable objects</h4>

<p>On all known systems, a reloadable object can be created by running
<kbd>ld -r -o <var>output</var>.o <var>input1</var>.o <var>input2</var>.o</kbd>.  This
reloadable object may be treated as exactly equivalent to other
objects.
</p>
<hr>
<span id="Multiple-dependencies"></span><div class="header">
<p>
Next: <a href="#Archivers" accesskey="n" rel="next">Archivers</a>, Previous: <a href="#Reloadable-objects" accesskey="p" rel="prev">Reloadable objects</a>, Up: <a href="#Platform-quirks" accesskey="u" rel="up">Platform quirks</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Multiple-dependencies-1"></span><h4 class="subsection">15.3.4 Multiple dependencies</h4>

<p>On most modern platforms the order where dependent libraries are listed
has no effect on object generation.  In theory, there are platforms
that require libraries that provide missing symbols to other libraries
to be listed after those libraries whose symbols they provide.
</p>
<p>Particularly, if a pair of static archives each resolve some of the
other’s symbols, it might be necessary to list one of those archives
both before and after the other one.  Libtool does not currently cope
with this situation well, since duplicate libraries are removed from
the link line by default.  Libtool provides the command line option
<samp>--preserve-dup-deps</samp> to preserve all duplicate dependencies
in cases where it is necessary.
</p>
<hr>
<span id="Archivers"></span><div class="header">
<p>
Next: <a href="#Cross-compiling" accesskey="n" rel="next">Cross compiling</a>, Previous: <a href="#Multiple-dependencies" accesskey="p" rel="prev">Multiple dependencies</a>, Up: <a href="#Platform-quirks" accesskey="u" rel="up">Platform quirks</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Archivers-1"></span><h4 class="subsection">15.3.5 Archivers</h4>

<p>On all known systems, building a static library can be accomplished by
running <kbd>ar cr lib<var>name</var>.a <var>obj1</var>.o <var>obj2</var>.o …</kbd>,
where the <samp>.a</samp> file is the output library, and each <samp>.o</samp> file is an
object file.
</p>
<p>On all known systems, if there is a program named <code>ranlib</code>, then it
must be used to “bless” the created library before linking against it,
with the <kbd>ranlib lib<var>name</var>.a</kbd> command.  Some systems, like Irix,
use the <code>ar ts</code> command, instead.
</p>
<hr>
<span id="Cross-compiling"></span><div class="header">
<p>
Next: <a href="#File-name-conversion" accesskey="n" rel="next">File name conversion</a>, Previous: <a href="#Archivers" accesskey="p" rel="prev">Archivers</a>, Up: <a href="#Platform-quirks" accesskey="u" rel="up">Platform quirks</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Cross-compiling-1"></span><h4 class="subsection">15.3.6 Cross compiling</h4>
<span id="index-cross-compile"></span>

<p>Most build systems support the ability to compile libraries and applications
on one platform for use on a different platform, provided a compiler capable
of generating the appropriate output is available.  In such cross compiling
scenarios, the platform where the libraries or applications are compiled
is called the <em>build platform</em>, while the platform where the libraries
or applications are intended to be used or executed is called the
<em>host platform</em>.
<a href="https://www.gnu.org/software/automake/manual/automake.html#GNU-Build-System">The GNU Build System</a> in <cite>The Automake Manual</cite>,
of which libtool is a part, supports cross compiling via arguments passed to
the configure script: <samp>--build=...</samp> and <samp>--host=...</samp>. However,
when the build platform and host platform are very different, libtool is
required to make certain accommodations to support these scenarios.
</p>
<p>In most cases, because the build platform and host platform differ, the
cross-compiled libraries and executables can’t be executed or tested on the
build platform where they were compiled.  The testsuites of most build systems
will often skip any tests that involve executing such foreign executables when
cross-compiling.  However, if the build platform and host platform are
sufficiently similar, it is often possible to run cross-compiled applications.
Libtool’s own testsuite often attempts to execute cross-compiled tests, but
will mark any failures as <em>skipped</em> since the failure might simply be due
to the differences between the two platforms.
</p>
<p>In addition to cases where the host platform and build platform are extremely
similar (e.g. ‘<samp>i586-pc-linux-gnu</samp>’ and ‘<samp>i686-pc-linux-gnu</samp>’), there is
another case where cross-compiled host applications may be executed on the
build platform.  This is possible when the build platform supports an emulation
or API-enhanced environment for the host platform.  One example of this
situation would be if the build platform were MinGW, and the host platform were
Cygwin (or vice versa).  Both of these platforms can actually operate within a
single Windows instance, so Cygwin applications can be launched from a MinGW
context, and vice versa—provided certain care is taken.  Another example
would be if the build platform were GNU/Linux on an x86 32bit processor, and
the host platform were MinGW.  In this situation, the
<a href="http://www.winehq.org/">Wine</a> environment can be used to launch Windows
applications from the GNU/Linux operating system; again, provided certain care
is taken.
</p>
<p>One particular issue occurs when a Windows platform such as MinGW, Cygwin, or
MSYS is the host or build platform, while the other platform is a Unix-style
system.  In these cases, there are often conflicts between the format of the
file names and paths expected within host platform libraries and executables,
and those employed on the build platform.
</p>
<p>This situation is best described using a concrete example: suppose the build
platform is GNU/Linux with canonical triplet ‘<samp>i686-pc-linux-gnu</samp>’.  Suppose
further that the host platform is MinGW with canonical triplet
‘<samp>i586-pc-mingw32</samp>’.  On the GNU/Linux platform there is a cross compiler
following the usual naming conventions of such compilers, where the compiler
name is prefixed by the host canonical triplet (or suitable alias).  (For more
information concerning canonical triplets and platform aliases, see
<a href="https://www.gnu.org/software/autoconf/manual/autoconf.html#Specifying-Target-Triplets">Specifying Target Triplets</a> in <cite>The Autoconf Manual</cite> and <a href="https://www.gnu.org/software/autoconf/manual/autoconf.html#Canonicalizing">Canonicalizing</a> in <cite>The Autoconf Manual</cite>)  In this case, the C compiler is named
‘<samp>i586-pc-mingw32-gcc</samp>’.
</p>
<p>As described in <a href="#Wrapper-executables">Wrapper executables</a>, for the MinGW host platform libtool
uses a wrapper executable to set various environment variables before launching
the actual program executable.  Like the program executable, the wrapper
executable is cross-compiled for the host platform (that is, for MinGW).  As
described above, ordinarily a host platform executable cannot be executed on
the build platform, but in this case the Wine environment could be used to
launch the MinGW application from GNU/Linux.  However, the wrapper executable,
as a host platform (MinGW) application, must set the <code>PATH</code> variable so
that the true application’s dependent libraries can be located—but the
contents of the <code>PATH</code> variable must be structured for MinGW.  Libtool
must use the Wine file name mapping facilities to determine the correct value
so that the wrapper executable can set the <code>PATH</code> variable to point to the
correct location.
</p>
<p>For example, suppose we are compiling an application in <samp>/var/tmp</samp> on
GNU/Linux, using separate source code and build directories:
</p>
<div class="example">
<table>
<tbody><tr><td width="50%"><pre class="example"><samp>/var/tmp/foo-1.2.3/app/</samp></pre></td><td width="50%"><pre class="example">(application source code)</pre></td></tr>
<tr><td width="50%"><pre class="example"><samp>/var/tmp/foo-1.2.3/lib/</samp></pre></td><td width="50%"><pre class="example">(library source code)</pre></td></tr>
<tr><td width="50%"><pre class="example"><samp>/var/tmp/BUILD/app/</samp></pre></td><td width="50%"><pre class="example">(application build objects here)</pre></td></tr>
<tr><td width="50%"><pre class="example"><samp>/var/tmp/BUILD/lib/</samp></pre></td><td width="50%"><pre class="example">(library build objects here)</pre></td></tr>
</tbody></table>
</div>

<p>Since the library will be built in <samp>/var/tmp/BUILD/lib</samp>, the wrapper
executable (which will be in <samp>/var/tmp/BUILD/app</samp>) must add that
directory to <code>PATH</code> (actually, it must add the directory named
<var>objdir</var> under <samp>/var/tmp/BUILD/lib</samp>, but we’ll ignore that detail
for now).  However, Windows does not have a concept of Unix-style file or
directory names such as <samp>/var/tmp/BUILD/lib</samp>.  Therefore, Wine provides
a mapping from Windows file names such as <samp>C:\Program Files</samp> to specific
Unix-style file names.  Wine also provides a utility that can be used to map
Unix-style file names to Windows file names.
</p>
<p>In this case, the wrapper executable should actually add the value
</p>
<div class="example">
<pre class="example">Z:\var\tmp\BUILD\lib
</pre></div>

<p>to the <code>PATH</code>.  libtool contains support for path conversions of this
type, for a certain limited set of build and host platform combinations. In
this case, libtool will invoke Wine’s <code>winepath</code> utility to ensure that
the correct <code>PATH</code> value is used.  See <a href="#File-name-conversion">File name conversion</a>.
</p>
<hr>
<span id="File-name-conversion"></span><div class="header">
<p>
Next: <a href="#Windows-DLLs" accesskey="n" rel="next">Windows DLLs</a>, Previous: <a href="#Cross-compiling" accesskey="p" rel="prev">Cross compiling</a>, Up: <a href="#Platform-quirks" accesskey="u" rel="up">Platform quirks</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="File-name-conversion-1"></span><h4 class="subsection">15.3.7 File name conversion</h4>
<span id="index-file-name-conversion"></span>
<span id="index-path-conversion"></span>

<p>In certain situations, libtool must convert file names and paths between
formats appropriate to different platforms.  Usually this occurs when
cross-compiling, and affects only the ability to launch host platform
executables on the build platform using an emulation or API-enhancement
environment such as Wine.  Failure to convert paths
(see <a href="#File-Name-Conversion-Failure">File Name Conversion Failure</a>) will cause a warning to be issued, but
rarely causes the build to fail—and should have no affect on the compiled
products, once installed properly on the host platform.  For more information,
see <a href="#Cross-compiling">Cross compiling</a>.
</p>
<p>However, file name conversion may also occur in another scenario: when using a
Unix emulation system on Windows (such as Cygwin or MSYS), combined with a
native Windows compiler such as MinGW or MSVC.  Only a limited set of such
scenarios are currently supported; in other cases file name conversion is
skipped.  The lack of file name conversion usually means that uninstalled
executables can’t be launched, but only rarely causes the build to fail
(see <a href="#File-Name-Conversion-Failure">File Name Conversion Failure</a>).
</p>
<p>libtool supports file name conversion in the following scenarios:
</p>
<table>
<thead><tr><th width="25%">build platform</th><th width="25%">host platform</th><th width="50%">Notes</th></tr></thead>
<tbody><tr><td width="25%">MinGW (MSYS)</td><td width="25%">MinGW (Windows)</td><td width="50%">see <a href="#Native-MinGW-File-Name-Conversion">Native MinGW File Name Conversion</a></td></tr>
<tr><td width="25%">Cygwin</td><td width="25%">MinGW (Windows)</td><td width="50%">see <a href="#Cygwin_002fWindows-File-Name-Conversion">Cygwin/Windows File Name Conversion</a></td></tr>
<tr><td width="25%">Unix + Wine</td><td width="25%">MinGW (Windows)</td><td width="50%">Requires Wine. See <a href="#Unix_002fWindows-File-Name-Conversion">Unix/Windows File Name Conversion</a>.</td></tr>
<tr><td width="25%">MinGW (MSYS)</td><td width="25%">Cygwin</td><td width="50%">Requires <code>LT_CYGPATH</code>. See <a href="#LT_005fCYGPATH">LT_CYGPATH</a>. Provided for testing
purposes only.</td></tr>
<tr><td width="25%">Unix + Wine</td><td width="25%">Cygwin</td><td width="50%">Requires both Wine and <code>LT_CYGPATH</code>, but does not yet work with
Cygwin 1.7.7 and Wine-1.2.
See <a href="#Unix_002fWindows-File-Name-Conversion">Unix/Windows File Name Conversion</a>, and <a href="#LT_005fCYGPATH">LT_CYGPATH</a>.</td></tr>
</tbody></table>

<table class="menu" border="0" cellspacing="0">
<tbody><tr><td align="left" valign="top">• <a href="#File-Name-Conversion-Failure" accesskey="1">File Name Conversion Failure</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">What happens when file name conversion fails
</td></tr>
<tr><td align="left" valign="top">• <a href="#Native-MinGW-File-Name-Conversion" accesskey="2">Native MinGW File Name Conversion</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">MSYS file name conversion idiosyncrasies
</td></tr>
<tr><td align="left" valign="top">• <a href="#Cygwin_002fWindows-File-Name-Conversion" accesskey="3">Cygwin/Windows File Name Conversion</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Using <code>cygpath</code> to convert Cygwin file names
</td></tr>
<tr><td align="left" valign="top">• <a href="#Unix_002fWindows-File-Name-Conversion" accesskey="4">Unix/Windows File Name Conversion</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Using Wine to convert Unix paths
</td></tr>
<tr><td align="left" valign="top">• <a href="#LT_005fCYGPATH" accesskey="5">LT_CYGPATH</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Invoking <code>cygpath</code> from other environments
</td></tr>
<tr><td align="left" valign="top">• <a href="#Cygwin-to-MinGW-Cross" accesskey="6">Cygwin to MinGW Cross</a></td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Other notes concerning MinGW cross
</td></tr>
</tbody></table>

<hr>
<span id="File-Name-Conversion-Failure"></span><div class="header">
<p>
Next: <a href="#Native-MinGW-File-Name-Conversion" accesskey="n" rel="next">Native MinGW File Name Conversion</a>, Up: <a href="#File-name-conversion" accesskey="u" rel="up">File name conversion</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="File-Name-Conversion-Failure-1"></span><h4 class="subsubsection">15.3.7.1 File Name Conversion Failure</h4>
<span id="index-File-Name-Conversion-_002d-Failure"></span>
<span id="index-Path-Conversion-_002d-Failure"></span>

<p>In most cases, file name conversion is not needed or attempted.  However, when
libtool detects that a specific combination of build and host platform does
require file name conversion, it is possible that the conversion may fail.
In these cases, you may see a warning such as the following:
</p>
<div class="example">
<pre class="example">Could not determine the host file name corresponding to
  `... a file name ...'
Continuing, but uninstalled executables may not work.
</pre></div>

<p>or
</p>
<div class="example">
<pre class="example">Could not determine the host path corresponding to
  `... a path ...'
Continuing, but uninstalled executables may not work.
</pre></div>

<p>This should not cause the build to fail.  At worst, it means that the wrapper
executable will specify file names or paths appropriate for the build platform.
Since those are not appropriate for the host platform, the uninstalled
executables would not operate correctly, even when the wrapper executable is
launched via the appropriate emulation or API-enhancement (e.g. Wine).  Simply
install the executables on the host platform, and execute them there.
</p>
<hr>
<span id="Native-MinGW-File-Name-Conversion"></span><div class="header">
<p>
Next: <a href="#Cygwin_002fWindows-File-Name-Conversion" accesskey="n" rel="next">Cygwin/Windows File Name Conversion</a>, Previous: <a href="#File-Name-Conversion-Failure" accesskey="p" rel="prev">File Name Conversion Failure</a>, Up: <a href="#File-name-conversion" accesskey="u" rel="up">File name conversion</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Native-MinGW-File-Name-Conversion-1"></span><h4 class="subsubsection">15.3.7.2 Native MinGW File Name Conversion</h4>
<span id="index-File-Name-Conversion-_002d-MinGW"></span>
<span id="index-Path-Conversion-_002d-MinGW"></span>
<span id="index-MSYS"></span>

<p>MSYS is a Unix emulation environment for Windows, and is specifically designed
such that in normal usage it <em>pretends</em> to be MinGW or native Windows,
but understands Unix-style file names and paths, and supports standard Unix
tools and shells.  Thus, “native” MinGW builds are actually an odd sort of
cross-compile, from an MSYS Unix emulation environment “pretending” to be
MinGW, to actual native Windows.
</p>
<p>When an MSYS shell launches a native Windows executable (as opposed to other
<em>MSYS</em> executables), it uses a system of heuristics to detect any
command-line arguments that contain file names or paths.  It automatically
converts these file names from the MSYS (Unix-like) format, to the
corresponding Windows file name, before launching the executable.  However,
this auto-conversion facility is only available when using the MSYS runtime
library.  The wrapper executable itself is a MinGW application (that is, it
does not use the MSYS runtime library).  The wrapper executable must set
<code>PATH</code> to, and call <code>_spawnv</code> with, values that have already been
converted from MSYS format to Windows.  Thus, when libtool writes the source
code for the wrapper executable, it must manually convert MSYS paths to
Windows format, so that the Windows values can be hard-coded into the wrapper
executable.
</p>
<hr>
<span id="Cygwin_002fWindows-File-Name-Conversion"></span><div class="header">
<p>
Next: <a href="#Unix_002fWindows-File-Name-Conversion" accesskey="n" rel="next">Unix/Windows File Name Conversion</a>, Previous: <a href="#Native-MinGW-File-Name-Conversion" accesskey="p" rel="prev">Native MinGW File Name Conversion</a>, Up: <a href="#File-name-conversion" accesskey="u" rel="up">File name conversion</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Cygwin_002fWindows-File-Name-Conversion-1"></span><h4 class="subsubsection">15.3.7.3 Cygwin/Windows File Name Conversion</h4>
<span id="index-File-Name-Conversion-_002d-Cygwin-to-Windows"></span>
<span id="index-Path-Conversion-_002d-Cygwin-to-Windows"></span>

<p>Cygwin provides a Unix emulation environment for Windows.  As part of that
emulation, it provides a file system mapping that presents the Windows file
system in a Unix-compatible manner.  Cygwin also provides a utility
<code>cygpath</code> that can be used to convert file names and paths between
the two representations.  In a correctly configured Cygwin installation,
<code>cygpath</code> is always present, and is in the <code>PATH</code>.
</p>
<p>Libtool uses <code>cygpath</code> to convert from Cygwin (Unix-style) file names
and paths to Windows format when the build platform is Cygwin and the host
platform is MinGW.
</p>
<p>When the host platform is Cygwin, but the build platform is MSYS or some Unix
system, libtool also uses <code>cygpath</code> to convert from Windows to Cygwin
format (after first converting from the build platform format to Windows format;
See <a href="#Native-MinGW-File-Name-Conversion">Native MinGW File Name Conversion</a>, and
<a href="#Unix_002fWindows-File-Name-Conversion">Unix/Windows File Name Conversion</a>.)  Because the build platform is not
Cygwin, <code>cygpath</code> is not (and should not be) in the <code>PATH</code>.
Therefore, in this configuration the environment variable <code>LT_CYGPATH</code> is
required. See <a href="#LT_005fCYGPATH">LT_CYGPATH</a>.
</p>
<hr>
<span id="Unix_002fWindows-File-Name-Conversion"></span><div class="header">
<p>
Next: <a href="#LT_005fCYGPATH" accesskey="n" rel="next">LT_CYGPATH</a>, Previous: <a href="#Cygwin_002fWindows-File-Name-Conversion" accesskey="p" rel="prev">Cygwin/Windows File Name Conversion</a>, Up: <a href="#File-name-conversion" accesskey="u" rel="up">File name conversion</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Unix_002fWindows-File-Name-Conversion-1"></span><h4 class="subsubsection">15.3.7.4 Unix/Windows File Name Conversion</h4>
<span id="index-File-Name-Conversion-_002d-Unix-to-Windows"></span>
<span id="index-Path-Conversion-_002d-Unix-to-Windows"></span>


<p><a href="http://www.winehq.org/">Wine</a> provides an interpretation environment for
some Unix platforms where Windows applications can be executed.  It provides
a mapping between the Unix file system and a virtual Windows file system used
by the Windows programs.  For the file name conversion to work, Wine must be
installed and properly configured on the build platform, and the
<code>winepath</code> application must be in the build platform’s <code>PATH</code>.  In
addition, on 32bit GNU/Linux it is usually helpful if the binfmt extension is
enabled.
</p>
<hr>
<span id="LT_005fCYGPATH"></span><div class="header">
<p>
Next: <a href="#Cygwin-to-MinGW-Cross" accesskey="n" rel="next">Cygwin to MinGW Cross</a>, Previous: <a href="#Unix_002fWindows-File-Name-Conversion" accesskey="p" rel="prev">Unix/Windows File Name Conversion</a>, Up: <a href="#File-name-conversion" accesskey="u" rel="up">File name conversion</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="LT_005fCYGPATH-1"></span><h4 class="subsubsection">15.3.7.5 LT_CYGPATH</h4>
<span id="index-LT_005fCYGPATH"></span>

<p>For some cross-compile configurations (where the host platform is Cygwin), the
<code>cygpath</code> program is used to convert file names from the build platform
notation to the Cygwin form (technically, this conversion is from Windows
notation to Cygwin notation; the conversion from the build platform format
to Windows notation is performed via other means).  However, because the
<code>cygpath</code> program is not (and should not be) in the <code>PATH</code> on
the build platform, <code>LT_CYGPATH</code> must specify the full build platform
file name (that is, the full Unix or MSYS file name) of the <code>cygpath</code>
program.
</p>
<p>The reason <code>cygpath</code> should not be in the build platform <code>PATH</code> is
twofold: first, <code>cygpath</code> is usually installed in the same directory as
many other Cygwin executables, such as <code>sed</code>, <code>cp</code>, etc.  If
the build platform environment had this directory in its <code>PATH</code>, then these
Cygwin versions of common Unix utilities might be used in preference to the
ones provided by the build platform itself, with deleterious effects.  Second,
especially when Cygwin-1.7 or later is used, multiple Cygwin installations can
coexist within the same Windows instance.  Each installation will have separate
“mount tables” specified in <samp><var>CYGROOT-N</var>/etc/fstab</samp>.  These
<em>mount tables</em> control how that instance of Cygwin will map Windows file
names and paths to Cygwin form.  Each installation’s <code>cygpath</code> utility
automatically deduces the appropriate <samp>/etc/fstab</samp> file.  Since each
<samp><var>CYGROOT-N</var>/etc/fstab</samp> mount table may specify different mappings, it
matters what <code>cygpath</code> is used.
</p>
<p>Note that <code>cygpath</code> is a Cygwin application; to execute this tool from
Unix requires a working and properly configured Wine installation, as well
as enabling the GNU/Linux <code>binfmt</code> extension.  Furthermore, the Cygwin
<code>setup.exe</code> tool should have been used, via Wine, to properly install
Cygwin into the Wine file system (and registry).
</p>
<p>Unfortunately, Wine support for Cygwin is intermittent.  Recent releases of
Cygwin (1.7 and above) appear to require more Windows API support than Wine
provides (as of Wine version 1.2); most Cygwin applications fail to execute.
This includes <code>cygpath</code> itself.  Hence, it is best <em>not</em> to use
the LT_CYGPATH machinery in libtool when performing Unix to Cygwin
cross-compiles.  Similarly, it is best <em>not</em> to enable the GNU/Linux binfmt
support in this configuration, because while Wine will fail to execute the
compiled Cygwin applications, it will still exit with status zero.  This tends
to confuse build systems and test suites (including libtool’s own testsuite,
resulting in spurious reported failures).  Wine support for the older
Cygwin-1.5 series appears satisfactory, but the Cygwin team no longer supports
Cygwin-1.5.  It is hoped that Wine will eventually be improved such that
Cygwin-1.7 will again operate correctly under Wine.  Until then, libtool will
report warnings as described in see <a href="#File-Name-Conversion-Failure">File Name Conversion Failure</a> in these
scenarios.
</p>
<p>However, <code>LT_CYGPATH</code> is also used for the MSYS to Cygwin cross compile
scenario, and operates as expected.
</p>
<hr>
<span id="Cygwin-to-MinGW-Cross"></span><div class="header">
<p>
Previous: <a href="#LT_005fCYGPATH" accesskey="p" rel="prev">LT_CYGPATH</a>, Up: <a href="#File-name-conversion" accesskey="u" rel="up">File name conversion</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Cygwin-to-MinGW-Cross-1"></span><h4 class="subsubsection">15.3.7.6 Cygwin to MinGW Cross</h4>
<span id="index-Cygwin-to-MinGW-Cross"></span>

<p>There are actually three different scenarios that could all legitimately be
called a “Cygwin to MinGW” cross compile.  The current (and standard)
definition is when there is a compiler that produces native Windows libraries
and applications, but which itself is a Cygwin application, just as would be
expected in any other cross compile setup.
</p>
<p>However, historically there were two other definitions, which we will refer
to as the <em>fake</em> one, and the <em>lying</em> one.
</p>
<p>In the <em>fake</em> Cygwin to MinGW cross compile case, you actually use a
native MinGW compiler, but you do so from within a Cygwin environment:
</p>
<div class="example">
<pre class="example"><kbd>export PATH="/c/MinGW/bin:${PATH}"</kbd>
<kbd>configure --build=i686-pc-cygwin \
	--host=mingw32 \
	NM=/c/MinGW/bin/nm.exe</kbd>
</pre></div>

<p>In this way, the build system “knows” that you are cross compiling, and the
file name conversion logic will be used.  However, because the tools
(<code>mingw32-gcc</code>, <code>nm</code>, <code>ar</code>) used are actually native
Windows applications, they will not understand any Cygwin (that is, Unix-like)
absolute file names passed as command line arguments (and, unlike MSYS, Cygwin
does not automatically convert such arguments).  However, so long as only
relative file names are used in the build system, and non-Windows-supported
Unix idioms such as symlinks and mount points are avoided, this scenario should
work.
</p>
<p>If you must use absolute file names, you will have to force Libtool to convert
file names for the toolchain in this case, by doing the following before you
run configure:
</p>
<div class="example">
<pre class="example"><kbd>export lt_cv_to_tool_file_cmd=func_convert_file_cygwin_to_w32</kbd>
</pre></div>
<span id="index-lt_005fcv_005fto_005ftool_005ffile_005fcmd"></span>
<span id="index-func_005fconvert_005ffile_005fcygwin_005fto_005fw32"></span>

<p>In the <em>lying</em> Cygwin to MinGW cross compile case, you lie to the
build system:
</p>
<div class="example">
<pre class="example"><kbd>export PATH="/c/MinGW/bin:${PATH}"</kbd>
<kbd>configure --build=i686-pc-mingw32 \
	--host=i686-pc-mingw32 \
	--disable-dependency-tracking</kbd>
</pre></div>

<p>and claim that the build platform is MinGW, even though you are actually
running under <em>Cygwin</em> and not MinGW.  In this case, libtool does
<em>not</em> know that you are performing a cross compile, and thinks instead
that you are performing a native MinGW build.  However, as described in
(see <a href="#Native-MinGW-File-Name-Conversion">Native MinGW File Name Conversion</a>), that scenario triggers an “MSYS
to Windows” file name conversion.  This, of course, is the wrong conversion
since we are actually running under Cygwin.  Also, the toolchain is expecting
Windows file names (not Cygwin) but unless told so Libtool will feed Cygwin
file names to the toolchain in this case.  To force the correct file name
conversions in this situation, you should do the following <em>before</em>
running configure:
</p>
<div class="example">
<pre class="example"><kbd>export lt_cv_to_host_file_cmd=func_convert_file_cygwin_to_w32</kbd>
<kbd>export lt_cv_to_tool_file_cmd=func_convert_file_cygwin_to_w32</kbd>
</pre></div>
<span id="index-lt_005fcv_005fto_005fhost_005ffile_005fcmd"></span>
<span id="index-lt_005fcv_005fto_005ftool_005ffile_005fcmd-1"></span>
<span id="index-func_005fconvert_005ffile_005fcygwin_005fto_005fw32-1"></span>

<p>Note that this relies on internal implementation details of libtool, and
is subject to change.  Also, <code>--disable-dependency-tracking</code> is required,
because otherwise the MinGW GCC will generate dependency files that contain
Windows file names.  This, in turn, will confuse the Cygwin <code>make</code>
program, which does not accept Windows file names:
</p>
<div class="example">
<pre class="example">Makefile:1: *** target pattern contains no `%'.  Stop.
</pre></div>

<p>There have also always been a number of other details required for the
<em>lying</em> case to operate correctly, such as the use of so-called
<em>identity mounts</em>:
</p>
<div class="example">
<pre class="example"># <var>cygwin-root</var>/etc/fstab
D:/foo    /foo     some_fs binary 0 0
D:/bar    /bar     some_fs binary 0 0
E:/grill  /grill   some_fs binary 0 0
</pre></div>

<p>In this way, top-level directories of each drive are available using
identical names within Cygwin.
</p>
<p>Note that you also need to ensure that the standard Unix directories
(like <samp>/bin</samp>, <samp>/lib</samp>, <samp>/usr</samp>, <samp>/etc</samp>) appear in the root
of a drive.  This means that you must install Cygwin itself into the <samp>C:/</samp>
root directory (or <samp>D:/</samp>, or <samp>E:/</samp>, etc)—instead of the
recommended installation into <samp>C:/cygwin/</samp>.  In addition, all file names
used in the build system must be relative, symlinks should not be used within
the source or build directory trees, and all <samp>-M*</samp> options to
<code>gcc</code> except <samp>-MMD</samp> must be avoided.
</p>
<p>This is quite a fragile setup, but it has been in historical use, and so is
documented here.
</p>
<hr>
<span id="Windows-DLLs"></span><div class="header">
<p>
Previous: <a href="#File-name-conversion" accesskey="p" rel="prev">File name conversion</a>, Up: <a href="#Platform-quirks" accesskey="u" rel="up">Platform quirks</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Windows-DLLs-1"></span><h4 class="subsection">15.3.8 Windows DLLs</h4>
<span id="index-Windows-DLLs"></span>

<p>This topic describes a couple of ways to portably create Windows Dynamic
Link Libraries (DLLs).  Libtool knows how to create DLLs using GNU tools
and using Microsoft tools.
</p>
<p>A typical library has a “hidden” implementation with an interface
described in a header file.  On just about every system, the interface
could be something like this:
</p>
<p>Example <samp>foo.h</samp>:
</p>
<div class="example">
<pre class="example">#ifndef FOO_H
#define FOO_H

int one (void);
int two (void);
extern int three;

#endif /* FOO_H */
</pre></div>

<p>And the implementation could be something like this:
</p>
<p>Example <samp>foo.c</samp>:
</p>
<div class="example">
<pre class="example">#include "foo.h"

int one (void)
{
  return 1;
}

int two (void)
{
  return three - one ();
}

int three = 3;
</pre></div>

<p>When using contemporary GNU tools to create the Windows DLL, the above
code will work there too, thanks to its auto-import/auto-export
features.  But that is not the case when using older GNU tools or perhaps
more interestingly when using proprietary tools.  In those cases the code
will need additional decorations on the interface symbols with
<code>__declspec(dllimport)</code> and <code>__declspec(dllexport)</code> depending
on whether the library is built or it’s consumed and how it’s built and
consumed.  However, it should be noted that it would have worked also
with Microsoft tools, if only the variable <code>three</code> hadn’t been
there, due to the fact the Microsoft tools will automatically import
functions (but sadly not variables) and Libtool will automatically export
non-static symbols as described next.
</p>
<p>With Microsoft tools, Libtool digs through the object files that make up
the library, looking for non-static symbols to automatically export.
I.e., Libtool with Microsoft tools tries to mimic the auto-export feature
of contemporary GNU tools.  It should be noted that the GNU auto-export
feature is turned off when an explicit <code>__declspec(dllexport)</code> is
seen.  The GNU tools do this to not make more symbols visible for projects
that have already taken the trouble to decorate symbols.  There is no
similar way to limit what symbols are visible in the code when Libtool
is using Microsoft tools.  In order to limit symbol visibility in that
case you need to use one of the options <samp>-export-symbols</samp> or
<samp>-export-symbols-regex</samp>.
</p>
<p>No matching help with auto-import is provided by Libtool, which is why
variables must be decorated to import them from a DLL for everything but
contemporary GNU tools.  As stated above, functions are automatically
imported by both contemporary GNU tools and Microsoft tools, but for
other proprietary tools the auto-import status of functions is unknown.
</p>
<p>When the objects that form the library are built, there are generally
two copies built for each object.  One copy is used when linking the DLL
and one copy is used for the static library.  On Windows systems, a pair
of defines are commonly used to discriminate how the interface symbols
should be decorated.  The first define is ‘<samp>-DDLL_EXPORT</samp>’, which is
automatically provided by Libtool when <code>libtool</code> builds the copy
of the object that is destined for the DLL.  The second define is
‘<samp>-DLIBFOO_BUILD</samp>’ (or similar), which is often added by the package
providing the library and is used when building the library, but not
when consuming the library.
</p>
<p>However, the matching double compile is not performed when consuming
libraries.  It is therefore not possible to reliably distinguish if the
consumer is importing from a DLL or if it is going to use a static
library.
</p>
<p>With contemporary GNU tools, auto-import often saves the day, but see
the GNU ld documentation and its <samp>--enable-auto-import</samp> option
for some corner cases when it does not
(see <a href="https://sourceware.org/binutils/docs/ld/Options.html#Options">Options specific to
i386 PE targets</a> in <cite>Using ld, the GNU linker</cite>).
</p>
<p>With Microsoft tools you typically get away with always compiling the
code such that variables are expected to be imported from a DLL and
functions are expected to be found in a static library.  The tools will
then automatically import the function from a DLL if that is where they
are found.  If the variables are not imported from a DLL as expected, but
are found in a static library that is otherwise pulled in by some
function, the linker will issue a warning (LNK4217) that a locally
defined symbol is imported, but it still works.  In other words, this
scheme will not work to only consume variables from a library.  There is
also a price connected to this liberal use of imports in that an extra
indirection is introduced when you are consuming the static version of
the library.  That extra indirection is unavoidable when the DLL is
consumed, but it is not needed when consuming the static library.
</p>
<p>For older GNU tools and other proprietary tools there is no generic way
to make it possible to consume either of the DLL or the static library
without user intervention, the tools need to be told what is intended.
One common assumption is that if a DLL is being built (‘<samp>DLL_EXPORT</samp>’
is defined) then that DLL is going to consume any dependent libraries as
DLLs.  If that assumption is made everywhere, it is possible to select
how an end-user application is consuming libraries by adding a single
flag ‘<samp>-DDLL_EXPORT</samp>’ when a DLL build is required.  This is of course
an all or nothing deal, either everything as DLLs or everything as static
libraries.
</p>
<p>To sum up the above, the header file of the foo library needs to be
changed into something like this:
</p>
<p>Modified <samp>foo.h</samp>:
</p>
<div class="example">
<pre class="example">#ifndef FOO_H
#define FOO_H

#if defined _WIN32 &amp;&amp; !defined __GNUC__
# ifdef LIBFOO_BUILD
#  ifdef DLL_EXPORT
#   define LIBFOO_SCOPE            __declspec (dllexport)
#   define LIBFOO_SCOPE_VAR extern __declspec (dllexport)
#  endif
# elif defined _MSC_VER
#  define LIBFOO_SCOPE
#  define LIBFOO_SCOPE_VAR  extern __declspec (dllimport)
# elif defined DLL_EXPORT
#  define LIBFOO_SCOPE             __declspec (dllimport)
#  define LIBFOO_SCOPE_VAR  extern __declspec (dllimport)
# endif
#endif
#ifndef LIBFOO_SCOPE
# define LIBFOO_SCOPE
# define LIBFOO_SCOPE_VAR extern
#endif

LIBFOO_SCOPE     int one (void);
LIBFOO_SCOPE     int two (void);
LIBFOO_SCOPE_VAR int three;

#endif /* FOO_H */
</pre></div>

<p>When the targets are limited to contemporary GNU tools and Microsoft
tools, the above can be simplified to the following:
</p>
<p>Simplified <samp>foo.h</samp>:
</p>
<div class="example">
<pre class="example">#ifndef FOO_H
#define FOO_H

#if defined _WIN32 &amp;&amp; !defined __GNUC__ &amp;&amp; !defined LIBFOO_BUILD
# define LIBFOO_SCOPE_VAR extern __declspec (dllimport)
#else
# define LIBFOO_SCOPE_VAR extern
#endif

int one (void);
int two (void);
LIBFOO_SCOPE_VAR int three;

#endif /* FOO_H */
</pre></div>

<p>This last simplified version can of course only work when Libtool is
used to build the DLL, as no symbols would be exported otherwise (i.e.,
when using Microsoft tools).
</p>
<p>It should be noted that there are various projects that attempt to relax
these requirements by various low level tricks, but they are not
discussed here.
Examples are
<a href="http://alain.frisch.fr/flexdll.html">FlexDLL</a> and
<a href="http://edll.sourceforge.net/">edll</a>.
</p>

<hr>
<span id="libtool-script-contents"></span><div class="header">
<p>
Next: <a href="#Cheap-tricks" accesskey="n" rel="next">Cheap tricks</a>, Previous: <a href="#Platform-quirks" accesskey="p" rel="prev">Platform quirks</a>, Up: <a href="#Maintaining" accesskey="u" rel="up">Maintaining</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="libtool-script-contents-1"></span><h3 class="section">15.4 <code>libtool</code> script contents</h3>
<span id="index-implementation-of-libtool"></span>
<span id="index-libtool-implementation"></span>

<p>Since version 1.4, the <code>libtool</code> script is generated by
<code>configure</code> (see <a href="#Configuring">Configuring</a>).  In earlier versions,
<code>configure</code> achieved this by calling a helper script called
<samp>ltconfig</samp>.  From libtool version 0.7 to 1.0, this script
simply set shell variables, then sourced the libtool backend,
<code>ltmain.sh</code>.  <code>ltconfig</code> from libtool version 1.1 through 1.3
inlined the contents of <code>ltmain.sh</code> into the generated
<code>libtool</code>, which improved performance on many systems.  The tests
that <samp>ltconfig</samp> used to perform are now kept in <samp>libtool.m4</samp>
where they can be written using Autoconf.  This has the runtime
performance benefits of inlined <code>ltmain.sh</code>, <em>and</em> improves
the build time a little while considerably easing the amount of raw
shell code that used to need maintaining.
</p>
<p>The convention used for naming variables that hold shell commands for
delayed evaluation, is to use the suffix <code>_cmd</code> where a single
line of valid shell script is needed, and the suffix <code>_cmds</code> where
multiple lines of shell script <strong>may</strong> be delayed for later
evaluation.  By convention, <code>_cmds</code> variables delimit the
evaluation units with the <code>~</code> character where necessary.
</p>
<p>Here is a listing of each of the configuration variables, and how they
are used within <code>ltmain.sh</code> (see <a href="#Configuring">Configuring</a>):
</p>
<dl>
<dt id="index-AR">Variable: <strong>AR</strong></dt>
<dd><p>The name of the system library archiver.
</p></dd></dl>

<dl>
<dt id="index-CC-1">Variable: <strong>CC</strong></dt>
<dd><p>The name of the compiler used to configure libtool.  This will always
contain the compiler for the current language (see <a href="#Tags">Tags</a>).
</p></dd></dl>

<dl>
<dt id="index-ECHO">Variable: <strong>ECHO</strong></dt>
<dd><p>An <code>echo</code> program that does not interpret backslashes as an
escape character.  It may be given only one argument, so due quoting
is necessary.
</p></dd></dl>

<dl>
<dt id="index-LD-1">Variable: <strong>LD</strong></dt>
<dd><p>The name of the linker that libtool should use internally for reloadable
linking and possibly shared libraries.
</p></dd></dl>

<dl>
<dt id="index-LTCC">Variable: <strong>LTCC</strong></dt>
<dt id="index-LTCFLAGS">Variable: <strong>LTCFLAGS</strong></dt>
<dd><p>The name of the C compiler and C compiler flags used to configure
libtool.
</p></dd></dl>

<dl>
<dt id="index-NM-1">Variable: <strong>NM</strong></dt>
<dd><p>The name of a BSD- or MS-compatible program that produces listings of
global symbols.
For BSD <code>nm</code>, the symbols should be in one the following formats:
</p>
<div class="example">
<pre class="example"><var>address</var> C <var>global-variable-name</var>
<var>address</var> D <var>global-variable-name</var>
<var>address</var> T <var>global-function-name</var>
</pre></div>

<p>For MS <code>dumpbin</code>, the symbols should be in one of the following
formats:
</p>
<div class="example">
<pre class="example"><var>counter</var> <var>size</var>    UNDEF    notype       External     | <var>global-var</var>
<var>counter</var> <var>address</var> <var>section</var>  notype       External     | <var>global-var</var>
<var>counter</var> <var>address</var> <var>section</var>  notype ()    External     | <var>global-func</var>
</pre></div>

<p>The <var>size</var> of the global variables are not zero and the <var>section</var>
of the global functions are not "UNDEF". Symbols in "pick any" sections
("pick any" appears in the section header) are not global either.
</p></dd></dl>

<dl>
<dt id="index-RANLIB-1">Variable: <strong>RANLIB</strong></dt>
<dd><p>Set to the name of the <code>ranlib</code> program, if any.
</p></dd></dl>

<dl>
<dt id="index-allow_005fundefined_005fflag">Variable: <strong>allow_undefined_flag</strong></dt>
<dd><p>The flag that is used by ‘<samp>archive_cmds</samp>’ to declare that
there will be unresolved symbols in the resulting shared library.
Empty, if no such flag is required.  Set to ‘<samp>unsupported</samp>’ if there
is no way to generate a shared library with references to symbols that
aren’t defined in that library.
</p></dd></dl>

<dl>
<dt id="index-always_005fexport_005fsymbols">Variable: <strong>always_export_symbols</strong></dt>
<dd><p>Whether libtool should automatically generate a list of exported symbols
using <code>export_symbols_cmds</code> before linking an archive.
Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’.  Default is ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-archive_005fcmds">Variable: <strong>archive_cmds</strong></dt>
<dt id="index-archive_005fexpsym_005fcmds">Variable: <strong>archive_expsym_cmds</strong></dt>
<dt id="index-old_005farchive_005fcmds">Variable: <strong>old_archive_cmds</strong></dt>
<dd><p>Commands used to create shared libraries, shared libraries with
<samp>-export-symbols</samp> and static libraries, respectively.
</p></dd></dl>

<dl>
<dt id="index-archiver_005flist_005fspec">Variable: <strong>archiver_list_spec</strong></dt>
<dd><p>Specify filename containing input files for <code>AR</code>.
</p></dd></dl>

<dl>
<dt id="index-old_005farchive_005ffrom_005fnew_005fcmds">Variable: <strong>old_archive_from_new_cmds</strong></dt>
<dd><p>If the shared library depends on a static library,
‘<samp>old_archive_from_new_cmds</samp>’ contains the commands used to create that
static library.  If this variable is not empty, ‘<samp>old_archive_cmds</samp>’ is
not used.
</p></dd></dl>

<dl>
<dt id="index-old_005farchive_005ffrom_005fexpsyms_005fcmds">Variable: <strong>old_archive_from_expsyms_cmds</strong></dt>
<dd><p>If a static library must be created from the export symbol list to
correctly link with a shared library, ‘<samp>old_archive_from_expsyms_cmds</samp>’
contains the commands needed to create that static library.  When these
commands are executed, the variable <code>soname</code> contains the name of the
shared library in question, and the ‘<samp>$objdir/$newlib</samp>’ contains the
path of the static library these commands should build.  After executing
these commands, libtool will proceed to link against ‘<samp>$objdir/$newlib</samp>’
instead of <code>soname</code>.
</p></dd></dl>

<dl>
<dt id="index-lock_005fold_005farchive_005fextraction">Variable: <strong>lock_old_archive_extraction</strong></dt>
<dd><p>Set to ‘<samp>yes</samp>’ if the extraction of a static library requires locking
the library file.  This is required on Darwin.
</p></dd></dl>

<dl>
<dt id="index-build">Variable: <strong>build</strong></dt>
<dt id="index-build_005falias">Variable: <strong>build_alias</strong></dt>
<dt id="index-build_005fos">Variable: <strong>build_os</strong></dt>
<dd><p>Set to the specified and canonical names of the system that libtool was
built on.
</p></dd></dl>

<dl>
<dt id="index-build_005flibtool_005flibs">Variable: <strong>build_libtool_libs</strong></dt>
<dd><p>Whether libtool should build shared libraries on this system.  Set to
‘<samp>yes</samp>’ or ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-build_005fold_005flibs">Variable: <strong>build_old_libs</strong></dt>
<dd><p>Whether libtool should build static libraries on this system.  Set to
‘<samp>yes</samp>’ or ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-compiler_005fc_005fo">Variable: <strong>compiler_c_o</strong></dt>
<dd><p>Whether the compiler supports the <samp>-c</samp> and <samp>-o</samp> options
simultaneously.  Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-compiler_005fneeds_005fobject">Variable: <strong>compiler_needs_object</strong></dt>
<dd><p>Whether the compiler has to see an object listed on the command line in
order to successfully invoke the linker.  If ‘<samp>no</samp>’, then a set of
convenience archives or a set of object file names can be passed via
linker-specific options or linker scripts.
</p></dd></dl>

<dl>
<dt id="index-dlopen_005fsupport">Variable: <strong>dlopen_support</strong></dt>
<dd><p>Whether <code>dlopen</code> is supported on the platform.
Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-dlopen_005fself">Variable: <strong>dlopen_self</strong></dt>
<dd><p>Whether it is possible to <code>dlopen</code> the executable itself.
Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-dlopen_005fself_005fstatic">Variable: <strong>dlopen_self_static</strong></dt>
<dd><p>Whether it is possible to <code>dlopen</code> the executable itself, when it
is linked statically (<samp>-all-static</samp>).  Set to ‘<samp>yes</samp>’ or
‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-exclude_005fexpsyms">Variable: <strong>exclude_expsyms</strong></dt>
<dd><p>List of symbols that should not be listed in the preloaded symbols.
</p></dd></dl>

<dl>
<dt id="index-export_005fdynamic_005fflag_005fspec">Variable: <strong>export_dynamic_flag_spec</strong></dt>
<dd><p>Compiler link flag that allows a dlopened shared library to reference
symbols that are defined in the program.
</p></dd></dl>

<dl>
<dt id="index-export_005fsymbols_005fcmds">Variable: <strong>export_symbols_cmds</strong></dt>
<dd><p>Commands to extract exported symbols from <code>libobjs</code> to the
file <code>export_symbols</code>.
</p></dd></dl>

<dl>
<dt id="index-extract_005fexpsyms_005fcmds">Variable: <strong>extract_expsyms_cmds</strong></dt>
<dd><p>Commands to extract the exported symbols list from a shared library.
These commands are executed if there is no file ‘<samp>$objdir/$soname-def</samp>’,
and should write the names of the exported symbols to that file, for
the use of ‘<samp>old_archive_from_expsyms_cmds</samp>’.
</p></dd></dl>

<dl>
<dt id="index-fast_005finstall">Variable: <strong>fast_install</strong></dt>
<dd><p>Determines whether libtool will privilege the installer or the
developer.  The assumption is that installers will seldom run programs
in the build tree, and the developer will seldom install.  This is only
meaningful on platforms where <code>shlibpath_overrides_runpath</code> is
not ‘<samp>yes</samp>’, so <code>fast_install</code> will be set to ‘<samp>needless</samp>’ in
this case.  If <code>fast_install</code> set to ‘<samp>yes</samp>’, libtool will create
programs that search for installed libraries, and, if a program is run
in the build tree, a new copy will be linked on-demand to use the
yet-to-be-installed libraries.  If set to ‘<samp>no</samp>’, libtool will create
programs that use the yet-to-be-installed libraries, and will link
a new copy of the program at install time.  The default value is
‘<samp>yes</samp>’ or ‘<samp>needless</samp>’, depending on platform and configuration
flags, and it can be turned from ‘<samp>yes</samp>’ to ‘<samp>no</samp>’ with the
configure flag <samp>--disable-fast-install</samp>.
</p>
<p>On some systems, the linker always hardcodes paths to dependent libraries
into the output.  In this case, <code>fast_install</code> is never set to ‘<samp>yes</samp>’,
and relinking at install time is triggered.  This also means that <code>DESTDIR</code>
installation does not work as expected.
</p></dd></dl>

<dl>
<dt id="index-file_005fmagic_005fglob">Variable: <strong>file_magic_glob</strong></dt>
<dd><p>How to find potential files when <code>deplibs_check_method</code> is
‘<samp>file_magic</samp>’. <code>file_magic_glob</code> is a <code>sed</code> expression,
and the <code>sed</code> instance is fed potential file names that are
transformed by the <code>file_magic_glob</code> expression. Useful when the
shell does not support the shell option <code>nocaseglob</code>, making
<code>want_nocaseglob</code> inappropriate. Normally disabled (i.e.
<code>file_magic_glob</code> is empty).
</p></dd></dl>

<dl>
<dt id="index-finish_005fcmds">Variable: <strong>finish_cmds</strong></dt>
<dd><p>Commands to tell the dynamic linker how to find shared libraries in a
specific directory.
</p></dd></dl>

<dl>
<dt id="index-finish_005feval">Variable: <strong>finish_eval</strong></dt>
<dd><p>Same as <code>finish_cmds</code>, except the commands are not displayed.
</p></dd></dl>

<dl>
<dt id="index-global_005fsymbol_005fpipe">Variable: <strong>global_symbol_pipe</strong></dt>
<dd><p>A pipeline that takes the output of <code>NM</code>, and produces a listing of
raw symbols followed by their C names.  For example:
</p>
<div class="example">
<pre class="example">$ <kbd>eval "$NM progname | $global_symbol_pipe"</kbd>
D <var>symbol1</var> <var>C-symbol1</var>
T <var>symbol2</var> <var>C-symbol2</var>
C <var>symbol3</var> <var>C-symbol3</var>
…
$
</pre></div>

<p>The first column contains the symbol type (used to tell data from code)
but its meaning is system dependent.
</p></dd></dl>

<dl>
<dt id="index-global_005fsymbol_005fto_005fcdecl">Variable: <strong>global_symbol_to_cdecl</strong></dt>
<dd><p>A pipeline that translates the output of <code>global_symbol_pipe</code> into
proper C declarations.  Since some platforms, such as HP/UX, have
linkers that differentiate code from data, data symbols are declared
as data, and code symbols are declared as functions.
</p></dd></dl>

<dl>
<dt id="index-hardcode_005faction">Variable: <strong>hardcode_action</strong></dt>
<dd><p>Either ‘<samp>immediate</samp>’ or ‘<samp>relink</samp>’, depending on whether shared
library paths can be hardcoded into executables before they are installed,
or if they need to be relinked.
</p></dd></dl>

<dl>
<dt id="index-hardcode_005fdirect">Variable: <strong>hardcode_direct</strong></dt>
<dd><p>Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’, depending on whether the linker
hardcodes directories if a library is directly specified on the command
line (such as ‘<samp><var>dir</var>/lib<var>name</var>.a</samp>’) when
<code>hardcode_libdir_flag_spec</code> is specified.
</p></dd></dl>

<dl>
<dt id="index-hardcode_005fdirect_005fabsolute">Variable: <strong>hardcode_direct_absolute</strong></dt>
<dd><p>Some architectures hardcode "absolute" library directories that cannot
be overridden by <code>shlibpath_var</code> when <code>hardcode_direct</code> is
‘<samp>yes</samp>’.  In that case set <code>hardcode_direct_absolute</code> to
‘<samp>yes</samp>’, or otherwise ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-hardcode_005finto_005flibs">Variable: <strong>hardcode_into_libs</strong></dt>
<dd><p>Whether the platform supports hardcoding of run-paths into libraries.
If enabled, linking of programs will be much simpler but libraries will
need to be relinked during installation.  Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-hardcode_005flibdir_005fflag_005fspec">Variable: <strong>hardcode_libdir_flag_spec</strong></dt>
<dd><p>Flag to hardcode a <code>libdir</code> variable into a binary, so that the
dynamic linker searches <code>libdir</code> for shared libraries at runtime.
If it is empty, libtool will try to use some other hardcoding mechanism.
</p></dd></dl>

<dl>
<dt id="index-hardcode_005flibdir_005fseparator">Variable: <strong>hardcode_libdir_separator</strong></dt>
<dd><p>If the compiler only accepts a single <code>hardcode_libdir_flag</code>, then
this variable contains the string that should separate multiple
arguments to that flag.
</p></dd></dl>

<dl>
<dt id="index-hardcode_005fminus_005fL">Variable: <strong>hardcode_minus_L</strong></dt>
<dd><p>Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’, depending on whether the linker
hardcodes directories specified by <samp>-L</samp> flags into the resulting
executable when <code>hardcode_libdir_flag_spec</code> is specified.
</p></dd></dl>

<dl>
<dt id="index-hardcode_005fshlibpath_005fvar">Variable: <strong>hardcode_shlibpath_var</strong></dt>
<dd><p>Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’, depending on whether the linker
hardcodes directories by writing the contents of ‘<samp>$shlibpath_var</samp>’
into the resulting executable when <code>hardcode_libdir_flag_spec</code> is
specified.  Set to ‘<samp>unsupported</samp>’ if directories specified by
‘<samp>$shlibpath_var</samp>’ are searched at run time, but not at link time.
</p></dd></dl>

<dl>
<dt id="index-host">Variable: <strong>host</strong></dt>
<dt id="index-host_005falias">Variable: <strong>host_alias</strong></dt>
<dt id="index-host_005fos">Variable: <strong>host_os</strong></dt>
<dd><p>Set to the specified and canonical names of the system that libtool was
configured for.
</p></dd></dl>

<dl>
<dt id="index-include_005fexpsyms">Variable: <strong>include_expsyms</strong></dt>
<dd><p>List of symbols that must always be exported when using <code>export_symbols</code>.
</p></dd></dl>

<dl>
<dt id="index-inherit_005frpath">Variable: <strong>inherit_rpath</strong></dt>
<dd><p>Whether the linker adds runtime paths of dependency libraries to the
runtime path list, requiring libtool to relink the output when installing.
Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’.  Default is ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-install_005foverride_005fmode">Variable: <strong>install_override_mode</strong></dt>
<dd><p>Permission mode override for installation of shared libraries.  If the
runtime linker fails to load libraries with wrong permissions, then it
may fail to execute programs that are needed during installation,
because these need the library that has just been installed.  In this
case, it is necessary to pass the mode to <code>install</code> with
<samp>-m <var>install_override_mode</var></samp>.
</p></dd></dl>

<dl>
<dt id="index-libext">Variable: <strong>libext</strong></dt>
<dd><p>The standard old archive suffix (normally ‘<samp>a</samp>’).
</p></dd></dl>

<dl>
<dt id="index-libname_005fspec">Variable: <strong>libname_spec</strong></dt>
<dd><p>The format of a library name prefix.  On all Unix systems, static
libraries are called ‘<samp>lib<var>name</var>.a</samp>’, but on some systems (such
as OS/2 or MS-DOS), the library is just called ‘<samp><var>name</var>.a</samp>’.
</p></dd></dl>

<dl>
<dt id="index-library_005fnames_005fspec">Variable: <strong>library_names_spec</strong></dt>
<dd><p>A list of shared library names.  The first is the name of the file,
the rest are symbolic links to the file.  The name in the list is
the file name that the linker finds when given <samp>-l<var>name</var></samp>.
</p></dd></dl>

<dl>
<dt id="index-link_005fall_005fdeplibs">Variable: <strong>link_all_deplibs</strong></dt>
<dd><p>Whether libtool must link a program against all its dependency libraries.
Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’.  Default is ‘<samp>unknown</samp>’, which is
a synonym for ‘<samp>yes</samp>’.
</p></dd></dl>

<dl>
<dt id="index-link_005fstatic_005fflag">Variable: <strong>link_static_flag</strong></dt>
<dd><p>Linker flag (passed through the C compiler) used to prevent dynamic
linking.
</p></dd></dl>

<dl>
<dt id="index-macro_005fversion">Variable: <strong>macro_version</strong></dt>
<dt id="index-macro_005frevision">Variable: <strong>macro_revision</strong></dt>
<dd><p>The release and revision from which the libtool.m4 macros were
taken.  This is used to ensure that macros and <code>ltmain.sh</code>
correspond to the same Libtool version.
</p></dd></dl>

<dl>
<dt id="index-max_005fcmd_005flen">Variable: <strong>max_cmd_len</strong></dt>
<dd><p>The approximate longest command line that can be passed to ‘<samp>$SHELL</samp>’
without being truncated, as computed by ‘<samp>LT_CMD_MAX_LEN</samp>’.
</p></dd></dl>

<dl>
<dt id="index-need_005flib_005fprefix">Variable: <strong>need_lib_prefix</strong></dt>
<dd><p>Whether we can <code>dlopen</code> modules without a ‘<samp>lib</samp>’ prefix.
Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’.  By default, it is ‘<samp>unknown</samp>’, which
means the same as ‘<samp>yes</samp>’, but documents that we are not really sure
about it.  ‘<samp>no</samp>’ means that it is possible to <code>dlopen</code> a
module without the ‘<samp>lib</samp>’ prefix.
</p></dd></dl>

<dl>
<dt id="index-need_005fversion">Variable: <strong>need_version</strong></dt>
<dd><p>Whether versioning is required for libraries, i.e. whether the
dynamic linker requires a version suffix for all libraries.
Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’.  By default, it is ‘<samp>unknown</samp>’, which
means the same as ‘<samp>yes</samp>’, but documents that we are not really sure
about it.
</p></dd></dl>

<dl>
<dt id="index-need_005flocks">Variable: <strong>need_locks</strong></dt>
<dd><p>Whether files must be locked to prevent conflicts when compiling
simultaneously.  Set to ‘<samp>yes</samp>’ or ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-nm_005ffile_005flist_005fspec">Variable: <strong>nm_file_list_spec</strong></dt>
<dd><p>Specify filename containing input files for <code>NM</code>.
</p></dd></dl>

<dl>
<dt id="index-no_005fbuiltin_005fflag">Variable: <strong>no_builtin_flag</strong></dt>
<dd><p>Compiler flag to disable builtin functions that conflict with declaring
external global symbols as <code>char</code>.
</p></dd></dl>

<dl>
<dt id="index-no_005fundefined_005fflag">Variable: <strong>no_undefined_flag</strong></dt>
<dd><p>The flag that is used by ‘<samp>archive_cmds</samp>’ to declare that
there will be no unresolved symbols in the resulting shared library.
Empty, if no such flag is required.
</p></dd></dl>

<dl>
<dt id="index-objdir">Variable: <strong>objdir</strong></dt>
<dd><p>The name of the directory that contains temporary libtool files.
</p></dd></dl>

<dl>
<dt id="index-objext">Variable: <strong>objext</strong></dt>
<dd><p>The standard object file suffix (normally ‘<samp>o</samp>’).
</p></dd></dl>

<dl>
<dt id="index-pic_005fflag">Variable: <strong>pic_flag</strong></dt>
<dd><p>Any additional compiler flags for building library object files.
</p></dd></dl>

<dl>
<dt id="index-postinstall_005fcmds">Variable: <strong>postinstall_cmds</strong></dt>
<dt id="index-old_005fpostinstall_005fcmds">Variable: <strong>old_postinstall_cmds</strong></dt>
<dd><p>Commands run after installing a shared or static library, respectively.
</p></dd></dl>

<dl>
<dt id="index-postuninstall_005fcmds">Variable: <strong>postuninstall_cmds</strong></dt>
<dt id="index-old_005fpostuninstall_005fcmds">Variable: <strong>old_postuninstall_cmds</strong></dt>
<dd><p>Commands run after uninstalling a shared or static library, respectively.
</p></dd></dl>

<dl>
<dt id="index-postlink_005fcmds">Variable: <strong>postlink_cmds</strong></dt>
<dd><p>Commands necessary for finishing linking programs. <code>postlink_cmds</code>
are executed immediately after the program is linked.  Any occurrence of
the string <code>@OUTPUT@</code> in <code>postlink_cmds</code> is replaced by the
name of the created executable (i.e. not the wrapper, if a wrapper is
generated) prior to execution.  Similarly, <code>@TOOL_OUTPUT@</code> is
replaced by the toolchain format of <code>@OUTPUT@</code>.  Normally disabled
(i.e. <code>postlink_cmds</code> empty).
</p></dd></dl>

<dl>
<dt id="index-reload_005fcmds">Variable: <strong>reload_cmds</strong></dt>
<dt id="index-reload_005fflag">Variable: <strong>reload_flag</strong></dt>
<dd><p>Commands to create a reloadable object.  Set <code>reload_cmds</code> to
‘<samp>false</samp>’ on systems that cannot create reloadable objects.
</p></dd></dl>

<dl>
<dt id="index-runpath_005fvar">Variable: <strong>runpath_var</strong></dt>
<dd><p>The environment variable that tells the linker what directories to
hardcode in the resulting executable.
</p></dd></dl>

<dl>
<dt id="index-shlibpath_005foverrides_005frunpath">Variable: <strong>shlibpath_overrides_runpath</strong></dt>
<dd><p>Indicates whether it is possible to override the hard-coded library
search path of a program with an environment variable.  If this is set
to no, libtool may have to create two copies of a program in the build
tree, one to be installed and one to be run in the build tree only.
When each of these copies is created depends on the value of
<code>fast_install</code>.  The default value is ‘<samp>unknown</samp>’, which is
equivalent to ‘<samp>no</samp>’.
</p></dd></dl>

<dl>
<dt id="index-shlibpath_005fvar">Variable: <strong>shlibpath_var</strong></dt>
<dd><p>The environment variable that tells the dynamic linker where to find
shared libraries.
</p></dd></dl>

<dl>
<dt id="index-soname_005fspec">Variable: <strong>soname_spec</strong></dt>
<dd><p>The name coded into shared libraries, if different from the real name of
the file.
</p></dd></dl>

<dl>
<dt id="index-striplib">Variable: <strong>striplib</strong></dt>
<dt id="index-old_005fstriplib">Variable: <strong>old_striplib</strong></dt>
<dd><p>Command to strip a shared (<code>striplib</code>) or static (<code>old_striplib</code>)
library, respectively.  If these variables are empty, the strip flag
in the install mode will be ignored for libraries (see <a href="#Install-mode">Install mode</a>).
</p></dd></dl>

<dl>
<dt id="index-sys_005flib_005fdlsearch_005fpath_005fspec">Variable: <strong>sys_lib_dlsearch_path_spec</strong></dt>
<dd><p>Expression to get the run-time system library search path.  Directories
that appear in this list are never hard-coded into executables.
</p></dd></dl>

<dl>
<dt id="index-sys_005flib_005fsearch_005fpath_005fspec">Variable: <strong>sys_lib_search_path_spec</strong></dt>
<dd><p>Expression to get the compile-time system library search path.  This
variable is used by libtool when it has to test whether a certain
library is shared or static.  The directories listed in
<code>shlibpath_var</code> are automatically appended to this list, every time
libtool runs (i.e., not at configuration time), because some linkers use
this variable to extend the library search path.  Linker switches such
as <samp>-L</samp> also augment the search path.
</p></dd></dl>

<dl>
<dt id="index-thread_005fsafe_005fflag_005fspec">Variable: <strong>thread_safe_flag_spec</strong></dt>
<dd><p>Linker flag (passed through the C compiler) used to generate thread-safe
libraries.
</p></dd></dl>

<dl>
<dt id="index-to_005fhost_005ffile_005fcmd">Variable: <strong>to_host_file_cmd</strong></dt>
<dd><p>If the toolchain is not native to the build platform (e.g. if you are using
MSYS to drive the scripting, but are using the MinGW native Windows compiler)
this variable describes how to convert file names from the format used by the
build platform to the format used by host platform.  Normally set to
‘<samp>func_convert_file_noop</samp>’, libtool will autodetect most cases where
other values should be used.  On rare occasions, it may be necessary to override
the autodetected value (see <a href="#Cygwin-to-MinGW-Cross">Cygwin to MinGW Cross</a>).
</p></dd></dl>

<dl>
<dt id="index-to_005ftool_005ffile_005fcmd">Variable: <strong>to_tool_file_cmd</strong></dt>
<dd><p>If the toolchain is not native to the build platform (e.g. if you are using
some Unix to drive the scripting together with a Windows toolchain running
in Wine) this variable describes how to convert file names from the format
used by the build platform to the format used by the toolchain.  Normally set
to ‘<samp>func_convert_file_noop</samp>’.
</p></dd></dl>

<dl>
<dt id="index-version_005ftype">Variable: <strong>version_type</strong></dt>
<dd><p>The library version numbering type.  One of ‘<samp>libtool</samp>’,
‘<samp>freebsd-aout</samp>’, ‘<samp>freebsd-elf</samp>’, ‘<samp>irix</samp>’, ‘<samp>linux</samp>’,
‘<samp>osf</samp>’, ‘<samp>sunos</samp>’, ‘<samp>windows</samp>’, or ‘<samp>none</samp>’.
</p></dd></dl>

<dl>
<dt id="index-want_005fnocaseglob">Variable: <strong>want_nocaseglob</strong></dt>
<dd><p>Find potential files using the shell option <code>nocaseglob</code>, when
<code>deplibs_check_method</code> is ‘<samp>file_magic</samp>’. Normally set to
‘<samp>no</samp>’. Set to ‘<samp>yes</samp>’ to enable the <code>nocaseglob</code> shell
option when looking for potential file names in a case-insensitive
manner.
</p></dd></dl>

<dl>
<dt id="index-whole_005farchive_005fflag_005fspec">Variable: <strong>whole_archive_flag_spec</strong></dt>
<dd><p>Compiler flag to generate shared objects from convenience archives.
</p></dd></dl>

<dl>
<dt id="index-wl">Variable: <strong>wl</strong></dt>
<dd><p>The C compiler flag that allows libtool to pass a flag directly to the
linker.  Used as: <code>${wl}<var>some-flag</var></code>.
</p></dd></dl>

<p>Variables ending in ‘<samp>_cmds</samp>’ or ‘<samp>_eval</samp>’ contain a
‘<samp>~</samp>’-separated list of commands that are <code>eval</code>ed one after
another.  If any of the commands return a nonzero exit status, libtool
generally exits with an error message.
</p>
<p>Variables ending in ‘<samp>_spec</samp>’ are <code>eval</code>ed before being used by
libtool.
</p>
<hr>
<span id="Cheap-tricks"></span><div class="header">
<p>
Previous: <a href="#libtool-script-contents" accesskey="p" rel="prev">libtool script contents</a>, Up: <a href="#Maintaining" accesskey="u" rel="up">Maintaining</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Cheap-tricks-1"></span><h3 class="section">15.5 Cheap tricks</h3>

<p>Here are a few tricks that you can use to make maintainership
easier:
</p>
<ul>
<li> When people report bugs, ask them to use the <samp>--config</samp>,
<samp>--debug</samp>, or <samp>--features</samp> flags, if you think they will help
you.  These flags are there to help you get information directly, rather
than having to trust second-hand observation.

</li><li> Rather than reconfiguring libtool every time I make a change to
<code>ltmain.in</code>, I keep a permanent <code>libtool</code> script in my
<code>PATH</code>, which sources <code>ltmain.in</code> directly.

<p>The following steps describe how to create such a script, where
<code>/home/src/libtool</code> is the directory containing the libtool source
tree, <code>/home/src/libtool/libtool</code> is a libtool script that has been
configured for your platform, and <code>~/bin</code> is a directory in your
<code>PATH</code>:
</p>
<div class="example">
<pre class="example">trick$ cd ~/bin
trick$ sed 's%^\(macro_version=\).*$%\1@VERSION@%;
            s%^\(macro_revision=\).*$%\1@package_revision@%;
            /^# ltmain\.sh/q' /home/src/libtool/libtool &gt; libtool
trick$ echo '. /home/src/libtool/ltmain.in' &gt;&gt; libtool
trick$ chmod +x libtool
trick$ libtool --version
ltmain.sh (GNU @PACKAGE@@TIMESTAMP@) @VERSION@

Copyright (C) 2014 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
trick$
</pre></div>
</li></ul>

<p>The output of the final ‘<samp>libtool --version</samp>’ command shows that the
<code>ltmain.in</code> script is being used directly.  Now, modify
<code>~/bin/libtool</code> or <code>/home/src/libtool/ltmain.in</code> directly in
order to test new changes without having to rerun <code>configure</code>.
</p>
<hr>
<span id="GNU-Free-Documentation-License"></span><div class="header">
<p>
Next: <a href="#Combined-Index" accesskey="n" rel="next">Combined Index</a>, Previous: <a href="#Maintaining" accesskey="p" rel="prev">Maintaining</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="GNU-Free-Documentation-License-1"></span><h2 class="appendix">Appendix A GNU Free Documentation License</h2>

<span id="index-FDL_002c-GNU-Free-Documentation-License"></span>

<div align="center">Version 1.3, 3 November 2008
</div>

<div class="display">
<pre class="display">Copyright © 2000, 2001, 2002, 2007, 2008 Free Software Foundation, Inc.
<a href="https://fsf.org/">https://fsf.org/</a>

Everyone is permitted to copy and distribute verbatim copies
of this license document, but changing it is not allowed.
</pre></div>

<ol start="0">
<li> PREAMBLE

<p>The purpose of this License is to make a manual, textbook, or other
functional and useful document <em>free</em> in the sense of freedom: to
assure everyone the effective freedom to copy and redistribute it,
with or without modifying it, either commercially or noncommercially.
Secondarily, this License preserves for the author and publisher a way
to get credit for their work, while not being considered responsible
for modifications made by others.
</p>
<p>This License is a kind of “copyleft”, which means that derivative
works of the document must themselves be free in the same sense.  It
complements the GNU General Public License, which is a copyleft
license designed for free software.
</p>
<p>We have designed this License in order to use it for manuals for free
software, because free software needs free documentation: a free
program should come with manuals providing the same freedoms that the
software does.  But this License is not limited to software manuals;
it can be used for any textual work, regardless of subject matter or
whether it is published as a printed book.  We recommend this License
principally for works whose purpose is instruction or reference.
</p>
</li><li> APPLICABILITY AND DEFINITIONS

<p>This License applies to any manual or other work, in any medium, that
contains a notice placed by the copyright holder saying it can be
distributed under the terms of this License.  Such a notice grants a
world-wide, royalty-free license, unlimited in duration, to use that
work under the conditions stated herein.  The “Document”, below,
refers to any such manual or work.  Any member of the public is a
licensee, and is addressed as “you”.  You accept the license if you
copy, modify or distribute the work in a way requiring permission
under copyright law.
</p>
<p>A “Modified Version” of the Document means any work containing the
Document or a portion of it, either copied verbatim, or with
modifications and/or translated into another language.
</p>
<p>A “Secondary Section” is a named appendix or a front-matter section
of the Document that deals exclusively with the relationship of the
publishers or authors of the Document to the Document’s overall
subject (or to related matters) and contains nothing that could fall
directly within that overall subject.  (Thus, if the Document is in
part a textbook of mathematics, a Secondary Section may not explain
any mathematics.)  The relationship could be a matter of historical
connection with the subject or with related matters, or of legal,
commercial, philosophical, ethical or political position regarding
them.
</p>
<p>The “Invariant Sections” are certain Secondary Sections whose titles
are designated, as being those of Invariant Sections, in the notice
that says that the Document is released under this License.  If a
section does not fit the above definition of Secondary then it is not
allowed to be designated as Invariant.  The Document may contain zero
Invariant Sections.  If the Document does not identify any Invariant
Sections then there are none.
</p>
<p>The “Cover Texts” are certain short passages of text that are listed,
as Front-Cover Texts or Back-Cover Texts, in the notice that says that
the Document is released under this License.  A Front-Cover Text may
be at most 5 words, and a Back-Cover Text may be at most 25 words.
</p>
<p>A “Transparent” copy of the Document means a machine-readable copy,
represented in a format whose specification is available to the
general public, that is suitable for revising the document
straightforwardly with generic text editors or (for images composed of
pixels) generic paint programs or (for drawings) some widely available
drawing editor, and that is suitable for input to text formatters or
for automatic translation to a variety of formats suitable for input
to text formatters.  A copy made in an otherwise Transparent file
format whose markup, or absence of markup, has been arranged to thwart
or discourage subsequent modification by readers is not Transparent.
An image format is not Transparent if used for any substantial amount
of text.  A copy that is not “Transparent” is called “Opaque”.
</p>
<p>Examples of suitable formats for Transparent copies include plain
ASCII without markup, Texinfo input format, LaTeX input
format, SGML or XML using a publicly available
DTD, and standard-conforming simple HTML,
PostScript or PDF designed for human modification.  Examples
of transparent image formats include PNG, XCF and
JPG.  Opaque formats include proprietary formats that can be
read and edited only by proprietary word processors, SGML or
XML for which the DTD and/or processing tools are
not generally available, and the machine-generated HTML,
PostScript or PDF produced by some word processors for
output purposes only.
</p>
<p>The “Title Page” means, for a printed book, the title page itself,
plus such following pages as are needed to hold, legibly, the material
this License requires to appear in the title page.  For works in
formats which do not have any title page as such, “Title Page” means
the text near the most prominent appearance of the work’s title,
preceding the beginning of the body of the text.
</p>
<p>The “publisher” means any person or entity that distributes copies
of the Document to the public.
</p>
<p>A section “Entitled XYZ” means a named subunit of the Document whose
title either is precisely XYZ or contains XYZ in parentheses following
text that translates XYZ in another language.  (Here XYZ stands for a
specific section name mentioned below, such as “Acknowledgements”,
“Dedications”, “Endorsements”, or “History”.)  To “Preserve the Title”
of such a section when you modify the Document means that it remains a
section “Entitled XYZ” according to this definition.
</p>
<p>The Document may include Warranty Disclaimers next to the notice which
states that this License applies to the Document.  These Warranty
Disclaimers are considered to be included by reference in this
License, but only as regards disclaiming warranties: any other
implication that these Warranty Disclaimers may have is void and has
no effect on the meaning of this License.
</p>
</li><li> VERBATIM COPYING

<p>You may copy and distribute the Document in any medium, either
commercially or noncommercially, provided that this License, the
copyright notices, and the license notice saying this License applies
to the Document are reproduced in all copies, and that you add no other
conditions whatsoever to those of this License.  You may not use
technical measures to obstruct or control the reading or further
copying of the copies you make or distribute.  However, you may accept
compensation in exchange for copies.  If you distribute a large enough
number of copies you must also follow the conditions in section 3.
</p>
<p>You may also lend copies, under the same conditions stated above, and
you may publicly display copies.
</p>
</li><li> COPYING IN QUANTITY

<p>If you publish printed copies (or copies in media that commonly have
printed covers) of the Document, numbering more than 100, and the
Document’s license notice requires Cover Texts, you must enclose the
copies in covers that carry, clearly and legibly, all these Cover
Texts: Front-Cover Texts on the front cover, and Back-Cover Texts on
the back cover.  Both covers must also clearly and legibly identify
you as the publisher of these copies.  The front cover must present
the full title with all words of the title equally prominent and
visible.  You may add other material on the covers in addition.
Copying with changes limited to the covers, as long as they preserve
the title of the Document and satisfy these conditions, can be treated
as verbatim copying in other respects.
</p>
<p>If the required texts for either cover are too voluminous to fit
legibly, you should put the first ones listed (as many as fit
reasonably) on the actual cover, and continue the rest onto adjacent
pages.
</p>
<p>If you publish or distribute Opaque copies of the Document numbering
more than 100, you must either include a machine-readable Transparent
copy along with each Opaque copy, or state in or with each Opaque copy
a computer-network location from which the general network-using
public has access to download using public-standard network protocols
a complete Transparent copy of the Document, free of added material.
If you use the latter option, you must take reasonably prudent steps,
when you begin distribution of Opaque copies in quantity, to ensure
that this Transparent copy will remain thus accessible at the stated
location until at least one year after the last time you distribute an
Opaque copy (directly or through your agents or retailers) of that
edition to the public.
</p>
<p>It is requested, but not required, that you contact the authors of the
Document well before redistributing any large number of copies, to give
them a chance to provide you with an updated version of the Document.
</p>
</li><li> MODIFICATIONS

<p>You may copy and distribute a Modified Version of the Document under
the conditions of sections 2 and 3 above, provided that you release
the Modified Version under precisely this License, with the Modified
Version filling the role of the Document, thus licensing distribution
and modification of the Modified Version to whoever possesses a copy
of it.  In addition, you must do these things in the Modified Version:
</p>
<ol type="A" start="1">
<li> Use in the Title Page (and on the covers, if any) a title distinct
from that of the Document, and from those of previous versions
(which should, if there were any, be listed in the History section
of the Document).  You may use the same title as a previous version
if the original publisher of that version gives permission.

</li><li> List on the Title Page, as authors, one or more persons or entities
responsible for authorship of the modifications in the Modified
Version, together with at least five of the principal authors of the
Document (all of its principal authors, if it has fewer than five),
unless they release you from this requirement.

</li><li> State on the Title page the name of the publisher of the
Modified Version, as the publisher.

</li><li> Preserve all the copyright notices of the Document.

</li><li> Add an appropriate copyright notice for your modifications
adjacent to the other copyright notices.

</li><li> Include, immediately after the copyright notices, a license notice
giving the public permission to use the Modified Version under the
terms of this License, in the form shown in the Addendum below.

</li><li> Preserve in that license notice the full lists of Invariant Sections
and required Cover Texts given in the Document’s license notice.

</li><li> Include an unaltered copy of this License.

</li><li> Preserve the section Entitled “History”, Preserve its Title, and add
to it an item stating at least the title, year, new authors, and
publisher of the Modified Version as given on the Title Page.  If
there is no section Entitled “History” in the Document, create one
stating the title, year, authors, and publisher of the Document as
given on its Title Page, then add an item describing the Modified
Version as stated in the previous sentence.

</li><li> Preserve the network location, if any, given in the Document for
public access to a Transparent copy of the Document, and likewise
the network locations given in the Document for previous versions
it was based on.  These may be placed in the “History” section.
You may omit a network location for a work that was published at
least four years before the Document itself, or if the original
publisher of the version it refers to gives permission.

</li><li> For any section Entitled “Acknowledgements” or “Dedications”, Preserve
the Title of the section, and preserve in the section all the
substance and tone of each of the contributor acknowledgements and/or
dedications given therein.

</li><li> Preserve all the Invariant Sections of the Document,
unaltered in their text and in their titles.  Section numbers
or the equivalent are not considered part of the section titles.

</li><li> Delete any section Entitled “Endorsements”.  Such a section
may not be included in the Modified Version.

</li><li> Do not retitle any existing section to be Entitled “Endorsements” or
to conflict in title with any Invariant Section.

</li><li> Preserve any Warranty Disclaimers.
</li></ol>

<p>If the Modified Version includes new front-matter sections or
appendices that qualify as Secondary Sections and contain no material
copied from the Document, you may at your option designate some or all
of these sections as invariant.  To do this, add their titles to the
list of Invariant Sections in the Modified Version’s license notice.
These titles must be distinct from any other section titles.
</p>
<p>You may add a section Entitled “Endorsements”, provided it contains
nothing but endorsements of your Modified Version by various
parties—for example, statements of peer review or that the text has
been approved by an organization as the authoritative definition of a
standard.
</p>
<p>You may add a passage of up to five words as a Front-Cover Text, and a
passage of up to 25 words as a Back-Cover Text, to the end of the list
of Cover Texts in the Modified Version.  Only one passage of
Front-Cover Text and one of Back-Cover Text may be added by (or
through arrangements made by) any one entity.  If the Document already
includes a cover text for the same cover, previously added by you or
by arrangement made by the same entity you are acting on behalf of,
you may not add another; but you may replace the old one, on explicit
permission from the previous publisher that added the old one.
</p>
<p>The author(s) and publisher(s) of the Document do not by this License
give permission to use their names for publicity for or to assert or
imply endorsement of any Modified Version.
</p>
</li><li> COMBINING DOCUMENTS

<p>You may combine the Document with other documents released under this
License, under the terms defined in section 4 above for modified
versions, provided that you include in the combination all of the
Invariant Sections of all of the original documents, unmodified, and
list them all as Invariant Sections of your combined work in its
license notice, and that you preserve all their Warranty Disclaimers.
</p>
<p>The combined work need only contain one copy of this License, and
multiple identical Invariant Sections may be replaced with a single
copy.  If there are multiple Invariant Sections with the same name but
different contents, make the title of each such section unique by
adding at the end of it, in parentheses, the name of the original
author or publisher of that section if known, or else a unique number.
Make the same adjustment to the section titles in the list of
Invariant Sections in the license notice of the combined work.
</p>
<p>In the combination, you must combine any sections Entitled “History”
in the various original documents, forming one section Entitled
“History”; likewise combine any sections Entitled “Acknowledgements”,
and any sections Entitled “Dedications”.  You must delete all
sections Entitled “Endorsements.”
</p>
</li><li> COLLECTIONS OF DOCUMENTS

<p>You may make a collection consisting of the Document and other documents
released under this License, and replace the individual copies of this
License in the various documents with a single copy that is included in
the collection, provided that you follow the rules of this License for
verbatim copying of each of the documents in all other respects.
</p>
<p>You may extract a single document from such a collection, and distribute
it individually under this License, provided you insert a copy of this
License into the extracted document, and follow this License in all
other respects regarding verbatim copying of that document.
</p>
</li><li> AGGREGATION WITH INDEPENDENT WORKS

<p>A compilation of the Document or its derivatives with other separate
and independent documents or works, in or on a volume of a storage or
distribution medium, is called an “aggregate” if the copyright
resulting from the compilation is not used to limit the legal rights
of the compilation’s users beyond what the individual works permit.
When the Document is included in an aggregate, this License does not
apply to the other works in the aggregate which are not themselves
derivative works of the Document.
</p>
<p>If the Cover Text requirement of section 3 is applicable to these
copies of the Document, then if the Document is less than one half of
the entire aggregate, the Document’s Cover Texts may be placed on
covers that bracket the Document within the aggregate, or the
electronic equivalent of covers if the Document is in electronic form.
Otherwise they must appear on printed covers that bracket the whole
aggregate.
</p>
</li><li> TRANSLATION

<p>Translation is considered a kind of modification, so you may
distribute translations of the Document under the terms of section 4.
Replacing Invariant Sections with translations requires special
permission from their copyright holders, but you may include
translations of some or all Invariant Sections in addition to the
original versions of these Invariant Sections.  You may include a
translation of this License, and all the license notices in the
Document, and any Warranty Disclaimers, provided that you also include
the original English version of this License and the original versions
of those notices and disclaimers.  In case of a disagreement between
the translation and the original version of this License or a notice
or disclaimer, the original version will prevail.
</p>
<p>If a section in the Document is Entitled “Acknowledgements”,
“Dedications”, or “History”, the requirement (section 4) to Preserve
its Title (section 1) will typically require changing the actual
title.
</p>
</li><li> TERMINATION

<p>You may not copy, modify, sublicense, or distribute the Document
except as expressly provided under this License.  Any attempt
otherwise to copy, modify, sublicense, or distribute it is void, and
will automatically terminate your rights under this License.
</p>
<p>However, if you cease all violation of this License, then your license
from a particular copyright holder is reinstated (a) provisionally,
unless and until the copyright holder explicitly and finally
terminates your license, and (b) permanently, if the copyright holder
fails to notify you of the violation by some reasonable means prior to
60 days after the cessation.
</p>
<p>Moreover, your license from a particular copyright holder is
reinstated permanently if the copyright holder notifies you of the
violation by some reasonable means, this is the first time you have
received notice of violation of this License (for any work) from that
copyright holder, and you cure the violation prior to 30 days after
your receipt of the notice.
</p>
<p>Termination of your rights under this section does not terminate the
licenses of parties who have received copies or rights from you under
this License.  If your rights have been terminated and not permanently
reinstated, receipt of a copy of some or all of the same material does
not give you any rights to use it.
</p>
</li><li> FUTURE REVISIONS OF THIS LICENSE

<p>The Free Software Foundation may publish new, revised versions
of the GNU Free Documentation License from time to time.  Such new
versions will be similar in spirit to the present version, but may
differ in detail to address new problems or concerns.  See
<a href="https://www.gnu.org/licenses/">https://www.gnu.org/licenses/</a>.
</p>
<p>Each version of the License is given a distinguishing version number.
If the Document specifies that a particular numbered version of this
License “or any later version” applies to it, you have the option of
following the terms and conditions either of that specified version or
of any later version that has been published (not as a draft) by the
Free Software Foundation.  If the Document does not specify a version
number of this License, you may choose any version ever published (not
as a draft) by the Free Software Foundation.  If the Document
specifies that a proxy can decide which future versions of this
License can be used, that proxy’s public statement of acceptance of a
version permanently authorizes you to choose that version for the
Document.
</p>
</li><li> RELICENSING

<p>“Massive Multiauthor Collaboration Site” (or “MMC Site”) means any
World Wide Web server that publishes copyrightable works and also
provides prominent facilities for anybody to edit those works.  A
public wiki that anybody can edit is an example of such a server.  A
“Massive Multiauthor Collaboration” (or “MMC”) contained in the
site means any set of copyrightable works thus published on the MMC
site.
</p>
<p>“CC-BY-SA” means the Creative Commons Attribution-Share Alike 3.0
license published by Creative Commons Corporation, a not-for-profit
corporation with a principal place of business in San Francisco,
California, as well as future copyleft versions of that license
published by that same organization.
</p>
<p>“Incorporate” means to publish or republish a Document, in whole or
in part, as part of another Document.
</p>
<p>An MMC is “eligible for relicensing” if it is licensed under this
License, and if all works that were first published under this License
somewhere other than this MMC, and subsequently incorporated in whole
or in part into the MMC, (1) had no cover texts or invariant sections,
and (2) were thus incorporated prior to November 1, 2008.
</p>
<p>The operator of an MMC Site may republish an MMC contained in the site
under CC-BY-SA on the same site at any time before August 1, 2009,
provided the MMC is eligible for relicensing.
</p>
</li></ol>

<span id="ADDENDUM_003a-How-to-use-this-License-for-your-documents"></span><h3 class="heading">ADDENDUM: How to use this License for your documents</h3>

<p>To use this License in a document you have written, include a copy of
the License in the document and put the following copyright and
license notices just after the title page:
</p>
<div class="example">
<pre class="example">  Copyright (C)  <var>year</var>  <var>your name</var>.
  Permission is granted to copy, distribute and/or modify this document
  under the terms of the GNU Free Documentation License, Version 1.3
  or any later version published by the Free Software Foundation;
  with no Invariant Sections, no Front-Cover Texts, and no Back-Cover
  Texts.  A copy of the license is included in the section entitled ``GNU
  Free Documentation License''.
</pre></div>

<p>If you have Invariant Sections, Front-Cover Texts and Back-Cover Texts,
replace the “with…Texts.” line with this:
</p>
<div class="example">
<pre class="example">    with the Invariant Sections being <var>list their titles</var>, with
    the Front-Cover Texts being <var>list</var>, and with the Back-Cover Texts
    being <var>list</var>.
</pre></div>

<p>If you have Invariant Sections without Cover Texts, or some other
combination of the three, merge those two alternatives to suit the
situation.
</p>
<p>If your document contains nontrivial examples of program code, we
recommend releasing these examples in parallel under your choice of
free software license, such as the GNU General Public License,
to permit their use in free software.
</p>

<hr>
<span id="Combined-Index"></span><div class="header">
<p>
Previous: <a href="#GNU-Free-Documentation-License" accesskey="p" rel="prev">GNU Free Documentation License</a>, Up: <a href="#Top" accesskey="u" rel="up">Top</a> &nbsp; [<a href="#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="#Combined-Index" title="Index" rel="index">Index</a>]</p>
</div>
<span id="Combined-Index-1"></span><h2 class="unnumbered">Combined Index</h2>

<table><tbody><tr><th valign="top">Jump to: &nbsp; </th><td><a class="summary-letter" href="#Combined-Index_cp_symbol-1"><b>-</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_symbol-2"><b>.</b></a>
 &nbsp; 
<br>
<a class="summary-letter" href="#Combined-Index_cp_letter-A"><b>A</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-B"><b>B</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-C"><b>C</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-D"><b>D</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-E"><b>E</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-F"><b>F</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-G"><b>G</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-H"><b>H</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-I"><b>I</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-L"><b>L</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-M"><b>M</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-N"><b>N</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-O"><b>O</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-P"><b>P</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-Q"><b>Q</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-R"><b>R</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-S"><b>S</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-T"><b>T</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-U"><b>U</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-V"><b>V</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-W"><b>W</b></a>
 &nbsp; 
</td></tr></tbody></table>
<table class="index-cp" border="0">
<tbody><tr><td></td><th align="left">Index Entry</th><td>&nbsp;</td><th align="left"> Section</th></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_symbol-1">-</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-_002dno_002dsuppress_002c-libtool-compile-mode-option"><samp>-no-suppress</samp>, libtool compile mode option</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Creating-object-files">Creating object files</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-_002dweak-option"><samp>-weak</samp> option</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-with-dlopened-modules">Linking with dlopened modules</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_symbol-2">.</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-_002ela-files"><samp>.la</samp> files</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-libraries">Linking libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-_002elibs-subdirectory"><samp>.libs</samp> subdirectory</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-libraries">Linking libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-_002elo-files"><samp>.lo</samp> files</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Creating-object-files">Creating object files</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-A">A</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-aclocal">aclocal</a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fCONFIG_005fAUX_005fDIR"><code>AC_CONFIG_AUX_DIR</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtoolize">Invoking libtoolize</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fCONFIG_005fMACRO_005fDIRS"><code>AC_CONFIG_MACRO_DIRS</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtoolize">Invoking libtoolize</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fDISABLE_005fFAST_005fINSTALL"><code>AC_DISABLE_FAST_INSTALL</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fDISABLE_005fSHARED"><code>AC_DISABLE_SHARED</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fDISABLE_005fSTATIC"><code>AC_DISABLE_STATIC</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fENABLE_005fSHARED"><code>AC_ENABLE_SHARED</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fENABLE_005fSTATIC"><code>AC_ENABLE_STATIC</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fLIBLTDL_005fCONVENIENCE"><code>AC_LIBLTDL_CONVENIENCE</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing-libltdl">Distributing libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fLIBLTDL_005fINSTALLABLE"><code>AC_LIBLTDL_INSTALLABLE</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing-libltdl">Distributing libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fLIBTOOL_005fDLOPEN"><code>AC_LIBTOOL_DLOPEN</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fLIBTOOL_005fWIN32_005fDLL"><code>AC_LIBTOOL_WIN32_DLL</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fPROG_005fLIBTOOL"><code>AC_PROG_LIBTOOL</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AC_005fWITH_005fLTDL"><code>AC_WITH_LTDL</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing-libltdl">Distributing libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-allow_005fundefined_005fflag"><code>allow_undefined_flag</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-always_005fexport_005fsymbols"><code>always_export_symbols</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AM_005fDISABLE_005fSHARED"><code>AM_DISABLE_SHARED</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AM_005fDISABLE_005fSTATIC"><code>AM_DISABLE_STATIC</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AM_005fENABLE_005fSHARED"><code>AM_ENABLE_SHARED</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AM_005fENABLE_005fSTATIC"><code>AM_ENABLE_STATIC</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AM_005fPROG_005fLIBTOOL"><code>AM_PROG_LIBTOOL</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-application_002dlevel-dynamic-linking">application-level dynamic linking</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopened-modules">Dlopened modules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-application_002dlevel-dynamic-linking-1">application-level dynamic linking</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libltdl">Using libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-ar">ar</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-libraries">Linking libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AR"><code>AR</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-archiver_005flist_005fspec"><code>archiver_list_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-archive_005fcmds"><code>archive_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-archive_005fexpsym_005fcmds"><code>archive_expsym_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-AS"><code>AS</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-autoconf-traces">autoconf traces</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Trace-interface">Trace interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-avoiding-shared-libraries">avoiding shared libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static_002donly-libraries">Static-only libraries</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-B">B</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-bug-reports">bug reports</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Reporting-bugs">Reporting bugs</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-buggy-system-linkers">buggy system linkers</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-executables">Linking executables</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-bugs_002c-subtle-ones-caused-by-buggy-linkers">bugs, subtle ones caused by buggy linkers</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-executables">Linking executables</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-build"><code>build</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-build_005falias"><code>build_alias</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-build_005flibtool_005flibs"><code>build_libtool_libs</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-build_005fold_005flibs"><code>build_old_libs</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-build_005fos"><code>build_os</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-C">C</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-C-header-files_002c-portable">C header files, portable</a>:</td><td>&nbsp;</td><td valign="top"><a href="#C-header-files">C header files</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-C_002b_002b_002c-pitfalls">C++, pitfalls</a>:</td><td>&nbsp;</td><td valign="top"><a href="#C_002b_002b-libraries">C++ libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-C_002b_002b_002c-using">C++, using</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Other-languages">Other languages</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-C_002c-not-using">C, not using</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Other-languages">Other languages</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-CC"><code>CC</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-CC-1"><code>CC</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dconf_002etest">cdemo-conf.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dexec_002etest">cdemo-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dmake_002etest">cdemo-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dshared_002dexec_002etest">cdemo-shared-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dshared_002dmake_002etest">cdemo-shared-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dshared_002etest">cdemo-shared.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dstatic_002dexec_002etest">cdemo-static-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dstatic_002dmake_002etest">cdemo-static-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dstatic_002etest">cdemo-static.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dundef_002dexec_002etest">cdemo-undef-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dundef_002dmake_002etest">cdemo-undef-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cdemo_002dundef_002etest">cdemo-undef.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-CFLAGS"><code>CFLAGS</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-check_002dinteractive">‘<samp>check-interactive</samp>’</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-check_002dnoninteractive">‘<samp>check-noninteractive</samp>’</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-clean-mode">clean mode</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Clean-mode">Clean mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-command-options_002c-libtool">command options, libtool</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtool">Invoking libtool</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-command-options_002c-libtoolize">command options, libtoolize</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtoolize">Invoking libtoolize</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-compile-mode">compile mode</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Compile-mode">Compile mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-compiler_005fc_005fo"><code>compiler_c_o</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-compiler_005fneeds_005fobject"><code>compiler_needs_object</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-compiling-object-files">compiling object files</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Creating-object-files">Creating object files</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-complexity-of-library-systems">complexity of library systems</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Postmortem">Postmortem</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-config_002eguess">config.guess</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing">Distributing</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-config_002esub">config.sub</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing">Distributing</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-configuring-libtool">configuring libtool</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Configuring">Configuring</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-convenience-libraries">convenience libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static-libraries">Static libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-CPPFLAGS"><code>CPPFLAGS</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-cross-compile">cross compile</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Cross-compiling">Cross compiling</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-Cygwin-to-MinGW-Cross">Cygwin to MinGW Cross</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Cygwin-to-MinGW-Cross">Cygwin to MinGW Cross</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-D">D</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-debugging-libraries">debugging libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static_002donly-libraries">Static-only libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-definition-of-libraries">definition of libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libtool-paradigm">Libtool paradigm</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dconf_002etest">demo-conf.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002ddeplibs_002etest">demo-deplibs.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dexec_002etest">demo-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dhardcode_002etest">demo-hardcode.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dinst_002etest">demo-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dmake_002etest">demo-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dnofast_002dexec_002etest">demo-nofast-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dnofast_002dinst_002etest">demo-nofast-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dnofast_002dmake_002etest">demo-nofast-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dnofast_002dunst_002etest">demo-nofast-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dnofast_002etest">demo-nofast.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dnoinst_002dlink_002etest">demo-noinst-link.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dnopic_002dexec_002etest">demo-nopic-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dnopic_002dmake_002etest">demo-nopic-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dnopic_002etest">demo-nopic.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dpic_002dexec_002etest">demo-pic-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dpic_002dmake_002etest">demo-pic-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dpic_002etest">demo-pic.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002drelink_002etest">demo-relink.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dshared_002dexec_002etest">demo-shared-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dshared_002dinst_002etest">demo-shared-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dshared_002dmake_002etest">demo-shared-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dshared_002dunst_002etest">demo-shared-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dshared_002etest">demo-shared.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dstatic_002dexec_002etest">demo-static-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dstatic_002dinst_002etest">demo-static-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dstatic_002dmake_002etest">demo-static-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dstatic_002dunst_002etest">demo-static-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dstatic_002etest">demo-static.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-demo_002dunst_002etest">demo-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dconf_002etest">depdemo-conf.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dexec_002etest">depdemo-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dinst_002etest">depdemo-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dmake_002etest">depdemo-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dnofast_002dexec_002etest">depdemo-nofast-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dnofast_002dinst_002etest">depdemo-nofast-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dnofast_002dmake_002etest">depdemo-nofast-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dnofast_002dunst_002etest">depdemo-nofast-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dnofast_002etest">depdemo-nofast.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002drelink_002etest">depdemo-relink.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dshared_002dexec_002etest">depdemo-shared-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dshared_002dinst_002etest">depdemo-shared-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dshared_002dmake_002etest">depdemo-shared-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dshared_002dunst_002etest">depdemo-shared-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dshared_002etest">depdemo-shared.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dstatic_002dexec_002etest">depdemo-static-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dstatic_002dinst_002etest">depdemo-static-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dstatic_002dmake_002etest">depdemo-static-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dstatic_002dunst_002etest">depdemo-static-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dstatic_002etest">depdemo-static.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-depdemo_002dunst_002etest">depdemo-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dependencies-between-libraries">dependencies between libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Inter_002dlibrary-dependencies">Inter-library dependencies</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dependency-versioning">dependency versioning</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Versioning">Versioning</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-deplibs_005fcheck_005fmethod"><code>deplibs_check_method</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Porting-inter_002dlibrary-dependencies">Porting inter-library dependencies</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-design-issues">design issues</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Issues">Issues</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-design-of-library-interfaces">design of library interfaces</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Library-tips">Library tips</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-design-philosophy">design philosophy</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Motivation">Motivation</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-developing-libraries">developing libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static_002donly-libraries">Static-only libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlclose"><code>dlclose</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopened-modules">Dlopened modules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlclose-1"><code>dlclose</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libltdl">Using libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlerror"><code>dlerror</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libltdl">Using libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-DLLTOOL"><code>DLLTOOL</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlopen"><code>dlopen</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopened-modules">Dlopened modules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlopen-1"><code>dlopen</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libltdl">Using libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlopening-modules">dlopening modules</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopened-modules">Dlopened modules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlopening-modules-1">dlopening modules</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libltdl">Using libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlopening_002c-pitfalls">dlopening, pitfalls</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopen-issues">Dlopen issues</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlopen_005fself"><code>dlopen_self</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlopen_005fself_005fstatic"><code>dlopen_self_static</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlopen_005fsupport"><code>dlopen_support</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlsym"><code>dlsym</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopened-modules">Dlopened modules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dlsym-1"><code>dlsym</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libltdl">Using libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-double_002dcompilation_002c-avoiding">double-compilation, avoiding</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static_002donly-libraries">Static-only libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dynamic-dependencies">dynamic dependencies</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Versioning">Versioning</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dynamic-linking_002c-applications">dynamic linking, applications</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopened-modules">Dlopened modules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dynamic-linking_002c-applications-1">dynamic linking, applications</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libltdl">Using libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-dynamic-modules_002c-names">dynamic modules, names</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Finding-the-dlname">Finding the dlname</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-E">E</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-ECHO"><code>ECHO</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-eliding-shared-libraries">eliding shared libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static_002donly-libraries">Static-only libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-examples-of-using-libtool">examples of using libtool</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libtool">Using libtool</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-exclude_005fexpsyms"><code>exclude_expsyms</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-execute-mode">execute mode</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Execute-mode">Execute mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-export_005fdynamic_005fflag_005fspec"><code>export_dynamic_flag_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-export_005fsymbols_005fcmds"><code>export_symbols_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-extract_005fexpsyms_005fcmds"><code>extract_expsyms_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-F">F</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-f77demo_002dconf_002etest">f77demo-conf.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-f77demo_002dexec_002etest">f77demo-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-f77demo_002dmake_002etest">f77demo-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-f77demo_002dshared_002dexec_002etest">f77demo-shared-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-f77demo_002dshared_002dmake_002etest">f77demo-shared-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-f77demo_002dshared_002etest">f77demo-shared.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-f77demo_002dstatic_002dexec_002etest">f77demo-static-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-f77demo_002dstatic_002dmake_002etest">f77demo-static-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-f77demo_002dstatic_002etest">f77demo-static.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-failed-tests">failed tests</a>:</td><td>&nbsp;</td><td valign="top"><a href="#When-tests-fail">When tests fail</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-fast_005finstall"><code>fast_install</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-fcdemo_002dconf_002etest">fcdemo-conf.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-fcdemo_002dexec_002etest">fcdemo-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-fcdemo_002dmake_002etest">fcdemo-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-fcdemo_002dshared_002dexec_002etest">fcdemo-shared-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-fcdemo_002dshared_002dmake_002etest">fcdemo-shared-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-fcdemo_002dshared_002etest">fcdemo-shared.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-fcdemo_002dstatic_002dexec_002etest">fcdemo-static-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-fcdemo_002dstatic_002dmake_002etest">fcdemo-static-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-fcdemo_002dstatic_002etest">fcdemo-static.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-FDL_002c-GNU-Free-Documentation-License">FDL, GNU Free Documentation License</a>:</td><td>&nbsp;</td><td valign="top"><a href="#GNU-Free-Documentation-License">GNU Free Documentation License</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-file-name-conversion">file name conversion</a>:</td><td>&nbsp;</td><td valign="top"><a href="#File-name-conversion">File name conversion</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-File-Name-Conversion-_002d-Cygwin-to-Windows">File Name Conversion - Cygwin to Windows</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Cygwin_002fWindows-File-Name-Conversion">Cygwin/Windows File Name Conversion</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-File-Name-Conversion-_002d-Failure">File Name Conversion - Failure</a>:</td><td>&nbsp;</td><td valign="top"><a href="#File-Name-Conversion-Failure">File Name Conversion Failure</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-File-Name-Conversion-_002d-MinGW">File Name Conversion - MinGW</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Native-MinGW-File-Name-Conversion">Native MinGW File Name Conversion</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-File-Name-Conversion-_002d-Unix-to-Windows">File Name Conversion - Unix to Windows</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Unix_002fWindows-File-Name-Conversion">Unix/Windows File Name Conversion</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-file_005fmagic"><code>file_magic</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Porting-inter_002dlibrary-dependencies">Porting inter-library dependencies</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-file_005fmagic_005fcmd"><code>file_magic_cmd</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Porting-inter_002dlibrary-dependencies">Porting inter-library dependencies</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-file_005fmagic_005fglob"><code>file_magic_glob</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-file_005fmagic_005ftest_005ffile"><code>file_magic_test_file</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Porting-inter_002dlibrary-dependencies">Porting inter-library dependencies</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-finish-mode">finish mode</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Finish-mode">Finish mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-finish_005fcmds"><code>finish_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-finish_005feval"><code>finish_eval</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-formal-versioning">formal versioning</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libtool-versioning">Libtool versioning</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-func_005fconvert_005ffile_005fcygwin_005fto_005fw32">func_convert_file_cygwin_to_w32</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Cygwin-to-MinGW-Cross">Cygwin to MinGW Cross</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-func_005fconvert_005ffile_005fcygwin_005fto_005fw32-1">func_convert_file_cygwin_to_w32</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Cygwin-to-MinGW-Cross">Cygwin to MinGW Cross</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-G">G</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-global-functions">global functions</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Library-tips">Library tips</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-global_005fsymbol_005fpipe"><code>global_symbol_pipe</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-global_005fsymbol_005fto_005fcdecl"><code>global_symbol_to_cdecl</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-H">H</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-hardcode_005faction"><code>hardcode_action</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-hardcode_005fdirect"><code>hardcode_direct</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-hardcode_005fdirect_005fabsolute"><code>hardcode_direct_absolute</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-hardcode_005finto_005flibs"><code>hardcode_into_libs</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-hardcode_005flibdir_005fflag_005fspec"><code>hardcode_libdir_flag_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-hardcode_005flibdir_005fseparator"><code>hardcode_libdir_separator</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-hardcode_005fminus_005fL"><code>hardcode_minus_L</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-hardcode_005fshlibpath_005fvar"><code>hardcode_shlibpath_var</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-header-files">header files</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Library-tips">Library tips</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-host"><code>host</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-host_005falias"><code>host_alias</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-host_005fos"><code>host_os</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-I">I</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-implementation-of-libtool">implementation of libtool</a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-include-files_002c-portable">include files, portable</a>:</td><td>&nbsp;</td><td valign="top"><a href="#C-header-files">C header files</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-include_005fexpsyms"><code>include_expsyms</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-inferring-tags">inferring tags</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Tags">Tags</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-inherit_005frpath"><code>inherit_rpath</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-install">install</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Installing-libraries">Installing libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-install-mode">install mode</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Install-mode">Install mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-install_002dsh">install-sh</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing">Distributing</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-installation_002c-finishing">installation, finishing</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Installing-libraries">Installing libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-install_005foverride_005fmode"><code>install_override_mode</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-inter_002dlibrary-dependencies">inter-library dependencies</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Inter_002dlibrary-dependencies">Inter-library dependencies</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-inter_002dlibrary-dependency">inter-library dependency</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Porting-inter_002dlibrary-dependencies">Porting inter-library dependencies</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-L">L</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-language-names">language names</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Tags">Tags</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-languages_002c-non_002dC">languages, non-C</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Other-languages">Other languages</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LD"><code>LD</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LD-1"><code>LD</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LDFLAGS"><code>LDFLAGS</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libext"><code>libext</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libltdl"><code>libltdl</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libltdl">Using libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libname_005fspec"><code>libname_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libraries_002c-definition-of">libraries, definition of</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libtool-paradigm">Libtool paradigm</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libraries_002c-finishing-installation">libraries, finishing installation</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Installing-libraries">Installing libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libraries_002c-stripping">libraries, stripping</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Installing-libraries">Installing libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-library-interfaces">library interfaces</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Interfaces">Interfaces</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-library-interfaces_002c-design">library interfaces, design</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Library-tips">Library tips</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-library-object-file">library object file</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Creating-object-files">Creating object files</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-library_005fnames_005fspec"><code>library_names_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LIBS"><code>LIBS</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libtool">libtool</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtool">Invoking libtool</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libtool-command-options">libtool command options</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtool">Invoking libtool</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libtool-examples">libtool examples</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libtool">Using libtool</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libtool-implementation">libtool implementation</a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libtool-libraries">libtool libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-libraries">Linking libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libtool-library-versions">libtool library versions</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libtool-versioning">Libtool versioning</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libtool-specifications">libtool specifications</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Motivation">Motivation</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libtoolize">libtoolize</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtoolize">Invoking libtoolize</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-libtoolize-command-options">libtoolize command options</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtoolize">Invoking libtoolize</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LIBTOOLIZE_005fOPTIONS">LIBTOOLIZE_OPTIONS</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtoolize">Invoking libtoolize</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-link-mode">link mode</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Link-mode">Link mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-link_002d2_002etest">link-2.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-link_002etest">link.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-linking-against-installed-libraries">linking against installed libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-executables">Linking executables</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-linking-against-uninstalled-libraries">linking against uninstalled libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-executables">Linking executables</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-linking-with-installed-libtool-libraries">linking with installed libtool libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-executables">Linking executables</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-linking_002c-dlopen">linking, dlopen</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-with-dlopened-modules">Linking with dlopened modules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-linking_002c-dlpreopen">linking, dlpreopen</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-with-dlopened-modules">Linking with dlopened modules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-linking_002c-partial">linking, partial</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Link-mode">Link mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-link_005fall_005fdeplibs"><code>link_all_deplibs</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-link_005fstatic_005fflag"><code>link_static_flag</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LN_005fS"><code>LN_S</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lock_005fold_005farchive_005fextraction"><code>lock_old_archive_extraction</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LTCC"><code>LTCC</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LTCFLAGS"><code>LTCFLAGS</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LTDL_005fCONVENIENCE"><code>LTDL_CONVENIENCE</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing-libltdl">Distributing libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LTDL_005fINIT"><code>LTDL_INIT</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing-libltdl">Distributing libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LTDL_005fINSTALLABLE"><code>LTDL_INSTALLABLE</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing-libltdl">Distributing libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LTDL_005fSET_005fPRELOADED_005fSYMBOLS"><code>LTDL_SET_PRELOADED_SYMBOLS</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlpreopening">Dlpreopening</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LTLIBOBJS">LTLIBOBJS</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-and-LTLIBOBJS">Autoconf and LTLIBOBJS</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LTLIBRARIES"><code>LTLIBRARIES</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-Automake">Using Automake</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-ltmain_002esh">ltmain.sh</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing">Distributing</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fCMD_005fMAX_005fLEN"><code>LT_CMD_MAX_LEN</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fCONFIG_005fLTDL_005fDIR"><code>LT_CONFIG_LTDL_DIR</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing-libltdl">Distributing libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fcv_005fto_005fhost_005ffile_005fcmd">lt_cv_to_host_file_cmd</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Cygwin-to-MinGW-Cross">Cygwin to MinGW Cross</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fcv_005fto_005ftool_005ffile_005fcmd">lt_cv_to_tool_file_cmd</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Cygwin-to-MinGW-Cross">Cygwin to MinGW Cross</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fcv_005fto_005ftool_005ffile_005fcmd-1">lt_cv_to_tool_file_cmd</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Cygwin-to-MinGW-Cross">Cygwin to MinGW Cross</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fCYGPATH">LT_CYGPATH</a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fCYGPATH">LT_CYGPATH</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fDIRSEP_005fCHAR"><code>LT_DIRSEP_CHAR</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdladderror"><code>lt_dladderror</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdladdsearchdir"><code>lt_dladdsearchdir</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdladvise"><code>lt_dladvise</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdladvise_005fdestroy"><code>lt_dladvise_destroy</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdladvise_005fext"><code>lt_dladvise_ext</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdladvise_005fglobal"><code>lt_dladvise_global</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdladvise_005finit"><code>lt_dladvise_init</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdladvise_005flocal"><code>lt_dladvise_local</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdladvise_005fpreload"><code>lt_dladvise_preload</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdladvise_005fresident"><code>lt_dladvise_resident</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlcaller_005fget_005fdata"><code>lt_dlcaller_get_data</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlcaller_005fset_005fdata"><code>lt_dlcaller_set_data</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlclose"><code>lt_dlclose</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlerror"><code>lt_dlerror</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlexit"><code>lt_dlexit</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlforeachfile"><code>lt_dlforeachfile</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlgetinfo"><code>lt_dlgetinfo</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlgetsearchpath"><code>lt_dlgetsearchpath</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlhandle"><code>lt_dlhandle</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlhandle_005ffetch"><code>lt_dlhandle_fetch</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlhandle_005finterface"><code>lt_dlhandle_interface</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlhandle_005fiterate"><code>lt_dlhandle_iterate</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlhandle_005fmap"><code>lt_dlhandle_map</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlinfo"><code>lt_dlinfo</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlinit"><code>lt_dlinit</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlinsertsearchdir"><code>lt_dlinsertsearchdir</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlinterface_005ffree"><code>lt_dlinterface_free</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlinterface_005fid"><code>lt_dlinterface_id</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlinterface_005fregister"><code>lt_dlinterface_register</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#User-defined-module-data">User defined module data</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlisresident"><code>lt_dlisresident</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlloader"><code>lt_dlloader</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlloader_005fadd"><code>lt_dlloader_add</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlloader_005fdata"><code>lt_dlloader_data</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlloader_005fexit"><code>lt_dlloader_exit</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlloader_005ffind"><code>lt_dlloader_find</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlloader_005fname"><code>lt_dlloader_name</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlloader_005fnext"><code>lt_dlloader_next</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlloader_005fremove"><code>lt_dlloader_remove</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlmakeresident"><code>lt_dlmakeresident</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlopen"><code>lt_dlopen</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlopenadvise"><code>lt_dlopenadvise</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlopenext"><code>lt_dlopenext</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlpreload"><code>lt_dlpreload</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlpreopening">Dlpreopening</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlpreload_005fcallback_005ffunc"><code>lt_dlpreload_callback_func</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlpreopening">Dlpreopening</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlpreload_005fdefault"><code>lt_dlpreload_default</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlpreopening">Dlpreopening</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlpreload_005fopen"><code>lt_dlpreload_open</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlpreopening">Dlpreopening</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlseterror"><code>lt_dlseterror</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlsetsearchpath"><code>lt_dlsetsearchpath</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlsym"><code>lt_dlsym</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlsymlist"><code>lt_dlsymlist</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlpreopening">Dlpreopening</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fdlsymlist-1"><code>lt_dlsymlist</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005ffind_005fsym"><code>lt_find_sym</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fFUNC_005fDLSYM_005fUSCORE"><code>LT_FUNC_DLSYM_USCORE</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fINIT"><code>LT_INIT</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fLANG"><code>LT_LANG</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fLIB_005fDLLOAD"><code>LT_LIB_DLLOAD</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fLIB_005fM"><code>LT_LIB_M</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fmodule"><code>lt_module</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fmodule_005fclose"><code>lt_module_close</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fmodule_005fopen"><code>lt_module_open</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fOUTPUT"><code>LT_OUTPUT</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fPATHSEP_005fCHAR"><code>LT_PATHSEP_CHAR</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libltdl-interface">Libltdl interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fPATH_005fLD"><code>LT_PATH_LD</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fPATH_005fNM"><code>LT_PATH_NM</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fpreloaded_005fsymbols_005b_005d"><code>lt_preloaded_symbols[]</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlpreopening">Dlpreopening</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fPREREQ"><code>LT_PREREQ</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fSUPPORTED_005fTAG"><code>LT_SUPPORTED_TAG</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Trace-interface">Trace interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fSYS_005fDLOPEN_005fDEPLIBS"><code>LT_SYS_DLOPEN_DEPLIBS</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fSYS_005fDLOPEN_005fSELF"><code>LT_SYS_DLOPEN_SELF</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fSYS_005fDLSEARCH_005fPATH"><code>LT_SYS_DLSEARCH_PATH</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fSYS_005fLIBRARY_005fPATH"><code>LT_SYS_LIBRARY_PATH</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fSYS_005fMODULE_005fEXT"><code>LT_SYS_MODULE_EXT</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fSYS_005fMODULE_005fPATH"><code>LT_SYS_MODULE_PATH</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fSYS_005fSYMBOL_005fUSCORE"><code>LT_SYS_SYMBOL_USCORE</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Autoconf-macros">Autoconf macros</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fuser_005fdata"><code>lt_user_data</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-lt_005fuser_005fdlloader"><code>lt_user_dlloader</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Module-loaders-for-libltdl">Module loaders for libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-LT_005fWITH_005fLTDL"><code>LT_WITH_LTDL</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Distributing-libltdl">Distributing libltdl</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-M">M</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-macro_005frevision"><code>macro_revision</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-macro_005fversion"><code>macro_version</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-Makefile">Makefile</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Makefile-rules">Makefile rules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-Makefile_002eam">Makefile.am</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Makefile-rules">Makefile rules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-Makefile_002ein">Makefile.in</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Makefile-rules">Makefile rules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-MANIFEST_005fTOOL"><code>MANIFEST_TOOL</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-max_005fcmd_005flen"><code>max_cmd_len</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dconf_002etest">mdemo-conf.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002ddryrun_002etest">mdemo-dryrun.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dexec_002etest">mdemo-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dinst_002etest">mdemo-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dmake_002etest">mdemo-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dshared_002dexec_002etest">mdemo-shared-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dshared_002dinst_002etest">mdemo-shared-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dshared_002dmake_002etest">mdemo-shared-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dshared_002dunst_002etest">mdemo-shared-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dshared_002etest">mdemo-shared.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dstatic_002dexec_002etest">mdemo-static-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dstatic_002dinst_002etest">mdemo-static-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dstatic_002dmake_002etest">mdemo-static-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dstatic_002dunst_002etest">mdemo-static-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dstatic_002etest">mdemo-static.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo_002dunst_002etest">mdemo-unst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo2_002dconf_002etest">mdemo2-conf.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo2_002dexec_002etest">mdemo2-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mdemo2_002dmake_002etest">mdemo2-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mode_002c-clean">mode, clean</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Clean-mode">Clean mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mode_002c-compile">mode, compile</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Compile-mode">Compile mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mode_002c-execute">mode, execute</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Execute-mode">Execute mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mode_002c-finish">mode, finish</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Finish-mode">Finish mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mode_002c-install">mode, install</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Install-mode">Install mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mode_002c-link">mode, link</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Link-mode">Link mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-mode_002c-uninstall">mode, uninstall</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Uninstall-mode">Uninstall mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-modules_002c-dynamic">modules, dynamic</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopened-modules">Dlopened modules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-modules_002c-dynamic-1">modules, dynamic</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libltdl">Using libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-motivation-for-writing-libtool">motivation for writing libtool</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Motivation">Motivation</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-MSYS">MSYS</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Native-MinGW-File-Name-Conversion">Native MinGW File Name Conversion</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-N">N</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-names-of-dynamic-modules">names of dynamic modules</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Finding-the-dlname">Finding the dlname</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-need_005flib_005fprefix"><code>need_lib_prefix</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-need_005flocks"><code>need_locks</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-need_005fversion"><code>need_version</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-NM"><code>NM</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-NM-1"><code>NM</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-nm_005ffile_005flist_005fspec"><code>nm_file_list_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-nomode_002etest">nomode.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-none"><code>none</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Porting-inter_002dlibrary-dependencies">Porting inter-library dependencies</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-no_005fbuiltin_005fflag"><code>no_builtin_flag</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-no_005fundefined_005fflag"><code>no_undefined_flag</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-O">O</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-objdir"><code>objdir</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-OBJDUMP"><code>OBJDUMP</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-object-files_002c-compiling">object files, compiling</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Creating-object-files">Creating object files</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-object-files_002c-library">object files, library</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Creating-object-files">Creating object files</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-objectlist_002etest">objectlist.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-objext"><code>objext</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-old_005farchive_005fcmds"><code>old_archive_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-old_005farchive_005ffrom_005fexpsyms_005fcmds"><code>old_archive_from_expsyms_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-old_005farchive_005ffrom_005fnew_005fcmds"><code>old_archive_from_new_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-old_005fpostinstall_005fcmds"><code>old_postinstall_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-old_005fpostuninstall_005fcmds"><code>old_postuninstall_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-old_005fstriplib"><code>old_striplib</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-opaque-data-types">opaque data types</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Library-tips">Library tips</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-options_002c-libtool-command">options, libtool command</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtool">Invoking libtool</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-options_002c-libtoolize-command">options, libtoolize command</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Invoking-libtoolize">Invoking libtoolize</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-other-implementations_002c-flaws-in">other implementations, flaws in</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Postmortem">Postmortem</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-P">P</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-partial-linking">partial linking</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Link-mode">Link mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-pass_005fall"><code>pass_all</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Porting-inter_002dlibrary-dependencies">Porting inter-library dependencies</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-path-conversion">path conversion</a>:</td><td>&nbsp;</td><td valign="top"><a href="#File-name-conversion">File name conversion</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-Path-Conversion-_002d-Cygwin-to-Windows">Path Conversion - Cygwin to Windows</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Cygwin_002fWindows-File-Name-Conversion">Cygwin/Windows File Name Conversion</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-Path-Conversion-_002d-Failure">Path Conversion - Failure</a>:</td><td>&nbsp;</td><td valign="top"><a href="#File-Name-Conversion-Failure">File Name Conversion Failure</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-Path-Conversion-_002d-MinGW">Path Conversion - MinGW</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Native-MinGW-File-Name-Conversion">Native MinGW File Name Conversion</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-Path-Conversion-_002d-Unix-to-Windows">Path Conversion - Unix to Windows</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Unix_002fWindows-File-Name-Conversion">Unix/Windows File Name Conversion</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-pdemo_002dconf_002etest">pdemo-conf.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-pdemo_002dexec_002etest">pdemo-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-pdemo_002dinst_002etest">pdemo-inst.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-pdemo_002dmake_002etest">pdemo-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-PIC-_0028position_002dindependent-code_0029">PIC (position-independent code)</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Creating-object-files">Creating object files</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-pic_005fflag"><code>pic_flag</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-pitfalls-using-C_002b_002b">pitfalls using C++</a>:</td><td>&nbsp;</td><td valign="top"><a href="#C_002b_002b-libraries">C++ libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-pitfalls-with-dlopen">pitfalls with dlopen</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopen-issues">Dlopen issues</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-portable-C-headers">portable C headers</a>:</td><td>&nbsp;</td><td valign="top"><a href="#C-header-files">C header files</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-position_002dindependent-code">position-independent code</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Creating-object-files">Creating object files</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-postinstallation">postinstallation</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Installing-libraries">Installing libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-postinstall_005fcmds"><code>postinstall_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-postlink_005fcmds"><code>postlink_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-postuninstall_005fcmds"><code>postuninstall_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-problem-reports">problem reports</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Reporting-bugs">Reporting bugs</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-problems_002c-blaming-somebody-else-for">problems, blaming somebody else for</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Troubleshooting">Troubleshooting</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-problems_002c-solving">problems, solving</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Troubleshooting">Troubleshooting</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-program-wrapper-executables">program wrapper executables</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Wrapper-executables">Wrapper executables</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-program-wrapper-scripts">program wrapper scripts</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-executables">Linking executables</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-Q">Q</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-quote_002etest">quote.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-R">R</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-ranlib">ranlib</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-libraries">Linking libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-RANLIB"><code>RANLIB</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#LT_005fINIT">LT_INIT</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-RANLIB-1"><code>RANLIB</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-reload_005fcmds"><code>reload_cmds</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-reload_005fflag"><code>reload_flag</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-renaming-interface-functions">renaming interface functions</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Library-tips">Library tips</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-reporting-bugs">reporting bugs</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Reporting-bugs">Reporting bugs</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-reusability-of-library-systems">reusability of library systems</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Postmortem">Postmortem</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-runpath_005fvar"><code>runpath_var</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-S">S</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-saving-time">saving time</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static_002donly-libraries">Static-only libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-security-problems-with-buggy-linkers">security problems with buggy linkers</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-executables">Linking executables</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-sh_002etest">sh.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-shared-libraries_002c-not-using">shared libraries, not using</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static_002donly-libraries">Static-only libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-shared-library-versions">shared library versions</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Versioning">Versioning</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-shlibpath_005foverrides_005frunpath"><code>shlibpath_overrides_runpath</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-shlibpath_005fvar"><code>shlibpath_var</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-shl_005fload"><code>shl_load</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopened-modules">Dlopened modules</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-shl_005fload-1"><code>shl_load</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Using-libltdl">Using libltdl</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-solving-problems">solving problems</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Troubleshooting">Troubleshooting</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-soname_005fspec"><code>soname_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-specifications-for-libtool">specifications for libtool</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Motivation">Motivation</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-standalone-binaries">standalone binaries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static-libraries">Static libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-static-linking">static linking</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static-libraries">Static libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-strip">strip</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Installing-libraries">Installing libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-striplib"><code>striplib</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-stripping-libraries">stripping libraries</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Installing-libraries">Installing libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-su">su</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Installing-libraries">Installing libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-suffix_002etest">suffix.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-sys_005flib_005fdlsearch_005fpath_005fspec"><code>sys_lib_dlsearch_path_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-sys_005flib_005fsearch_005fpath_005fspec"><code>sys_lib_search_path_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-T">T</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-tag-names">tag names</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Tags">Tags</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dconf_002etest">tagdemo-conf.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dexec_002etest">tagdemo-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dmake_002etest">tagdemo-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dshared_002dexec_002etest">tagdemo-shared-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dshared_002dmake_002etest">tagdemo-shared-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dshared_002etest">tagdemo-shared.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dstatic_002dexec_002etest">tagdemo-static-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dstatic_002dmake_002etest">tagdemo-static-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dstatic_002etest">tagdemo-static.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dundef_002dexec_002etest">tagdemo-undef-exec.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dundef_002dmake_002etest">tagdemo-undef-make.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tagdemo_002dundef_002etest">tagdemo-undef.test</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Test-descriptions">Test descriptions</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-test-suite">test suite</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libtool-test-suite">Libtool test suite</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tests_002c-failed">tests, failed</a>:</td><td>&nbsp;</td><td valign="top"><a href="#When-tests-fail">When tests fail</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-test_005fcompile"><code>test_compile</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Porting-inter_002dlibrary-dependencies">Porting inter-library dependencies</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-thread_005fsafe_005fflag_005fspec"><code>thread_safe_flag_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-time_002c-saving">time, saving</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static_002donly-libraries">Static-only libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-to_005fhost_005ffile_005fcmd"><code>to_host_file_cmd</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-to_005ftool_005ffile_005fcmd"><code>to_tool_file_cmd</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-trace-interface">trace interface</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Trace-interface">Trace interface</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-tricky-design-issues">tricky design issues</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Issues">Issues</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-trouble-with-C_002b_002b">trouble with C++</a>:</td><td>&nbsp;</td><td valign="top"><a href="#C_002b_002b-libraries">C++ libraries</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-trouble-with-dlopen">trouble with dlopen</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Dlopen-issues">Dlopen issues</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-troubleshooting">troubleshooting</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Troubleshooting">Troubleshooting</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-U">U</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-undefined-symbols_002c-allowing">undefined symbols, allowing</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Link-mode">Link mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-uninstall-mode">uninstall mode</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Uninstall-mode">Uninstall mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-unknown"><code>unknown</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#Porting-inter_002dlibrary-dependencies">Porting inter-library dependencies</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-unresolved-symbols_002c-allowing">unresolved symbols, allowing</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Link-mode">Link mode</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-using-shared-libraries_002c-not">using shared libraries, not</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Static_002donly-libraries">Static-only libraries</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-V">V</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-versioning_002c-formal">versioning, formal</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Libtool-versioning">Libtool versioning</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-version_005ftype"><code>version_type</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
<tr><th id="Combined-Index_cp_letter-W">W</th><td></td><td></td></tr>
<tr><td></td><td valign="top"><a href="#index-want_005fnocaseglob"><code>want_nocaseglob</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-whole_005farchive_005fflag_005fspec"><code>whole_archive_flag_spec</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-Windows-DLLs">Windows DLLs</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Windows-DLLs">Windows DLLs</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-wl"><code>wl</code></a>:</td><td>&nbsp;</td><td valign="top"><a href="#libtool-script-contents">libtool script contents</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-wrapper-executables-for-uninstalled-programs">wrapper executables for uninstalled programs</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Wrapper-executables">Wrapper executables</a></td></tr>
<tr><td></td><td valign="top"><a href="#index-wrapper-scripts-for-programs">wrapper scripts for programs</a>:</td><td>&nbsp;</td><td valign="top"><a href="#Linking-executables">Linking executables</a></td></tr>
<tr><td colspan="4"> <hr></td></tr>
</tbody></table>
<table><tbody><tr><th valign="top">Jump to: &nbsp; </th><td><a class="summary-letter" href="#Combined-Index_cp_symbol-1"><b>-</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_symbol-2"><b>.</b></a>
 &nbsp; 
<br>
<a class="summary-letter" href="#Combined-Index_cp_letter-A"><b>A</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-B"><b>B</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-C"><b>C</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-D"><b>D</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-E"><b>E</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-F"><b>F</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-G"><b>G</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-H"><b>H</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-I"><b>I</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-L"><b>L</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-M"><b>M</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-N"><b>N</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-O"><b>O</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-P"><b>P</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-Q"><b>Q</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-R"><b>R</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-S"><b>S</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-T"><b>T</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-U"><b>U</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-V"><b>V</b></a>
 &nbsp; 
<a class="summary-letter" href="#Combined-Index_cp_letter-W"><b>W</b></a>
 &nbsp; 
</td></tr></tbody></table>

<div class="footnote">
<hr>
<h4 class="footnotes-heading">Footnotes</h4>

<h5><a id="FOOT1" href="#DOCF1">(1)</a></h5>
<p>If you don’t
specify an <code>rpath</code>, then libtool builds a libtool convenience
archive, not a shared library (see <a href="#Static-libraries">Static libraries</a>).</p>
<h5><a id="FOOT2" href="#DOCF2">(2)</a></h5>
<p>However, you should avoid using
<samp>-L</samp> or <samp>-l</samp> flags to link against an uninstalled libtool
library.  Just specify the relative path to the <samp>.la</samp> file, such as
<samp>../intl/libintl.la</samp>.  This is a design decision to eliminate any
ambiguity when linking against uninstalled shared libraries.</p>
<h5><a id="FOOT3" href="#DOCF3">(3)</a></h5>
<p>And why should we? <samp>main.o</samp> doesn’t directly depend on <samp>-lm</samp>
after all.
</p>
<h5><a id="FOOT4" href="#DOCF4">(4)</a></h5>
<p>Don’t
strip static libraries though, or they will be unusable.</p>
<h5><a id="FOOT5" href="#DOCF5">(5)</a></h5>
<p>Since GNU Automake 1.5, the flags <samp>-dlopen</samp>
or <samp>-dlpreopen</samp> (see <a href="#Link-mode">Link mode</a>) can be employed with the
‘<samp>program_LDADD</samp>’ variable.  Unfortunately, older releases didn’t
accept these flags, so if you are stuck with an ancient Automake, we
recommend quoting the flag itself, and setting
‘<samp>program_DEPENDENCIES</samp>’ too:
</p>
<div class="example">
<pre class="example">program_LDADD = "-dlopen" libfoo.la
program_DEPENDENCIES = libfoo.la
</pre></div>
<h5><a id="FOOT6" href="#DOCF6">(6)</a></h5>
<p><code>LT_INIT</code> requires
that you define the <samp>Makefile</samp> variable <code>top_builddir</code> in your
<samp>Makefile.in</samp>.  Automake does this automatically, but Autoconf
users should set it to the relative path to the top of your build
directory (<samp>../..</samp>, for example).</p>
<h5><a id="FOOT7" href="#DOCF7">(7)</a></h5>
<p>GNU Image
Manipulation Program, for those who haven’t taken the plunge.  See
<a href="http://www.gimp.org/">http://www.gimp.org/</a>.</p>
<h5><a id="FOOT8" href="#DOCF8">(8)</a></h5>
<p>We used to recommend <code>__P</code>,
<code>__BEGIN_DECLS</code> and <code>__END_DECLS</code>.  This was bad advice since
symbols (even preprocessor macro names) that begin with an underscore
are reserved for the use of the compiler.</p>
<h5><a id="FOOT9" href="#DOCF9">(9)</a></h5>
<p><code>LIBPATH</code>
on AIX, and <code>SHLIB_PATH</code> on HP-UX.</p>
<h5><a id="FOOT10" href="#DOCF10">(10)</a></h5>
<p>Some platforms, notably Mac OS X,
differentiate between a runtime library that cannot be opened by
<code>lt_dlopen</code> and a dynamic module that can.  For maximum
portability you should try to ensure that you only pass
<code>lt_dlopen</code> objects that have been compiled with libtool’s
<samp>-module</samp> flag.</p>
<h5><a id="FOOT11" href="#DOCF11">(11)</a></h5>
<p>This is used for
the host dependent module loading API – <code>shl_load</code> and
<code>LoadLibrary</code> for example</p>
<h5><a id="FOOT12" href="#DOCF12">(12)</a></h5>
<p>We used to recommend adding the contents of <samp>ltdl.m4</samp> to
<samp>acinclude.m4</samp>, but with <code>aclocal</code> from a modern
Automake (1.8 or newer) and this release of libltdl that is not only
unnecessary but makes it easy to forget to upgrade <samp>acinclude.m4</samp>
if you move to a different release of libltdl.
</p>
<h5><a id="FOOT13" href="#DOCF13">(13)</a></h5>
<p>Even if libltdl is installed, ‘<samp>LTDL_INIT</samp>’ may fail
to detect it if libltdl depends on symbols provided by libraries
other than the C library.
</p>
<h5><a id="FOOT14" href="#DOCF14">(14)</a></h5>
<p>All code compiled
for the PowerPC and RS/6000 chips (<code>powerpc-*-*</code>, <code>powerpcle-*-*</code>,
and <code>rs6000-*-*</code>) is position-independent, regardless of the operating
system or compiler suite.  So, “regular objects” can be used to build
shared libraries on these systems and no special PIC compiler flags are
required.</p>
</div>
<hr>





</body></html>