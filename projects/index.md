---
layout: default
title: publications and talks
---
# Publications and Talks

My main projects involve retrieving the semantics of mensural music and present them in score layout (either by developing tools to achieve this task or using them to encode a new corpus). Most mensural pieces are written in separate parts rather than in score format. The separate-parts arrangement difficults the visualization of the vertial sonorities (one cannot visualize what notes are being sung at the same time) and relation between the voices. Most of my projects involve the conversion of this separate-parts layout of the original pieces into a score layout. This, implies dealing with the interpretation of the duration of the notes in mensural notation, which is an issue on its own (in triple meter, the duration of the mensural notes depends on the context—notes preceding/following). Therefore, retrieving the semantics of mensural notation is an integral part of presenting the mensural piece in score layout.

## [This set of slides](/assets/slides/PDF/Freiburg_Music_Research_Colloquium - compressed.pdf) present a survey of my work on different projects that have been working towards this goal.

## Related talks:
{% for item in site.data.talksSurvey %}
- {{ item.name }} {% if item.link != '/'%}[slides]({{ item.link }}){% endif %}
{% endfor %}


Another big topic I have been working on recently is about digitization, encoding, and analysis of chants.

---
---

**The following entries organize my publications and talks according to their topics, and these are separated into two main sections.**
1. The first section addresses the projects that involve **mensural notation** (**polyphonic music** from the Late Middle Ages and Renaissance).
2. The second section is about **monophonic music** and **neumes**. It addresses the topics of chant digitization, encoding, and analysis.

---
---

## <span style="color:cadetblue;">PROJECTS ON POLYPHONIC EARLY MUSIC AND MENSURAL NOTATION</span>

## <span style="color:Gray">TOPIC:</span> GUATEMALAN CHOIRBOOK DIGITIZATION AND ENCONDING

For more information about this project (including videos of the do-it-yourself book scanner) and the paper with the images in full color, see [Guatemalan Digitization Project](/projects/guatemala.html).

## Related talks
{% for item in site.data.talksGuate %}
- {{ item.name }} {% if item.link != '/'%}[slides]({{ item.link }}){% endif %}
{% endfor %}

Different slide presentations focus on different aspects of the project. Some talks were more focused towards archives and libraries, others towards technologies, others towards future work. [This set of slides](/) contains everything that has been presented on the 'Guatemalan Digitization' topic.

**Notes:**
- The **OMR process** was indeed conducted at McGill, but it was done with the *MuRET* (*Music Recognition, Encoding, and Transcription*) framework developed by David Rizo at the University of Alicante.
- The **scoring up** (or interpretation of mensural notation) was indeed done with the *Scoring-up Tool*, but through the *Measuring Polyphony Editor (MP Editor)*. The MP Editor is an online mensural notation editor that includes the scoring-up functionality and allows for editorial corrections. The MP Editor is a project lead by Professor Karen Desmond (Brandeis University), its lead developer is Juliette Regimbal (McGill University) and I am the developer of its scoring-up functionality. The editorial corrections were further facilitated by integrating *humlib's dissonance filter* into the MP Editor, showing all dissonance types present in the score and highlighting the ones that are considered "illegal dissonances" according to the Renaissance style. Humlib is a library for parsing Humdrum files developed by Craig Sapp, its dissonance filter was developed by Alex Morgan as part of the Josquin Research Project.

