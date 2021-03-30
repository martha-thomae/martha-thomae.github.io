---
layout: default
title: projects
---
# Projects

1. [Guatemalan choirbooks digitization project](guatemala.html)
2. [Automatic scoring up of mensural voices & mensural notation editor](scoringup.html)
3. [Translation of annotated modern transcriptions of mensural pieces into their original (mensural) notation](cmn2mensural.html)
4. [Machine translation applied to OMR](machinetranslation.html)

These invited talks summarize the work on projects 1 to 3:

{% for item in site.data.talksSurvey %}
- {{ item.name }} [slides]({{ item.link }})
{% endfor %}

The most complete version of these presentations can be found [here](/assets/slides/Freiburg_Music_Research_Colloquium - compressed.pdf).
