---
layout: default
title: Guatemalan digitization project
---

# Guatemalan Digitization Project

This a Music Information Retrieval (MIR) project involving three big steps, each related to a different type of technology. The goal of the project is to be able to retrieve digital scores with the voices properly lined-up from Renaissance polyphonic books. Renaissance polyphony is notated in: 
1. **Mensural notation.** This is an early music notation system where the duration of notes depends on the mensuration (meter), the note shape, and---when dealing with triple-meter pieces---the context (i.e., notes preceding or following).
2. **Separate parts.** The voices are contained in different areas of the book opening (e.g., choirbook format) or on completely different books (e.g., partbooks).

In this project, a mensural music source (Guatemala City's Metropolitan Cathedral polyphonic choirbook 1) is digitized, and then processed by different MIR technologies to convert the separate-parts layout of the voices into a score with the voices properly lined up---dealing with the intricacies of mensural notation regarding rhythmic interpretation, as well as correcting scribal errors.

The pipeline, and technologies behind the scene of each of the three steps are shown in the diagram below:

<img src="/assets/images/MIR_Pipeline.png" alt="Music information retrieval pipeline" width="1000">

The **first step** (shown in green in the diagram) is digitization, which---given the lack of suitable digitization options in Guatemala---was conducted with a **do-it-yourself (DIY) book scanner**. [<font size="5" color="green">Click here for details!</font>](digit_guatemala)

The **next two steps** are the **MIR steps**, which allow to *semiautomatically transcribe the images of mensural sources into symbolic scores* (as indicated by the orange steps in the diagdram). 

The first of these orange steps is the **optical music recognition (OMR) step**. This OMR step was conducted with [**MuRET**](https://muret.dlsi.ua.es/muret/#/home). Similar to OCR (optical **character** recognition) automatically recognizes the characters of digital text document, OMR (optical **music** recognition) automatically recognizes the music symbols in a digital music document. MuRET is an OMR framework that has support for the recognition of handwritten mensural notation (among other things), and it allows also to correct the results of this recognition process in case of errors.

Since we are dealing with mensural notation, however, recognizing the music symbols is not enough to retrieve all the rhythmic information of these symbols and line up the voices into a score. An extra step is needed, this is the **automatic scoring up and editorial correction step** (the last orange step in the diagram). This step is performed by the [**Measuring Polyphony (MP) Editor**](https://editor.measuringpolyphony.org/#/), which automatically scores up the piece (as it interprets mensural notation with a heuristic method I introduced in [The Mensural Scoring-Up Tool](https://dl.acm.org/doi/10.1145/3358664.3358668) paper) and allows for performing editorial corrections (corrections of scribal errors) that can solve alignment issues. The detection of scribal errors is facilitated by the MP Editor's barring and switch to modern clefs functionalities, and by highlighting of "illegal dissonances." This *marking of illegal dissonances* is conducted by the [**Dissonance Filter (DF)**](https://doc.verovio.humdrum.org/filter/dissonant) that is part of the [*humlib* library](https://humlib.humdrum.org). The DF is integrated into the MP Editor, it marks all the dissonances in the piece using the labels provided in [this table](https://doc.verovio.humdrum.org/filter/dissonant/#dissonant-function-labels). The ones that are considered "legal" (e.g., passing tones *P*/*p*, neighbour tones *N*/*n*, suspensions *S*/*s* and their agents *G*/*g*) are marked in blue font, while the ones considered "illegal" (e.g., unknown dissonances *z*, unknown dissonances in parallel accompaniment *L*/*l*, and dissonant note against known dissonance types *Y*/*y*).

The work that allows to use the output of MuRET as input to the MP Editor and the work that allows to use the DF Filter in the MP Editor is contained in the last two sections of [this paper](https://hcommons.org/deposits/item/hc:45973/). I conducted some testing of the efficiency of using the DF filter to help catching and correcting scribal errors in an automatically scored-up piece within the MP Editor, the experiment and results can be consulted in [this paper](https://archives.ismir.net/ismir2022/paper/000060.pdf) and summarized in this [poster]() and [video](https://youtu.be/lQpYktuFFlc).


## Summary of the Complete Work

<figure>
	<iframe width="420" height="315" src="https://www.youtube.com/embed/aNpDpPOyOMY" frameborder="0" allowfullscreen></iframe>
	<figcaption style="font-size:15pt; font-style:italic">Summary of the digitization and encoding pipeline</figcaption>
</figure>


## Extra information

- [Report on conditions for the input file of the MP Editor]()
- [Discussion and improvements to be made]()
