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

----------------
----------------

# The Corpus: The GCA-Gaha 1 Choirbook

This choirbook has a few sigla associated to it: 
- _**GuatC 1**_, according to the Census Catalogue.
- **_GCA-Gc 1_**, according to the Digital Image Archive of Medieval Music (DIAMM) — [Link to entry _GCA-Gc 1_ in DIAMM](https://www.diamm.ac.uk/sources/985/)
- **_GCA-Gaha 1_**, which would be its correct siglum given its current location at the _Archivo Histórico Arquidiocesano "Francisco de Paula García Peláez", Ciudad de Guatemala_ (_GCA-Gaha_, according to RISM) — [Link to entry _GCA-Gaha_ in RISM](https://rism.online/search?q=guatemala&mode=institutions&page=1&rows=40#institutions-30080989).

The choirbook is a Book of Masses. It contains twelve masses: six of them copied from another book (a _Libro de Kyries_ copied by Gaspar Fernandes in 1602), and the other six were added by Manuel José de Quirós in the eighteenth century. It also includes fifteen short pieces, which consists of polyphonic settings of chants (e.g., _Asperges me_ and _Vidi aquam_). 

The following two images show the title page, which indicate that this book was copied from a previous one copied by Gaspar Fernandes in 1602 and to which six new masses were added by Manuel Joseph de Quirós in 176[0], and the index page, which lists the twelve masses according to these two groups (the ones from the 1602 book and the one sadded later).

<img src="/assets/images/titlepage.jpg" alt="title page" width="400"/> <img src="/assets/images/indexpage.jpg" alt="index page" width="400"/>

---------------

# Virtual Exhibition & Inventory

In the next section, you will find the [inventory list](./guatemala.md#inventory-list) of all the pieces in the choirbook. This inventory includes links to mass movements (or work sections) that, when clicked on, will open the corresponding movement (or section) in _mei-friend_, where the user will be able to:

1. Visualize the transcription of the piece, with notes in green for editorial corrections;
2. Visualize the original images (we will call these _facsimile_ from now on);
3. Explore the piece thanks to the link that exists between the transcription, encoding, and facsimile. Just click on the border of the bounding boxes of the systems/staffs in the facsimile (so it is highlighted in blue), and you will be conducted to the first note/rest of that system in the transcription (which will now be highlighted in blue as well) and to its place in the encoded file (highlighted in orange). **You can see this in the following figure.**
4. Play back the music using the speaker button in the lower-left corner.

**Important note:** Please make sure that you are using Chrome or Firefox, _mei-friend_ does not work well with Safari.
<img src="/assets/images/mei-friend-example_Mass11.4.2.png" alt="pieces as visualized in mei-friend" width="1000">

**The transcriptions were fully revised by Ellis Reyes (PhD Candidate in Musicology, McGill University). He proofread the whole symbolic corpus, visualizing and listening to it using mei-friend, making any corrections necessary and adding the ficta.** The metadata of each file shows the names of the people (and software) involved in its creation, usually including the names of: Martha Eladia Thomae Elias (mine), Ellis Reyes (proofreader of the whole corpus and in charge of ficta accidentals), Geneviève Gates-Panneton (when involved), and ocasionally Julie E. Cumming and Peter Schubert (who acted as consultants in a few instances).

---------------

## Inventory List

Here is the **list inventoring** the contents of the GCA-Gaha 1 (the composer attribution was provided by Guatemalan Musicologist Omar Morales Abril). Click on the links to open the pieces in _mei-friend_, where you will have access to a kind of **"virtual exhibition"** showing the transcriptions, with editorial corrections in green; the original images; the link between the transcription, images, and encoding; and playback, just as explained in the previous paragraph. **Click on the links! Have a look!**

### 1. Asperges me - [Pedro Bermúdez?]
Added in the 18th century.
- [Asperges](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/01_Anonymous-OR-Bermudez_Asperges-me/Piece1_Asperges-me_Section1_f1v-2r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Miserere](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/01_Anonymous-OR-Bermudez_Asperges-me/Piece1_Asperges-me_Section2_f2v-3r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/01_Anonymous-OR-Bermudez_Asperges-me/Piece1_Asperges-me_Section3_f3v-4r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 2. Asperges me - Anonymous
Added in the 18th century.
- [Asperges](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/02_Anonymous_Asperges-me/Piece2_Asperges-me_Section1_f4v-6r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54) 
- [Miserere](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/02_Anonymous_Asperges-me/Piece2_Asperges-me_Section2_f5v-6r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/02_Anonymous_Asperges-me/Piece2_Asperges-me_Section3_f6v-7r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 3. Vidi aquam - Pedro Bermúdez
Added in the 18th century.
- [Vidi aquam](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/03_Pedro-Bermudez_Vidi-aquam/Piece3_Vidi-aquam_Section1_f7v-9r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Confitemini](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/03_Pedro-Bermudez_Vidi-aquam/Piece3_Vidi-aquam_Section2_f9v-10r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/03_Pedro-Bermudez_Vidi-aquam/Piece3_Vidi-aquam_Section3_f10v-11r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 4. Vidi aquam - [Hernando Franco]
Added in the 18th century.
- [Vidi aquam](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/04_Franco_Vidi-aquam/Piece4_Vidi-aquam_Section1_f11v-13r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Confitemini](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/04_Franco_Vidi-aquam/Piece4_Vidi-aquam_Section2_f12v-13r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/04_Franco_Vidi-aquam/Piece4_Vidi-aquam_Section3_f13v-14r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 5. Asperges me - [Alonso Trujillo]
Added in the 18th century.
- [Asperges](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/05_Trujillo_Asperges-me/Piece5_Vidi-aquam_Section1_f14v-15r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Miserere](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/05_Trujillo_Asperges-me/Piece5_Vidi-aquam_Section2_f15v-16r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/05_Trujillo_Asperges-me/Piece5_Vidi-aquam_Section3_f16v-17r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 6. Missa sobre las voces - Cristóbal de Morales
From the 1602 Libro de Kyries, copied by Gaspar Fernández. This is Morales's hexachord mass, which, according to Robert Snow (1996, p. 19), is preserved in only three other sources: a manuscript at the Capilla Real in Granada, the manuscript formerly known as _Medinaceli 607_ and now owned by Bartolomé March Servera, and _Tarazona 5_.
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/06_Cristobal-de-Morales_Mass/Missa6.1_Kyrie_FullMovement_f17v-19r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/06_Cristobal-de-Morales_Mass/Missa6.2_Gloria_FullMovement_f19v-22r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PARTb4b7b905-10db-4a01-8ada-d11f114bfca7_A95dbe38a-2001-4f53-b5f1-b46666d034f0&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/06_Cristobal-de-Morales_Mass/Missa6.3_Credo_FullMovement_f22v-27r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PARTbf0d1613-62d4-4683-b328-51112bed377d_Ace2b4880-73ac-4773-9432-f724ec7ca6fc&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/06_Cristobal-de-Morales_Mass/Missa6.4_Sanctus_FullMovement_f27v-30r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART78a5d400-4ff9-4d67-8010-90c3e14645b4_A6f08d835-3adc-4beb-867e-ef4737fdd0fe&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/06_Cristobal-de-Morales_Mass/Missa6.5_Agnus_FullMovement_f30v-31r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PARTfec4a0f0-f272-45e4-b85f-9ac2b52291cb_A92e169f8-5eac-4c36-8d7a-ab6feb4bb118&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 7. Missa sine nomine - Giovanni Pierluigi da Palestrina
From the 1602 Libro de Kyries, copied by Gaspar Fernández. This is the _Missa sine nomine_ first published in the compsoer's _Missarum liber secundus_ in 1567 (RIMS P 660), see Snow (1996, p.19).
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.1_Kyrie_FullMovement_f31v-33r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.2_Gloria_FullMovement_f33v-35r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.3_Credo_FullMovement_f35v-38r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.4_Sanctus_FullMovement_f38v-41r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus I](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.5_AgnusI_FullMovement_f41v-42r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus II](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/07_Giovanni-Pierluigi-da-Palestrina_Mass/Missa7.6_AgnusII_FullMovement_f42v-43r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 8. Missa Pere de nous - Pierre Colin
From the 1602 Libro de Kyries, copied by Gaspar Fernández. This is Colin's _Missa Pere de nous_, published at Lyon in 1546 by Jacques Moderne in his _Liturgicon musicarum duodecim missarum_ (RISM C 3310), see Snow (1996, p.19).
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/08_Pierre-Colin_Mass/Missa8.1_Kyrie_FullMovement_f43v-44r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/08_Pierre-Colin_Mass/Missa8.2_Gloria_FullMovement_f44v-47r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/08_Pierre-Colin_Mass/Missa8.3_Credo_FullMovement_f47v-52r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/08_Pierre-Colin_Mass/Missa8.4_Sanctus_FullMovement_f52v-53r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/08_Pierre-Colin_Mass/Missa8.5_Agnus_FullMovement_f53v-54r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 9. Missa de 3er tono - Rodrigo de Ceballos
From the 1602 Libro de Kyries, copied by Gaspar Fernández. This is Ceballos's popular _Missa tertii toni_, preserved in at least ten other sources (Snow 1996, p.19).
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/09_Rodrigo-de-Ceballos_Mass/Missa9.1_Kyrie_FullMovement_f54v-56r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/09_Rodrigo-de-Ceballos_Mass/Missa9.2_Gloria_FullMovement_f56v-60r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/09_Rodrigo-de-Ceballos_Mass/Missa9.3_Credo_FullMovement_f60v-66r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/09_Rodrigo-de-Ceballos_Mass/Missa9.4_Sanctus_FullMovement_f66v-68r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus I](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/09_Rodrigo-de-Ceballos_Mass/Missa9.5_Agnus_FullMovement_f68v-70r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus II](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/09_Rodrigo-de-Ceballos_Mass/Missa9.6_AgnusII_FullMovement_f70v-71r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 10. Missa sine nomine - José de Torres y Martínez Bravo
Added in the 18th century.
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/10_Jose-de-Torres-y-Martinez-Bravo_Mass/Missa10.1_Kyrie_FullMovement_f71v-73r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/10_Jose-de-Torres-y-Martinez-Bravo_Mass/Missa10.2_Gloria_FullMovement_f73v-76r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/10_Jose-de-Torres-y-Martinez-Bravo_Mass/Missa10.3_Credo_FullMovement_f76v-81r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/10_Jose-de-Torres-y-Martinez-Bravo_Mass/Missa10.4_Sanctus_FullMovement_f81v-83r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus I](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/10_Jose-de-Torres-y-Martinez-Bravo_Mass/Missa10.5_AgnusI_FullMovement_f83v-84r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus II](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/10_Jose-de-Torres-y-Martinez-Bravo_Mass/Missa10.6_AgnusII_FullMovement_f84v-85r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 11. Missa O quam gloriosum - Tomás Luis de Victoria
Added in the 18th century. Many concordant European sources.
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/11_Tomas-Luis-de-Victoria_Mass/Missa11.1_Kyrie_FullMovement_f85v-87r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/11_Tomas-Luis-de-Victoria_Mass/Missa11.2_Gloria_FullMovement_f87v-89r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/11_Tomas-Luis-de-Victoria_Mass/Missa11.3_Credo_FullMovement_f89v-92r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/11_Tomas-Luis-de-Victoria_Mass/Missa11.4_Sanctus_FullMovement_f92v-94r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/11_Tomas-Luis-de-Victoria_Mass/Missa11.5_Agnus_FullMovement_f94v-95r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 12. Missa Ave maris stella - Tomás Luis de Victoria
Added in the 18th century. Many concordant European sources.
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/12_Tomas-Luis-de-Victoria_Mass/Missa12.1_Kyrie_FullMovement_f95v-97r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/12_Tomas-Luis-de-Victoria_Mass/Missa12.2_Gloria_FullMovement_f97v-100r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/12_Tomas-Luis-de-Victoria_Mass/Missa12.3_Credo_FullMovement_f100v-105r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/12_Tomas-Luis-de-Victoria_Mass/Missa12.4_Sanctus_FullMovement_f105v-108r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/12_Tomas-Luis-de-Victoria_Mass/Missa12.5_Agnus_FullMovement_f108v-109r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 13. Missa de 5to tono - Luis Serra
Added in the 18th century.
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/13_Serra_Mass/Missa13.1_Kyrie_FullMovement_f109v-111r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/13_Serra_Mass/Missa13.2_Gloria_FullMovement_f111v-113r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/13_Serra_Mass/Missa13.3_Credo_FullMovement_f113v-117r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/13_Serra_Mass/Missa13.4_Sanctus_FullMovement_f117v-118r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/13_Serra_Mass/Missa13.5_Agnus_FullMovement_f118v-119r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 14. Missa de 4to tono - Alegre
Added in the 18th century.
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/14_Alegre_Mass/Missa14.1_Kyrie_FullMovement_f119v-121r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/14_Alegre_Mass/Missa14.2_Gloria_FullMovement_f121v-124r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/14_Alegre_Mass/Missa14.3_Credo_FullMovement_f124v-130r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/14_Alegre_Mass/Missa14.4_Sanctus_FullMovement_f130v-131r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus I](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/14_Alegre_Mass/Missa14.5_AgnusI_FullMovement_f131v-132r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus II](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/14_Alegre_Mass/Missa14.6_AgnusII_FullMovement_f132v-133r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 15. Missa de 8to tono - Rodrigo de Ceballos
From the 1602 Libro de Kyries, copied by Gaspar Fernández. This is Ceballos's _Missa Simile est regnum caelorum_, a parody mass based on a motet by Morales (Snow 1996, p.19).
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/15_Rodrigo-de-Ceballos_Mass/Missa15.1_Kyrie_FullMovement_f133v-135r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/15_Rodrigo-de-Ceballos_Mass/Missa15.2_Gloria_FullMovement_f135v-139r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/15_Rodrigo-de-Ceballos_Mass/Missa15.3_Credo_FullMovement_f139v-146r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/15_Rodrigo-de-Ceballos_Mass/Missa15.4_Sanctus_FullMovement_f146v-149r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus I](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/15_Rodrigo-de-Ceballos_Mass/Missa15.5_Agnus_FullMovement_f149v-150r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus II](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/15_Rodrigo-de-Ceballos_Mass/Missa15.6_AgnusII_FullMovement_f150v-152r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 16. Missa de Bomba - Pedro Bermúdez
From the 1602 Libro de Kyries, copied by Gaspar Fernández. Parody mass based on Mateo Felcha's (el Viejo) ensalada _la Bomba_.
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/16_Pedro-Bermudez_Mass/Missa16.1_Kyrie_FullMovement_f152v-154r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/16_Pedro-Bermudez_Mass/Missa16.2_Gloria_FullMovement_f154v-158r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/16_Pedro-Bermudez_Mass/Missa16.3_Credo_FullMovement_f158v-165r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/16_Pedro-Bermudez_Mass/Missa16.4_Sanctus_FullMovement_f165v-168r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/16_Pedro-Bermudez_Mass/Missa16.5_Agnus_FullMovement_f168v-169r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 17. Missa sine nomine - Juan Matías de Rivera
Added in the 18th century.
- [Kyrie](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/17_Juan-Matias-de-Rivera_Mass/Missa17.1_Kyrie_FullMovement_f169v-171r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Gloria](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/17_Juan-Matias-de-Rivera_Mass/Missa17.2_Gloria_FullMovement_f171v-173r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Credo](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/17_Juan-Matias-de-Rivera_Mass/Missa17.3_Credo_FullMovement_f173v-177r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Sanctus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/17_Juan-Matias-de-Rivera_Mass/Missa17.4_Sanctus_FullMovement_f177v-179r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Agnus](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/17_Juan-Matias-de-Rivera_Mass/Missa17.5_Agnus_FullMovement_f179v-180r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 18. Christus natus est - Pedro Bermúdez
Added in the 18th century.
- [Full Piece](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/18_Pedro-Bermudez_Christus-natus-est/Piece18_Christus-natus-est_FullPiece_f180v-181r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 19. Christus natus est - Pedro Bermúdez
Added in the 18th century.
- [Full Piece](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/19_Pedro-Bermudez_Christus-natus-est/Piece19_Christus-natus-est_FullPiece_f181v-183r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 20. Christus natus est - Anonymous
Added in the 18th century.
- [Full Piece](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/20_Anonymous_Christus-natus-est/Piece20_Christus-natus-est_FullPiece_f183v-184r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 21. Surrexit Dominus vere - Anonymous
Added in the 18th century.
- [Full Piece](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/21_Anonymous_Surrexit-Dominus-vere/Piece21_Surrexit-Dominus-vere_FullPiece_f184v-186r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 22. Lumen ad revelationem - Hernando Franco
Added in the 18th century.
- [Full Piece](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/22_Hernando-Franco_Lumen-ad-revelationem/Piece22_Lumen-ad-revelationem_FullPiece_f186v-187r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 23. Lumen ad revelationem - Pedro Bermúdez
Added in the 18th century.
- [Full piece](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/23_Pedro-Bermudez_Lumen-ad-revelationem/Piece23_Lumen-ad-revelationem_FullPiece_f187v-188r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 24. Lumen ad revelationem - Pedro Bermúdez
Added in the 18th century.
- [Full Piece](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/24_Pedro-Bermudez_Lumen-ad-revelationem/Piece24_Lumen-ad-revelationem_FullPiece_f188v-189r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 25. Surrexit Dominus vere - Anonymous
Added in the 18th century.
- [Full Piece](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/25_Anonymous_Surrexit-Dominus-vere/Piece25_Surrexit-Dominus-vere_FullPiece_f189v-190r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 26. Victimae paschali laudes - Francisco Guerrero
Added in the 18th century.
- [Pars 1a, a 4](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/26_Francisco-Guerrero_Victimae-paschali-laudes/Piece26_Victimae-paschali-laudes_1aPars-a4_f190v-191r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)
- [Pars 2a, a 5](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/26_Francisco-Guerrero_Victimae-paschali-laudes/Piece26_Victimae-paschali-laudes_2aPars-a5_f191v-192r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

### 27. Tantum ergo - [Pedro Bermúdez]
Added in the 18th century.
- [Full Piece](https://mei-friend.mdw.ac.at/?file=https://raw.githubusercontent.com/martha-thomae/GuatC1/refs/heads/main/27_Bermudez_Tantum-ergo/Piece27_Tantum-ergo_FullPiece_f192v-193r_MensuralScore-and-Facsimile.xml&scale=31&breaks=none&select=PART0906de42-7bc1-47c4-afe7-5f04e6bcfcd4_A414df90d-62e4-4ef5-bb1c-111946ffc5aa&page=1&speed=true&notationOrientation=left&notationProportion=0.32&facsimileOrientation=bottom&facsimileProportion=0.54)

---------------

The original files can be found at the [GuatC1 GitHub repository - main branch](https://github.com/martha-thomae/GuatC1/tree/main).

_(There is also a secondary branch to visualize all the intermediate files obtained through OMR and the MP Editor, called `all_data_omr_and_mped`, but it is linked through the main branch's README.)_

----------------
----------------

# Acknowledgements

## Guatemalan Institutions and Colleagues
I am very thankful to the many Guatemalan conservators, archivists, musicologists, photographers, and conservation and archival institutions that supported this project, especially during the digitization stage. I would not have been able to complete this initial phase of the project without the valuable support of:

The **Centro de Rescate, Estudios y Análisis Científico del Arte** (**CREA**), a non-profit institution dedicated to the conservation and restoration of historical and cultural movable heritage (i.e., sculptures, paintings, and paper). Its conservators evaluated the condition of the choirbooks, which helped determine the book selected for this pilot project, and provided conservation treatment prior to digitization. I also thank the **Fundación Rozas-Botrán**, which manages social development projects in health and culture in Central America and Panama and of which CREA is a part.
- **Lucy González Muñoz**, CREA's lead conservator, who enthusiastically took on the project, and the two Gabys, who carried out the conservation treatment of the book prior to digitization.
- **Thelma Castillo**, Art and Culture consultant at the Rozas-Botrán Foundation, who put me in contact with CREA.

The **Archivo Histórico Arquidiocesano de Guatemala** (**AHAG**), the archive holding these Cathedral choirbooks and which allowed me to conduct this pilot project.
- **Father Eddy René Calvillo**, Chancellor of the Ecclesiastical Curia of Santiago de Guatemala and Director of the AHAG, for approving the project.
- **Alejandro Conde**, archivist, for his advice and support throughout the process.

The **Centro de Investigaciones Regionales de Mesoamérica** (**CIRMA**), which holds microfilms of many of the AHAG's music holdings. Special thanks to:
- **Guisela Asensio Lueg**, CIRMA’s General Director, who provided me with the contact of the photographer hired for the project.
- **Thelma Porres Morfín**, Director of CIRMA’s Historical Archive, who showed me the microfilms and provided valuable background information.
- **María de los Ángeles Ávila de León**, Photo Library Assistant, who generously offered her help during the digitization process.

I extend my gratitude towards:
- **Omar Morales Abril**, musicologist, for his advice throughout the project and for providing the metadata (especially composer attributions) for the selected choirbook.
- **Daniel Hernández-Salazar** (artistic photographer), the professional photographer hired for this project. He assisted in setting up the camera and equipment during the first session and provided valuable guidance (e.g., including the verso number directly in the photograph using printed labels placed beside the color patch). As there was no digitization technician specialized in handling special collections, the manuscript handling and digitization were carried out by me under the guidance of several institutions listed below.
- **José German Thomae Villela** (father), for designing and constructing the book cradle according to the requirements provided.

## Digitization Part (External Institutions)

I also thank the experts who provided advice before and during the digitization process. I received support from specialists at three institutions working on digitization projects involving special collections, cultural heritage materials, and music manuscripts:

- The **McGill Library’s Digital Initiatives**.
  - **Gregory Houston**, McGill’s New Media & Digitization Administrator, for his recommendations as to where to obtain archival supplies (e.g., snake weights) and suggestions for future improvements to the book scanner.

- The **Bibliothèque et Archives nationales du Québec** (**BAnQ**). Special thanks to three BAnQ experts who received me on multiple occasions for consultation on conservation and digitization matters:
  - **Jessica Régimbald**, conservator at the _direction du dépôt légal et de la conservation des collections patrimoniales_, who advised me on safe manuscript handling, conservation treatments prior to digitization, and the use of platens.
  - **Marie-Chantal Anctil**, coordinator of the _section de la reproduction et des ateliers audiovisuels and direction de la numérisation_, who advised me on key considerations for building a do-it-yourself (DIY) book scanner.
  - **Michel Legendre**, photographer (_direction de la numérisation and section de la reproduction_), who advised me on lighting and approved the selected equipment.

  Anctil and Legendre also proposed the open-at-one-side cradle configuration (to solve the issue of keeping the page flat without a platen), which I ultimately adopted.

- The **Digital Image Archive of Medieval Music** (**DIAMM**). Special thanks to:
  - **Julia Craig-McFeely**, Project Manager.
  - **Lynda Sayce**, Lead Photographer.

  For their extensive email support throughout the project. Many aspects of the digitization process were based on their advice, including the use of a neutral background, the positioning of the color patch, and the decision not to use a platen.

  Finally, thanks to **Professor Eun Park** and **colleagues from the _Preservation Management_ course** (McGill). Through this course, I gained valuable knowledge and connected with professionals at BAnQ and McGill Library. I am also grateful to my classmates, for their advice and encouragement.

## MIR Part
- I am thankful to everyone involved in the development of _MuRET_, the software used for the _optical music recognition (OMR)_ component. Special thanks to:
  - **David Rizo**, lead developer of MuRET
  - **Jorge Calvo-Zaragoza** and **Antonio Ríos-Vila**, for the symbol recognition models
  - **Francisco (Paco) Castellanos**, for the document analysis model
  - **José Manuel Iñesta**, principal investigator of the HISPAMUS project
  
  I also thank to them for their collegial support and collaboration.

- Regarding the _scoring up_ stage carried out in the _Measuring Polyphony (MP) Editor_, I would like to thank:
  - **Karen Desmond** (PI), for supporting the interoperability between MuRET and the MP Editor
  - **Juliette Regimbal** (lead developer), for her help in implementing this interoperability.
  - **Craig Sapp**, for enabling the integration of the humlib dissonant filter
  - **Alex Morgan**, developer of the humlib dissonant filter
 
I also acknowledge the developers of _mei-friend_ (David Weigl and Werner Goebl), _Verovio_ (Laurent Pugin), and the _MEI Community_, without whom this work would not have been possible. Special thanks to Werner Goebl for resolving an issue with the facsimile view of mensural voices distributed across the book opening, and to Anna Plaksin for her work on editorial markup display.

## Editorial Correction and Final Corpus
- **Geneviève Gates-Panneton**, for experimenting with the dissonant filter in the MP Editor
- **Ellis Reyes**, for proofreading the transcriptions of the entire corpus and making editorial decisions regarding ficta.
- **Peter Schubert** and **Julie E. Cumming**, for their advice on problematic passages
	
## Supporters
Supervisors **Julie E. Cumming** and **Ichiro Fujinaga**, for their invaluable guidance, and the **Fonds de recherche du Québec – Société et culture (FRQSC), doctoral grant (2019-B2Z-261749)** for funding this project.

I also acknowledge the valuable contributions of: _Virginia Golcher_, _Ana Miriam López_, _Karla Lou_, _Anneliese Thomae_, _Emilio Rós Fábregas_, _Andrés Lou_, _Juan Pablo Pira Martínez_, and _Ana Patricia Elías López de Thomae_, who supported me in various ways, ranging from sharing knowledge on conservation and musicological research in Guatemala to assisting with filming the digitization process.
