# Ruqyah Treatment Knowledge Base

Research archive on **Ruqyah South Africa** (ruqyah.org.za) and the scholar whose method they
follow, **Sheikh Ben Halima Abderraouf**. Built as the source-of-truth resource for a future
agent that takes a person's symptoms and prescribes a Ruqyah treatment plan following this
school's methodology.

## Who they follow

Ruqyah South Africa is a network of ruqa (Ruqyah practitioners) who studied and practice under
**Sheikh Ben Halima Abderraouf** (born Tunis, 1967) and are part of his international group of
ruqa. They state: *"Our method of Ruqyah is primarily that of Sheikh Abder Rauf Ben Halima, and
we are associated to his international group of Ruqa... We have adopted his method primarily,
and adapted it to the South African context."* Full profile in [SCHOLAR.md](SCHOLAR.md).

## File map

| File | What it is |
|------|-----------|
| [SCHOLAR.md](SCHOLAR.md) | Who Ben Halima is, his books, his network, Ruqyah SA's relationship to him |
| [DIAGNOSIS.md](DIAGNOSIS.md) | The complete diagnostic framework: the three afflictions, the four symptom categories, the self-diagnosis questionnaire, sorcery types, dream-symbol decoding, differential rules |
| [TREATMENT.md](TREATMENT.md) | The complete treatment methodology: the 12-day program, verse lists with counts, senna/sidr/hijama/oil protocols, jinn removal, house treatment, prevention, relapse checklist |
| [SYMPTOM-INDEX.md](SYMPTOM-INDEX.md) | The lookup table an agent needs: presentation → indicated affliction → prescription components |
| [AGENT-NOTES.md](AGENT-NOTES.md) | Design notes for building the prescriber agent: intake flow, decision rules, escalation and safety guardrails |
| [SOURCES.md](SOURCES.md) | Annotated index of every online source, with the local copy each one maps to |
| `sources/ruqyah-sa/` | Full text of every diagnosis/treatment page on ruqyah.org.za (fetched 2026-08-20) |
| `sources/ben-halima/` | Full text of Ben Halima's English articles from benhalimaabderraouf.fr — including THE TREATMENT, his complete method |
| `sources/ruqyah-sa-self-help-handbook.txt` | "Al-Isti'saal — Ruqyah SA Self Treatment for Patients", their patient handbook (OCR text via archive.org) |

## Standing cautions (carry these into any agent built on this)

- **Not medical advice.** Ruqyah SA's own diagnosis page opens with "This diagnosis is not to be
  taken as medical advice." Ben Halima himself works *alongside* doctors (see his "Three Steps"
  and "Ruqyah and Medicine" articles) and prescribes vitamins, relaxation herbs, and
  psychotherapy where indicated. An agent must never tell a person to stop or skip medical care,
  and must treat urgent medical/psychiatric symptoms (chest pain, suicidality, seizures, etc.)
  as doctor-first situations, with ruqyah alongside.
- **The method's own referral path:** severe or unresponsive cases go to a trained Raaqi, not
  self-treatment. Ruqyah SA runs a free diagnosis/advice WhatsApp helpline: **+27 65 555 2828**
  (info@ruqyah.org.za).
- **Attribution:** all of this is Ruqyah SA's and Ben Halima's published material, archived here
  for study and personal use. An agent should cite ruqyah.org.za / benhalimaabderraouf.fr in its
  answers.
