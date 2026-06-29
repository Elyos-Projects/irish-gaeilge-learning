# Competitive & Improvement Analysis — `irish-gaeilge-learning`

> Scope: review of PLAN.md v0.1.0 (+ TASKS.md skim) against the live competitive landscape, grounded
> in web research. Project = a free, openly-licensed, dialect-honest, native-speaker-reviewed Irish
> (Gaeilge) course as an Open Educational Resource and a template for minority-language revitalization.
> Date: 2026-06-29.

---

## 1. Correctness & completeness review of PLAN.md

The plan is unusually strong for a v0.1 minority-language effort. It already internalizes the two
failure modes that have actually damaged the leading commercial product (see §2): (a) synthetic/AI
voice masquerading as native pronunciation, and (b) dialect mishandling. The headline controls — "no
unreviewed AI-generated Irish ever ships," dialect parity as a *locked* decision, audio
provenance+consent manifest, and a hard CI licence/provenance gate — are the right spine. Findings:

**Strong / correct**
- **Dialect handling is the plan's best feature and is correctly framed.** Teaching *An Caighdeán
  Oifigiúil* for spelling/grammar while presenting **all three dialect groups (Munster/Connacht/Ulster)
  in labelled audio and never ranking them** is exactly the model the authoritative reference
  (Teanglann's 66,000-file pronunciation DB) and ABAIR both use, and it directly avoids the
  single-dialect lock-in that Rosetta Stone (Munster-only) and "Now You're Talking" (Ulster-only)
  impose. This is correct and is a genuine differentiator, not just compliance.
- **Native-speaker review as a hard gate**, with a mandatory second reviewer + back-translation for
  mutations (séimhiú/urú), the copula, and negation, is well-targeted: those are precisely the
  features generic LLMs and TTS mangle. Credibly evidence-based.
- **Voice-as-PII / GDPR posture** (signed consent, performer release, right to withdraw, adults-only,
  manifest with `speakerIsAdult`) is more rigorous than any commercial competitor publishes.
- **Non-extractive ethics**: CC BY-SA content, "complement not replacement for teachers/Gaeltacht
  immersion," community advisory with Gaeltacht representation, quality-over-quantity ("unreviewed =
  zero") — all align with revitalization ethics rather than data extraction.
- **Honest `verifiedNeed: false`** until a partner/cohort exists, with partner-independent M0
  foundations, is intellectually honest sequencing.

**Gaps / corrections needed**
1. **Pedagogy is under-specified relative to its own ambition.** The plan asserts CEFR/TEG alignment
   and "can-do" measurement but names **no L2 acquisition methodology** (e.g. comprehensible-input
   sequencing, spaced retrieval, task-based/communicative competence, frequency-based vocabulary
   selection). "Evidence-based pedagogy" is a stated guardrail but currently only the SRS export and
   pre/post can-do test operationalize it. Add a pedagogy-design task and a pedagogy reviewer
   credential distinct from the *linguistic* reviewer (a fluent speaker is not necessarily a trained
   L2 instructional designer).
2. **Dialect-*authenticity* of audio needs a sharper rule than dialect-*parity*.** Parity (all three
   present) is necessary but not sufficient. The plan should explicitly require that each dialect
   clip be produced/validated by a **speaker native to that dialect region** (a Connacht speaker
   reading "Munster" audio is parity without authenticity), and forbid open TTS (ABAIR) from being
   presented as native — TTS may be allowed only as explicitly-labelled synthetic support, never as
   the dialect exemplar. This is the most important missing precision (see summary).
3. **Audio supply is the real bottleneck and the plan knows it but under-resources it.** Common Voice
   Irish is CC0 but is *read sentences by mixed-proficiency volunteers*, not curated item-level,
   dialect-balanced, native pronunciation — so it cannot alone satisfy "native, dialect-authentic,
   per-item." Open question #2 flags this, but the roadmap should treat **funded native-speaker
   recording sessions (under a hard cap)** as a likely M1/M2 necessity, not an optional M4 nicety.
4. **TEG mapping risk.** TEG is itself the recognized CEFR-aligned Irish framework (Maynooth). Mapping
   "CEFR A1 → TEG band" is defensible, but the plan should cite the *published* TEG descriptors as the
   source of truth and have the mapping reviewed by someone TEG-familiar; otherwise the alignment claim
   is itself an accuracy risk.
5. **Caighdeán-vs-dialect spelling edge cases** (open question #7) are flagged but unresolved; this is
   an M0 policy detail, not a later one, because the very first A1 unit will hit it (e.g. common
   Munster/Ulster forms diverging from the standard).
6. **Extensibility to other minority languages is asserted, not architected.** The schema is generic
   enough, but nothing in M0–M3 actually abstracts "Irish-specific" assumptions (dialect taxonomy,
   mutation types, the three-dialect model). Recommend a small "minority-language profile" config
   concept early so the template claim is real (see §7).
7. **Sustainability owner / steward / maintainer all TBD.** Acknowledged honestly, but this is the
   single biggest execution risk: a review-gated project with no named native-speaker reviewer pool is
   blocked at its core. M1's "≥2 qualified reviewers" is the true critical path, ahead of tooling.
8. **Minor:** success metric 1 ("≥60% meet ≥80% of A1 can-dos") relies on self/teacher assessment with
   no inter-rater reliability plan; fine for a pilot but label it as such.

Overall: **complete and correct on licence/provenance/ethics; needs reinforcement on pedagogy method,
dialect *authenticity* (not just parity), audio-supply realism, and the template abstraction.**

---

## 2. Competitive landscape (researched, cited)

| Product | What it is | Strengths | Weaknesses (vs. our goals) |
|---|---|---|---|
| **Duolingo Irish** | Free/freemium gamified app; dominant by reach | Huge funnel; Irish among most-studied; gamification/retention | **Native recordings largely replaced by AI/synthetic voices 2022–2023**; TTS not trained on native Irish, fails broad/slender consonant distinction; documented grammar/translation errors; no dialect transparency; closed; part of "AI-first" 2025 strategy [1][2][3] |
| **Bitesize Irish** | Subscription online course | Clear, succinct explanations; audio on nearly every item; community calls/forum; honest dialect blog | **Munster-leaning** audio (only course teaching Munster well, but not balanced); subscription/closed; Caighdeán-based but not full three-dialect parity [4][5] |
| **Rosetta Stone Irish** | Premium immersion app | Polished immersion method; native-context learning | **Munster dialect only**; expensive "for what you get"; no dialect choice; closed [6] |
| **Teanglann.ie / Foclóir.ie** | Foras na Gaeilge dictionaries + pronunciation DB | **Authoritative**; free; **66,000 native sound files across Connacht/Ulster/Munster**; the gold standard for dialect audio reference | Reference works, **not a structured course**; reuse is reference-only (licence ≠ open reuse); no pedagogy/sequencing [7] |
| **ABAIR (TCD)** | Irish speech synthesis (TTS) | **State-of-the-art Irish TTS in all three dialects**; €2m+ state-funded; accessibility/education focus | **Synthetic, not native**; contributor terms grant ABAIR a licence but redistribution rights of generated audio unclear/likely restricted; cannot be presented *as native* [8][9] |
| **FutureLearn "Irish 101/102" (DCU)** | Free MOOC, diaspora-targeted | Free; university-backed; culture-rich; targets global diaspora | Very short (3 weeks × 3h); introductory only; platform-locked; not openly-licensed OER; not dialect-systematic [10][11] |
| **"Now You're Talking" (RTÉ/BBC NI)** | Legacy TV/book/audio beginner course | Real native audio; cultural grounding; historically important | **Ulster only**; dated (1990s); print/cassette legacy; copyrighted broadcaster material [12] |
| **Clozemaster Irish** | Cloze-in-context sentence trainer | Free tier; good for intermediate+ vocabulary-in-context (~1,400+ sentences) | Not a beginner course; no structured pedagogy; thin audio; no dialect framing [13] |
| **Drops / Transparent Language** | Vocabulary/commercial apps | Polished UX (Drops); breadth (Transparent) | Vocabulary-focused; closed; little/no dialect transparency; thin grammar [13] |
| **Gaeltacht immersion (Oideas Gael etc.) / university courses** | In-person/accredited | **Authentic, native, accredited, community-rooted** — the real benchmark | Cost, location, scarcity outside Ireland; not a free global on-ramp |

**Landscape summary:** the dominant mass-market product (Duolingo) has *regressed* on the exact axis
this project leads (native, dialect-authentic audio). The best dialect audio asset (Teanglann) is a
dictionary, not a course. No one occupies "free, openly-licensed, structured, dialect-balanced,
native-reviewed course." That is the white space.

---

## 3. Gaps we can fill

1. **Open + structured + dialect-balanced simultaneously.** Every competitor has at most two of the
   three: Teanglann (open-ish reference + 3 dialects, no course), Duolingo/Rosetta (course, but
   closed + single/AI dialect), FutureLearn (free + structured, but tiny + not OER + not dialect-systematic).
2. **Native, dialect-*authentic* audio as a first-class, provenance-tracked asset** — directly into the
   gap Duolingo opened by going synthetic.
3. **Adoptable, adaptable OER** (CC BY-SA) that teachers/ciorcail chomhrá/diaspora centres can localize
   for free — no competitor offers a reusable source-of-truth course.
4. **Offline / low-bandwidth packs** for rural Gaeltacht and diaspora — unaddressed by app competitors.
5. **Accessibility (WCAG 2.2 AA)** as a gate — commercial apps are inconsistent here.
6. **A reusable minority-language-revitalization template** — none of these generalize beyond Irish.

---

## 4. Differentiators to win (vs. a dominant-but-criticized Duolingo)

1. **"Real voices, real dialects" vs. Duolingo's AI voice.** The single sharpest wedge: Duolingo
   replaced native recordings with synthetic voices that mispronounce broad/slender consonants [1][2].
   Our hard rule — native, dialect-authentic, provenance-tracked audio, TTS never passed off as native —
   is a marketing-and-trust differentiator the community already cares about loudly.
2. **Dialect parity with honesty** — three labelled dialects, none ranked — vs. single-dialect
   commercial courses and Duolingo's inconsistent dialect mixing.
3. **Accuracy guarantee via human review gate** — "0 critical errors post-publication" as an actual
   gate, vs. crowd/AI-error-prone competitors.
4. **Genuinely open + adaptable** (CC BY-SA OER) — teachers can own and remix it; nobody else allows this.
5. **Non-extractive, community-governed** — Gaeltacht advisory, "complement not replacement," outcomes
   measured in learner attainment not engagement metrics.
6. **Trust/provenance as product** — every asset cites its source, licence, and reviewer; a credibility
   moat against AI-slop language content.

---

## 5. Claude API leverage (and the hard limits)

**Where Claude adds leverage (donated lane; all Irish output draft-only, native-reviewed):**
- **English-language scaffolding at scale**: lesson sequencing, CEFR/TEG-tagged unit structure,
  exercise *templates* (cloze/match/order/listen/dictation), can-do statement drafting, cultural-note
  first drafts (for cultural review).
- **Dialect-*aware* drafting support**: proposing candidate items/dialogues and *flagging* where a form
  is likely to diverge by dialect or trigger a mutation — surfaced as `UNCERTAIN:` notes for the
  reviewer, never as ground truth.
- **Grammar-explanation drafting** (séimhiú/urú, copula vs *bí*, negation) in plain English for the
  reviewer to correct — explanation prose, not authoritative Irish.
- **Pipeline/tooling**: schema authoring, validators, the licence/provenance CI gate, audio-manifest
  scaffolding, accessibility checks, link-rot/source-change watcher, Anki/CSV export, back-translation
  QA harness (machine back-translation as a *flag generator* for the human reviewer).
- **Reviewer-throughput multiplier**: pre-formatting reviewer checklists, diffing proposed vs. standard
  forms, drafting handoff packets so scarce native reviewers spend time judging, not formatting.

**Where Claude must NOT decide (hard boundaries — encode in the gate):**
- **Linguistic accuracy & dialect authenticity**: final correctness of any Irish word/sentence/grammar
  claim is **native-speaker/expert** decided. No Irish ships on model confidence.
- **Audio**: Claude (or any TTS, incl. ABAIR) must **never** be presented as native pronunciation.
  Synthetic audio only if licence permits *and* explicitly labelled synthetic — never the dialect
  exemplar.
- **Pedagogical soundness**: instructional-design choices reviewed by a qualified L2 educator, not
  asserted by the model.
- **Cultural respect**: cultural/heritage notes are human cultural-review gated (anti-stereotype/
  appropriation).
- **No fabricated Irish**: the model must flag uncertainty, not invent plausible-but-wrong forms;
  unresolved `UNCERTAIN:` flags block sign-off.
- **Dialect ranking / "best" form**: never — locked policy decision, not a model output.

---

## 6. Ten concrete optimizations

1. **Add a dialect-*authenticity* clause** to the policy: each dialect clip validated by a speaker
   native to that region; TTS labelled synthetic, never the exemplar. (Closes §1 finding 2.)
2. **Add a pedagogy-design task + distinct pedagogy-reviewer credential** (L2 instructional designer),
   separate from the linguistic reviewer; name the acquisition method (comprehensible input + spaced
   retrieval + task-based). (Closes §1 finding 1.)
3. **Promote funded native-recording sessions** from M4 to a costed, hard-capped option in M1/M2;
   budget per-item dialect-balanced recording now. (Closes §1 finding 3.)
4. **Build a "minority-language profile" config** (dialect taxonomy, mutation set, standard-vs-dialect
   policy) so the engine abstraction is real from M0. (Enables §7 template.)
5. **Frequency-rank A1 vocabulary** against an open Irish corpus (e.g. Gaois/Common Voice sentences,
   licence-checked) so the first 15+ items are the *highest-value* ones, not arbitrary.
6. **Integrate Teanglann/foclóir.ie as a reviewer *reference* tool** (not reused content) — a
   reviewer-side linking step to the authoritative 3-dialect pronunciation DB to speed verification.
7. **Ship a machine-back-translation QA harness** as an automated *flag generator* feeding the second
   reviewer for mutation/negation items (operationalizes the existing rule cheaply).
8. **Add an inter-rater reliability check** to the pilot can-do measurement (two assessors on a sample)
   so metric 1 is defensible.
9. **Publish a public "why not just use Duolingo/AI" trust page** citing the AI-voice regression — turns
   the differentiator into discoverable, shareable positioning for partner/learner acquisition.
10. **Stand up a lightweight reviewer-recruitment pipeline immediately** (university Irish departments,
    Conradh na Gaeilge, Gaeltacht co-ops) — the reviewer pool, not the tooling, is the binding
    constraint; treat it as M0-parallel outreach.

---

## 7. Parallel & perpendicular spin-offs

- **Minority-language-learning engine template (perpendicular, high-value).** Generalize the
  content-schema + dialect-profile + provenance-gate + review-workflow into a reusable
  `minority-language-course` engine. Irish becomes the reference implementation; Scottish Gaelic, Manx,
  Welsh, Cornish, Breton (and beyond Celtic) plug in via a profile. This is the project's biggest
  leverage beyond Irish itself.
- **`open-pronunciation-audio` (parallel).** A standalone open corpus of consented, dialect-labelled,
  provenance-tracked native pronunciation clips — useful far beyond this course (ASR, accessibility,
  other Celtic projects) and directly fills the gap Duolingo's AI-voice move created.
- **`world-folktales-open` (parallel content feed).** Reviewed, openly-licensed Irish folktales/dialogues
  as graded reading material — shared pipeline, cultural depth, ties revitalization to heritage content.
- **`literacy-from-zero` tie-in.** The CEFR-A1/can-do + accessibility + offline-pack machinery overlaps
  a from-zero literacy effort; share the renderer, a11y gate, and offline packer.
- **MCP server: "Irish review assistant."** An MCP tool exposing the schema, allow-list, dictionary
  *reference* links, and the back-translation flag harness to a reviewer's agent — speeds native
  reviewers without ever auto-approving Irish.
- **Gaeltacht-org partnership track.** Formalize outreach to Conradh na Gaeilge, Glór na nGael, Oideas
  Gael, Údarás/Foras na Gaeilge, Maynooth TEG, Gaeloideachas — both as reviewer supply and as the
  M2 adopting partner. This is also the ethics requirement (non-extractive governance), not just BD.

---

## 8. Open questions

1. **Partner & first cohort** (already #1 in plan) — which org requests/adopts, and what scope? Blocks M2.
2. **Audio supply economics** — what % can Common Voice CC0 realistically cover vs. funded native
   recording? What is the per-item recording budget, and who are the paid dialect-native speakers?
3. **ABAIR/TTS redistribution** — do ABAIR's terms permit redistributing generated clips at all? If not,
   is synthetic audio simply excluded? (Research suggests contributor terms favor ABAIR; redistribution
   rights of *outputs* look restricted — verify.)
4. **foclóir.ie / téarma.ie / Gaois reuse** — confirm reference-only vs. any reuse licence per dataset.
5. **Dialect-authenticity sourcing** — can we recruit native speakers from *each* of the three regions,
   or do we phase coverage by dialect with advisory input?
6. **Reviewer compensation model** — volunteer/academic/stipend? Determines M1 timing and feasibility.
7. **Pedagogy ownership** — who is the qualified L2 instructional designer, and is that the same or a
   different person from the linguistic reviewer?
8. **Template scope** — do we commit to the multi-language engine abstraction in v0.1 (cheap now,
   expensive to retrofit), or defer and risk Irish-specific lock-in?

---

### Sources
1. LetsLearnIrish — "You Won't Become Fluent in Irish With Duolingo" — https://letslearnirish.com/articles/duolingo-irish-language-learning/
2. The Geeky Gaeilgeoir (Duolingo critiques) — https://thegeekygaeilgeoir.wordpress.com/tag/duolingo/
3. "Why not Duolingo, and what to use instead?" (Gaeilge Chonamara) — https://gaeilgechonamara.com/why-not-duolingo-and-what-to-use-instead/
4. Bitesize Irish — Irish Dialects — https://www.bitesize.irish/irish-dialects/ ; review: https://www.mezzoguild.com/review-bitesize-irish-gaelic/
5. Bitesize Irish — "Diving into dialects" — https://www.bitesize.irish/blog/dialects-2/
6. Rosetta Stone Irish (Munster dialect; cost critiques) — https://www.rosettastone.com/learn-irish ; https://www.bitesize.irish/blog/rosetta-stone-forgaelic/
7. Teanglann.ie pronunciation database (66,000 files, 3 dialects; Foras na Gaeilge) — https://www.teanglann.ie/en/fuaim/ ; https://www.teanglann.ie/en/_about
8. ABAIR (TCD) speech synthesis, three dialects — https://abair.ie/ ; https://www.abair.tcd.ie/en/synthesis
9. ABAIR Terms of Service (contributor licence) — https://www.abair.tcd.ie/terms ; funding: https://www.gov.ie/en/department-of-rural-and-community-development-and-the-gaeltacht/press-releases/minister-calleary-approves-over-2-million-for-abair-project...
10. FutureLearn "Irish 101" (DCU) — https://www.futurelearn.com/courses/irish-language
11. Irish Times — DCU diaspora Irish MOOC — https://www.irishtimes.com/news/education/dcu-targets-global-diaspora-with-free-irish-language-course-online-1.3366014
12. "Now You're Talking" (RTÉ/BBC NI, Ulster dialect) — https://thegeekygaeilgeoir.wordpress.com/tag/now-youre-talking/
13. Clozemaster Irish — https://www.clozemaster.com/languages/learn-irish-online ; resource tier comparisons: https://foghlaimeoir.substack.com/p/my-irish-language-resource-tier-list
14. Mozilla Common Voice (CC0 speech corpus, incl. Irish) — https://commonvoice.mozilla.org/en/datasets
