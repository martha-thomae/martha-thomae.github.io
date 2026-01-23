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

Since we are dealing with mensural notation, however, recognizing the music symbols is not enough to retrieve all the rhythmic information of these symbols and line up the voices into a score. An extra step is needed, this is the **automatic scoring up and editorial correction step** (the last orange step in the diagram). This step is performed by the [**Measuring Polyphony (MP) Editor**](https://editor.measuringpolyphony.org/#/), which automatically scores up the piece (as it interprets mensural notation with a heuristic method I introduced in [The Mensural Scoring-Up Tool](/assets/papers/thomae_2019_dlfm_mensural_publication.pdf) paper) and allows for performing editorial corrections (corrections of scribal errors) that can solve alignment issues. The detection of scribal errors is facilitated by the MP Editor's barring and switch to modern clefs functionalities, and by highlighting of "illegal dissonances." This *marking of illegal dissonances* is conducted by the [**Dissonance Filter (DF)**](https://doc.verovio.humdrum.org/filter/dissonant) that is part of the [*humlib* library](https://humlib.humdrum.org). The DF is integrated into the MP Editor, it marks all the dissonances in the piece using the labels provided in [this table](https://doc.verovio.humdrum.org/filter/dissonant/#dissonant-function-labels). The ones that are considered "legal" (e.g., passing tones *P*/*p*, neighbour tones *N*/*n*, suspensions *S*/*s* and their agents *G*/*g*) are marked in blue font, while the ones considered "illegal" (e.g., unknown dissonances *z*, unknown dissonances in parallel accompaniment *L*/*l*, and dissonant note against known dissonance types *Y*/*y*).

The work that allows to use the output of MuRET as input to the MP Editor and the work that allows to use the DF Filter in the MP Editor is contained in the last two sections of [this paper](https://hcommons.org/deposits/item/hc:45973/). I conducted some testing of the efficiency of using the DF filter to help catching and correcting scribal errors in an automatically scored-up piece within the MP Editor, the experiment and results can be consulted in [this paper](/assets/papers/thomae_2022_ismir_counterpoint_publication.pdf) and summarized in this [poster](/assets/papers/poster-ismir_submission44.pdf) and [video](https://youtu.be/lQpYktuFFlc).


## Summary of the Complete Work

<figure>
	<iframe width="420" height="315" src="https://www.youtube.com/embed/aNpDpPOyOMY" frameborder="0" allowfullscreen></iframe>
	<figcaption style="font-size:15pt; font-style:italic">Summary of the digitization and encoding pipeline</figcaption>
</figure>



## Corpus

### 1. Asperges me (Anonymous or Pedro Bermúdez)
- Section 1
- Section 2
- Section 3

### 2. Asperges me (Anonymous)
- Section 1
- Section 2
- Section 3

### 3. Vidi aquam (Pedro Bermúdez)
- Section 1
- Section 2
- Section 3

### 4. Vidi aquam (Hernando Franco)
- Section 1
- Section 2
- Section 3

### 5. Asperges me (Trujillo)
- Section 1
- Section 2
- Section 3

### 6. Missa sobre las voces (Cristóbal de Morales)
His hexachord mass (Ut re mi fa sol la). Peserved in only three other sources: a manuscript at the Capilla Real in Granada, the manuscript formerly known as Medinaceli 607 and now owned by Bartolomé March Servera, and Tarazona 5.
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/06_Cristobal-de-Morales_Mass/Missa6.1_Kyrie_FullMovement_f17v-19r_MENSURAL_FULLSCORE.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/06_Cristobal-de-Morales_Mass/Missa6.2_Gloria_FullMovement_f19v-22r_MENSURAL_FULLSCORE.xml&scale=31&breaks=none&select=PARTb4b7b905-10db-4a01-8ada-d11f114bfca7_A95dbe38a-2001-4f53-b5f1-b46666d034f0&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/06_Cristobal-de-Morales_Mass/Missa6.3_Credo_FullMovement_f22v-27r_MENSURAL_FULSCORE.xml&scale=31&breaks=none&select=PARTbf0d1613-62d4-4683-b328-51112bed377d_Ace2b4880-73ac-4773-9432-f724ec7ca6fc&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/06_Cristobal-de-Morales_Mass/Missa6.4_Sanctus_FullMovement_f27v-30r_MENSURAL_FULLSCORE.xml&scale=31&breaks=none&select=PART78a5d400-4ff9-4d67-8010-90c3e14645b4_A6f08d835-3adc-4beb-867e-ef4737fdd0fe&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/06_Cristobal-de-Morales_Mass/Missa6.5_Agnus_FullMovement_f30v-31r_MENSURAL_FULLSCORE.xml&scale=31&breaks=none&select=PARTfec4a0f0-f272-45e4-b85f-9ac2b52291cb_A92e169f8-5eac-4c36-8d7a-ab6feb4bb118&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 7. Missa sine nomine (Palestrina)
First published in the composer's Missarum liber secundus in 1567 (RISM P 660)
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.1_Kyrie_FullMovement_f31v-33r_MENSURAL_FULLSCORE.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.2_Gloria_FullMovement_f33v-35r_MENSURAL_FULLSCORE.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.3_Credo_FullMovement_f35v-38r_MENSURAL_FULLSCORE.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.4_Sanctus_FullMovement_f38v-41r_MENSURAL_FULLSCORE.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus I](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.5_AgnusI_FullMovement_f41v-42r_MENSURAL_FULLSCORE.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- Agnus II

### 8. Missa Pere de nous (Pierre Colin)
Also published at Lyon in 1546 by Jacques Moderne in his Liturgicon musicarum duodecim missarum (RISM C 3310).
- Kyrie
- Gloria
- Credo
- Sanctus
- Agnus

### 9. Missa de 3er tono (Rodrigo de Ceballos)
Missa tertii toni, which is preserved in at least ten other sources.
- Kyrie
- Gloria
- Credo
- Sanctus
- Agnus I
- Agnus II

### 10. Missa sine nomine (José de Torres y Martínez Bravo)
- Kyrie
- Gloria
- Credo
- Sanctus
- Agnus I
- Agnus II

### 11. Missa O quam gloriosum (Tomás Luis de Victoria)
- Kyrie
- Gloria
- Credo
- Sanctus
- Agnus

### 12. Missa Ave maris stella (Tomás Luis de Victoria)
- Kyrie
- Gloria
- Credo
- Sanctus
- Agnus

### 13. Missa de 5to tono (Maestro Serra)
- Kyrie
- Gloria
- Credo
- Sanctus
- Agnus

### 14. Missa de 4to tono (Alegre)
- Kyrie
- Gloria
- Credo
- Sanctus
- Agnus I
- Agnus II

### 15. Missa de 8to tono (Rodrigo de Ceballos)
This is Ceballos' Missa Simile est regnum cælorum (parody mass based on a motet by Morales).
- Kyrie
- Gloria
- Credo
- Sanctus
- Agnus I
- Agnus II

### 16. Missa de Bomba (Pedro Bermúdez)
- Kyrie
- Gloria
- Credo
- Sanctus
- Agnus

### 17. Missa sine nomine (Juan Matias de Rivera)
- Kyrie
- Gloria
- Credo
- Sanctus
- Agnus

### 18. Christus natus est (Pedro Bermúdez)
- Piece

### 19. Christus natus est (Pedro Bermúdez)
- Section 1
- Section 2

### 20. Christus natus est (Anonymous)
- Piece

### 21. Surrexit Dominus vere (Anonymous)
- Section 1
- Section 2

### 22. Lumen ad revelationem (Hernando Franco)
- Piece

### 23. Lumen ad revelationem (Pedro Bermúdez)
- Piece

### 24. Lumen ad revelationem (Pedro Bermúdez)
- Piece

### 25. Surrexit Dominus vere (Anonymous)
- Piece

### 26. Victimae paschali laudes (Francisco Guerrero)
- Section 1 & 2
- Section 3

### 27. Tantum ergo (Pedro Bermúdez)
- Piece



## Extra information

- [Report on conditions for the input file of the MP Editor]()
- [Discussion and improvements to be made]()