## Related publications
Thomae, Martha E., Julie E. Cumming, and Ichiro Fujinaga. “Counterpoint Error-Detection Tools for Optical Music Recognition of Renaissance Polyphonic Music.” In Proceedings of the 23rd International Society for Music Information Retrieval Conference. Bengaluru, India, 2022. [https://archives.ismir.net/ismir2022/paper/000060.pdf](https://archives.ismir.net/ismir2022/paper/000060.pdf). [**PDF**](/assets/papers/thomae_2022_ismir_counterpoint_publication.pdf)

Thomae, Martha E., Julie E. Cumming, and Ichiro Fujinaga. “Digitization of Choirbooks in Guatemala.” In Proceedings of the 9th International Conference on Digital Libraries for Musicologists, 19–26. Prague, Czech Republic: ACM, 2022. [https://doi.org/10.1145/3543882.3543885](https://doi.org/10.1145/3543882.3543885). [**PDF**](/assets/papers/thomae_2022_dlfm_digitization_publication.pdf)

Thomae, Martha E. “The Guatemalan Choirbooks: Facilitating Preservation, Performance, and Study of the Colonial Repertoire.” In Christian Sacred Music in the Americas, edited by Andrew Shenton and Joanna Smolko. New York, NY: Rowman & Littlefield, 2021. [**PDF (as published in B&W)**](/assets/papers/ThomaeChapter.pdf)

---

## <span style="color:Gray">TOPIC:</span> AUTOMATIC SCORING UP FOR MENSURAL NOTATION

Vocal polyphonic music from 1280 to 1600 is written in mensural notation and it is typically presented in a layout with separate parts.The Mensural Scoring-up Tool is a set of Python scripts designed to automatically transform the separate-parts representation of the music into a score by dealing with the context-dependent nature of the notation through the implementation of the principles of imperfection and alteration, outlined by Franco of Cologne (ca. 1280). This tool exhibits 97% accuracy in a corpus of fourteenth- and fifteenth-century pieces, including both black and white mensural notation.

## Related talks
{% for item in site.data.talksScup %}
- {{ item.name }} {% if item.link != '/'%}[slides]({{ item.link }}){% endif %}
{% endfor %}

## Related publications
Thomae, Martha E., Julie E. Cumming, and Ichiro Fujinaga. “The Mensural Scoring-Up Tool.” In Proceedings of the 6th International Workshop on Digital Libraries for Musicology, 9–19. National Library of the Netherlands, The Hague, NL: ACM, 2019. [https://doi.org/10.1145/3358664.3358668](https://doi.org/10.1145/3358664.3358668). [**PDF**](/assets/papers/thomae_2019_dlfm_mensural_publication.pdf)

---

## <span style="color:Gray">TOPIC:</span> MEASURING POLYPHONY EDITOR (MP EDITOR)

An online mensural notation editor. My contribution to this editor was the scoring-up functionality (see previous project). This implied converting my Python script into JavaScript, and introducing functionality to deal with older mensural repertoire (Ars antiqua) among other things.

## Related publications (and talks)
Desmond, Karen, Laurent Pugin, Juliette Regimbal, David Rizo, Craig Sapp, and Martha E. Thomae. “Encoding Polyphony from Medieval Manuscripts Notated in Mensural Notation.” In Proceedings of the Music Encoding Conference, edited by Stefan Münnich and David Rizo, 197–219. Alicante, Spain (online): Humanities Commons, 2021. [https://doi.org/10.17613/tf2j-x697](https://doi.org/10.17613/tf2j-x697). [**PDF**](/assets/papers/desmond_2021_mec_encodingpolyphony_publication.pdf)

Desmond, Karen, Andrew Hankinson, Laurent Pugin, Juliette Regimbal, Craig Sapp, and Martha E. Thomae. “Next Steps for Measuring Polyphony: A Prototype Editor for Encoding Mensural Music.” In Proceedings of the Music Encoding Conference, 121–24. Tufts University, Boston, MA: Humanities Commons, 2020. [http://dx.doi.org/10.17613/5k88-9z02](http://dx.doi.org/10.17613/5k88-9z02). [**PDF**](/assets/papers/desmond_2020_mec_nextsteps_poster.pdf)

---

## <span style="color:Gray">TOPIC:</span> CMN TO MENSURAL MEI TRANSLATOR

Translation of annotated modern transcriptions of mensural pieces back into their original notation.

## Related talks
{% for item in site.data.talksMensuraltrans %}
- {{ item.name }} {% if item.link != '/'%}[slides]({{ item.link }}){% endif %}
{% endfor %}

---

## <span style="color:Gray">TOPIC:</span> MACHINE TRANSLATION APPLIED TO OMR

Applied machine translation techniques to solve one of the central problems in the field of optical music recognition---extracting the semantics of a sequence of music characters---using the seq2seq model and the attention mechanism from machine translation to address this issue. This initial approach could provide a more generalizable solutions than the current approaches, which involve heuristics and grammars.

## Related publications (and talks)
Thomae, Martha E., Antonio Ríos-Vila, Jorge Calvo-Zaragoza, David Rizo, and José M. Iñesta. “Retrieving Music Semantics from Optical Music Recognition by Machine Translation.” In Proceedings of the Music Encoding Conference, 19–24. Tufts University, Boston, MA: Humanities Commons, 2020. [http://dx.doi.org/10.17613/605z-nt78](http://dx.doi.org/10.17613/605z-nt78). [**PDF**](/assets/papers/thomae_2020_mec_retrieving_publication.pdf)


## <span style="color:Gray">TOPIC:</span> Encoding Technologies

## Related talks
{% for item in site.data.talksEncodingTechs %}
- {{ item.name }} {% if item.link != '/'%}[slides]({{ item.link }}){% endif %}
{% endfor %}

---
---

# <span style="color:green;">PROJECTS ON CHANT, MONOPHONIC EARLY MUSIC, NEUMES, AND SQUARE NOTATION</span>

## <span style="color:Gray">TOPIC:</span> CHANT ENCODING AND ANALYSIS

Recently, during my postdoctoral research fellowship at Universidade NOVA de Lisboa, I have focused my work on chants. I have also joined the **[Digital Analysis of Chant Transmission (DACT)](https://dact-chant.ca)** group, where I collaborate with information about Spanish chantbooks in Guatemala for the **Cantorales Project** (since 2022). The Cantorales Project team works towards developing a catalogue of Spanish chantbooks outside of Spain.

## Related talks
{% for item in site.data.talksNeumes %}
- {{ item.name }} {% if item.link != '/'%}[slides]({{ item.link }}){% endif %}
{% endfor %}

---
