---
layout: workshop      # DON'T CHANGE THIS.
carpentry: "dc"    # what kind of Carpentry (must be either "lc" or "dc" or "swc").  
                      # Be sure to update the Carpentry type in _config.yml as well.  
venue: "Massey"        # brief name of host site without address (e.g., "Euphoric State University")
address: null      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria")
country: null      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes)
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
latlng: "null"       # decimal latitude and longitude of workshop venue (e.g., "41.7901128,-87.6007318" - use https://www.latlong.net/)
humandate: "Wed, Mar 6, 2019"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9am - 5pm"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
instructor: ["David Winter"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Shannon Ormond"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["dwinter@massey.ac.nz"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
---

{% if page.carpentry != site.carpentry %}
<div class="alert alert-warning">
You specified <code>carpentry: {{page.carpentry}}</code> in <code>index.md</code> and
<code>carpentry: {{site.carpentry}}</code> in <code>_config.yml</code>. Make sure you edit both files. After editing <code>_config.yml</code>, you need to run <code>make serve</code> again to 
see the changes take effect locally.
</div>
{% endif %}



<h2 id="general">General Information</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if page.carpentry == "swc" %}
{% include sc/intro.html %}
{% elsif page.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif page.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if page.carpentry == "swc" %}
{% include sc/who.html %}
{% elsif page.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif page.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://itouchmap.com/latlong.html to find the lat/long of an
address.
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Where:</strong> ScC5.15 (i.e the Electronic room on the 5th floor of
  Science Tower C).
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

<p>
 <strong>Slack</strong>: We will use slack, a messaging app, during the
 workshop. Please <a
 href="https://join.slack.com/t/massey-bioinformatics/shared_invite/enQtNTYyMzQyMDAxNDg4LWVlMDJiYzI0M2ZmYjVhM2NmYzVlZWQ5MmMyYTY3Y2NmOTA4YjA0YzkxNDNhYjIzY2FkMTA2M2RlY2FiNjE3ZDc">sign up for the Massey Bioinformatics Slack here</a>.

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong> Participants must bring a laptop with a
  Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on. They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<p id="code-of-conduct">
<strong>Code of Conduct:</strong>  We ask that all participants conform to The Carpentries
<a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>



{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact</strong>:
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<hr/>



{% comment %}
SCHEDULE

Show the workshop's schedule.  Edit the items and times in the table
to match your plans.  You may also want to change 'Day 1' and 'Day
2' to be actual dates or days of the week.
{% endcomment %}
<h2 id="schedule">Schedule</h2>

{% if page.carpentry == "swc" %}
{% include sc/schedule.html %}
{% elsif page.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif page.carpentry == "lc" %}
{% include lc/schedule.html %}
{% endif %}

{% comment %}


If you want to use an Etherpad, go to

http://pad.software-carpentry.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  We will use this <a href="{{page.collaborative_notes}}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
{% endif %}

<hr/>

{% comment %}
SYLLABUS

Show what topics will be covered.

1. If your workshop is R rather than Python, remove the comment
around that section and put a comment around the Python section.
2. Some workshops will delete SQL.
3. Please make sure the list of topics is synchronized with what you
intend to teach.
4. You may need to move the div's with class="col-md-6" around inside
the div's with class="row" to balance the multi-column layout.

This is one of the places where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}
<h2 id="syllabus">Syllabus</h2>

{% if page.carpentry == "swc" %}
{% include sc/syllabus.html %}
{% elsif page.carpentry == "dc" %}
{% include dc/syllabus.html %}
{% elsif page.carpentry == "lc" %}
{% include lc/syllabus.html %}
{% endif %}

<hr/>

{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in a
  {% if page.carpentry == "swc" %}
  Software Carpentry
  {% elsif page.carpentry == "dc" %}
  Data Carpentry
  {% elsif page.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to the software described below.
  In addition, you will need an up-to-date web browser.
</p>
<p>
  We maintain a list of common issues that occur during installation as a reference for instructors
  that may be useful on the
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

<div id="shell"> {% comment %} Start of 'shell' section. {% endcomment %}
  <h3>The Bash Shell</h3>
  <p>
    Bash is a commonly-used shell that gives you the power to do simple
    tasks more quickly.
  </p>

  <div>
    <ul class="nav nav-tabs nav-justified" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#shell-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#shell-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#shell-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="shell-windows">
        <a href="https://www.youtube.com/watch?v=339AEqk9c-8">Video Tutorial</a>
        <ol>
          <li>Download the Git for Windows <a href="https://git-for-windows.github.io/">installer</a>.</li>
          <li>Run the installer and follow the steps below:
            <ol>
              {% comment %} Git 2.18.0 Setup {% endcomment %}
              <li>
                Click on "Next" four times (two times if you've previously
                installed Git).  You don't need to change anything
                in the Information, location, components, and start menu screens.
              </li>
              <li>
                <strong>
                  Select “Use the nano editor by default” and click on “Next”.
                </strong>
              </li>
              {% comment %} Adjusting your PATH environment {% endcomment %}
              <li>
                Keep "Use Git from the Windows Command Prompt" selected and click on "Next".
                If you forgot to do this programs that you need for the workshop will not work properly.
                If this happens rerun the installer and select the appropriate option.
              </li>
              {% comment %} Choosing the SSH executable {% endcomment %}
              <li>Click on "Next".</li>
              {% comment %} Configuring the line ending conversions {% endcomment %}
              <li>
                Keep "Checkout Windows-style, commit Unix-style line endings" selected and click on "Next".
              </li>
              {% comment %} Configuring the terminal emulator to use with Git Bash {% endcomment %}
              <li>
                <strong>
                  Select "Use Windows' default console window" and click on "Next".
                </strong>
              </li>
              {% comment %} Configuring experimental performance tweaks {% endcomment %}
              <li>Click on "Install".</li>
              {% comment %} Installing {% endcomment %}
              {% comment %} Completing the Git Setup Wizard {% endcomment %}
              <li>Click on "Finish".</li>
            </ol>
          </li>
          <li>
            If your "HOME" environment variable is not set (or you don't know what this is):
            <ol>
              <li>Open command prompt (Open Start Menu then type <code>cmd</code> and press [Enter])</li>
              <li>
                Type the following line into the command prompt window exactly as shown:
                <p><code>setx HOME "%USERPROFILE%"</code></p>
              </li>
              <li>Press [Enter], you should see <code>SUCCESS: Specified value was saved.</code></li>
              <li>Quit command prompt by typing <code>exit</code> then pressing [Enter]</li>
            </ol>
          </li>
        </ol>
        <p>This will provide you with both Git and Bash in the Git Bash program.</p>
      </article>
      <article role="tabpanel" class="tab-pane" id="shell-macos">
        <p>
          The default shell in all versions of macOS is Bash, so no
          need to install anything.  You access Bash from the Terminal
          (found in
          <code>/Applications/Utilities</code>).
          See the Git installation <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">video tutorial</a>
          for an example on how to open the Terminal.
          You may want to keep
          Terminal in your dock for this workshop.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane" id="shell-linux">
        <p>
          The default shell is usually Bash, but if your
          machine is set up differently you can run it by opening a
          terminal and typing <code>bash</code>.  There is no need to
          install anything.
        </p>
      </article>
    </div>
  </div>
</div> {% comment %} End of 'shell' section. {% endcomment %}



<div id="editor"> {% comment %} Start of 'editor' section. {% endcomment %}
  <h3>Text Editor</h3>

  <p>
    When you're writing code, it's nice to have a text editor that is
    optimized for writing code, with features like automatic
    color-coding of key words. The default text editor on macOS and
    Linux is usually set to Vim, which is not famous for being
    intuitive. If you accidentally find yourself stuck in it, hit
    the <kbd>Esc</kbd> key, followed by <kbd>:</kbd>+<kbd>Q</kbd>+<kbd>!</kbd> 
    (colon, lower-case 'q', exclamation mark), then hitting <kbd>Return</kbd> to 
    return to the shell.
  </p>

  <div>
    <ul class="nav nav-tabs nav-justified" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#editor-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#editor-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#editor-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="editor-windows">
        <p>
          nano is a basic editor and the default that instructors use in the workshop.
          It is installed along with Git.
        </p>
        <p>
          Others editors that you can use are
          <a href="https://notepad-plus-plus.org/">Notepad++</a> or
          <a href="https://www.sublimetext.com/">Sublime Text</a>.
          <strong>Be aware that you must
            add its installation directory to your system path.</strong>
          Please ask your instructor to help you do this.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="editor-macos">
        <p>
          nano is a basic editor and the default that instructors use in the workshop.
          See the Git installation <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">video tutorial</a>
          for an example on how to open nano.
          It should be pre-installed.
        </p>
        <p>
          Others editors that you can use are
          <a href="https://www.barebones.com/products/bbedit/">BBEdit</a> or
          <a href="https://www.sublimetext.com/">Sublime Text</a>.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="editor-macos">
        <p>
          nano is a basic editor and the default that instructors use in the workshop.
          It should be pre-installed.
        </p>
        <p>
          Others editors that you can use are
          <a href="https://wiki.gnome.org/Apps/Gedit">Gedit</a>,
          <a href="https://kate-editor.org/">Kate</a> or
          <a href="https://www.sublimetext.com/">Sublime Text</a>.
        </p>
      </article>
    </div>
  </div>
</div> {% comment %} End of 'editor' section. {% endcomment %}



<div id="r"> {% comment %} Start of 'R' section. {% endcomment %}
  <h3>R</h3>

  <p>
    <a href="https://www.r-project.org">R</a> is a programming language
    that is especially powerful for data exploration, visualization, and
    statistical analysis. To interact with R, we use
    <a href="https://www.rstudio.com/">RStudio</a>.
  </p>

  <div>
    <ul class="nav nav-tabs nav-justified" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#rstats-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#rstats-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#rstats-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="rstats-windows">
        <a href="https://www.youtube.com/watch?v=q0PjTAylwoU">Video Tutorial</a>
        <p>
          Install R by downloading and running
          <a href="https://cran.r-project.org/bin/windows/base/release.htm">this .exe file</a>
          from <a href="https://cran.r-project.org/index.html">CRAN</a>.
          Also, please install the
          <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
          Note that if you have separate user and admin accounts, you should run the 
          installers as administrator (right-click on .exe file and select "Run as 
          administrator" instead of double-clicking). Otherwise problems may occur later, 
          for example when installing R packages.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="rstats-macos">
        <a href="https://www.youtube.com/watch?v=5-ly3kyxwEg">Video Tutorial</a>
        <p>
          Install R by downloading and running
          <a href="https://cran.r-project.org/bin/macosx/R-latest.pkg">this .pkg file</a>
          from <a href="https://cran.r-project.org/index.html">CRAN</a>.
          Also, please install the
          <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="rstats-linux">
        <p>
          You can download the binary files for your distribution
          from <a href="https://cran.r-project.org/index.html">CRAN</a>. Or
          you can use your package manager (e.g. for Debian/Ubuntu
          run <code>sudo apt-get install r-base</code> and for Fedora run
          <code>sudo dnf install R</code>).  Also, please install the
          <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
        </p>
      </article>
    </div>
  </div>
</div> {% comment %} End of 'R' section. {% endcomment %}


<div id="vm">
  <h3>Virtual Machine</h3>

  <p>
    Some instructors prefer to have learners use a virtual machine (VM)
    rather than install software on their own computers.  If your
    instructors have chosen to do this, please:
  </p>
  <ol>
    <li>
      Install <a href="https://www.virtualbox.org/">VirtualBox</a>.
    </li>
    <li>
      Download our <a href="{{site.swc_vm}}">VM image</a>.
      <strong>Warning:</strong> this file is 1.7 GByte, so please
      download it <em>before</em> coming to your workshop.
    </li>
    <li>
      Load the VM into VirtualBox by selecting "Import Appliance" and
      loading the <code>.ova</code> file.
    </li>
  </ol>
</div>
