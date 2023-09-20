<head>
    <link rel="stylesheet" href="tufte.css"/>
  </head>
<p><span class="marginnote">Authors: Nava Whiteford, Andrew Heron, Leonard McCline, Ales Flidr, Jacob Swett.
NW performed the majority of research and analysis. AH provided guidance on research and analysis. LM provided research assistance and performed modeling. AF conducted expert interviews and edited the document. JS conceptualized the project.
    Funding was provided by <a href="https://www.openphilanthropy.org">Open Philanthropy</a> and organized by <a href="https://www.convergentresearch.org">Convergent Research.</a>
</span></p>
<div class="keywords">
<p>metagenomic sequencing | sample preparation | clinical microbiology |
single-molecule sequencing | technology roadmap</p>
</div>
<div class="corrauthor">
<p>newsgenomics.org</p>
</div>
<h1 class="unnumbered" id="introduction">Introduction</h1>
<p>The COVID-19 pandemic has revealed the limitations of our ability to
identify emerging pathogens. SARS-CoV-2 circulated in human populations
as an unknown pneumonia, undetected by standard-of-care diagnostics, for
an estimated 4-8 weeks <span class="citation"
data-cites="Pekar2021"></span> before a novel coronavirus was identified
in infected samples by unbiased <span data-acronym-label="MGS"
data-acronym-form="singular+short">MGS</span> <span class="citation"
data-cites="Zhu2020"></span>. This delay lost valuable time for
addressing the pandemic, which has resulted in millions of deaths and
trillions of dollars in economic costs <span class="citation"
data-cites="glennerster2023calculating"></span>.</p>
<p>Imagine if, instead, every clinician and patient around the world had
access to a simple device capable of detecting any virus, bacterium or
other pathogen causing disease in a symptomatic patient. Such a world
would be much better positioned to diagnose and treat infectious disease
and to detect novel emerging pathogens before they cause a devastating
pandemic.</p>
<p>MGS has demonstrated the potential to become such a near-universal
diagnostic <span class="citation"
data-cites="Chiu2019 schlaberg_viral_2017 Zinter2019 Charalampous2019"></span>
and is already saving lives by informing clinical decisions for a
variety of symptoms and sample types <span class="citation"
data-cites="edgeworth2023respiratory"></span>. However, it is not yet
ready for prime time: complex workflows and high costs prevent
widespread adoption <span class="citation"
data-cites="Chiu2019"></span>. As a result, MGS has had a limited impact
on the management of the pandemic at the point of care. Therefore,
regardless of their value for public health, sequencing-based assays
have to become comparable with the standard of care to be considered a
viable alternative.</p>
<p>While isothermal amplification methods and other new modalities
gained in use during COVID-19, assays based on the <span
data-acronym-label="qPCR" data-acronym-form="singular+short">qPCR</span>
were by far the most widely used molecular diagnostic. Currently, qPCR
is considered the gold standard for the detection of respiratory
pathogens, offering high sensitivity, specificity, and a rapid
turnaround time <span class="citation" data-cites="WHO2011"></span>. In
this paper, we use qPCR as a benchmark and outline the specifications
for a clinical MGS device for viral respiratory infection diagnostics.
Having outlined these specifications, we discuss the most promising
candidate technologies that may meet these requirements.</p>
<h1 class="unnumbered"
id="motivation-pandemic-early-detection">Motivation: pandemic early
detection</h1>
<figure>
<img src="images/threatnet_architecture.jpeg" />
<figcaption>Proposed architecture of a network of MGS early detection
sites in emergency departments. Source: Sharma et al. 2023 <span
class="citation" data-cites="sharma2023threat"></span>, with permission
from the authors.</figcaption>
</figure>
<p>MGS can be leveraged for early detection in a number of ways,
including sequencing sites searching for emerging pathogens in
wastewater and waterways <span class="citation"
data-cites="Consortium2021"></span>, or strategic testing of "sentinel"
populations. While these approaches should certainly form an important
part of a layered early detection system, we focus this roadmap report
solely on the vision of MGS deployed widely at the point of care for
detection of pathogens in human respiratory samples. The key reasons for
this focus are:</p>
<ul>
<li><p>Distinguishing between signal and noise is likely to be easier in
human respiratory samples than in environmental ones.</p></li>
<li><p>Early detection of pathogens will only be enabled when MGS is
deployed at a relatively large scale <span class="citation"
data-cites="sharma2023threat"></span>. If MGS proves to be clinically
useful and cost-effective, it can scale up naturally within the current
health-economic system <span class="citation"
data-cites="Topol2023"></span>, without the need for continued public or
philanthropic support above those of current diagnostics.</p></li>
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
<h1 class="unnumbered"
id="current-practice-and-near-term-potential">Current practice and
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
According to a WHO report <span class="citation"
data-cites="WHO2011"></span>, real-time PCR devices have led to wider
adoption of molecular diagnostics due to their improved rapidity,
sensitivity, reproducibility and the reduced risk of carry-over
contamination. With the exception of sensitivity, all of these problems
currently still plague MGS.</p>
<figure>
<img src="images/cepheid.jpeg" />
<figcaption>A Cepheid GeneXpert device. Source: MSF (2022) <span
class="citation" data-cites="msf2022access"></span>.</figcaption>
</figure>
<p>A concrete example of this success is the Cepheid GeneXpert <span
class="citation" data-cites="GeneXpertSystem"></span> device. Originally
developed for the detection of anthrax, it has been adapted to many
other infectious diseases following collaboration between Cepheid and
international organizations and philanthropic bodies. Through successive
rounds of cost-optimization, the device arrived at a point where it
became practical even in developing countries for testing infections
such as tuberculosis or HIV. This resulted in an overall installed base
of some 22,000 devices even prior to the COVID pandemic <span
class="citation" data-cites="CepheidNewsReleaseArchive"></span>, which
increased to 40,000 between 2019 and 2022 <span class="citation"
data-cites="GenomeWeb2022"></span>. This enabled relatively rapid
development of primers for testing the presence of SARS-CoV-2 in
clinical samples without the need for developing novel
infrastructure.</p>
<p>PCR devices can also test for multiple pathogens or genes (such as
those conferring antimicrobial resistance) in parallel. The BioFire
FilmArray <span class="citation"
data-cites="BioFireDiagnostics2016"></span>, for instance, offers
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
<div class="table*">
<table>
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
<td style="text-align: left;"><span class="citation"
data-cites="novaSeq6000"></span></td>
</tr>
<tr class="even">
<td style="text-align: left;">Illumina MiSeq</td>
<td style="text-align: left;">SBS</td>
<td style="text-align: left;">1.5 hr</td>
<td style="text-align: left;">1.5 hr</td>
<td style="text-align: left;">No</td>
<td style="text-align: left;">$30</td>
<td style="text-align: left;"><span class="citation"
data-cites="miseqSpecs"></span></td>
</tr>
<tr class="odd">
<td style="text-align: left;">Illumina iSeq</td>
<td style="text-align: left;">SBS</td>
<td style="text-align: left;">1.5 hr</td>
<td style="text-align: left;">2 hr</td>
<td style="text-align: left;">No</td>
<td style="text-align: left;">$50</td>
<td style="text-align: left;"><span class="citation"
data-cites="iseq100"></span></td>
</tr>
<tr class="even">
<td style="text-align: left;">Ion Torrent GeneStudio S5</td>
<td style="text-align: left;">Ion Semi. SBS</td>
<td style="text-align: left;">2 hr</td>
<td style="text-align: left;">10 min</td>
<td style="text-align: left;">No</td>
<td style="text-align: left;">$50</td>
<td style="text-align: left;"><span class="citation"
data-cites="ionGeneStudio ion520Chip quail2012 heger2015"></span></td>
</tr>
<tr class="odd">
<td style="text-align: left;">ONT MinION</td>
<td style="text-align: left;">SM Nanopore</td>
<td style="text-align: left;">10 min</td>
<td style="text-align: left;">&lt;1 hr</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: left;">$250</td>
<td style="text-align: left;"><span class="citation"
data-cites="nanoporeKits greninger2015 tyson2020 nanoporeUpdate2023"></span></td>
</tr>
<tr class="even">
<td style="text-align: left;">SeqLL (Helicos)</td>
<td style="text-align: left;">SMO SBS</td>
<td style="text-align: left;">0 min</td>
<td style="text-align: left;">7 d</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: left;">$50</td>
<td style="text-align: left;"><span class="citation"
data-cites="seqll2017brochure"></span></td>
</tr>
<tr class="odd">
<td style="text-align: left;">Pacific Biosciences Sequel II</td>
<td style="text-align: left;">SMO SBS</td>
<td style="text-align: left;">3 hr</td>
<td style="text-align: left;">&lt;1 hr</td>
<td style="text-align: left;">No</td>
<td style="text-align: left;">$50</td>
<td style="text-align: left;"><span class="citation"
data-cites="sequelSystems"></span></td>
</tr>
</tbody>
</table>
</div>
<h2 class="unnumbered" id="current-sequencing-landscape">Current
sequencing landscape</h2>
<p>As <a href="#tab:platform-comparison" data-reference-type="autoref"
data-reference="tab:platform-comparison">[tab:platform-comparison]</a>
(supplementary note) illustrates, no sequencing device currently comes
close to meeting these specifications. Sensitivity itself is already
achievable with sufficient sequencing depth (see <a
href="#sec:requirements">section on platform requirements</a>), but
incompatible with the other requirements of cost and time-to-answer.
Workflows involve complex sequential steps in both sample and library
preparation and typically require hours of work by trained experts.
Automated and integrated solutions such as VolTRAX for nanopore
sequencing <span class="citation" data-cites="voltrax"></span> or
NeoPrep for Illumina <span class="citation" data-cites="neoprep"></span>
are only available at high costs for specialized laboratories. Cost per
sample can be reduced below $10 only by sequencing many samples in
parallel, which is not practical in the point-of-care context, as this
step introduces a significant delay in time-to-answer.</p>
<p>The need for rapid results speaks against the majority of sequencing
platforms based on <strong>colony-based approaches</strong>. The cluster
generation step alone takes at least 60 minutes <span class="citation"
data-cites="whiteford2023cluster"></span>. In addition, this approach
requires a large set of reagents that would add significant complexity
and cost to the design of a sample-to-answer system.</p>
<p>Although the emergence of new companies (e.g. MGI <span
class="citation" data-cites="MGITech2023"></span>, Singular Genomics
<span class="citation" data-cites="SingularGenomics2023"></span>) is
likely to decrease consumable and device costs by driving down margins
and enabling innovations, the new players are unlikely to change this
fundamental limitation. To our knowledge, the most serious attempt at
decreasing the time requirements is the use of Lighting Terminators
<span class="citation" data-cites="GenomeWeb2009"></span>.</p>
<p>While this and other future innovations could make some colony-based
approaches viable, a more natural category to focus on is that of
<strong>single-molecule approaches</strong>. Single-molecule approaches
have the advantage of potentially minimal library preparation and
compatibility with a real-time readout, with results delivered in
minutes following sample and library preparation. The two main
approaches in this category as of 2023 are nanopore sequencing and
single-molecule optical (SMO) sequencing.</p>
<p>As of 2023, the cheapest available instrument for runs on single
samples is <span data-acronym-label="ONT"
data-acronym-form="singular+short">ONT</span>’s Flongle, whose
consumables sell for $90 <span class="citation"
data-cites="flongle"></span> and likely costs around $50 to make <span
class="citation" data-cites="Whiteford2022notes_on_nanopores"></span>.
Optimized clinical workflows utilizing real-time sequencing with <span
data-acronym-label="ONT" data-acronym-form="singular+short">ONT</span>’s
MinION can achieve a time-to-answer of 6 hours <span class="citation"
data-cites="Charalampous2019"></span>. This is driven primarily by
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
technology development goals</a> and what steps might be necessary to <a
href="#sec:accelerating">direct and accelerate this
development</a>?</p></li>
</ul>
<h2 class="unnumbered" id="sec:sample-to-answer">Towards a
sample-to-answer system</h2>
<p>Perhaps the greatest contrast between sequencing and PCR tests today
lies in the complexity of workflows. As previously mentioned, even
workflows optimized for the ICU setting require a clinical microbiology
laboratory to execute <span class="citation"
data-cites="edgeworth2023respiratory"></span>. Interviews with
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
estimated at $10 <span class="citation"
data-cites="CambridgeConsultants2019"></span> and marketed at prices
typically exceeding $20.</p>
<figure id="fig:cartridge">
<img src="images/IMG_1893.jpeg" />
<p>. <span id="fig:cartridge" label="fig:cartridge"></span></p>
<figcaption>A sketch of a sample and library preparation cartridge for a
fixed respiratory MGS workflow. Originally appeared in <span
class="citation"
data-cites="Whiteford2022Metagenomic"></span>.</figcaption>
</figure>
<p>While achieving the same simplicity for MGS may seem like a tall
order, it is important to note that currently available cartridges have
been designed to be versatile and serve a number of applications. For
MGS applications, workflows can be optimized for specific sample types
such as nasopharyngeal, upper nasal, or saliva, along with a consistent
input volume and exclusive RNA sequencing. If sequencing is stripped
down to its bare essentials (see <a href="#fig:cartridge"
data-reference-type="autoref"
data-reference="fig:cartridge">[fig:cartridge]</a>), the complexity need
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
undue bias <span class="citation"
data-cites="regnault2021deep"></span>.</p>
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
indication of infection <span class="citation"
data-cites="Zinter2019 Chiu2019"></span>.</p>
<p>In clinical practice, cutoffs for clinical significance will likely
be determined for each pathogen or pathogen class as information about
typical abundance in non-infected individuals is accumulated. As an
example, in a pulmonary sample study, Zinter et al. used two criteria: a
normalized score of reads per million (rpm) and the deviation in
abundance from other samples in the cohort and determined the cutoff for
bacteria as a deviation of <span
class="math inline"><em>Z</em> ≥ 2</span> or <span
class="math inline">10</span> rpm, and for viruses and fungi as <span
class="math inline">1</span> rpm <span class="citation"
data-cites="Zinter2019"></span>. Miller et al. developed threshold
criteria based on the detection of non-overlapping reads from <span
class="math inline"> ≥ 3</span> distinct genomic regions <span
class="citation" data-cites="Miller2019"></span>.</p>
<div class="table*">
<table>
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
<td style="text-align: left;"><span
class="math inline">1 × 10<sup>−7</sup></span></td>
<td style="text-align: left;"><span
class="math inline">1.8 × 10<sup>3</sup></span></td>
<td style="text-align: left;">1</td>
<td style="text-align: left;">0.1</td>
<td style="text-align: left;">0.2</td>
<td style="text-align: left;">39.1</td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><span
class="math inline">1 × 10<sup>−6</sup></span></td>
<td style="text-align: left;"><span
class="math inline">1.8 × 10<sup>4</sup></span></td>
<td style="text-align: left;">10</td>
<td style="text-align: left;">1</td>
<td style="text-align: left;">2</td>
<td style="text-align: left;">35.8</td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><span
class="math inline">1 × 10<sup>−5</sup></span></td>
<td style="text-align: left;"><span
class="math inline">1.8 × 10<sup>5</sup></span></td>
<td style="text-align: left;">100</td>
<td style="text-align: left;">10</td>
<td style="text-align: left;">25</td>
<td style="text-align: left;">32.4</td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><span
class="math inline">1 × 10<sup>−4</sup></span></td>
<td style="text-align: left;"><span
class="math inline">1.8 × 10<sup>6</sup></span></td>
<td style="text-align: left;">1000</td>
<td style="text-align: left;">100</td>
<td style="text-align: left;">250</td>
<td style="text-align: left;">29.1</td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><span
class="math inline">1 × 10<sup>−3</sup></span></td>
<td style="text-align: left;"><span
class="math inline">1.8 × 10<sup>7</sup></span></td>
<td style="text-align: left;">10000</td>
<td style="text-align: left;">1000</td>
<td style="text-align: left;">2496</td>
<td style="text-align: left;">25.7</td>
<td style="text-align: left;"></td>
</tr>
</tbody>
</table>
</div>
<h2 class="unnumbered" id="throughput">Throughput</h2>
<p>With these goals in mind, what sequencing depth is required? PCR
tests are characterized by a high sensitivity, or very low limit of
detection (LoD): in principle, they can detect the presence of a target
fragment with only a handful of copies present in a sample. Sequencing a
human clinical sample can obviously achieve very high levels of
sensitivity: a sequencing run of terabases (Tb) on a single sample
should readily detect even pathogens that are very low in abundance. At
a depth of 40M reads per sample, MGS was shown to consistently achieve a
sensitivity on par with if not greater than PCR <span class="citation"
data-cites="jumpcode Whiteford2022Metagenomic"></span>. However, when
the requirements of cost and time-to-answer are added, practical
sensitivity of sequencing has to be determined.</p>
<p>PCR has a key advantage over sequencing: because PCR targets a short,
unique region of a genetic sequence, it is <em>insensitive to background
material</em>. A high fraction of human material (mostly <span
data-acronym-label="rRNA" data-acronym-form="singular+short">rRNA</span>
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
as low as tens of copies/mL found in more than 1% of cases <span
class="citation" data-cites="Arnaout2020"></span>.</p>
<p>The expected number of reads from the pathogen of interest is a
straightforward function of the relative fraction of the pathogen in the
sample, and the number of fragments sequenced in a run. For example, if
one fragment in 100 thousand belongs to the pathogen and 1 million reads
are obtained, we should expect to see 10 reads on average <a href="#fn1"
class="footnote-ref" id="fnref1"
role="doc-noteref"><sup>1</sup></a>.</p>
<figure id="fig:jumpcode">
<img src="images/jumpcode.jpg" />
<figcaption>Scatter plot of target fraction and Ct data that form the
basis of predicted Ct in Table 2 based on data from <span
class="citation" data-cites="jumpcode"></span>. Originally appeared in
<span class="citation"
data-cites="Whiteford2022Modeling"></span>.</figcaption>
</figure>
<p>One way to think about the requirements for a MGS diagnostic is to
draw a rough correspondence with the familiar <span
data-acronym-label="Ct" data-acronym-form="singular+short">Ct</span>
values from PCR for given sample characteristics. As a heuristic, Ct
values of 25 represent high viral load and values over 35 are of
disputed clinical relevance <span class="citation"
data-cites="healy2021impact"></span>. The relationship between viral
load, Ct values and fraction of reads have been by a number of empirical
studies for SARS-CoV-2 <span class="citation"
data-cites="babiker_metagenomic_2020 jumpcode"></span>. <a
href="#table:target_reads" data-reference-type="autoref"
data-reference="table:target_reads">[table:target_reads]</a> shows the
relationship between the real fraction of target nucleic acids in a
sample, measured Ct values and expected target reads based on data
obtained from <span class="citation" data-cites="jumpcode"></span>.</p>
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
depth <span class="citation" data-cites="orlandi2020hiv"></span>.</p>
<p>It is worth noting that these requirements could potentially be
dramatically reduced by depleting host nucleic acids. Depletion methods
remove known non-target nucleic acids (e.g., host material) from a
sequencing library and doing so can reduce read depth requirements and
increase detection sensitivity for pathogen nucleic acid <span
class="citation" data-cites="jumpcode"></span>. When sequencing RNA
libraries, highly repetitive ribosomal RNA (rRNA) can constitute 60-95%
of a sample, making it a prime target for depletion. As indicated by
interviews with practitioners, Qiagen’s FastSelect <span
class="citation" data-cites="Qiagen"></span> is currently the most
viable alternative, removing &gt;95% rRNA (host and bacterial) in 14
minutes. There are yet to be sufficient studies examining the
effectiveness of FastSelect across various sample types, but in a case
where FastSelect was applied to <span data-acronym-label="CSF"
data-acronym-form="singular+short">CSF</span> samples, practitioners
report a 10x reduction in required read depth requirements (from 10-20M
to 1-2M).</p>
<p>Unfortunately, FastSelect costs &gt;$50/sample <span class="citation"
data-cites="Qiagen"></span>, although labs have reported <span
class="citation" data-cites="RapidResponse2021"></span> similar
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
object of study. However, our simulations <span class="citation"
data-cites="whiteford2022longreads"></span> suggest that for the task of
correctly classifying a known virus, or detecting a high abundance of
unknown material, read length and accuracy requirements are
comparatively modest. In addition, decrease in one can be compensated by
an increase in the other.</p>
<p>For example, for read length, we estimate that a <strong>read length
of only 25 <span data-acronym-label="bp"
data-acronym-form="singular+short">bp</span></strong> and
<strong>single-base accuracy of 95%</strong> are sufficient for unique
pathogen detection, given sufficient sequencing depth <span
class="citation" data-cites="whiteford2022longreads"></span>. In terms
of single-base accuracy, highly sensitive detection of emerging
pathogens has been demonstrated in the field with error rates as high as
20-30% with early versions of long-read nanopore sequencing <span
class="citation" data-cites="quick2016real"></span>. The fact that
requirements for pathogen detection diverge so significantly from that
for research applications has key implications for development
directions, the subject of the next section.</p>
<figure id="fig:read_length">
<img src="images/read length.png" />
<p>. <span id="fig:read_length" label="fig:read_length"></span></p>
<figcaption>Relationship between read length, accuracy, and unique
alignment to the SARS-CoV-2 genome. Originally appeared in <span
class="citation"
data-cites="whiteford2022longreads"></span></figcaption>
</figure>
<h1 class="unnumbered" id="sec:dev-goals">Development directions</h1>
<p>Having determined these targets for sequencing platforms, we can now
formulate concrete development goals for the previously mentioned
candidate single-molecule platforms, focusing on nanopore and
single-molecule optical (SMO) sequencing. While these two platform
classes have a different profile of upsides and downsides for MGS, they
share a key advantage in minimal time required for library preparation.
ONT’s rapid sequencing kit <span class="citation"
data-cites="ont2023rapidkit"></span> requires less than 10 minutes, and
some SMO platforms do not require any library preparation after lysis
and nucleic acid extraction <span class="citation"
data-cites="seqll2017brochure whiteford2022reticulatech"></span>.</p>
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
interpretable <span class="citation"
data-cites="wang2021nanopore"></span>.</p>
<p>In a research context, the primary advantage of nanopore sequencing
over other platforms lies in its long reads. Average read lengths in a
standard protocol exceed 1,000 bp and the longest recorded reads exceed
a million base pairs <span class="citation"
data-cites="loose2019whale"></span>. In the MGS context, long reads
provide limited utility and, for nanopore sequencing in particular,
present an active hindrance, as longer fragments occupy pores for a
longer time period. There is therefore a direct trade-off between read
length and number of reads: to a first approximation, the number of
fragments sequenced scales linearly with the inverse of average read
length.</p>
<p>A logical conclusion is that for MGS, sample preparation should
include a fragmentation step to reduce the average fragment size and
thus increase the chance of detecting a low-abundance pathogen. ONT
MinION has 512 active channels working in parallel <span
class="citation" data-cites="ont_minion"></span>. With sufficient
saturation and the standard translocation speed of approximately 400
bp/s, we need an average fragment length of some 700 bp to get 1M reads
in an hour of sequencing, and 70 bp to achieve 10M reads. The cheapest
device, Flongle, has approximately 100 active channels, implying some 2
million reads in 60 minutes of sequencing.</p>
<p>This implies that for a sufficiently fragmented sample, nanopore
platforms already meet the key requirements of fast time-to-answer,
sufficient throughput, and relatively simple library preparation.
However, at present, the greatest barrier for a nanopore-based
diagnostic platform is the high <span data-acronym-label="COGS"
data-acronym-form="singular+short">COGS</span> of consumables. This
cost, in turn, is primarily driven by the cost of manufacturing nanopore
arrays, whose cost scales linearly with chip area <span class="citation"
data-cites="Whiteford2022notes_on_nanopores"></span>. It follows that
the two available levers for cost-optimization are reducing the required
area or using lower-cost materials or fabrication procedures.</p>
<p>From published patents <span class="citation"
data-cites="ont-array-patent"></span>, it is possible to infer that the
design employed by ONT presently requires the use of non-standard
fabrication facilities able to process novel materials, such as <span
data-acronym-label="MEMS" data-acronym-form="singular+short">MEMS</span>
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
by the companies Nanion and Elements <span class="citation"
data-cites="elements2019"></span>. While there is technical uncertainty
as to whether this approach can scale beyond 16 channels, scaling to
some 100 channels with this approach might be feasible.</p>
<p>While it is difficult to predict which approach will yield the best
results, we should expect that a ground-up reimplentation that aims for
cost-optimization should achieve a much lower cost point. Although it is
unclear whether any of these will be perceived as attractive by ONT, a
number of companies, including Qitan, Genia or Nanion have entered the
market and this trend is poised to continue.</p>
<div class="table*">
<p><span id="table:sequencing_capacity"
label="table:sequencing_capacity"></span></p>
<table>
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
<h2 id="single-molecule-optical-platforms">Single-molecule optical
platforms</h2>
<p>Single-molecule optical technologies were brought to the market by
Helicos <span class="citation" data-cites="thompson2010helicos"></span>
(now defunct) and <span data-acronym-label="PacBio"
data-acronym-form="singular+short">PacBio</span> <span class="citation"
data-cites="rhoads_pacbio_2015"></span>. Considering this class of
technologies as a candidate platform may be surprising, as they have
generally been embodied as costly, "fridge-sized" instruments with long
library preparation (&gt;3 hours). However, this is driven not by the
fundamental needs of the platform, but rather by the market demand for
high single-base accuracy and long reads. If these requirements are
relaxed, <span data-acronym-label="SMO"
data-acronym-form="singular+short">SMO</span> approaches can achieve
very simple sample preparation <span class="citation"
data-cites="seqll2017brochure"></span> and a low cost of consumables
<span class="citation"
data-cites="whiteford2022reticulatech"></span>.</p>
<p>Commonly employed library preparation techniques take many hours and
are not a good fit for point-of-care MGS. However, the SMRTBells library
preparation kit <span class="citation" data-cites="SMRTbells"></span>
was introduced to drive accuracy to &gt;99.9% and read length to  15 kb,
neither of which is required for MGS. Without these requirements,
library preparation for optical methods can be as fast as for nanopore
sequencing ( 5 minutes) and still achieve accuracies upwards of 80%
combined with a compensating read length of hundreds of bases.
Similarly, approaches derived from the Helicos technology have been
demonstrated to work with minimal library preparation with error rates
below 5% and read lengths exceeding 25 bp, making them a potential
candidate for a MGS device <span class="citation"
data-cites="whiteford2022reticulatech"></span>.</p>
<p>In terms of throughput, the sequencing step alone can be achieved in
a fraction of the time required for nanopore sequencing, as SMO
approaches can use many more sensors working in parallel. In PacBio
sequencing, imaging more than 1 million fragments in parallel is common
<span class="citation" data-cites="sequelSystems"></span> and, with a
speed of 10 nucleotides per second, the run can be finished in less than
a minute for the read lengths required for MGS. Another key advantage of
an optical approach relative to nanopore sequencing is that it is
compatible with a less complex chip and presents a clearer path to a
consumable cost of $10 or less <span class="citation"
data-cites="whiteford2022reticulatech"></span>.</p>
<p>A key challenge to address will be the optimization of device cost,
currently exceeding $500,000 in the case of PacBio instruments. However,
achieving a cost lower than $10,000 appears feasible if instrumentation
is reimagined from the ground up. For example, photonic chips need not
be monolithically integrated. Consumer-grade cameras available for $300
have resolution sufficient for the accuracy requirements of an MGS
diagnostic. Throughput in a low-cost platform will be limited by
compatibility with low-cost cameras, but the goal of 1-10 million
sensing regions (and hence reads) appears achievable.</p>
<p>A particularly promising emerging approach is that of electro-optical
zero-mode waveguides <span class="citation"
data-cites="wanunu2022zmw"></span>, which may enable substantially lower
input requirements, potentially obviating the need for random
amplification of nucleic acids in a sample.</p>
<figure>
<img src="images/IMG_1895.jpeg" />
<figcaption>Sketch of a cost-optimized single-molecule optical platform.
Originally appeared in <span class="citation"
data-cites="whiteford2022reticulatech"></span>.</figcaption>
</figure>
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
<p>By our estimates, more than half of global sequencing capacity in
terms of the number of bases sequenced annually is accounted for by
Illumina NovaSeq alone <span class="citation"
data-cites="whiteford_seq_capability"></span>. NovaSeq is a $1 million
instrument that yields up to 6 Tb of data per run with an error rate on
the order of 0.1%.A single run can cost more than $5,000. This large
share of sequencing capacity is accounted for by only some 1500
instruments in large laboratories <span class="citation"
data-cites="whiteford_seq_capability"></span>.</p>
<p>Another key player, ONT, is known for its relatively affordable,
miniaturized devices such as the MinION or Flongle. In 2021, however,
fully 55.7% of ONT’s revenue was generated by its 67 PromethION <span
class="citation" data-cites="ont_promethion"></span> instruments <span
class="citation" data-cites="ont-2021-annual-report"></span>, each of
which can generate up to 12 Tb of data, with device costs ranging from
$225,000 to $450,000.</p>
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
commitments <span class="citation" data-cites="kremer2020amc"></span>
may be appropriate here, as the target product profile is readily
definable in this context, and achievable in a timeframe of less than 5
years. At present, building a fab from scratch, which could pave the way
towards low-cost nanopore devices, is an endeavor in the hundreds of
millions of dollars and is difficult to justify given the lack of a
credible demand signal. However, at volumes comparable to qPCR
diagnostics (&gt;1M units a month), such investment could be justified.
Tools such as advanced market commitments, as well as credible signals
of interest in an MGS diagnostic platform from national and
international organizations, could pave the way towards such
investments.</p></li>
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
<div class="acknowledgements">
<p>This project was funded by Open Philanthropy, whose support we are
grateful for. We are grateful to Rahul Arora, Jake Pencharz and Janvi
Ahuja for help on the project.</p>
</div>
<h1 class="unnumbered" id="bibliography">Bibliography</h1>
<h1 id="sensitivity">Sensitivity</h1>
<figure id="fig:heat-map">
<img src="images/predicted Ct vs at least one.png" />
<figcaption>Heat map for probability of at least one read. Expected
number of reads based on given target fraction (predicted Ct on x-axis)
and sequencing depth (y-axis ranging from 100,000 to 5,000,000
reads).</figcaption>
</figure>
<aside id="footnotes" class="footnotes footnotes-end-of-document"
role="doc-endnotes">
<hr />
<ol>
<li id="fn1"><p>This discussion focuses on expected reads for
simplicity. A more informative metric may be the probability of at least
n reads. <a href="#fig:heat-map" data-reference-type="autoref"
data-reference="fig:heat-map">[fig:heat-map]</a> in the appendix shows
the probability of at least one read as a function of the target’s
relative abundance and number of reads obtained.<a href="#fnref1"
class="footnote-back" role="doc-backlink">↩︎</a></p></li>
</ol>
</aside>