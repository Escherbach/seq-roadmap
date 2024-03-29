<head>
<style>
  .csl-right-inline a {
    word-break: break-all;
  }
  figure {
    text-align: center;
  }
  figure img {
    display: block;
    margin: auto;
    max-width: 600px;
  }
  figcaption {
    display: inline-block;
    text-align: center;
    width: 100%;
  }
  
  caption {
  caption-side: bottom; /* Places caption at the bottom of the table */
  text-align: center;
  margin-top: 10px;
}

sup {
  vertical-align: super;
  font-size: smaller;
}

  
  /* General Text Properties */
  body {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 16px;
    line-height: 1.5;
    max-width: 800px;
    margin: auto;
    padding: 20px;
  }

  /* Headings */
  h1, h2, h3 {
    font-weight: 700;
  }
  /* Custom Title Style */
.title-large {
  font-size: 40px;  /* Set size larger than typical H1 */
  font-weight: bold;
  text-align: left;  /* Changed from center to left */
  border-bottom: 1px solid #000;
}
  body {
  background-color: #ffffff;  /* White */
}

table th {
  border-bottom: 1px solid #000;  /* 2px thick, black line */
}

h1 {
  border-bottom: 1px solid #000;  /* 2px thick, black line */
}

/* Initialize counter */
body {
  counter-reset: figure-counter;
}

/* Increment counter and display it */
figure {
  counter-increment: figure-counter;
}

  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</style>
</head>
<div class="title-large">Towards ubiquitous metagenomic sequencing: a technology roadmap</div>
<p>
<b>
    Nava Whiteford<sup>1</sup>, 
    Andrew Heron<sup>2</sup>, 
    Leonard McCline<sup>3</sup>, 
    Ales Flidr<sup>3</sup>, 
    Jacob Swett<sup>4</sup>, 
    Ajay Karpur<sup>5</sup>
