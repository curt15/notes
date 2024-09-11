Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[python 3rd party packages]]
Ref: [docs](https://docs.djangoproject.com/en/)
- [django-import-export](https://django-import-export.readthedocs.io/en/latest/installation.html)
- [django-tables2](https://django-tables2.readthedocs.io/en/latest/pages/installation.html)
- [django-filter](https://django-filter.readthedocs.io/en/stable/guide/install.html)
- [django-crispy-forms](https://django-crispy-forms.readthedocs.io/en/latest/install.html)

Django (web framework)

```pip install Django```

--- 

```
django-admin startproject projname
django-admin startapp appname
python manage.py # ...
```

--- 

fixtures 

https://docs.djangoproject.com/en/3.2/howto/initial-data/


--- 




I don't need any of the sites actually, rather, I need to dissect -> a single django mysite:

*tsite*
django-nested-admin
psycopg2

*mysite*
django-tinymce

*fitsite*
django-crispy-forms




django-admin startproject projname
python manage.py migrate
django-admin startapp appname





```py
from django.shortcuts import render

def about(request):
	return render(request, 'base/about.html')
```
~=
```py
from django.views.generic import TemplateView

urlpatterns = [
    path('', TemplateView.as_view(template_name='base/about.html')),
]
```

[[dj snippits]]


--- 
[[ django recieve webhooks]]

### asgi.py
```
"""
ASGI config for tutorial project.

It exposes the ASGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/3.1/howto/deployment/asgi/
"""

import os

from django.core.asgi import get_asgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'tutorial.settings')

application = get_asgi_application()
```


### wsgi.py
```
"""
WSGI config for tutorial project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/3.1/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'tutorial.settings')

application = get_wsgi_application()

```

### admin.py
```
from django.contrib import admin

# Register your models here.

```

### apps.py
```
from django.apps import AppConfig


class SnippetsConfig(AppConfig):
    name = 'snippets'

```

### models.py
```
from django.db import models
from pygments.lexers import get_all_lexers
from pygments.styles import get_all_styles

LEXERS = [item for item in get_all_lexers() if item[1]]
LANGUAGE_CHOICES = sorted([(item[1][0], item[0]) for item in LEXERS])
STYLE_CHOICES = sorted([(item, item) for item in get_all_styles()])


class Snippet(models.Model):
    created = models.DateTimeField(auto_now_add=True)
    title = models.CharField(max_length=100, blank=True, default='')
    code = models.TextField()
    linenos = models.BooleanField(default=False)
    language = models.CharField(choices=LANGUAGE_CHOICES, default='python', max_length=100)
    style = models.CharField(choices=STYLE_CHOICES, default='friendly', max_length=100)

    class Meta:
        ordering = ['created']
```

### views.py
```
from django.shortcuts import render

# Create your views here.

```

### urls.py
```
"""tutorial URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/3.1/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path

urlpatterns = [
    path('admin/', admin.site.urls),
]

```
### tests.py
```
from django.test import TestCase

# Create your tests here.

```

### serializers.py
```
from rest_framework import serializers
from snippets.models import Snippet, LANGUAGE_CHOICES, STYLE_CHOICES


class SnippetSerializer(serializers.Serializer):
    id = serializers.IntegerField(read_only=True)
    title = serializers.CharField(required=False, allow_blank=True, max_length=100)
    code = serializers.CharField(style={'base_template': 'textarea.html'})
    linenos = serializers.BooleanField(required=False)
    language = serializers.ChoiceField(choices=LANGUAGE_CHOICES, default='python')
    style = serializers.ChoiceField(choices=STYLE_CHOICES, default='friendly')

    def create(self, validated_data):
        """
        Create and return a new `Snippet` instance, given the validated data.
        """
        return Snippet.objects.create(**validated_data)

    def update(self, instance, validated_data):
        """
        Update and return an existing `Snippet` instance, given the validated data.
        """
        instance.title = validated_data.get('title', instance.title)
        instance.code = validated_data.get('code', instance.code)
        instance.linenos = validated_data.get('linenos', instance.linenos)
        instance.language = validated_data.get('language', instance.language)
        instance.style = validated_data.get('style', instance.style)
        instance.save()
        return instance
```

### settings.py
```
"""
Django settings for tutorial project.

Generated by 'django-admin startproject' using Django 3.1.1.

For more information on this file, see
https://docs.djangoproject.com/en/3.1/topics/settings/

For the full list of settings and their values, see
https://docs.djangoproject.com/en/3.1/ref/settings/
"""

from pathlib import Path

# Build paths inside the project like this: BASE_DIR / 'subdir'.
BASE_DIR = Path(__file__).resolve().parent.parent


# Quick-start development settings - unsuitable for production
# See https://docs.djangoproject.com/en/3.1/howto/deployment/checklist/

# SECURITY WARNING: keep the secret key used in production secret!
SECRET_KEY = 'dd$4ovv6pc94&(s7_@qkgs-a7$)&+&%!2v_gjtl!3^(rp1h$ds'

# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = True

ALLOWED_HOSTS = []


# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'rest_framework',
    'snippets.apps.SnippetsConfig',
]

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'tutorial.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

WSGI_APPLICATION = 'tutorial.wsgi.application'


# Database
# https://docs.djangoproject.com/en/3.1/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}


# Password validation
# https://docs.djangoproject.com/en/3.1/ref/settings/#auth-password-validators

AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]


# Internationalization
# https://docs.djangoproject.com/en/3.1/topics/i18n/

LANGUAGE_CODE = 'en-us'

TIME_ZONE = 'UTC'

USE_I18N = True

USE_L10N = True

USE_TZ = True


# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/3.1/howto/static-files/

STATIC_URL = '/static/'

```

### manage.py
```
#!/usr/bin/env python
"""Django's command-line utility for administrative tasks."""
import os
import sys


def main():
    """Run administrative tasks."""
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'tutorial.settings')
    try:
        from django.core.management import execute_from_command_line
    except ImportError as exc:
        raise ImportError(
            "Couldn't import Django. Are you sure it's installed and "
            "available on your PYTHONPATH environment variable? Did you "
            "forget to activate a virtual environment?"
        ) from exc
    execute_from_command_line(sys.argv)


if __name__ == '__main__':
    main()

```


#### ../migrations/0001_initial.py
```
# Generated by Django 3.1.1 on 2020-09-07 22:03

from django.db import migrations, models


class Migration(migrations.Migration):

    initial = True

    dependencies = [
    ]

    operations = [
        migrations.CreateModel(
            name='Snippet',
            fields=[
                ('id', models.AutoField(auto_created=True, primary_key=True, serialize=False, verbose_name='ID')),
                ('created', models.DateTimeField(auto_now_add=True)),
                ('title', models.CharField(blank=True, default='', max_length=100)),
                ('code', models.TextField()),
                ('linenos', models.BooleanField(default=False)),
                ('language', models.CharField(choices=[('abap', 'ABAP'), ('abnf', 'ABNF'), ('ada', 'Ada'), ('adl', 'ADL'), ('agda', 'Agda'), ('aheui', 'Aheui'), ('ahk', 'autohotkey'), ('alloy', 'Alloy'), ('ampl', 'Ampl'), ('antlr', 'ANTLR'), ('antlr-as', 'ANTLR With ActionScript Target'), ('antlr-cpp', 'ANTLR With CPP Target'), ('antlr-csharp', 'ANTLR With C# Target'), ('antlr-java', 'ANTLR With Java Target'), ('antlr-objc', 'ANTLR With ObjectiveC Target'), ('antlr-perl', 'ANTLR With Perl Target'), ('antlr-python', 'ANTLR With Python Target'), ('antlr-ruby', 'ANTLR With Ruby Target'), ('apacheconf', 'ApacheConf'), ('apl', 'APL'), ('applescript', 'AppleScript'), ('arduino', 'Arduino'), ('as', 'ActionScript'), ('as3', 'ActionScript 3'), ('aspectj', 'AspectJ'), ('aspx-cs', 'aspx-cs'), ('aspx-vb', 'aspx-vb'), ('asy', 'Asymptote'), ('at', 'AmbientTalk'), ('augeas', 'Augeas'), ('autoit', 'AutoIt'), ('awk', 'Awk'), ('basemake', 'Base Makefile'), ('bash', 'Bash'), ('bat', 'Batchfile'), ('bbcbasic', 'BBC Basic'), ('bbcode', 'BBCode'), ('bc', 'BC'), ('befunge', 'Befunge'), ('bib', 'BibTeX'), ('blitzbasic', 'BlitzBasic'), ('blitzmax', 'BlitzMax'), ('bnf', 'BNF'), ('boa', 'Boa'), ('boo', 'Boo'), ('boogie', 'Boogie'), ('brainfuck', 'Brainfuck'), ('bst', 'BST'), ('bugs', 'BUGS'), ('c', 'C'), ('c-objdump', 'c-objdump'), ('ca65', 'ca65 assembler'), ('cadl', 'cADL'), ('camkes', 'CAmkES'), ('capdl', 'CapDL'), ('capnp', "Cap'n Proto"), ('cbmbas', 'CBM BASIC V2'), ('ceylon', 'Ceylon'), ('cfc', 'Coldfusion CFC'), ('cfengine3', 'CFEngine3'), ('cfm', 'Coldfusion HTML'), ('cfs', 'cfstatement'), ('chai', 'ChaiScript'), ('chapel', 'Chapel'), ('charmci', 'Charmci'), ('cheetah', 'Cheetah'), ('cirru', 'Cirru'), ('clay', 'Clay'), ('clean', 'Clean'), ('clojure', 'Clojure'), ('clojurescript', 'ClojureScript'), ('cmake', 'CMake'), ('cobol', 'COBOL'), ('cobolfree', 'COBOLFree'), ('coffee-script', 'CoffeeScript'), ('common-lisp', 'Common Lisp'), ('componentpascal', 'Component Pascal'), ('console', 'Bash Session'), ('control', 'Debian Control file'), ('coq', 'Coq'), ('cpp', 'C++'), ('cpp-objdump', 'cpp-objdump'), ('cpsa', 'CPSA'), ('cr', 'Crystal'), ('crmsh', 'Crmsh'), ('croc', 'Croc'), ('cryptol', 'Cryptol'), ('csharp', 'C#'), ('csound', 'Csound Orchestra'), ('csound-document', 'Csound Document'), ('csound-score', 'Csound Score'), ('css', 'CSS'), ('css+django', 'CSS+Django/Jinja'), ('css+erb', 'CSS+Ruby'), ('css+genshitext', 'CSS+Genshi Text'), ('css+lasso', 'CSS+Lasso'), ('css+mako', 'CSS+Mako'), ('css+mozpreproc', 'CSS+mozpreproc'), ('css+myghty', 'CSS+Myghty'), ('css+php', 'CSS+PHP'), ('css+smarty', 'CSS+Smarty'), ('cucumber', 'Gherkin'), ('cuda', 'CUDA'), ('cypher', 'Cypher'), ('cython', 'Cython'), ('d', 'D'), ('d-objdump', 'd-objdump'), ('dart', 'Dart'), ('dasm16', 'DASM16'), ('delphi', 'Delphi'), ('dg', 'dg'), ('diff', 'Diff'), ('django', 'Django/Jinja'), ('docker', 'Docker'), ('doscon', 'MSDOS Session'), ('dpatch', 'Darcs Patch'), ('dtd', 'DTD'), ('duel', 'Duel'), ('dylan', 'Dylan'), ('dylan-console', 'Dylan session'), ('dylan-lid', 'DylanLID'), ('earl-grey', 'Earl Grey'), ('easytrieve', 'Easytrieve'), ('ebnf', 'EBNF'), ('ec', 'eC'), ('ecl', 'ECL'), ('eiffel', 'Eiffel'), ('elixir', 'Elixir'), ('elm', 'Elm'), ('emacs', 'EmacsLisp'), ('email', 'E-mail'), ('erb', 'ERB'), ('erl', 'Erlang erl session'), ('erlang', 'Erlang'), ('evoque', 'Evoque'), ('extempore', 'xtlang'), ('ezhil', 'Ezhil'), ('factor', 'Factor'), ('fan', 'Fantom'), ('fancy', 'Fancy'), ('felix', 'Felix'), ('fennel', 'Fennel'), ('fish', 'Fish'), ('flatline', 'Flatline'), ('floscript', 'FloScript'), ('forth', 'Forth'), ('fortran', 'Fortran'), ('fortranfixed', 'FortranFixed'), ('foxpro', 'FoxPro'), ('freefem', 'Freefem'), ('fsharp', 'F#'), ('gap', 'GAP'), ('gas', 'GAS'), ('genshi', 'Genshi'), ('genshitext', 'Genshi Text'), ('glsl', 'GLSL'), ('gnuplot', 'Gnuplot'), ('go', 'Go'), ('golo', 'Golo'), ('gooddata-cl', 'GoodData-CL'), ('gosu', 'Gosu'), ('groff', 'Groff'), ('groovy', 'Groovy'), ('gst', 'Gosu Template'), ('haml', 'Haml'), ('handlebars', 'Handlebars'), ('haskell', 'Haskell'), ('haxeml', 'Hxml'), ('hexdump', 'Hexdump'), ('hlsl', 'HLSL'), ('hsail', 'HSAIL'), ('hspec', 'Hspec'), ('html', 'HTML'), ('html+cheetah', 'HTML+Cheetah'), ('html+django', 'HTML+Django/Jinja'), ('html+evoque', 'HTML+Evoque'), ('html+genshi', 'HTML+Genshi'), ('html+handlebars', 'HTML+Handlebars'), ('html+lasso', 'HTML+Lasso'), ('html+mako', 'HTML+Mako'), ('html+myghty', 'HTML+Myghty'), ('html+ng2', 'HTML + Angular2'), ('html+php', 'HTML+PHP'), ('html+smarty', 'HTML+Smarty'), ('html+twig', 'HTML+Twig'), ('html+velocity', 'HTML+Velocity'), ('http', 'HTTP'), ('hx', 'Haxe'), ('hybris', 'Hybris'), ('hylang', 'Hy'), ('i6t', 'Inform 6 template'), ('icon', 'Icon'), ('idl', 'IDL'), ('idris', 'Idris'), ('iex', 'Elixir iex session'), ('igor', 'Igor'), ('inform6', 'Inform 6'), ('inform7', 'Inform 7'), ('ini', 'INI'), ('io', 'Io'), ('ioke', 'Ioke'), ('irc', 'IRC logs'), ('isabelle', 'Isabelle'), ('j', 'J'), ('jags', 'JAGS'), ('jasmin', 'Jasmin'), ('java', 'Java'), ('javascript+mozpreproc', 'Javascript+mozpreproc'), ('jcl', 'JCL'), ('jlcon', 'Julia console'), ('js', 'JavaScript'), ('js+cheetah', 'JavaScript+Cheetah'), ('js+django', 'JavaScript+Django/Jinja'), ('js+erb', 'JavaScript+Ruby'), ('js+genshitext', 'JavaScript+Genshi Text'), ('js+lasso', 'JavaScript+Lasso'), ('js+mako', 'JavaScript+Mako'), ('js+myghty', 'JavaScript+Myghty'), ('js+php', 'JavaScript+PHP'), ('js+smarty', 'JavaScript+Smarty'), ('jsgf', 'JSGF'), ('json', 'JSON'), ('json-object', 'JSONBareObject'), ('jsonld', 'JSON-LD'), ('jsp', 'Java Server Page'), ('julia', 'Julia'), ('juttle', 'Juttle'), ('kal', 'Kal'), ('kconfig', 'Kconfig'), ('kmsg', 'Kernel log'), ('koka', 'Koka'), ('kotlin', 'Kotlin'), ('lagda', 'Literate Agda'), ('lasso', 'Lasso'), ('lcry', 'Literate Cryptol'), ('lean', 'Lean'), ('less', 'LessCss'), ('lhs', 'Literate Haskell'), ('lidr', 'Literate Idris'), ('lighty', 'Lighttpd configuration file'), ('limbo', 'Limbo'), ('liquid', 'liquid'), ('live-script', 'LiveScript'), ('llvm', 'LLVM'), ('llvm-mir', 'LLVM-MIR'), ('llvm-mir-body', 'LLVM-MIR Body'), ('logos', 'Logos'), ('logtalk', 'Logtalk'), ('lsl', 'LSL'), ('lua', 'Lua'), ('make', 'Makefile'), ('mako', 'Mako'), ('maql', 'MAQL'), ('mask', 'Mask'), ('mason', 'Mason'), ('mathematica', 'Mathematica'), ('matlab', 'Matlab'), ('matlabsession', 'Matlab session'), ('md', 'markdown'), ('mime', 'MIME'), ('minid', 'MiniD'), ('modelica', 'Modelica'), ('modula2', 'Modula-2'), ('monkey', 'Monkey'), ('monte', 'Monte'), ('moocode', 'MOOCode'), ('moon', 'MoonScript'), ('mosel', 'Mosel'), ('mozhashpreproc', 'mozhashpreproc'), ('mozpercentpreproc', 'mozpercentpreproc'), ('mql', 'MQL'), ('ms', 'MiniScript'), ('mscgen', 'Mscgen'), ('mupad', 'MuPAD'), ('mxml', 'MXML'), ('myghty', 'Myghty'), ('mysql', 'MySQL'), ('nasm', 'NASM'), ('ncl', 'NCL'), ('nemerle', 'Nemerle'), ('nesc', 'nesC'), ('newlisp', 'NewLisp'), ('newspeak', 'Newspeak'), ('ng2', 'Angular2'), ('nginx', 'Nginx configuration file'), ('nim', 'Nimrod'), ('nit', 'Nit'), ('nixos', 'Nix'), ('notmuch', 'Notmuch'), ('nsis', 'NSIS'), ('numpy', 'NumPy'), ('nusmv', 'NuSMV'), ('objdump', 'objdump'), ('objdump-nasm', 'objdump-nasm'), ('objective-c', 'Objective-C'), ('objective-c++', 'Objective-C++'), ('objective-j', 'Objective-J'), ('ocaml', 'OCaml'), ('octave', 'Octave'), ('odin', 'ODIN'), ('ooc', 'Ooc'), ('opa', 'Opa'), ('openedge', 'OpenEdge ABL'), ('pacmanconf', 'PacmanConf'), ('pan', 'Pan'), ('parasail', 'ParaSail'), ('pawn', 'Pawn'), ('peg', 'PEG'), ('perl', 'Perl'), ('perl6', 'Perl6'), ('php', 'PHP'), ('pig', 'Pig'), ('pike', 'Pike'), ('pkgconfig', 'PkgConfig'), ('plpgsql', 'PL/pgSQL'), ('pony', 'Pony'), ('postgresql', 'PostgreSQL SQL dialect'), ('postscript', 'PostScript'), ('pot', 'Gettext Catalog'), ('pov', 'POVRay'), ('powershell', 'PowerShell'), ('praat', 'Praat'), ('prolog', 'Prolog'), ('properties', 'Properties'), ('protobuf', 'Protocol Buffer'), ('ps1con', 'PowerShell Session'), ('psql', 'PostgreSQL console (psql)'), ('pug', 'Pug'), ('puppet', 'Puppet'), ('py2tb', 'Python 2.x Traceback'), ('pycon', 'Python console session'), ('pypylog', 'PyPy Log'), ('pytb', 'Python Traceback'), ('python', 'Python'), ('python2', 'Python 2.x'), ('qbasic', 'QBasic'), ('qml', 'QML'), ('qvto', 'QVTO'), ('racket', 'Racket'), ('ragel', 'Ragel'), ('ragel-c', 'Ragel in C Host'), ('ragel-cpp', 'Ragel in CPP Host'), ('ragel-d', 'Ragel in D Host'), ('ragel-em', 'Embedded Ragel'), ('ragel-java', 'Ragel in Java Host'), ('ragel-objc', 'Ragel in Objective C Host'), ('ragel-ruby', 'Ragel in Ruby Host'), ('raw', 'Raw token data'), ('rb', 'Ruby'), ('rbcon', 'Ruby irb session'), ('rconsole', 'RConsole'), ('rd', 'Rd'), ('reason', 'ReasonML'), ('rebol', 'REBOL'), ('red', 'Red'), ('redcode', 'Redcode'), ('registry', 'reg'), ('resource', 'ResourceBundle'), ('rexx', 'Rexx'), ('rhtml', 'RHTML'), ('ride', 'Ride'), ('rnc', 'Relax-NG Compact'), ('roboconf-graph', 'Roboconf Graph'), ('roboconf-instances', 'Roboconf Instances'), ('robotframework', 'RobotFramework'), ('rql', 'RQL'), ('rsl', 'RSL'), ('rst', 'reStructuredText'), ('rts', 'TrafficScript'), ('rust', 'Rust'), ('sarl', 'SARL'), ('sas', 'SAS'), ('sass', 'Sass'), ('sc', 'SuperCollider'), ('scala', 'Scala'), ('scaml', 'Scaml'), ('scdoc', 'scdoc'), ('scheme', 'Scheme'), ('scilab', 'Scilab'), ('scss', 'SCSS'), ('sgf', 'SmartGameFormat'), ('shen', 'Shen'), ('shexc', 'ShExC'), ('sieve', 'Sieve'), ('silver', 'Silver'), ('slash', 'Slash'), ('slim', 'Slim'), ('slurm', 'Slurm'), ('smali', 'Smali'), ('smalltalk', 'Smalltalk'), ('smarty', 'Smarty'), ('sml', 'Standard ML'), ('snobol', 'Snobol'), ('snowball', 'Snowball'), ('solidity', 'Solidity'), ('sourceslist', 'Debian Sourcelist'), ('sp', 'SourcePawn'), ('sparql', 'SPARQL'), ('spec', 'RPMSpec'), ('splus', 'S'), ('sql', 'SQL'), ('sqlite3', 'sqlite3con'), ('squidconf', 'SquidConf'), ('ssp', 'Scalate Server Page'), ('stan', 'Stan'), ('stata', 'Stata'), ('swift', 'Swift'), ('swig', 'SWIG'), ('systemverilog', 'systemverilog'), ('tads3', 'TADS 3'), ('tap', 'TAP'), ('tasm', 'TASM'), ('tcl', 'Tcl'), ('tcsh', 'Tcsh'), ('tcshcon', 'Tcsh Session'), ('tea', 'Tea'), ('termcap', 'Termcap'), ('terminfo', 'Terminfo'), ('terraform', 'Terraform'), ('tex', 'TeX'), ('text', 'Text only'), ('thrift', 'Thrift'), ('todotxt', 'Todotxt'), ('toml', 'TOML'), ('trac-wiki', 'MoinMoin/Trac Wiki markup'), ('treetop', 'Treetop'), ('ts', 'TypeScript'), ('tsql', 'Transact-SQL'), ('ttl', 'Tera Term macro'), ('turtle', 'Turtle'), ('twig', 'Twig'), ('typoscript', 'TypoScript'), ('typoscriptcssdata', 'TypoScriptCssData'), ('typoscripthtmldata', 'TypoScriptHtmlData'), ('ucode', 'ucode'), ('unicon', 'Unicon'), ('urbiscript', 'UrbiScript'), ('usd', 'USD'), ('vala', 'Vala'), ('vb.net', 'VB.net'), ('vbscript', 'VBScript'), ('vcl', 'VCL'), ('vclsnippets', 'VCLSnippets'), ('vctreestatus', 'VCTreeStatus'), ('velocity', 'Velocity'), ('verilog', 'verilog'), ('vgl', 'VGL'), ('vhdl', 'vhdl'), ('vim', 'VimL'), ('wdiff', 'WDiff'), ('webidl', 'Web IDL'), ('whiley', 'Whiley'), ('x10', 'X10'), ('xml', 'XML'), ('xml+cheetah', 'XML+Cheetah'), ('xml+django', 'XML+Django/Jinja'), ('xml+erb', 'XML+Ruby'), ('xml+evoque', 'XML+Evoque'), ('xml+lasso', 'XML+Lasso'), ('xml+mako', 'XML+Mako'), ('xml+myghty', 'XML+Myghty'), ('xml+php', 'XML+PHP'), ('xml+smarty', 'XML+Smarty'), ('xml+velocity', 'XML+Velocity'), ('xorg.conf', 'Xorg'), ('xquery', 'XQuery'), ('xslt', 'XSLT'), ('xtend', 'Xtend'), ('xul+mozpreproc', 'XUL+mozpreproc'), ('yaml', 'YAML'), ('yaml+jinja', 'YAML+Jinja'), ('zeek', 'Zeek'), ('zephir', 'Zephir'), ('zig', 'Zig')], default='python', max_length=100)),
                ('style', models.CharField(choices=[('abap', 'abap'), ('algol', 'algol'), ('algol_nu', 'algol_nu'), ('arduino', 'arduino'), ('autumn', 'autumn'), ('borland', 'borland'), ('bw', 'bw'), ('colorful', 'colorful'), ('default', 'default'), ('emacs', 'emacs'), ('friendly', 'friendly'), ('fruity', 'fruity'), ('igor', 'igor'), ('inkpot', 'inkpot'), ('lovelace', 'lovelace'), ('manni', 'manni'), ('monokai', 'monokai'), ('murphy', 'murphy'), ('native', 'native'), ('paraiso-dark', 'paraiso-dark'), ('paraiso-light', 'paraiso-light'), ('pastie', 'pastie'), ('perldoc', 'perldoc'), ('rainbow_dash', 'rainbow_dash'), ('rrt', 'rrt'), ('sas', 'sas'), ('solarized-dark', 'solarized-dark'), ('solarized-light', 'solarized-light'), ('stata', 'stata'), ('stata-dark', 'stata-dark'), ('stata-light', 'stata-light'), ('tango', 'tango'), ('trac', 'trac'), ('vim', 'vim'), ('vs', 'vs'), ('xcode', 'xcode')], default='friendly', max_length=100)),
            ],
            options={
                'ordering': ['created'],
            },
        ),
    ]

```
**URL = Uniform Resource Locator**
- a Django URL configuration matches a unique URL with a project resource
    by matching a Python path using dot notation:
        ```
		package.module.class.method
        package.module.function.attribute
		```

** Django's urls package provides dozens of functions and classes for working with different URL formats, name resolution, exception handling, and other navigational utilities, but at its MOST basic:

    it allows you to map a URL to a function or class within your
    Django project:

       - App1 <= path('app1', app1.views.some_view())

       - App2

- a URL doesn't have to match to a view - e.g. a custom module sensors.py has a function or class that records sensor data to your database (wireless environment sensors --> post sensor data) all without touching a view...

____
### MVC?
Django = MVT = “model, view, template”
https://djangobook.com/mdj2-django-structure/ 

**view**
- describes the data that gets presented to the user aka which data you see.
- is the python callback function for a particular URL in the view, because that callback describes which data is presented.

-> delegates to a…

**template** - describes how you see it. 

**“controller”** - the framework itself: the machinery that sends a request to the appropriate view, according to the Django URL configuration.


DJANGO TEMPLATE  [client side]

__________________________________


                 [server side]

--------------------------------

            |                      |

    App Logic               VIEW Logic

            |                      |

                MODEL(s)

                        |           [django framework]

--------------------------------

                        |

                 database


                    

____
**Why PostgreSQL?**
- reccomended by Django book
- python can be used as a procedural language
- JSON support w/out NoSQL
-  Data type changes of a column w/out rewriting the table
-  geographical data w/ GeoDjangos



```
###################
# modeling custom fields
###################
from django.db.models import CharField

DAY_OF_THE_WEEK = {
	1 : 'Sunday',
	2 : 'Monday',
	3 : 'Tuesday',
	4 : 'Wednesday',
	5 : 'Thursday',
	6 : 'Friday',
	7 : 'Saturday'
}

class DayOfTheWeekField(models.CharField):
	def __init__(self, *args, **kwargs):
		kwargs['choices']=tuple(sorted(DAY_OF_THE_WEEK.items()))
		kwargs['max_length']=1
		super(DayOfTheWeekField, self).__init__(*args, **kwargs)





#####################
# example resolution order
######################

class Destination(models.Model):
    city_name=models.CharField()

class Trip(models.Model):
    departing_on=models.DateField()
    returning_on=models.DateField()
    destinations=models.ManyToManyField(Destination)

class Activity(models.Model):
    destination=models.ForeignKey(Destination, null=False)
    trip=models.ForeignKey(Trip, null=False)



class Destination(models.Model):
    city_name=models.CharField(max_length=50)

class Trip(models.Model):
    departing_on=models.DateField()
    returning_on=models.DateField()
    destinations=models.ManyToManyField(Destination, through='Visit')

class Visit(models.Model):
    destination=models.ForeignKey(Destination)
    trip=models.ForeignKey(Trip)

class Activity(models.Model):
    name=models.CharField(max_length=50)
    visit=models.ForeignKey(Visit)

    
	# Trip 1
    #     Destination 1
    #     Destination 2
    #     	Activity 1
    # Trip 2
    #     Destination 1
    #     Activity 2

```





--- 
References:
- [Advanced tutorial: How to write reusable apps](https://docs.djangoproject.com/en/3.1/intro/reusable-apps)

- [Classy Class-Based Views](https://ccbv.co.uk)

- HTML URL Encoding Reference [w3schools](https://www.w3schools.com/tags/ref_urlencode.asp?_sm_au_=iVVDMg0TSmrMV6Dm)

- [django-allauth](https://django-allauth.readthedocs.io/en/latest)
- [django-tables2](https://django-tables2.readthedocs.io/en/latest/pages/installation.html)
- 