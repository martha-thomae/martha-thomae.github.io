---
layout: default
title: workshops
---
# Workshops

## Optical Music Recognition (OMR) workshops:
{% for item in site.data.workshopsOMR %}
- <p>{{ item.name }} {% if item.link != '/'%}[slides]({{ item.link }}){% endif %}</p>
{% endfor %}

## Music Encoding workshops/lectures:
The purpose of the following workshops were to teach musicologists (professionals and students) to use the _Music Encoding Initiative (MEI)_ format to encode early music pieces, in particular, pieces notated in mensural notation (used for vocal polyphonic compositions during the Late Middle Ages and the Renaissance).

{% for item in site.data.workshopsMEI %}
- {{ item.name }} {% if item.link != '/'%}[slides]({{ item.link }}){% endif %}
{% endfor %}

[This set of slides](/assets/slides/MEI General and MEI for Mensural Notation - compressed.pdf) summarizes what was presented during these workshops. It covers the very basics of the encoding MEI (Music Encoding Initiative) format and then it moves into the use of MEI for encoding mensural notation in particular.