</b>
</p>
<!-- Affiliations -->
<p>
<sup>1</sup> Whiteford Research<br/>
<sup>2</sup> Independent<br/>
<sup>3</sup> Convergent Research<br/>
<sup>4</sup> Blueprint Biosecurity<br/>
<sup>5</sup> Open Philanthropy
</p>
<p>Project was funded by <a href="https://www.openphilanthropy.org">Open Philanthropy</a> and managed by <a href="https://www.convergentresearch.org">Convergent Research.</a></p>
<p><a href="roadmap.pdf">PDF Version</a></p>
<p>Cite as: Whiteford, N., Heron, A., McCline, L., Flidr, A., Swett, J., & Karpur, A. (2024, February 6). Towards Ubiquitous Metagenomic Sequencing: A Technology Roadmap. https://doi.org/10.17605/OSF.IO/8JU9M</p>
<h1 class="unnumbered" id="abstract">Abstract</h1>
<p>Metagenomic sequencing (MGS) has shown promise for infectious disease diagnostics and pandemic preparedness but has not yet reached widespread clinical adoption due to limitations such as high costs and complex workflows. This technology roadmap proposes target specifications for a MGS diagnostic device to enable routine use: sensitivity comparable to polymerase chain reaction, time-to-answer under 1 hour, cost per test under $10, and a portable, affordable instrument. We estimate that throughput of 1-10 million reads per hour with modest read lengths &gt;25 base pairs and accuracy &gt;95% could robustly detect most pathogens in human respiratory samples. Existing sequencing platforms do not meet this combination of targets, so focused technology development is needed. Nanopore and single-molecule optical sequencing are highlighted as promising approaches if optimized for the proposed specifications rather than long reads and maximum accuracy. Realizing ubiquitous MGS may require push and pull incentives for innovation. A low-cost, rapid MGS diagnostic appears technically feasible and could greatly enhance pandemic preparedness.</p>
<h1 class="unnumbered" id="introduction">Introduction</h1>
<p>The COVID-19 pandemic has revealed the limitations of our ability to
identify emerging pathogens. SARS-CoV-2 circulated in human populations
as an unknown pneumonia, undetected by standard-of-care diagnostics, for
an estimated 4-8 weeks <span class="citation" data-cites="Pekar2021"><a href="#ref-Pekar2021">[1]</a></span> before a novel coronavirus was
identified in infected samples by unbiased <span data-acronym-form="singular+short" data-acronym-label="MGS">MGS</span>
<span class="citation" data-cites="Zhu2020"><a href="#ref-Zhu2020">[2]</a></span>. This delay lost
valuable time for addressing the pandemic, which has resulted in
millions of deaths and trillions of dollars in economic costs <span class="citation" data-cites="glennerster2023calculating"><a href="#ref-glennerster2023calculating">[3]</a></span>.</p>
<p>Imagine if, instead, every clinician and patient around the world had
access to a simple device capable of detecting any virus, bacterium or
other pathogen causing disease in a symptomatic patient. Such a world
would be much better positioned to diagnose and treat infectious disease
and to detect novel emerging pathogens before they cause a devastating
pandemic.</p>
<p>MGS has demonstrated the potential to become such a near-universal
diagnostic <span class="citation" data-cites="Chiu2019 schlaberg_viral_2017 Zinter2019 Charalampous2019">[4-7]</span>
and is already saving lives by informing clinical decisions for a
variety of symptoms and sample types <span class="citation" data-cites="edgeworth2023respiratory"><a href="#ref-edgeworth2023respiratory">[8]</a></span>. However, it is not yet
ready for prime time: complex workflows and high costs prevent
widespread adoption <span class="citation" data-cites="Chiu2019"><a href="#ref-Chiu2019">[4]</a></span>. As a result, MGS has had a limited
impact on the management of the pandemic at the point of care.
Therefore, regardless of their value for public health, sequencing-based
assays have to become comparable with the standard of care to be
considered a viable alternative.</p>
<p>While isothermal amplification methods and other new modalities
gained in use during COVID-19, assays based on the <span data-acronym-form="singular+short" data-acronym-label="qPCR">qPCR</span>
were by far the most widely used molecular diagnostic. Currently, qPCR
is considered the gold standard for the detection of respiratory
pathogens, offering high sensitivity, specificity, and a rapid
turnaround time <span class="citation" data-cites="WHO2011"><a href="#ref-WHO2011">[9]</a></span>.
In this paper, we use qPCR as a benchmark and outline the specifications
for a clinical MGS device for viral respiratory infection diagnostics.
Having outlined these specifications, we discuss the most promising
candidate technologies that may meet these requirements.</p>
<h1 class="unnumbered" id="motivation-pandemic-early-detection">Motivation: pandemic early
detection</h1>
<p><span class="marginnote"><figure>
<img src="images/threatnet_architecture.jpeg"/>
<figcaption>Proposed architecture of a network of MGS early detection
sites in emergency departments. Source: Sharma et al. 2023 <span class="citation" data-cites="sharma2023threat"><a href="#ref-sharma2023threat">[10]</a></span>, with
permission from the authors.</figcaption>
</figure></span></p>
<p>MGS can be leveraged for early detection in a number of ways,
including sequencing sites searching for emerging pathogens in
wastewater and waterways <span class="citation" data-cites="Consortium2021"><a href="#ref-Consortium2021">[11]</a></span>, or strategic testing of
"sentinel" populations. While these approaches should certainly form an
important part of a layered early detection system, we focus this
roadmap report solely on the vision of MGS deployed widely at the point
of care for detection of pathogens in human respiratory samples. The key
reasons for this focus are:</p>
<ul>
<li><p>Distinguishing between signal and noise is likely to be easier in
human respiratory samples than in environmental ones.</p></li>
<li><p>Early detection of pathogens will only be enabled when MGS is
deployed at a relatively large scale <span class="citation" data-cites="sharma2023threat"><a href="#ref-sharma2023threat">[10]</a></span>. If MGS proves to be
clinically useful and cost-effective, it can scale up naturally within
the current health-economic system <span class="citation" data-cites="Topol2023"><a href="#ref-Topol2023">[12]</a></span>, without the need for continued
public or philanthropic support above those of current
diagnostics.</p></li>
<li><p>Detecting a pathogen of concern in an individual sample
immediately enables effective quarantining and contact tracing.</p></li>
<li><p>Widely available MGS testing would put humanity in a position
where mass testing of a novel pathogen is possible from "day zero" of a
potential pandemic, saving the months it would take to develop and
approve novel primers for PCR tests.</p></li>
</ul>
<p>With the ongoing COVID-19 pandemic, we have seen that sequencing has
had a limited impact relative to its huge potential: while it has aided
initial sequence identification and variant tracking, a number of
bottlenecks prevent its widespread adoption directly at the point of
care. In this report, we analyze these bottlenecks and ask what it would
take to make the technology for MGS truly ubiquitous, fit for developed
and low-income countries alike in a 10-year time frame.</p>
<h1 class="unnumbered" id="current-practice-and-near-term-potential">Current practice and
near-term potential</h1>
<h2 class="unnumbered" id="pcr-as-a-benchmark">PCR as a benchmark</h2>
<p>What is it going to take to make MGS ubiquitous in clinics around the
world? A necessary condition is the existence of an affordable,
easy-to-use technical solution.</p>
<p>A natural success story to draw on is that of point-of-care
polymerase chain reactions (PCR) machines. Initially, these devices were
bulky, expensive, and limited to specialized laboratories, requiring
hours to produce results. Over time, they have been transformed into
affordable, user-friendly devices that can quickly deliver results with
the "push of a button", eliminating the need for specialized personnel.
According to a WHO report <span class="citation" data-cites="WHO2011"><a href="#ref-WHO2011">[9]</a></span>, real-time PCR devices have led to wider
adoption of molecular diagnostics due to their improved rapidity,
sensitivity, reproducibility and the reduced risk of carry-over
contamination. With the exception of sensitivity, all of these problems
currently still plague MGS.</p>
<p><span class="marginnote"><figure>
<img src="images/cepheid.jpeg"/>
<figcaption>A Cepheid GeneXpert device. Source: MSF (2022) <span class="citation" data-cites="msf2022access"><a href="#ref-msf2022access">[13]</a></span>.</figcaption>
</figure></span></p>
<p>A concrete example of this success is the Cepheid GeneXpert <span class="citation" data-cites="GeneXpertSystem"><a href="#ref-GeneXpertSystem">[14]</a></span> device.
Originally developed for the detection of anthrax, it has been adapted
to many other infectious diseases following collaboration between
Cepheid and international organizations and philanthropic bodies.
Through successive rounds of cost-optimization, the device arrived at a
point where it became practical even in developing countries for testing
infections such as tuberculosis or HIV. This resulted in an overall
installed base of some 22,000 devices even prior to the COVID
pandemic <span class="citation" data-cites="CepheidNewsReleaseArchive"><a href="#ref-CepheidNewsReleaseArchive">[15]</a></span>, which increased to
40,000 between 2019 and 2022 <span class="citation" data-cites="GenomeWeb2022"><a href="#ref-GenomeWeb2022">[16]</a></span>. This enabled relatively rapid
development of primers for testing the presence of SARS-CoV-2 in
clinical samples without the need for developing novel
infrastructure.</p>
<p>PCR devices can also test for multiple pathogens or genes (such as
those conferring antimicrobial resistance) in parallel. The BioFire
FilmArray <span class="citation" data-cites="BioFireDiagnostics2016"><a href="#ref-BioFireDiagnostics2016">[17]</a></span>, for instance, offers
simultaneous sensitive detection of 20-40 targets in samples including
respiratory (sputum, bronchoalveolar lavage), blood culture,
cerebrospinal fluid or gastrointestinal.</p>
<p>However, PCR cannot in principle detect unknown or changing targets.
For example, a novel gene conferring drug resistance, or a novel virus
strain, require the design of novel primers. Perhaps more importantly,
the emergence of a completely novel pathogen (in recent decades,
consider, SARS-CoV-1 and 2, HIV, Ebola and Marburg virus, for instance)
would go completely undetected.</p>
<p>In principle, then, MGS has a clear advantage, as it can detect any
pathogen, whether bacterial, viral, fungal or otherwise. Despite this
advantage, however, it is difficult to imagine that MGS might become
truly ubiquitous without being close to matching PCR on the set of
characteristics that made it successful.</p>
<p>In particular, we believe that MGS-based diagnostics should aspire to
meet these <strong>requirements</strong>:</p>
<ul>
<li><p><strong>Sensitivity comparable to qPCR</strong> (ideally matching
a Ct of 35).</p></li>
<li><p><strong>Workflow should be “push-button”</strong>, requiring
minimal operator time and skill (<span class="math inline">&lt;</span>5
minutes).</p></li>
<li><p><strong>Time to answer</strong> should be <strong>less than 1
hour</strong>.</p></li>
<li><p>The <strong>cost</strong> of a single test (COGS) should be
<strong>comparable to qPCR</strong> ($10).</p></li>
<li><p>The <strong>device itself should be affordable</strong> (ideally
<span class="math inline">&lt;</span> $10,000) and compact, ideally
portable.</p></li>
<li><p><strong>Supply chains</strong> should not be overly
complex.</p></li>
</ul>
<h2 class="unnumbered" id="current-sequencing-landscape">Current
sequencing landscape</h2>
<p>As <a href="#table1">Table 1</a>
(supplementary note) illustrates, no sequencing device currently comes
close to meeting these specifications. Sensitivity itself is already
achievable with sufficient sequencing depth (see <a href="#sec:requirements">section on platform requirements</a>), but
incompatible with the other requirements of cost and time-to-answer.
Workflows involve complex sequential steps in both sample and library
preparation and typically require hours of work by trained experts.
Automated and integrated solutions such as VolTRAX for nanopore
sequencing <span class="citation" data-cites="voltrax"><a href="#ref-voltrax">[31]</a></span> or
NeoPrep for Illumina <span class="citation" data-cites="neoprep"><a href="#ref-neoprep">[32]</a></span> are only available at high costs for
specialized laboratories. Cost per sample can be reduced below $10 only
by sequencing many samples in parallel, which is not practical in the
point-of-care context, as this step introduces a significant delay in
time-to-answer.</p>
<div class="table*">
<table id="table1">
<caption><b>Table 1:</b> Comparison of sequencing platforms</caption>
<thead>
<tr class="header">
<th style="text-align: left;">Platform</th>
<th style="text-align: left;">Method</th>
<th style="text-align: left;">Fastest lib. prep</th>
<th style="text-align: left;">Fastest run time</th>
<th style="text-align: left;">RNA?</th>
<th style="text-align: left;">COGS</th>
<th style="text-align: left;">Ref</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">Illumina NovaSeq 6000</td>
<td style="text-align: left;">SBS</td>
<td style="text-align: left;">1.5 hr</td>
<td style="text-align: left;">13 hr</td>
<td style="text-align: left;">No</td>
<td style="text-align: left;">$50</td>
<td style="text-align: left;"><span class="citation" data-cites="novaSeq6000"><a href="#ref-novaSeq6000">[18]</a></span></td>
</tr>
<tr class="even">
<td style="text-align: left;">Illumina MiSeq</td>
<td style="text-align: left;">SBS</td>
<td style="text-align: left;">1.5 hr</td>
<td style="text-align: left;">1.5 hr</td>
<td style="text-align: left;">No</td>
<td style="text-align: left;">$30</td>
<td style="text-align: left;"><span class="citation" data-cites="miseqSpecs"><a href="#ref-miseqSpecs">[19]</a></span></td>
</tr>
<tr class="odd">
<td style="text-align: left;">Illumina iSeq</td>
<td style="text-align: left;">SBS</td>
<td style="text-align: left;">1.5 hr</td>
<td style="text-align: left;">2 hr</td>
<td style="text-align: left;">No</td>
<td style="text-align: left;">$50</td>
<td style="text-align: left;"><span class="citation" data-cites="iseq100"><a href="#ref-iseq100">[20]</a></span></td>
</tr>
<tr class="even">
<td style="text-align: left;">Ion Torrent GeneStudio S5</td>
<td style="text-align: left;">Ion Semi. SBS</td>
<td style="text-align: left;">2 hr</td>
<td style="text-align: left;">10 min</td>
<td style="text-align: left;">No</td>
<td style="text-align: left;">$50</td>
<td style="text-align: left;"><span class="citation" data-cites="ionGeneStudio ion520Chip quail2012 heger2015">[21]–[24]</span></td>
</tr>
<tr class="odd">
<td style="text-align: left;">ONT MinION</td>
<td style="text-align: left;">SM Nanopore</td>
<td style="text-align: left;">10 min</td>
<td style="text-align: left;">&lt;1 hr</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: left;">$250</td>
<td style="text-align: left;"><span class="citation" data-cites="nanoporeKits greninger2015 tyson2020 nanoporeUpdate2023">[25]–[28]</span></td>
</tr>
<tr class="even">
<td style="text-align: left;">SeqLL (Helicos)</td>
<td style="text-align: left;">SMO SBS</td>
<td style="text-align: left;">0 min</td>
<td style="text-align: left;">7 d</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: left;">$50</td>
<td style="text-align: left;"><span class="citation" data-cites="seqll2017brochure"><a href="#ref-seqll2017brochure">[29]</a></span></td>
</tr>
<tr class="odd">
<td style="text-align: left;">Pacific Biosciences Sequel II</td>
<td style="text-align: left;">SMO SBS</td>
<td style="text-align: left;">3 hr</td>
<td style="text-align: left;">&lt;1 hr</td>
<td style="text-align: left;">No</td>
<td style="text-align: left;">$50</td>
<td style="text-align: left;"><span class="citation" data-cites="sequelSystems"><a href="#ref-sequelSystems">[30]</a></span></td>
</tr>
</tbody>
</table>
</div>
<p>The need for rapid results speaks against the majority of sequencing
platforms based on <strong>colony-based approaches</strong>. The cluster
generation step alone takes at least 60 minutes <span class="citation" data-cites="whiteford2023cluster"><a href="#ref-whiteford2023cluster">[33]</a></span>. In addition, this
approach requires a large set of reagents that would add significant
complexity and cost to the design of a sample-to-answer system.</p>
<p>Although the emergence of new companies (e.g. MGI <span class="citation" data-cites="MGITech2023"><a href="#ref-MGITech2023">[34]</a></span>, Singular Genomics
<span class="citation" data-cites="SingularGenomics2023"><a href="#ref-SingularGenomics2023">[35]</a></span>) is
likely to decrease consumable and device costs by driving down margins
and enabling innovations, the new players are unlikely to change this
fundamental limitation. To our knowledge, the most serious attempt at
decreasing the time requirements is the use of Lighting Terminators
<span class="citation" data-cites="GenomeWeb2009"><a href="#ref-GenomeWeb2009">[36]</a></span>.</p>
<p>While this and other future innovations could make some colony-based
approaches viable, a more natural category to focus on is that of
<strong>single-molecule approaches</strong>. Single-molecule approaches
have the advantage of potentially minimal library preparation and
compatibility with a real-time readout, with results delivered in
minutes following sample and library preparation. The two main
approaches in this category as of 2023 are nanopore sequencing and
single-molecule optical (SMO) sequencing.</p>
<p>As of 2023, the cheapest available instrument for runs on single
samples is <span data-acronym-form="singular+short" data-acronym-label="ONT">ONT</span>’s Flongle, whose
consumables sell for $90 <span class="citation" data-cites="flongle"><a href="#ref-flongle">[37]</a></span> and likely costs around $50 to make
<span class="citation" data-cites="Whiteford2022notes_on_nanopores"><a href="#ref-Whiteford2022notes_on_nanopores">[38]</a></span>. Optimized
clinical workflows utilizing real-time sequencing with <span data-acronym-form="singular+short" data-acronym-label="ONT">ONT</span>’s
MinION can achieve a time-to-answer of 6 hours <span class="citation" data-cites="Charalampous2019"><a href="#ref-Charalampous2019">[7]</a></span>. This is driven primarily by
sample and library preparation, as sequencing itself takes less than 1
hour. Even workflows optimized for the ICU setting require a clinical
microbiology laboratory to execute.</p>
<p>In the rest of this report, we ask what requirements a sequencing
device has to meet in order to match all of the above criteria. In
particular, we ask:</p>
<ul>
<li><p>How could the <a href="#sec:sample-to-answer">sample and library
preparation</a> workflows be automated to meet the cost and
time-to-answer requirements?</p></li>
<li><p>How does clinical <a href="#sec:requirements">sensitivity</a>
translate into sequencing device specifications?</p></li>
<li><p>What does this imply for <a href="#sec:dev-goals">sequencing
technology development goals</a> and what steps might be necessary to <a href="#sec:accelerating">direct and accelerate this
development</a>?</p></li>
</ul>
<h2 class="unnumbered" id="sec:sample-to-answer">Towards a
sample-to-answer system</h2>
<p>Perhaps the greatest contrast between sequencing and PCR tests today
lies in the complexity of workflows. As previously mentioned, even
workflows optimized for the ICU setting require a clinical microbiology
laboratory to execute <span class="citation" data-cites="edgeworth2023respiratory"><a href="#ref-edgeworth2023respiratory">[8]</a></span>. Interviews with
practitioners at the forefront of clinical MGS adoption reveal that
training new personnel in MGS workflows takes months and results vary
significantly based on operator skill.</p>
<p>In contrast, PCR assays are straightforward. To obtain a clinical
answer with the previously mentioned Cepheid GeneXpert, the user places
the sample into a cartridge, inserts it into the device, and waits for
approximately 45 minutes to obtain the result. This simplicity is
currently unattainable in the sequencing world, where the standard
procedure includes complex sample and library preparation workflows.
Given the ease of use and efficacy of Cepheid’s sample-to-answer RT-PCR
platform, it is valuable to explore whether similar principles could be
applied to sequencing technologies. Can we envision a device akin to
Cepheid’s, but centered around sequencing instead of qPCR? This would
potentially offer streamlined, rapid sequencing workflows, which could
dramatically accelerate the field.</p>
<p>Cepheid’s first and second generation instruments were incapable of
processing raw samples directly. To establish a comprehensive
sample-to-answer system, Cepheid tackled this limitation by
incorporating sample preparation into the platform. This was
accomplished by designing a fluidic cartridge capable of processing raw
samples and concurrently integrating a qPCR reaction tube. Reagents can
be preloaded, with no fluidic coupling to the instrument. The instrument
interfaces with the cartridge via a reagent selection valve and plunger.
The cost of goods for the cartridge, including reagents, has been
estimated at $10 <span class="citation" data-cites="CambridgeConsultants2019"><a href="#ref-CambridgeConsultants2019">[39]</a></span> and marketed at prices
typically exceeding $20.</p>
<figure id="fig:cartridge">
<img src="images/IMG_1893.jpeg"/>
<p>. <span id="fig:cartridge" label="fig:cartridge"></span></p>
<figcaption>A sketch of a sample and library preparation cartridge for a
fixed respiratory MGS workflow. Originally appeared in <span class="citation" data-cites="Whiteford2022Metagenomic"><a href="#ref-Whiteford2022Metagenomic">[40]</a></span>.</figcaption>
</figure>
<p>While achieving the same simplicity for MGS may seem like a tall
order, it is important to note that currently available cartridges have
been designed to be versatile and serve a number of applications. For
MGS applications, workflows can be optimized for specific sample types
such as nasopharyngeal, upper nasal, or saliva, along with a consistent
input volume and exclusive RNA sequencing. If sequencing is stripped
down to its bare essentials (see cartridge sketch figure), the complexity need
not be much greater than that of qPCR.</p>
<p>Like qPCR, sample preparation will, for the foreseeable future, need
to involve cell lysis, nucleic acid extraction and, unless direct RNA
sequencing becomes more reliable, a reverse transcription step to
convert RNA to complementary DNA (cDNA). Further needed steps include
the removal of unwanted nucleic acid material, in this case, digesting
DNA using DNAase, and, in most cases, the addition of adapters for the
sequencing platform in question. For platforms with relatively high
input requirements such as ONT, random amplification may be necessary to
reach a lower threshold of nucleic acids in a sample without introducing
undue bias <span class="citation" data-cites="regnault2021deep"><a href="#ref-regnault2021deep">[41]</a></span>.</p>
<p>Developing a cartridge for this use case and integrating the whole
system into one box can be done with relatively little technical risk.
Why, then, has no one developed such a system? The key reason, we
believe, is the lack of a platform that could achieve the sufficient
sequencing depth at a low enough cost without the need to analyze
multiple samples in parallel. In the next section, we ask what the
required sequencing depth for an MGS diagnostic is likely to be.</p>
<h1 class="unnumbered" id="sec:requirements">Requirements: throughput,
read length and accuracy</h1>
<h2 class="unnumbered" id="sensitivity-requirements">Sensitivity
requirements</h2>
<p>The most important question any candidate test for infectious disease
has to address is whether its sensitivity of detection is sufficient.
While PCR and sequencing will offer a different profile of costs and
benefits and need not compete for the same niche, the performance of PCR
offers a good starting point for thinking about sensitivity requirements
for MGS. In the following discussion, we focus on viral pathogens in
respiratory samples, as their relative abundances is generally much
lower than those of bacteria and viruses are therefore likely to drive
the requirements for sequencing depth.</p>
<p>It is worth emphasizing that MGS and PCR yield results that differ in
kind. PCR delivers binary information about the presence or absence of a
pathogen, and indirectly about its abundance in the sample. In contrast,
a MGS run will identify a number of nucleic acid fragments belonging to
a pathogen of interest, in addition to fragments of the host and the
non-pathogenic microbiome. Hence, an additional judgment call is
necessary for determining whether a given result should be taken as
indication of infection <span class="citation" data-cites="Zinter2019 Chiu2019">[4,6]</span>.</p>
<p>In clinical practice, cutoffs for clinical significance will likely
be determined for each pathogen or pathogen class as information about
typical abundance in non-infected individuals is accumulated. As an
example, in a pulmonary sample study, Zinter et al. used two criteria: a
normalized score of reads per million (rpm) and the deviation in
abundance from other samples in the cohort and determined the cutoff for
bacteria as a deviation of <span class="math inline"><em>Z</em> ≥ 2</span> or <span class="math inline">10</span> rpm, and for viruses and fungi as <span class="math inline">1</span> rpm <span class="citation" data-cites="Zinter2019"><a href="#ref-Zinter2019">[6]</a></span>. Miller et al. developed threshold
criteria based on the detection of non-overlapping reads from <span class="math inline"> ≥ 3</span> distinct genomic regions <span class="citation" data-cites="Miller2019"><a href="#ref-Miller2019">[42]</a></span>.</p>
<h2 class="unnumbered" id="throughput">Throughput</h2>
<p>With these goals in mind, what sequencing depth is required? PCR
tests are characterized by a high sensitivity, or very low limit of
detection (LoD): in principle, they can detect the presence of a target
fragment with only a handful of copies present in a sample. Sequencing a
human clinical sample can obviously achieve very high levels of
sensitivity: a sequencing run of terabases (Tb) on a single sample
should readily detect even pathogens that are very low in abundance. At
a depth of 40M reads per sample, MGS was shown to consistently achieve a
sensitivity on par with if not greater than PCR <span class="citation" data-cites="jumpcode Whiteford2022Metagenomic">[40,43]</span>.
However, when the requirements of cost and time-to-answer are added,
practical sensitivity of sequencing has to be determined.</p>
<p>PCR has a key advantage over sequencing: because PCR targets a short,
unique region of a genetic sequence, it is <em>insensitive to background
material</em>. A high fraction of human material (mostly <span data-acronym-form="singular+short" data-acronym-label="rRNA">rRNA</span>
in the case of RT-qPCR) or bacterial material will have only a minor
effect on the sensitivity of qPCR. In other words, the limit of
detection relies on the sample’s absolute abundance of the target. MGS,
however, is sensitive to background material. To ensure that the target
of interest is detected, one must also sequence through background
fragments until the target is reached. Thus, the sensitivity of MGS
relies on the <em>relative abundance</em> of the target among the other
nucleic acids in a sample.</p>
<p>In typical human clinical samples, host nucleic acids are orders of
magnitude more abundant than those of the pathogen. For example, the
typical fraction of SARS-CoV-2 RNA in nasopharyngeal samples was between
0.01% (or one fragment in 10,000) and 0.001% (one in 100,000). However,
viral load has been found to span some 8 orders of magnitude, with loads
as low as tens of copies/mL found in more than 1% of cases <span class="citation" data-cites="Arnaout2020"><a href="#ref-Arnaout2020">[44]</a></span>.</p>
<div class="table*">
<table id="table2">
<caption><b>Table 2:</b> Expected target reads for runs with 10M reads, 1M reads and 1M reads with rRNA depletion in SARS-CoV-2 respiratory samples. Best fit for predicted Ct values obtained based on data from [43], where the PerkinElmer®  SARS-CoV-2  Nucleic  Acid  Detection  Kit was used. Modeled with the following parameters.Total RNA: 10ng; Genome Size: 30Kb; rRNA fraction: 60%; qPCR Target Region: 90nt; Fragment Size: 1000nt.</caption>
<thead>
<tr class="header">
<th style="text-align: left;">Target Fraction</th>
<th style="text-align: left;">Target in Sample</th>
<th style="text-align: left;">Target Reads (10M)</th>
<th style="text-align: left;">Target Reads (1M)</th>
<th style="text-align: left;">Target Reads (1M, rRNA dep.)</th>
<th style="text-align: left;">Pred. Ct</th>
<th style="text-align: left;"></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><span class="math inline">1 × 10<sup>−7</sup></span></td>
<td style="text-align: left;"><span class="math inline">1.8 × 10<sup>3</sup></span></td>
<td style="text-align: left;">1</td>
<td style="text-align: left;">0.1</td>
<td style="text-align: left;">0.2</td>
<td style="text-align: left;">39.1</td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><span class="math inline">1 × 10<sup>−6</sup></span></td>
<td style="text-align: left;"><span class="math inline">1.8 × 10<sup>4</sup></span></td>
<td style="text-align: left;">10</td>
<td style="text-align: left;">1</td>
<td style="text-align: left;">2</td>
<td style="text-align: left;">35.8</td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><span class="math inline">1 × 10<sup>−5</sup></span></td>
<td style="text-align: left;"><span class="math inline">1.8 × 10<sup>5</sup></span></td>
<td style="text-align: left;">100</td>
<td style="text-align: left;">10</td>
<td style="text-align: left;">25</td>
<td style="text-align: left;">32.4</td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><span class="math inline">1 × 10<sup>−4</sup></span></td>
<td style="text-align: left;"><span class="math inline">1.8 × 10<sup>6</sup></span></td>
<td style="text-align: left;">1000</td>
<td style="text-align: left;">100</td>
<td style="text-align: left;">250</td>
<td style="text-align: left;">29.1</td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><span class="math inline">1 × 10<sup>−3</sup></span></td>
<td style="text-align: left;"><span class="math inline">1.8 × 10<sup>7</sup></span></td>
<td style="text-align: left;">10000</td>
<td style="text-align: left;">1000</td>
<td style="text-align: left;">2496</td>
<td style="text-align: left;">25.7</td>
<td style="text-align: left;"></td>
</tr>
</tbody>
</table>
</div>
<p>The expected number of reads from the pathogen of interest is a
straightforward function of the relative fraction of the pathogen in the
sample, and the number of fragments sequenced in a run. For example, if
one fragment in 100 thousand belongs to the pathogen and 1 million reads
are obtained, we should expect to see 10 reads on average <a class="footnote-ref" href="#fn1" id="fnref1" role="doc-noteref"><sup>1</sup></a>.</p>
<figure id="fig:jumpcode">
<img src="images/jumpcode.jpg"/>
<figcaption>Scatter plot of target fraction and Ct data that form the
basis of predicted Ct in Table 2 based on data from <span class="citation" data-cites="jumpcode"><a href="#ref-jumpcode">[43]</a></span>. Originally appeared
in <span class="citation" data-cites="Whiteford2022Modeling"><a href="#ref-Whiteford2022Modeling">[45]</a></span>.</figcaption>
</figure>
<p>One way to think about the requirements for a MGS diagnostic is to
draw a rough correspondence with the familiar <span data-acronym-form="singular+short" data-acronym-label="Ct">Ct</span>
values from PCR for given sample characteristics. As a heuristic, Ct
values of 25 represent high viral load and values over 35 are of
disputed clinical relevance <span class="citation" data-cites="healy2021impact"><a href="#ref-healy2021impact">[46]</a></span>. The relationship between viral
load, Ct values and fraction of reads have been by a number of empirical
studies for SARS-CoV-2 <span class="citation" data-cites="babiker_metagenomic_2020 jumpcode">[43,47]</span>. <a data-reference="table:target_reads" data-reference-type="autoref" href="#table:target_reads">[table:target_reads]</a> shows the
relationship between the real fraction of target nucleic acids in a
sample, measured Ct values and expected target reads based on data
obtained from <span class="citation" data-cites="jumpcode"><a href="#ref-jumpcode">[43]</a></span>.</p>
<figure id="fig:heat-map">
<img src="images/predicted Ct vs at least one.png"/>
<figcaption>Heat map for probability of at least one read. Expected
number of reads based on given target fraction (predicted Ct on x-axis)
and sequencing depth (y-axis ranging from 100,000 to 5,000,000
reads).</figcaption>
</figure>
<p>Based on this, we can map quite directly from the desired limit of
detection to the required sequencing depth. For example, we see that for
respiratory samples with 10 ng total nucleic acid yield, a MGS device
that delivers 10M reads in the allocated runtime yields more than 10
expected reads for Ct 35. Devices capable of 1 million reads will be
unreliable at these levels but may find clinical use in contexts where
an order of magnitude higher limit of detection is acceptable. Given the
time budget of 1 hour, this requirement leads quite directly to a
throughput, which for the majority of respiratory sample applications we
expect to range from 1M to 10M reads/hour. This conclusion notably does
not generalize for sample types with greater abundance of human RNA such
as blood, where low-abundance pathogens such as HIV are present at
concentrations requiring an order of magnitude or two greater sequencing
depth <span class="citation" data-cites="orlandi2020hiv"><a href="#ref-orlandi2020hiv">[48]</a></span>.</p>
<p>It is worth noting that these requirements could potentially be
dramatically reduced by depleting host nucleic acids. Depletion methods
remove known non-target nucleic acids (e.g., host material) from a
sequencing library and doing so can reduce read depth requirements and
increase detection sensitivity for pathogen nucleic acid <span class="citation" data-cites="jumpcode"><a href="#ref-jumpcode">[43]</a></span>. When sequencing RNA
libraries, highly repetitive ribosomal RNA (rRNA) can constitute 60-95%
of a sample, making it a prime target for depletion. As indicated by
interviews with practitioners, Qiagen’s FastSelect <span class="citation" data-cites="Qiagen"><a href="#ref-Qiagen">[49]</a></span> is currently the most
viable alternative, removing &gt;95% rRNA (host and bacterial) in 14
minutes. There are yet to be sufficient studies examining the
effectiveness of FastSelect across various sample types, but in a case
where FastSelect was applied to <span data-acronym-form="singular+short" data-acronym-label="CSF">CSF</span> samples, practitioners
report a 10x reduction in required read depth requirements (from 10-20M
to 1-2M).</p>
<p>Unfortunately, FastSelect costs &gt;$50/sample <span class="citation" data-cites="Qiagen"><a href="#ref-Qiagen">[49]</a></span>, although labs have reported <span class="citation" data-cites="RapidResponse2021"><a href="#ref-RapidResponse2021">[50]</a></span> similar
depletion results after diluting the reagent tenfold to reduce cost. The
cost and time budget may be justified in many or all cases and cost
reduction for rapid depletion kits are a high priority for development.
However, here we conservatively assume no depletion when further
building on these sequencing depth requirements.</p>
<h2 class="unnumbered" id="accuracy-and-read-length">Accuracy and read
length</h2>
<p>Sequencers also vary widely on two other variables: read length and
single-base accuracy. Both of these features are highly desirable in
research contexts where changes of even a single mutation are often the
object of study. However, our simulations <span class="citation" data-cites="whiteford2022longreads"><a href="#ref-whiteford2022longreads">[51]</a></span> suggest that for the
task of correctly classifying a known virus, or detecting a high
abundance of unknown material, read length and accuracy requirements are
comparatively modest. In addition, decrease in one can be compensated by
an increase in the other.</p>
<p>For example, for read length, we estimate that a <strong>read length
of only 25 <span data-acronym-form="singular+short" data-acronym-label="bp">bp</span></strong> and
<strong>single-base accuracy of 95%</strong> are sufficient for unique
pathogen detection, given sufficient sequencing depth <span class="citation" data-cites="whiteford2022longreads"><a href="#ref-whiteford2022longreads">[51]</a></span>. In
terms of single-base accuracy, highly sensitive detection of emerging
pathogens has been demonstrated in the field with error rates as high as
20-30% with early versions of long-read nanopore sequencing <span class="citation" data-cites="quick2016real"><a href="#ref-quick2016real">[52]</a></span>. The fact that
requirements for pathogen detection diverge so significantly from that
for research applications has key implications for development
directions, the subject of the next section.</p>
<figure id="fig:read_length">
<img src="images/read length.png"/>
<p>. <span id="fig:read_length" label="fig:read_length"></span></p>
<figcaption>Relationship between read length, accuracy, and unique
alignment to the SARS-CoV-2 genome. Originally appeared in <span class="citation" data-cites="whiteford2022longreads"><a href="#ref-whiteford2022longreads">[51]</a></span></figcaption>
</figure>
<h1 class="unnumbered" id="sec:dev-goals">Development directions</h1>
<p>Having determined these targets for sequencing platforms, we can now
formulate concrete development goals for the previously mentioned
candidate single-molecule platforms, focusing on nanopore and
single-molecule optical (SMO) sequencing. While these two platform
classes have a different profile of upsides and downsides for MGS, they
share a key advantage in minimal time required for library preparation.
ONT’s rapid sequencing kit <span class="citation" data-cites="ont2023rapidkit"><a href="#ref-ont2023rapidkit">[53]</a></span> requires less than 10 minutes,
and some SMO platforms do not require any library preparation after
lysis and nucleic acid extraction <span class="citation" data-cites="seqll2017brochure whiteford2022reticulatech">[29,54]</span>.</p>
<p>It is worth emphasizing that while we expect viable solutions in the
next 5-10 years to come from these two categories, we cannot confidently
rule out that a viable solution will emerge from a colony-based method
(e.g., if cluster generation time is reduced by an order of magnitude)
or from unexpectedly fast progress on a novel technology (such as
solid-state nanopores).</p>
<h2 id="nanopore-platforms">Nanopore platforms</h2>
<p>In nanopore sequencing, nucleic acid bases are read sequentially as
they pass through protein pores embedded within a membrane. The
throughput of this technology is therefore determined by the speed at
which bases translocate through the pore, and the number of active pores
working in parallel. Unfortunately, speed of translocation is already
close to the upper bound: the translocation needs to be slowed down by a
specialized motor protein in order for the electrical signal to be
interpretable <span class="citation" data-cites="wang2021nanopore"><a href="#ref-wang2021nanopore">[55]</a></span>.</p>
<p>In a research context, the primary advantage of nanopore sequencing
over other platforms lies in its long reads. Average read lengths in a
standard protocol exceed 1,000 bp and the longest recorded reads exceed
a million base pairs <span class="citation" data-cites="loose2019whale"><a href="#ref-loose2019whale">[56]</a></span>. In the MGS context, long reads
provide limited utility and, for nanopore sequencing in particular,
present an active hindrance, as longer fragments occupy pores for a
longer time period. There is therefore a direct trade-off between read
length and number of reads: to a first approximation, the number of
fragments sequenced scales linearly with the inverse of average read
length.</p>
<p>A logical conclusion is that for MGS, sample preparation should
include a fragmentation step to reduce the average fragment size and
thus increase the chance of detecting a low-abundance pathogen. ONT
MinION has 512 active channels working in parallel <span class="citation" data-cites="ont_minion"><a href="#ref-ont_minion">[57]</a></span>. With sufficient
saturation and the standard translocation speed of approximately 400
bp/s, we need an average fragment length of some 700 bp to get 1M reads
in an hour of sequencing, and 70 bp to achieve 10M reads. The cheapest
device, Flongle, has approximately 100 active channels, implying some 2
million reads in 60 minutes of sequencing.</p>
<p>This implies that for a sufficiently fragmented sample, nanopore
platforms already meet the key requirements of fast time-to-answer,
sufficient throughput, and relatively simple library preparation.
However, at present, the greatest barrier for a nanopore-based
diagnostic platform is the high <span data-acronym-form="singular+short" data-acronym-label="COGS">COGS</span> of consumables. This
cost, in turn, is primarily driven by the cost of manufacturing nanopore
arrays, whose cost scales linearly with chip area <span class="citation" data-cites="Whiteford2022notes_on_nanopores"><a href="#ref-Whiteford2022notes_on_nanopores">[38]</a></span>. It follows
that the two available levers for cost-optimization are reducing the
required area or using lower-cost materials or fabrication
procedures.</p>
<p>From published patents <span class="citation" data-cites="ont-array-patent"><a href="#ref-ont-array-patent">[58]</a></span>, it is possible to infer that
the design employed by ONT presently requires the use of non-standard
fabrication facilities able to process novel materials, such as <span data-acronym-form="singular+short" data-acronym-label="MEMS">MEMS</span>
fabrication facilities. Thus, the cost is likely to be driven driven by
the limited capacity of MEMS fabrication facilities globally, rather
than by the fundamental cost of materials and fabrication
procedures.</p>
<p>The potential to replace MEMS fabrication with a less costly process
is worth investigating as a pathway of achieving a device that fits the
point-of-care specifications. There are potentially many approaches to
try in parallel.</p>
<p>While silicon substrate arrays appear to be the most viable strategy
for scaling the number of pores into the thousands or tens of thousands.
For applications where a lower pore count is sufficient—such as the 126
in the Flongle—alternative methodologies may offer advantages. One such
alternative is the direct fabrication of silver electrodes onto printed
circuit boards, a technique successfully demonstrated on a smaller scale
by the companies Nanion and Elements <span class="citation" data-cites="elements2019"><a href="#ref-elements2019">[59]</a></span>. While there is technical
uncertainty as to whether this approach can scale beyond 16 channels,
scaling to some 100 channels with this approach might be feasible.</p>
<p>While it is difficult to predict which approach will yield the best
results, we should expect that a ground-up reimplentation that aims for
cost-optimization should achieve a much lower cost point. Although it is
unclear whether any of these will be perceived as attractive by ONT, a
number of companies, including Qitan, Genia or Nanion have entered the
market and this trend is poised to continue.</p>
<h2 id="single-molecule-optical-platforms">Single-molecule optical
platforms</h2>
<p>Single-molecule optical technologies were brought to the market by
Helicos <span class="citation" data-cites="thompson2010helicos"><a href="#ref-thompson2010helicos">[60]</a></span> (now defunct) and <span data-acronym-form="singular+short" data-acronym-label="PacBio">PacBio</span> <span class="citation" data-cites="rhoads_pacbio_2015"><a href="#ref-rhoads_pacbio_2015">[61]</a></span>. Considering this class of
technologies as a candidate platform may be surprising, as they have
generally been embodied as costly, "fridge-sized" instruments with long
library preparation (&gt;3 hours). However, this is driven not by the
fundamental needs of the platform, but rather by the market demand for
high single-base accuracy and long reads. If these requirements are
relaxed, <span data-acronym-form="singular+short" data-acronym-label="SMO">SMO</span> approaches can achieve
very simple sample preparation <span class="citation" data-cites="seqll2017brochure"><a href="#ref-seqll2017brochure">[29]</a></span> and a low cost of consumables
<span class="citation" data-cites="whiteford2022reticulatech"><a href="#ref-whiteford2022reticulatech">[54]</a></span>.</p>
<p>Commonly employed library preparation techniques take many hours and
are not a good fit for point-of-care MGS. However, the SMRTBells library
preparation kit <span class="citation" data-cites="SMRTbells"><a href="#ref-SMRTbells">[62]</a></span> was introduced to drive accuracy to
&gt;99.9% and read length to  15 kb, neither of which is required for
MGS. Without these requirements, library preparation for optical methods
can be as fast as for nanopore sequencing ( 5 minutes) and still achieve
accuracies upwards of 80% combined with a compensating read length of
hundreds of bases. Similarly, approaches derived from the Helicos
technology have been demonstrated to work with minimal library
preparation with error rates below 5% and read lengths exceeding 25 bp,
making them a potential candidate for a MGS device <span class="citation" data-cites="whiteford2022reticulatech"><a href="#ref-whiteford2022reticulatech">[54]</a></span>.</p>
<p>In terms of throughput, the sequencing step alone can be achieved in
a fraction of the time required for nanopore sequencing, as SMO
approaches can use many more sensors working in parallel. In PacBio
sequencing, imaging more than 1 million fragments in parallel is common
<span class="citation" data-cites="sequelSystems"><a href="#ref-sequelSystems">[30]</a></span> and, with
a speed of 10 nucleotides per second, the run can be finished in less
than a minute for the read lengths required for MGS. Another key
advantage of an optical approach relative to nanopore sequencing is that
it is compatible with a less complex chip and presents a clearer path to
a consumable cost of $10 or less <span class="citation" data-cites="whiteford2022reticulatech"><a href="#ref-whiteford2022reticulatech">[54]</a></span>.</p>
<p>A key challenge to address will be the optimization of device cost,
currently exceeding $500,000 in the case of PacBio instruments. However,
achieving a cost lower than $10,000 appears feasible if instrumentation
is reimagined from the ground up. For example, photonic chips need not
be monolithically integrated. Consumer-grade cameras available for $300
have resolution sufficient for the accuracy requirements of an MGS
diagnostic. Throughput in a low-cost platform will be limited by
compatibility with low-cost cameras, but the goal of 1-10 million
sensing regions (and hence reads) appears achievable.</p>
<p>A particularly promising emerging approach is that of electro-optical
zero-mode waveguides <span class="citation" data-cites="wanunu2022zmw"><a href="#ref-wanunu2022zmw">[63]</a></span>, which may enable substantially
lower input requirements, potentially obviating the need for random
amplification of nucleic acids in a sample.</p>
<p><span class="marginnote"><figure>
<img src="images/IMG_1895.jpeg"/>
<figcaption>Sketch of a cost-optimized single-molecule optical platform.
Originally appeared in <span class="citation" data-cites="whiteford2022reticulatech"><a href="#ref-whiteford2022reticulatech">[54]</a></span>.</figcaption>
</figure></span></p>
<h1 class="unnumbered" id="sec:accelerating">Accelerating
development</h1>
<p>Based on the previous analysis, there are at least two independent
pathways that are likely to meet the criteria for a viable point-of-care
MGS device. Despite the large large amounts of private investments
flowing into sequencing technology as a whole, there is a number reasons
to believe that directed development can yield significant improvements
over business-as-usual. A number of observations, informed largely by
the authors’ experience with the sequencing landscape, as well as
conversations with experts, push in this direction:</p>
<ul>
<li><p>Development is driven by <strong>customer demand</strong>. The
primary market for sequencing instruments is in research and high-end
diagnostics (e.g. cancer). In these contexts, the primary consideration
is often extraordinarily high accuracy, as the correct identification of
every single base is potentially informative. The task of correctly
classifying a pathogen of interest or detecting an anomaly does not
require such high single-base accuracies, as we justify later.
Similarly, the requirements for read length, as well as sequencing
depth, are much lower.</p></li>
<li><p><strong>Time to answer</strong> of hours or days is not a
limiting factor in many research contexts. Typical workflows are
structured around large runs, often counted in thousands of billions of
bases (e.g. ONT PromethION, Illumina NovaSeq). Researchers typically
care about a low cost per base for these large runs. Large, high-end
instruments can minimize this cost per base.</p></li>
<li><p>The sequencing market is still comparatively small, dominated by
a few players with relatively enforceable intellectual property, and
<strong>freedom-to-operate</strong> is thus relatively limited.</p></li>
<li><p>Relative to the present sequencing device applications, the
infectious disease diagnostic market is likely to present lower margins
and lower barriers to entry. While the market is potentially large in
volume, there is presently <strong>no clear demand signal</strong> that
would justify the relatively large investments (at least tens of
millions of dollars for a working product) necessary.</p></li>
</ul>
<div class="table*">
<p><span id="table:sequencing_capacity" label="table:sequencing_capacity"></span></p>
<table>
<caption><b>Table 3:</b> Estimated annual sequencing capacity by platform, based on analysis detailed in [60].</caption>
<thead>
<tr class="header">
<th style="text-align: left;">Platform</th>
<th style="text-align: left;">Estimated Instruments</th>
<th style="text-align: left;">Runs/Week</th>
<th style="text-align: left;">Total Runs/Year</th>
<th style="text-align: left;">Run Yield (Tb)</th>
<th style="text-align: left;">Tb/year</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">ONT MinION</td>
<td style="text-align: left;">5501</td>
<td style="text-align: left;">3</td>
<td style="text-align: left;">858156</td>
<td style="text-align: left;">0.05</td>
<td style="text-align: left;">42907.8</td>
</tr>
<tr class="even">
<td style="text-align: left;">ONT GridION</td>
<td style="text-align: left;">782</td>
<td style="text-align: left;">3</td>
<td style="text-align: left;">121992</td>
<td style="text-align: left;">0.25</td>
<td style="text-align: left;">30498</td>
</tr>
<tr class="odd">
<td style="text-align: left;">ONT PromethION 48</td>
<td style="text-align: left;">67</td>
<td style="text-align: left;">2</td>
<td style="text-align: left;">6968</td>
<td style="text-align: left;">14</td>
<td style="text-align: left;">97552</td>
</tr>
<tr class="even">
<td style="text-align: left;">Ilm Novaseq 6000</td>
<td style="text-align: left;">1485</td>
<td style="text-align: left;">3</td>
<td style="text-align: left;">231660</td>
<td style="text-align: left;">6</td>
<td style="text-align: left;">1389960</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Ilm NextSeq</td>
<td style="text-align: left;">5430</td>
<td style="text-align: left;">3</td>
<td style="text-align: left;">847080</td>
<td style="text-align: left;">0.36</td>
<td style="text-align: left;">304948.8</td>
</tr>
<tr class="even">
<td style="text-align: left;">Ilm Miseq/Mini/iSeq</td>
<td style="text-align: left;">12340</td>
<td style="text-align: left;">3</td>
<td style="text-align: left;">1925040</td>
<td style="text-align: left;">0.015</td>
<td style="text-align: left;">28875.6</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Ion Torrent</td>
<td style="text-align: left;">2220</td>
<td style="text-align: left;">14</td>
<td style="text-align: left;">1616160</td>
<td style="text-align: left;">0.05</td>
<td style="text-align: left;">80808</td>
</tr>
<tr class="even">
<td style="text-align: left;">PacBio</td>
<td style="text-align: left;">577</td>
<td style="text-align: left;">5</td>
<td style="text-align: left;">150020</td>
<td style="text-align: left;">0.03</td>
<td style="text-align: left;">4500.6</td>
</tr>
<tr class="odd">
<td style="text-align: left;">MGI - Mid/Low</td>
<td style="text-align: left;">2000</td>
<td style="text-align: left;">3</td>
<td style="text-align: left;">312000</td>
<td style="text-align: left;">0.72</td>
<td style="text-align: left;">224640</td>
</tr>
<tr class="even">
<td style="text-align: left;">MGI -T7</td>
<td style="text-align: left;">10</td>
<td style="text-align: left;">5</td>
<td style="text-align: left;">2600</td>
<td style="text-align: left;">6</td>
<td style="text-align: left;">15600</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Total</td>
<td style="text-align: left;">30412</td>
<td style="text-align: left;"></td>
<td style="text-align: left;">6071676</td>
<td style="text-align: left;"></td>
<td style="text-align: left;">2220290.8</td>
</tr>
</tbody>
</table>
</div>
<p>By our estimates, more than half of global sequencing capacity in
terms of the number of bases sequenced annually is accounted for by
Illumina NovaSeq alone <span class="citation" data-cites="whiteford_seq_capability"><a href="#ref-whiteford_seq_capability">[64]</a></span>. NovaSeq is a $1
million instrument that yields up to 6 Tb of data per run with an error
rate on the order of 0.1%.A single run can cost more than $5,000. This
large share of sequencing capacity is accounted for by only some 1500
instruments in large laboratories <span class="citation" data-cites="whiteford_seq_capability"><a href="#ref-whiteford_seq_capability">[64]</a></span>.</p>
<p>Another key player, ONT, is known for its relatively affordable,
miniaturized devices such as the MinION or Flongle. In 2021, however,
fully 55.7% of ONT’s revenue was generated by its 67 PromethION <span class="citation" data-cites="ont_promethion"><a href="#ref-ont_promethion">[65]</a></span> instruments
<span class="citation" data-cites="ont-2021-annual-report"><a href="#ref-ont-2021-annual-report">[66]</a></span>,
each of which can generate up to 12 Tb of data, with device costs
ranging from $225,000 to $450,000.</p>
<p>What, then, could shift these market dynamics? Broadly, we see two
approaches to this problem:</p>
<ul>
<li><p><strong>Push mechanisms</strong> have historically been
successful in stimulating R&amp;D in sequencing. The Human Genome
Project and its successors (e.g. the $1,000 Genome Project) paved the
way for technology development by direct public investment into R&amp;D.
Similarly, a $10 MGS device provides a challenging but achievable goal
around which activity can be catalyzed by direct grants or other forms
of support.</p></li>
<li><p><strong>Pull mechanisms</strong> such as advanced market
commitments <span class="citation" data-cites="kremer2020amc"><a href="#ref-kremer2020amc">[67]</a></span> may be appropriate here, as the
target product profile is readily definable in this context, and
achievable in a timeframe of less than 5 years. At present, building a
fab from scratch, which could pave the way towards low-cost nanopore
devices, is an endeavor in the hundreds of millions of dollars and is
difficult to justify given the lack of a credible demand signal.
However, at volumes comparable to qPCR diagnostics (&gt;1M units a
month), such investment could be justified. Tools such as advanced
market commitments, as well as credible signals of interest in an MGS
diagnostic platform from national and international organizations, could
pave the way towards such investments.</p></li>
</ul>
<h1 class="unnumbered" id="conclusions">Conclusions</h1>
<p>Widespread adoption of metagenomic sequencing for infectious disease
diagnosis promises both continuous public health benefits and a greatly
enhanced capacity to detect and contain future pandemics. While
currently available technologies are not well suited for such widespread
adoption, at least two classes of technologies, single-molecule optical
and nanopore sequencing, have a good chance of achieving a combination
of cost and performance that would make them a viable solution for
clinicians worldwide.</p>
<h1 class="unnumbered">Acknowledgements</h1>
<p>This project was funded by Open Philanthropy, whose support we are
grateful for. We are grateful to Rahul Arora, Jake Pencharz and Janvi
Ahuja for help on the project and to Adam Marblestone for helpful comments. We also thank the researchers and clinicians who shared invaluable details on practical workflows and real-world implementation.</p>
<h1 class="unnumbered" id="bibliography">Bibliography</h1>
<div class="references csl-bib-body" id="refs" role="list">
<div class="csl-entry" id="ref-Pekar2021" role="listitem">
<div class="csl-right-inline">[1] J. Pekar, M. Worobey, N. Moshiri, K. Scheffler, and J. Wertheim, <span>“Timing the SARS-CoV-2 index case in hubei province,”</span> <em>Science</em>, vol. 372, no. 6540, pp. 412–7, 2021.</div>
</div>
<div class="csl-entry" id="ref-Zhu2020" role="listitem">
<div class="csl-right-inline">[2] N. Zhu <em>et al.</em>, <span>“A novel coronavirus from patients with pneumonia in china, 2019,”</span> <em>N Engl J Med</em>, vol. 382, no. 8, pp. 727–33, 2020.</div>
</div>
<div class="csl-entry" id="ref-glennerster2023calculating" role="listitem">
<div class="csl-right-inline">[3] R. Glennerster, C. M. Snyder, and B. J. Tan, <span>“Calculating the costs and benefits of advance preparations for future pandemics,”</span> <em>IMF Economic Review</em>, pp. 1–38, 2023.</div>
</div>
<div class="csl-entry" id="ref-Chiu2019" role="listitem">
<div class="csl-right-inline">[4] C. Chiu and S. Miller, <span>“Clinical metagenomics,”</span> <em>Nat Rev Genet</em>, vol. 20, no. 6, pp. 341–55, 2019.</div>
</div>
<div class="csl-entry" id="ref-schlaberg_viral_2017" role="listitem">
<div class="csl-right-inline">[5] R. Schlaberg <em>et al.</em>, <span>“Viral Pathogen Detection by Metagenomics and Pan-Viral Group Polymerase Chain Reaction in Children With Pneumonia Lacking Identifiable Etiology,”</span> <em>The Journal of Infectious Diseases</em>, vol. 215, no. 9, pp. 1407–1415, May 2017.</div>
</div>
<div class="csl-entry" id="ref-Zinter2019" role="listitem">
<div class="csl-right-inline">[6] M. Zinter <em>et al.</em>, <span>“Pulmonary metagenomic sequencing suggests missed infections in immunocompromised children,”</span> <em>Clin Infect Dis</em>, vol. 68, no. 11, pp. 1847–1855, 2019.</div>
</div>
<div class="csl-entry" id="ref-Charalampous2019" role="listitem">
<div class="csl-right-inline">[7] T. Charalampous <em>et al.</em>, <span>“Nanopore metagenomics enables rapid clinical diagnosis of bacterial lower respiratory infection,”</span> <em>Nat Biotechnol</em>, vol. 37, no. 7, pp. 783–92, 2019.</div>
</div>
<div class="csl-entry" id="ref-edgeworth2023respiratory" role="listitem">
<div class="csl-right-inline">[8] J. D. Edgeworth, <span>“Respiratory metagenomics: Route to routine service,”</span> <em>Current Opinion in Infectious Diseases</em>, vol. 36, no. 2, p. 115, 2023.</div>
</div>
<div class="csl-entry" id="ref-WHO2011" role="listitem">
<div class="csl-right-inline">[9] World Health Organization, <span>“Establishment of PCR laboratory in developing countries,”</span> WHO Regional Office for South-East Asia, SEA-HLM-419, 2011.</div>
</div>
<div class="csl-entry" id="ref-sharma2023threat" role="listitem">
<div class="csl-right-inline">[10] S. Sharma, J. Pannu, S. Chorlton, J. L. Swett, and D. J. Ecker, <span>“Threat net: A metagenomic surveillance network for biothreat detection and early warning,”</span> <em>Health security</em>, 2023.</div>
</div>
<div class="csl-entry" id="ref-Consortium2021" role="listitem">
<div class="csl-right-inline">[11] The Nucleic Acid Observatory Consortium, <span>“A global nucleic acid observatory for biodefense and planetary health,”</span> <em>arXiv preprint arXiv:2108.02678</em>, 2021.</div>
</div>
<div class="csl-entry" id="ref-Topol2023" role="listitem">
<div class="csl-right-inline">[12] E.
Topol, <span>“A culture of [blood] cultures,”</span> 2023. <a href="https://erictopol.substack.com/p/a-culture-of-blood-cultures">https://erictopol.substack.com/p/a-culture-of-blood-cultures</a></div>
</div>
<div class="csl-entry" id="ref-msf2022access" role="listitem">
<div class="csl-right-inline">[13] Médecins Sans Frontières, <span>“Principles for
access to multi-disease molecular diagnostics.”</span> 2022. Available:
<a href="https://www.msfaccess.org/principles-access-multi-disease-molecular-diagnostics">https://www.msfaccess.org/principles-access-multi-disease-molecular-diagnostics</a></div>
</div>
<div class="csl-entry" id="ref-GeneXpertSystem" role="listitem">
<div class="csl-right-inline">[14] Cepheid, <span>“GeneXpert system.”</span>
Available: <a href="https://www.cepheid.com/en-US/systems/genexpert-family-of-systems/genexpert-system.html">https://www.cepheid.com/en-US/systems/genexpert-family-of-systems/genexpert-system.html</a></div>
</div>
<div class="csl-entry" id="ref-CepheidNewsReleaseArchive" role="listitem">
<div class="csl-right-inline">[15] <span>“Cepheid news release archive. Cepheid
announces FleXible cartridge program.”</span> Available: <a href="https://cepheid.mediaroom.com/2019-04-15-Cepheid-Announces-FleXible-Cartridge-Program">https://cepheid.mediaroom.com/2019-04-15-Cepheid-Announces-FleXible-Cartridge-Program</a></div>
</div>
<div class="csl-entry" id="ref-GenomeWeb2022" role="listitem">
<div class="csl-right-inline">[16] GenomeWeb, <span>“Danaher <span>Q4</span>
revenues rise 21 percent.”</span> 2022. Available: <a href="https://www.genomeweb.com/business-news/danaher-q4-revenues-rise-21-percent">https://www.genomeweb.com/business-news/danaher-q4-revenues-rise-21-percent</a></div>
</div>
<div class="csl-entry" id="ref-BioFireDiagnostics2016" role="listitem">
<div class="csl-right-inline">[17] <span>“BioFire diagnostics. FilmArray
panels—infectious disease diagnostics.”</span> 2016. Available: <a href="https://www.biofiredx.com/products/the-filmarray-panels/">https://www.biofiredx.com/products/the-filmarray-panels/</a></div>
</div>
<div class="csl-entry" id="ref-novaSeq6000" role="listitem">
<div class="csl-right-inline">[18] Illumina, <span>“NovaSeq 6000 reagent
kits,”</span> 2023. <a href="https://www.illumina.com/products/by-type/sequencing-kits/cluster-gen-sequencing-reagents/novaseq-reagent-kits.html">https://www.illumina.com/products/by-type/sequencing-kits/cluster-gen-sequencing-reagents/novaseq-reagent-kits.html</a></div>
</div>
<div class="csl-entry" id="ref-miseqSpecs" role="listitem">
<div class="csl-right-inline">[19] Illumina, <span>“MiSeq specifications,”</span>
2023. <a href="https://www.illumina.com/systems/sequencing-platforms/miseq/specifications.html">https://www.illumina.com/systems/sequencing-platforms/miseq/specifications.html</a></div>
</div>
<div class="csl-entry" id="ref-iseq100" role="listitem">
<div class="csl-right-inline">[20] Illumina, <span>“ISeq 100 system,”</span> 2023.
<a href="https://www.illumina.com/systems/sequencing-platforms/iseq.html">https://www.illumina.com/systems/sequencing-platforms/iseq.html</a></div>
</div>
<div class="csl-entry" id="ref-ionGeneStudio" role="listitem">
<div class="csl-right-inline">[21] Ion Torrent, <span>“Ion GeneStudio S5
system,”</span> 2023. <a href="https://www.thermofisher.com/order/catalog/product/A38194">https://www.thermofisher.com/order/catalog/product/A38194</a></div>
</div>
<div class="csl-entry" id="ref-ion520Chip" role="listitem">
<div class="csl-right-inline">[22] Ion Torrent, <span>“Ion 520 chip kit,”</span>
2023. <a href="https://www.thermofisher.com/order/catalog/product/A27762">https://www.thermofisher.com/order/catalog/product/A27762</a></div>
</div>
<div class="csl-entry" id="ref-quail2012" role="listitem">
<div class="csl-right-inline">[23] M.
Quail <em>et al.</em>, <span>“A tale of three next generation sequencing
platforms: Comparison of ion torrent, <span>Pacific BioSciences</span>
and illumina MiSeq sequencers,”</span> <em>BMC Genomics</em>, vol. 13,
p. 341, 2012.</div>
</div>
<div class="csl-entry" id="ref-heger2015" role="listitem">
<div class="csl-right-inline">[24] GenomeWeb, <span>“Thermo fisher launches new
systems to focus on plug and play targeted sequencing,”</span> 2015. <a href="https://www.genomeweb.com/sequencing-technology/thermo-fisher-launches-new-systems-focus-plug-and-play-targeted-sequencing">https://www.genomeweb.com/sequencing-technology/thermo-fisher-launches-new-systems-focus-plug-and-play-targeted-sequencing</a></div>
</div>
<div class="csl-entry" id="ref-nanoporeKits" role="listitem">
<div class="csl-right-inline">[25] Oxford Nanopore Technologies, <span>“DNA and
RNA sequencing kits,”</span> 2023. <a href="https://nanoporetech.com/products/kits">https://nanoporetech.com/products/kits</a></div>
</div>
<div class="csl-entry" id="ref-greninger2015" role="listitem">
<div class="csl-right-inline">[26] A.
Greninger <em>et al.</em>, <span>“Rapid metagenomic identification of
viral pathogens in clinical samples by real-time nanopore sequencing
analysis,”</span> <em>Genome Med</em>, vol. 7, p. 99, 2015.</div>
</div>
<div class="csl-entry" id="ref-tyson2020" role="listitem">
<div class="csl-right-inline">[27] J.
Tyson <em>et al.</em>, <span>“Improvements to the ARTIC multiplex PCR
method for SARS-CoV-2 genome sequencing using nanopore.”</span> 2020.
doi: <a href="https://doi.org/10.1101/2020.09.04.283077">10.1101/2020.09.04.283077</a>.</div>
</div>
<div class="csl-entry" id="ref-nanoporeUpdate2023" role="listitem">
<div class="csl-right-inline">[28] <span>“Oxford nanopore delivers technology
update at annual london calling conference: Bringing together years of
innovation to showcase one sensing platform for all biological
analyses,”</span> 2023. <a href="https://nanoporetech.com/about-us/news/oxford-nanopore-delivers-technology-update-annual-london-calling-conference-bringing">https://nanoporetech.com/about-us/news/oxford-nanopore-delivers-technology-update-annual-london-calling-conference-bringing</a></div>
</div>
<div class="csl-entry" id="ref-seqll2017brochure" role="listitem">
<div class="csl-right-inline">[29] SeqLL, <span>“<span>SeqLL</span>
<span>Sequencing</span> <span>Brochure</span>.”</span> 2017. Accessed:
Mar. 04, 2023. [Online]. Available: <a href="http://seqll.com/wp-content/uploads/2017/02/seqll-sequence-brochure2_2017.pdf">http://seqll.com/wp-content/uploads/2017/02/seqll-sequence-brochure2_2017.pdf</a></div>
</div>
<div class="csl-entry" id="ref-sequelSystems" role="listitem">
<div class="csl-right-inline">[30] Pacific BioSciences, <span>“Sequel
systems,”</span> 2018. <a href="https://www.pacb.com/technology/hifi-sequencing/sequel-system/">https://www.pacb.com/technology/hifi-sequencing/sequel-system/</a></div>
</div>
<div class="csl-entry" id="ref-voltrax" role="listitem">
<div class="csl-right-inline">[31] Oxford Nanopore Technologies,
<span>“<span>VolTRAX</span> <span></span> <span>Oxford</span>
<span>Nanopore</span> <span>Technologies</span>.”</span> Accessed: Mar.
03, 2023. [Online]. Available: <a href="https://nanoporetech.com/products/voltrax">https://nanoporetech.com/products/voltrax</a></div>
</div>
<div class="csl-entry" id="ref-neoprep" role="listitem">
<div class="csl-right-inline">[32] Illumina, <span>“<span>NeoPrep</span>
<span>Library</span> <span>Prep</span> <span>System</span>.”</span>
Accessed: Mar. 03, 2023. [Online]. Available: <a href="https://jp.illumina.com/content/dam/illumina-marketing/documents/products/datasheets/neoprep-system-data-sheet-970-2014-004.pdf">https://jp.illumina.com/content/dam/illumina-marketing/documents/products/datasheets/neoprep-system-data-sheet-970-2014-004.pdf</a></div>
</div>
<div class="csl-entry" id="ref-whiteford2023cluster" role="listitem">
<div class="csl-right-inline">[33] N.
Whiteford, <span>“Why does cluster generation take 5 hours? ASeq
newsletter.”</span> 2023. Available: <a href="https://aseq.substack.com/p/why-does-cluster-generation-take">https://aseq.substack.com/p/why-does-cluster-generation-take</a></div>
</div>
<div class="csl-entry" id="ref-MGITech2023" role="listitem">
<div class="csl-right-inline">[34] MGI, <span>“About MGI,”</span> 2023. <a href="https://en.mgi-tech.com/about/">https://en.mgi-tech.com/about/</a></div>
</div>
<div class="csl-entry" id="ref-SingularGenomics2023" role="listitem">
<div class="csl-right-inline">[35] Singular Genomics, <span>“About us,”</span>
2023. <a href="https://singulargenomics.com/company/about/">https://singulargenomics.com/company/about/</a></div>
</div>
<div class="csl-entry" id="ref-GenomeWeb2009" role="listitem">
<div class="csl-right-inline">[36] GenomeWeb, <span>“LaserGen says its new
reversible terminators could improve several sequencing
platforms.”</span> 2009. Available: <a href="https://www.genomeweb.com/sequencing/lasergen-says-its-new-reversible-terminators-could-improve-several-sequencing-pl">https://www.genomeweb.com/sequencing/lasergen-says-its-new-reversible-terminators-could-improve-several-sequencing-pl</a></div>
</div>
<div class="csl-entry" id="ref-flongle" role="listitem">
<div class="csl-right-inline">[37] Oxford Nanopore Technologies, <span>“Flongle |
<span>Oxford Nanopore Technologies</span>.”</span> 2023. Available: <a href="https://nanoporetech.com/products/flongle">https://nanoporetech.com/products/flongle</a></div>
</div>
<div class="csl-entry" id="ref-Whiteford2022notes_on_nanopores" role="listitem">
<div class="csl-right-inline">[38] N.
Whiteford, <span>“Notes on nanopores,”</span> 2022. <a href="https://aseq.substack.com/p/notes-on-nanopores">https://aseq.substack.com/p/notes-on-nanopores</a>
(accessed Sep. 06, 2023).</div>
</div>
<div class="csl-entry" id="ref-CambridgeConsultants2019" role="listitem">
<div class="csl-right-inline">[39] <span>“Cambridge consultants, medecins sans
frontieres. Cost of goods and manufacturing analysis of GeneXpert
cartridges.”</span> <a href="https://msfaccess.org/sites/default/files/2019-12/2018\%20COGS\%20analysis\%20of\%20Xpert\%20MTB_RIF\%20Ultra\%20cartridges.pdf">https://msfaccess.org/sites/default/files/2019-12/2018\%20COGS\%20analysis\%20of\%20Xpert\%20MTB_RIF\%20Ultra\%20cartridges.pdf</a></div>
</div>
<div class="csl-entry" id="ref-Whiteford2022Metagenomic" role="listitem">
<div class="csl-right-inline">[40] N.
Whiteford, <span>“A metagenomic sample prep system,”</span> <em>ASeq
Newsletter</em>. 2022. Available: <a href="https://aseq.substack.com/p/a-metagenomic-sample-prep-system">https://aseq.substack.com/p/a-metagenomic-sample-prep-system</a></div>
</div>
<div class="csl-entry" id="ref-regnault2021deep" role="listitem">
<div class="csl-right-inline">[41] B.
Regnault, T. Bigot, L. Ma, P. Pérot, S. Temmam, and M. Eloit,
<span>“Deep impact of random amplification and library construction
methods on viral metagenomics results,”</span> <em>Viruses</em>, vol.
13, no. 2, p. 253, 2021.</div>
</div>
<div class="csl-entry" id="ref-Miller2019" role="listitem">
<div class="csl-right-inline">[42] S.
Miller <em>et al.</em>, <span>“Laboratory validation of a clinical
metagenomic sequencing assay for pathogen detection in cerebrospinal
fluid,”</span> <em>Genome Res</em>, vol. 29, no. 5, pp. 831–842,
2019.</div>
</div>
<div class="csl-entry" id="ref-jumpcode" role="listitem">
<div class="csl-right-inline">[43] A.
P. Chan <em>et al.</em>, <span>“A universal day zero infectious disease
testing strategy leveraging CRISPR-based sample depletion and
metagenomic sequencing,”</span> <em>medRxiv</em>, pp. 2022–05,
2022.</div>
</div>
<div class="csl-entry" id="ref-Arnaout2020" role="listitem">
<div class="csl-right-inline">[44] R.
Arnaout <em>et al.</em>, <span>“SARS-CoV2 testing: The limit of
detection matters,”</span> <em>bioRxiv</em>, 2020.</div>
</div>
<div class="csl-entry" id="ref-Whiteford2022Modeling" role="listitem">
<div class="csl-right-inline">[45] N.
Whiteford, <span>“Modeling sequencing sensitivity,”</span> <em>ASeq
Newsletter</em>, 2022, Available: <a href="https://aseq.substack.com/p/modeling-sequencing-sensitivity">https://aseq.substack.com/p/modeling-sequencing-sensitivity</a></div>
</div>
<div class="csl-entry" id="ref-healy2021impact" role="listitem">
<div class="csl-right-inline">[46] B.
Healy, A. Khan, H. Metezai, I. Blyth, and H. Asad, <span>“The impact of
false positive COVID-19 results in an area of low prevalence,”</span>
<em>Clinical Medicine</em>, vol. 21, no. 1, p. e54, 2021.</div>
</div>
<div class="csl-entry" id="ref-babiker_metagenomic_2020" role="listitem">
<div class="csl-right-inline">[47] A.
Babiker <em>et al.</em>, <span>“Metagenomic <span>Sequencing</span>
<span>To</span> <span>Detect</span> <span>Respiratory</span>
<span>Viruses</span> in <span>Persons</span> under
<span>Investigation</span> for <span>COVID</span>-19,”</span>
<em>Journal of Clinical Microbiology</em>, vol. 59, no. 1, pp.
e02142–20, Dec. 2020, doi: <a href="https://doi.org/10.1128/JCM.02142-20">10.1128/JCM.02142-20</a>.</div>
</div>
<div class="csl-entry" id="ref-orlandi2020hiv" role="listitem">
<div class="csl-right-inline">[48] C.
Orlandi <em>et al.</em>, <span>“A comparative analysis of unintegrated
HIV-1 DNA measurement as a potential biomarker of the cellular reservoir
in the blood of patients controlling and non-controlling viral
replication,”</span> <em>J Transl Med</em>, vol. 18, no. 1, p. 204, May
2020.</div>
</div>
<div class="csl-entry" id="ref-Qiagen" role="listitem">
<div class="csl-right-inline">[49] <span>“Qiagen. QIAseq FastSelect epidemiology
kits.”</span> Available: <a href="https://www.qiagen.com/us/products/discovery-and-translational-research/next-generation-sequencing/rna-sequencing/ribosomal-rna-and-globin-mRNA-removal/qiaseq-fastselect-epidemiology-kits">https://www.qiagen.com/us/products/discovery-and-translational-research/next-generation-sequencing/rna-sequencing/ribosomal-rna-and-globin-mRNA-removal/qiaseq-fastselect-epidemiology-kits</a></div>
</div>
<div class="csl-entry" id="ref-RapidResponse2021" role="listitem">
<div class="csl-right-inline">[50] Chan Zuckerberg Biohub, <span>“Rapid response.
resources.”</span> 2021. Available: <a href="https://www.czbiohub.org/rapid-response/resources/">https://www.czbiohub.org/rapid-response/resources/</a></div>
</div>
<div class="csl-entry" id="ref-whiteford2022longreads" role="listitem">
<div class="csl-right-inline">[51] N.
Whiteford, <span>“Are long reads useful for infectious disease
testing?”</span> <em>ASeq Newsletter</em>. Oct. 2022. Accessed: Mar. 03,
2023. [Online]. Available: <a href="https://aseq.substack.com/p/are-long-reads-useful-for-infectious">https://aseq.substack.com/p/are-long-reads-useful-for-infectious</a></div>
</div>
<div class="csl-entry" id="ref-quick2016real" role="listitem">
<div class="csl-right-inline">[52] J.
Quick <em>et al.</em>, <span>“Real-time, portable genome sequencing for
ebola surveillance,”</span> <em>Nature</em>, vol. 530, no. 7589, pp.
228–232, 2016.</div>
</div>
<div class="csl-entry" id="ref-ont2023rapidkit" role="listitem">
<div class="csl-right-inline">[53] Oxford Nanopore Technologies, <span>“Rapid
sequencing kit v1.4.”</span> 2023. Available: <a href="https://store.nanoporetech.com/uk/productDetail/?id=rapid-sequencing-kit-v14">https://store.nanoporetech.com/uk/productDetail/?id=rapid-sequencing-kit-v14</a></div>
</div>
<div class="csl-entry" id="ref-whiteford2022reticulatech" role="listitem">
<div class="csl-right-inline">[54] N.
Whiteford, <span>“Reticula pt. 3 - technological approach,”</span>
<em>ASeq Newsletter</em>, 2022, Available: <a href="https://aseq.substack.com/p/reticula-pt-3-technological-approach">https://aseq.substack.com/p/reticula-pt-3-technological-approach</a></div>
</div>
<div class="csl-entry" id="ref-wang2021nanopore" role="listitem">
<div class="csl-right-inline">[55] Y.
Wang, Y. Zhao, A. Bollas, Y. Wang, and K. F. Au, <span>“Nanopore
sequencing technology, bioinformatics and applications,”</span>
<em>Nature biotechnology</em>, vol. 39, no. 11, pp. 1348–1365,
2021.</div>
</div>
<div class="csl-entry" id="ref-loose2019whale" role="listitem">
<div class="csl-right-inline">[56] M.
Loose, V. Rakyan, N. Holmes, and A. Payne, <span>“Whale watching with
BulkVis: A graphical viewer for oxford nanopore bulk fast5
files,”</span> <em>Bioinformatics</em>, vol. 35, no. 13, 2019.</div>
</div>
<div class="csl-entry" id="ref-ont_minion" role="listitem">
<div class="csl-right-inline">[57] Oxford Nanopore Technologies, <span>“Getting
started with <span>MinION</span> - what you need to know,”</span>
<em><span>Oxford Nanopore Technologies</span></em>. Accessed: Feb. 08,
2023. [Online]. Available: <a href="https://nanoporetech.com/community/faqs">https://nanoporetech.com/community/faqs</a></div>
</div>
<div class="csl-entry" id="ref-ont-array-patent" role="listitem">
<div class="csl-right-inline">[58] J.
R. Hyde, P. M. O. Bahamon, C. G. Brown, A. John, and P. R. Mackett,
<span>“Formation of array of membranes and apparatus therefor,”</span>
US20220023819A1, 2022 Accessed: Sep. 06, 2023. [Online]. Available: <a href="https://patents.google.com/patent/US20220023819A1">https://patents.google.com/patent/US20220023819A1</a></div>
</div>
<div class="csl-entry" id="ref-elements2019" role="listitem">
<div class="csl-right-inline">[59] Elements, <span>“eNPR – flow cell for nanopore
chip assembly and measurement instructions,”</span> 2019. <a href="https://elements-ic.com/wp-content/uploads/2019/07/eNPR-%E2%80%93-Nanopore-Chip-assembly-and-measurement-instructions.pdf">https://elements-ic.com/wp-content/uploads/2019/07/eNPR-%E2%80%93-Nanopore-Chip-assembly-and-measurement-instructions.pdf</a></div>
</div>
<div class="csl-entry" id="ref-thompson2010helicos" role="listitem">
<div class="csl-right-inline">[60] J.
F. Thompson and K. E. Steinmann, <span>“Single molecule sequencing with
a HeliScope genetic analysis system,”</span> <em>Current protocols in
molecular biology</em>, vol. 92, no. 1, pp. 7–10, 2010.</div>
</div>
<div class="csl-entry" id="ref-rhoads_pacbio_2015" role="listitem">
<div class="csl-right-inline">[61] A.
Rhoads and K. F. Au, <span>“<span>PacBio</span> <span>Sequencing</span>
and <span>Its</span> <span>Applications</span>,”</span> <em>Genomics,
Proteomics &amp; Bioinformatics</em>, vol. 13, no. 5, pp. 278–289, Oct.
2015, doi: <a href="https://doi.org/10.1016/j.gpb.2015.08.002">10.1016/j.gpb.2015.08.002</a>.</div>
</div>
<div class="csl-entry" id="ref-SMRTbells" role="listitem">
<div class="csl-right-inline">[62] Pacific BioSciences, <span>“Library prep and
barcoding kits,”</span> 2023. <a href="https://www.pacb.com/products-and-services/consumables/library-prep-and-barcoding-kits/">https://www.pacb.com/products-and-services/consumables/library-prep-and-barcoding-kits/</a>
(accessed Sep. 06, 2023).</div>
</div>
<div class="csl-entry" id="ref-wanunu2022zmw" role="listitem">
<div class="csl-right-inline">[63] F.
Farhangdoust, M. Alibakshi, F. Cheng, W. Liang, Y. Liu, and M. Wanunu,
<span>“Rapid identification of DNA fragments through direct sequencing
with electro‐optical zero‐mode waveguides,”</span> <em>Advanced
Materials</em>, vol. 34, p. 2108479, Jan. 2022, doi: <a href="https://doi.org/10.1002/adma.202108479">10.1002/adma.202108479</a>.</div>
</div>
<div class="csl-entry" id="ref-whiteford_seq_capability" role="listitem">
<div class="csl-right-inline">[64] N.
Whiteford, <span>“Global sequencing capability notes,”</span> 2022. <a href="https://41j.com/blog/2022/09/global-sequencing-capability-notes/">https://41j.com/blog/2022/09/global-sequencing-capability-notes/</a></div>
</div>
<div class="csl-entry" id="ref-ont_promethion" role="listitem">
<div class="csl-right-inline">[65] Oxford Nanopore Technologies,
<span>“<span>PromethION</span> 24（<span>Nanopore</span>）,”</span>
<em>Core Facility</em>. Accessed: Mar. 04, 2023. [Online]. Available: <a href="https://ashbi.kyoto-u.ac.jp/core-facility/equipment/promethion-24/">https://ashbi.kyoto-u.ac.jp/core-facility/equipment/promethion-24/</a></div>
</div>
<div class="csl-entry" id="ref-ont-2021-annual-report" role="listitem">
<div class="csl-right-inline">[66] Oxford Nanopore Technologies, <span>“Oxford
<span>Nanopore</span> <span>Annual</span> <span>Report</span>
2021.”</span> 2021. Available: <a href="https://nanoporetech.com/sites/default/files/s3/investors/reports/ONT%20Annual%20Report%202021.pdf">https://nanoporetech.com/sites/default/files/s3/investors/reports/ONT%20Annual%20Report%202021.pdf</a></div>
</div>
<div class="csl-entry" id="ref-kremer2020amc" role="listitem">
<div class="csl-right-inline">[67] M.
Kremer, J. Levin, and C. M. Snyder, <span>“Advance market commitments:
Insights from theory and experience,”</span> in <em>AEA papers and
proceedings</em>, American Economic Association 2014 Broadway, Suite
305, Nashville, TN 37203, 2020, pp. 269–273.</div>
</div>
</div>
