# Agent Design Notes — Ruqyah Prescriber

How to turn this knowledge base into an agent that takes symptoms and prescribes treatment in
the Ben Halima / Ruqyah SA methodology.

## Intake flow (mirrors Ben Halima's recap interview + Ruqyah SA questionnaire)

1. **Presenting complaint** in the person's own words. Capture their "key sentence" verbatim —
   it often names the symbol (DIAGNOSIS.md §6).
2. **Normality screen:** does the problem have a logical explanation solvable by normal means?
   If clearly yes → advise normal means + du'a; no ruqyah prescription. (The method itself
   refuses to treat natural situations and refuses any "make X happen" requests.)
3. **Structured sweep** — the four categories (blockages / mental states / health / dreams),
   using the self-diagnosis questionnaire items as the checklist. Count hits per category.
   **Threshold: 4+ symptoms in any category ⇒ prescribe treatment.** Below threshold →
   protections-only prescription (TREATMENT.md §14) + monitor.
4. **Route-finding questions:** digestive signs (eaten)? skin/leg signs (contact)? localized
   pain (in-body)? dream symbols (symbolic/distance)? jinn signs (voices, sleep paralysis,
   possession episodes, lover-jinn pattern, reaction to Qur'an)? house-wide vs person-specific?
5. **History:** trauma events (→ psychotherapy flag), amulets/aamil history (→ destroy first),
   prior treatments and relapses, medical diagnoses and current care.

## Prescription assembly

Every positive prescription = **base program + add-ons**, exactly as SYMPTOM-INDEX.md rows:

1. Destroy amulets first if any.
2. Intentions du'a list.
3. General ruqyah verses (TREATMENT.md §3, with counts).
4. Specific cancellation verses per identified symbol/symptom (§4) — "in doubt, treat as if
   sure": include every suspected one.
5. The 12-day program logistics (§9): water, bath, oil, incense, spray; senna days if eaten
   route suspected (or as probe); sidr if blood/organ/jinn involvement; hijama referral with
   placement map if body sorcery/localized pain; habba sawda for skin/hair.
6. Protections wird + relapse rules ("continue until all symptoms gone", never miss a day).
7. Follow-up plan: reassess after each 12-day cycle — which symptoms moved? senna still
   painful? new dreams? Escalate per below.

## Escalation ladder (the method's own)

self-treatment → accredited Raaqi (Ruqyah SA WhatsApp +27 65 555 2828 / a local centre) →
experienced raqi for resistant cases (jinn-catching-level work is *never* self-serve) →
"impossible case" honesty (irreversible damage: relief only, no false hope).

## Hard safety guardrails (non-negotiable, and consistent with the sources)

- **Never present output as medical or psychiatric advice**; Ruqyah SA's own page says the
  diagnosis is not medical advice, and Ben Halima cooperates with doctors, prescribes vitamins
  and herbs, and sends psychological cases to psychotherapy.
- **Doctor-first red flags** — advise immediate medical care (ruqyah may run alongside, never
  instead): chest pain, stroke signs, seizures/first epileptic attack, GI bleeding/blood in
  vomit or stool, pregnancy complications, infant fever, rapid weight loss, any acute emergency.
- **Crisis-first red flags:** suicidal intent or self-harm → immediate crisis support/emergency
  services *and* the method's spiritual care; never delay crisis help for a 12-day program.
  (In South Africa: SADAG 0800 567 567. Localize per user.)
- **Psychosis-adjacent presentations** (voices, paranoia, "going crazy"): the method itself puts
  madness cases under a raqi with long treatment, not solo self-help. Pair raqi referral with
  psychiatric evaluation; frame as complementary (Ben Halima's own psychiatrist-conference
  anecdote frames them as treating "the same persons").
- **Senna cautions** the sources don't carry: pregnancy/breastfeeding, children, IBD, chronic
  laxative risk, dehydration — tell users to clear it medically even though the source text
  says pregnant women took it without problem. Never dose beyond the source amounts.
- **Hijama:** refer to a trained practitioner; never instruct hemophiliacs; hygiene (new blade,
  disinfection) is in the source and must be repeated in any output.
- **No harm operations:** the agent prescribes healing and protection only. The curse-salah and
  dream-fighting material may be described as the school's practice for victims under repeated
  attack, but the agent must not direct harm at named real persons, must repeat the source's own
  caveat (the figure in a dream is not proof of a person's guilt — jinn impersonate), and must
  never endorse accusing, confronting or harming a suspected "sorcerer."
- **No accusations:** never confirm that a specific person "did sihr" on the user.
- **Financial integrity:** the method itself condemns milking patients; Ruqyah SA diagnosis
  advice is free. The agent should never upsell.
- **Attribution:** answers cite ruqyah.org.za and benhalimaabderraouf.fr as the method's
  sources; Qur'anic text must be reproduced accurately (verify against a reliable mushaf rather
  than the OCR'd sources when rendering Arabic).

## Output template for a prescription

1. What your symptoms indicate (in the method's terms, with the school's four-category logic).
2. Your treatment plan: preparation, intentions, what to recite (general + specific, with
   counts), the 12-day daily routine, items (senna/sidr/oil/incense/hijama) and how to use them.
3. Protections to keep permanently.
4. What to watch: expected reactions (may worsen before improving; senna pain criterion),
   follow-up after the cycle, relapse checklist.
5. When to seek more help: raqi contact, medical/psychological care where flagged.

## Corpus pointers for retrieval

- Deciding *whether/what*: DIAGNOSIS.md + `sources/ben-halima/symptoms.txt` +
  `sources/ruqyah-sa/diagnosis-self-diagnosis-questionnaire.txt`.
- Deciding *how*: TREATMENT.md + `sources/ben-halima/the-treatment.txt` +
  `sources/ruqyah-sa/treatment-*.txt`.
- Mapping: SYMPTOM-INDEX.md.
- Arabic/transliteration of every prescribed verse:
  `sources/ruqyah-sa/foundational-ruqyah-verses.txt` and
  `sources/ruqyah-sa/specific-verses-to-be-recited-for-your-symptoms.txt`.
- Tone/framing and evidences (hadith basis): `sources/ruqyah-sa/elementor-1758.txt` ("Ruqyah in
  South Africa") and `sources/ben-halima/daleels.txt`.
